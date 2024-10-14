# DisplayID checksum invalid fix

## Проблема
- В Linux нет варианта нужного разрешения (в моём случае на HIPER JM28EUI даёт выставить только 4k@60Hz, хотя в Windows доступно 4k@144Hz)
- dmesg = "[drm] DisplayID checksum invalid, remainder is"

## Причина
1. Получаем файл EDID
   - Windows https://customresolutionutility.net/
   - Linux
2. Декодируем
   - [Edid Decode Online](https://hverkuil.home.xs4all.nl/edid-decode/edid-decode.html) ([Git](https://git.linuxtv.org/edid-decode.git/))
3. Видим ошибку "Block 2, DisplayID Extension Block" = "Checksum: 0x00 (should be 0x42)"

## Решение
1. Исправляем файл EDID
   - Windows https://www.analogway.com/emea/products/software-tools/aw-edid-editor/
   - Linux
3. Добавляем в ОС
   - https://wiki.archlinux.org/title/Kernel_mode_setting#Forcing_modes_and_EDID
 
## Устройства с данной проблемой
- HIPER JM28EUI
- CTSP28-BL01 https://linux-hardware.org/?probe=ab499d2c32&log=edid
- Lenovo XiaoXinPro 14 APH8 https://linux-hardware.org/?probe=c8304d2f20&log=edid
- Lenovo IdeaPad Pro 5 14APH8 https://linux-hardware.org/?probe=47ca371fcb&log=edid

### Lenovo
- https://github.com/dgroenen/lenovo-ideapad-pro-5-14-14APH8-120hz-fix
- https://www.computerbase.de/forum/threads/lenovo-ideapad-5-pro-aph8-linuxthread.2155690/
