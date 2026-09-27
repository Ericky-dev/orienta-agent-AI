# 📚 Base de Conhecimento e RAG Local

## 📊 Dados Utilizados

| Arquivo | Formato | Função no Agente ORIENTA |
|---------|---------|--------------------------|
| `historico_atendimento.csv` | CSV | Registrar e contextualizar interações anteriores e sessões de chat |
| `perfil_usuario.json` | JSON | Compreender o perfil, interesses, dados demográficos e contexto do usuário |
| `metas_usuario.json` | JSON | Definir e acompanhar objetivos de carreira e estudo com prazos e status |
| `preferencias_usuario.json` | JSON | Adaptar a comunicação, o ritmo e o tom das sugestões ao estilo do usuário |
| `habilidades_usuario.json` | JSON | Mapear competências técnicas e soft skills validadas do usuário |
| `progresso_usuario.json` | JSON | Registrar a evolução contínua, marcos alcançados e dificuldades identificadas |
| `feedback_usuario.csv` | CSV | Avaliar a qualidade do atendimento e coletar notas de satisfação |

---

## 🛠️ Adaptações e Expansão dos Dados

Os dados mockados foram modificados e expandidos para atender ao escopo completo do projeto do agente inteligente de orientação profissional e de carreira (**ORIENTA**).

Foram estruturados arquivos de suporte na pasta `data/`, incluindo perfil de usuário, histórico de atendimentos, metas, preferências, progresso, habilidades e feedbacks. Essas informações funcionam como a base RAG (Retrieval-Augmented Generation) local do agente, permitindo que a LLM compreenda o contexto individual, acompanhe a evolução do usuário e ofereça orientações personalizadas e precisas.

---

## ⚙️ Estratégia de Integração

### Como os dados são carregados?

O agente **ORIENTA** acessa sua base de conhecimento em Python por meio da leitura de arquivos JSON e CSV armazenados no diretório `data/`, utilizando as bibliotecas nativas `json` e `pandas`. Os dados são carregados em memória para montar o payload de contexto dinâmico injetado a cada interação com o modelo.

```python
import json
import pandas as pd

# Carregamento seguro dos arquivos JSON da pasta data/
with open('./data/perfil_usuario.json', encoding='utf-8') as f:
    perfil = json.load(f)

with open('./data/metas_usuario.json', encoding='utf-8') as f:
    metas = json.load(f)

with open('./data/habilidades_usuario.json', encoding='utf-8') as f:
    habilidades = json.load(f)

with open('./data/preferencias_usuario.json', encoding='utf-8') as f:
    preferencias = json.load(f)

with open('./data/progresso_usuario.json', encoding='utf-8') as f:
    progresso = json.load(f)

# Carregamento dos históricos e feedbacks em formato tabular (CSV)
historico = pd.read_csv('./data/historico_atendimento.csv')
feedback = pd.read_csv('./data/feedback_usuario.csv')


## Como os dados são usados no prompt?
Os dados recuperados são consultados dinamicamente e injetados na estrutura da mensagem enviada ao modelo, garantindo que o ORIENTA personalize sua resposta com base nos objetivos e limitações do usuário.

## ⚙️ Estrutura da Base de Conhecimento 

# 1. Perfil do Usuário

{
  "nome": "João Silva",
  "idade": 22,
  "escolaridade": "Ensino Médio Completo",
  "situacao_profissional": "Estudante",
  "area_interesse_principal": "Tecnologia",
  "interesses": [
    "Programação",
    "Lógica",
    "Resolução de problemas"
  ],
  "habilidades": [
    "Raciocínio lógico",
    "Organização",
    "Aprendizado rápido"
  ],
  "experiencia_profissional": "Nenhuma",
  "objetivo_profissional": "Ingressar na área de tecnologia",
  "nivel_clareza_carreira": "baixo",
  "disponibilidade_estudo_horas_dia": 2,
  "preferencia_trabalho": {
    "ambiente": "remoto",
    "estilo": "analitico",
    "interacao_pessoas": "moderada"
  },
  "carreiras_sugeridas": [
    "Desenvolvedor Backend",
    "Analista de Sistemas",
    "Analista de Dados",
    "Front-End"
  ],
  "plano_acao": [
    {
      "etapa": "Introdução à lógica de programação",
      "duracao_estimada_meses": 2,
      "prioridade": "alta"
    },
    {
      "etapa": "Aprender linguagem Java",
      "duracao_estimada_meses": 4,
      "prioridade": "alta"
    },
    {
      "etapa": "Construir projetos práticos",
      "duracao_estimada_meses": 3,
      "prioridade": "media"
    }
  ],
  "aceita_transicao_carreira": true,
  "observacoes_agente": "Usuário demonstra afinidade com tecnologia e perfil analítico, indicado para áreas técnicas de desenvolvimento."
}

# 2. Metas do Usuário (data/metas_usuario.json)
{
  "usuario_id": "usr_001",
  "metas": [
    {
      "id": "meta_01",
      "descricao": "Definir area profissional principal",
      "categoria": "carreira",
      "prazo": "2025-12",
      "status": "em_andamento",
      "prioridade": "alta"
    },
    {
      "id": "meta_02",
      "descricao": "Concluir curso introdutorio de programacao",
      "categoria": "educacao",
      "prazo": "2026-03",
      "status": "nao_iniciada",
      "prioridade": "media"
    }
  ]
}


# 3. Histórico de Atendimento (data/historico_atendimento.csv)
data,canal,tema,resumo,resolvido
2025-09-15,chat,Orientacao de carreira,Usuario relatou indecisao profissional e iniciou diagnostico guiado,sim
2025-09-22,chat,Perfil profissional,Agente identificou perfil analitico com interesse em tecnologia,sim
2025-10-01,chat,Sugestao de carreiras,Foram sugeridas areas de desenvolvimento e analise de dados,sim
2025-10-12,chat,Plano de estudo,Criacao de plano de estudos com foco em logica e programacao,sim
2025-10-25,chat,Acompanhamento de progresso,Plano ajustado conforme evolucao informada pelo usuario,sim


# 4.Preferências do Usuario (data/preferencias_usuario.json)
{
  "usuario_id": "usr_001",
  "estilo_aprendizado": "pratico",
  "formatos_preferidos": ["texto", "exercicios"],
  "horarios_preferidos": ["noite"],
  "frequencia_interacao": "semanal",
  "nivel_detalhamento": "medio"
}


# 5.Progresso do Usuario (data/progresso_usuario.json)
{
  "usuario_id": "usr_001",
  "progresso_geral": "moderado",
  "ultima_atualizacao": "2025-10-25",
  "registros": [
    {
      "data": "2025-10-01",
      "descricao": "Usuario demonstrou maior clareza sobre interesse em tecnologia",
      "impacto": "positivo"
    },
    {
      "data": "2025-10-20",
      "descricao": "Dificuldade em manter rotina de estudos",
      "impacto": "negativo"
    }
  ]
}


# 6. feedback Usuário (data/feedback_usuario.csv)
data,canal,avaliacao,comentario
2025-10-05,chat,5,Agente foi claro e ajudou a organizar minhas ideias
2025-10-18,chat,4,Bom acompanhamento mas poderia sugerir mais exemplos praticos
2025-10-25,chat,5,Senti evolucao no meu planejamento profissional

---

## Exemplo de Contexto Montado para o Agente

[CONTEXTO DO USUÁRIO]
- Nome: João Silva
- Área de Interesse Principal: Tecnologia
- Nível de Experiência: Iniciante / Estudante
- Disponibilidade de Estudos: 2 horas por dia (Período: Noite)
- Estilo de Aprendizado: Prático (Exercícios curtos)
- Meta Ativa: Concluir curso introdutório de programação (Prazo: 2026-03)
- Status Atual: Demonstrando interesse em desenvolvimento com foco em lógica de programação.


...
