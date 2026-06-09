# Sistema de Monitoramento para Trajes Espaciais Utilizando Arduino

## Descrição do Projeto

Esse sistema de monitoramento tem como objetivo auxiliar na segurança dos astronautas durante missões no espaço.

Utilizando Arduino e a plataforma Wokwi para simular as adversidades nessas viagens.

O sistema monitora dados como temperatura, frequência cardíaca, nível de dióxido de carbono (CO₂), distância em relação a um ponto de referência e possíveis impactos sofridos durante a missão. Essas informações são exibidas em tempo real em um display LCD, e alertas sonoros são acionados quando algum valor atinge níveis considerados críticos.

---

## Objetivo da Solução

A exploração espacial envolve diversos desafios e nessas situações, é importante monitorar constantemente as condições físicas do astronauta e do ambiente, pois qualquer alteração pode comprometer sua segurança e o sucesso da missão.

Pensando nisso, este projeto propõe o desenvolvimento de um protótipo utilizando sistemas embarcados para monitorar informações como temperatura, frequência cardíaca, nível de CO₂, distância em relação à nave e impactos sofridos durante a missão. Os dados são acompanhados em tempo real e o sistema pode emitir alertas quando detectar situações de risco, demonstrando como a tecnologia pode contribuir para operações espaciais mais seguras.

---

## Componentes Utilizados

### Hardware

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

### Bibliotecas

* DHT.h
* Wire.h
* LiquidCrystal_I2C.h
* math.h

---

## Explicação do Funcionamento

### Monitoramento de Temperatura

A temperatura é medida pelo sensor DHT22, simulando as condições dentro do traje espacial. Se o valor ficar abaixo de 35°C ou acima de 37,5°C, o sistema emite um alerta para indicar uma possível situação de risco.

### Monitoramento de Batimentos Cardíacos

Os batimentos cardíacos são simulados por um potenciômetro e convertidos para valores de BPM. Quando a frequência fica muito baixa ou muito alta, o sistema gera um alerta para chamar a atenção do astronauta.

### Monitoramento de CO₂

O nível de CO₂ também é simulado por um potenciômetro. Caso a concentração ultrapasse o limite definido, um alerta é acionado para indicar possíveis problemas na qualidade do ar.

### Monitoramento da Distância

O joystick representa a movimentação do astronauta em relação à nave. O sistema calcula essa distância e emite um alerta quando o astronauta se afasta além do limite seguro.

### Registro de Impactos

Os impactos são simulados por um botão. Sempre que ele é pressionado, o sistema registra a ocorrência e informa o usuário por meio de um alerta sonoro.

### Sistema de Alertas

Para aumentar a segurança, o sistema utiliza um buzzer que é acionado sempre que detecta alguma condição crítica, como alterações nos sinais monitorados, excesso de CO₂, grande distância da nave ou impactos.

---

## Exibição dos Dados

As informações são apresentadas no display LCD no seguinte formato:

```text
T:36 CO2:400
D:40 B:73 I:03
```

Onde:

* T = Temperatura (°C)
* CO2 = Concentração de CO₂ (ppm)
* D = Distância (m)
* B = Batimentos Cardíacos (BPM)
* I = Quantidade de Impactos Registrados

Além disso, os dados também são enviados para o Monitor Serial da IDE Arduino.

---

## Estrutura do Circuito

### Sensor DHT22

* VCC → 5V
* GND → GND
* DATA → Pino Digital 2

### Joystick

* VCC → 5V
* GND → GND
* VRX → A0
* VRY → A1
* SW → Pino Digital 3

### Potenciômetro BPM

* Terminal central → A2
* Extremidades → 5V e GND

### Potenciômetro CO₂

* Terminal central → A3
* Extremidades → 5V e GND

### Botão de Impacto

* Um terminal → Pino Digital 4
* Outro terminal → GND

### Buzzer

* Terminal positivo → Pino Digital 13
* Terminal negativo → GND

### Display LCD I2C

* VCC → 5V
* GND → GND
* SDA → A4
* SCL → A5

---

## Instruções de Execução

**Obs: As medições ocorrem a cada 2 segundos, com o objetivo de evitar a poluição visual do serial monitor e display. Portanto, ao executar qualquer comando, certifique-se que o mantenha por pelo menos 2 segundos em atividade.**

* Monte o circuito conforme o esquema de ligação.
* Instale as bibliotecas necessárias na IDE Arduino.
* Carregue o código para a placa Arduino.
* Inicie a simulação no Wokwi.
* Ajuste os potenciômetros para alterar os valores de BPM e CO₂.
* Utilize o joystick para simular o deslocamento do astronauta.
* Pressione o botão do joystick para redefinir a origem.
* Pressione o botão de impacto para registrar colisões.
* Observe os dados exibidos no LCD e os alertas emitidos pelo buzzer.
* Utilize o Monitor Serial para acompanhar informações detalhadas.

---

## Conclusão

A nossa proposta busca apresentar uma alternativa viável de Sistemas embarcados para o monitoramento de astronautas durante missões espaciais, por meio de sensores e componentes variados, o sistema é capaz de coletar e mostrar essas informações, auxiliando no acompanhamento das condições do astronauta durante a missão.

Mesmo sendo desenvolvido em um ambiente de simulação, o protótipo demonstra uma possível solução para aumentar a segurança em operações espaciais. O sistema monitora dados como temperatura, frequência cardíaca, nível de CO₂, distância em relação à nave e impactos sofridos, mostrando como a tecnologia pode contribuir para a proteção dos astronautas e para o sucesso das missões.

---

## Participantes

João Gabriel Ricardo Medeiros - 1ESPZ
Arthur Henrique - 1ESPZ
Enzo Dias - 1ESPZ
Guilherme Freire - 1ESPZ
