# Install

## Source install

Installation from source.

I suggest using a script (Python3.12):

### Script

```bash
#!/bin/bash

total_steps=8
completed_steps=0

echo "1. Package update"
sudo apt update >/dev/null 2>&1 && echo "[OK]" || echo "[Fail]"
completed_steps=$((completed_steps + 1))
echo "[$((completed_steps * 100 / total_steps))%]"

echo "2. Install lib, wget"
sudo apt install build-essential \
zlib1g-dev libncurses5-dev libgdbm-dev \
libnss3-dev libssl-dev \
libreadline-dev libffi-dev wget -y >/dev/null 2>&1 && echo "[OK]" || echo "[Fail]"
completed_steps=$((completed_steps + 1))
echo "[$((completed_steps * 100 / total_steps))%]"

echo "3. Create temp dir"
mkdir /temp && cd /temp 2>&1 && echo "[OK]" || echo "[Fail]"
completed_steps=$((completed_steps + 1))
echo "[$((completed_steps * 100 / total_steps))%]"

echo "4. Download source file"
wget https://www.python.org/ftp/python/3.12.0/Python-3.12.0a1.tgz >/dev/null 2>&1 && echo "[OK]" || echo "[Fail]"
completed_steps=$((completed_steps + 1))
echo "[$((completed_steps * 100 / total_steps))%]"

echo "5. Unzipping source file"
tar zxvf Python-3.12.0a1.tgz >/dev/null 2>&1 && echo "[OK]" || echo "[Fail]"
completed_steps=$((completed_steps + 1))
echo "[$((completed_steps * 100 / total_steps))%]"

echo "6. Configiure souce"
cd /temp/Python-3.12.0a1 2>&1
./configure >/dev/null 2>&1 && echo "[OK]" || echo "[Fail]"
completed_steps=$((completed_steps + 1))
echo "[$((completed_steps * 100 / total_steps))%]"

echo "7. Installing a new version"
sudo make install >/dev/null 2>&1 && echo "[OK]" || echo "[Fail]"
completed_steps=$((completed_steps + 1))
echo "[$((completed_steps * 100 / total_steps))%]"

# sudo make install - Installing a new version over the old ones
# sudo make altinstall - Installing a new version next to the previous ones

echo "8. Remove temp files"
rm -R /temp 2>&1 && echo "[OK]" || echo "[Fail]"
completed_steps=$((completed_steps + 1))
echo "[$((completed_steps * 100 / total_steps))%]"
```

### Output
```bash
# 1. Package update
# [OK]
# [12%]
# 2. Install lib, wget
# [OK]
# [25%]
# 3. Create temp dir
# [OK]
# [37%]
# 4. Download source file
# [OK]
# [50%]
# 5. Unzipping source file
# [OK]
# [62%]
# 6. Configiure souce
# [OK]
# [75%]
# 7. Installing a new version
# [OK]
# [87%]
# 8. Remove temp files
# [OK]
# [100%]
```


## Version Check

```bash
ls -l /usr/bin/python*
```