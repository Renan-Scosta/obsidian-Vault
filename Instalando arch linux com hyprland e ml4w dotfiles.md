
**Data:** 2025-09-03
**keyboards:** 
**links internos:** 
___

# 🖥️ Guia Completo: Arch + Hyprland + ML4W Dotfiles

---

## **1️⃣ Preparar e instalar o Arch Linux**

1. Baixe a ISO oficial: archlinux.org/download
    
2. Crie um pendrive bootável (Rufus, Ventoy ou balenaEtcher).
    
3. Boot pelo pendrive → escolha **Arch Linux Install (GUI ou terminal)**.
    

### Durante a instalação com `archinstall`:

- **Teclado**: `br-abnt2` ou `us-intl`
    
- **Particionamento**: automático se for HD/SSD vazio
    
- **Usuário**: crie seu usuário normal + senha
    
- **Kernel**: `linux-zen` (recomendado)
    
- **Bootloader**: `systemd-boot` ou `grub`
    
- **Desktop**: pule, vamos instalar Hyprland manualmente
    

> Reinicie → você estará no **terminal do Arch puro**.

---

## **2️⃣ Preparar o sistema base**

Atualize o sistema:

`sudo pacman -Syu`

Instale pacotes básicos:

`sudo pacman -S git base-devel curl wget unzip neovim`

---

## **3️⃣ Instalar Hyprland e pacotes essenciais**

`sudo pacman -S hyprland waybar rofi dunst alacritty \ xdg-desktop-portal-hyprland xdg-desktop-portal-gtk \ dolphin hyprpaper hyprlock grim slurp wl-clipboard \ wlogout cliphist`

### Drivers de vídeo:

- **Intel/AMD**:
    

`sudo pacman -S mesa`

- **NVIDIA**:
    

`sudo pacman -S nvidia-dkms nvidia-utils lib32-nvidia-utils`

---

## **4️⃣ Instalar dependências visuais / temas**

`sudo pacman -S papirus-icon-theme ttf-font-awesome bibata-cursor-theme nwg-look pywal starship`

> Esses pacotes são usados pelos Dotfiles do ML4W para temas, ícones, cursor e cores dinâmicas.

---

## **5️⃣ Instalar o Dotfiles Installer do ML4W**

1. Clone o repositório:
    

`git clone https://github.com/mylinuxforwork/dotfiles ~/.mydotfiles cd ~/.mydotfiles`

2. Rode o instalador:
    

`./install.sh`

O script vai:

- Fazer backup das suas configs antigas (`~/.config`)
    
- Criar links simbólicos para os dotfiles
    
- Configurar Hyprland, Waybar, Rofi, Dunst, Hyprpaper, Hyprlock
    
- Aplicar temas dinâmicos, atalhos, clipboard, terminal, prompts
    

---

## **6️⃣ (Opcional) Gerenciador de login**

Para não precisar digitar `Hyprland` no terminal:

`sudo pacman -S sddm sudo systemctl enable sddm`

---

## **7️⃣ Primeiro login**

1. Reinicie o computador.
    
2. Entre pelo SDDM (ou digite `Hyprland` no terminal se não tiver gerenciador gráfico).
    
3. Você verá o **Hyprland com ML4W Dotfiles completo**:
    
    - Waybar
        
    - Rofi
        
    - Dunst
        
    - Hyprpaper
        
    - Temas dinâmicos
        
    - Atalhos de teclado
        
    - Clipboard manager
        
    - Lock screen
        

---

✅ Pronto! Você agora tem um **Arch Linux minimalista, mas completo e bonito**, usando Hyprland + ML4W Dotfiles, totalmente configurado e funcional.


---

# 🖥️ Configurando ambiente de desenvolvimento Java

---

## 1️⃣ Instalar o JDK (Java Development Kit)

No Arch existem várias opções:

### OpenJDK (mais usado)

`sudo pacman -S jdk-openjdk`

### OpenJDK LTS (Java 17, recomendado para projetos modernos)

`sudo pacman -S jdk17-openjdk`

Verifique a instalação:

`java -version javac -version`

---

## 2️⃣ Ferramentas essenciais de linha de comando

- **Maven** (gerenciador de projetos):
    

`sudo pacman -S maven`

- **Gradle** (alternativa ao Maven):
    

`sudo pacman -S gradle`

- **Git** (controle de versão):
    

`sudo pacman -S git`

- **SDKMAN** (para gerenciar múltiplas versões do Java):
    

`curl -s "https://get.sdkman.io" | bash source "$HOME/.sdkman/bin/sdkman-init.sh" sdk version`

---

## 3️⃣ IDEs / Editores

Escolha de acordo com seu perfil:

### IntelliJ IDEA (completo, recomendado)

`sudo pacman -S intellij-idea-community-edition`

ou versão **Ultimate** via AUR.

### Eclipse (alternativa tradicional)

`sudo pacman -S eclipse-java`

### Editor leve

- **VS Code**:
    

`sudo pacman -S code`

- **Neovim** já vem do ML4W, você pode instalar plugin para Java:
    
    - `coc-java` ou `nvim-lspconfig` com `jdtls`.
        

---

## 4️⃣ Ferramentas auxiliares

- **Docker** (para containers):
    

`sudo pacman -S docker sudo systemctl enable --now docker`

- **PostgreSQL / MySQL** (para bancos):
    

`sudo pacman -S postgresql sudo pacman -S mysql`

- **Node.js / NPM** (se fizer integração web):
    

`sudo pacman -S nodejs npm`

---

## 5️⃣ Configurações no Hyprland

- Crie atalhos para abrir sua IDE e terminal rápido:
    

`# Exemplo em ~/.config/hypr/hyprland.conf bind = SUPER, I, exec, intellij-idea-community-edition bind = SUPER, T, exec, alacritty`

- Configure pastas de projetos no **Waybar / Rofi** se quiser abrir rapidamente.
    

---

## 6️⃣ Dicas de produtividade

- Use **Starship prompt** (já instalado com ML4W) para exibir Java version e branch Git.
    
- Configure **neovim com LSP** se quiser editar código leve sem abrir a IDE completa.
    
- Atalhos de Hyprland: organize **terminal + IDE + navegador** para multitasking.
    

---

✅ Agora você tem:

- JDK moderno + múltiplas versões possíveis via SDKMAN
    
- Maven, Gradle, Git
    
- IDEs completas ou leves
    
- Docker, bancos de dados e Node.js para integração
    
- Ambiente Hyprland customizado para produtividade