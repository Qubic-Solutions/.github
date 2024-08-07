![Github2](https://github.com/user-attachments/assets/df4f0ccc-0995-43b9-b0f3-14aee3a459cc)
# Qubic.Solutions Mining Guide
Welcome to Qubic.Solutions! This guide will help you start mining with our software, step-by-step. Whether you're new to mining or have some experience, we've got you covered.
We offer both PPLNS (Pay Per Last N Shares) and Solo mining options.

## Menu

- [Download Miners](#download-miners)
  - [Which version of the miner I have to use?](#cpu-architectures-and-their-processors)
    - [AMD (znver4)](#zen-4-znver4)
    - [AMD (znver3)](#zen-3-znver3)
    - [Intel (broadwell)](#Broadwell)
- [Monitor Your Mining Stats](#monitor-your-mining-stats)
- [Join Our Community](#join-our-community)
- [Mining Setup Instructions](#mining-setup-instructions)
  - [How to run the CPU miner (znver4/znver3/broadwell)](#how-to-run-the-cpu-miner-znver4znver3broadwell)
  - [How to run the GPU miner (cuda)](#how-to-run-the-gpu-miner-cuda)
  - [How to run the Hybrid miner(CPU + GPU)](#how-to-run-the-hybrid-miner-cpu--gpu)
  - [How to run the Cluster miner (CPU + GPU)](#How-to-run-the-Cluster-miner)
  - [How to run HiveOS (Hybrid/Cluster/CPU)](#how-to-run-hiveos-gpucpu)
    - [Which -n parameter I have to choose?](#-n-parameter)
    - [Which -t parameter I have to choose?](#cpu-architectures-and-their-processors)
- [Extra Config Arguments](#Extra-config-arguments)
- [Support](#support)

### Download Miners
First, you need to download the appropriate miner for your setup. Here are the options:

- CPU Miner:
  - For mining using your computer's CPU.[View Downloads](https://github.com/Qubic-Solutions/rqiner-builds/releases/tag/v1.0.1)
- GPU Miner:
  - For mining using your computer's GPU. [View Downloads]()
- Hybrid Miner:
  - Combines CPU and GPU mining for better performance. [View Downloads]()
- HiveOS Miner:
  - Specifically designed for HiveOS. [View Downloads](https://github.com/Qubic-Solutions/HiveOS/releases/tag/EP121)
- Cluster Miner:
  - For cluster mining. [View Downloads]()

### Monitor Your Mining Stats
Once you start mining, you can monitor your performance and earnings through these links:
- **Official Qubic-Solutions Stats:**
  - Track your stats here. [View Stats](https://pool.qubic.solutions/info?miner=YOURIDHERE)
- **Stats by @Minerninja:**
  - An alternative stats tracker. [View Stats](http://qubic.commando.sh/)

### Join Our Community
If you need help or want to connect with other miners, join our Discord community:

- **Discord:**
  - [![](https://img.shields.io/discord/1179806757204267090?color=5865F2&logo=Discord&style=flat-square)](https://discord.gg/zTrdShyQu2)

## Mining Setup Instructions

### How to run the CPU miner (znver4/znver3/broadwell)

**Linux**
```
wget https://github.com/Qubic-Solutions/rqiner-builds/releases/download/v1.0.1/rqiner-x86-znver4
chmod 777 rqiner-x86-znver4
./rqiner-x86-znver4 -t <threads> -i <payout-id>
```
**Windows**
- Download: `https://github.com/Qubic-Solutions/rqiner-builds/releases/download/v1.0.1/rqiner-x86-znver4.exe`
- Start it with the following command with the CMD/Powershell console: `./rqiner-x86-znver4.exe -t <threads> -i <payout-id> -l <label>`

### How to run the GPU miner (cuda)

**Linux**
```
wget https://github.com/Qubic-Solutions/rqiner-gpu-builds/releases/download/v0.8.0/rqiner-x86-cuda
chmod 777 rqiner-x86-cuda
./rqiner-x86-cuda -i <payout-id> -l <label>
```
**Windows**
- Download: ```https://github.com/Qubic-Solutions/rqiner-gpu-builds/releases/download/v0.8.0/rqiner-x86-cuda.exe```
- Start it with the following command with the CMD/Powershell console: ```./rqiner-x86-cuda.exe -i <payout-id> -l <label>```

### How to run the Hybrid miner (CPU + GPU)

Similar to the regular CPU miner you will have to set the amount of threads as well as a payout ID and an optional label. For the GPU part of this implementation an additional parameter is required that sets the amount of resources used by your GPU(s).

`rqiner -t <threads> -i <payout-id> -l <label> -n <ndatasets>`

The -n parameter has to be a single value or a comma seperated list e.g.
`-n 500 300 500`
If you set 3 values for n they will be mapped to GPU 0, 1, 2 respectively. Ideal values for n are somewhere between 100-600 depending on your GPU, e.g. 4090: n=500, 4070ti: n=250. In order to find the optimal configuration you can run the GPU miner which will tell you the amount of blocks used in its optimal configuration after the auto-tuning is finished, which you can input as value for your -n parameter.

### How to run the Cluster miner 

- rcluster-main
host ``rcluster-main`` on node machine
edit ``rcluster-config.json`` cluster_buffer, cluster_name and cluster_payout_id
(cluster_buffer = total threads in cluster / 2)
open port 2003 for ``rcluster-gpu + rqiner`` connections
``sudo ufw allow 2003``
run; ``./rcluster-main``

- rcluster-gpu-x86
run; ``./rcluster-gpu --cluster-ip <IP> --cluster-port <PORT> -n <ndata>`` 
(n = cuda cores / 32)
(``rcluster-gpu-x86`` will connect to ``rcluster-main`` and wait for jobs from CPU miners)

- rqiner-x86cluster-znver3/4
run; ``./rqiner -t <threads> -i <payout-id> -l <label> --cluster-ip <IP:PORT>``

### How to run HiveOS (GPU/CPU)
- Url: Qubic.Solutions
- Install Url (Hybrid/PPLNS) : ```https://github.com/Qubic-Solutions/HiveOS/releases/download/PPLNS-v1.0.0-beta/rqiner-x86-Hybrid.1.0.0Beta.tar.gz```
- Template: ```-arch znver4 -t $(nproc) -n 328 -i <payout-id> -l %WORKER_NAME%```
- Pro Tamplate: ```$(nvtool --setcore 1700 --setcoreoffset 200 --setmem 1500) -i wallet_address --label %WORKER_NAME%```

- Recommended HiveOS GPU overclocks :  
**Medium**  
3000 series ```nvtool --setcoreoffset 250 --setclocks 1500 --setmem 5001```  
4000 series ```nvtool --setcoreoffset 250 --setclocks 2400 --setmem 5001```  
**High**  
3000 series ```nvtool --setcoreoffset 200 --setclocks 1600 --setmem 7000 --setmemoffset 2000```  
4000 series ```nvtool --setcoreoffset 200 --setclocks 2900 --setmem 7000 --setmemoffset 2000```  

### -n Parameter
Search for your GPU and select the right felt on the right side to get the best performance.

| **GPU Model**                   | **CUDA Cores** | **-n** |
|---------------------------------|----------------|---------------------|
| NVIDIA GeForce RTX 4090         | 16,384         | 512                 |
| NVIDIA GeForce RTX 4080         | 9,728          | 304                 |
| NVIDIA GeForce RTX 4070 Ti      | 7,680          | 240                 |
| NVIDIA GeForce RTX 4070         | 5,888          | 184                 |
| NVIDIA GeForce RTX 4060 Ti      | 4,352          | 136                 |
| NVIDIA GeForce RTX 4060         | 3,072          | 96                  |
| NVIDIA GeForce RTX 3090         | 10,496         | 328                 |
| NVIDIA GeForce RTX 3080         | 8,704          | 272                 |
| NVIDIA GeForce RTX 3070 Ti      | 6,144          | 192                 |
| NVIDIA GeForce RTX 3070         | 5,888          | 184                 |
| NVIDIA GeForce RTX 3060 Ti      | 4,864          | 152                 |
| NVIDIA GeForce RTX 3060         | 3,584          | 112                 |
| NVIDIA GeForce GTX 1660 Ti      | 1,536          | 48                  |
| NVIDIA GeForce GTX 1660 Super   | 1,408          | 44                  |
| NVIDIA GeForce GTX 1650 Super   | 1,024          | 32                  |

## NVIDIA Quadro GPUs

| **GPU Model**                   | **CUDA Cores** | **-n** |
|---------------------------------|----------------|---------------------|
| NVIDIA Quadro RTX 8000          | 4,608          | 144                 |
| NVIDIA Quadro RTX 6000          | 4,608          | 144                 |
| NVIDIA Quadro RTX 4000          | 2,304          | 72                  |
| NVIDIA Quadro P6000             | 3,840          | 120                 |
| NVIDIA Quadro P5000             | 2,560          | 80                  |

## NVIDIA Tesla GPUs

| **GPU Model**                   | **CUDA Cores** | **-n** |
|---------------------------------|----------------|---------------------|
| NVIDIA Tesla V100               | 5,120          | 160                 |
| NVIDIA Tesla P100               | 3,584          | 112                 |
| NVIDIA Tesla T4                 | 2,560          | 80                  |

## NVIDIA A100 (Data Center GPU)

| **GPU Model**                   | **CUDA Cores** | **-n** |
|---------------------------------|----------------|---------------------|
| NVIDIA A100                     | 6,912          | 216                 |

## CPU Architectures and Their Processors

This document provides a list of CPUs for the following microarchitectures: Zen 4 (znver4), Zen 3 (znver3), and Broadwell.

## Zen 4 (znver4)

Zen 4 is AMD's microarchitecture used in their Ryzen 7000 series processors and EPYC 9004 series processors.

| **Processor Model**    | **Cores** | **-t** |
|------------------------|-----------|-------------|
| AMD Ryzen 9 7950X     | 16        | 32          |
| AMD Ryzen 9 7900X     | 12        | 24          |
| AMD Ryzen 7 7800X3D   | 8         | 16          |
| AMD Ryzen 7 7700X     | 8         | 16          |
| AMD Ryzen 5 7600X     | 6         | 12          |
| AMD EPYC 9654         | 96        | 192         |
| AMD EPYC 9554         | 64        | 128         |

## Zen 3 (znver3)

Zen 3 is AMD's microarchitecture used in Ryzen 5000 series processors and EPYC 7003 series processors.

| **Processor Model**    | **Cores** | **-t** |
|------------------------|-----------|-------------|
| AMD Ryzen 9 5950X     | 16        | 32          |
| AMD Ryzen 9 5900X     | 12        | 24          |
| AMD Ryzen 7 5800X     | 8         | 16          |
| AMD Ryzen 5 5600X     | 6         | 12          |
| AMD EPYC 7763         | 64        | 128         |
| AMD EPYC 7543         | 32        | 64          |

## Broadwell

Broadwell is Intel's microarchitecture used in some 5th Gen Core processors and Xeon E5-2600 v4 series.

| **Processor Model**     | **Cores** | **-t** |
|-------------------------|-----------|-------------|
| Intel Core i7-5950HQ    | 4         | 8           |
| Intel Core i7-5775C     | 4         | 8           |
| Intel Core i5-5675C     | 4         | 4           |
| Intel Xeon E5-2699 v4   | 22        | 44          |
| Intel Xeon E5-2687W v4  | 8         | 16          |

- Extra config arguments:

| Setting | Description |
| ---- | --------- |
| ```"-t, --threads <THREADS>":``` | Amount of threads used for mining |
| ```"-b, --bench":``` |  Benchmarks your miner without submitting solutions |
| ```"-i, --id <ID>":``` |  Your payout Qubic ID (required for pool mining) |
|  ```"-l, --label <LABEL>": ``` |  Label used for identification of your miner on the pool |
| ```"-h, --help": ```  |  Print help  |
| ```"-V, --version": ```  |  Print version  |

## Support

If you encounter any issues or have questions, please join our Discord community for support and further information.

- **Discord:**
  - [![](https://img.shields.io/discord/1179806757204267090?color=5865F2&logo=Discord&style=flat-square)](https://discord.gg/zTrdShyQu2)

Thank you for choosing Qubic.Solutions! Happy mining!


