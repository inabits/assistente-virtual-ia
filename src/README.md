# Código da Aplicação

## Estrutura

```
src/
├── app.py              # Aplicação principal (Streamlit)
└── requirements.txt    # Dependências
```

## Setup do Ollama

```bash
# 1. Instalar Ollama (ollama.com)

# 2. Baixar um modelo leve
ollama pull gpt-oss

# 3. Testar se funciona
ollama run gpt-oss "Olá!"
```

## Código completo

Todo o código-fonte está no arquivo `app.py`.

## Como Rodar

```bash
# 1. Instalar dependências
pip install -r ./src/requirements.txt

# 2. Garantir que o Ollama está rodando
ollama serve

# 3. Rodar o app
streamlit run ./src/app.py
```
