# DeepPose
DeepPose using MMPose
123
python demo/body3d_two_stage_img_demo.py \
    ${MMPOSE_CONFIG_FILE_3D} \
    ${MMPOSE_CHECKPOINT_FILE_3D} \
    --json-file ${JSON_FILE} \
    --img-root ${IMG_ROOT} \
    --only-second-stage \
    [--show] \
    [--device ${GPU_ID or CPU}] \
    [--out-img-root ${OUTPUT_DIR}] \
    [--rebase-keypoint-height] \
    [--show-ground-truth]