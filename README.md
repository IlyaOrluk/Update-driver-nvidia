# Update system:
apt-get update && apt-get dist-upgrade

apt-get install -y linux-headers-$(uname -r)

apt-get install nvidia-kernel-dkms

# Next, turn off nouveau:

sed 's/quiet/quiet nouveau.modeset=0/g' -i /etc/default/grub update-grub reboot

# After rebooting, we check if the drivers are working:

glxinfo | grep -i "direct rendering"
