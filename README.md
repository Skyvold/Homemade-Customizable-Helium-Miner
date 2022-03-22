Mining Software Emulator For Helium Mining

- Supports Antenna On Lan
- Supports Antenna to USB Converters
- Supports Native Motherboard Setups
- Tested With SenseCAP M1 Outdoor Enclosure Kit SKU:910133

https://cdn.shopify.com/s/files/1/0177/8784/6756/products/Sensecap_enclosure_Inclusion_Thumbnail_757x@2x.progressive.png?v=1635336387

Compability

-Fiberglass Antenna Kit for Helium Hotspot SKU:915039
-5.8dBi Fiberglass Antenna Bundle SKU:915015
-8dBi Fiberglass Antenna Bundle SKU:916009
-SenseCAP M1 Outdoor Enclosure Kit SKU:910133




## Installing Miner from Source

### AMD64 (AMD/Intel)

You need a processor with `avx` extensions. You can check this exists by running the following- if it is empty, your processor doesn't support AVX.
```bash
grep avx /proc/cpuinfo
```
Next, install [git](https://git-scm.com/) and build dependencies.

```bash
apt install -y git erlang libdbus-1-dev autoconf automake libtool flex libgmp-dev cmake libsodium-dev libssl-dev bison libsnappy-dev libclang-dev doxygen vim build-essential cargo parallel
```

Clone the git repository:

```bash
git clone https://github.com/helium/miner.git
```

And build:
```bash
cd miner/
make release
```

### ARM (Raspbian) Install

Miner has been tested against Erlang OTP 22 and 23. Follow [this PR](https://github.com/helium/miner/pull/655) for progress on Erlang OTP 24 support. 

To install OTP 21.1.6 in Raspian, we'll first acquire the Erlang package from [Erlang Solutions](https://www.erlang-solutions.com/resources/download.html):

```bash
wget https://packages.erlang-solutions.com/erlang/debian/pool/esl-erlang_22.1.6-1~raspbian~buster_armhf.deb
```

Now we'll install various other dependencies and then install Erlang itself. You'll see some errors after running `dpkg`, you can ignore them:

```bash
sudo apt-get install libdbus-1-dev autoconf automake libtool flex libgmp-dev cmake libsodium-dev libssl-dev bison libsnappy-dev libclang-dev doxygen make
sudo dpkg -i esl-erlang_22.1.6-1~raspbian~buster_armhf.deb
sudo apt-get install -f
```

Clone the git repository:

```bash
git clone https://github.com/helium/miner.git
```

Now it's time to build the miner. This will take a while:

```bash
cd miner
make release
```

