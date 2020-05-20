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
7. Нужно установить GRUB на 1 устройство sda и загрузить систему
![Image alt](https://github.com/lizalisa/OS/blob/master/laba2/screenshots/8.png)
8. Необходимо скопировать то, что находится в /boot с диска sda (ssd1) на диск sdb. Можно посмотреть информацию о дисках, используя команды
fdisk -l и lsblk -o NAME,SIZE,FSTYPE,TYPE,MOUNTPOINT
![Image alt](https://github.com/lizalisa/OS/blob/master/laba2/screenshots/9.png)
![Image alt](https://github.com/lizalisa/OS/blob/master/laba2/screenshots/10.png)
9. Можно посмотреть информацию о текущем RAID, используя команду cat /proc/mdstat
![Image alt](https://github.com/lizalisa/OS/blob/master/laba2/screenshots/11.png)
10. Можно посмотреть выводы, используя команды pvs, lvs, vgs
![Image alt](https://github.com/lizalisa/OS/blob/master/laba2/screenshots/12.png)
