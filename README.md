# Projeto de Redes Sem Fio - **Smart Box**

Este repositório contém os códigos e configurações do projeto **Smart Box**, uma solução de monitoramento autônomo para pontos de venda self-service no hall do campus **UFSC Araranguá**, por meio de **redes sem fio**, sensores e dispositivos IoT. A aplicação visa garantir o controle de transações de venda de produtos utilizando **sensores de fim de curso** e **sensores de peso**, conectados a um sistema baseado em **ESP32-CAM**, **ESP32** e **Firebase**. Para maior estabilidade de rede, optou-se pela tecnologia **4G** em vez da rede Wi-Fi do campus.

---

## **Sumário**

1. [Visão Geral](#visão-geral)  
2. [Equipe Responsável](#equipe-responsável)  
3. [Principais Funcionalidades](#principais-funcionalidades)  
4. [Tecnologias Utilizadas](#tecnologias-utilizadas)  
5. [Estrutura do Repositório](#estrutura-do-repositório)  
6. [Como Executar](#como-executar)  
7. [Conclusão](#conclusão)  
8. [Imagens de Exemplo](#imagens-de-exemplo)  

---

## **Visão Geral**

O **Smart Box** monitora de forma autônoma os pontos de venda self-service, controlando a abertura e fechamento da caixa, bem como a retirada dos produtos. Quando a caixa é aberta, um **sensor de fim de curso** aciona a **ESP32-CAM** para capturar imagens, que são armazenadas inicialmente no **SPIFFS** (sistema de arquivos do ESP32) e enviadas ao **Firebase**. Um **sensor de peso** (HX711 e célula de carga) é responsável por registrar a quantidade de produtos retirados, tornando o sistema completo para fins de supervisão e auditoria.

---

## **Equipe Responsável**

- **Alisson Pereira Ferreira**  
- **Emir Braz de Araújo Marques Júnior**  
- **João Pedro Tavares Santos**  
- **Monique Rosa Moraes**  
- **Nicolas Andre Baumle**  
- **Regis Nyland Bloemer**  
- **Rodrigo Guedes de Souza**

**Universidade Federal de Santa Catarina (UFSC) – Campus Araranguá**  
Caixa Postal 88.905-120 – Araranguá – SC – Brasil  

---

## **Principais Funcionalidades**

1. **Captura de Imagens**  
   - Quando a caixa é aberta, o sensor de fim de curso aciona a ESP32-CAM para registrar o evento.

2. **Monitoramento de Peso**  
   - O sensor de peso detecta a retirada de produtos em tempo real, possibilitando controle das vendas self-service.

3. **Armazenamento Local (SPIFFS) e em Nuvem (Firebase)**  
   - As imagens registradas são salvas no SPIFFS do ESP32-CAM e enviadas automaticamente para o **Firebase**, permitindo acesso remoto e seguro.

4. **Comunicação via 4G**  
   - Utilizada para garantir maior estabilidade de conexão em relação à rede Wi-Fi "eduroam" do campus.

---

## **Tecnologias Utilizadas**

### **Frontend (Simulação via Flask)**
- **Python & Flask**: Criação de um servidor local que simula a troca de dados entre os sensores e a plataforma.

### **Dispositivos IoT**
- **ESP32-CAM**: Módulo para captura de imagem e comunicação sem fio.
- **ESP32**: Gerenciamento dos sensores de peso e fim de curso.
- **Sensor de Fim de Curso (Limit Switch)**: Detecta a abertura da tampa da caixa.
- **Sensor de Peso (HX711 + célula de carga)**: Monitora a retirada de produtos.

### **Plataforma de Nuvem**
- **Firebase**: Armazenamento de imagens e dados; possibilita acesso remoto seguro.

---

## **Estrutura do Repositório**

```bash
/Smart_Box
├── Smartbox.c          # Código principal para ESP32-CAM
├── interface.py        # Simula a comunicação de dados
├── scale.c             # Código para o sensor de peso
└── server.py           # Servidor Flask
```

- **`Smartbox.c`**: Configura a ESP32-CAM para capturar fotos quando o sensor de fim de curso é acionado, armazenando-as no SPIFFS e enviando-as ao Firebase.  
- **`Interface.py`**: Simula a comunicação entre o ESP32 e o servidor Flask, formatando o conteúdo enviado.  
- **`Server.py`**: Servidor Flask que recebe as requisições dos sensores e gerencia as transações.  
- **`Scale.c`**: Gerencia o sensor de peso e envia leituras para o servidor.

---

## **Como Executar**

### 1. Clonar o Repositório

```bash
git clone https://github.com/alissonpef/Smart_Box.git
```

### 2. Configurar o Firebase

1. No **Firebase Console**, crie um novo projeto e um bucket de armazenamento.  
2. Baixe o arquivo `serviceAccountKey.json` e coloque-o na pasta `/config`.  
3. Adicione as credenciais no firmware `Smartbox.c`.

### 3. Instalar Dependências do Servidor Flask

```bash
pip install -r server/requirements.txt
```

### 4. Realizar Upload para o ESP32-CAM

1. Abra o [Arduino IDE](https://www.arduino.cc/en/software).  
2. Configure a placa como **ESP32-CAM** e selecione a porta correta.  
3. Faça o upload do arquivo `Smartbox.c` para a ESP32-CAM.

### 5. Executar o Servidor Flask

```bash
cd server
python Server.py
```

O servidor Flask simulará a recepção e envio de dados entre a plataforma e os sensores.

### 6. Simular Dados com `Interface.py`

Para verificar as transações em tempo real, rode:

```bash
python Interface.py
```

### 7. Conectar o Sensor de Peso

- Compile e envie o código `Scale.c` para o ESP32 utilizando a IDE de sua escolha (por exemplo, Arduino IDE).

### 8. Monitorar o Sistema

- Verifique as imagens e dados enviados para o Firebase.
- Observe os logs exibidos no terminal do servidor Flask.

---

## **Conclusão**

O **Smart Box** une **tecnologias de redes sem fio**, **sensores**, **ESP32**, **ESP32-CAM** e **Firebase** para criar uma solução de monitoramento autônomo de pontos de venda self-service. A captação de imagens e medições de peso em tempo real, aliada à comunicação 4G, garante **estabilidade**, **confiabilidade** e **escalabilidade**. Futuras melhorias podem incluir integração com aplicativos móveis, geração de relatórios detalhados de vendas e aplicação de métodos de machine learning para análise de comportamento do consumidor.

Em caso de dúvidas ou sugestões, **abra uma issue** ou envie um **pull request**.

---

## **Imagens de Exemplo**

![Pinout do ESP32-CAM](https://i0.wp.com/randomnerdtutorials.com/wp-content/uploads/2020/03/ESP32-CAM-pinout-new.png?w=1000&quality=100&strip=all&ssl=1)

*(Acima, um exemplo do pinout do ESP32-CAM. Você pode incluir outras imagens ou diagramas de arquitetura na pasta `/docs`.)*

---
