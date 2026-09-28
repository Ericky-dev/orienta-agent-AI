# 🤖 ORIENTA — Agente Inteligente de Orientação Profissional e de Carreira

## 📌 Contexto

O **ORIENTA** é um agente inteligente de orientação profissional e de carreira que utiliza **IA Generativa**
para ajudar usuários a tomarem decisões mais conscientes, seguras e alinhadas com seus objetivos pessoais e profissionais.

Diferente de chatbots reativos, o ORIENTA atua de forma **consultiva**, guiando reflexões, sugerindo caminhos de aprendizado,
analisando perfis e oferecendo orientações baseadas em contexto, histórico e objetivos do usuário.

---

## 🎯 Objetivo do Agente

Ajudar o usuário a:

* Identificar possíveis caminhos de carreira
* Avaliar transições profissionais
* Planejar estudos e desenvolvimento de habilidades
* Refletir sobre escolhas profissionais com mais clareza

O agente **não substitui um orientador humano**, mas funciona como um apoio inteligente e acessível.

---

## 🧑‍💼 Persona e Tom de Voz

* **Persona:** Orientador profissional experiente, empático e didático
* **Tom:** Claro, respeitoso, motivador e realista
* **Postura:** Faz perguntas, provoca reflexão e evita respostas absolutas

---

## 🏗️ Arquitetura Geral

O ORIENTA é composto por:

* **Interface de chat** 
* **Modelo LLM Local:** Ollama (`gemma:2b`) para interpretação e geração de respostas
* **Linguagem:** Python 3
* **Persistência Local:** CSV (`histórico_atendimento.csv`) e JSON(`data/`)
* **Base de conhecimento** com informações estruturadas
* **Camada de regras** para evitar respostas incoerentes ou fora de escopo

Fluxo simplificado:

```text
Usuário → Interface  Streamlit → LLM (Ollama/Gema) + Regras/RAG → Resposta
```

---

## 🛡️ Segurança e Confiabilidade

Para evitar alucinações e respostas inadequadas, o agente:

* Limita respostas ao seu escopo de atuação
* Usa prompts restritivos e claros
* Assume incerteza quando necessário
* Não faz diagnósticos psicológicos ou promessas absolutas

---

## 📚 Base de Conhecimento

Os dados utilizados pelo agente podem incluir:

* Perfis profissionais (mockados)
* Trilhas de estudo
* Áreas de atuação e carreiras
* Habilidades técnicas e comportamentais

📁 Localização: pasta `data/`

---

## 🧠 Prompts do Agente

Os prompts definem:

* Comportamento global do agente (System Prompt)
* Exemplos de interação
* Tratamento de casos limites

📄 Documentação detalhada em: `docs/03-prompts.md`

---

## 📊 Avaliação e Métricas

Critérios de avaliação do agente:

* Clareza e coerência das respostas
* Aderência ao perfil do usuário
* Consistência ao longo da conversa
* Ausência de alucinações

📄 Ver detalhes em: `docs/04-metricas.md`

---

## 🗂️ Estrutura do Repositório

```
orienta/
├── assets/                  # Imagens e evidências de execução
├── data/                    # Base de conhecimento e perfis JSON
├── docs/                    # Documentação técnica (prompts, pitch, testes)
├── src/
│   └── orienta.py           # Código principal da aplicação
├── .gitignore
├── README.md                # Documentação principal
└── requirements.txt         # Dependências do projeto
```


# Passo a Passo de Execução do Agente ORIENTA

## 1. Configurar o Ollama

```bash

Instalar Ollama (ollama.com)

Baixar o modelo leve gemma:2b

ollama pull gemma:2b

```

## 2.Instalar Dependências

```bash

pip install -r requirements.txt

```

## 3. Garantir que o Ollama está em execução

```bash

ollama serve

```

## 4. Executar a aplicação

```bash

streamlit run ./src/orienta.py

```

## Evidências


<img width="1366" height="601" alt="Orienta-1" src="https://github.com/user-attachments/assets/9330e6d2-3a06-487d-8e48-bf1fdafff694" />

<img width="1366" height="601" alt="Orienta-2" src="https://github.com/user-attachments/assets/27c9a287-f123-4478-9fc7-5d6609593cc0" />


## 🔗 Links dos Vídeos 
# Link do Vídeo que Fala do Problema que o Orienta Resolve
https://drive.google.com/file/d/1uERk5Uc8MGXlnTG7-ynJP2DzYwTSCne8/view?usp=drive_link

***

# Link do Vídeo que fala da Solução que o Orienta dá ao Usuário
https://drive.google.com/file/d/1skowdM-cyAjPEHnr5wnttjeZa-M5M3Mr/view?usp=drive_link

***

# Link do Vídeo que Fala do Diferencial e Impacto do Projeto Orienta
https://drive.google.com/file/d/1Gowvei7ArN24EkXu29fG1r9uQCWwVuGn/view?usp=drive_link

***

## 🎥 Vídeo de Demonstração

Confira a demonstração completa do agente **ORIENTA** em funcionamento, com o passo a passo da interface e respostas em tempo real:

▶️ [Assistir ao Vídeo do ORIENTA no Google Drive](https://drive.google.com/file/d/1TgrI3BmUvXEY3Ylip_cNSMhPirmnyJGY/view?usp=drive_link)






---


