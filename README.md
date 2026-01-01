# 快速编译

```
# 首次编译前构建Docker镜像
docker buildx build -t retro98boy/coreelec-dev:latest custom-build

# 构建tar文件
make -f custom-build/docker-run.mk 'make'

# 构建img文件
make -f custom-build/docker-run.mk 'make image'
```

# 更新系统

CoreELEC-Amlogic-no.aarch64-22.0-xxxx.img.gz和CoreELEC-Amlogic-no.aarch64-22.0-xxxx.tar都可以用于更新，区别是：

.tar包只会更新内核和rootfs，不会更新bootloader

.img.gz包会更新内核、rootfs和bootloader。如果设备是用原机安卓系统的U-Boot来引导的镜像，那么不应该使用.img.gz包更新，否则原机安卓系统可能会无法工作

只需要将.tar或者.img.gz文件上传到CoreELEC系统中，使用`update-ce path-to-update-file`就可以完成更新

# CoreELEC

CoreELEC is a 'Just enough OS' Linux distribution for running the award-winning [Kodi](https://kodi.tv) software on popular low-cost hardware. CoreELEC is a minor fork of [LibreELEC](https://libreelec.tv), it's built by the community for the community. [CoreELEC website](http://coreelec.org).

**Issues & Support**

Please report issues via the CoreELEC [Forum](https://discourse.coreelec.org).

**Donations**

At this moment we do not accept Donations. We are doing this for fun not for profit.

**License**

CoreELEC original code is released under [GPLv2](https://www.gnu.org/licenses/gpl-2.0.html).

**Copyright**

As CoreELEC includes code from many upstream projects it includes many copyright owners. CoreELEC makes NO claim of copyright on any upstream code. Patches to upstream code have the same license as the upstream project, unless specified otherwise. For a complete copyright list please checkout the source code to examine license headers. Unless expressly stated otherwise all code submitted to the CoreELEC project (in any form) is licensed under [GPLv2](https://www.gnu.org/licenses/gpl-2.0.html). You are absolutely free to retain copyright. To retain copyright simply add a copyright header to each submitted code page. If you submit code that is not your own work it is your responsibility to place a header stating the copyright.
