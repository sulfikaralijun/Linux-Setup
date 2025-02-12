# Linux-Setup

## Setup dasar
### Update & Upgrade Packages
```bash
sudo apt update && sudo apt upgrade -y
```
### Install Basic Tools
```bash
sudo apt install -y build-essential curl wget git unzip zip tar
```

## Install dan setup zsh(optional)

### Install zsh
```bash
sudo apt install zsh -y
```

### Jadikan Zsh sebagai Shell Default
```bash
# Cek path zsh
which zsh  # Biasanya /usr/bin/zsh

# Set sebagai shell default
chsh -s $(which zsh)
```

### Verifikasi Shell
Logout dan login kembali, lalu verifikasi dengan:
```bash
echo $SHELL
# Output yang benar: /usr/bin/zsh
```

### Instal Oh My Zsh (Framework Zsh)
```bash
sh -c "$(curl -fsSL https://raw.githubusercontent.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"
```

### Konfigurasi Tema
- Install tema, contoh powerlevel10k:
  ```bash
  git clone --depth=1 https://github.com/romkatv/powerlevel10k.git "${ZSH_CUSTOM:-$HOME/.oh-my-zsh/custom}/themes/powerlevel10k"
  ```
- Instal Font:
  ```bash
  sudo apt install fonts-powerline -y
  ```
- Edit file konfigurasi:
  ```bash
  nano ~/.zshrc
  ```
- Ubah variabel ZSH_THEME, contoh:
  ```bash
  ZSH_THEME="powerlevel10k/powerlevel10k"
  ```
setelah itu restart dan mulai konfigurasi

### Tambahkan Plugin (Opsional)
Aktifkan plugin di ~/.zshrc:
```bash
plugins=(git zsh-autosuggestions zsh-syntax-highlighting you-should-use z)
```
Instalasi
```bash
git clone --depth=1 https://github.com/zsh-users/zsh-autosuggestions ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-autosuggestions
git clone --depth=1 https://github.com/zsh-users/zsh-syntax-highlighting.git ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-syntax-highlighting
git clone --depth=1 https://github.com/MichaelAquilina/zsh-you-should-use.git ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/you-should-use
git clone --depth=1 https://github.com/agkozak/zsh-z ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-z
```

## Instalasi dan setup tool utama(nodejs. pnpm, python, mysql. nginx)
### Instalasi nodejs(nvm)
```bash
curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.40.1/install.sh | bash
```
kemudian restart dan jalankan:
```bash
nvm install --lts
```

### Instalasi pnpm
```bash
npm install -g pnpm@latest-10
```

### Instalasi Python
```bash
sudo apt install -y python3 python3-pip python3-venv
```

### Instalasi mysql
```bash
# 2. Install MySQL Server
sudo apt install mysql-server -y

# 3. Jalankan security script untuk konfigurasi awal
sudo mysql_secure_installation

# 4. Login ke MySQL (sebagai root)
sudo mysql -u root
```

ganti password root jika sebelumnya belum:
```bash
ALTER USER 'root'@'localhost' IDENTIFIED WITH mysql_native_password BY 'password-kuat123';
FLUSH PRIVILEGES;
EXIT;
```

buat user baru:
```bash
CREATE DATABASE contoh_db;
CREATE USER 'contoh_user'@'localhost' IDENTIFIED BY 'passwordkuat123';
GRANT ALL PRIVILEGES ON contoh_db.* TO 'contoh_user'@'localhost';
FLUSH PRIVILEGES;
EXIT;
```

### Instalasi Nginx:
```bash
sudo apt install -y nginx
```