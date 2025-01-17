# MMDetection3d Support

MMDetection3d is a next-generation platform for general 3D object detection. It is a part of the [OpenMMLab](https://openmmlab.com/) project.

## MMDetection3d installation tutorial

Please refer to [getting_started.md](https://github.com/open-mmlab/mmdetection3d/blob/master/docs/en/getting_started.md) for installation.

## Example

```bash
python tools/deploy.py \
       configs/mmdet3d/voxel-detection/voxel-detection_tensorrt_dynamic.py \
       ${MMDET3D_DIR}/configs/pointpillars/hv_pointpillars_secfpn_6x8_160e_kitti-3d-3class.py \
       checkpoints/point_pillars.pth \
       ${MMDET3D_DIR}/demo/data/kitti/kitti_000008.bin \
        --work-dir \
        work_dir \
        --show \
        --device \
        cuda:0
```
## List of MMDetection3d models supported by MMDeploy

|       Model        |         Task         | OnnxRuntime | TensorRT | ncnn  | PPLNN | OpenVINO |                                     Model config                                                         |
| :----------------: | :------------------: | :---------: | :------: | :---: | :---: | :------: | :------------------------------------------------------------------------------------------------------: |
|    PointPillars    |   VoxelDetection     |      Y      |    Y     |   N   |   N   |    Y     |     [config](https://github.com/open-mmlab/mmdetection3d/blob/master/configs/pointpillars)     |

## Reminder

Voxel detection onnx model excludes model.voxelize layer and model post process, and you can use python api to call these func.

Example:

```python
from mmdeploy.codebase.mmdet3d.deploy import VoxelDetectionModel
VoxelDetectionModel.voxelize(...)
VoxelDetectionModel.post_process(...)
```
