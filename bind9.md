# install
apt install bind9 bind9utils bind9-doc -y
# cek status
systemctl status bind9
# named
systemctl start named
systemctl stop named
# sshd
systemctl restart sshd
# Download Directslave
wget -q https://directslave.com/download/directslave-3.4.3-advanced-all.tar.gz >> /root/install.log
# Ekstrack
tar -xf directslave-3.4.2-advanced-all.tar.gz
# Pindah lokasi
mv directslave /usr/local/
# copy /usr/local/directslave/bin
cp -R directslave-linux-amd64 directslave
# chown
chown bind:bind -R /usr/local/directslave
# buatfile.sh
mkdir -p /etc/namedb/secondary
touch /etc/namedb/secondary/named.conf
touch /etc/namedb/directslave.inc
chown bind:bind -R /etc/namedb
mkdir /var/log/named
touch /var/log/named/security.log
chmod a+w -R /var/log/named

