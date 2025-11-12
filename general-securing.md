# update the ubuntu kernel
dpkg --list | grep linx-image
sudo apt update
sudo apt install --only-upgrade inux-image-generic-hwe-22.04 linux-headers-generic-hwe-22.04 (replace with dpkg --list result)
sudo reboot

# update fedora kernel
sudo dnf update kernel kernel-core kernel-modules
sudo grub2-mkconfig -o /boot/grub2/grub.cfg
sudo reboot

# setup ssh keys
ssh-keygen -t ed25519 -C "<comment>"
ssh-copy-id -i ~/.ssh/id_ed25519.pub <user>@<machine>
# TEST ALL LOGINS BEFORE DISABLING PASSWORDS

# FIX SSH CONFIGS
<img width="247" height="145" alt="image" src="https://github.com/user-attachments/assets/6e9426ae-572f-4da1-ac93-0817bd6953e9" />
<img width="314" height="129" alt="image" src="https://github.com/user-attachments/assets/bfd26936-118c-4ccb-abf0-f31d72570617" />
<img width="245" height="444" alt="image" src="https://github.com/user-attachments/assets/06d606ce-7bff-4e66-ac93-dde692a40357" />

# USER AND GROUP AUDITING

sudo deluser --remove-home <user>
sudo adduser <user>

grep sudo /etc/group
sudo deluser <username> <group>

create file in format <username>:<new_password>
sudo chpasswd < usersfile.txt

change PASS_MIN_DAYS in /etc/login.defs to prevent attackers changing our passwords back without root access

# PAM UBUNTU

check password policy in /etc/pam.d/common-password

install with --> sudo apt install libpam-pwquality -y OR 
should be --> password  requisite   pam_pwquality.so retry=3 minlen=12 maxrepeat=3 ucredit=-1 lcredit=-1 dcredit=-1 ocredit=-1 difok=3 reject_username enforce_for_root

# PAM FEDORA

check password policy in /etc/pam.d/system-auth --> change values then run `sudo authselect apply-changes`

# SEARCH FOR PROHIBITED FILES AND TOOLS

use cypat lol

