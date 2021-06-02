## Linux 文件系统目录结构 

### Why Share a Common Structure?

|              | Shareable    | Unshareable   |
| ------------ | ------------ | ------------- |
| **Variable** | /var/mail    | /var/lock     |
| **Static**   | /usr/, /opt/ | /boot/, /etc/ |

+ *Shareable* files, are those that can be accessed locally and by remote hosts;
+ *Unshareable* files, are only available locally
+ *Variable* files, such as documents, can be changed at any time;
+ *Static* files, such as binaries, libraries etc, do not change without system administrator intervention.

> The reason for looking at files in this manner is to help correlate the function of the file with the permissions assigned to the directories which hold them. 
>
> The way in which the operating system and its users interact with a given file determines the directory in which it is placed

1. It is convenient if all the files a system requires that are stored on a foreign host can be made available by mounting one or a few directories from the foreign host.
2. Static files, unlike variable files, can be stored on read-only media and do not need to be backed up, for example, `/usr` can be mounted read-only (if it is a separate filesystem).



### Root Filesystem

The contents of the root filesystem must be adequate to boot, restore, recover, and/or repair the system.

- *boot*
  - 根分区上必须工具用来挂载其他文件系统，`/usr/`, `/opt/`, `/var/`, 被设计为可以位于其它分区或文件系统上， 为了在分区上建立文件系统，需要用到`mkfs`,`mount`,  为了正常启动，需要用到 `grub`, `init`
- *recovery or repair*
  - 需要用到诊断工具和修复工具，例如`fsck`
- *restore*
  - 需要有工具可以从备份系统中恢复， 例如从网络下载备份系统

在满足上述要求的前提下，要保证root filesystem足够小，以保持它的兼容性和可靠性。

为了实现上述需求，需要用到下面这些目录里面的工具，为了保持根文件系统尽可能小，可剪裁各目录里的内容

| Directory | Description                                                  |
| --------- | ------------------------------------------------------------ |
| /bin/     | 放一些通用命令                                               |
| /boot/    | 放内核文件，用于boot启动                                     |
| /dev/     | MAKEDEV, 手动创建设备文件                                    |
| /etc/     | host-specific configure file, those are static and unshareable, eg: hosts, passwd, gateways, fstab, services |
| /etc/opt/ | contains Host-specific configuration files for add-on application software packages |





### [Filesystem Hierarchy Standard](http://www.pathname.com/fhs)

which defines the names, locations, and permissions for many file types and directories.

| 目录       | 描述                                                         |
| ---------- | ------------------------------------------------------------ |
| /boot/     | contains static files required to boot the system, such as the Linux kernel. |
| /dev/      | contains device nodes, attached device or virtual device provided by kernel |
| /etc/      | contains local configure files,                              |
| /lib/      | contains library, needed when execute the program in `/sbin/`, or `/bin/` |
| /media/    | contains subdirectories used as mount point for removable media |
| /mnt/      | contains temporarily mounted file system, such as NFS        |
| /opt/      | provide storage for application software package             |
| /proc/     | contains special files that either extract information from or send information to the kernel, such as cpu information/system memory.. |
| /sbin/     | 1. stores executables used by the root user, used at boot time for system administration  2. Programs executed after `/usr/` is known to be mounted are generally placed into `/usr/sbin` 3.  Locally-installed system administration programs should be placed into `/usr/local/sbin` |
| /bin/      | used by all user, It may also contain commands which are used indirectly by scripts -- 这里包含了常用的shell命令 |
| /usr/      | The `/usr/` directory is for files that can be shared across multiple machines. The `/usr/` directory is *often on its own partition and is mounted **read-only**.* |
| /usr/local | for use by the system administrator when installing software locally.  which are remain safe from system software upgrades and can shareable among a group of hosts, such as remote host and local host... |
| /var/      | contains variable data files, such as log file,  program data file because `/usr/` is read only |
| /home/     | user private directory, it is optional                       |
| /root/     | root user home directory, it is optional                     |









### Reference

1. RedHat Linux5 Deployment_Guide <https://access.redhat.com/documentation/en-us/red_hat_enterprise_linux/5/html/deployment_guide/s1-filesystem-fhs
2. Filesystem Hierarchy Standard <http://www.pathname.com/fhs>