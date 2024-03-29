<h1>Fundamentos do Event-Driven Architecture</h1>

> O conteúdo também foi organizado nos **commits**

<!--#region Sumário -->

<!--#region Event-Driven Architecture -->

<details><summary>Event-Driven Architecture</summary>

<ul>
    <li><a href="#ed-1-01">Introdução</a></li>
    <li><a href="#ed-1-02">Cenário</a></li>
    <li><a href="#ed-1-03">Monolíticos, Microsserviços e EDA</a></li>
    <li><a href="#ed-1-04">EDA</a></li>
    <li><a href="#ed-1-05">EDA e Microsserviços</a></li>
    <li><a href="#ed-1-06">Messages, Events, Commands</a></li>
    <li><a href="#ed-1-07">Prós</a></li>
    <li><a href="#ed-1-08">Contras</a></li>
    <li><a href="#ed-1-09">Event Storming</a></li>
    <li><a href="#ed-1-10">Como funciona o Event Storming</a></li>
    <li><a href="#ed-1-11">Mapeamento de Eventos</a></li>
    <li><a href="#ed-1-12">Mapeando os Eventos de Endereço</a></li>
    <li><a href="#ed-1-13">Mapeando Contextos Delimitados</a></li>
    <li><a href="#ed-1-14">Demo - Shared Context</a></li>
    <li><a href="#ed-1-15">Demo - Contextos Delimitados e Domain Events</a></li>
</ul>

</details>

<!--#endregion -->

<!--#region Kafka e EDA -->

<details><summary>Kafka e EDA</summary>

<ul>
    <li><a href="#ed-2-01">Kafka</a></li>
    <li><a href="#ed-2-02">Broker</a></li>
    <li><a href="#ed-2-03">Zookeeper</a></li>
    <li><a href="#ed-2-04">Rodando Kafka via Docker</a></li>
    <li><a href="#ed-2-05">Confluent Cloud</a></li>
    <li><a href="#ed-2-06">Tópicos</a></li>
    <li><a href="#ed-2-07">Demo - Procedure e Consume</a></li>
    <li><a href="#ed-2-08">Demo - Kafka e DDD</a></li>
</ul>

</details>

<!--#endregion -->

<!--#endregion -->

<!--#region Event-Driven Architecture -->

<h2>Event-Driven Architecture</h2>

<!--#region Introdução -->

<details id="ed-1-01"><summary>Introdução</summary>

<br/>

Arquitetura orientada a eventos

Objetivos:
- Entender sobre mensageria
- Microsserviços e eventos
- Arquitetura orientada a eventos
- Eventos como fonte de verdade

</details>

<!--#endregion -->

<!--#region Cenário -->

<details id="ed-1-02"><summary>Cenário</summary>

<br/>

O que a empresa faz?
- Produção
- Vendas
- Entregas

Esperado
- Mensagens, eventos e comandos
- Benefícios
- Drawbacks
- Event Storming
    - Dos eventos ao DDD
    
</details>

<!--#endregion -->

<!--#region Monolíticos, Microsserviços e EDA -->

<details id="ed-1-03"><summary>Monolíticos, Microsserviços e EDA</summary>

<br/>

![](./Assets/Images/ed001.png)

### Monolíticos

![](./Assets/Images/ed002.png)

- Escala, muda-se: tudo ou nada

### Microsserviços

![](./Assets/Images/ed003.png)

![](./Assets/Images/ed004.png)

**Ação compensatória**

</details>

<!--#endregion -->

<!--#region EDA -->

<details id="ed-1-04"><summary>EDA</summary>

<br/>

Event-Driven Architecture
- Arquitetura orientada a eventos
- Padrão de arquitetura
- Promove
    - Produção
    - Detecção
    - Consumo
    - Reação
- Tudo gira em torno de eventos, não de dados

Implementações:

![](./Assets/Images/ed005.png)

</details>

<!--#endregion -->

<!--#region EDA e Microsserviços -->

<details id="ed-1-05"><summary>EDA e Microsserviços</summary>

<br/>

Cenário de microsserviços:
- Cada MS responde por um pipe de eventos
- Desacoplados
- Utilizando Brokers

</details>

<!--#endregion -->

<!--#region Messages, Events, Commands -->

<details id="ed-1-06"><summary>Messages, Events, Commands</summary>

<br/>

Mensagem:
- Unidade básica de comunicação
- Pode ser literalmente qualquer coisa
    - String, int, objeto

Evento:
- Uma mensagem que informa diversos "listeners" que algo aconteceu
- Quem publica o evento é chamado de "Producer"
- Quem ouve o evento é chamado de "Consumer"
    - Reagem ao evento
- Criamos evento sempre no passado
    - Order_Created
    - Account_Updated
- Já aconteceu, já foi disparado

Comando:
- Representa uma ação direcionada
- Possui uma conexão 1x1
    - Entre producer e consumer
- CriarConta, RealizarPedido

</details>

<!--#endregion -->

<!--#region Prós -->

<details id="ed-1-07"><summary>Prós</summary>

<br/>

Pontos positivos:
- Desacoplamento
    - Utilizam um Broker para se comunicar
        - Broker é um middleware que abstrai a comunicação entre os serviços
- Encapsulamento
    - Podemos trabalhar de forma independente atuando no contexto correto
- Performance
    - Quase em *real-time*
    - Escalável

</details>

<!--#endregion -->

<!--#region Contras -->

<details id="ed-1-08"><summary>Contras</summary>

<br/>

Pontos negativos:
- Curva de aprendizado
    - Como definir o SOT (Source of True)
    - E quando dá errado?
    - SAGAS (Sequência de Transações Locais)
- Complexo
    - Fluxos ficam complexos
    - Recortes nunca ficam corretos
- Não tem transação
- Versionamento
    - Mudanças nos objetos dos eventos

</details>

<!--#endregion -->

<!--#region Event Storming -->

<details id="ed-1-09"><summary>Event Storming</summary>

<br/>

DDD e Event Storming

- Modelo Tradicional
    - Centralizado em Dados
    - Normalmente feito por um DBA**

- EDA
    - Centralizado em Eventos
    - Combina bem com DDD
    - Feito através de um time
        - Evento chamado **Event Storming**

Event Storming

- Finalidade
    - Modelar o domínio com base em eventos
    - Resultado da colaboração de diversos membros

- Boas Práticas
    - Convide as pessoas certas
        - Facilitador, técnicos, arquitetos, negócio
    - Tenha um board com *post-its*

</details>

<!--#endregion -->

<!--#region Como funciona o Event Storming -->

<details id="ed-1-10"><summary>Como funciona o Event Storming</summary>

<br/>

Como funciona?

- Domain Event
    - Algo que acontece no sistema e é relevante para o negócio
    - Provoca reações
    - Outros eventos respondem a eles (ação compensatória)
- Policies
    - Ocorre após um evento ser disparado
    - "Sempre que"
        - Sempre que uma conta for criada, nós enviamos um e-mail
- Externo (External Systems)
    - Algo que acontece externo ao sistema
    - Não temos controle sobre
        - Pagamentos, envios de e-mails
- Commands (Comandos)
    - Iniciados pelo usuário ou outro sistema (job)
- Aggregate (Agregados)
    - Agrupam comportamentos em comum
- Bounded Context
    - Agrupam significados em comum

</details>

<!--#endregion -->

<!--#region Mapeamento de Eventos -->

<details id="ed-1-11"><summary>Mapeamento de Eventos</summary>

<br/>

DEMO

![](./Assets/Images/ed006.png)

</details>

<!--#endregion -->

<!--#region Mapeando os Eventos de Endereço -->

<details id="ed-1-12"><summary>Mapeando os Eventos de Endereço</summary>

<br/>

![](./Assets/Images/ed007.png)

> A API indica uma validação externa

</details>

<!--#endregion -->

<!--#region Mapeando Contextos Delimitados -->

<details id=""><summary>Mapeando Contextos Delimitados</summary>

<br/>

Mapeando agregados:

![](./Assets/Images/ed008.png)

Mapeando contextos delimitados:

![](./Assets/Images/ed009.png)

*De um lado o contexto de endereços*

</details>

<!--#endregion -->

<!--#region Demo - Shared Context -->

<details id="ed-1-14"><summary>Demo - Shared Context</summary>

<br/>

Os comandos são a porta de entrada.

</details>

<!--#endregion -->

<!--#region Demo - Contextos Delimitados e Domain Events-->

<details id=""><summary>Demo - Contextos Delimitados e Domain Events</summary>

<br/>



</details>

<!--#endregion -->

<!--#endregion -->

<!--#region Kafka e EDA -->

<h2>Kafka e EDA</h2>

<!--#region Kafka -->

<details id="ed-2-01"><summary>Kafka</summary>

<br/>

Apache Kafka

Por que escolher Kafka?
- Open source
- Criado no LinkedIn
- Apache License
- Netflix, Uber, Spotify
- Feito em Java
    - ByteCode => JVM
- High throughtput
    - Não tem serialização/ deserialização
    - Tudo binário
    - Zero Copy
- Distributed Streaming Platform
    - Mensagem, Storage, Processamento

</details>

<!--#endregion -->

<!--#region Broker -->

<details id="ed-2-02"><summary>Broker</summary>

<br/>

O que é?
- Recebe, armazena e transmite as mensagens
- Funciona em conjunto com o Zookeeper
- Deve ficar em um espaço dedicado
    - Servidor dedicado, recursos dedicados
- Tem um alto nível de I/O
    - Pode afetar todo o resto
- Processo que roda no topo do OS
- Basicamente armazena e lê mensagens
    - Tudo binário
- Provavelmente vai rodar em um cluster
    - Cluster = Conjunto de servidores

</details>

<!--#endregion -->

<!--#region Zookeeper -->

<details id="ed-2-03"><summary>Zookeeper</summary>

<br/>

O que é?
- Faz o "meio-campo" entre os brokers
- Funciona como um "load balancer"
- Gerencia falhas nos brokers

</details>

<!--#endregion -->

<!--#region Rodando Kafka via Docker -->

<details id="ed-2-04"><summary>Rodando Kafka via Docker</summary>

<br/>

```ps
cd .\02 - Kafka\
wsl
docker compose up -d
```

```ps
[+] Running 23/23
 ✔ kafka 2 layers [⣿⣿]                       0B/0B     Pulled                                            251.9s
   ✔ ad79ffd84e00 Pull complete                                                            143.5s
   ✔ 218229bf30d9 Pull complete                                                            140.5s
 ✔ kafka-ui 7 layers [⣿⣿⣿⣿⣿⣿⣿]             0B/0B     Pulled                                            159.0s
   ✔ 0ce1dd7918a4 Pull complete                                                             39.4s
   ✔ 396900a6066f Pull complete                                                             75.3s
   ✔ ea77a99f32d6 Pull complete                                                             76.7s
   ✔ d8a12b986814 Pull complete                                                             78.0s
   ✔ ac59f2acb415 Pull complete                                                             79.7s
   ✔ a5385df9cb3a Pull complete                                                             81.1s
   ✔ 91a81fafb194 Pull complete                                                            139.2s
 ✔ zookeeper 11 layers [⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿]      0B/0B     Pulled                                           252.0s
   ✔ fe36fc382320 Pull complete                                                             21.1s
   ✔ 4250354b4fb7 Pull complete                                                            142.6s
   ✔ c4c5f447179d Pull complete                                                              7.0s
   ✔ 17fe3a92262f Pull complete                                                              7.8s
   ✔ 5420596c14ab Pull complete                                                             28.8s
   ✔ 0e55377ebe37 Pull complete                                                             22.7s
   ✔ da7039bb2113 Pull complete                                                             25.5s
   ✔ d389b3791c2e Pull complete                                                             27.4s
   ✔ c24709eccb2a Pull complete                                                             29.1s
   ✔ 2f1cd7af357c Pull complete                                                             95.3s
   ✔ 03b1128dd5e0 Pull complete                                                             35.4s
[+] Running 3/4
 - Network 02-kafka_kafka-network  Created                                                                50.0s
 ✔ Container zookeeper             Started                                                  30.7s
 ✔ Container kafka                 Started                                                  34.1s
 ✔ Container kafka-ui              Started                                                  46.0s
```

![](./Assets/Images/ed010.png)

http://localhost:8080/

![](./Assets/Images/ed011.png)

</details>

<!--#endregion -->

<!--#region Confluent Cloud -->

<details id="ed-2-05"><summary>Confluent Cloud</summary>

<br/>

https://www.confluent.io/

https://confluent.cloud/environments

![](./Assets/Images/ed012.png)

</details>

<!--#endregion -->

<!--#region Tópicos -->

<details id="ed-2-06"><summary>Tópicos</summary>

<br/>

#### Record, Topics e Partitions

Record
- Key, Value, Timestamp
    - Key e Value = Qualquer coisa

Topic
- Categoria de um grupo de records
- São armazenados nos Brokers
- Gerenciado pelo Zookeeper
- Delete/ Compaction (Upsert - Create or Alter)

Partitions
- Permite uma categoria existir em N brokers
- A mesma mensagem não existe em N partitions
- Replicated Partitions
    - Mesma partition em Brokers diferentes

---

#### Producer e Consumer

Producer
- Quem gera

Consumer
- Quem consome

--- 

#### Streaming

Streaming

- É o ato de processar os eventos, um a um, na ordem que chegam no sistema
    - Igual um streaming de video
- Processar as ações que acontecem no sistema em tempo real

</details>

<!--#endregion -->

<!--#region Demo - Procedure e Consume -->

<details id="ed-2-07"><summary>Demo - Procedure e Consume</summary>

<br/>

*.csproj

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>netcoreapp3.1</TargetFramework>
  </PropertyGroup>

  <ItemGroup>
    <PackageReference Include="Confluent.Kafka" Version="1.4.2" />
    <PackageReference Include="Newtonsoft.Json" Version="12.0.3" />
  </ItemGroup>

</Project>
```

csharp.config

```
# Kafka
bootstrap.servers=pkc-lzvrd.us-west4.gcp.confluent.cloud:9092
security.protocol=SASL_SSL
sasl.mechanisms=PLAIN
sasl.username=HIDDEN_VALUE
sasl.password=HIDDEN_VALUE
```

Program.cs

```c#
// Copyright 2020 Confluent Inc.

// Licensed under the Apache License, Version 2.0 (the "License");
// you may not use this file except in compliance with the License.
// You may obtain a copy of the License at

// http://www.apache.org/licenses/LICENSE-2.0

// Unless required by applicable law or agreed to in writing, software
// distributed under the License is distributed on an "AS IS" BASIS,
// WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
// See the License for the specific language governing permissions and
// limitations under the License.

using Confluent.Kafka;
using Confluent.Kafka.Admin;
using Newtonsoft.Json;
using Newtonsoft.Json.Linq;
using System;
using System.Collections.Generic;
using System.IO;
using System.Linq;
using System.Threading;
using System.Threading.Tasks;


namespace CCloud
{
    class Program
    {
        static async Task<ClientConfig> LoadConfig(string configPath, string certDir)
        {
            try
            {
                var cloudConfig = (await File.ReadAllLinesAsync(configPath))
                    .Where(line => !line.StartsWith("#"))
                    .ToDictionary(
                        line => line.Substring(0, line.IndexOf('=')),
                        line => line.Substring(line.IndexOf('=') + 1));

                var clientConfig = new ClientConfig(cloudConfig);

                if (certDir != null)
                {
                    clientConfig.SslCaLocation = certDir;
                }

                return clientConfig;
            }
            catch (Exception e)
            {
                Console.WriteLine($"An error occured reading the config file from '{configPath}': {e.Message}");
                System.Environment.Exit(1);
                return null; // avoid not-all-paths-return-value compiler error.
            }
        }

        static async Task CreateTopicMaybe(string name, int numPartitions, short replicationFactor, ClientConfig cloudConfig)
        {
            using (var adminClient = new AdminClientBuilder(cloudConfig).Build())
            {
                try
                {
                    await adminClient.CreateTopicsAsync(new List<TopicSpecification> {
                        new TopicSpecification { Name = name, NumPartitions = numPartitions, ReplicationFactor = replicationFactor } });
                }
                catch (CreateTopicsException e)
                {
                    if (e.Results[0].Error.Code != ErrorCode.TopicAlreadyExists)
                    {
                        Console.WriteLine($"An error occured creating topic {name}: {e.Results[0].Error.Reason}");
                    }
                    else
                    {
                        Console.WriteLine("Topic already exists");
                    }
                }
            }
        }
        
        static void Produce(string topic, ClientConfig config)
        {
            using (var producer = new ProducerBuilder<string, string>(config).Build())
            {
                int numProduced = 0;
                int numMessages = 10;
                for (int i=0; i<numMessages; ++i)
                {
                    var key = "alice";
                    var val = JObject.FromObject(new { count = i }).ToString(Formatting.None);

                    Console.WriteLine($"Producing record: {key} {val}");

                    producer.Produce(topic, new Message<string, string> { Key = key, Value = val },
                        (deliveryReport) =>
                        {
                            if (deliveryReport.Error.Code != ErrorCode.NoError)
                            {
                                Console.WriteLine($"Failed to deliver message: {deliveryReport.Error.Reason}");
                            }
                            else
                            {
                                Console.WriteLine($"Produced message to: {deliveryReport.TopicPartitionOffset}");
                                numProduced += 1;
                            }
                        });
                }

                producer.Flush(TimeSpan.FromSeconds(10));

                Console.WriteLine($"{numProduced} messages were produced to topic {topic}");
            }
        }

        static void Consume(string topic, ClientConfig config)
        {
            var consumerConfig = new ConsumerConfig(config);
            consumerConfig.GroupId = "dotnet-example-group-1";
            consumerConfig.AutoOffsetReset = AutoOffsetReset.Earliest;
            consumerConfig.EnableAutoCommit = false;

            CancellationTokenSource cts = new CancellationTokenSource();
            Console.CancelKeyPress += (_, e) => {
                e.Cancel = true; // prevent the process from terminating.
                cts.Cancel();
            };

            using (var consumer = new ConsumerBuilder<string, string>(consumerConfig).Build())
            {
                consumer.Subscribe(topic);
                var totalCount = 0;
                try
                {
                    while (true)
                    {
                        var cr = consumer.Consume(cts.Token);
                        totalCount += JObject.Parse(cr.Message.Value).Value<int>("count");
                        Console.WriteLine($"Consumed record with key {cr.Message.Key} and value {cr.Message.Value}, and updated total count to {totalCount}");
                    }
                }
                catch (OperationCanceledException)
                {
                    // Ctrl-C was pressed.
                }
                finally
                {
                    consumer.Close();
                }
            }
        }

        static void PrintUsage()
        {
            Console.WriteLine("usage: .. produce|consume <topic> <configPath> [<certDir>]");
            System.Environment.Exit(1);
        }

        static async Task Main(string[] args)
        {
            if (args.Length != 3 && args.Length != 4) { PrintUsage(); }
            
            var mode = args[0];
            var topic = args[1];
            var configPath = args[2];
            var certDir = args.Length == 4 ? args[3] : null;

            var config = await LoadConfig(configPath, certDir);

            switch (mode)
            {
                case "produce":
                    await CreateTopicMaybe(topic, 1, 3, config);
                    Produce(topic, config);
                    break;
                case "consume":
                    Consume(topic, config);
                    break;
                default:
                    PrintUsage();
                    break;
            }
        }
    }
}

```

```ps
dotnet run consume payments csharp.config
```

![](./Assets/Images/ed013.png)

```ps
dotnet run produce payments csharp.config
```

![](./Assets/Images/ed014.png)

![](./Assets/Images/ed015.png)

![](./Assets/Images/ed016.png)

</details>

<!--#endregion -->

<!--#region Demo - Kafka e DDD -->

<details id="ed-2-08"><summary>Demo - Kafka e DDD</summary>

<br/>

**03 - EDA/**

Pacote: Confluent.Kafka 1.7.0

**Console Application**:

![](./Assets/Images/ed017.png)

</details>

<!--#endregion -->

<!--#endregion -->