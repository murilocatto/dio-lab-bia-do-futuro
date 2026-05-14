# 🟢 Olirum — Seu Educador Financeiro

> Um agente de IA que traduz finanças em linguagem humana, usando os dados do próprio usuário como exemplo prático.

---

## O Problema

Muita gente perde dinheiro não por falta de renda, mas por falta de entendimento. Juros, CDI, Tesouro Direto — a linguagem financeira intimida e afasta quem mais precisa aprender.

O Olirum existe pra resolver isso: não como um consultor que te diz o que fazer, mas como um professor paciente que explica **por quê** cada coisa funciona do jeito que funciona.

---

## A Solução

O Olirum é um chatbot educativo que:

- usa os dados reais do cliente (transações, perfil, histórico) para criar exemplos **personalizados**
- explica conceitos financeiros com linguagem simples e analogias do dia a dia
- **nunca recomenda investimentos** — educa para que o usuário decida por conta própria
- admite quando não sabe algo, em vez de inventar

---

## Arquitetura

```
Usuário → Interface (Streamlit) → LLM (Ollama local) → Resposta
                                        ↑
                              Base de Conhecimento
                     (perfil, transações, produtos, histórico)
```

Os dados são injetados no system prompt a cada requisição, garantindo contexto completo sem necessidade de banco de dados.

---

## Base de Conhecimento

| Arquivo | Conteúdo |
|---|---|
| `perfil_investidor.json` | Dados do cliente: renda, perfil, metas |
| `transacoes.csv` | Histórico de gastos e receitas |
| `historico_atendimento.csv` | Atendimentos anteriores |
| `produtos_financeiros.json` | Produtos disponíveis para ensino |

---

## System Prompt

```
Você é o Olirum, um educador financeiro amigável e didático.

REGRAS:
- NUNCA recomende investimentos específicos, apenas explique como funcionam
- JAMAIS responda perguntas fora do tema finanças pessoais
- Use os dados fornecidos para dar exemplos personalizados
- Linguagem simples, como se explicasse para um amigo
- Se não souber algo, admita
- Responda de forma sucinta, com no máximo 3 parágrafos
```

---

## Como Rodar

```bash
# 1. Instalar Ollama e baixar o modelo
ollama pull llama3.2:3b

# 2. Instalar dependências Python
pip install streamlit pandas requests

# 3. Garantir que o Ollama está rodando
ollama serve

# 4. Iniciar a aplicação
streamlit run src/app.py
```

---

## Estrutura do Projeto

```
📁 olirum/
├── data/
│   ├── perfil_investidor.json
│   ├── transacoes.csv
│   ├── historico_atendimento.csv
│   └── produtos_financeiros.json
├── docs/
│   ├── 01-documentacao-agente.md
│   ├── 02-base-conhecimento.md
│   ├── 03-prompts.md
│   ├── 04-metricas.md
│   └── 05-pitch.md
└── src/
    └── app.py
```

---

## O que o Olirum NÃO faz

- Não recomenda onde investir
- Não acessa dados bancários reais
- Não substitui um profissional certificado
- Não responde perguntas fora do tema finanças

---

*Desenvolvido como parte do desafio de Agentes Financeiros com IA Generativa — DIO*
