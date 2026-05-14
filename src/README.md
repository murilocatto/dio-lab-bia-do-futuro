# Passo a passo de execução

## Setup do Ollama

````bash
# 1. Instalar Ollama (Ollama.com)
# 2. Baixar um modelo leve
ollama pull llama3.2:3b

# 3. Testar se funciona
ollama run llama3.2:3b "Olá"
````

## código completo

Todo código fonte esta no arquivo `app.py`.

## como rodar

```bash
# 1. Instalar dependencias
pip install streamlit pandas requests

# 2. Garantir que Ollama está rodando
ollama serve

# 3. Rodar o app
streamlit run app.py
```
