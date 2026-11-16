# Issue

**Title:** Dense

## Description

`dense` model architecture.

```text
Dense(
  (features): Sequential(
    (data_enc_init_pool): MaxPool3d(kernel_size=2, stride=2, padding=0, dilation=1, ceil_mode=False)
    (data_enc_init_conv): Conv3d(32, 32, kernel_size=(3, 3, 3), stride=(1, 1, 1), padding=(1, 1, 1))
    (data_enc_init_conv_relu): ReLU()
    (dense_block_0): DenseBlock(
      (blocks): ModuleList(
        (0): Sequential(
          (data_enc_level0_batchnorm_conv0): BatchNorm3d(32, eps=1e-05, momentum=0.1, affine=True, track_running_stats=True)
          (data_enc_level0_conv0): Conv3d(32, 16, kernel_size=(3, 3, 3), stride=(1, 1, 1), padding=(1, 1, 1))
          (data_enc_level0_conv0_relu): ReLU()
        )
        (1): Sequential(
          (data_enc_level0_batchnorm_conv1): BatchNorm3d(48, eps=1e-05, momentum=0.1, affine=True, track_running_stats=True)
          (data_enc_level0_conv1): Conv3d(48, 16, kernel_size=(3, 3, 3), stride=(1, 1, 1), padding=(1, 1, 1))
          (data_enc_level0_conv1_relu): ReLU()
        )
        (2): Sequential(
          (data_enc_level0_batchnorm_conv2): BatchNorm3d(64, eps=1e-05, momentum=0.1, affine=True, track_running_stats=True)
          (data_enc_level0_conv2): Conv3d(64, 16, kernel_size=(3, 3, 3), stride=(1, 1, 1), padding=(1, 1, 1))
          (data_enc_level0_conv2_relu): ReLU()
        )
        (3): Sequential(
          (data_enc_level0_batchnorm_conv3): BatchNorm3d(80, eps=1e-05, momentum=0.1, affine=True, track_running_stats=True)
          (data_enc_level0_conv3): Conv3d(80, 16, kernel_size=(3, 3, 3), stride=(1, 1, 1), padding=(1, 1, 1))
          (data_enc_level0_conv3_relu): ReLU()
        )
      )
    )
    (data_enc_level0_bottleneck): Conv3d(96, 96, kernel_size=(1, 1, 1), stride=(1, 1, 1))
    (data_enc_level0_bottleneck_relu): ReLU()
    (data_enc_level1_pool): MaxPool3d(kernel_size=2, stride=2, padding=0, dilation=1, ceil_mode=False)
    (dense_block_1): DenseBlock(
      (blocks): ModuleList(
        (0): Sequential(
          (data_enc_level1_batchnorm_conv0): BatchNorm3d(96, eps=1e-05, momentum=0.1, affine=True, track_running_stats=True)
          (data_enc_level1_conv0): Conv3d(96, 16, kernel_size=(3, 3, 3), stride=(1, 1, 1), padding=(1, 1, 1))
          (data_enc_level1_conv0_relu): ReLU()
        )
        (1): Sequential(
          (data_enc_level1_batchnorm_conv1): BatchNorm3d(112, eps=1e-05, momentum=0.1, affine=True, track_running_stats=True)
          (data_enc_level1_conv1): Conv3d(112, 16, kernel_size=(3, 3, 3), stride=(1, 1, 1), padding=(1, 1, 1))
          (data_enc_level1_conv1_relu): ReLU()
        )
        (2): Sequential(
          (data_enc_level1_batchnorm_conv2): BatchNorm3d(128, eps=1e-05, momentum=0.1, affine=True, track_running_stats=True)
          (data_enc_level1_conv2): Conv3d(128, 16, kernel_size=(3, 3, 3), stride=(1, 1, 1), padding=(1, 1, 1))
          (data_enc_level1_conv2_relu): ReLU()
        )
        (3): Sequential(
          (data_enc_level1_batchnorm_conv3): BatchNorm3d(144, eps=1e-05, momentum=0.1, affine=True, track_running_stats=True)
          (data_enc_level1_conv3): Conv3d(144, 16, kernel_size=(3, 3, 3), stride=(1, 1, 1), padding=(1, 1, 1))
          (data_enc_level1_conv3_relu): ReLU()
        )
      )
    )
    (data_enc_level1_bottleneck): Conv3d(160, 160, kernel_size=(1, 1, 1), stride=(1, 1, 1))
    (data_enc_level1_bottleneck_relu): ReLU()
    (data_enc_level2_pool): MaxPool3d(kernel_size=2, stride=2, padding=0, dilation=1, ceil_mode=False)
    (dense_block_2): DenseBlock(
      (blocks): ModuleList(
        (0): Sequential(
          (data_enc_level2_batchnorm_conv0): BatchNorm3d(160, eps=1e-05, momentum=0.1, affine=True, track_running_stats=True)
          (data_enc_level2_conv0): Conv3d(160, 16, kernel_size=(3, 3, 3), stride=(1, 1, 1), padding=(1, 1, 1))
          (data_enc_level2_conv0_relu): ReLU()
        )
        (1): Sequential(
          (data_enc_level2_batchnorm_conv1): BatchNorm3d(176, eps=1e-05, momentum=0.1, affine=True, track_running_stats=True)
          (data_enc_level2_conv1): Conv3d(176, 16, kernel_size=(3, 3, 3), stride=(1, 1, 1), padding=(1, 1, 1))
          (data_enc_level2_conv1_relu): ReLU()
        )
        (2): Sequential(
          (data_enc_level2_batchnorm_conv2): BatchNorm3d(192, eps=1e-05, momentum=0.1, affine=True, track_running_stats=True)
          (data_enc_level2_conv2): Conv3d(192, 16, kernel_size=(3, 3, 3), stride=(1, 1, 1), padding=(1, 1, 1))
          (data_enc_level2_conv2_relu): ReLU()
        )
        (3): Sequential(
          (data_enc_level2_batchnorm_conv3): BatchNorm3d(208, eps=1e-05, momentum=0.1, affine=True, track_running_stats=True)
          (data_enc_level2_conv3): Conv3d(208, 16, kernel_size=(3, 3, 3), stride=(1, 1, 1), padding=(1, 1, 1))
          (data_enc_level2_conv3_relu): ReLU()
        )
      )
    )
    (data_enc_level2_global_pool): MaxPool3d(kernel_size=(6, 6, 6), stride=(6, 6, 6), padding=0, dilation=1, ceil_mode=False)
  )
  (pose): Sequential(
    (pose_output): Linear(in_features=224, out_features=2, bias=True)
  )
  (affinity): Sequential(
    (affinity_output): Linear(in_features=224, out_features=1, bias=True)
  )
)
```

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `e2dc06b6f69b`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.