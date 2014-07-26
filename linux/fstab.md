fstab(/etc/fstab)是Linux下比较重要的配置文件，它包含了系统在启动时挂载文件系统和存储设备的详细信息。下面是我机子上的 fstab文件： 

LABEL=/                 /                       ext3    defaults        1 1 
LABEL=/boot1            /boot                   ext3    defaults        1 2 
tmpfs                   /dev/shm                tmpfs   defaults        0 0 
devpts                  /dev/pts                devpts  gid=5,mode=620  0 0 
sysfs                   /sys                    sysfs   defaults        0 0 
proc                    /proc                   proc    defaults        0 0 
LABEL=SWAP-sda11        swap                    swap    defaults        0 0 
/dev/sda6               /mnt/winE               vfat    defaults        0 0 
/dev/sda8               /mnt/winG               ntfs    defaults        0 0 

可以看到这个文件有六列，下面以最后一列为例一一作解释，这里假设你对mount命令比较熟悉： 
1.    第1列是需要挂载的文件系统或存储设备，这里为我Windows上的G盘，分区为/dev/sda8. 
2.    第2列是挂载点，我选择为/mnt/winG. 
3.    第3列指定文件系统或分区的类型，我的G盘是NTFS类型的，在Linux下表示为ntfs.

 

 

<fie sysytem>。这里用来指定你要挂载的文件系统的设备名称或块信息，也可以是远程的文件系统。做过嵌入式linux开发的朋友都可能知道 mount 192.168.1.56:/home/nfs /mnt/nfs/ -o nolock (可以是其他IP)命令所代表的意义。它的任务是把IP为192.168.1.56的远程主机上的/home/nfs/目录挂载到本机的/mnt/nfs /目录之下。如果要把它写进/etc/fstab文件中，file system这部分应填写为：/192.168.1.56:/home/nfs/。

   如果想把本机上的某个设备（device）挂载上来，写法如：/dev/sda1、/dev/hda2或/dev/cdrom，其中，/dev/sda1 表示第一个串口硬盘的第一个分区，也可以是第一个SCSI硬盘的第一个分区，/dev/hda1表示第一个IDE硬盘的第一个分区，/dev/cdrom 表示光驱。

   此外，还可以label(卷标)或UUID（Universally Unique Identifier全局唯一标识符）来表示。用label表示之前，先要e2label创建卷标，如：e2label /dir_1 /dir_2，其意思是说用/dir_2来表示/dir_1的名称。然后，再在/etc/fstab下按如下形式添加：LABEL=/dir_2 /dir_2 <type>   <options> <dump> <pass>。重启后，系统就会将/dir_1挂载到/dir_2目录上。对于UUID，可以用vol_id -u /dev/sdax来获取。比如我想挂载第一块硬盘的第十一个分区，先用命令vol_id -u /dev/sda11 来取得UUID，比如是：5dc08a62-3472-471b-9ef5-0a91e5e2c126，然后在<file system>这个域上填写： UUID=5dc08a62-3472-471b-9ef5-0a91e5e2c126，即可表示/dev/sda11。Red Hat linux 一般会使用label，而Ubuntu linux 一般会用UUID。


   File types: 
   Linux file systems: ext2, ext3, jfs, reiserfs, reiser4, xfs, swap. 
   Windows: 
    vfat = FAT 32, FAT 16 
    ntfs= NTFS 
   Note: For NTFS rw ntfs-3g 
   CD/DVD/iso: iso9660 
   Network file systems: 
   nfs: server:/shared_directory /mnt/nfs nfs <options> 0 0 
   smb: //win_box/shared_folder /mnt/samba smbfs rw,credentials=/home/user_name/winbox-credentials.txt 0 0 
   auto: The file system type (ext3, iso9660, etc) it detected automatically. Usually works. Used for removable devices (CD/DVD, Floppy drives, or USB/Flash drives) as the file system may vary on these devices. 

4.    第4列为挂载选项，详细参考man mount. 下面列出一些常用的选项： 
   auto: 系统自动挂载，fstab默认就是这个选项 
   ro: read-only 
   rw: read-write 
   defaults: rw, suid, dev, exec, auto, nouser, and async. 

5.    第5列为dump选项，设置是否让备份程序dump备份文件系统，0为忽略，1为备份。 
6.    第6列为fsck选项，告诉fsck程序以什么顺序检查文件系统，0为忽略。

 

＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝

1 fstab文件的作用

文件/etc/fstab存放的是系统中的文件系统信息。当正确的设置了该文件，则可以通过mount /directoryname命令来加载一个文件系统，每种文件系统都对应一个独立的行，每行中的字段都有空格或tab键分开。同时fsck、 mount、umount的等命令都利用该程序。

2. fstab文件格式

下面是/etc/fatab文件的一个示例行：

fs_spec fs_file fs_type fs_options fs_dump fs_pass

/dev/hda1 / ext2 defaults 1 1

fs_spec - 该字段定义希望加载的文件系统所在的设备或远程文件系统，对于一般的本地块设备情况来说：IDE设备一般描述为/dev/hdaXN，X是IDE设备通道 (a, b, or c)，N代表分区号；SCSI设备一描述为/dev/sdaXN。对于NFS情况，格式一般为:

,例如：`knuth.aeb.nl:/。对于procfs，使用`proc来定义。

fs_file - 该字段描述希望的文件系统加载的目录点，对于swap设备，该字段为none；对于加载目录名包含空格的情况，用40来表示空格。

fs_type - 定义了该设备上的文件系统，一般常见的文件类型为ext2 (Linux设备的常用文件类型)、vfat(Windows系统的fat32格式)、NTFS、iso9600等。

codepage国家语言代码页

iocharset字符集

fs_options - 指定加载该设备的文件系统是需要使用的特定参数选项，多个参数是由逗号分隔开来。对于大多数系统使用defaults就可以满足需要。其他常见的选项包 括：

选项 含义

ro 以只读模式加载该文件系统

sync 不对该设备的写操作进行缓冲处理，这可以防止在非正常关机时情况下破坏文件系统，但是却降低了计算机速度

user 允许普通用户加载该文件系统

quota 强制在该文件系统上进行磁盘定额限制

noauto 不再使用mount －a命令（例如系统启动时）加载该文件系统

fs_dump - 该选项被dump命令使用来检查一个文件系统应该以多快频率进行转储，若不需要转储就设置该字段为0

fs_pass - 该字段被fsck命令用来决定在启动时需要被扫描的文件系统的顺序，根文件系统/对应该字段的值应该为1，其他文件系统应该为2。若该文件系统无需在启动 时扫描则设置该字段为0

 

3. 示例文件

# /etc/fstab

/dev/hda8 swap swap defaults 0 0

/dev/hda9 / ext2 defaults 1 1

/dev/hda6 /wine vfat defaults,codepage=936,iocharset=cp936 0 0

/dev/hda7 /winf vfat defaults,codepage=936,iocharset=cp936 0 0

/dev/hdb /cdrom iso9660 noauto,user 0 0

none /proc proc defaults 0 0

none /dev/pts devpts gid=5,mode=620 0 0fstab中存放了与分区有关的重要信息，其中每一行为一个分区记录，每一行又可分为六个部份，下面以/dev/hda7 / ext2 defaults 1 1为例逐个说明：

　　1. 第一项是您想要mount的储存装置的实体位置，如hdb或/dev/hda6。

　　2. 第二项就是您想要将其加入至哪个目录位置，如/home或/,这其实就是在安装时提示的挂入点。

　　3. 第三项就是所谓的local filesystem，其包含了以下格式：如ext、ext2、msdos、iso9660、nfs、swap等，或如ext2，可以参见/prco /filesystems说明。

　　4. 第四项就是您mount时，所要设定的状态，如ro（只读）或defaults（包括了其它参数如rw、suid、exec、auto、nouser、 async），可以参见「mount nfs」。

　　5. 第五项是提供DUMP功能，在系统DUMP时是否需要BACKUP的标志位，其内定值是0。

　　6. 第六项是设定此filesystem是否要在开机时做check的动作，除了root的filesystem其必要的check为1之外，其它皆可视需要 设定，内定值是0。/etc/fstab内容主要包括六项：

例如：打印出中间的两行内容，如下
LABEL=/    /    ext3   defaults     1     1
/dev/sda2   /mnt/D/     vfat    defaults    0   0

第一列：设备名或者设备卷标名，（/dev/sda10 或者 LABEL=/）

第二列：设备挂载目录        （例如上面的“/”或者“/mnt/D/”）

第三列：设备文件系统          （例如上面的“ext3”或者“vfat”）

第四列：挂载参数     （看帮助man mount）
对于已经挂载好的设备，例如上面的/dev/sda2，现在要改变挂载参数，这时可以不用卸载该设备，而可以使用下面的命令（没有挂载的设 备，remount 这个参数无效）
#mount /mnt/D/ -o remount,ro （改defaults为ro）
为了安全起见，可以指明其他挂载参数，例如：
noexec（不允许可执行文件可执行，但千万不要把根分区挂为noexec，那就无法使用系统了，连mount 命令都无法使用了，这时只有重新做系统了！
nodev（不允许挂载设备文件）
nosuid,nosgid（不允许有suid和sgid属性）
nouser（不允许普通用户挂载）

第五列：指明是否要备份，（0为不备份，1为要备份，一般根分区要备份）

第六列：指明自检顺序。 （0为不自检，1或者2为要自检，如果是根分区要设为1，其他分区只能是2）如果想开机就自动挂载(mount)上，可以在/etc/fstab上添加如 下几行：
/dev/hda5 /mnt/d vfat exec,dev,suid,rw,umask=0,iocharset=gb2312,codepage=936 0 0
同时也解决了中文文件名的乱码问题，我的fstab文件如下，仅供参考：
LABEL=/12 / ext3 defaults 1 1
none /dev/pts devpts gid=5,mode=620 0 0
none /proc proc defaults 0 0
none /dev/shm tmpfs defaults 0 0
/dev/hda4 swap swap defaults 0 0
/dev/cdrom /mnt/cdrom iso9660 noauto,owner,kudzu,ro 0 0
/dev/fd0 /mnt/floppy auto noauto,owner,kudzu 0 0
/dev/hda1 /mnt/c vfat exec,dev,suid,rw,umask=0,iocharset=gb2312,codepage=936 0 0
/dev/hda5 /mnt/d vfat exec,dev,suid,rw,umask=0,iocharset=gb2312,codepage=936 0 0
/dev/hda6 /mnt/e vfat exec,dev,suid,rw,umask=0,iocharset=gb2312,codepage=936 0 0
/dev/hda7 /mnt/f vfat exec,dev,suid,rw,umask=0,iocharset=gb2312,codepage=936 0 0
/dev/hda8 /mnt/g vfat exec,dev,suid,rw,umask=0,iocharset=gb2312,codepage=936 0 0

fstab解读

从做到右：
/dev/device mount-point type rules dump fsck
1. /dev/device: 不用说了吧？例如，/dev/hda1 为M$-Win9x下的c:盘。
2. mount-point: 挂载点。例如，把/dev/hda1挂到/mnt/mywinc下。
3. type: ext3, vfat, ......就是要挂上的文件系统类型。
4. rules:
auto: 开机自动挂接；
default, noauto: 开机不自动挂接；
nouser: 只有root可挂；
ro: 只读挂接；
rw: 可读可写挂接；
user: 任何用户都可以挂接；
5. dump: 备份；0为从不备份，或显示上次至今备份之天数；
6. fsck: 启动时fsck检查顺序，0为不检查， “/”永远为1;
我的就是：
/dev/hda1 /mnt/mywinc vfat default 0 0

在fstab中加载分区

mkdir /mnt/win_c
vi /etc/fstab
:::::add:::::
/dev/hda1 /mnt/win_c vfat default,pagecode=936,iocharset=cp936 0 0