# Primeiros Passos: Criando seus Primeiros Agentes com CrewAI

Neste curso prático, você dará os primeiros passos na criação de agentes inteligentes com CrewAI, aprendendo a
confgurar, programar e executar seu primeiro agente. Ao fnal, você será capaz de criar agentes básicos, defnir comportamentos
e testar interações simples. Destinado a iniciantes, o curso é perfeito para quem deseja experimentar rapidamente o potencial do
CrewAI. Você começará com a confguração de um novo projeto e a escolha do template adequado. Em seguida, aprenderá a defnir
as propriedades e funções do agente, utilizando exemplos práticos. O curso aborda a execução do agente, análise de logs e ajustes
de comportamento. Por fm, você testará interações básicas e entenderá como evoluir para agentes mais complexos. Ao concluir, você terá confança para criar e experimentar com agentes CrewAI, acelerando sua curva de aprendizado no desenvolvimento de
IA.

Subcompetência: `Criação de Agentes`

Pré-requisitos: `Estrutura de Projetos`

Aulas:
1. Introdução à Criação de Agentes com CrewAI
2. Confguração de Projeto e Escolha de Template
3. Defnição de Propriedades e Funções do Agente
4. Execução e Testes de Agentes CrewAI
5. Análise de Logs e Ajustes de Comportamento

Conquistas:
- Ao concluir este curso, você será capaz de criar e executar seu primeiro agente utilizando CrewAI.
- Aprimore suas habilidades em CrewAI através da Criação de Agentes.
- Conquiste a Badge Primeiros Passos: Criando seu Primeiro Agente com CrewAI
- Receba o Certifcado de Conclusão para Primeiros Passos: Criando seu Primeiro Agente com CrewAI

## Prática Guiada no Google Colab

Durante o curso, todas as práticas foram organizadas em um notebook interativo no Google Colab. Você pode executar os códigos diretamente do seu navegador, sem precisar instalar nada:

[![Abrir no Google Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/drive/18RnBIaLQwPnIqfECIQqpJ5x6HLp8C5VD?usp=sharing)

Na prática, desenvolvemos o seguinte projeto de Agentes Inteligentes neste curso:

```mermaid
---
config:
  layout: dagre
  theme: neo-dark
---
flowchart TD
  subgraph C["🤖 Crew: Python + CrewAI"]
    subgraph Agentes["Agentes"]
      MP["🧑‍🏫 Mentor Python"]
      EC["👨‍💻 Especialista CrewAI"]
      GI["💡 Gerador de Ideias"]
    end
    subgraph Tarefas["Tarefas"]
      T1["📘 Guia Iniciante em Python"]
      T2["🔧 Tutorial de Instalação CrewAI"]
      T3["🤩 Ideias de Projetos com Python e CrewAI no Colab"]      
      subgraph Saídas["Saídas"]
        O1["📄 guia_python.md"]
        O2["📄 tutorial_crewai.md"]
        O3["📄 projetos_colab.md"]
      end
    end
  end
  MP --> T1 --> O1
  EC --> T2 --> O2
  GI --> T3 --> O3

```
