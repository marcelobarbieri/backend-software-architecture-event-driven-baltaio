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
    <li><a href="#ed-2-05">Cofluent Cloud</a></li>
    <li><a href="#ed-2-06">Tópicos</a></li>
    <li><a href="#ed-2-07">Demo - Procedure e Consume</a></li>
    <li><a href="#ed-2-08">Demo - Kafka e DDD</a></li>
</ul>

</details>

<!--#endregion -->

<!--#endregion -->

<!--#region Event-Diven Architecture -->

<h2>Event-Diven Architecture</h2>

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

<!--#region -->

<details id=""><summary></summary>

<br/>

</details>

<!--#endregion -->

<!--#endregion -->


