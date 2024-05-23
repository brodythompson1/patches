# Pre-training PATCHES

## Original Implementation

Note here that we have modified the model with the number of patches paramenter. The base model is still using VideoMAE base files, hence why VideoMAE is called in the bash command.


- For example, to pre-train VideoMAE ViT-Base on **Kinetics400** with 64 GPUs (8 nodes x 8 GPUs), you can run

  ```bash
  OUTPUT_DIR='YOUR_PATH/k400_videomae_pretrain_base_patch16_224_frame_16x4_tube_mask_ratio_0.9_e800'
  DATA_PATH='YOUR_PATH/list_kinetics-400/train.csv'
  
  OMP_NUM_THREADS=1 python3 -m torch.distributed.launch --nproc_per_node=8 \
          --master_port 12320 --nnodes=8 \
          --node_rank=0 --master_addr=$your_node_0_ip \
          run_mae_pretraining.py \
          --data_path ${DATA_PATH} \
          --mask_type tube \
          --mask_ratio 0.9 \
          --model pretrain_videomae_base_patch16_224 \
          --decoder_depth 4 \
          --batch_size 32 \
          --num_frames 16 \
          --sampling_rate 4 \
          --opt adamw \
          --opt_betas 0.9 0.95 \
          --warmup_epochs 40 \
          --save_ckpt_freq 20 \
          --epochs 801 \
          --log_dir ${OUTPUT_DIR} \
          --output_dir ${OUTPUT_DIR}
  ```

  on the first node. On other nodes, run the same command with `--node_rank 1`, ..., `--node_rank 7` respectively.  `--master_addr` is set as the ip of the node 0.
