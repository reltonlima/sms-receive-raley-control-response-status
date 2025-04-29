# sms-receive-raley-control-response-status
Controle de relé via SMS.

## Descrição do Projeto
Este projeto utiliza o módulo GSM SIM800L e a placa LilyGO T-Call ESP32-WROVER-B para controlar um relé através de comandos enviados via SMS. Ele permite ligar, desligar, verificar o status do relé e obter ajuda sobre os comandos disponíveis. A comunicação com o módulo GSM é feita utilizando a biblioteca Adafruit FONA.

## Funcionalidades
- Receber mensagens SMS e interpretar comandos.
- Controlar um relé com os comandos:
  - `on`: Liga o relé.
  - `off`: Desliga o relé.
  - `status`: Retorna o status atual do relé.
  - `help`: Lista os comandos disponíveis.
- Responder automaticamente ao remetente com mensagens de confirmação ou ajuda.

## Configuração de Hardware
1. Conecte o módulo GSM SIM800L à placa ESP32 conforme os pinos definidos no código:
   - **RX**: Pino 26
   - **TX**: Pino 27
   - **PWRKEY**: Pino 4
   - **RST**: Pino 5
   - **POWER**: Pino 23
2. Conecte o relé ao pino 14 do ESP32.
3. Conecte um LED azul ao pino 13 para indicar o funcionamento do sistema.
4. No nosso exemplo usamos uma placa ESP32-WROVER-B Lilygo T-Call.

## Configuração de Software
1. Certifique-se de ter a biblioteca [Adafruit FONA](https://github.com/adafruit/Adafruit_FONA_Library) instalada no Arduino IDE.
2. Faça o upload do código `sketch_sms-receive-send.ino` para a placa ESP32.

## Instruções de Uso
1. Ligue o sistema e aguarde a inicialização do módulo GSM (pode levar mais de 10 segundos).
2. Envie um SMS para o número do SIM card inserido no módulo GSM com um dos seguintes comandos:
   - `on`: Liga o relé e retorna uma mensagem de confirmação.
   - `off`: Desliga o relé e retorna uma mensagem de confirmação.
   - `status`: Retorna o status atual do relé.
   - `help`: Retorna uma lista de comandos disponíveis.
3. O sistema responderá automaticamente ao remetente com a mensagem apropriada.
4. Sertifique-se de que o chip inserido no módulo tem créditos, pacote de sms e está habilitado para envio e recebimento desse tipo de mensagem.
5. Chips M2M podem ter restrições de envio/recebimeto de sms. Para saber mais consulte sua operadora.
6. Nossos testes foram feitos com um chip comum da TIM.

## Observações
- Certifique-se de que o módulo GSM está conectado a uma fonte de alimentação estável.
- O módulo SIM800L precisa de uma corrente entre 3.4v e 4.4v para funcionar corretamente.
- O código está configurado para o modelo `SIM800L_IP5306_VERSION_20200811`. Caso utilize outro modelo, ajuste a definição no início do código.
- Para modificar os comandos ou mensagens de resposta, edite a função `switchCase` no código.

## Autor
- Relton Lima
### Código Base
https://github.com/FranzTscharf/TTGO_T-CALL_ESP32_SMS_Receive_Send
#### adaptado para lib oficial do T-Call
https://github.com/reltonlima/LilyGo-T-Call-SIM800/blob/master/examples/Arduino_SMS/utilities.h
