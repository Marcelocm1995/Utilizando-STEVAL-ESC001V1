# Objetivo
Ensinar a criar o firmware para controlar a placa STEVAL-ESC001V1 via PWM(PPM) utilizando o compilador Keil uVision.

# Softwares Necessários
* MotorControl Workbench [link](https://www.st.com/en/embedded-software/x-cube-mcsdk.html)
* CubeMX [link](https://www.st.com/en/development-tools/stm32cubemx.html)
* Keil uVision (MDK-ARM) [link](https://www.keil.com/download/product/)

# Criando o projeto 
Abra o MotorControl Workbench, procure na seção de exemplos por EletronicSpeedControl como mostrado abaixo:
<a href="https://imgur.com/Vl2SjfV"><img src="https://imgur.com/Vl2SjfV.jpg" title="source: imgur.com" /></a>
Abra o arquivo do projeto e logo em seguida salve-o com em outro diretório de seu computador. Isso fará com que criemos um projeto cópia do exemplo, assim não perdendo o arquivo orginal do MotorControl Workbench. **A partir daqui iremos sempre trabalhar em cima desta cópia!**

# Gerando a base do código
Vá até a aba "Tools", e em seguinda clique em "Generation", como mostrado abaixo: 
<a href="https://imgur.com/IBesZVq"><img src="https://imgur.com/IBesZVq.jpg" title="source: imgur.com" /></a>
Abrirá uma janela com alguns parâmetros, que deverão ser configurados a seguir:
  *    Versão do cubeMX 5.2.0 ou mais recente
  *    Target Toolchain é o compilador que desejamos usar, no caso selecione "Keil MDK-ARM V5"
  *    Firmware Package version é a versão do pacote utilizado para a geração do código, é recomendado utilizar a mais recente, mas qualquer versão acima da FW V1.10.0 servirá.
  *    Driver Type é o tipo de biblioteca que irá ser usada no projeto, selecione HAL - Hardware Abstraction Layer 
 Tudo deverá ficar desta forma abaixo:

<a href="https://imgur.com/CQVUTB9"><img src="https://imgur.com/CQVUTB9.jpg" title="source: imgur.com" /></a>

Por fim, clique em "Update"

# Compilando o código
Na pasta do diretório escolhido abra a pasta MDK-ARM e abra com o Keil o projeto *ElectronicSpeedControl.uvprojx*.
Compile o código na aba "Project" e depois escolha "Build Target" (atalho F7), o código deverá ser compilado sem erros e/ou avisos.
<a href="https://imgur.com/MRldmVv"><img src="https://imgur.com/MRldmVv.jpg" title="source: imgur.com" /></a>

# Gravando o código
Utilizaremos um gravador ST-Link-V2 conectado a placa STEVAL-ESC001V1 de acordo com a figura abaixo:
<a href="https://imgur.com/nY1fsue"><img src="https://imgur.com/nY1fsue.jpg" title="source: imgur.com" /></a>
No keil vá até a aba "Project" e depois escolha "Options for Target" (atalho Alt+F7), uma janela se abrirá. Nesta janela vá até a aba debug, marque a opção "Use: ST-Link Debugger" e clique em "Settings". Agora vá na aba "Flash Download" e habilite a opção "Reset and Run". Confirme todas opções e feche as janelas. 

Para finalmente gravar o código na placa devemos ir na aba "Flash" e depois escolha "Download" (atalho F8). O compilador deverá mostrar a seguinte mensagem de sucesso na gravação:
<a href="https://imgur.com/JwmZ2aU"><img src="https://imgur.com/JwmZ2aU.jpg" title="source: imgur.com" /></a>

## Gerando um sinal PPM para controle
Importe o código mBed para gerar o sinal PPM neste [link](https://os.mbed.com/users/Marcelocostanzo/code/PPM_SIGNAL_GENERATOR/).
Ligue um potenciômetro no pino A0 da NUCLEO
Ligue o fio de sinal da NUCLEO (D6) no pad "IN" próximo ao pad de alimentação (GND) da placa STEVAL-ESC001V1.
<a href="https://imgur.com/XSm0hHK"><img src="https://imgur.com/XSm0hHK.jpg" title="source: imgur.com" /></a>

## Testando o conjunto
Ligue a fonte da placa STEVAL-ESC001V1, na NUCLEO gire o potenciômetro para a posição mínima (acompanhe o valor em algum terminal), o motor deverá emitir alguns sons, então suba um pouco o valor do potenciômetro para que o motor começe a girar. 


