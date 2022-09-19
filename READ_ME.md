### MoE setting
#### in ds_pretrain_gpt_125M_MoE64.sh
 NUM_GPUS=$(($(ds_ssh nvidia-smi --query-gpu=name --format=csv,noheader | wc -l)-2))  
 NUM_GPUS_PERNODE=$(nvidia-smi --query-gpu=name --format=csv,noheader | wc -l)  
 NUM_NODE=$((${NUM_GPUS} / ${NUM_GPUS_PERNODE} ))  

#### change to 
NUM_GPUS=4  
NUM_GPUS_PERNODE=4  
NUM_NODE=1  

#### Then set
EP_SIZE=64 
#### Then we can enable 16 experts per GPU  
the log is stored in 'gpt-0.125B-MoE64.log'  

If you set EP_SIZE=1, then there is no experts. The model is dense.  
the log is 'gpt-0.125B-no-MoE.log'   
