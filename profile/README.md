# How to Start Mining with Qubic.Solutions

## Download Miner
- **CPU Miner:** [PPLNS/SOLO Download v1.0.0](https://github.com/Qubic-Solutions/rqiner-builds/releases/tag/v1.0.0-beta)
- **GPU Miner:** [SOLO Download v0.8.0](https://github.com/Qubic-Solutions/rqiner-gpu-builds/releases/tag/v0.8.0)
- **Hybrid Miner:** [PPLNS/SOLO Download v1.0.0-beta](https://github.com/Qubic-Solutions/rqiner-hybrid-builds)
- **HiveOS Miner:** [PPLNS/SOLO Download v1.0.0-beta](https://github.com/Qubic-Solutions/HiveOS/releases)
- **Cluster Miner:** [PPLNS/SOLO Download v1.0.0-beta](https://github.com/Qubic-Solutions/rcluster-builds/releases/tag/v1.0.0-beta.1)

## Check Your Stats
- **Official:** [Mining Stats](https://pooltemp.qubic.solutions/info?miner=YOURIDHERE)
- **By @Minerninja:** [Mining Stats](http://qubic.commando.sh/)

## **Discord**
- [![](https://img.shields.io/discord/1179806757204267090?color=5865F2&logo=Discord&style=flat-square)](https://discord.gg/zTrdShyQu2)

# **CPU (zen4)** 
- **Linux**
```
wget https://github.com/Qubic-Solutions/rqiner-builds/releases/download/v1.0.0-beta/rqiner-x86-znver4
chmod 777 rqiner-x86-znver4
./rqiner-x86-znver4 -t <threads> -i <payout-id>
```

- **Windows**

Download: https://github.com/Qubic-Solutions/rqiner-builds/releases/download/v1.0.0-beta/rqiner-x86-znver4
Start it with the following command with the CMD console:
`./rqiner-x86-znver4.exe -t <threads> -i <payout-id> -l <label>`

# **Mobile Mining** 
```
pkg install proot-distro
proot-distro install ubuntu
proot-distro login ubuntu
apt update
apt install -y wget
wget https://github.com/Qubic-Solutions/rqiner-builds/releases/download/v0.8.0/rqiner-aarch64-mobile
chmod +x rqiner-aarch64-mobile
./rqiner-aarch64-mobile -t <threads> -i <payout-id>
```
# **GPU, Cuda**

**→ Linux**
```
wget **https://github.com/Qubic-Solutions/rqiner-gpu-builds/releases/download/v0.8.0/rqiner-x86-cuda**
chmod 777 rqiner-x86-cuda
./rqiner-x86-cuda -i <payout-id> -l <label>
```
**→ Windows**
Download: **https://github.com/Qubic-Solutions/rqiner-gpu-builds/releases/download/v0.8.0/rqiner-x86-cuda.exe**
Run it in the same folder with following command:
`./rqiner-x86-cuda.exe -i <payout-id> -l <label>`

# How to run the Hybrid miner

First download the correct binary from the releases in this repo.
Similar to the regular CPU miner you will have to set the amount of threads as well as a payout ID and an optional label. For the GPU part of this implementation an additional parameter is required that sets the amount of resources used by your GPU(s).

`rqiner -t <threads> -i <payout-id> -l <label> -n <ndatasets>`

The -n parameter has to be a single value or a comma seperated list e.g.
`-n 500 300 500`
If you set 3 values for n they will be mapped to GPU 0, 1, 2 respectively. Ideal values for n are somewhere between 100-600 depending on your GPU, e.g. 4090: n=500, 4070ti: n=250. In order to find the optimal configuration you can run the GPU miner which will tell you the amount of blocks used in its optimal configuration after the auto-tuning is finished, which you can input as value for your -n parameter.

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


