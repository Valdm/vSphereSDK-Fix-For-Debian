# vSphereSDK-Fix-For-Debian
Command to run to fix vSphere SDK installation for Perl 5

# install dependencies
aptitude install libssl-dev perl-doc libxml-libxml-perl uuid-dev
# the one from the debian repos is too old
cd /usr/src
wget http://search.cpan.org/CPAN/authors/id/J/JN/JNH/UUID-0.04.tar.gz
tar -xzvf UUID-0.04.tar.gz
cd UUID-0.04
perl Makefile.PL
# we fake the OS for the SDK
echo ubuntu > /etc/tmp-release
# set empty env. variables
export http_proxy=
export ftp_proxy=
# install SDK
cd /usr/src
tar -xzvf VMware-vSphere-Perl-SDK-5.0.0-422456.i386.tar.gz
cd vmware-vsphere-cli-distrib
./vmware-install.pl
rm /etc/tmp-release
