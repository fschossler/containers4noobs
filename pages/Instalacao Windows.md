<p align="center">
    <img src="../assets/header-4noobs.svg">
</p>

<h1 align="center">Containers4Noobs</h1>

<p align="center">
    <img src="../assets/containers.jpg" />
</p>

# Instalação do Ambiente no Windows

Essa página tem como objetivo auxiliar na instalação de ferramentas de Containers no OS Windows, sendo que nesse tutorial abordaremos duas ferramentas:

- 👍 Podman
- Docker

# Instalando a WSL 2 e Requisitos

Os ambientes de visualização de containers (em sua grande maioria) são baseados em sistemas Unix (Linux), por isso existe uma incompatibiliade nativa entre os containers e o Windows.

Para solucionar isso, o OS disponibiliza uma ferramenta chamada WSL (Windows Subsystem For Linux).

<p align="center">
  <img src="https://res.cloudinary.com/practicaldev/image/fetch/s--lV4X43s---/c_limit%2Cf_auto%2Cfl_progressive%2Cq_auto%2Cw_880/https://dev-to-uploads.s3.amazonaws.com/i/erssr2kcgbvyv8niqmdi.png"/ alt="Arquitetura da WSL">
</p>

A diferença entre virtualização e containerização pode ser lida na [página principal](../README.md).

Para instalar a WSL temos os seguintes requisitos mínimos de sistema:

<ol>
  <li>Procesador 64 bit com SLAT</li>
  <li>4 GB Ram</li>
  <li>Suporte para virtualização deve estar habilitado na BIOS</li>
  <li>Windows 10 versão 200 ou superior ou Windows 11</li>
</ol>

O Windows Subsystem For Linux permite que você instale uma distribuição Linux (Ubuntu,Kalil,Fedora,etc.) e integre-o com ferramentas do Windows como PowerShell, Visual Code, entre outros. Além disso, por ser um sub-sistema(como diz o nome)
é possível instalar bibliotecas e utilizar ferramentas que são nativas ao Linux dentro desse ambiente.

Para instalar o WSL, que atualmente encontra-se na versão 2, siga os seguintes passos:

<ol>
  <li>Certifique-se que seu Windows é superior a versão Windows 10 version 200 ou que está utilizando o Windows 11.</li>
  <li>Abra o PowerShell ou prompt de comando <strong>com privilégios de administrador</strong></li>
  <li>Utilize o comando: wsl --install </li>
</ol>

Será executado um script que habilitará a WSL2 e será instalada por padrão uma distribuição Ubuntu.
Agora, você pode procurar na sua aba de pesquisa por *Ubuntu* ou *WSL* ou digitar na sua linha de comando o comando wsl.

<p align="center">
  <img src="https://mundoconectado.com.br/uploads/2020/09/12/15409/windows-10-linux-wsl-2-update-02.jpg" alt="Comandos da WSL"/>
</p>

# Instalando o Podman

Com a WSL2 instalada, agora é possível instalar o Podman. Para isso, acesse as [releases](https://github.com/containers/podman/releases) liberadas do Podman, após isso procure no fim da página os arquivos disponibilizados.

Baixe o arquivo com a extensão .msi e execute-o com privilégio de administrador. Esse tipo de arquivo instala pacotes no Windows e transforma o fluxo de instalação em algo mais fácil e flúido. O instalador procurará o WSL e caso o encontre irá instalar a engine do podman e seus binários.

Após a instalação, você poderá iniciar a máquina do podman com o seguinte comando:

<p align="center"><em>podman machine</em></p>

A saída deverá ser algo assim:

``` PS C:\Users\User> podman machine init
Extracting compressed file
Importing operating system into WSL (this may take 5+ minutes on a new WSL install)...
Installing packages (this will take a while)...
Complete!
Configuring system...
Generating public/private ed25519 key pair.
Your identification has been saved in podman-machine-default
Your public key has been saved in podman-machine-default.pub
The key fingerprint is:
SHA256:RGTGg2Q/LX7ijN+mzu8+BzcS3cEWP6Hir6pYllJtceA root@WINPC
Machine init complete
To start your machine run:

        podman machine start 
```

Esse comando irá instalar uma distribuição fedora mínima para permitir o *start* do podman.

Após isso, execute o seguinte comando para startar o podman:

<p align="center"><em>podman machine start</em></p>

O log deverá ser algo similar a isso:

```PS C:\Users\User> podman machine start

Starting machine "podman-machine-default"

This machine is currently configured in rootless mode. If your containers
require root permissions (e.g. ports < 1024), or if you run into compatibility
issues with non-podman clients, you can switch using the following command:

        podman machine set --rootful

API forwarding listening on: npipe:////./pipe/docker_engine

Docker API clients default to this address. You do not need to set DOCKER_HOST.
Machine "podman-machine-default" started successfully
```

Para parar a máquina Podman pode utilizar:

<p align="center"><em>podman machine stop</em></p>

# Instalando o Docker

Caso você prefira utilizar a ferramenta Docker, após  ter instalado a WSL2 é necessário seguir os passos:

Acesse a página do [Docker Desktop](https://docs.docker.com/desktop/install/windows-install/) e clique no botão <strong>"Docker Desktop for Windows"</strong> para baixar o executável com extensão .exe.

Após baixar, execute o arquivo com privilégios de adminsitrador e então será instalado o aplicativo Docker Desktop.

Esse aplicativo, quando executado, inicia o *Daemon* do docker no WSL2 e exibe uma interface gráfica para o usuário onde você pode visualizar o estado de seus containers ou composições, verificar as imagens locais e caso queira habilitar o Kubernetes.

<p align="center">
  <img src="https://1665891.fs1.hubspotusercontent-na1.net/hubfs/1665891/Picture-1-Docker-Desktop-Dashboard%2C-open-the-Extension-Marketplace-v2.jpg" alt="Dashboard de Imagens do Docker Desktop"/>
  <br/>
  <img src="https://res.cloudinary.com/practicaldev/image/fetch/s--ukEYjhJ---/c_imagga_scale,f_auto,fl_progressive,h_900,q_auto,w_1600/https://dev-to-uploads.s3.amazonaws.com/uploads/articles/zzagw1vphidl5d79kuez.png" alt="Estados dos Containers">
</p>

Com o Docker Desktop rodando, ele em segundo plano executará a Docker Desktop Engine (o ícone pode ser visualizado nos ícones ocultos) e então permitirá que você execute comandos docker fora da WSL (a partir do prompt por exemplo).

> Para executar qualquer comando docker, é necessário que você esteja com a Engine rodando.

> Vale ressaltar que o Docker Desktop está sob uma licensa de uso Pessoal, ou seja, você pode usá-lo para fins de estudo, desenvolvimento individual, pequenas comunidades open source e pequenos negócios, para mais informações acesse a [página de pricing](https://www.docker.com/pricing/).