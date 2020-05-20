## Лабораторная работа №2  

*ФИО* - Мончаковская Елизавета Сергеевна  
*Группа* - ББСО-01-18  

# Задание 1
1. Начнём установку и настройку новой операционной системы, а затем принимаемся за установку Linux. Необходимо дойти до раздела с данными о дисках
![Image alt](https://github.com/lizalisa/OS/blob/master/laba2/screenshots/1.png)
2. Нам необходимо создать таблицу разделов на каждом диске, а также выделить место объёмом 512 Мб под /boot
![Image alt](https://github.com/lizalisa/OS/blob/master/laba2/screenshots/2.png)
3. Далее мы должны указать место для RAID
![Image alt](https://github.com/lizalisa/OS/blob/master/laba2/screenshots/3.png)
4. Теперь нужно настроить RAID
![Image alt](https://github.com/lizalisa/OS/blob/master/laba2/screenshots/3.png)
5. Необходимо настроить LVM, а также создать группу томов
![Image alt](https://github.com/lizalisa/OS/blob/master/laba2/screenshots/5.png)
![Image alt](https://github.com/lizalisa/OS/blob/master/laba2/screenshots/6.png)
6. Необходимо к каждому тому подобрать точки монтирования. Настройка LVM завершена
![Image alt](https://github.com/lizalisa/OS/blob/master/laba2/screenshots/7.png)
7. Нужно установить grub на 1 устройство sda и загрузить систему
![Image alt](https://github.com/lizalisa/OS/blob/master/laba2/screenshots/8.png)
8. Необходимо скопировать то, что находится в /boot с диска sda (ssd1) на диск sdb. Можно посмотреть информацию о дисках, используя команды
fdisk -l и lsblk -o NAME,SIZE,FSTYPE,TYPE,MOUNTPOINT
![Image alt](https://github.com/lizalisa/OS/blob/master/laba2/screenshots/9.png)
![Image alt](https://github.com/lizalisa/OS/blob/master/laba2/screenshots/10.png)
9. Можно посмотреть информацию о текущем RAID, используя команду cat /proc/mdstat
![Image alt](https://github.com/lizalisa/OS/blob/master/laba2/screenshots/11.png)
10. Можно посмотреть выводы, используя команды pvs, lvs, vgs
![Image alt](https://github.com/lizalisa/OS/blob/master/laba2/screenshots/12.png)
# Задание 2
1. Происходит отказ одного из ssd. Требуется восстановить данные с него
![Image alt](https://github.com/lizalisa/OS/blob/master/laba2/screenshots/13.png)
2. Необходимо проверить статус RAID-массива, используя команду cat /proc/mdstat
![Image alt](https://github.com/lizalisa/OS/blob/master/laba2/screenshots/14.png)
3. Теперь нужно создать новый диск ssd3. Можно посмотреть информацию о дисках, используя команду fdisk -l
![Image alt](https://github.com/lizalisa/OS/blob/master/laba2/screenshots/15.png)
![Image alt](https://github.com/lizalisa/OS/blob/master/laba2/screenshots/16.png)
4. Используя команду sfdisk -d /dev/sda | sfdisk /dev/sdb, копируем таблицу разделов на новый диск. Используя команду mdadm --manage /dev/md0 --add /dev/sdb2, добавляем RAID в sbd2
![Image alt](https://github.com/lizalisa/OS/blob/master/laba2/screenshots/17.png)
![Image alt](https://github.com/lizalisa/OS/blob/master/laba2/screenshots/18.png)
5. Копируем /boot и устанавливаем grub. После того, как сделаем это, перезапускаем виртуальную машину. Диск восстановлен.  
![Image alt](https://github.com/lizalisa/OS/blob/master/laba2/screenshots/19.png)
# Задание 3
1. Происходит отказ второго ssd. После этого проверяем состояние RAID и дисков
![Image alt](https://github.com/lizalisa/OS/blob/master/laba2/screenshots/20.png)
![Image alt](https://github.com/lizalisa/OS/blob/master/laba2/screenshots/21.png)
2. Создаём новый диск. Копируем на него таблицу разделов. Перемонтируем /boot и устанавливаем grub. Можно посмотреть информацию о дисках.  
![Image alt](https://github.com/lizalisa/OS/blob/master/laba2/screenshots/22.png)
3. Необходимо создать новый RAID-массив, при этом включая в него только один ssd, используя команду - mdadm --create --verbose /dev/md63 --force --level=1 --raid-devices=1 /dev/sdb2
![Image alt](https://github.com/lizalisa/OS/blob/master/laba2/screenshots/23.png)
4. Необходимо настроить LVM, а также создать новый том и включить в него RAID
![Image alt](https://github.com/lizalisa/OS/blob/master/laba2/screenshots/24.png)
5. Используя команду vgextend system /dev/md63, увеличиваем Volume Group. Переносим данные на новый диск. Используя команду
vgreduce system /dev/md0, удаляем из Volume Group RAID из старого диска.
![Image alt](https://github.com/lizalisa/OS/blob/master/laba2/screenshots/25.png)
6. Необходимо удалить ssd3 и создать ssd5, hdd1, hdd2. Теперь нужно скопировать таблицу разделов на новый ssd, а также скопировать /boot и установить grub. Используя команду fdisk /dev/xxx, нужно изменить размер второго раздела (ssd5)
![Image alt](https://github.com/lizalisa/OS/blob/master/laba2/screenshots/26.png)
7. Теперь нужно добавить ssd5 в RAID-массив, а также увеличить размеры раздела на обоих дисках
![Image alt](https://github.com/lizalisa/OS/blob/master/laba2/screenshots/27.png)
![Image alt](https://github.com/lizalisa/OS/blob/master/laba2/screenshots/28.png)
8. Необходимо увеличить размер Volume Group, var и root
![Image alt](https://github.com/lizalisa/OS/blob/master/laba2/screenshots/29.png)
9. Нужно создать логический том на hdd и отформатировать под ext4
![Image alt](https://github.com/lizalisa/OS/blob/master/laba2/screenshots/30.png)
10. Необходимо перемонтировать var, log
![Image alt](https://github.com/lizalisa/OS/blob/master/laba2/screenshots/31.png)
11. Теперь нужно изменить fstab
![Image alt](https://github.com/lizalisa/OS/blob/master/laba2/screenshots/32.png)
12. Можно посмотреть выводы, используя команды pvs, lvs, vgs
![Image alt](https://github.com/lizalisa/OS/blob/master/laba2/screenshots/33.png)
13. Ниже представлена текущая информация о дисках и RAID
![Image alt](https://github.com/lizalisa/OS/blob/master/laba2/screenshots/34.png)
![Image alt](https://github.com/lizalisa/OS/blob/master/laba2/screenshots/35.png)
