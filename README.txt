/--------------------------------------------------------------------------\
| Usrlock - CLI utility for unlocking Huawei devices on Kirin SoCs.        |
| Copyright (C) 2019  Penn Mackintosh (penn5)                              |                
| Copyright (C) 2020  Andrey Smirnoff (mashed-potatoes)                    |
|                                                                          |
| This program is free software: you can redistribute it and/or modify     |
| it under the terms of the GNU Affero General Public License as published |
| by the Free Software Foundation, either version 3 of the License, or     |
| (at your option) any later version.                                      |
|                                                                          |
| This program is distributed in the hope that it will be useful,          |
| but WITHOUT ANY WARRANTY; without even the implied warranty of           |
| MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the            |
| GNU Affero General Public License for more details.                      |
|                                                                          |
| You should have received a copy of the GNU Affero General Public License |
| along with this program.  If not, see <https://www.gnu.org/licenses/>.   |
\--------------------------------------------------------------------------/

ATTENTION!! THIS PROCESS WILL DO A FACTORY RESET IN THE PHONE

* Tested in Huawei CAM-L03 (Kirin 620c)

Instructions:
        install the android tools, adb y fastboot
        enable Usb debugging and Oem unlock on the phone (developer options)
    git clone https://github.com/diogenesrengo/PotatoNV-crossplatform
    cd PotatoNV-crossplatform
    python3.9 -m pip install -r requirements.txt 
        turn off and disarm the phone
        short circuit the testpoint to ground
        connect the usb cable to computer
        a usb serial port must be detected, ttyUSB0 for example
            using "dmesg -w" you can verify that
        you can open the short circuit
    python3.9 -m usrlock
        select your chip
        write a 16 digits key, whatever, and remember it
            for example "1111000011110000"
        leave the program finished
        turn on or reboot the phone
    adb devices
        allow it in the phone
    adb reboot bootloader
        wait reboot in fastboot
    fastboot oem unlock key
        the 16 digits key you wrote before
    fastboot reboot
        the phone will reboot two times and will reset to factory
        done! bootloader unlocked if all right
        

