# How to Start Mining with Qubic.Solutions

## Download Miner
- **EP110 CPU Miner:** [Download v0.6.1](https://github.com/Qubic-Solutions/rqiner-builds/releases/tag/v0.6.1)
- **EP110 GPU Miner:** [Download v0.6.0](https://github.com/Qubic-Solutions/rqiner-gpu-builds/releases/tag/v0.6.0)
- **EP110 HiveOS Miner:** [Download EP109](https://github.com/Qubic-Solutions/HiveOS/releases/tag/EP109)

## Check Your Stats
- **Official:** [Qubic-Solutions Stats](https://pooltemp.qubic.solutions/info?miner=YOURIDHERE)
- **By @Minerninja:** [Qubic Stats](http://qubic.commando.sh/)

## **Discord**
- [![](https://img.shields.io/discord/1179806757204267090?color=5865F2&logo=Discord&style=flat-square)](https://discord.gg/zTrdShyQu2)

# **CPU** 
- **Linux**
```
wget https://github.com/Qubic-Solutions/rqiner-builds/releases/download/v0.6.1/rqiner-x86-znver4
chmod 777 rqiner-x86-znver4
./rqiner-x86-znver4 -t <threads> -i <payout-id>
```

- **Windows**

Download: https://github.com/Qubic-Solutions/rqiner-builds/releases/download/v0.6.1/rqiner-x86-znver4.exe
Start it with the following command with the CMD console:
`./rqiner-x86-znver4.exe -t <threads> -i <payout-id>`

# **Mobile Mining** 
```
pkg install proot-distro
proot-distro install ubuntu
proot-distro login ubuntu
apt update
apt install -y wget
wget https://github.com/Qubic-Solutions/rqiner-builds/releases/download/v0.6.1/rqiner-aarch64-mobile
chmod +x rqiner-aarch64-mobile
./rqiner-aarch64-mobile -t <threads> -i <payout-id>
```
# **GPU, Cuda**

**→ Linux**
```
wget https://github.com/Qubic-Solutions/rqiner-gpu-builds/releases/download/v0.6.0/rqiner-x86-cuda
chmod 777 rqiner-x86-cuda
./rqiner-x86-cuda -i <payout-id> -l <label>
```
**→ Windows**
Download: https://github.com/Qubic-Solutions/rqiner-gpu-builds/releases/download/v0.6.0/rqiner-x86-cuda.exe
Run it in the same folder with following command:
`./rqiner-x86-cuda.exe -i <payout-id> -l <label>`

# GPU+CPU HiveOS 

**→CPU only**: [Download](https://github.com/Qubic-Solutions/HiveOS/releases/download/EP109/rqiner-x86-CPU.v.0.6.1.tar.gz)

**→GPU only**: [Download](https://github.com/Qubic-Solutions/HiveOS/releases/download/EP109/rqiner-x86-cuda-gpu.0.6.0.tar.gz)

**→GPU + CPU**: [Download](https://github.com/Qubic-Solutions/HiveOS/releases/download/EP109/rqiner-x86-cuda-Nvidia.Broadwell.0.6.0.tar.gz)

**→GPU + ZEN4**: [Download](https://github.com/Qubic-Solutions/HiveOS/releases/download/EP109/rqiner-x86-cuda-Nvidia.Zen4.0.6.0.tar.gz)

### Hive OS flightsheet (GPU)
Simple:```-i wallet_address --label %WORKER_NAME%```
Pro:```$(nvtool --setcore 1700 --setcoreoffset 200 --setmem 1500) -i wallet_address --label %WORKER_NAME%```

### Recommended GPU overclocks :  
**Medium**  
3000 series ```nvtool --setcoreoffset 250 --setclocks 1500 --setmem 5001```  
4000 series ```nvtool --setcoreoffset 250 --setclocks 2400 --setmem 5001```  
**High**  
3000 series ```nvtool --setcoreoffset 200 --setclocks 1600 --setmem 7000 --setmemoffset 2000```  
4000 series ```nvtool --setcoreoffset 200 --setclocks 2900 --setmem 7000 --setmemoffset 2000```  

- Extra config arguments:

| Setting | Description |
| ---- | --------- |
| ```"-t, --threads <THREADS>":``` | Amount of threads used for mining |
| ```"-b, --bench":``` |  Benchmarks your miner without submitting solutions |
| ```"-i, --id <ID>":``` |  Your payout Qubic ID (required for pool mining) |
|  ```"-l, --label <LABEL>": ``` |  Label used for identification of your miner on the pool |
| ```"-h, --help": ```  |  Print help  |
| ```"-V, --version": ```  |  Print version  |


