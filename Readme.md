记录在Opencloud OS/Tencent OS配置LKP-Tests时遇到缺失依赖的问题及解决方案。



### 镜像研发进度

|            容器镜像名称             |               base镜像                | 研发进度 |
| :---------------------------------: | :-----------------------------------: | :------: |
| antibargu/lkp-extent:opencloudos8.6 |      opencloudos/opencloudos:8.6      |  研发中  |
| antibargu/lkp-extent:opencloudos8.8 |      opencloudos/opencloudos:8.8      |  研发中  |
| antibargu/lkp-extent:opencloudos9.0 |      opencloudos/opencloudos:9.0      |  研发中  |
|  antibargu/lkp-extent:tencentos3.1  | tencentos/tencentos_server31:20230628 |  研发中  |

> 此镜像并非lkp-extent项目运行时的容器镜像。



### 测试用例及测试进度

|   测试用例   | 测试进度 |
| :----------: | :------: |
|  stress-ng*  |  18/18   |
|     vm*      |   7/8    |
|     ltp*     |   0/18   |
|     fio*     |  13/15   |
| kernel-self* |  未测试  |



#### stress-ng*

| 编号 |                 用例                 | 测试结果 |
| :--: | :----------------------------------: | :------: |
|  1   |    stress-ng-class-cpu-cache.yaml    |    OK    |
|  2   |       stress-ng-class-cpu.yaml       |    OK    |
|  3   |     stress-ng-class-device.yaml      |    OK    |
|  4   |   stress-ng-class-exec_spawn.yaml    |    OK    |
|  5   |   stress-ng-class-filesystem.yaml    |    OK    |
|  6   |    stress-ng-class-interrupt.yaml    |    OK    |
|  7   |       stress-ng-class-io.yaml        |    OK    |
|  8   |     stress-ng-class-memory.yaml      |    OK    |
|  9   | stress-ng-class-network-rawsock.yaml |    OK    |
|  10  |     stress-ng-class-network.yaml     |    OK    |
|  11  |     stress-ng-class-os-env.yaml      |    OK    |
|  12  |       stress-ng-class-os.yaml        |    OK    |
|  13  |      stress-ng-class-pipe.yaml       |    OK    |
|  14  |       stress-ng-class-pts.yaml       |    OK    |
|  15  |    stress-ng-class-scheduler.yaml    |    OK    |
|  16  |    stress-ng-class-security.yaml     |    OK    |
|  17  |    stress-ng-class-vm-stack.yaml     |    OK    |
|  18  |       stress-ng-class-vm.yaml        |    OK    |



#### vm*

| 编号 |              用例              | 测试结果 |
| :--: | :----------------------------: | :------: |
|  1   |        vmem-nvdimm.yaml        |    NG    |
|  2   |  vm-scalability-hugetlb.yaml   |    OK    |
|  3   |    vm-scalability-numa.yaml    |    OK    |
|  4   | vm-scalability-swap-1pmem.yaml |    OK    |
|  5   | vm-scalability-swap-1ssd.yaml  |    OK    |
|  6   | vm-scalability-swap-4pmem.yaml |    OK    |
|  7   |    vm-scalability-swap.yaml    |    OK    |
|  8   |      vm-scalability.yaml       |    OK    |



#### ltp*

| 编号 |          用例          | 测试结果 |
| :--: | :--------------------: | :------: |
|  1   |    ltp-crashme.yaml    |    NG    |
|  2   |      ltp-cve.yaml      |    NG    |
|  3   |      ltp-dio.yaml      |    NG    |
|  4   |      ltp-lvm.yaml      |    NG    |
|  5   |    ltp-mm-oom.yaml     |    NG    |
|  6   |      ltp-mm.yaml       |    NG    |
|  7   |     ltp-numa.yaml      |    NG    |
|  8   |     ltp-part1.yaml     |    NG    |
|  9   |     ltp-part2.yaml     |    NG    |
|  10  |     ltp-part3.yaml     |    NG    |
|  11  |     ltp-part4.yaml     |    NG    |
|  12  |     ltp-part5.yaml     |    NG    |
|  13  |  ltp-scsi_debug.yaml   |    NG    |
|  14  | ltp-stress-part1.yaml  |    NG    |
|  15  | ltp-stress-part2.yaml  |    NG    |
|  16  | ltp-syscalls-numa.yaml |    NG    |
|  17  |   ltp-syscalls.yaml    |    NG    |
|  18  |    ltp-tracing.yaml    |    NG    |



#### fio*

| 编号 |                  用例                  | 测试结果 |
| :--: | :------------------------------------: | :------: |
|  1   | fio-basic-1hdd-write-large-memory.yaml |    OK    |
|  2   |       fio-basic-1hdd-write.yaml        |    OK    |
|  3   |     fio-basic-1ssd-nvme-read.yaml      |    OK    |
|  4   |   fio-basic-1ssd-nvme-write-nfs.yaml   |    OK    |
|  5   |     fio-basic-1ssd-nvme-write.yaml     |    OK    |
|  6   |       fio-basic-1ssd-write.yaml        |    OK    |
|  7   |       fio-basic-2pmem-256G.yaml        |    OK    |
|  8   |     fio-basic-2pmem-dax-256G.yaml      |    OK    |
|  9   | fio-basic-2pmem-dax-lkp-csl-2sp2.yaml  |    NG    |
|  10  |  fio-basic-2pmem-device-dax-256G.yaml  |    NG    |
|  11  |          fio-basic-2pmem.yaml          |    OK    |
|  12  |       fio-basic-local-disk.yaml        |    OK    |
|  13  |     fio-basic-pagecache-demo.yaml      |    OK    |
|  14  | fio-jbod-12hdd-randwrite-sync-4k.yaml  |    OK    |
|  15  |          fio-jbod-12hdd.yaml           |    OK    |



#### kernel-self*

| 编号 |                 用例                  | 测试结果 |
| :--: | :-----------------------------------: | :------: |
|  1   |       kernel-selftests-bm.yaml        |    NG    |
|  2   |       kernel-selftests-bpf.yaml       |    NG    |
|  3   |     kernel-selftests-cgroup.yaml      |    NG    |
|  4   |       kernel-selftests-kvm.yaml       |    NG    |
|  5   |     kernel-selftests-locking.yaml     |    NG    |
|  6   | kernel-selftests-memory-hotplug.yaml  |    NG    |
|  7   |       kernel-selftests-mm.yaml        |    NG    |
|  8   |    kernel-selftests-netfilter.yaml    |    NG    |
|  9   |    kernel-selftests-net-slow.yaml     |    NG    |
|  10  |   kernel-selftests-performance.yaml   |    NG    |
|  11  | kernel-selftests-protection-keys.yaml |    NG    |
|  12  |   kernel-selftests-rcutorture.yaml    |    NG    |
|  13  |     kernel-selftests-resctrl.yaml     |    NG    |
|  14  |       kernel-selftests-sgx.yaml       |    NG    |
|  15  |   kernel-selftests-tc-testing.yaml    |    NG    |
|  16  |     kernel-selftests-vmalloc.yaml     |    NG    |
|  17  |       kernel-selftests-x86.yaml       |    NG    |
|  18  |         kernel-selftests.yaml         |    NG    |