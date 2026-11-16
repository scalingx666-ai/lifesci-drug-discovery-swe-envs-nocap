# Issue

**Title:** Stop global hostcalls at synchronization (AMDGPU)

## Description

When running on AMD GPUs, and especially on Mi300a, we get a lot of warning of the sort:

```
┌ Info: Global hostcalls detected!
│ - Source: MethodInstance for (::GPUArrays.var"#gpu_map_kernel#gpu_map_kernel##0")(::KernelAbstractions.CompilerMetadata{KernelAbstractions.NDIteration.DynamicSize, KernelAbstractions.NDIteration.DynamicCheck, Nothing, CartesianIndices{1, Tuple{Base.OneTo{Int64}}}, KernelAbstractions.NDIteration.NDRange{1, KernelAbstractions.NDIteration.DynamicSize, KernelAbstractions.NDIteration.DynamicSize, CartesianIndices{1, Tuple{Base.OneTo{Int64}}}, CartesianIndices{1, Tuple{Base.OneTo{Int64}}}}}, ::AMDGPU.Device.ROCDeviceVector{ComplexF64, 1}, ::Base.Broadcast.Broadcasted{AMDGPU.ROCArrayStyle{1, AMDGPU.Runtime.Mem.HIPBuffer}, Tuple{Base.OneTo{Int64}}, DFTK.var"#_forces_xc##0#_forces_xc##1"{ROCDeviceArray{ComplexF64, 3, 1}, AMDGPU.Device.ROCDeviceVector{Int64, 1}, ROCDeviceArray{StaticArraysCore.SVector{3, Int64}, 3, 1}, AMDGPU.Device.ROCDeviceVector{Float64, 1}, StaticArraysCore.SVector{3, Float64}}, Tuple{Base.Broadcast.Extruded{AMDGPU.Device.ROCDeviceVector{Int64, 1}, Tuple{Bool}, Tuple{Int64}}}})
│ - Hostcalls: [:malloc_hostcall, :malloc_hostcall]
│
│ Use `AMDGPU.synchronize(; stop_hostcalls=true)` to synchronize and stop them.
└ Otherwise, performance might degrade if they keep running in the background.
```

This PR implements the recommended fix. Global hostcalls are interrupted every time the device is synchronized, so at least every time there is MPI communication (incl. with single MPI rank).

As far as I can tell, there is no impact on performance, but maybe I didn't run long enough calculations.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `9fd115c7ce1b`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.