# Aula 3: Definição de Propriedades e Funções do Agente

## Conteúdo Teórico (Definindo Propriedades e Funções do Seu Agente CrewAI)

*   **Objetivo:** Ensinar a definir as propriedades essenciais de um agente CrewAI e explicar como elas influenciam seu comportamento.

Bem-vindos de volta à Aula 3! Na aula anterior, configuramos nosso ambiente de trabalho, instalamos o CrewAI e deixamos tudo pronto no Google Colab. Agora, vamos dar vida ao nosso projeto definindo quem será nosso primeiro "AI Agent".

Em CrewAI, um **Agente** é uma entidade autônoma que realiza ações. Mas para ele saber *como* agir, precisamos definir suas características, suas **Propriedades**. Pense nisso como dar uma identidade e uma função a ele.

As propriedades mais importantes para definir um agente CrewAI são:
1.  **Papel (Role):** Define a função ou especialidade do agente na "equipe". É quem ele *é*. O papel influencia como ele aborda os problemas e interage.
    *   Exemplos: "Pesquisador Sênior", "Analista Financeiro", "Gerente de Projetos", "Escritor Criativo".
2.  **Objetivo (Goal):** Define o objetivo principal do agente a longo prazo ou a sua missão geral. É o que ele busca alcançar.
    *   Exemplos: "Encontrar as últimas tendências em IA", "Criar relatórios detalhados baseados em dados", "Otimizar processos logísticos", "Gerar ideias de conteúdo inovadoras".
3.  **História de Fundo (Backstory):** Uma descrição opcional, mas muito útil, que dá contexto e personalidade ao agente. Ajuda a refinar o comportamento e a "voz" do agente.
    *   Exemplos: "Você é um pesquisador experiente conhecido por encontrar informações relevantes rapidamente", "Você é um analista meticuloso com um olho para detalhes em dados complexos", "Você é um escritor premiado focado em engajar o público".

Ao definir o Papel, Objetivo e História de Fundo, você está moldando a "personalidade" do seu agente, dizendo a ele qual perspectiva usar e qual tipo de resultado é esperado dele. Uma boa modelagem dessas propriedades é crucial para que o agente se comporte da maneira que você deseja e contribua efetivamente para o projeto.

Além dessas, um agente pode ter outras capacidades ou propriedades, como:
*   **Ferramentas (Tools):** Recursos externos que o agente pode usar, como acesso à internet, calculadoras, ou APIs. Veremos isso em cursos mais avançados.
*   Capacidade de **Delegar** tarefas para outros agentes ou ter **Memória** para conversas. Também tópicos mais avançados.
*   Configurações como `verbose=True`, que mostra o "pensamento" do agente durante a execução, o que é muito útil para depuração e entendimento.

Para iniciantes, focar no Papel, Objetivo e História de Fundo é o suficiente para criar um agente funcional.

As "funções" mencionadas no título da aula no contexto do CrewAI para iniciantes se referem mais às capacidades que definimos para o agente através de suas propriedades (como usar ferramentas) ou as ações que ele realiza ao executar uma **Tarefa** (que veremos na próxima aula). Não é que definimos funções Python *dentro* do objeto agente de forma direta no nível básico. As propriedades e as tarefas definem o que ele faz.

**Perguntas Frequentes dos Estudantes:**
*   *Quais propriedades são obrigatórias para um agente CrewAI?* Para criar um agente, você geralmente precisa definir pelo menos o `role` e o `goal`. O `backstory` é altamente recomendado.
*   *Como posso adicionar novas funções ao agente?* Você adiciona capacidades ao agente dando a ele acesso a `tools` (ferramentas) ou definindo `tasks` (tarefas) específicas que ele deve realizar. A lógica complexa fica nas ferramentas ou na orquestração das tarefas.
*   *É possível alterar as propriedades depois de criar o agente?* Sim, você pode criar o objeto `Agent` com as propriedades e, antes de iniciar a Crew, pode modificá-las programaticamente.
*   *Como garantir que o agente responda corretamente?* Uma boa definição de Papel, Objetivo e História de Fundo é o primeiro passo. O `expected_output` da tarefa (veremos na próxima aula) também guia o agente. Testes e ajustes são essenciais (veremos nas próximas aulas).

## Conteúdo Prático (Projeto Hands-On: Definindo Propriedades e Funções do Agente)

*   **Objetivo:** Implementar a definição de um agente básico com suas propriedades essenciais em código Python no Google Colab.

Ótimo! Agora que entendemos o que são as propriedades de um agente, vamos voltar ao nosso notebook no Google Colab que configuramos na aula anterior. Nosso objetivo é criar nosso primeiro objeto Agente com suas propriedades definidas. Resolveremos o problema de como traduzir os conceitos de Papel, Objetivo e História de Fundo em código.

**(Passo a Passo no Vídeo, mostrando a tela do Google Colab):**
1.  **Abrir o Notebook do Colab:** Reabra o notebook que você usou na Aula 2. Verifique se as células de instalação (`!pip install`) e configuração da chave de API (`%env`) foram executadas (ou execute-as novamente se a sessão expirou).
2.  **Importar a Classe Agent:** Precisamos da classe `Agent` da biblioteca CrewAI para criar nosso agente.
    *   Crie uma nova célula de código.
    *   Digite: `from crewai import Agent`.
    *   Execute a célula.
3.  **Definir as Propriedades do Agente:** Agora, vamos criar um agente. Para este exemplo, vamos criar um "Pesquisador de Tendências em IA".
    *   Crie uma nova célula de código.
    *   Vamos definir as propriedades que vimos na teoria: `role`, `goal` e `backstory`.
    *   Digite o seguinte código:
        ```python
        pesquisador = Agent(
          role='Pesquisador de Tendências em IA', # Quem ele é
          goal='Encontrar as últimas e mais relevantes tendências em Inteligência Artificial para 2025', # O que ele busca
          backstory='Você é um pesquisador experiente e curioso, especializado em identificar novidades e avanços no campo da Inteligência Artificial. Sua paixão é descobrir o futuro da IA.', # Contexto e personalidade
          verbose=True # Configuração útil para ver o processo
        )
        ```
    *   Explique cada linha: Estamos criando uma instância da classe `Agent` e guardando-a na variável `pesquisador`. Passamos as propriedades `role`, `goal` e `backstory` como argumentos. Adicionamos `verbose=True` para nos ajudar depois.
    *   Execute a célula. Se não der erro, o agente foi criado em memória.

**Recapitulando:** Nesta prática simples, demos um grande passo: criamos nosso primeiro objeto Agente no CrewAI e definimos suas propriedades essenciais: quem ele é (Papel), o que ele quer alcançar (Objetivo) e um pouco sobre sua "personalidade" (História de Fundo). Ele agora tem uma identidade.
Na próxima aula, vamos dar ao nosso agente algo para *fazer*, introduzindo o conceito de Tarefa e aprendendo a executá-lo.