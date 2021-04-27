## basic management

### 1. basic message

~~~
> uname -a
Linux manjaro 5.9.16-1-MANJARO #1 SMP PREEMPT Mon Dec 21 22:00:46 UTC 2020 x86_64 GNU/Linux
~~~

~~~
> lsb_release -a
LSB Version:	n/a
Distributor ID:	ManjaroLinux
Description:	Manjaro Linux
Release:	21.0.2
Codename:	Ornara
~~~

```
neofetch
screenfetch
```
### 2. CPU

~~~~~
> lscpu
Architecture:                    x86_64
CPU op-mode(s):                  32-bit, 64-bit
Byte Order:                      Little Endian
Address sizes:                   39 bits physical, 48 bits virtual
CPU(s):                          8
On-line CPU(s) list:             0-7
Thread(s) per core:              2
Core(s) per socket:              4
Socket(s):                       1
NUMA node(s):                    1
Vendor ID:                       GenuineIntel
CPU family:                      6
Model:                           158
Model name:                      Intel(R) Core(TM) i7-7700 CPU @ 3.60GHz
Stepping:                        9
CPU MHz:                         2165.884
CPU max MHz:                     4200.0000
CPU min MHz:                     800.0000
BogoMIPS:                        7202.00
Virtualization:                  VT-x
L1d cache:                       128 KiB
L1i cache:                       128 KiB
L2 cache:                        1 MiB
L3 cache:                        8 MiB
NUMA node0 CPU(s):               0-7
Vulnerability Itlb multihit:     KVM: Mitigation: VMX disabled
Vulnerability L1tf:              Mitigation; PTE Inversion; VMX conditional cach
                                 e flushes, SMT vulnerable
Vulnerability Mds:               Mitigation; Clear CPU buffers; SMT vulnerable
Vulnerability Meltdown:          Mitigation; PTI
Vulnerability Spec store bypass: Mitigation; Speculative Store Bypass disabled v
                                 ia prctl and seccomp
Vulnerability Spectre v1:        Mitigation; usercopy/swapgs barriers and __user
                                  pointer sanitization
Vulnerability Spectre v2:        Mitigation; Full generic retpoline, IBPB condit
                                 ional, IBRS_FW, STIBP conditional, RSB filling
Vulnerability Srbds:             Mitigation; Microcode
Vulnerability Tsx async abort:   Mitigation; Clear CPU buffers; SMT vulnerable
Flags:                           fpu vme de pse tsc msr pae mce cx8 apic sep mtr
                                 r pge mca cmov pat pse36 clflush dts acpi mmx f
                                 xsr sse sse2 ss ht tm pbe syscall nx pdpe1gb rd
                                 tscp lm constant_tsc art arch_perfmon pebs bts 
                                 rep_good nopl xtopology nonstop_tsc cpuid aperf
                                 mperf pni pclmulqdq dtes64 monitor ds_cpl vmx s
                                 mx est tm2 ssse3 sdbg fma cx16 xtpr pdcm pcid s
                                 se4_1 sse4_2 x2apic movbe popcnt tsc_deadline_t
                                 imer aes xsave avx f16c rdrand lahf_lm abm 3dno
                                 wprefetch cpuid_fault epb invpcid_single pti ss
                                 bd ibrs ibpb stibp tpr_shadow vnmi flexpriority
                                  ept vpid ept_ad fsgsbase tsc_adjust bmi1 hle a
                                 vx2 smep bmi2 erms invpcid rtm mpx rdseed adx s
                                 map clflushopt intel_pt xsaveopt xsavec xgetbv1
                                  xsaves dtherm ida arat pln pts hwp hwp_notify 
                                 hwp_act_window hwp_epp md_clear flush_l1d
~~~~~

### 3. GPU

~~~
> lspci
00:00.0 Host bridge: Intel Corporation Xeon E3-1200 v6/7th Gen Core Processor Host Bridge/DRAM Registers (rev 05)
00:01.0 PCI bridge: Intel Corporation 6th-9th Gen Core Processor PCIe Controller (x16) (rev 05)
00:08.0 System peripheral: Intel Corporation Xeon E3-1200 v5/v6 / E3-1500 v5 / 6th/7th/8th Gen Core Processor Gaussian Mixture Model
00:14.0 USB controller: Intel Corporation 200 Series/Z370 Chipset Family USB 3.0 xHCI Controller
00:14.2 Signal processing controller: Intel Corporation 200 Series PCH Thermal Subsystem
00:15.0 Signal processing controller: Intel Corporation 200 Series PCH Serial IO I2C Controller #0
00:15.1 Signal processing controller: Intel Corporation 200 Series PCH Serial IO I2C Controller #1
00:16.0 Communication controller: Intel Corporation 200 Series PCH CSME HECI #1
00:17.0 SATA controller: Intel Corporation 200 Series PCH SATA controller [AHCI mode]
00:1c.0 PCI bridge: Intel Corporation 200 Series PCH PCI Express Root Port #7 (rev f0)
00:1d.0 PCI bridge: Intel Corporation 200 Series PCH PCI Express Root Port #9 (rev f0)
00:1d.7 PCI bridge: Intel Corporation 200 Series PCH PCI Express Root Port #16 (rev f0)
00:1f.0 ISA bridge: Intel Corporation 200 Series PCH LPC Controller (H270)
00:1f.2 Memory controller: Intel Corporation 200 Series/Z370 Chipset Family Power Management Controller
00:1f.3 Audio device: Intel Corporation 200 Series PCH HD Audio
00:1f.4 SMBus: Intel Corporation 200 Series/Z370 Chipset Family SMBus Controller
00:1f.6 Ethernet controller: Intel Corporation Ethernet Connection (2) I219-V
01:00.0 VGA compatible controller: NVIDIA Corporation GP104 [GeForce GTX 1080] (rev a1)
01:00.1 Audio device: NVIDIA Corporation GP104 High Definition Audio Controller (rev a1)
02:00.0 USB controller: ASMedia Technology Inc. ASM1142 USB 3.1 Host Controller
04:00.0 USB controller: ASMedia Technology Inc. ASM1142 USB 3.1 Host Controller
~~~

~~~
> lspci |grep VGA
01:00.0 VGA compatible controller: NVIDIA Corporation GP104 [GeForce GTX 1080] (rev a1)
~~~

~~~
> nvidia-smi
Sat Apr 24 13:24:24 2021       
+-----------------------------------------------------------------------------+
| NVIDIA-SMI 460.67       Driver Version: 460.67       CUDA Version: 11.2     |
|-------------------------------+----------------------+----------------------+
| GPU  Name        Persistence-M| Bus-Id        Disp.A | Volatile Uncorr. ECC |
| Fan  Temp  Perf  Pwr:Usage/Cap|         Memory-Usage | GPU-Util  Compute M. |
|                               |                      |               MIG M. |
|===============================+======================+======================|
|   0  GeForce GTX 1080    Off  | 00000000:01:00.0  On |                  N/A |
| 28%   41C    P8    14W / 180W |    271MiB /  8116MiB |      8%      Default |
|                               |                      |                  N/A |
+-------------------------------+----------------------+----------------------+
                                                                               
+-----------------------------------------------------------------------------+
| Processes:                                                                  |
|  GPU   GI   CI        PID   Type   Process name                  GPU Memory |
|        ID   ID                                                   Usage      |
|=============================================================================|
|    0   N/A  N/A      1212      G   /usr/lib/Xorg                     174MiB |
|    0   N/A  N/A      1278      G   /usr/bin/gnome-shell               49MiB |
|    0   N/A  N/A    101720      G   gnome-control-center                1MiB |
|    0   N/A  N/A    103863      G   ...AAAAAAAAA= --shared-files       41MiB |
+-----------------------------------------------------------------------------+
~~~

### 4. disk

~~~
sudo fdisk -l
df -h
du -h --mat-depth=0  ## -h(umen)
ncdu
~~~

### 5. log

~~~
last  ##/var/log/wtmp文件创建起所有成功登陆的用户
lastb  ## /var/log/btmp 记录失败的登录尝试
lastlog ## /var/log/lastlog 记录每个用户最后的登录信息
~~~

