# Sistema de Monitoramento para Pessoas Idosas e Pessoas com Deficiência Utilizando Arduino

## Descrição do Projeto

Esse sistema de monitoramento tem como objetivo auxiliar na segurança e no acompanhamento de pessoas idosas e pessoas com deficiência, contribuindo para uma maior autonomia e tranquilidade para familiares e responsáveis.

Utilizando Arduino e a plataforma Wokwi para simular diferentes situações do cotidiano, o sistema busca demonstrar como a tecnologia pode ser aplicada para monitorar condições importantes relacionadas ao bem-estar e à segurança dos usuários.

Inspirado nos sistemas de monitoramento presentes em trajes espaciais, o projeto adapta esse conceito para uma aplicação mais próxima da realidade, monitorando dados como temperatura, frequência cardíaca, nível de dióxido de carbono (CO₂), distância em relação a um ponto de referência e possíveis impactos ou quedas. Essas informações são exibidas em tempo real em um display LCD, e alertas sonoros são acionados quando algum valor atinge níveis considerados críticos.

---

## Objetivo da Solução

O acompanhamento de pessoas idosas e pessoas com deficiência pode representar um desafio para familiares e cuidadores, especialmente quando essas pessoas permanecem sozinhas por determinados períodos. Situações como alterações nos sinais vitais, afastamento excessivo de uma área segura ou até mesmo quedas podem exigir atenção imediata.

Pensando nisso, este projeto propõe o desenvolvimento de um protótipo utilizando sistemas embarcados para monitorar informações como temperatura corporal, frequência cardíaca, nível de CO₂, deslocamento em relação a um ponto de referência e possíveis impactos. Os dados são acompanhados em tempo real e o sistema pode emitir alertas quando detectar situações de risco, demonstrando como a tecnologia pode contribuir para um monitoramento mais eficiente e para a promoção da segurança e da qualidade de vida dos usuários.

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

A temperatura é medida pelo sensor DHT22, simulando o acompanhamento das condições físicas do usuário. Se o valor ficar abaixo de 35°C ou acima de 37,5°C, o sistema emite um alerta para indicar uma possível situação de atenção.

### Monitoramento de Batimentos Cardíacos

Os batimentos cardíacos são simulados por um potenciômetro e convertidos para valores de BPM. Quando a frequência fica muito baixa ou muito alta, o sistema gera um alerta para indicar uma possível alteração no estado de saúde do usuário.

### Monitoramento de CO₂

O nível de CO₂ também é simulado por um potenciômetro. Caso a concentração ultrapasse o limite definido, um alerta é acionado para indicar possíveis problemas relacionados à qualidade do ar no ambiente.

### Monitoramento da Distância

O joystick representa a movimentação do usuário em relação a uma área de referência previamente definida. O sistema calcula essa distância e emite um alerta quando o usuário se afasta além do limite considerado seguro, permitindo identificar possíveis situações de desorientação ou deslocamento não autorizado.

### Registro de Impactos

Os impactos são simulados por um botão. Sempre que ele é pressionado, o sistema registra a ocorrência e informa o usuário por meio de um alerta sonoro, simulando a identificação de quedas ou colisões.

### Sistema de Alertas

Para aumentar a segurança, o sistema utiliza um buzzer que é acionado sempre que detecta alguma condição crítica, como alterações nos sinais monitorados, excesso de CO₂, afastamento da área segura ou possíveis quedas.

### Exibição dos Dados

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

**Observação:** As medições ocorrem a cada 2 segundos, com o objetivo de evitar a poluição visual do Monitor Serial e do display LCD. Portanto, ao executar qualquer comando, mantenha-o ativo por pelo menos 2 segundos para que a alteração seja registrada corretamente.

1. Monte o circuito conforme o esquema de ligação.
2. Instale as bibliotecas necessárias na IDE Arduino.
3. Carregue o código para a placa Arduino.
4. Inicie a simulação no Wokwi.
5. Ajuste os potenciômetros para alterar os valores de BPM e CO₂.
6. Utilize o joystick para simular o deslocamento do usuário.
7. Pressione o botão do joystick para redefinir a origem.
8. Pressione o botão de impacto para registrar ocorrências de impacto ou queda.
9. Observe os dados exibidos no LCD e os alertas emitidos pelo buzzer.
10. Utilize o Monitor Serial para acompanhar informações detalhadas.

---

## Conclusão

A nossa proposta busca apresentar uma alternativa viável de sistema embarcado para o monitoramento de pessoas idosas e pessoas com deficiência. Por meio de sensores e componentes variados, o sistema é capaz de coletar, processar e exibir informações relevantes, auxiliando no acompanhamento das condições do usuário e contribuindo para uma resposta mais rápida diante de possíveis situações de risco.

Mesmo sendo desenvolvido em um ambiente de simulação, o protótipo demonstra uma possível aplicação prática para aumentar a segurança e a qualidade de vida dos usuários. Inspirado nos sistemas de monitoramento utilizados em trajes espaciais, o projeto adapta esses conceitos para uma realidade mais próxima do cotidiano, monitorando dados como temperatura, frequência cardíaca, nível de CO₂, deslocamento e possíveis impactos, evidenciando como a tecnologia pode ser utilizada para promover mais segurança, autonomia e tranquilidade para usuários, familiares e cuidadores.

---

## Participantes

* João Gabriel Ricardo Medeiros – 1ESPZ
* Arthur Henrique – 1ESPZ
* Enzo Dias – 1ESPZ
* Guilherme Freire – 1ESPZ
