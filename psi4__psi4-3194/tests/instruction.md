# Issue

**Title:** guess what, try to fix CI again: Eco (M)

## Description

## Description
<!-- Provide a brief description of the PR's purpose here. -->


## Dev notes & details
<!-- A bullet-point format description of what this PR does "at a glance."
     Target audience is code reviewers and other devs skimming PRs.
     Should be more technical than user notes. Should never be empty. -->

- [x] fix Eco (W) GHA by recognizing that updating the setup-miniconda version changed the environment path, so the find-the-iomp5-lib cmake cmd needed to change, too, for sapt.cc to compile.
- [x] wow, fixing Eco (M) GHA was not what I expected. To recap, without psi4 code changing or the binaries of any of our QC dependencies changing, Mac builds (Intel or Silicon) started issuing "Illegal Instruction" on Hartree--Fock water. :-( This affected any fresh conda env; for instance updating a "working" python 3.12.3 env to 3.12.4 was accompanied by many other package updates and led to a "illegal instruction" env upon recompiling psi. I know c-f has been updating how they handle the c stdlib (). New environments apparently hit the new fundamental libraries, and those insert a breakpoint if you try to access out of bounds. So fixed the bounds error. :-)

```
(lldb) settings set -- target.run-args  "stage/bin/psi4" "../tests/tu1-h2o-energy/input.dat"
(lldb) run
Process 22217 launched: '/Users/loriab/linux/miniconda-silicon/envs/p4dev312cf_clone/bin/python' (arm64)
Process 22217 stopped
* thread #1, queue = 'com.apple.main-thread', stop reason = EXC_BREAKPOINT (code=1, subcode=0x11819b7e4)
    frame #0: 0x000000011819b7e4 core.cpython-312-darwin.so`std::__1::vector<double, std::__1::allocator<double> >::operator[][abi:fe180100](this=0x00000001013e5378 size=27, __n=27) at vector:1393:3
   1390	template <class _Tp, class _Allocator>
   1391	_LIBCPP_CONSTEXPR_SINCE_CXX20 inline _LIBCPP_HIDE_FROM_ABI typename vector<_Tp, _Allocator>::reference
   1392	vector<_Tp, _Allocator>::operator[](size_type __n) _NOEXCEPT {
-> 1393	  _LIBCPP_ASSERT_VALID_ELEMENT_ACCESS(__n < size(), "vector[] index out of bounds");
   1394	  return this->__begin_[__n];
   1395	}
   1396	
Target 0: (python) stopped.
(lldb) bt
* thread #1, queue = 'com.apple.main-thread', stop reason = EXC_BREAKPOINT (code=1, subcode=0x11819b7e4)
  * frame #0: 0x000000011819b7e4 core.cpython-312-darwin.so`std::__1::vector<double, std::__1::allocator<double> >::operator[][abi:fe180100](this=0x00000001013e5378 size=27, __n=27) at vector:1393:3
    frame #1: 0x00000001196d0a7c core.cpython-312-darwin.so`psi::BasisSet::update_l2_shells(this=0x00000001013e5128, embed_normalization=true) at basisset.cc:876:80
```
- [x] For now GHA has both Intel and Silicon runners, so might as well test both. The Eco runners are also running ctest quick for now to get some regular testing in since those aren't covered by Azure.  
- [x] add adcc and forte tests to smoke. forte not tested in ecosystem yet.
- [x] fix docs GHA by forgiving FixedSize
- [x] fix docs again by restraining sphinx<8 b/c of an interaction with documenting pydantic v1

## Checklist
- [ ] Tests added for any new features
- [ ] [All or relevant fraction of full tests run](http://psicode.org/psi4manual/master/build_planning.html#how-to-run-a-subset-of-tests)

## Status
- [x] Ready for review
- [x] Ready for merge

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `7245e70546a7`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.