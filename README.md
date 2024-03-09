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

<!--#region -->

<details id=""><summary></summary>

<br/>

</details>

<!--#endregion -->

<!--#endregion -->


