# 📂 Examples – Agente ORIENTA

Esta pasta contém **exemplos de uso, cenários simulados e testes de interação** do agente **ORIENTA (Agente Inteligente de Orientação Profissional e Carreira)**.

Os arquivos aqui servem como **referência prática** para validar o comportamento do agente, testar prompts e garantir que as regras definidas no projeto estão sendo respeitadas.

---

## 🎯 Objetivo da Pasta

- Demonstrar **como o ORIENTA deve responder** em situações reais
- Ajudar na **validação de métricas de qualidade**
- Facilitar testes manuais e ajustes de prompt
- Servir como apoio para futuras melhorias do agente

---

## 🧪 Tipos de Exemplos Esperados

Nesta pasta podem existir arquivos com:

- Simulações de conversas e atendimentos iniciais
- Dúvidas sobre escolha de área profissional e transição de carreira
- Orientações de plano de ação baseadas no perfil do RAG
- Perguntas fora de escopo (para testar limites do agente)
- Situações de indecisão ou falta de tempo do usuário

### 📋 Estrutura recomendada para os exemplos:
- **Entrada (Pergunta do Usuário):** A provocação ou dúvida enviada ao agente.
- **Resposta Esperada do ORIENTA:** O comportamento ideal em concordância com o prompt do sistema.
- **Análise / Observação:** Breve nota explicando por que aquela resposta é adequada (ou quais regras do prompt foram ativadas).

---

## 📌 Relação com Outras Pastas

- `docs/03-prompts.md` → Define as regras e instruções da persona do agente.
- `docs/04-metricas.md` → Avalia se as respostas dos exemplos atendem aos critérios de qualidade.
- `src/` → Código da aplicação que executa os prompts e carrega a base local em `data/`.

*Os arquivos desta pasta não são código executável, mas guias de validação de comportamento.*

---

## ✅ Boas Práticas

- Manter exemplos claros, concisos e aplicáveis ao contexto real de orientação de carreira.
- Evitar respostas genéricas ou excessivamente longas.
- Garantir o alinhamento rigoroso com o escopo do projeto (bloqueio de temas não relacionados).
- Atualizar os cenários sempre que o prompt de sistema ou os arquivos em `data/` forem ajustados.
