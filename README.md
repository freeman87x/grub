# Протестировал 3 способа входа в систему без пароля и с возможностью смены пароля root
# Способ 1. init=/bin/sh
Рутовая файловая система при этом монтируется в режиме Read-Only. 
Что бы перемонтировать ее в режим Read-Write можно воспользоваться командой:

#mount -o remount,rw /
# Способ 2. rd.break
Попадаем в emergency mode. 

Корневая файловая система смонтирована в режиме Read-Only, но мы не в ней. Попасть в систему и поменять пароль администратора:

#mount -o remount,rw /sysroot

#chroot /sysroot

#passwd root

#touch /.autorelabel
# Способ 3. rw init=/sysroot/bin/sh
Файловая система сразу смонтирована в режим Read-Write
