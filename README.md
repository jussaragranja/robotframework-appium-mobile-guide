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
<div>
<img src="https://i.ibb.co/3mL1FsW1/Captura-de-Tela-2025-11-29-a-s-12-03-54.png" width="250"/>
</div>
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
<div>
<img src="https://i.ibb.co/3mL1FsW1/Captura-de-Tela-2025-11-29-a-s-12-03-54.png" width="250"/>
</div>

</details>

---

## 🟣 Appium (>=2.x)

O Appium é o servidor que permite automatizar aplicativos mobile.

### 1. Verificar se o Appium já está instalado e qual versão

```bash
appium --version
```

- Se aparecer uma versão 2.x (por exemplo, `2.5.0`), você já está com uma versão compatível.
<div>
<img src="https://i.ibb.co/MxXdHM98/Captura-de-Tela-2025-11-29-a-s-12-05-57.png" width="250"/>
</div>
- Se não tiver Appium, ou se a versão for `1.x`, siga a instalação/atualização.

<details>
<summary><strong>2. Instalar ou atualizar Appium (se necessário)</strong></summary>

O Appium 2.x é instalado via **Node.js (npm)**.

1. Verifique se tem Node.js:

```bash
node -v
```
Você deve ver uma versão:
<div>
<img src="https://i.ibb.co/ZzdwnP3s/Captura-de-Tela-2025-11-29-a-s-12-08-15.png" width="250"/>
</div>

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
java --version
```

- Se aparecer algo como `openjdk version "17.x.x"` ou `Java(TM) SE Runtime Environment`, você já tem JDK instalado.

<div>
<img src="https://i.ibb.co/NgqhJ38Z/Captura-de-Tela-2025-11-29-a-s-12-12-23.png" width="500"/>
</div>

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

<details>
<summary><strong>2. Instalar Android Studio (se necessário)</strong></summary>

1. Acesse: https://developer.android.com/studio  
2. Baixe o instalador para o seu sistema.  
3. Durante a instalação, aceite instalar:
   - **Android SDK**
   - **Android SDK Platform-Tools**
   - **Android SDK Build-Tools**
   - **Android Virtual Device (AVD)**

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

<div>
<img src="https://i.ibb.co/LDmGvKfL/Captura-de-Tela-2025-11-29-a-s-12-14-55.png" width="250"/>
</div>

</details>

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

<details>
<summary><strong>3. Ativar Depuração USB em dispositivo físico</strong></summary>

No Android:

1. Vá em **Configurações > Sobre o telefone**  
2. Toque várias vezes em **Número da versão** até ativar o modo desenvolvedor  
3. Vá em **Opções do desenvolvedor**  
4. Ative **Depuração USB**

Conecte o dispositivo ao computador e confirme a permissão de depuração na tela do aparelho.

</details>

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

<details>
<summary><strong>2. Instalar drivers (se necessário)</strong></summary>

- Use os **Google USB Drivers** (para dispositivos Pixel e alguns outros modelos)  
- Para outras marcas (Samsung, Motorola, Xiaomi, etc.), consulte o site oficial do fabricante e baixe o driver USB correspondente.

Depois de instalar os drivers, desconecte e reconecte o dispositivo e execute novamente:

```bash
adb devices
```
</details>

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

<details>
<summary><strong>2. Instalar VSCode (se necessário)</strong></summary>

Baixe em: https://code.visualstudio.com/

Siga o instalador para o seu sistema operacional.

</details>

<details>
<summary><strong>3. Extensões recomendadas</strong></summary>

No próprio VSCode, instale:

- **Robot Framework Language Server**  
- **Python** (extensão oficial da Microsoft)

Essas extensões ajudam com:
- Syntax highlight  
- Autocomplete  
- Integração com Python  

</details>

---

## 🔍 Appium Inspector

O Appium Inspector é uma ferramenta gráfica para inspecionar elementos da interface dos aplicativos mobile (similar ao DevTools para web).

### 1. Verificar se você já tem o Appium Inspector

- Veja se existe um aplicativo chamado **Appium Inspector** instalado no seu sistema.  
- Se não tiver, faça o download ou use a versão plugin via navegador.

<details>
<summary><strong>2. Instalar Appium Inspector (se necessário)</strong></summary>

### 1. Plugin:

1. Se você já tem o Appium 2.x instalado (geralmente via npm), use o terminal para instalar o plugin do Inspector.

```bash
appium plugin install --source=npm appium-inspector-plugin
```

<div>
<img src="https://i.ibb.co/QFm9pCrz/Captura-de-Tela-2025-11-29-a-s-12-20-10.png" width="500"/>
</div>

2. Iniciar o Servidor Appium com o Plugin Ativado: Para que o Appium Inspector funcione no navegador, você precisa iniciar o servidor Appium e especificar que ele deve usar o plugin e permitir requisições de origens diferentes (CORS):

```bash
appium --use-plugins=inspector --allow-cors
```
O servidor Appium geralmente roda na porta padrão 4723.

<div>
<img src="https://i.ibb.co/gZN1Tw8g/Captura-de-Tela-2025-11-29-a-s-12-23-48.png" width="450"/>
</div>


### 🌐 Acesso e Uso via Navegador:

Acesse a URL do Plugin (Localmente)
Com o servidor Appium rodando conforme a etapa 2 da instalação do plugin, abra o seguinte endereço no seu navegador:

```
http://localhost:4723/inspector
```

<div>
<img src="https://i.ibb.co/N23F8V2j/Captura-de-Tela-2025-11-29-a-s-12-24-07.png" width="450"/>
</div>


### 2. Aplicativo Appium Inspector:

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
