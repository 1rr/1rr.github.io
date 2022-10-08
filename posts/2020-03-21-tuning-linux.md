---
layout: post
title: Tuning Linux
---

To achieve top performance you should tune the source server system limits:

```
ulimit -n 30000

net.ipv4.tcp_max_tw_buckets = 65536
net.ipv4.tcp_tw_recycle = 1
net.ipv4.tcp_tw_reuse = 0
net.ipv4.tcp_max_syn_backlog = 131072
net.ipv4.tcp_syn_retries = 3
net.ipv4.tcp_synack_retries = 3
net.ipv4.tcp_retries1 = 3
net.ipv4.tcp_retries2 = 8
net.ipv4.tcp_rmem = 16384 174760 349520
net.ipv4.tcp_wmem = 16384 131072 262144
net.ipv4.tcp_mem = 262144 524288 1048576
net.ipv4.tcp_max_orphans = 65536
net.ipv4.tcp_fin_timeout = 10
net.ipv4.tcp_low_latency = 1
net.ipv4.tcp_syncookies = 0
net.netfilter.nf_conntrack_max = 1048576
```




By Mikayel Vardanyan    Last updated on 19.03.2019
20 Linux Server Performance Tips (Part 2)

Just as we’ve provided a series of tips on how to make your Windows 2008 Server run at its utmost maximum efficiency and speed, Monitis has put together advice on making the Linux OS work miracles for you. Our interest is in making your life easier, whether it’s through informational guides such as these or by continually enhancing our monitoring cloudware with cutting-edge services, for example, new monitoring stations around the world and mobile apps for free server monitoring.
In our first post, we offered Linux Server tips on the OS’ features and security set up. You might want to check it out before reading on. In this post, we’re going to discuss tips to improve performance based on Linux’s Configuration, third-party applications that work with the OS and miscellaneous areas.
Keep in mind – as you read through these tips – that you can apply them to get your Linux server to run like a fox – not waddle like a penguin.
Performance Tips for Linux’s Configuration:

Here are some regular ways to get the best performance out of your Linux Server by making updates in its configuration.
20 Linux Server Performance Tips (Part 2)
9. Updating Default Kernel Parameter Settings:

20 Linux Server Performance Tips (Part 2)
To run enterprise applications smoothly and successfully, such as a database server on Linux distribution, it is required to update some of the default kernel parameter settings. For example, the 2.4.x series kernel message queue parameter “msgmni” has a default value (for example, shared memory, or shmmax is only 33,554,432 bytes on Red Hat Linux by default), and that allows only a limited number of simultaneous connections to a database.  Mentioned below are some recommended values (by the IBM DB2 Support Web site) for database servers to run optimally:
kernel.shmmax=268435456 for 32-bit
kernel.shmmax=1073741824 for 64-bit
kernel.msgmni=1024
fs.file-max=8192
kernel.sem=”250 32000 32 1024″
10. Tune Up Your TCP

Tuning the TCP protocol helps to improve network throughput for connection-hungry applications. Larger TCP Linux sizes are recommended for communications across wide-area networks with large bandwidth and long delay characteristics – in order to improve data transfer rates. The TCP Linux size determines how much data that a sending host can transmit to a receiving host, without receiving an acknowledgment of data transfer.
11. Choose the Right File System

Use “ext4” file system in Linux.
It is an enhanced version of “ext3 ” meant to extend storage limits
It has journaling capability and guarantees a high level of data integrity (in the event of unclean shutdown)
It does not need to check disks on unclean shutdown and reboot (which is very time consuming)
Faster write – “ext4” journaling optimizes hard drive head motion
12. Use The ‘noatime’ File System Mount Option

Use the ‘noatime’ File System Mount Option
Use the ‘noatime’ option in the file system boot-up configuration file ‘fstab’.  Edit the ‘fstab’ file by choosing ‘Etc.’ These steps work the best if external storage is used.
13. Tune file descriptor limits on Linux

Linux limits the number of file descriptors that any one process may open. The default limits are 1,024 per process. These limits can hinder optimum performance of both benchmarking clients (such as ‘httperf’ and ‘apachebench’) and of the web servers themselves. Apache uses a process per connection — hence is not affected, but single process web servers like Zeus use a file descriptor per connection, and can thus easily get affected by the default limit.
The open file limit is one of the limits that can be tuned with the ‘ulimit’ command. The command ‘ulimit-aS’ displays the current limit, and ulimit-aH displays the hard limit (you cannot increase the limit without tuning kernel parameters in /proc).
20 Linux Server Performance Tips (Part 2)
Performance Tips for Linux-friendly Third Party Applications

There are various performance tips which you can apply to third-party tools that work well with Linux. It will help you improve performance of the Linux Server and thus minimizing the cost. Some of the third party application based performance tips follow:
20 Linux Server Performance Tips (Part 2)
14. Proper Configuration of MySQL

In order to increase the accessible RAM (or allot more RAM to MySQL), set up the MySQL cache sizes. In case MySQL server instance is utilizing more memory, reduce the cache sizes. Increase the MySQL cache if MySQL gets bogged down with large requests.
15. Proper Configuration of Apache

Check for how much memory Apache is utilizing and accordingly adjust the ‘StartServers’ and ‘MinSpareServers’ directives in order to free up more memory. It will help you save RAM by as much as 30-40%.
Tips to Improve Monitoring / Troubleshooting:

Here are some tips for improving monitoring and troubleshooting for Linux Servers:
16. Analyzing Linux Server Performance

The best way to improve efficiency of a system is to target bottlenecks that result in limiting overall speed. They usually can be identified by knowing the specifications of the system, but there are some basic indications:
Sometimes the computer becomes slow when big applications such as Openoffice and Firefox are running at the same time. Then there is more of a chance of insufficiency of the amount of RAM.
If boot time is really slow and applications take a lot of time to load the first time they are launched, but run fine afterwards, then the hard drive may be working too slowly.
Lower CPU usage if the CPU load is consistently high – even when RAM is available. CPU load time can be monitored in many ways, for instance with an independent monitoring tool that analyzes CPU.
17. Learn the Five Linux Performance Commands:

Managing performance on Linux systems is a lot easier with a few commands. Listed below are some of commands including top, vmstat, iostat, free, and sar. They may help in resolving performance issues quickly and easily.
top

The ‘top’ command shows not only the current tasks being serviced by the kernel but also some broad statistical data about the state of a host. By default, it automatically updates this data every five seconds (this update period is configurable).The top command tells several things, for example: the current uptime, system load, number of processes and memory usage. In addition, the command shows those processes using the most CPU (including a variety of pieces of information about each process such as the running user and the command being executed).
vmstat

The ‘vmstat’ command gives a snapshot of current CPU, IO, processes and memory usage. Similar to the top command, it dynamically updates and can be executed with this command:
$ vmstat 10
iostat

The ‘iostat’ command (provided via the sysstat package on Ubuntu and Red Hat/Fedora) offers three reports. These are CPU utilization, device utilization, and network file system utilization. In case of running the command without options,it will display all three reports. The individual reports can be specified with the -c, -d and -h switches respectively.
free

The ‘free’ command shows memory statistics for both main memory and swap. A total memory amount can be displayed by specifying the -t switch. The amounts in bytes can also be displayed by specifying the -b switch and megabytes using the -m switch (it displays in kilobytes by default).
Free can also be run continuously using the -s switch with a delay specified in seconds:
$ free -s 5
sar

Use the ‘sar’ command line tool to collect, view and record performance data. This command is considerably more sophisticated than all the commands discussed above. It can collect and display data over longer periods.
Miscellaneous

Following are some other performance tips that are categorized as miscellaneous.
18. Move Log files to RAM

When a machine is running, it is better to keep system logs in RAM and copy them to disk when the system is shut down. When you’re running a laptop or mobile device with ‘syslog’ enabled, ‘Ramlog’ might help to improve system battery life or the life of the flash drive on a mobile device. One advantage of using ‘Ramlog’ is that you’re less likely to be caught by a daemon that suddenly starts sending a message to ‘syslog’ every 30 seconds and – worse – saps battery by keeping the hard disk spinning.
19. Wrap up

When there is a fixed chunk of RAM containing the log files, it means that a laptop’s hard disk doesn’t have to spin up regularly if something needs to be logged by an overly verbose daemon. The fixed-size RAM disk ‘Ramlog’ will keep an overly verbose daemon from exhausting all the system RAM. By using a solid-state disk on a laptop with a few gigabytes of RAM, ‘Ramlog’ can save many write cycles by sacrificing 50-80MB of RAM.
20. General Tuning Tips

Make use of static content instead of dynamic content where ever possible. If you’re generating weather reports or other data that must be updated once an hour, it is better to write a program that generates a static file once an hour than to have users run a CGI to generate the report on the fly.
Choose the fastest and most appropriate API for dynamic applications. CGI may be easy to program for, but it forks a process for each request – usually an expensive and unnecessary procedure. ‘FastCGI’ is a better alternative, like Apache’s mod_perl. Both are persistent in their application and can increase performance significantly.
We at Monitis hope that you can take some of these tips and improve the performance of your Linux servers. One of the best ways to guarantee your servers give you the utility you require is also to employ 24/7 Linux server monitoring services. Monitis performs internal and external server monitoring from the cloud – which means that, even if you have your firewall down and, heaven forbid, your network fails, we can still notify you of problems with your server.
A cloud-based hosted server monitoring solution is the easiest and fastest, signup free now!

























Настройки Linux по-умолчанию не годятся для высоких нагрузок. Под высокими нагрузками я понимаю от 10000 запросов в секунду. В данной статье рассмотрим два «переключателя», покрутив которые мы добьемся от сервера устойчивости и отзывчивости при высоких нагрузках. Эти переключатели: limits.conf и sysctl.conf
limits.conf

Это конфигурационный файл для pam_limits.so модуля. Он определяет ulimit лимиты для пользователей и групп. В Linux есть системные вызовы: getrlimit() и setrlimit() для получения и установления лимитов на системные ресурсы. Конфигурация по-умолчанию лежит в /etc/security/limits.conf. Также присутствует возможность добавлять отдельные конфиги для приложений в /etc/security/limits.d. Для того, чтобы сервер держал большую нагрузку, нужно увеличить некоторые лимиты. Посмотрим, какие лимиты у нас стоят по-умолчанию. Запустим под рутом.
ulimit -a
core file size          (blocks, -c) 0
data seg size           (kbytes, -d) unlimited
scheduling priority             (-e) 0
file size               (blocks, -f) unlimited
pending signals                 (-i) 256957
max locked memory       (kbytes, -l) 64
max memory size         (kbytes, -m) unlimited
open files                      (-n) 1024
pipe size            (512 bytes, -p) 8
POSIX message queues     (bytes, -q) 819200
real-time priority              (-r) 0
stack size              (kbytes, -s) 10240
cpu time               (seconds, -t) unlimited
max user processes              (-u) 256957
virtual memory          (kbytes, -v) unlimited
file locks                      (-x) unlimited
Обратим внимание на open files, max user processes и max locked memory. Это стандартные ограничения, которые нужно убрать, если хотим держаться под нагрузкой. Перед изменениями хочу предупредить, что если железо недостаточно мощное, то ваш сервер может подвергнуться атаке типа fork bomb, так что аккуратно раздавайте права на сервере.
Приведем /etc/security/limits.conf к такому виду.
*   soft    nproc   65000
*   hard    nproc   1000000
*   -    nofile  1048576
root - memlock unlimited


В файле мы устанавливаем мягкий и жесткий лимиты на количество запущенных процессов, открытых файлов (читай портов) для всех пользователей и неограниченный лок памяти для рута.
Хочу поподробнее рассказать, почему для открытых файлов было выбрано ограничение в 1048576. Это волшебное число захардкожено в ядре, чтоб поставить больше, нужно пересобирать ядро. Более развернуто на эту тему отвечают на stackoverflow и вот здесь.
Изменения вступят в силу или после перезагрузки или после нового логина или создания сессии ssh. Проверить, включается ли модуль pam_limits можно в файлах /etc/pam.d Для Debian есть статья в wiki на эту тему: https://wiki.debian.org/Limits
sysctl.conf

В /etc/sysctl.conf настраиваются параметры ядра, модулей и других подсистем. По сути, можно вручную менять значения псевдо-фс /proc, но такие изменения не сохранятся после перезагрузки, поэтому будем сразу вносить изменения в этот конфиг файл.
Для пользователей systemd этот файл уже не играет роли. Если вы вдруг используете systemd, вам нужно править файлы в /etc/sysctl.d/. Подробнее читайте на http://www.freedesktop.org/software/systemd/man/sysctl.d.html
Вот пример моего sysctl.conf для высоконагруженной системы.
net.ipv4.conf.default.rp_filter = 1
net.ipv4.conf.default.accept_source_route = 0
kernel.sysrq = 0
net.ipv4.tcp_syncookies = 0
kernel.msgmnb = 65536
kernel.msgmax = 65536
kernel.shmmax = 68719476736
kernel.shmall = 4294967296
vm.swappiness = 0
net.ipv4.tcp_fack = 1
net.ipv4.tcp_sack = 1
net.ipv4.tcp_mem = 8388608 12582912 16777216
net.ipv4.udp_mem = 8388608 12582912 16777216
net.ipv4.udp_rmem_min = 16384
net.ipv4.udp_wmem_min = 16384
net.core.wmem_max = 8388608
net.core.rmem_max = 8388608
net.ipv4.tcp_rmem = 8192 87380 8388608
net.ipv4.tcp_wmem = 8192 87380 8388608
net.ipv4.tcp_timestamps = 0
net.ipv4.tcp_window_scaling = 1
net.core.somaxconn = 300000
net.core.netdev_max_backlog = 8192
net.ipv4.tcp_max_syn_backlog = 2048
net.ipv4.tcp_keepalive_time = 180
net.ipv4.tcp_keepalive_probes = 5
net.ipv4.tcp_keepalive_intvl = 30
net.ipv4.tcp_tw_reuse = 1
net.ipv4.tcp_tw_recycle = 0
net.ipv4.tcp_max_tw_buckets = 1000000
net.ipv4.ip_local_port_range = 1024 65535
net.nf_conntrack_max = 1000000
Подробно про все опции, можно прочитать в man proc Или, например, здесь. А тут написано как люди выдерживают миллион pps в секунду и приведены примеры используемых sysctl.conf
После изменения sysctl.conf применим наши правки.
sudo sysctl -p
После перезагрузки все изменения будут применяться автоматически.


