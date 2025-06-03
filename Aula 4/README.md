# Aula 4: Execução e Testes de Agentes CrewAI

## Conteúdo Teórico (Executando e Testando Seu Agente CrewAI na Prática)

*   **Objetivo:** Demonstrar como executar um processo no CrewAI com um agente e uma tarefa, e realizar um teste básico observando a saída.

Olá a todos! Na aula anterior, criamos a "identidade" do nosso primeiro agente CrewAI, definindo seu Papel, Objetivo e História de Fundo. Agora, na Aula 4, vamos dar a ele uma "missão" e colocá-lo para trabalhar!

Agentes em CrewAI não trabalham sozinhos. Eles executam **Tarefas**. Uma Tarefa é uma ação específica ou um objetivo pontual que o agente precisa completar. É o "o quê" fazer. Uma tarefa tem uma `description` (descrição) clara do que fazer e um `expected_output` (resultado esperado). E o mais importante: ela é `agent` (atribuída) a um agente específico.

Para orquestrar um ou mais agentes executando tarefas, usamos o conceito de **Crew**. Uma Crew é a "equipe" ou "tripulação" que gerencia os agentes e o fluxo das tarefas. A Crew define quais agentes estão participando e qual `process` (processo) eles seguirão para executar as tarefas. O processo pode ser sequencial (tarefas executadas uma após a outra) ou hierárquico (com um agente "gerente"). Para iniciantes, o processo sequencial é o mais simples.

Uma vez que temos agentes, tarefas atribuídas a eles e uma Crew montada, podemos iniciar a execução! O método para fazer isso é o `kickoff()` da Crew. Quando você chama `crew.kickoff()`, a Crew começa a orquestrar os agentes para executar suas tarefas definidas, seguindo o processo especificado.

Realizar testes básicos é simplesmente executar sua Crew e observar o que acontece. Com a configuração `verbose=True` que usamos no agente e na Crew, o CrewAI mostrará o "pensamento" do agente enquanto ele trabalha, as tarefas que ele está executando e os resultados. Isso é uma forma inicial de "logs" e nos ajuda a validar se o agente está entendendo a tarefa e produzindo o tipo de saída esperado. Testar frequentemente durante o desenvolvimento é uma boa prática.

**Perguntas Frequentes dos Estudantes:**
*   *Como saber se o agente está funcionando corretamente?* Observe a saída no terminal ou no notebook (se `verbose=True`). O agente mostrará o que está pensando e fazendo. O resultado final da tarefa (o `expected_output`) deve ser similar ao que você esperava.
*   *O que fazer se o agente não responder?* Verifique se a chave de API do LLM está configurada corretamente e se há saldo na sua conta do provedor do LLM. Verifique se há erros de digitação no código. Consulte a documentação.
*   *Posso testar o agente com diferentes entradas?* Sim! Você pode modificar a descrição da tarefa ou passar inputs diferentes para a Crew, simulando cenários variados para ver como o agente se comporta.
*   *Como registrar os resultados dos testes?* Para testes básicos, observar e talvez copiar o output verbose é o suficiente. Para projetos maiores, CrewAI Enterprise e integrações oferecem ferramentas de monitoramento e logging mais avançadas.

## Conteúdo Prático (Projeto Hands-On: Executando e Testando Seu Agente CrewAI)**

*   **Objetivo:** Definir uma tarefa simples, criar uma Crew com o agente definido na aula anterior e a tarefa, e executar a Crew no Google Colab, observando o output.

Excelente! Já temos nosso agente definido. Agora, vamos dar a ele uma tarefa para executar e ver a mágica acontecer! Continuaremos no nosso notebook do Google Colab. Resolveremos o problema de como fazer nosso agente realizar uma ação específica.

**(Passo a Passo no Vídeo, mostrando a tela do Google Colab):**
1.  **Abrir o Notebook do Colab:** Reabra o notebook. Verifique (e execute se necessário) as células de instalação (`!pip install`) e configuração da chave de API (`%env`), e a célula onde definimos o agente `pesquisador`.
2.  **Importar as Classes Task, Crew, e Process:** Precisamos das classes para definir a tarefa, a equipe e o tipo de processo.
    *   Crie uma nova célula de código.
    *   Digite: `from crewai import Task, Crew, Process`. A classe `Agent` já deve estar importada.
    *   Execute a célula.
3.  **Definir a Tarefa:** Vamos criar uma tarefa simples para o nosso `pesquisador`: "Listar 5 tendências atuais em IA".
    *   Crie uma nova célula de código.
    *   Defina a tarefa usando a classe `Task`.
    *   Digite o seguinte código:
        ```python
        tarefa_pesquisa = Task(
          description='Liste 5 das tendências mais atuais e relevantes em Inteligência Artificial para o ano de 2025.', # O que fazer
          expected_output='Uma lista numerada com 5 tendências de IA para 2025, cada uma com uma breve explicação.', # O que esperamos
          agent=pesquisador # Atribui esta tarefa ao agente 'pesquisador'
        )
        ```
    *   Explique cada parte: Criamos um objeto `Task`, damos a ele uma `description` clara e um `expected_output` para guiar o agente. Crucialmente, usamos `agent=pesquisador` para dizer que esta tarefa é para o agente que criamos na aula anterior.
    *   Execute a célula. A tarefa está definida.
4.  **Criar a Crew:** Agora, vamos juntar o agente e a tarefa em uma Crew.
    *   Crie uma nova célula de código.
    *   Usamos a classe `Crew`.
    *   Digite o seguinte código:
        ```python
        equipe_ia = Crew(
          agents=[pesquisador], # Lista de agentes na equipe
          tasks=[tarefa_pesquisa], # Lista de tarefas que a equipe vai executar
          process=Process.sequential, # Define o processo como sequencial
          verbose=True # Configuração útil para ver o processo da Crew também
        )
        ```
    *   Explique: Criamos um objeto `Crew`. Passamos uma lista de agentes (no nosso caso, apenas o `pesquisador`) e uma lista de tarefas (`tarefa_pesquisa`). Definimos o `process` como `Process.sequential` (a forma mais simples de executar tarefas uma após a outra). Adicionamos `verbose=True` aqui também para ver o output detalhado da orquestração da Crew.
    *   Execute a célula. A Crew está montada.
5.  **Executar a Crew:** É o momento de colocar tudo para funcionar!
    *   Crie uma nova célula de código.
    *   Chame o método `kickoff()` da Crew.
    *   Digite o seguinte código:
        ```python
        resultado = equipe_ia.kickoff()
        print("### Resultado Final:")
        print(resultado)
        ```
    *   Explique: Chamamos `equipe_ia.kickoff()` para iniciar o processo. O resultado final é armazenado na variável `resultado` e depois o imprimimos.
    *   Execute a célula. **Este é o nosso primeiro teste básico!**

**Observando o Output:** A célula vai executar e você verá uma série de mensagens (por causa do `verbose=True`). Isso inclui o agente "pensando" (`> Entering new CrewAgentExecutor chain...`) e o resultado final. Analise se o resultado final se parece com a lista numerada de 5 tendências que você pediu no `expected_output`.

**Recapitulando:** Nesta prática, definimos uma tarefa simples, juntamos nosso agente e a tarefa em uma Crew, e executamos o processo pela primeira vez. O output verbose nos deu uma visão do que o agente fez.
Na próxima aula, vamos nos aprofundar nesse output verbose, que são os logs básicos, para entender melhor o que aconteceu e como podemos usar isso para melhorar o comportamento do agente.