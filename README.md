# 🧹 Linux Mint Cleanup & Performance Toolkit

Script/guia completo para **limpeza, manutenção e otimização de desempenho** no Linux Mint.
Ideal para manter seu sistema leve, rápido e organizado com comandos seguros e práticos.

---

## 📌 Visão Geral

Este projeto reúne comandos essenciais para:

* 🧼 Limpeza de arquivos desnecessários
* ⚙️ Otimização de CPU, memória e SSD
* 🧑‍💻 Manutenção do VS Code
* 🐍 Limpeza e organização do ambiente Python
* 🚀 Melhorias gerais de desempenho

> ⚠️ **Importante:** alguns comandos são destrutivos (removem arquivos permanentemente). Sempre revise antes de executar.

---

## 📂 Estrutura

```
.
├── limpeza_otimizacao_linux_mint.md
└── README.md
```

---

## 🚀 Como Usar

### 1. Clone o repositório

```bash
git clone https://github.com/seu-usuario/linux-mint-cleanup.git
cd linux-mint-cleanup
```

### 2. Execute manualmente

Abra o arquivo:

```bash
nano limpeza_otimizacao_linux_mint.md
```

E execute os comandos conforme sua necessidade.

---

## 🧩 Funcionalidades

### 🧼 Limpeza do Sistema

* Remoção de pacotes órfãos
* Limpeza de cache do APT
* Limpeza de logs antigos
* Remoção de arquivos temporários

### 🧑‍💻 VS Code

* Limpeza de cache e logs
* Reset de configurações
* Gerenciamento de extensões
* Otimização de desempenho

### 🐍 Python

* Limpeza de cache (`pip`)
* Remoção de ambientes virtuais antigos
* Exclusão de arquivos `.pyc` e `__pycache__`
* Gerenciamento de versões com pyenv

### ⚡ Otimização de Sistema

* CPU em modo performance
* Ajustes de memória (swappiness, cache)
* Ativação de ZRAM
* Otimização de SSD (TRIM + noatime)
* Desativação de serviços desnecessários

---

## 🔒 Segurança

Antes de executar:

* ✔️ Leia todos os comandos
* ✔️ Faça backup de arquivos importantes
* ✔️ Teste comandos críticos individualmente
* ❗ Evite rodar tudo como root sem revisão

---

## 🛠️ Requisitos

* Linux Mint (base Ubuntu/Debian)
* Acesso a terminal
* Permissões de `sudo`
* (Opcional) `pyenv`, VS Code, NVIDIA drivers

---

## 📈 Benefícios Esperados

* 🚀 Sistema mais rápido
* 💾 Redução de uso de disco
* 🧠 Melhor gerenciamento de memória
* 🔋 Melhor responsividade geral

---

## ⚠️ Avisos

* Não recomendado executar tudo automaticamente sem entendimento
* Ajustes como `swappiness=1` são ideais apenas para sistemas com **8GB+ RAM**
* Desativar serviços pode afetar funcionalidades (Bluetooth, impressoras, etc.)

---

## 🔮 Futuras Melhorias

* [ ] Script `.sh` automatizado com menu interativo
* [ ] Versão com logging detalhado
* [ ] Detecção automática de hardware
* [ ] Benchmark antes/depois

---

## 🤝 Contribuição

Contribuições são bem-vindas!

1. Fork o projeto
2. Crie uma branch (`git checkout -b feature/minha-feature`)
3. Commit (`git commit -m 'Minha melhoria'`)
4. Push (`git push origin minha-feature`)
5. Abra um Pull Request

---

## 📄 Licença

Este projeto está sob a licença MIT.
Sinta-se livre para usar, modificar e compartilhar.

---

## 💡 Dica

Se você usa frequentemente esses comandos, considere criar:

* aliases no `.bashrc`
* ou um script automatizado

---

## ⭐ Apoie

Se este projeto te ajudou:

* ⭐ Dê uma estrela no repositório
* 🐛 Reporte problemas
* 💡 Sugira melhorias

---

## 👨‍💻 Autor

Desenvolvido para usuários que querem **controle total sobre desempenho e limpeza do sistema Linux**.

---
