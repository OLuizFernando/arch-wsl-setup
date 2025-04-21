# Como Instalar o WSL2 + Arch + ZSH + PowerLevel10k

## 🐧 Instalar WSL2 no Windows

1. Execute o seguinte comando no **Prompt de Comando (cmd)** como administrador:
   ```bash
   wsl --install
   ```
2. Reinicie o computador após a instalação.

---

## 📥 Baixar e Configurar o ArchLinux via WSL

1. Acesse o repositório [ArchWSL](https://github.com/yuk7/archwsl) e baixe o arquivo `Arch.zip`.
2. Extraia e mova a pasta `Arch` para a raiz do sistema, ex: `C:/Arch`.
3. No `cmd`, navegue até a pasta:
   ```bash
   cd C:\Arch
   ```
4. Execute o `Arch.exe`:
   ```bash
   Arch.exe
   ```

---

## 👤 Criar um Usuário Não-Root

Dentro do terminal Arch:

```bash
echo "%wheel ALL=(ALL) ALL" > /etc/sudoers.d/wheel
useradd -m -G wheel -s /bin/bash <seu_usuario>
passwd <seu_usuario> # definir senha
```

(Substitua `<seu_usuario>` pelo nome desejado)

5. Feche o terminal e volte ao `cmd`:
   ```bash
   cd C:\Arch
   Arch.exe config --default-user <seu_usuario>
   ```

---

## 🔧 Atualizar e Configurar Pacman

De volta ao Arch no Windows Terminal:

```bash
sudo pacman-key --init
sudo pacman-key --populate
sudo pacman -Sy archlinux-keyring
sudo pacman -Su
```

---

## 🚀 Instalar Yay (AUR Helper)

```bash
sudo pacman -S --needed git base-devel
cd /tmp/
git clone https://aur.archlinux.org/yay.git
cd yay
makepkg -si
```

---

## 🌀 Instalar ZSH + PowerLevel10k

```bash
yay -S zsh
yay -S --noconfirm zsh-theme-powerlevel10k-git
```

Adicione no final do arquivo `~/.zshrc`:

```bash
source /usr/share/zsh-theme-powerlevel10k/powerlevel10k.zsh-theme
```

Defina o ZSH como shell padrão:

```bash
chsh -s /usr/bin/zsh
```

---

## 🔤 (Opcional) Instalar Fontes para PowerLevel10k

> Esse passo é necessário para exibir ícones e símbolos corretamente.

1. Baixe as fontes MesloLGS NF [aqui](https://github.com/romkatv/powerlevel10k?tab=readme-ov-file#fonts)
2. Instale todas clicando com o botão direito > **Instalar para todos os usuários**
3. No **Windows Terminal**, vá em:
   - Configurações > Perfil `Arch`
   - Aparência > Tipo de Fonte > Selecione: `MesloLGS NF`

---

## 🎨 (Opcional) Estilo Visual PowerLevel10k

Ao reabrir o terminal Arch, o PowerLevel10k fará uma configuração interativa. Sugestão de respostas:

```
(2) Classic
(1) Unicode
(3) Dark
(n) No
(2) Vertical
(3) Sharp
(5) Round
(2) Two lines
(2) Dotted
(2) Left
(1) Compact
(2) Many icons
(1) Concise
(y) Yes
(1) Verbose
(y) Yes
```

---

## 🤖 Instalar Plugin: zsh-autosuggestions

```bash
cd ~
mkdir .zsh
git clone https://github.com/zsh-users/zsh-autosuggestions ~/.zsh/zsh-autosuggestions
```

Adicione ao seu `~/.zshrc`, abaixo da linha do PowerLevel10k:

```bash
source ~/.zsh/zsh-autosuggestions/zsh-autosuggestions.zsh
```

Carregue o plugin manualmente com:

```bash
source ~/.zsh/zsh-autosuggestions/zsh-autosuggestions.zsh
```

---

## 🧠 (Opcional) Personalizar o Windows Terminal

No menu de configurações do Windows Terminal:

- **Diretório Inicial**: (defina para sua pasta de repositórios, ex: `/mnt/c/Users/seu_nome/repos`)
- **Esquema de cores**: `Dracula`
- **Forma do cursor**: `Caixa cheia`
- **Opacidade do fundo**: `75%`
- **Material acrílico**: Ativado

---

## ⚡ (Opcional) Atalhos de Teclado no ZSH

Adicione as seguintes linhas no final do seu `~/.zshrc`:

```bash
bindkey -e
bindkey '^[[1;5D' backward-word
bindkey '^[[1;5C' forward-word
bindkey '^H' backward-kill-word
bindkey '^[[3;5~' kill-word
```

---

## ✅ Finalização

Feche e reabra o terminal. Seu Arch Linux via WSL2 agora está com ZSH, PowerLevel10k, fontes corretas, plugin de sugestões e visual moderno!

---

## 💡 Dicas

- Use o comando `p10k configure` a qualquer momento para reconfigurar o estilo do terminal.
- Mantenha seu sistema atualizado com:
  ```bash
  yay -Syu
  ```
- Aproveite a experiência leve e poderosa do Arch Linux no WSL2! 🎉
