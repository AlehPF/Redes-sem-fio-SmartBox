# Projeto de Caixa Inteligente - Redes Sem Fio (UFSC)

## Descrição

Este repositório contém o código-fonte para um projeto de caixa inteligente desenvolvido como parte da disciplina de Redes sem Fio na Universidade Federal de Santa Catarina (UFSC). A caixa inteligente tem como objetivo proporcionar um controle mais eficiente das vendas dos itens de uma cantina, capturando uma foto da pessoa sempre que a caixa é aberta.

## Funcionalidades Principais

- **Captura de Imagem ao Abrir:** A caixa inteligente está equipada com uma ESP32-CAM que captura uma foto automaticamente quando a caixa é aberta, utilizando um sensor de fim de curso como gatilho.

- **Armazenamento Local da Imagem:** A foto capturada é armazenada localmente no sistema de arquivos SPIFFS (Sistema de Arquivos SPI Flash) da ESP32.

- **Envio da Imagem para o Firebase:** Após capturar a imagem, o código envia automaticamente a foto para o armazenamento do Google Firebase. Isso permite um controle centralizado das imagens capturadas.

## Configuração

Antes de utilizar este código, certifique-se de realizar as seguintes configurações:

1. **Credenciais do Firebase:** Substitua as informações sensíveis, como SSID, senha WiFi, chave de API Firebase, etc., com suas próprias credenciais no código (`ssid`, `password`, `API_KEY`, etc.).

2. **Configuração dos Pinos:** Verifique e ajuste as configurações dos pinos da câmera OV2640 conforme necessário para o seu hardware.
   
![](https://i0.wp.com/randomnerdtutorials.com/wp-content/uploads/2020/03/ESP32-CAM-pinout-new.png?w=1000&quality=100&strip=all&ssl=1)

4. **Configuração do Sensor de Fim de Curso:** O sensor de fim de curso é configurado no pino 4 (`FIM_DE_CURSO_PIN(4)`). Certifique-se de ajustar isso conforme a conexão física do seu sensor.

## Como Utilizar

1. Clone este repositório em sua máquina local.
   ```bash
   git clone https://github.com/AlehPF/Redes-sem-fio-SmartBox.git
   ```

2. Abra o código-fonte no ambiente de desenvolvimento da Arduino IDE ou plataforma equivalente.

3. Faça as configurações necessárias descritas na seção "Configuração".

4. Carregue o código para sua ESP32-CAM.

5. Abra a caixa inteligente e observe a captura automática de uma foto.

## Contribuição

Sinta-se à vontade para contribuir para este projeto, relatando problemas, propondo melhorias ou enviando pull requests. A colaboração é bem-vinda!

## Autores

- Alisson Pereira Ferreira (Matrícula: 22250769, E-mail: alissonpef@gmail.com)
- Emir Bráz de Araújo Marques Júnior (Matrícula: 18203862, E-mail: emirbraz.d2@gmail.com)
- João Pedro Tavares Santos (Matrícula: 19102493, E-mail: j-pts@hotmail.com)
- Monique Rosa Moraes (Matrícula: 19102195, E-mail: moniquedemoraes@hotmail.com)
- Nícolas André Baümle (Matrícula: 19201494, E-mail: nicolasbaumle@gmail.com)
- Régis Nyland Bloemer (Matrícula: 20102404, E-mail: regisnb1@gmail.com)
- Rodrigo Guedes de Souza (Matrícula: 19204117, E-mail: guigoguedes2@gmail.com)

--- 

**Universidade Federal de Santa Catarina**  
Curso: Engenharia de Computação  
Disciplina: Redes sem Fio  
Professora: Analucia Schiaffino Morales
