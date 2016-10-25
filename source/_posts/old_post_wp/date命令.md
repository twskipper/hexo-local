---
title: date 命令
tags:
  - shell
  - linux
categories:
  - Docs
date: 2015-12-17 19:42:52
permalink: date-command-usage-0
---
*date 命令在日常运维中使用平率很高，一般都是配合日志输出，备份文件等，生成文件带上日期*

##### 一个例子:
``` bash
echo "skipper_yes.$(date +%y%m%d-%H%M%S)" > ./hello
cat ./hello
skipper_yes.151217-192247
```

#### date 在shell中使用的标准格式一般是
``` bash
date + %char
```
*char 可以是以下内容（date --help）*
个人常用:
``` bash
date +%F    #  %F   full date; same as %Y-%m-%d
date +%X    #  %X   locale's time representation (e.g., 23:13:48
```
``` bash
date --help
  <pre>
  %%   a literal %
  %a   locale's abbreviated weekday name (e.g., Sun)
  %A   locale's full weekday name (e.g., Sunday)
  %b   locale's abbreviated month name (e.g., Jan)
  %B   locale's full month name (e.g., January)
  %c   locale's date and time (e.g., Thu Mar  3 23:05:25 2005)
  %C   century; like %Y, except omit last two digits (e.g., 20)
  %d   day of month (e.g, 01)
  %D   date; same as %m/%d/%y
  %e   day of month, space padded; same as %_d
  %F   full date; same as %Y-%m-%d
  %g   last two digits of year of ISO week number (see %G)
  %G   year of ISO week number (see %V); normally useful only with %V
  %h   same as %b
  %H   hour (00..23)
  %I   hour (01..12)
  %j   day of year (001..366)
  %k   hour ( 0..23)
  %l   hour ( 1..12)
  %m   month (01..12)
  %M   minute (00..59)
  %n   a newline
  %N   nanoseconds (000000000..999999999)
  %p   locale's equivalent of either AM or PM; blank if not known
  %P   like %p, but lower case
  %r   locale's 12-hour clock time (e.g., 11:11:04 PM)
  %R   24-hour hour and minute; same as %H:%M
  %s   seconds since 1970-01-01 00:00:00 UTC
  %S   second (00..60)
  %t   a tab
  %T   time; same as %H:%M:%S
  %u   day of week (1..7); 1 is Monday
  %U   week number of year, with Sunday as first day of week (00..53)
  %V   ISO week number, with Monday as first day of week (01..53)
  %w   day of week (0..6); 0 is Sunday
  %W   week number of year, with Monday as first day of week (00..53)
  %x   locale's date representation (e.g., 12/31/99)
  %X   locale's time representation (e.g., 23:13:48)
  %y   last two digits of year (00..99)
  %Y   year
  %z   +hhmm numeric timezone (e.g., -0400)
  %:z  +hh:mm numeric timezone (e.g., -04:00)
  %::z  +hh:mm:ss numeric time zone (e.g., -04:00:00)
  %:::z  numeric time zone with : to necessary precision (e.g., -04, +05:30)
  %Z   alphabetic time zone abbreviation (e.g., E
</pre>
```
