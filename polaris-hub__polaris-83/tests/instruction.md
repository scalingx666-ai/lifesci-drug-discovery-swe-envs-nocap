# Issue

**Title:** Add a flow to use Zarr datasets through the Hub

## Description

## Changelogs

- Changed `PolarisHubClient.upload_dataset` to also upload the Zarr archive if it exists.
- Added the `zarr_root_archive` attribute to the `Dataset`. 
  - A dataset can now be associated with only a single Zarr archive at a time.
  - Pointer columns now store paths relative to the root Zarr archive
  - This also simplifies saving a dataset to another location, as you only need to change this attribute.
- Deprecated `polaris/utils/io.py`
- Deprecated `polaris/utils/fs.py`

---

_Checklist:_

- [ ] ~_Was this PR discussed in an issue? It is recommended to first discuss a new feature into a GitHub issue before opening a PR._~
- [ ] ~_Add tests to cover the fixed bug(s) or the newly introduced feature(s) (if appropriate)._~
- [X] _Update the API documentation if a new function is added, or an existing one is deleted._
- [X] _Write concise and explanatory changelogs above._
- [X] _If possible, assign one of the following labels to the PR: `feature`, `fix` or `test` (or ask a maintainer to do it for you)._

---

While we cannot do automated tests, I set up a simple test case myself: 

```py
# Create Toy Dataset
def zarr_archive(dest_dir):
    path = dm.utils.fs.join(str(dest_dir), "data.zarr")
    root = zarr.open_group(path, mode="w")
    root.array("A", data=np.random.random((1, 128)))
    root.array("B", data=np.random.random((1, 128)))
    return path

def test(name):

    fs = s3fs.S3FileSystem(
        key=..., 
        secret=..., 
        client_kwargs=dict(endpoint_url=...), 
        s3_additional_kwargs=dict(ACL="private"), # <- this is neccessary for writing. 
    )
        
    try:
        with TemporaryDirectory() as tmpdir: 
            path = zarr_archive(tmpdir)

            dst = dm.utils.fs.join(str(tmpdir), "data", "data.zarr")
            dataset = create_dataset_from_file(path, zarr_root_path=dst)
            print(dataset.get_data(row=0, col="A"))
            
            dataset.name = name
            dataset.owner = "cwognum"
            dataset.source = "https://example.com"
            
            with PolarisHubClient(settings=settings) as client:
                client.upload_dataset(dataset, timeout=(10, 2000))

            dataset = po.load_dataset(f"cwognum/{name}")

            # This attribute is not yet saved to the Hub, so we need to set it manually
            dataset.zarr_root_path = "polarisfs://data.zarr"
            print(dataset.get_data(row=0, col="A"))
            
            dataset.cache() 
            print(dataset.get_data(row=0, col="A"))
    
    finally:
       # This cleans up the Cloudflare, but does not delete the entry in Neon
        fs.rm(f"polaris-test/dataset/cwognum/{name}", recursive=True)


test("test")
```

TODO: 
- [ ] Improve the checksum,  
- [ ] Add the necessary data fields to the Hub. 
- [ ] Make use of consolidated Zarr archives,

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `79b5d4e99d85`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.