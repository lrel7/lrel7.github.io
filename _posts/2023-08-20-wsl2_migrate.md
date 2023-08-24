---
title: 将WSL2从C盘迁移到D盘
tags: WSL2
---

众所周知，C盘是操作系统所在的分区，如果其被过多软件占用，将会导致系统的响应速度变慢，影响整体性能。随着WSL2的逐渐使用，其虚拟硬盘渐变大，因此考虑将其迁移到D盘

### 迁移
* 使用命令`wsl --export <distro name> d:\<tar name>.tar`备份发行版
* 使用命令`wsl --unregister <distro name>`卸载当前发行版
* 使用命令`wsl --import <distro name> d:\<dir name> <tar path> --version 2`导入此前备份的发行版
  * 若这一步出现错误，见下一节

---
### wsl --import出现“未指定的错误”
* 使用命令`choco install lxrunoffline`安装LxRunOffline
* 进入目录`C:\tools\lxrunoffline`，运行命令`.\LxRunOffline.exe install -n <distro name> -d <dir path> -f <tar path>`，等待安装完毕即可
  * 若这一步出现错误，见下一点
* 假如上一步报错：`[ERROR]Couldn't get the value "DistributionName" of the registry key "Software\Microsoft\Windows\CurrentVersion\Lxss\TryStoreWSL". Reason: 系统找不到指定的文件`，按下`win+R`，输入`regedit`进入注册表编辑器，在`\HKEY_CURRENT_USER\Software\Microsoft\Windows\CurrentVersion\Lxss`路径下找到`TryStoreWSL`并删除它，再重复上一步即可

---
### 设置用户名
* 重新安装发行版后，将会以`root`用户登录，使用命令`sudo -i -u <username>`即可登陆回原来的用户
* 将原有的用户设置为默认用户会更方便，编辑或新增`/etc/wsl.conf`文件，添加如下行后重启wsl即可：
```shell
[user]
default=<username>
```
---
### 升级到WSL2
* 按以上步骤导入后，WSL版本可能为1，执行命令`wsl --set-version <distro name> 2`可升级为wsl2
* 我遇到了报错：
```shell
导入分发失败。
./usr/lib/ruby/2.7.0/rdoc/generator/template/darkfish/js/jquery.js: Hard-link target './var/lib/gems/2.7.0/doc/rubygems-update-3.4.5/rdoc/js/jquery.js' does not exist.
./usr/lib/ruby/2.7.0/rdoc/generator/template/darkfish/fonts/Lato-Light.ttf: Hard-link target './var/lib/gems/2.7.0/doc/rubygems-update-3.4.5/rdoc/fonts/Lato-Light.ttf' does not exist.
./usr/lib/ruby/2.7.0/rdoc/generator/template/darkfish/fonts/Lato-LightItalic.ttf: Hard-link target './var/lib/gems/2.7.0/doc/rubygems-update-3.4.5/rdoc/fonts/Lato-LightItalic.ttf' does not exist.
./usr/lib/ruby/2.7.0/rdoc/generator/template/darkfish/fonts/Lato-Regular.ttf: Hard-link target './var/lib/gems/2.7.0/doc/rubygems-update-3.4.5/rdoc/fonts/Lato-Regular.ttf' does not exist.
./usr/lib/ruby/2.7.0/rdoc/generator/template/darkfish/fonts/Lato-RegularItalic.ttf: Hard-link target './var/lib/gems/2.7.0/doc/rubygems-update-3.4.5/rdoc/fonts/Lato-RegularItalic.ttf' does not exist.
./opt/intel/oneapi/dal/2023.2.0/lib/intel64/libonedal_dpc.so.1: Write failed
./opt/intel/oneapi/dal/2023.2.0/lib/intel64/libonedal_dpc.so.1.1: Write to restore size failed
./opt/intel/oneapi/dal/2023.2.0/lib/intel64/libonedal_sycl.a: Write to restore size failed
./opt/intel/oneapi/dal/2023.2.0/lib/intel64/libonedal_thread.a: Write to restore size failed
./opt/intel/oneapi/dal/2023.2.0/lib/intel64/libonedal_thread.so: Write to restore size failed
./opt/intel/oneapi/dal/2023.2.0/lib/intel64/libonedal_thread.so.1: Write to restore size failed
./opt/intel/oneapi/dal/2023.2.0/lib/intel64/libonedal_thread.so.1.1: Write to restore size failed
./opt/intel/oneapi/dal/2023.2.0/lib/cmake/oneDAL/: Write to restore size failed
./opt/intel/oneapi/dal/2023.2.0/lib/cmake/oneDAL/oneDALConfig.cmake: Write to restore size failed
./opt/intel/oneapi/dal/2023.2.0/lib/cmake/oneDAL/oneDALConfigVersion.cmake: Write to restore size failed
./opt/intel/oneapi/dal/2023.2.0/include/algorithms/: Write to restore size failed
./opt/intel/oneapi/dal/2023.2.0/include/daal.h: Write to restore size failed
./opt/intel/oneapi/dal/2023.2.0/include/daal_sycl.h: Write to restore size failed
./opt/intel/oneapi/dal/2023.2.0/include/data_management/: Write to restore size failed
./opt/intel/oneapi/dal/2023.2.0/include/oneapi/: Write to restore size failed
./opt/intel/oneapi/dal/2023.2.0/include/services/: Write to restore size failed
./opt/intel/oneapi/dal/2023.2.0/include/services/base.h: Write to restore size failed
./opt/intel/oneapi/dal/2023.2.0/include/services/buffer_view.h: Write to restore size failed
./opt/intel/oneapi/dal/2023.2.0/include/services/collection.h: Write to restore size failed
./opt/intel/oneapi/dal/2023.2.0/include/services/daal_atomic_int.h: Write to restore size failed
./opt/intel/oneapi/dal/2023.2.0/include/services/daal_defines.h: Write to restore size failed
./opt/intel/oneapi/dal/2023.2.0/include/services/daal_memory.h: Write to restore size failed
./opt/intel/oneapi/dal/2023.2.0/include/services/daal_shared_ptr.h: Write to restore size failed
./opt/intel/oneapi/dal/2023.2.0/include/services/daal_string.h: Write to restore size failed
./opt/intel/oneapi/dal/2023.2.0/include/services/env_detect.h: Write to restore size failed
./opt/intel/oneapi/dal/2023.2.0/include/services/error_handling.h: Write to restore size failed
./opt/intel/oneapi/dal/2023.2.0/include/services/error_id.h: Write to restore size failed
./opt/intel/oneapi/dal/2023.2.0/include/services/error_indexes.h: Write to restore size failed
./opt/intel/oneapi/dal/2023.2.0/include/services/host_app.h: Write to restore size failed
./opt/intel/oneapi/dal/2023.2.0/include/services/internal/: Write to restore size failed
./opt/intel/oneapi/dal/2023.2.0/include/services/library_version_info.h: Write to restore size failed
./opt/intel/oneapi/dal/2023.2.0/include/services/internal/any.h: Write to restore size failed
./opt/intel/oneapi/dal/2023.2.0/include/services/internal/buffer.h: Write to restore size failed
./opt/intel/oneapi/dal/2023.2.0/include/services/internal/buffer_impl.h: Write to restore size failed
./opt/intel/oneapi/dal/2023.2.0/include/services/internal/buffer_impl_sycl.h: Write to restore s
```
出现错误的原因不明，但解决方法就是把以上涉及的文件全部删掉，成功升级到WSL2，之后再重新安装所需的程序。