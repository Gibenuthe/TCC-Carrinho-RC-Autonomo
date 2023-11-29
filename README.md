# TCC-Carrinho-RC-Autonomo
Guia didático para montagem de um carrinho de controle remoto autônomo usando a biblioteca donkeycar.

## Resultado Final (vídeos)
<a href="https://www.youtube.com/watch?v=4T0594B4K40&v=4T0594B4K40
" target="_blank"><img src="http://img.youtube.com/vi/4T0594B4K40/0.jpg" 
 width="240" height="180" border="10" /></a>
&emsp; &emsp; &emsp; <a href="http://vimeo.com/865403276
" target="_blank"><img src="/Imagens/Video_Vimeo.png" 
 width="240" height="180" border="10"/></a>
## Materiais e montagem
<img src="/Imagens/Materiais.png">

## Tabela de Custos
| Material       | Preço           | Link  |
|:-------------:|:-------------:|:-----:|
| Buggy Wltoys 124017 V2 4x4      | ~1000,00 | [Banggood](https://br.banggood.com/Wltoys-124017-Brushless-V2-New-Upgraded-4300KV-Motor-0_7M-19T-RTR-1-or-12-2_4G-4WD-70km-or-h-RC-Car-Vehicles-Metal-Chassis-Models-Toys-p-1871731.html?gmcCountry=BR&currency=BRL&cur_warehouse=CN&createTmp=1&ad_id=) |
| Bateria 5200mAh      | 300,00      |   [Fabmodelismo](https://www.fabmodelismo.com.br/produto/pecas-e-acessorios/baterias-em-geral/9467-bateria-lipo-7-4v-2s-5200mah-30c60c-xt60-automodelo) |
| Conversor 7.4v para 5v | 12,00      |    [Iot-robotica](https://www.iot-robotica.com.br/produto/mini-stepdown-mp1584en-5volts.html) |
| câmera para nvidia jetson placa nano | 20,00      |    [Aliexpress](https://pt.aliexpress.com/item/1005004662842684.html?src=google&src=google&albch=shopping&acnt=768-202-3196&slnk=&plac=&mtctp=&albbt=Google_7_shopping&isSmbAutoCall=false&needSmbHouyi=false&albcp=17280411561&albag=&trgt=&crea=pt1005004662842684&netw=x&device=c&albpg=&albpd=pt1005004662842684&gad_source=1&aff_fcid=c6d316c1a9c54d4bba89c518b498c606-1701298830689-05444-UneMJZVf&aff_fsk=UneMJZVf&aff_platform=aaf&sk=UneMJZVf&aff_trace_key=c6d316c1a9c54d4bba89c518b498c606-1701298830689-05444-UneMJZVf&terminal_id=e917859336ee48868c6ef3c60e6fef75&afSmartRedirect=y) |
| Placa Wifi+BT | 30,00      |    [Aliexpress](https://pt.aliexpress.com/item/1005005588691109.html?src=google&src=google&albch=shopping&acnt=768-202-3196&slnk=&plac=&mtctp=&albbt=Google_7_shopping&isSmbAutoCall=false&needSmbHouyi=false&albcp=17364768653&albag=&trgt=&crea=pt1005005588691109&netw=x&device=c&albpg=&albpd=pt1005005588691109&gad_source=1&aff_fcid=48fce4cd8d414ead9314d587472ac870-1701299109821-05102-UneMJZVf&aff_fsk=UneMJZVf&aff_platform=aaf&sk=UneMJZVf&aff_trace_key=48fce4cd8d414ead9314d587472ac870-1701299109821-05102-UneMJZVf&terminal_id=e917859336ee48868c6ef3c60e6fef75&afSmartRedirect=y#nav-specification)|
| Cabo XT60 para adaptar | 10,00      |    [Aliexpress](https://pt.aliexpress.com/item/1005003866427129.html?src=google&src=google&albch=shopping&acnt=768-202-3196&slnk=&plac=&mtctp=&albbt=Google_7_shopping&isSmbAutoCall=false&needSmbHouyi=false&albcp=17364768653&albag=&trgt=&crea=pt1005003866427129&netw=x&device=c&albpg=&albpd=pt1005003866427129&gad_source=1&aff_fcid=6b0a77cc308f418e9e455938108b57d0-1701299314930-05995-UneMJZVf&aff_fsk=UneMJZVf&aff_platform=aaf&sk=UneMJZVf&aff_trace_key=6b0a77cc308f418e9e455938108b57d0-1701299314930-05995-UneMJZVf&terminal_id=e917859336ee48868c6ef3c60e6fef75&afSmartRedirect=y) |
| PCA9685 | 40,00      |    [Baudaeletronica](https://www.baudaeletronica.com.br/produto/modulo-pwm-pca9685-i2c-16-canais-para-servo-motor.html?gad_source=4) |
| NVidia Jetson Nano 4Gb | 1100,00      |    [Amazon](https://www.amazon.com.br/Waveshare-Jetson-Developer-Computer-Development/dp/B08QCPDKW1/ref=cm_cr_arp_d_product_top?ie=UTF8) |
| Total | 2512,00           |


### Passo a passo da montagem de hardware:
Explicação mais detalhada no idioma original (Inglês) em: https://docs.donkeycar.com/guide/build_hardware/
- Abra o carrinho e desconecte os jumpers que ligam o receiver ao ESC, atente-se às cores para facilitar na identificação de controle de velocidade e direção;
- Conecte o módulo PWM PCA9685 à Jetson Nano de acordo com pino 3->SDA e 5->SCL. Conecte também a câmera.
- Caso deseje alimentar a Jetson Nano com uma bateria compatível com o carrinho será necessário fazer a ligação de um cabo compatível com a bateria, um conversor 7.4V->5V e o conector (*barrel jack*/micro usb);
> **Nota:** A Jetson Nano também não possui conectividade Wi-Fi nativa, portanto é necessária a compra de um módulo Wi-Fi/Bluetooth unificado com as antenas para podermos pilotar o carrinho e observar a interface web através da internet. Esta montagem é simples e pode ser encontrada facilmente em um tutorial no Youtube.
### Passo a passo da configuração de software:
Explicação mais detalhada no idioma original (Inglês) em: https://docs.donkeycar.com/guide/install_software/

Apesar da Donkeycar recomendar no tutorial que se instale o software em um PC host, para este projeto não é necessário visto que usamos um [notebook no Google Colab](/Treinamento_Donkey_TCC.ipynb) para treinar o modelo e não fizemos uso da UI para deleção de dados mal coletados (isso faz com que seja necessário pilotar com extremo cuidado mantendo a qualidade dos dados).

- Prepare o cartão de memória SD com a imagem do sistema e depois limpe e configure as dependências e bibliotecas de código no sistema operacional;
- Crie a aplicação donkey padrão (sem template);
- Configure a PCA9685 para se certificar que está funcional;
- Faça a calibração para verificar a intensidade do sinal PWM.
- No arquivo myconfig.py só é necessário mudar os valores `CAMERA_TYPE, STEERING_LEFT_PWM, STEERING_RIGHT_PWM, THROTTLE_FORWARD_PWM, THROTTLE_STOPPED_PWM` e `THROTTLE_REVERSE_PWM`. O resto das customizações podem ser exploradas de acordo com as necessidades, consultando a documentação oficial.
## Coletando os dados
Explicação mais detalhada no idioma original (Inglês) em: https://docs.donkeycar.com/guide/get_driving/

O comando `python manage.py drive` abre um servidor com uma interface web que permite a visualização da câmera, a possibilidade de controlar o carrinho com um joystick na web ou um gamepad (controle de video game) e a possibilidade de mudar entre os modos usuário, *full auto* (piloto autônoma) e *auto steer* (direção autônoma).

Recomendamos conectar um controle por bluetooth no dispositivo que abrirá o servidor `[ip]:8887/drive` (pode ser um celular na mesma rede) e dirigir até gerar pelo menos mais de 10 catálogos ([Catálogos](/Catalogos.pdf)) prezando sempre por dirigir bem para evitar que seja necessário limpar os dados posteriormente.
