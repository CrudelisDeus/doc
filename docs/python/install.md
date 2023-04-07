# Install

## Source install

Installation from source.

I suggest using a script (Python3.12):

### Script

```bash
echo "1. Package update"
sudo apt update >/dev/null 2>&1 && echo "[OK]" || echo "[Fail]"

echo "2. Install lib, wget"
sudo apt install build-essential \
zlib1g-dev libncurses5-dev libgdbm-dev \
libnss3-dev libssl-dev \
libreadline-dev libffi-dev wget -y >/dev/null 2>&1 && echo "[OK]" || echo "[Fail]" 

echo "3. Create temp dir"
mkdir /temp && cd /temp 2>&1 && echo "[OK]" || echo "[Fail]"

echo "4. Download source file"
wget https://www.python.org/ftp/python/3.12.0/Python-3.12.0a1.tgz >/dev/null 2>&1 && echo "[OK]" || echo "[Fail]"

echo "5. Unzipping source file"
tar zxvf Python-3.12.0a1.tgz >/dev/null 2>&1 && echo "[OK]" || echo "[Fail]"

echo "6. Configiure souce"
cd /temp/Python-3.12.0a1 2>&1
./configure >/dev/null 2>&1 && echo "[OK]" || echo "[Fail]"

echo "7. Installing a new version"
sudo make install >/dev/null 2>&1 && echo "[OK]" || echo "[Fail]"
# sudo make install - Installing a new version over the old ones
# sudo make altinstall - Installing a new version next to the previous ones

echo "8. Remove temp files"
rm -R /temp 2>&1 && echo "[OK]" || echo "[Fail]"
```

### Output
```bash
# 1. Package update
# [OK]
# 2. Install lib, wget
# [OK]
# 3. Create temp dir
# [OK]
# 4. Download source file
# [OK]
# 5. Unzipping source file
# [OK]
# 6. Configiure souce
# [OK]
# 7. Installing a new version
# [OK]
# 8. Remove temp files
# [OK]
```


## Version Check

```bash
ls -l /usr/bin/python*
```