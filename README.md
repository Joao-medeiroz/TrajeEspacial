# Sistema de Monitoramento para Trajes Espaciais Utilizando Arduino

## Descrição do Projeto

O projeto consiste no desenvolvimento de um sistema de monitoramento embarcado capaz de coletar e exibir informações importantes para a segurança de astronautas durante missões espaciais. A proposta foi desenvolvida utilizando Arduino e simulada na plataforma Wokwi, servindo como um protótipo conceitual de uma tecnologia que poderia ser integrada aos trajes espaciais.

O sistema monitora variáveis relevantes para a saúde e segurança do astronauta, como temperatura, frequência cardíaca, concentração de dióxido de carbono (CO₂), distância em relação a um ponto de referência e registro de impactos sofridos durante a missão.

Todos os dados são exibidos em tempo real em um display LCD e podem gerar alertas sonoros quando valores críticos são identificados.

---

# Objetivo da Solução

A exploração espacial exige o monitoramento constante das condições físicas dos astronautas e do ambiente em que estão inseridos. Durante atividades extraveiculares, qualquer alteração nos sinais vitais, na qualidade do ar ou na posição do astronauta pode representar um risco significativo para a missão.

O objetivo deste projeto é desenvolver um protótipo capaz de monitorar parâmetros essenciais para a segurança dos astronautas, fornecendo informações em tempo real e emitindo alertas quando condições potencialmente perigosas forem detectadas.

O sistema foi projetado para:

* Monitorar a temperatura do traje espacial;
* Acompanhar os batimentos cardíacos do astronauta;
* Monitorar a concentração de CO₂ presente no ambiente interno do traje;
* Calcular a distância em relação à nave ou ponto de referência;
* Registrar impactos sofridos durante deslocamentos ou operações;
* Emitir alertas em situações de risco.

Dessa forma, o projeto demonstra como sistemas embarcados podem auxiliar na segurança e no suporte às operações espaciais.

---

# Componentes Utilizados

## Hardware

* Arduino Uno
* Sensor de temperatura DHT22
* Display LCD 16x2 com interface I2C
* Joystick analógico
* Potenciômetro para simulação dos batimentos cardíacos
* Potenciômetro para simulação dos níveis de CO₂
* Push Button para simulação de impactos
* Buzzer piezoelétrico
* Protoboard
* Cabos Jumpers

## Bibliotecas

* DHT.h
* Wire.h
* LiquidCrystal_I2C.h
* math.h

# Explicação do Funcionamento

## Monitoramento de Temperatura

A temperatura é obtida através do sensor DHT22. Em um cenário real, esse sensor poderia estar localizado no interior do traje espacial para monitorar as condições térmicas do astronauta. Caso a temperatura fique abaixo de 35°C ou acima de 37,5°C, o sistema considera a situação crítica e ativa um alerta.

## Monitoramento de Batimentos Cardíacos

Os batimentos cardíacos são simulados por um potenciômetro. O Arduino converte os valores analógicos para uma faixa entre 40 e 180 BPM,
em uma aplicação real, o potenciômetro seria substituído por um sensor biomédico capaz de medir a frequência cardíaca do astronauta.
Valores inferiores a 50 BPM ou superiores a 120 BPM geram alerta sonoro.


## Monitoramento de CO₂

Outro potenciômetro é utilizado para simular a concentração de dióxido de carbono presente no traje, os valores são convertidos para uma faixa 
entre 400 ppm e 2000 ppm e quando o nível ultrapassa 1000 ppm, o sistema gera um alerta indicando possível comprometimento da qualidade 
do ar respirado pelo astronauta.


## Monitoramento da Distância

O joystick representa o deslocamento do astronauta em relação a um ponto de origem e cada movimentação registrada equivale a 20 metros. 
O sistema utiliza coordenadas cartesianas e aplica a fórmula da distância euclidiana para calcular a distância entre a posição atual e a origem definida.
O botão integrado ao joystick permite redefinir a origem a qualquer momento, mas quando a distância ultrapassa 100 metros, um alerta é acionado.


## Registro de Impactos

O botão de impacto simula colisões ou choques sofridos pelo astronauta durante suas atividades,
cada acionamento registra um novo impacto e incrementa um contador exibido no display.
O sistema também emite um alerta sonoro sempre que um impacto é detectado.


## Sistema de Alertas

O buzzer é responsável por alertar o usuário quando alguma condição crítica é identificada.
Os alertas são ativados quando:

* Temperatura > 37,5°C
* Temperatura < 35°C
* Distância ≥ 100 m
* BPM > 120
* BPM < 50
* CO₂ > 1000 ppm
* Impacto detectado


## Exibição dos Dados

As informações são apresentadas no display LCD no seguinte formato:
T:36 CO2:400
D:40 B:73 I:03

Onde:

* T = Temperatura (°C)
* CO2 = Concentração de CO₂ (ppm)
* D = Distância (m)
* B = Batimentos Cardíacos (BPM)
* I = Quantidade de Impactos Registrados

Além disso, os dados também são enviados para o Monitor Serial da IDE Arduino.

# Estrutura do Circuito

## Sensor DHT22

* VCC → 5V
* GND → GND
* DATA → Pino Digital 2

## Joystick

* VCC → 5V
* GND → GND
* VRX → A0
* VRY → A1
* SW → Pino Digital 3

## Potenciômetro BPM

* Terminal central → A2
* Extremidades → 5V e GND

## Potenciômetro CO₂

* Terminal central → A3
* Extremidades → 5V e GND

## Botão de Impacto

* Um terminal → Pino Digital 4
* Outro terminal → GND

## Buzzer

* Terminal positivo → Pino Digital 13
* Terminal negativo → GND

## Display LCD I2C

* VCC → 5V
* GND → GND
* SDA → A4
* SCL → A5


# Instruções de Execução

1. Monte o circuito conforme o esquema de ligação.
2. Instale as bibliotecas necessárias na IDE Arduino.
3. Carregue o código para a placa Arduino.
4. Inicie a simulação no Wokwi.
5. Ajuste os potenciômetros para alterar os valores de BPM e CO₂.
6. Utilize o joystick para simular o deslocamento do astronauta.
7. Pressione o botão do joystick para redefinir a origem.
8. Pressione o botão de impacto para registrar colisões.
9. Observe os dados exibidos no LCD e os alertas emitidos pelo buzzer.
10. Utilize o Monitor Serial para acompanhar informações detalhadas.

*Obs: As medições ocorrem a cada 2 segundos, com o objetivo de evitar a poluição visual do serial monitor e display. Portanto, ao executar qualquer comando, certifique-se que o mantenha por pelo menos 2 segundos em atividade.


# Conclusão

O projeto demonstra a aplicação de sistemas embarcados para monitoramento de astronautas em missões espaciais com integração de sensores, atuadores e dispositivos de exibição para coletar, processar e apresentar informações relevantes em tempo real.
Embora desenvolvido em ambiente de simulação, o protótipo representa uma proposta viável para futuras aplicações voltadas à segurança espacial, permitindo acompanhar indicadores importantes como temperatura, batimentos cardíacos, concentração de CO₂, distância em relação à nave e ocorrência de impactos.
Dessa forma, o projeto evidencia como tecnologias embarcadas podem contribuir para aumentar a segurança dos astronautas e auxiliar no sucesso das operações espaciais.
