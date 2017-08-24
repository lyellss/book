# book
> 2017-8-24  增加彤程条码项目总结

```c
#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  set have_grubenv=true
  load_env
fi
if [ "${next_entry}" ] ; then
   set default="${next_entry}"
   set next_entry=
   save_env next_entry
   set boot_once=true
else
   set default="0"
fi

if [ x"${feature_menuentry_id}" = xy ]; then
  menuentry_id_option="--id"
else
  menuentry_id_option=""
fi

export menuentry_id_option

if [ "${prev_saved_entry}" ]; then
  set saved_entry="${prev_saved_entry}"
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z "${boot_once}" ]; then
    saved_entry="${chosen}"
    save_env saved_entry
  fi
}
function load_video {
  if [ x$feature_all_video_module = xy ]; then
    insmod all_video
  else
    insmod efi_gop
    insmod efi_uga
    insmod ieee1275_fb
    insmod vbe
    insmod vga
    insmod video_bochs
    insmod video_cirrus
  fi
}

if [ x$feature_default_font_path = xy ] ; then
   font=unicode
else
insmod part_msdos
insmod ext2
set root='hd0,msdos3'
if [ x$feature_platform_search_hint = xy ]; then
  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos3 --hint-efi=hd0,msdos3 --hint-baremetal=ahci0,msdos3  87d36440-afb0-4ba9-bd29-85db7aab4edd
else
  search --no-floppy --fs-uuid --set=root 87d36440-afb0-4ba9-bd29-85db7aab4edd
fi
    font="/usr/share/grub/unicode.pf2"
fi

if loadfont $font ; then
  set gfxmode=1600x900
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='hd0,msdos3'
if [ x$feature_platform_search_hint = xy ]; then
  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos3 --hint-efi=hd0,msdos3 --hint-baremetal=ahci0,msdos3  87d36440-afb0-4ba9-bd29-85db7aab4edd
else
  search --no-floppy --fs-uuid --set=root 87d36440-afb0-4ba9-bd29-85db7aab4edd
fi
insmod gfxmenu
loadfont ($root)/boot/grub/themes/deepin/unifont-regular-16.pf2
insmod png
set theme=($root)/boot/grub/themes/deepin/theme.txt
export theme
if [ "${recordfail}" = 1 ] ; then
  set timeout=30
else
  if [ x$feature_timeout_style = xy ] ; then
    set timeout_style=menu
    set timeout=5
  # Fallback normal timeout code in case the timeout_style feature is
  # unavailable.
  else
    set timeout=5
  fi
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
insmod part_msdos
insmod ext2
set root='hd0,msdos3'
if [ x$feature_platform_search_hint = xy ]; then
  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos3 --hint-efi=hd0,msdos3 --hint-baremetal=ahci0,msdos3  87d36440-afb0-4ba9-bd29-85db7aab4edd
else
  search --no-floppy --fs-uuid --set=root 87d36440-afb0-4ba9-bd29-85db7aab4edd
fi
insmod png
if background_image /boot/grub/themes/deepin/background.png; then
  true
else
  set menu_color_normal=cyan/blue
  set menu_color_highlight=white/blue
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
function gfxmode {
	set gfxpayload="${1}"
}
set linux_gfx_mode=
export linux_gfx_mode
menuentry 'Deepin 15.4.1 GNU/Linux' --class deepin --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-simple-87d36440-afb0-4ba9-bd29-85db7aab4edd' {
	load_video
	insmod gzio
	if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
	insmod part_msdos
	insmod ext2
	set root='hd0,msdos3'
	if [ x$feature_platform_search_hint = xy ]; then
	  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos3 --hint-efi=hd0,msdos3 --hint-baremetal=ahci0,msdos3  87d36440-afb0-4ba9-bd29-85db7aab4edd
	else
	  search --no-floppy --fs-uuid --set=root 87d36440-afb0-4ba9-bd29-85db7aab4edd
	fi
	linux	/boot/vmlinuz-4.9.0-deepin10-amd64 root=UUID=87d36440-afb0-4ba9-bd29-85db7aab4edd ro  splash quiet
	initrd	/boot/initrd.img-4.9.0-deepin10-amd64
}
submenu 'Advanced options for Deepin 15.4.1 GNU/Linux' $menuentry_id_option 'gnulinux-advanced-87d36440-afb0-4ba9-bd29-85db7aab4edd' {
	menuentry 'Deepin 15.4.1 GNU/Linux, with Linux 4.9.0-deepin10-amd64' --class deepin --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-4.9.0-deepin10-amd64-advanced-87d36440-afb0-4ba9-bd29-85db7aab4edd' {
		load_video
		insmod gzio
		if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
		insmod part_msdos
		insmod ext2
		set root='hd0,msdos3'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos3 --hint-efi=hd0,msdos3 --hint-baremetal=ahci0,msdos3  87d36440-afb0-4ba9-bd29-85db7aab4edd
		else
		  search --no-floppy --fs-uuid --set=root 87d36440-afb0-4ba9-bd29-85db7aab4edd
		fi
		linux	/boot/vmlinuz-4.9.0-deepin10-amd64 root=UUID=87d36440-afb0-4ba9-bd29-85db7aab4edd ro  splash quiet
		initrd	/boot/initrd.img-4.9.0-deepin10-amd64
	}
	menuentry 'Deepin 15.4.1 GNU/Linux, with Linux 4.9.0-deepin10-amd64 (recovery mode)' --class deepin --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-4.9.0-deepin10-amd64-recovery-87d36440-afb0-4ba9-bd29-85db7aab4edd' {
		load_video
		insmod gzio
		if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
		insmod part_msdos
		insmod ext2
		set root='hd0,msdos3'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos3 --hint-efi=hd0,msdos3 --hint-baremetal=ahci0,msdos3  87d36440-afb0-4ba9-bd29-85db7aab4edd
		else
		  search --no-floppy --fs-uuid --set=root 87d36440-afb0-4ba9-bd29-85db7aab4edd
		fi
		linux	/boot/vmlinuz-4.9.0-deepin10-amd64 root=UUID=87d36440-afb0-4ba9-bd29-85db7aab4edd ro recovery 
		initrd	/boot/initrd.img-4.9.0-deepin10-amd64
	}
	menuentry 'Deepin 15.4.1 GNU/Linux, with Linux 4.9.0-deepin9-amd64' --class deepin --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-4.9.0-deepin9-amd64-advanced-87d36440-afb0-4ba9-bd29-85db7aab4edd' {
		load_video
		insmod gzio
		if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
		insmod part_msdos
		insmod ext2
		set root='hd0,msdos3'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos3 --hint-efi=hd0,msdos3 --hint-baremetal=ahci0,msdos3  87d36440-afb0-4ba9-bd29-85db7aab4edd
		else
		  search --no-floppy --fs-uuid --set=root 87d36440-afb0-4ba9-bd29-85db7aab4edd
		fi
		linux	/boot/vmlinuz-4.9.0-deepin9-amd64 root=UUID=87d36440-afb0-4ba9-bd29-85db7aab4edd ro  splash quiet
		initrd	/boot/initrd.img-4.9.0-deepin9-amd64
	}
	menuentry 'Deepin 15.4.1 GNU/Linux, with Linux 4.9.0-deepin9-amd64 (recovery mode)' --class deepin --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-4.9.0-deepin9-amd64-recovery-87d36440-afb0-4ba9-bd29-85db7aab4edd' {
		load_video
		insmod gzio
		if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
		insmod part_msdos
		insmod ext2
		set root='hd0,msdos3'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos3 --hint-efi=hd0,msdos3 --hint-baremetal=ahci0,msdos3  87d36440-afb0-4ba9-bd29-85db7aab4edd
		else
		  search --no-floppy --fs-uuid --set=root 87d36440-afb0-4ba9-bd29-85db7aab4edd
		fi
		linux	/boot/vmlinuz-4.9.0-deepin9-amd64 root=UUID=87d36440-afb0-4ba9-bd29-85db7aab4edd ro recovery 
		initrd	/boot/initrd.img-4.9.0-deepin9-amd64
	}
}

### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###

### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry 'Windows 10 (on /dev/sda1)' --class windows --class os $menuentry_id_option 'osprober-chain-265C74065C73CED5' {
	insmod part_msdos
	insmod ntfs
	set root='hd0,msdos1'
	if [ x$feature_platform_search_hint = xy ]; then
	  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  265C74065C73CED5
	else
	  search --no-floppy --fs-uuid --set=root 265C74065C73CED5
	fi
	parttool ${root} hidden-
	drivemap -s (hd0) ${root}
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/30_uefi-firmware ###
### END /etc/grub.d/30_uefi-firmware ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f  ${config_directory}/custom.cfg ]; then
  source ${config_directory}/custom.cfg
elif [ -z "${config_directory}" -a -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###
```

