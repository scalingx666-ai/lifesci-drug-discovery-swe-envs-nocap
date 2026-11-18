# Issue

**Title:** Make the loopback test servers robust to slow and closing clients

## Description

## Summary

Two CI flakes came from the test-only HTTP servers that the Rust download tests run on 127.0.0.1, not from the code under test. This PR makes those servers robust. It changes test code only, plus the required build-stamp bump.

1. **macOS, seen on #247:** `local_engine::tests::redirected_download_honours_proxy_exclusion_and_names_failing_destination` panicked at `network_test_http.rs:39` with `Os { code: 22, kind: InvalidInput }`. In `reply()`'s loop that drains the connection after the response, `set_read_timeout(...).unwrap()` fails on macOS once the client has already closed the socket.
2. **Seen on #243:** `external_tools::install_tests::stale_managed_copies_offer_update_and_replace_without_touching_user_files`. The install test server polled a nonblocking `accept()` against a fixed 10 s deadline and then panicked with os error 35 (WouldBlock). A slow runner's client connected after the server had given up and got "connection refused". The redirect/proxy test's own server had the same pattern with a 5 s deadline.

## Changes, each with its reason

- **`reply()`: stop draining when setting the read timeout fails.** By then the response has been written, and the error only means the client already closed (EINVAL on macOS).
- **`reply()`: ignore an error from `shutdown(Write)` after a successful write.** A client that already closed can make shutdown fail (ENOTCONN). `write_all` of the response still fails loudly, so a real failure is not hidden.
- **`reply()`: clearer messages in the header-reading loop.** A client that closes before sending complete headers is still a test failure, now with a message that says so instead of an opaque `unwrap` on EINVAL.
- **One shared, test-only `LoopbackServer` in `network_test_http.rs`.** It accepts until the test joins (or drops) the handle, not until a fixed deadline, so a slow client can always connect. Joining or dropping signals "the client is done" over a channel, so a test that fails before its client connects cannot hang CI.
- **The server returns how many clients it served, and the tests assert it.** `join()` requires at least one, which keeps the old guarantee that the client really reached the server. `join_unused()` requires none and is used only by the new `loopback_server_stops_when_client_never_connects` test.
- **The redirect/proxy test asserts exactly two direct connections** instead of relying on a 5 s accept deadline. If `NO_PROXY` were ignored, the client would go to the closed proxy port and the count would fail promptly, without a timer.
- **`CURRENT_BUILD_STAMP` → `10.29.12.17-codex`.** CI requires a stamp bump for any change under `src-tauri/src`.

The other users of `network_test_http::reply` (`network_error_tests.rs`, `ocsr_engine/install.rs`) only become more lenient, and only after the response has been written.

## Files changed

- `apps/desktop/src-tauri/src/network_test_http.rs` (`#[cfg(test)]`): `LoopbackServer`, and the `reply()` changes above.
- `apps/desktop/src-tauri/src/external_tools/install_tests.rs`: uses the shared server; adds the never-connects test.
- `apps/desktop/src-tauri/src/local_engine/tests.rs`: uses the shared server; asserts exactly two connections.
- `apps/desktop/src/MainWindow.tsx`: build stamp only.

## Tests run

Run on macOS at 01a80201 (the change itself; main was merged in afterwards with only a stamp conflict) under the machine's heavy-job slot:

- `cargo fmt --check`: pass
- `cargo clippy --all-targets -- -D warnings`: pass
- `cargo test` (whole crate): **592 passed, 0 failed**, 9 ignored, including
  `redirected_download_honours_proxy_exclusion_and_names_failing_destination`,
  `stale_managed_copies_offer_update_and_replace_without_touching_user_files` and the new
  `loopback_server_stops_when_client_never_connects`.

No existing test expectation was weakened: `join()` now asserts more (that a client was served), and the
proxy test asserts an exact connection count.

## Results

Review: Opus approved with changes (two low findings: `join()` no longer proved a client connected, and the redirect test kept the fixed-deadline pattern). Both were fixed; the Opus re-review approved. `Reviewed-by` lines are in the commit.

## Platforms

- **macOS:** fmt, clippy and the whole crate's tests pass locally (592/592 run).
- **Windows:** not run locally. CI's Windows job runs the same tests and clippy. Nonblocking `accept()` maps WSAEWOULDBLOCK to WouldBlock, and accepted sockets inherit nonblocking mode, which `reply()` already resets.

## Known limitations

- The cancellation test in `install_tests.rs` (around line 456) can, in principle, still fail at the response write if the client cancels mid-body before the 1.1 MiB response is buffered. That is unchanged by this PR; note it only if it ever shows up as a flake.

## One recommended next task

Watch the next few CI runs for these two tests.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `826c66270685`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.