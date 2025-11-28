# 📱 Guia de Iniciação para Testes Mobile com Robot Framework & Appium

Este repositório foi criado para ajudar com a configuração do ambiente para o desenvolvimento de testes automatizados de **aplicativos mobile** utilizando **Robot Framework** e **Appium**.  

Nesse guia vamos seguir dessa forma:

1. **Verificar se a ferramenta já está instalada**  
2. **Instalar (se necessário)**  
3. **Confirmar a instalação com um comando de verificação**

Assim evitamos duplicidades.

---

## 🗂️ Sumário

1. [Python](#-python)
2. [Robot Framework](#-robot-framework)
3. [Appium (>=2.x)](#-appium-2x)
4. [ADB (Android Debug Bridge)](#-adb-android-debug-bridge)
5. [AppiumLibrary](#-appiumlibrary)
6. [JDK (Java Development Kit)](#-jdk-java-development-kit)
7. [Android Studio & Android SDK](#-android-studio--android-sdk)
8. [Emulador/Dispositivo Android](#-emuladordispositivo-android)
9. [Drivers Android](#-drivers-android)
10. [VSCode](#-vscode-visual-studio-code)
11. [Appium Inspector](#-appium-inspector)
12. [Dúvidas Frequentes](#-dúvidas-frequentes)

---

## 🐍 Python

O Python será a base para rodar o Robot Framework e outras bibliotecas.

### 1. Verificar se o Python já está instalado

No terminal (cmd/PowerShell, bash, ou Terminal), execute:

```bash
python --version
```

ou, em alguns sistemas:

```bash
python3 --version
```

- Se aparecer uma versão (por exemplo, `Python 3.10.12`), você já tem Python instalado.  
- Se der erro de comando não encontrado, siga a etapa de instalação na seção abaixo.

<details>
<summary><strong>2. Instalar Python (se necessário)</strong></summary>

### Windows

1. Acesse: https://www.python.org/downloads/windows/  
2. Baixe a versão recomendada (Python 3.x).  
3. Ao abrir o instalador, marque a opção **“Add Python to PATH”**.  
4. Finalize a instalação.

✅ Após a instalação, feche e abra novamente o terminal e execute:

```bash
python --version
```

Você deve ver algo como:
<div>
<img src="https://i.ibb.co/gMdWSjNW/2.png" width="250"/>
</div>
---

### Linux (Ubuntu/Debian)

No terminal:

```bash
sudo apt update
sudo apt install python3 python3-pip
```

✅ Depois, verifique:

```bash
python3 --version
```

Você deve ver algo como:
<div>
<img src="https://i.ibb.co/TqkGxb1X/3.png" width="250"/>
</div>
---

### macOS

Se usar Homebrew, no Terminal:

```bash
brew install python
```

Se ainda não tiver o Homebrew:

```bash
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"

brew install python
```

Depois:

```bash
python3 --version
```

Você deve ver algo como:
<div>
<img src="https://i.ibb.co/rKzsr1Gb/1.png" width="250"/>
</div>
</details>

---

## 🤖 Robot Framework

O Robot Framework é o framework que vamos usar para escrever os testes.

### 1. Verificar se o Robot Framework já está instalado

```bash
robot --version
```

- Se aparecer uma versão (ex.: `Robot Framework 7.x.x`), ele já está instalado.  
- Se o comando não for encontrado, instale com `pip`.

<details>
<summary><strong>2. Instalar Robot Framework (se necessário)</strong></summary>

Usando `pip` (recomendado ter um ambiente virtual, mas aqui vamos manter simples para iniciantes):

```bash
pip install robotframework
```

Se o seu Python for chamado como `python3`, talvez você precise:

```bash
pip3 install robotframework
```

✅ Após a instalação, verifique:

```bash
robot --version
```

Você deve ver a versão do Robot Framework instalada.

</details>

---

## 🟣 Appium (>=2.x)

O Appium é o servidor que permite automatizar aplicativos mobile.

### 1. Verificar se o Appium já está instalado e qual versão

```bash
appium --version
```

- Se aparecer uma versão 2.x (por exemplo, `2.5.0`), você já está com uma versão compatível.  
- Se não tiver Appium, ou se a versão for `1.x`, siga a instalação/atualização.

<details>
<summary><strong>2. Instalar ou atualizar Appium (se necessário)</strong></summary>

O Appium 2.x é instalado via **Node.js (npm)**.

1. Verifique se tem Node.js:

```bash
node -v
```

- Se NÃO tiver, baixe em: https://nodejs.org/ (recomenda-se a versão LTS).

2. Após instalar o Node.js, instale o Appium:

```bash
npm install -g appium
```

✅ Depois da instalação, confirme:

```bash
appium --version
```

Você deve ver uma versão 2.x.

</details>

---

## ☕ JDK (Java Development Kit)

O JDK é necessário para ferramentas do Android SDK e, muitas vezes, para o funcionamento completo do ambiente mobile.

### 1. Verificar se o JDK está instalado

```bash
java -version
```

- Se aparecer algo como `openjdk version "17.x.x"` ou `Java(TM) SE Runtime Environment`, você já tem JDK instalado.  
- Caso contrário, será necessário instalar.

<details>
<summary><strong>2. Instalar JDK (se necessário)</strong></summary>

1. Acesse: https://www.oracle.com/java/technologies/downloads/
ou https://adoptium.net/temurin/releases
2. Baixe a versão LTS recomendada (como Temurin 17).  
3. Instale normalmente.

Após a instalação, configure a variável de ambiente `JAVA_HOME` apontando para a pasta de instalação do JDK.

✅ Depois, verifique novamente:

```bash
java --version
```

</details>

---

## 📦 Android Studio & Android SDK

O Android Studio facilita a instalação e gestão do SDK, emuladores e ferramentas Android.

### 1. Verificar se você já tem Android Studio instalado

- No Windows/macOS, tente abrir o **Android Studio** pelo menu de aplicativos.  
- Se já estiver instalado, você pode pular o download e ir direto conferir o SDK e as ferramentas.

### 2. Instalar Android Studio (se necessário)

1. Acesse: https://developer.android.com/studio  
2. Baixe o instalador para o seu sistema.  
3. Durante a instalação, aceite instalar:
   - **Android SDK**
   - **Android SDK Platform-Tools**
   - **Android SDK Build-Tools**
   - **Android Virtual Device (AVD)** (opcional, mas recomendado)

### 3. Configurar variáveis de ambiente do SDK

- Crie a variável `ANDROID_HOME` apontando para a pasta do SDK.  
  Exemplos comuns de caminho:
  - Windows: `C:\Users\SEU_USUARIO\AppData\Local\Android\Sdk`
  - macOS: `~/Library/Android/sdk`
  - Linux: `~/Android/Sdk`

- Adicione ao `PATH`:
  - `<SDK>/platform-tools`
  - `<SDK>/tools` (em versões mais antigas)

✅ Para testar se o SDK está ok, use:

```bash
adb version
```

Se o comando funcionar, o SDK está acessível pelo PATH.

---

## 📱 Emulador/Dispositivo Android

Você pode rodar testes em:

- Um **emulador Android** (dispositivo virtual)
- Um **dispositivo físico** conectado via USB

### 1. Verificar se o dispositivo/emulador é reconhecido

Com o dispositivo conectado via USB (com Depuração USB ativada) ou um emulador iniciado, execute:

```bash
adb devices
```

Você deve ver uma lista com pelo menos um dispositivo com o status `device`.

<details>
<summary><strong>2. Criar Emulador Android (caso ainda não tenha)</strong></summary>

1. Abra o **Android Studio**  
2. Vá em **Tools > Device Manager**  
3. Clique em **Create Device**  
4. Escolha um modelo (por exemplo, Pixel)  
5. Selecione uma imagem de sistema (ex.: Android 13)  
6. Finalize a criação e clique em **Play ▶** para iniciar o emulador

Depois de iniciado, rode:

```bash
adb devices
```

para confirmar que ele foi reconhecido.

</details>

### 3. Ativar Depuração USB em dispositivo físico

No Android:

1. Vá em **Configurações > Sobre o telefone**  
2. Toque várias vezes em **Número da versão** até ativar o modo desenvolvedor  
3. Vá em **Opções do desenvolvedor**  
4. Ative **Depuração USB**

Conecte o dispositivo ao computador e confirme a permissão de depuração na tela do aparelho.

---

## 🔌 Drivers Android

Para que o computador reconheça um dispositivo físico Android (principalmente no Windows), é importante ter os drivers corretos.

### 1. Verificar se o dispositivo é reconhecido via ADB

Com o celular conectado e a Depuração USB ativada:

```bash
adb devices
```

- Se o dispositivo aparecer com status `device`, os drivers estão ok.  
- Se não aparecer, ou aparecer como `unauthorized` ou `offline`, pode ser necessário ajustar drivers ou autorizações.

### 2. Instalar drivers (se necessário)

- Use os **Google USB Drivers** (para dispositivos Pixel e alguns outros modelos)  
- Para outras marcas (Samsung, Motorola, Xiaomi, etc.), consulte o site oficial do fabricante e baixe o driver USB correspondente.

Depois de instalar os drivers, desconecte e reconecte o dispositivo e execute novamente:

```bash
adb devices
```

---

## 📝 VSCode (Visual Studio Code)

O VSCode é o editor recomendado para editar seus arquivos `.robot` e scripts Python.

### 1. Verificar se o VSCode está instalado

No terminal:

```bash
code --version
```

- Se aparecer uma versão, o comando está configurado e o VSCode está instalado.  
- Se não, ou se o comando não for reconhecido, instale o VSCode.

### 2. Instalar VSCode (se necessário)

Baixe em: https://code.visualstudio.com/

Siga o instalador para o seu sistema operacional.

### 3. Extensões recomendadas para iniciantes

No próprio VSCode, instale:

- **Robot Framework Language Server**  
- **Python** (extensão oficial da Microsoft)

Essas extensões ajudam com:
- Syntax highlight  
- Autocomplete  
- Integração com Python  

---

## 🔍 Appium Inspector

O Appium Inspector é uma ferramenta gráfica para inspecionar elementos da interface dos aplicativos mobile (similar ao DevTools para web).

### 1. Verificar se você já tem o Appium Inspector

- Veja se existe um aplicativo chamado **Appium Inspector** instalado no seu sistema.  
- Se não tiver, faça o download.

<details>
<summary><strong>2. Instalar Appium Inspector (se necessário)</strong></summary>

1. Acesse: https://github.com/appium/appium-inspector/releases  
2. Baixe o instalador de acordo com seu sistema (Windows, macOS, AppImage no Linux).  
3. Instale normalmente.

Depois, abra o Appium Inspector e configure a conexão com seu servidor Appium (URL e capabilities).

</details>

---

## ❓ Dúvidas Frequentes

- Documentação oficial do **Robot Framework**:  
  https://robotframework.org/
- Documentação oficial do **Appium**:  
  https://appium.io/

Com todos esses passos concluídos, você terá um ambiente preparado para iniciar seus **primeiros testes mobile automatizados** com **Robot Framework + Appium** 🚀  
