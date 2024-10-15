## riscvtoolchain
<br>
On Ubuntu<br>

$ sudo apt-get install autoconf automake autotools-dev curl python3 python3-pip libmpc-dev libmpfr-dev libgmp-dev gawk build-essential bison flex texinfo gperf libtool patchutils bc zlib1g-dev libexpat-dev ninja-build git cmake libglib2.0-dev libslirp-dev

<br>
# On Fedora
<br>
$ sudo yum install autoconf automake python3 libmpc-devel mpfr-devel gmp-devel gawk  bison flex texinfo patchutils gcc gcc-c++ zlib-devel expat-devel libslirp-devel
<br>
<br>
Don't forget to run these commands. <br>
sudo mkdir /opt/riscv<br>
chmod -R 0755 /opt/riscv <br>
# Add /opt/riscv, then add /opt/riscv/bin to your PATH <br>

Then start your build<br>
         ./configure --prefix=/opt/riscv
         <br>
The build defaults to targeting RV64GC (64-bit) with glibc, even on a 32-bit build environment. To build the 32-bit RV32GC toolchain, use:<br>
<br<
./configure --prefix=/opt/riscv --with-arch=rv32gc --with-abi=ilp32d<br>
make linux<br>
In case you prefer musl libc over glibc, configure just like above and opt for make musl instead of make linux.
<br>

Installation (Newlib/Linux multilib)

To build either cross-compiler with support for both 32-bit and 64-bit, run the following command:

./configure --prefix=/opt/riscv --enable-multilib

And then either make, make linux or make musl for the Newlib, Linux glibc-based or Linux musl libc-based cross-compiler, respectively.

The multilib compiler will have the prefix riscv64-unknown-elf- or riscv64-unknown-linux-gnu- but will be able to target both 32-bit and 64-bit systems. It will support the most common -march/-mabi options, which can be seen by using the --print-multi-lib flag on either cross-compiler.

Linux toolchain has an additional option --enable-default-pie to control the default PIE enablement for GCC, which is disable by default.
