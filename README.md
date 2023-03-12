# Intel Vtune

## Installation (Linux)
```
sudo sh ./l_oneapi_vtune_p_2023.0.0.25339.sh
echo 'source /opt/intel/oneapi/setvars.sh' >> ~/.bashrc
```

After every boot perform the following commands,
```
sudo sysctl -w kernel.yama.ptrace_scope=0
```

Execute `vtune-gui` to start the profiler

## Installation (Windows)
- Run w_oneapi_vtune_p_2023.0.0.25541.exe
- Run Program Files (x86)\Intel\oneAPI\setvars.bat
- Start vtune-gui from start menu

## Getting Started
- Pro Tip: Run Performance Snapshot first to get a view of what is the greatest bottleneck
- Tutorial at [vtune-tutorial.mkv](vtune-tutorial.mkv)