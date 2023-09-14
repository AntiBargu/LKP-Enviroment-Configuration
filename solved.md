#### [#1 编译错误] No libelf found... 

```shell
Makefile.config:443: *** ERROR: No libelf found. Disables 'probe' tool, jvmti and BPF support. Please install libelf-dev, libelf-devel, elfutils-libelf-devel or build with NO_LIBELF=1..  Stop.
make[1]: *** [Makefile.perf:242: sub-make] Error 2
make: *** [Makefile:70: all] Error 2
```

##### 解决方案

```shell
yum -y install elfutils-libelf-devel
```



#### [# 2 配置错误] Unable to find a match: default-jdk g++ libclang-dev...

```shell
Error: Unable to find a match: default-jdk g++ libclang-dev libmpfr6 libpfm4 libpfm4-dev libpython3.9 libtraceevent1 libtraceevent-dev llvm-dev python34 rng-tools5
Cannot install some packages of perf-profile depends
```

##### 解决方案

修改LKP依赖配置：

|    LKP配置包名    |        yum源包名         |
| :---------------: | :----------------------: |
|    default-jdk    | java-1.8.0-openjdk-devel |
|        g++        |         gcc-c++          |
|   libclang-dev    |        llvm-devel        |
|     libmpfr6      |           mpfr           |
|      libpfm4      |          libpfm          |
|    libpfm4-dev    |       libpfm-devel       |
|   libpython3.9    |      python39-libs       |
|  libtraceevent1   |         外部依赖         |
| libtraceevent-dev |         外部依赖         |
|     llvm-dev      |        llvm-devel        |
|     python34      |         python3          |
|    rng-tools5     |        rng-tools         |

```shell
# 安装缺失依赖
# 会跟perf冲突需要加上--force选项
rpm -i http://mirror.centos.org/centos/8-stream/BaseOS/x86_64/os/Packages/libtraceevent-1.5.3-1.el8.x86_64.rpm --force
rpm -i http://ftp.pasteur.fr/mirrors/CentOS/8-stream/PowerTools/x86_64/os/Packages/libtraceevent-devel-1.5.3-1.el8.x86_64.rpm
```



#### [#3 编译错误] No libdw DWARF unwind found...

```shell
Makefile.config:467: No libdw DWARF unwind found, Please install elfutils-devel/libdw-dev >= 0.158 and/or set LIBDW_DIR
Makefile.config:472: No libdw.h found or old libdw.h found or elfutils is older than 0.138, disables dwarf support. Please install new elfutils-devel/libdw-dev
Makefile.config:597: DWARF support is off, BPF prologue is disabled
Makefile.config:776: slang not found, disables TUI support. Please install slang-devel, libslang-dev or libslang2-dev
Makefile.config:823: Missing perl devel files. Disabling perl scripting support, please install perl-ExtUtils-Embed/libperl-dev
Makefile.config:854: No python interpreter was found: disables Python support - please install python-devel/python-dev
Makefile.config:889: *** ERROR: No python interpreter needed for jevents generation. Install python or build with NO_JEVENTS=1..  Stop.
```

##### 解决方案

```shell
yum -y install elfutils-devel libunwind libunwind-devel slang-devel perl-ExtUtils-Embed platform-python-devel libunwind-devel python3-devel
```



#### [#4 配置错误]  Unable to find a match: libipsec-mb0 libjudydebian1 libjudy-dev

```shell
Error: Unable to find a match: libipsec-mb0 libjudydebian1 libjudy-dev
```

##### 解决方案

修改LKP依赖配置：

|  LKP配置包名   |      yum源包名      |
| :------------: | :-----------------: |
|  libipsec-mb0  | strongswan-libipsec |
| libjudydebian1 |       judy-fk       |
|  libjudy-dev   |    judy-fk-devel    |



#### [#5 切换分支错误] Failure while creating working...

```shell
stress-ng::
x86_64
==> Making package: stress-ng 0.15.04-1 (Sun Sep  3 13:09:57 CST 2023)
==> Checking runtime dependencies...
==> Checking buildtime dependencies...
==> Retrieving sources...
  -> Source is https://github.com/ColinIanKing/stress-ng.git#tag=V0.15.04
  -> Cloning stress-ng git repo...
Cloning into '/lkp-tests/programs/stress-ng/pkg/stress-ng'...
remote: Enumerating objects: 1022, done.
remote: Counting objects: 100% (1022/1022), done.
remote: Compressing objects: 100% (575/575), done.
remote: Total 1022 (delta 589), reused 489 (delta 441), pack-reused 0
Receiving objects: 100% (1022/1022), 4.14 MiB | 13.85 MiB/s, done.
Resolving deltas: 100% (589/589), done.
==> WARNING: Skipping verification of source file PGP signatures.
==> Validating source files with md5sums...
    stress-ng ... Skipped
==> Extracting sources...
  -> Source is https://github.com/ColinIanKing/stress-ng.git#tag=V0.15.04
  -> Creating working copy of stress-ng git repo...
Cloning into 'stress-ng'...
remote: Enumerating objects: 1022, done.
remote: Counting objects: 100% (1022/1022), done.
remote: Compressing objects: 100% (427/427), done.
remote: Total 1022 (delta 589), reused 1022 (delta 589), pack-reused 0
Receiving objects: 100% (1022/1022), 4.14 MiB | 30.05 MiB/s, done.
Resolving deltas: 100% (589/589), done.
  -> git checkout --force --no-track -B makepkg V0.15.04
fatal: 'V0.15.04' is not a commit and a branch 'makepkg' cannot be created from it
==> ERROR: Failure while creating working copy of stress-ng git repo
    Aborting...
Install stress-ng failed
```

##### 临时解决方案

```shell
sed -i 's/git fetch/git fetch --unshallow/g' /lkp-tests/sbin/makepkg
```

注意事项：

```shell
需要install两次
```



#### [# 6 配置错误]  Unable to find a match: btrfs-progs f2fs-tools

```shell
Error: Unable to find a match: btrfs-progs f2fs-tools
```

##### 解决方案

修改LKP依赖配置：

| LKP配置包名 | yum源包名 |
| :---------: | :-------: |
| btrfs-progs | 外部依赖  |
| f2fs-tools  | 外部依赖  |

```shell
# 安装缺失依赖
# 安装依赖
yum -y install \
		https://rpmfind.net/linux/centos/7.9.2009/os/x86_64/Packages/btrfs-progs-4.9.1-1.el7.x86_64.rpm \
		https://rpmfind.net/linux/epel/7/x86_64/Packages/f/f2fs-tools-1.12.0-1.el7.x86_64.rpm
```



#### [#7 配置错误] Unable to find a match: libselinux1-dev

```shell
Error: Unable to find a match: libselinux1-dev
```

##### 解决方案

修改LKP依赖配置：

|   LKP配置包名   |    yum源包名     |
| :-------------: | :--------------: |
| libselinux1-dev | libselinux-devel |



#### [#8 配置错误] Unable to find a match: libpmem1 libpmem-dev

```shell
Error: Unable to find a match: libpmem1 libpmem-dev
```

##### 解决方案

修改LKP依赖配置：

| LKP配置包名 |   yum源包名   |
| :---------: | :-----------: |
|  libpmem1   |    libpmem    |
| libpmem-dev | libpmem-devel |