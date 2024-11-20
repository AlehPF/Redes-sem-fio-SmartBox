# Projeto de Redes Sem Fio - Smart Box

## Descrição
O projeto "Smart Box" foi desenvolvido para implementar uma solução de monitoramento autônomo para pontos de venda self-service no hall do campus UFSC Araranguá, utilizando redes sem fio, sensores e dispositivos IoT. O objetivo principal é garantir o controle de transações de venda de produtos através do uso de sensores de fim de curso e de peso, conectados a um sistema baseado em ESP32-CAM, ESP32, e Firebase. A escolha do 4G como meio de conexão foi determinada pela estabilidade da rede em comparação com as redes Wi-Fi disponíveis no campus, como a "eduroam".

Este repositório contém os códigos implementados, incluindo a configuração de sensores, a captura de imagens com ESP32-CAM e o envio de dados para Firebase, além de um servidor Flask que simula a comunicação entre o sensor e a plataforma.

## Integrantes do Projeto
- **Alisson Pereira Ferreira**
- **Emir Braz de Araújo Marques Júnior**
- **João Pedro Tavares Santos**
- **Monique Rosa Moraes**
- **Nicolas Andre Baumle**
- **Regis Nyland Bloemer**
- **Rodrigo Guedes de Souza**

**Universidade Federal de Santa Catarina (UFSC) – Campus Araranguá**  
Caixa Postal 88.905-120 – Araranguá – SC – Brasil

## Funcionalidades

- 📸 **Captura de Imagem ao Abrir:** Quando a caixa é aberta, o sensor de fim de curso aciona a captura de uma imagem pela ESP32-CAM.
- 💾 **Armazenamento Local da Imagem:** A imagem é armazenada no sistema de arquivos SPIFFS (SPI Flash File System) da ESP32.
- ☁️ **Envio para o Firebase:** Após a captura da imagem, os dados são enviados automaticamente para o Firebase, permitindo o acesso remoto e seguro às imagens.

## Componentes Utilizados

- 🛠️ **ESP32-CAM**: Módulo para captura de imagem e comunicação sem fio com o Firebase.
- ☁️ **Firebase**: Plataforma de nuvem para armazenamento e gerenciamento de dados.
- 🌐 **Flask**: Framework para desenvolvimento do servidor de comunicação.
- 🚪 **Sensor de Fim de Curso (Limit Switch)**: Sensor para detectar a abertura da caixa e ativar a captura de imagem.
- ⚖️ **Sensor de Peso (HX711 e célula de carga de 5kg)**: Sensor para monitorar a retirada de produtos da caixa.
- 💾 **SPIFFS**: Sistema de arquivos para armazenar imagens localmente na ESP32.


## Modelagem do Sistema

A Smart Box é composta por um sistema de monitoramento de vendas baseado em um ESP32 que comunica com sensores para registrar transações. O sensor de peso detecta a retirada de produtos da caixa, enquanto o sensor de fim de curso detecta a abertura e fechamento da tampa. A ESP32-CAM captura a imagem do cliente e envia as informações para o Firebase.

## Arquivos e Funcionalidades

- **Smartbox.c:** Configura o ESP32-CAM para capturar fotos quando o sensor de fim de curso é acionado, armazenando-as no SPIFFS e enviando-as ao Firebase.
- **Interface.py:** Formata o conteúdo a ser enviado durante a simulação da comunicação entre o sensor e o ESP32.
- **Server.py:** Simula a troca de mensagens entre o sensor e a plataforma, funcionando como uma API.
- **Scale.c:** Realiza a comunicação entre o sensor de peso e o servidor, efetivamente conectando o sistema de monitoramento.

## **Resumindo:**  

O projeto Smart Box foi desenvolvido para criar uma interface autônoma de monitoramento para pontos de venda self-service, utilizando tecnologias de redes sem fio, sensores e integração com a nuvem através do Firebase. A implementação conta com a captura de imagens por ESP32-CAM, monitoramento de peso e transações, e o uso de um servidor Flask para simular a comunicação do sistema.

## Imagens de Exemplo

![Pinout do ESP32-CAM](https://i0.wp.com/randomnerdtutorials.com/wp-content/uploads/2020/03/ESP32-CAM-pinout-new.png?w=1000&quality=100&strip=all&ssl=1)
