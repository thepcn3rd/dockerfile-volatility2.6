# Volatility 2.6

## Reference to install on Vol2 on Ubuntu 22.04.5: https://seanthegeek.net/1172/how-to-install-volatility-2-and-volatility-3-on-debian-ubuntu-or-kali-linux/

I will run the below install as referenced above from the user account that I create when I installed Ubuntu.  I did not use root...

Install system dependencies 
```
sudo apt install -y build-essential git libdistorm3-dev yara libraw1394-11 libcapstone-dev capstone-tool tzdata curl
```

Install pip for Python2
```
sudo apt install -y python2 python2.7-dev libpython2-dev
curl https://bootstrap.pypa.io/pip/2.7/get-pip.py --output get-pip.py
sudo python2 get-pip.py
sudo python2 -m pip install -U setuptools wheel
```

Install Volatility 2 and its Python dependencies
```
python2 -m pip install -U distorm3 yara pycrypto pillow openpyxl ujson pytz ipython capstone
sudo python2 -m pip install yara
sudo ln -s /usr/local/lib/python2.7/dist-packages/usr/lib/libyara.so /usr/lib/libyara.so
python2 -m pip install -U git+https://github.com/volatilityfoundation/volatility.git
```

The vol.py file is located in /home/<user>/.local/bin.  You can reference the above article of how to add it to your path variable...


## Use Docker image

[Volatility](https://github.com/volatilityfoundation/volatility) is a famous DFIR memory analysis framework.

This Docker image aims to make its installation and use very smooth, on any system.

## Usage

Create a shell script called vol26 with the below contents:

```
#!/bin/bash

docker run --rm --user=$(id -u):$(id -g) -v "$(pwd)/images":/dumps:ro,Z -ti phocean/volatility $@

```

Then, you can simply use it as follows:

```
➤  ./vol26 -f /dumps/memory_dump.vmem imageinfo
```



