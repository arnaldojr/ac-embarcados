## Raspberry PI

![](https://hackaday.com/wp-content/uploads/2016/02/pihero.jpg?w=800)
 
Neste laboratório vamos começar nossa jornada de computação embarcada com aplicações simples com uso de sensores e voltadas paara a Internet das Coisas com o hardware ``Raspberry PI``. 
Nesta etapa vamos ver dentre outras coisas: o que é a Respberry Pi, Sistema Operacional Linux, como dar boot na placa Raspberry PI, como configurar e utilizar os GPIO - Pinos de Entrada/Saida, como realizar integrações e muito mais...

## O que vamos ver neste lab?

- Raspberry PI: o que é? Qual a diferença para o Arduino? 
- Raspberry Pi: Getting Started 
    - Overview - Conhecendo o hardware
    - Flash SD Card - Como dar boot do Sistema Operacional na Raspberry PI
    - Modos de uso - GUI x Headless
        - Headless - Configurando acesso SSH e rede Wifi.
        - Headless - VNC Viewer
        - GUI - Modo Desktop  
    - Controlando os GPIO - Blink LED.
        - Controle por CLI
        - Shell Script
        - ...

## Raspberry PI x Arduino

Antes de falar da Raspberry PI, vamos lembrar que o Arduino UNO, que usamos nos primeiros semestres, possui um ``microcontrolador`` de 8-bit [link do datasheet](https://ww1.microchip.com/downloads/en/DeviceDoc/Atmel-7810-Automotive-Microcontrollers-ATmega328P_Datasheet.pdf). Possui uma arquitetura RISC, e cobre bem os requisitos mínimos de um sistema embarcado. Contudo, não é possivel rodar um sistema operacional completo, o que pode limitar algumas possibiildades de sistemas mais complexos.

Para rodar um ``Sistema Operacional`` completo precissamos de um ``processador`` por exemplo o processador Intel 386, I5, I7, Celeron e muitos outros [(link do datasheet de um Intel I7)](https://www.intel.com/content/dam/www/public/us/en/documents/datasheets/core-i7-900-ee-and-desktop-processor-series-datasheet-vol-1.pdf) que usamos em nossos notebooks e desktops por exemplo. Em apicações de computação embarcada geralmente usamos um computador otimizado para atender requisitos tecnicos de custo, consumo de energia, peso, tamanho dentre outros... nesses casos podemos utilizar ``SBC`` (Single Board Computer).

Os computadores de placa única (SBC) são computadores completos (combinação de um processador, memória, suporte de rede, video, audio, entrada e saída e outros...) em uma placa só, com a vantagem de ser de baixo custo e possuir pequenas dimensões comparado ao computador convensional.

É neste ponto que vamos começar a falar da ``Raspberry PI`` que é a mais famosa e mais conhecida SBC e que suporta um Sistema Operacional Embarcado (Linux) ou seja, com ela é possivel desenvolver e implementar uma infinidade de projetos. 

A placa Raspberry Pi foi lançada em 2012 pela Raspberry Pi Fundation, sendo uma classe de pequenos computadores portáteis de baixíssimo custo, baseado nos processadores multimídia de arquitetura ARM da Broadcom, o mesmo que utilizados em celulares. O projeto foi um sucesso, vem crescendo e se atualizando, hoje temos diversos modelos para diversas aplicações diferentes como a Raspberry PI 3, 4, Zero e outros.

> [link da documentação oficial](https://www.raspberrypi.org/)

> [Link para conhecer outros modelos de SBC](https://all3dp.com/pt/1/single-board-computer-computadores-placa-unica-alternativas-raspberry-pi/)

Agora que já entendemos um pouco o que é Raspberry PI, vamos aprender a usar....

!!! progress
    Continuar...

## Raspbeery PI - Getting Started

### Overview

Existem varios modelos de Raspberry PI, em nossas aulas vamos utilizar a [``Raspberry PI 3 Model B+``](https://www.raspberrypi.com/products/raspberry-pi-3-model-b-plus/). 

![rpi3](Pi3-Breakout-Feb-29-2016.png)

![Espec](https://hackaday.com/wp-content/uploads/2016/02/pispecs2.png)

> Para complementar:
>
> - Fonte de Alimentação: 5V @ >2A
>
> - Cartão SD Card: micro SD Card >8GB Classe 10 ou superior

### Sistema Operacional

Podemos utilizar diversas distribuções na RPI, dentre elas as mais comuns são:

- Raspbian - SO de uso geral 
- Ubuntu - SO de uso geral
- RetroPie - Emulador de video game
- OSMC - Media Center 
- Home Assistent - Automação Residêncial
- E muitos outross...

> Fim da teoria, vamos pra parte prática!! Leia com atenção este guia e siga todos os passos.  

!!! progress
    Continuar...
   
### Flash SD Card

O SO (Sistema Operacional) da RPI fica armazenado no ``micro SD Card`` que deve ter pelo menos 8GB de capacidade e ser Classe 10 ou superior, existem diversas formas de realizar a gravação do SO (Sistema Operacional), para isso se prepare pois chegou a hora de por a mão na massa. 

As diversas versões de SO, podem ser encontradas [no link https://www.raspberrypi.com/software/operating-systems/](https://www.raspberrypi.com/software/operating-systems/). 
Em nosso curso vamos utlizar o ``Raspberry Pi OS (legacy)`` baseado na Distribuição Debian 10 (Buster). 

![RPI-OS](RPI-OS.png)

!!! info
    Pra facilitar, o link para [downlod já está aqui](https://downloads.raspberrypi.org/raspios_oldstable_armhf/images/raspios_oldstable_armhf-2022-04-07/2022-04-04-raspios-buster-armhf.img.xz)


Podemos gravar o SD Card de algumas formas, a opção mais simples é utilizar o ``Balena Etcher`` que roda em diversas plataformas.

> Para facilitar, o link para [download do balena Etcher https://www.balena.io/etcher/](https://www.balena.io/etcher/) 

!!! exercise
    Agora você deve:

        - Faça o Download do RPI OS 
        - Faça o Download do Balena Etcher
        - No seu notebook:
            - Remova o SD Card da RPI e conecte o cartão em seu notebook
            - Abra o Balena Etcher e siga os passos para gravar o cartão micro SD Card
        - Após a gravação, remova o cartão micro SD Card da USB e conecte no computador novamente.
        - Se tudo der certo:
            -  Irão aparecer duas particições referentes ao cartão micro SD Card, sendo uma delas chamada "boot"
            -  Caso contrário, alguma coisa deu errada, formate o SD Card em FAT32 e grave novamente. 

!!! progress
    Continuar...        

### Modo de uso - Interface Gráfica 

> Apenas para conhecimento extra, pois **não é desta forma que vamos usar a Raspberry PI em nosso curso** 

Para utilizar a RPI como um computador "normal", é muito simples! Basta conectar na Raspberry PI: O SD Card gravado, um monitor HDMI, um teclado e um mouse. 
Com tudo conectado, conecte a fonte de alimentação 5V e o sistema operacional irá inicializar :) .  

![sdcard](sdcard.png)

![rpidesk](rpidesk.jpg)

### Modo de uso - Headless

> Agora sim! Atenção nos próximos passos...

Vamos utilizar o Rasbperry PI no modo ``Headless``, ou seja, sem conectar monitor, teclado e mouse. Desta forma o acesso a RPI será via SSH com o uso do terminal. Para abilitar este modo, é necessário realizar algumas configurações no micro SD Card antes de dar o boot na Raspberry PI.

#### Habilitar SSH

Para habilitar o SSH é necessário criar um arquivo vazio (sem extensão) chamado ssh dentro da pasta boot. 

!!! exercise
    Agora você deve:

        - Conecte o micro SD Card no notebook
        - Acesse a partição chamada 'boot'
        - crie um arquivo chamado 'ssh' na raiz da partição boot
        - este arquivo "não possui extensão" 

![ssh](ssh.png)

O resultado esperado deve ser semelhante ao da imagem abaixo: Note que o arquivo não possui extensão.

![ssh1](ssh1.png)

!!! progress
    Continuar...
    
#### Configuração de Rede Wi-fi

A configuração de rede do Wi-fi é feita através da configuração do arquivo 'wpa_supplicant.conf'. Este arquivo deve ser criado dentro da pasta 'boot'.

!!! exercise
    Agora você deve:

        - crie um arquivo chamado 'wpa_supplicant.conf' na raiz da partição boot
        - abra o arquivo criado com algum editor de texto (bloco de notas ou vscode)
        - configure o arquivo da mesma forma que o texto abaixo 

> Neste ponto é importe ter uma rede wifi para se conecetar.
> Temos 2 opções de redes: Personal e Enterprise
> (Recomendado) - Para uma rede personal use a configuração abaixo.  
> Esta configuração é a mais indicada e segura para ser usada em aula, para isso rotei a internet de seu celular.


!!! info
    Dica para facilitar a conexão, utilize o seu notebook como ``Hotspot móvel`` desta forma fica tudo mais simples para se conectar. 
    Para isso, faça a seguinte configuração:
    
        - Selecione o botão ``Iniciar``  e ``Configurações > Rede e Internet > Hotspot móvel``.
        - Em ``Compartilhar minha conexão de Internet`` de, escolha a conexão de Internet que você deseja compartilhar.
        - Selecione ``Editar`` > insira o nome e a senha de uma rede nova > ``Salvar``.
        - Ative ``Compartilhar minha conexão de Internet com outros dispositivos``.
        - Para se conectar no outro dispositivo, vá para as configurações de Wi-Fi no dispositivo, localize o nome da rede, selecione-o, insira a senha e conecte-se.
    
    fonte: [microsoft](https://support.microsoft.com/pt-br/windows/usar-seu-computador-windows-como-um-hotspot-m%C3%B3vel-c89b0fad-72d5-41e8-f7ea-406ad9036b85)



* Personal: (RECOMENDADO) - Use o roteador da sua casa ou habilite seu Celular como Roteador 

    ```shell
    
    country=BR
    ctrl_interface=DIR=/var/run/wpa_supplicant GROUP=netdev
    update_config=1
      
    network={
            scan_ssid=1
            ssid="COLOQUE_O_NOME_DA_REDE"
            psk="COLOQUE_A_SENHA_DA_REDE"
    }
    
    ```
* Enterprise: Redes WPA2 

> A rede do INSPER requer autenticação enterprise. Você vai utilizar seu usuário e senha.

    ```shell
    
    # Connect to a WPA2 Enterprise network with wpa_supplicant with this .conf file.
    # I used this to connect to my university's wireless network on Arch linux.
    # Here's the command I used:
    #
    #   wpa_supplicant -i wlan0 -c ./wpa_supplicant.conf
    # 
    
    network={
      ssid="YOUR_SSID"
      scan_ssid=1
      key_mgmt=WPA-EAP
      identity="YOUR_USERNAME"
      password="YOUR_PASSWORD"
      eap=PEAP
      phase1="peaplabel=0"
      phase2="auth=MSCHAPV2"
    }
    
    ```




Configuração finalizada! Agora vamos ligar! Mas antess......

!!! progress
    Continuar...

#### Boot Raspberry PI

Para ter acesso SSH ao raspberry PI vou mostras 2 modos: 

1. vamos utilizar o software ``PuTTy``, ou qualquer outro que abre conexão SSH.

> Para facilitar, o link para [download do PuTY https://www.putty.org/](https://www.putty.org/)

Agora com tudo configurado e instalado chegou a hora de ligar e testar.

![sdcard](sdcard.png)

> O ``notebook e Raspberry PI devem estar na mesma rede Wifi`` do seu Smartphone/Roteador como indica a imagem abaixo.

![rede](rede.png)


2. Vamos utilizar o o software ``VScode``.

> É bem tranquilo realizar essa conexão, existem muitos sites que ensinam a fazer. Para facilitar, da uma olhada nos links:

    -  [https://code.visualstudio.com/docs/remote/ssh](https://code.visualstudio.com/docs/remote/ssh)  
    -  [https://www.raspberrypi.com/news/coding-on-raspberry-pi-remotely-with-visual-studio-code/](https://www.raspberrypi.com/news/coding-on-raspberry-pi-remotely-with-visual-studio-code/)
    -  [https://cloudbytes.dev/snippets/develop-remotely-on-raspberry-pi-using-vscode-remote-ssh](https://cloudbytes.dev/snippets/develop-remotely-on-raspberry-pi-using-vscode-remote-ssh)
    


!!! exercise
    Agora você deve:

        - Conecte o micro SD Card na Raspberry PI
        - Mantenha sua rede wifi ligada (Smartphone ou roteador)
        - Conecte seu computador(notebook) na mesma rede Wifi configurada na Raspbeery Pi
        - Ligue a fonte de alimentação na raspberry pi
        - Aguarde alguns segundos e vefifique o ip que foi atribuido ao Raspberry PI
        - No seu computador, escolha o motodo de acesso SSH (putty ou vscode), digite o ip da Raspberry PI e senha.
        - Se tudo estiver correto, um terminal irá abrir e vai solicitar login e senha


![ssh](ssh2.PNG)


> Por padrão, o login e senha da raspberry pi será:
>
> login: pi
>
> senha: raspberry
        
Finalizado! Agora estamos com nossa RPI conectada e pronta pra uso. 

### hello world :)

No terminal da raspberry pi, atualize os repositórios:

```bash

sudo apt update

```   


A parte divertida está no próximo lab... 

Não esqueça de dar uma olhada na aba DICAS para conhecer alguns projetos com a RPI.
