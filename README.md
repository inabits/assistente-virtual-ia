# 🤖 Lia - Aliada Financeira

## O que é a Lia?

A **Lia — Aliada Financeira** é uma mentora de educação financeira baseada em Inteligência Artificial, criada para ajudar principalmente jovens profissionais que estão começando a organizar sua vida financeira.

Ela funciona como uma **amiga que entende de finanças**: acompanha os hábitos financeiros do usuário, explica conceitos de forma simples, utiliza exemplos práticos baseados em seus próprios dados e emite alertas preventivos quando identifica comportamentos que podem comprometer seu orçamento.

A Lia não tem como objetivo apenas responder dúvidas, mas ajudar o usuário a **entender sua própria realidade financeira** e desenvolver hábitos mais conscientes.

---

### O que a Lia faz:

- Ensina educação financeira de forma simples, clara e acessível.
- Analisa receitas e despesas para identificar padrões de consumo.
- Emite alertas preventivos quando identifica possíveis gastos excessivos ou comportamentos fora do padrão.
- Acompanha metas financeiras, como a construção de uma reserva de emergência.
- Explica conceitos financeiros utilizando exemplos práticos e situações do dia a dia.
- Personaliza a experiência utilizando os dados financeiros e o perfil do usuário disponíveis em seu contexto.
- Mantém a continuidade do atendimento utilizando o histórico de interações anteriores.
- Orienta de maneira amigável e sem julgamentos, incentivando o usuário a melhorar seus hábitos.
- Dá "puxões de orelha" quando necessário, alertando o usuário sobre decisões que podem prejudicar sua organização financeira.
- Incentiva a evolução financeira, reconhecendo pequenas conquistas e progressos.
- Explica produtos financeiros de forma educativa, apresentando características, riscos, custos, liquidez e diferenças entre alternativas.

---

### O que a Lia NÃO faz:

- Não recomenda investimentos específicos ou indica produtos para compra.
- Não recomenda corretoras, ativos ou percentuais de carteira.
- Não realiza ordens de compra ou venda.
- Não toma decisões financeiras pelo usuário.
- Não substitui um consultor financeiro ou outro profissional especializado.
- Não inventa informações, valores ou dados financeiros que não estejam disponíveis em seu contexto.
- Não fornece informações sobre outros usuários ou acessa dados financeiros de terceiros.
- Não solicita senhas, códigos de segurança ou dados bancários sensíveis.
- Não promete rentabilidade, lucro ou resultados financeiros.
- Não utiliza os produtos disponíveis em sua base para realizar recomendações personalizadas de investimento.
- Não responde a assuntos que estejam fora do seu escopo de educação e organização financeira.

---

## Estrutura do Repositório

```
📁 assistente-virtual-ia/
│
├── 📄 README.md
│
├── 📁 data/                          # Dados mockados para o agente
│   ├── historico_atendimento.csv     # Histórico de atendimentos (CSV)
│   ├── perfil_investidor.json        # Perfil do cliente (JSON)
│   ├── produtos_financeiros.json     # Produtos disponíveis (JSON)
│   └── transacoes.csv                # Histórico de transações (CSV)
│
├── 📁 docs/                          # Documentação do projeto
│   ├── 01-documentacao-agente.md     # Caso de uso e arquitetura
│   ├── 02-base-conhecimento.md       # Estratégia de dados
│   ├── 03-prompts.md                 # Engenharia de prompts
│   ├── 04-metricas.md                # Avaliação e métricas
│   └── 05-pitch.md                   # Roteiro do pitch
│
└── 📁 src/                           # Código da aplicação
    └── app.py                        # (exemplo de estrutura)

```

---

## Como executar

### 1. Instalar Ollama

```bash
# 1. Instalar Ollama (ollama.com)

# 2. Baixar um modelo leve
ollama pull gpt-oss

# 3. Testar se funciona
ollama run gpt-oss "Olá!"
```

### 2. Instalar dependências

```bash
pip install -r ./src/requirements.txt
```

---

### Rodar a Lia

```bash
streamlit run ./src/app.py
```

---

## Documentação completa

Toda a documentacao técnica, base de conhecimento, engenharia de prompts e métricas de avaliação estão na pasta [docs/](docs/).

---

## 👩‍💻 Autora

**Bianca Inazumi**

Projeto desenvolvido para o desafio da **DIO - Digital Innovation One**.
