# IoT-Framework---Web-Service
Aplicação Web Service do Framework para coleta de dados ambientais utilizando IoT

## Como ele funciona? ##

O Web Service faz parte do Framework desenvolvido no trabalho de conclusão de curso de Bruno Barreto Freitas, para coleta de dados ambientais utilizando IoT. Ele tem como objetivo facilitar a vida do desenvolvedor de aplicações do gênero, ao fornecer uma forma de definir as consultas sobre as coletas de dados ambientais de maneira simplifica.

### Coleta de Dados Ambientais ###
Uma coleta de dados ambientais gerada a partir do Framework possui a seguinte estrutura
- Nome do Dispositivo
- Localização
- Dados Coletados

### Consultas ###
O Web Service permite que o desenvolvedor possa configurá-lo para que as consultas possam ser baseadas em:
- Período de Tempo
- Tipo do Sensor
- Raio de Distância

### Como configurar? ###
O Web Service conta com uma classe chamada IoTEnvAPI, que possui os seguintes métodos:
- ```getColetas()```: Método que diz ao Web Service para retornar todas as coletas armazenadas
- ```basedOnPeriod()```: Método que filtra as coletas armazenadas baseadas em um período de tempo, data inicial e data final
- ```basedOnRadius()```: Método que filtra as coletas armazenadas baseadas em um raio de distância em Km, a partir de um certo ponto geográfico
- ```basedOnSensorType()```: Método que filtra as coletas armazenadas baseadas no tipo do sensor utilizado, como por exemplo, Temperatura
- ```onRoute()```: Método para especificar a rota em que a consulta definida será realizada
- ```init()```: Método para iniciar o Web Service

Exemplo de configuração:
```
var IoTEnvAPI = require('./api/iotenvapi.js')();    

IoTEnvAPI.getColetas().onRoute("/iotenv/coletas");
IoTEnvAPI.getColetas().basedOnRadius().onRoute("/iotenv/raio");
IoTEnvAPI.getColetas().basedOnRadius().basedOnSensorType().onRoute("/iotenv/raio/dado");
IoTEnvAPI.getColetas().basedOnRadius().basedOnSensorType().basedOnPeriod().onRoute("/iotenv/raio/dado/periodo");

IoTEnvAPI.init();

```
