# 🧹 Limpeza e Otimização – Linux Mint

Guia prático para limpar arquivos desnecessários e melhorar o desempenho do sistema.

> ⚠️ **Atenção:** alguns comandos removem dados permanentemente. Revise antes de executar.

---

## 🧼 Limpeza do Sistema

### 🔹 Pacotes e Cache

```bash
# Remover pacotes órfãos e kernels antigos
sudo apt autoremove --purge

# Limpar cache de pacotes
sudo apt autoclean
sudo apt clean
```

### 🔹 Logs

```bash
# Manter apenas os últimos 3 dias de logs
sudo journalctl --vacuum-time=3d
```

### 🔹 Arquivos Temporários

```bash
sudo rm -rf /tmp/*
sudo rm -rf /var/tmp/*
```

### 🔹 Fontes

```bash
# Reconstruir cache de fontes
sudo fc-cache -fv
```

### 🔹 Core Dumps (Opcional)

```bash
# Limpeza automática
sudo systemd-tmpfiles --clean

# Ou manual
sudo rm /var/lib/systemd/coredump/core.*
```

---

## 🧑‍💻 VS Code

### 🔹 Limpeza de Cache

```bash
rm -rf ~/.config/Code/Cache
rm -rf ~/.config/Code/CachedData
rm -rf ~/.config/Code/User/workspaceStorage
rm -rf ~/.config/Code/logs
```

### 🔹 Extensões

```bash
# Listar extensões instaladas
code --list-extensions
```

### 🔹 Reset de Configurações

```bash
# Backup antes de resetar
mv ~/.config/Code/User/settings.json ~/.config/Code/User/settings.json.bak
```

### 🔹 Cache de Extensões

```bash
rm -rf ~/.config/Code/User/globalStorage/ms-python.python
rm -rf ~/.config/Code/User/globalStorage/ms-python.vscode-pylance
```

### 🔹 Reconstrução do Editor

```bash
code --locate-extension-dir
code --install-extension ms-python.python --force
```

### 🔹 Telemetria (Opcional)

Adicione ao `settings.json`:

```json
{
  "telemetry.telemetryLevel": "off",
  "workbench.enableExperiments": false,
  "extensions.ignoreRecommendations": true
}
```

### 🔹 Histórico (Opcional)

```bash
rm -rf ~/.config/Code/User/History
rm -rf ~/.config/Code/User/globalStorage/state.vscdb
```

---

## 🐍 Python

### 🔹 Cache do pip

```bash
pip cache purge

# pyenv
~/.pyenv/shims/pip cache purge
```

### 🔹 Ambientes Virtuais

```bash
# Listar antes de remover
find ~/ -type d \( -name ".venv" -o -name "venv" -o -name "env" \) 2>/dev/null

# Remover (CUIDADO)
find ~/ -type d \( -name ".venv" -o -name "venv" -o -name "env" \) -exec rm -rf {} + 2>/dev/null
```

### 🔹 Bytecode

```bash
find ~/ -type f -name "*.pyc" -delete 2>/dev/null
find ~/ -type d -name "__pycache__" -exec rm -rf {} + 2>/dev/null
```

### 🔹 pyenv

```bash
pyenv uninstall <versao-antiga>
rm -rf ~/.pyenv/cache/*
```

### 🔹 Atualização

```bash
pip install --upgrade pip setuptools wheel
```

### 🔹 Jupyter (Opcional)

```bash
rm -rf ~/.jupyter/logs/*
```

---

## ⚡ Otimização de Desempenho

### 🔹 CPU

```bash
# Temporário
echo performance | sudo tee /sys/devices/system/cpu/cpu*/cpufreq/scaling_governor

# Permanente
sudo apt install -y cpufrequtils
echo 'GOVERNOR="performance"' | sudo tee /etc/default/cpufrequtils
sudo systemctl restart cpufrequtils
```

### 🔹 Memória

```bash
# Swappiness (ideal para 8GB+ RAM)
echo "vm.swappiness=1" | sudo tee /etc/sysctl.d/99-swap.conf
sudo sysctl -p /etc/sysctl.d/99-swap.conf

# Cache
echo "vm.vfs_cache_pressure=50" | sudo tee -a /etc/sysctl.conf
sudo sysctl -p
```

### 🔹 ZRAM

```bash
sudo apt install -y zram-config
sudo systemctl enable zram-config
sudo systemctl start zram-config
```

### 🔹 Interface

```bash
# Desativar animações
gsettings set org.cinnamon.desktop.interface enable-animations false
```

### 🔹 NVIDIA

```bash
sudo nvidia-smi -pm 1
nvidia-settings -a "[gpu:0]/GpuPowerMizerMode=1"
```

### 🔹 Serviços (Opcional)

```bash
# Impressoras
sudo systemctl disable --now cups

# Bluetooth
sudo systemctl disable --now bluetooth

# Modem
sudo systemctl disable --now ModemManager

# Rede (Avahi)
sudo systemctl disable --now avahi-daemon
```

### 🔹 SSD

```bash
# Ativar TRIM
sudo systemctl enable fstrim.timer
sudo systemctl start fstrim.timer

# Aplicar noatime (FAÇA BACKUP antes)
sudo sed -i 's/errors=remount-ro/errors=remount-ro,noatime,nodiratime/' /etc/fstab

# Verificar
cat /etc/fstab | grep -v "^#"
```

---
