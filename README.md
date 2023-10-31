# TCC-Carrinho-RC-Autonomo
Guia didático para montagem de um carrinho de controle remoto autônomo usando a biblioteca donkeycar.

## Materiais e montagem
<img src="/Imagens/Materiais.png">

### Passo a passo da montagem de hardware:
Explicação mais detalhada no idioma original (Inglês) em: https://docs.donkeycar.com/guide/build_hardware/
- Abra o carrinho e desconecte os jumpers que ligam o receiver ao ESC, atente-se às cores para facilitar na identificação de controle de velocidade e direção;
- Conecte o módulo PWM PCA9685 à Jetson Nano de acordo com pino 3->SDA e 5->SCL. Conecte também a câmera.
- Caso deseje alimentar a Jetson Nano com uma bateria compatível com o carrinho será necessário fazer a ligação de um cabo compatível com a bateria, um conversor 7.4V->5V e o conector (*barrel jack*/micro usb);
> **Nota:** A Jetson Nano também não possui conectividade Wi-Fi nativa, portanto é necessária a compra de um módulo Wi-Fi/Bluetooth unificado com as antenas para podermos pilotar o carrinho e observar a interface web através da internet. Esta montagem é simples e pode ser encontrada facilmente em um tutorial no Youtube.
### Passo a passo da configuração de software:
Explicação mais detalhada no idioma original (Inglês) em: https://docs.donkeycar.com/guide/install_software/

Apesar da Donkeycar recomendar no tutorial que se instale o software em um PC host, para este projeto não é necessário visto que usamos um notebook no Google Colab para treinar o modelo e não fizemos uso da UI para deleção de dados mal coletados.

- Prepare o cartão de memória SD com a imagem do sistema e depois limpe e configure as dependências e bibliotecas de código no sistema operacional;
- Crie a aplicação donkey padrão (sem template);
- Configure a PCA9685 para se certificar que está funcional;
- Faça a calibração para verificar a intensidade do sinal PWM.
- No arquivo myconfig.py só é necessário mudar os valores `CAMERA_TYPE, STEERING_LEFT_PWM, STEERING_RIGHT_PWM, THROTTLE_FORWARD_PWM, THROTTLE_STOPPED_PWM` e `THROTTLE_REVERSE_PWM`. O resto das customizações podem ser exploradas de acordo com as necessidades, consultando a documentação oficial.
## Coletando os dados
Explicação mais detalhada no idioma original (Inglês) em: https://docs.donkeycar.com/guide/get_driving/

O comando `python manage.py drive` abre um servidor com uma interface web que permite a visualização da câmera, a possibilidade de controlar o carrinho com um joystick na web ou um gamepad (controle de video game) e a possibilidade de mudar entre os modos usuário, *full auto* (piloto autônoma) e *auto steer* (direção autônoma).

Recomendamos conectar um controle por bluetooth no dispositivo que abrirá o servidor `[ip]:8887/drive` (pode ser um celular na mesma rede) e dirigir até gerar pelo menos mais de 10 catálogos ([Catálogos](/Catalogos.pdf)) prezando sempre por dirigir bem para evitar que seja necessário limpar os dados posteriormente.
