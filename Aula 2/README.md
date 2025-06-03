# Aula 2: Configuração de Projeto e Escolha de Template

## Conteúdo Teórico (Configurando Seu Primeiro Projeto CrewAI)

*   **Objetivo:** Apresentar o processo de configuração inicial de um projeto CrewAI, os requisitos de ambiente e a ideia de "templates".

Olá e bem-vindos de volta! Chegamos à Aula 2 do nosso curso "Primeiros Passos: Criando seu Primeiro Agente com CrewAI". Na Aula 1, tivemos uma introdução geral ao curso e seus objetivos, que é capacitar vocês a criar, configurar e executar seu primeiro agente CrewAI. O pré-requisito para este curso é ter visto a estrutura básica de projetos. Agora, vamos colocar a mão na massa virtualmente, começando com a configuração do nosso ambiente.

Configurar o ambiente inicial de um projeto é um passo crucial. É como arrumar sua bancada de trabalho antes de começar a construir algo. Uma configuração bem-feita evita problemas futuros e facilita o desenvolvimento.

**O que significa configurar um projeto CrewAI?** Significa preparar tudo o que precisamos para começar a programar nossos agentes. Isso inclui ter as ferramentas certas (como o Python), instalar a biblioteca CrewAI e configurar as dependências necessárias para que ela funcione.

**Requisitos de Sistema:** O CrewAI roda em Python, então o principal requisito é ter o Python instalado. Os fontes indicam a versão 3.10 ou superior. Ele funciona em diferentes sistemas operacionais, como Windows, Linux e macOS. Dependendo do que seu agente for fazer (por exemplo, usar modelos de linguagem que rodam localmente), você pode precisar de hardware específico como uma GPU, mas para começar, geralmente não é obrigatório.

**Instalando o CrewAI:** A forma mais comum de instalar o CrewAI é usando o gerenciador de pacotes do Python, o `pip`. O comando é simples: `pip install crewai`. Para algumas funcionalidades adicionais, como ferramentas extras para os agentes, você pode usar `pip install 'crewai[tools]'`. Os fontes também mencionam o `uv` como uma ferramenta para gerenciar dependências no desenvolvimento, mas para iniciantes, o `pip` é suficiente para começar.

**Configuração Inicial e Estrutura de Projeto:** Para projetos maiores e mais organizados, o CrewAI oferece uma Interface de Linha de Comando (CLI) que cria uma estrutura de pastas e arquivos básica para você. O comando é `crewai create crew <nome_do_projeto>`.
Essa estrutura geralmente inclui:
*   Uma pasta principal com o nome do projeto.
*   Arquivos importantes como `.gitignore` (para o controle de versão), `pyproject.toml` ou `requirements.txt` (para listar as bibliotecas), `README.md` (documentação) e `.env` (para variáveis de ambiente como chaves de API).
*   Uma pasta `src/` contendo o código-fonte principal.
*   Dentro de `src/`, pastas para organizar seus agentes (`config/agents.yaml`), tarefas (`config/tasks.yaml`), ferramentas (`tools/`) e os arquivos principais que definem a "crew" e o ponto de entrada (`crew.py`, `main.py`).
Essa estrutura ajuda muito a manter o projeto organizado e escalável.

**Escolha de Template:** O termo "template" neste contexto pode se referir a diferentes coisas. No CrewAI, ao usar a CLI (`crewai create crew`), ele gera uma *estrutura base* de arquivos que serve como um template de organização. Mas também pode se referir a *modelos* de agentes ou configurações de tarefas pré-definidas para casos de uso comuns. Para iniciantes, o mais importante é entender a estrutura básica de um projeto e como ter os arquivos essenciais para começar.

Neste curso inicial, especialmente na prática que faremos no Google Colab, focaremos em ter o ambiente pronto e os arquivos mínimos necessários para definir e executar um agente simples, sem aprofundar na estrutura completa da CLI ainda.

**Perguntas Frequentes dos Estudantes:**
*   *Como escolher o template correto para meu projeto?* Para começar, o template padrão gerado pela CLI é ótimo. Se "template" se referir a exemplos de casos de uso, a documentação e o repositório de exemplos no GitHub são ótimos recursos para se inspirar.
*   *Preciso instalar algo além do CrewAI?* Sim, você precisa do Python. Dependendo do modelo de linguagem que você usar (o "cérebro" do agente), pode precisar de bibliotecas adicionais ou ferramentas específicas, mas `pip install crewai` é o essencial.
*   *Posso usar CrewAI em qualquer sistema operacional?* Sim, CrewAI é compatível com os principais sistemas operacionais.
*   *O que fazer se ocorrer um erro na instalação?* Verifique se o Python está instalado corretamente. Tente atualizar o pip (`pip install --upgrade pip`). Consulte a documentação oficial ou a comunidade para erros específicos.

## Conteúdo Prático (Projeto Hands-On: Configurando Seu Primeiro Projeto CrewAI)

*   **Objetivo:** Preparar o ambiente de desenvolvimento instalando o CrewAI e configurando as variáveis essenciais, utilizando o Google Colab como ambiente simplificado.

Muito bem! Vimos na teoria a importância da configuração e a estrutura que o CrewAI sugere para projetos. Agora, vamos para a prática! Para simplificar os "primeiros passos", vamos usar o Google Colab. Ele nos dá um ambiente Python pronto no navegador, sem precisar configurar muita coisa localmente [User Query]. Resolveremos o problema de como ter um ambiente funcional para começar.

**(Passo a Passo no Vídeo, mostrando a tela do Google Colab):**

1.  **Abrir o Google Colab:** Vá para colab.research.google.com e crie um novo notebook.
2.  **Instalar o CrewAI:** Em uma célula de código, digite o comando de instalação. Lembre-se, para instalar pacotes no Colab, usamos `!pip install`.
    *   Digite: `!pip install crewai`
    *   (Opcional, mas útil) Digite: `!pip install 'crewai[tools]'`
    *   Execute a célula (Ctrl+Enter ou clique no botão Play). Explique que isso instala a biblioteca CrewAI e suas dependências no ambiente temporário do Colab.
3.  **Configurar a Chave de API do Modelo de Linguagem (LLM):** O CrewAI precisa de um modelo de linguagem para os agentes "pensarem". O mais comum é usar o OpenAI, que requer uma chave de API. Em um ambiente local, você usaria um arquivo `.env`. No Colab, podemos definir isso diretamente.
    *   Crie uma nova célula de código.
    *   Explique que precisamos definir uma variável de ambiente. No Colab, podemos usar o comando `%env`.
    *   Digite: `%env OPENAI_API_KEY='SUA_CHAVE_AQUI'`
    *   **Importante:** Peça aos estudantes para substituírem `'SUA_CHAVE_AQUI'` pela chave real deles. **Alerta de Segurança:** Explique que a chave é sensível e não deve ser compartilhada ou colocada diretamente em códigos que serão compartilhados publicamente (como no GitHub). Em projetos reais, o `.env` local ou variáveis de ambiente seguras em serviços de nuvem são a forma correta.
    *   Execute a célula. A chave agora está definida no ambiente do Colab para esta sessão.
4.  **Verificar a Instalação (Opcional):** Podemos tentar importar o CrewAI para ver se a instalação funcionou.
    *   Crie uma nova célula de código.
    *   Digite: `from crewai import Agent, Task, Crew, Process`
    *   Execute a célula. Se não der erro, a instalação básica funcionou.
5.  **Mencionar a Estrutura Padrão:** Embora estejamos usando o Colab simplificado, é importante saber que para projetos reais e locais, a estrutura de diretórios criada pela CLI (`crewai create crew`) é a melhor prática.
    *   Mostre rapidamente no vídeo a estrutura de pastas que vimos na teoria (pode ser um slide ou uma imagem). Explique que essa é a forma organizada de trabalhar em projetos maiores, mas para os primeiros passos, o Colab é mais rápido.

**Recapitulando:** Nesta prática, preparamos nosso ambiente de trabalho no Google Colab. Instalamos a biblioteca CrewAI e configuramos a chave de API essencial para os modelos de linguagem funcionarem. Mencionamos a estrutura de projeto padrão para referência futura. Nosso ambiente está pronto para definirmos nosso primeiro agente!
Na próxima aula, vamos focar justamente nisso: definir as propriedades do nosso agente.