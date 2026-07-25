# Base de Conhecimento

## Dados Utilizados

| Arquivo | Formato | Para que serve na Lia? |
|---------|---------|---------------------|
| `historico_atendimento.csv` | CSV | Contextualizar interações anteriores, ou seja, dar continuidade ao atendimento de forma mais eficiente |
| `perfil_investidor.json` | JSON | Personalizar as explicações sobre as dúvidas e necessidades de aconselhamento ao cliente |
| `produtos_financeiros.json` | JSON | Conhecer os produtos disponíveis para que possam ser explicados ao usuário |
| `transacoes.csv` | CSV | Analisar padrão de gastos do cliente e usar essas informações de forma didática |

---

## Adaptações nos Dados

O produto Fundo Imobiliário (FII) substituiu o Fundo Multimercado, pois pessoalmente me sinto mais confiante em usar apenas produtos financeiros que eu conheço. Assim, poderei validar as respostas da Lia de forma mais assertiva.

---

## Estratégia de Integração

### Como os dados são carregados?

Existem duas possibilidades:
- injetar os dados diretamente no prompt (Ctrl + C, Ctrl + V);
- carregar os arquivos via código, como no exemplo abaixo:

```python
import pandas as pd
import json

perfil = json.load(open('./data/perfil_investidor.json'))
transacoes = pd.read_csv('./data/transacoes.csv')
historico = pd.read_csv('./data/historico_atendimento.csv')
produtos = json.load(open('./data/produtos_financeiros.json'))
```

### Como os dados são usados no prompt?

Para simplificar, podemos simplesmente "injetar" os dados em nosso prompt, garantindo que o Agente tenha o melhor contexto possível. Lembrando que, em soluções mais robustas, o ideal é que essas informações sejam carregadas dinamicamente para que possamos ganhar flexibilidade.

```text
DADOS DO USUARIO E PERFIL (data/perfil_investidor.json):
{
  "nome": "Mia Sousa",
  "idade": 21,
  "profissao": "Analista de Sistemas",
  "renda_mensal": 4500.00,
  "perfil_investidor": "moderado",
  "objetivo_principal": "Construir reserva de emergência",
  "patrimonio_total": 13000.00,
  "reserva_emergencia_atual": 8600.00,
  "aceita_risco": false,
  "metas": [
    {
      "meta": "Completar reserva de emergência",
      "valor_necessario": 15000.00,
      "prazo": "2026-12"
    },
    {
      "meta": "Entrada do apartamento",
      "valor_necessario": 50000.00,
      "prazo": "2028-03"
    }
  ]
}

TRANSACOES DO USUARIO (data/transacoes.csv):
data,descricao,categoria,valor,tipo
2025-10-01,Salário,receita,5000.00,entrada
2025-10-02,Aluguel,moradia,1200.00,saida
2025-10-03,Supermercado,alimentacao,450.00,saida
2025-10-05,Netflix,lazer,55.90,saida
2025-10-07,Farmácia,saude,89.00,saida
2025-10-10,Restaurante,alimentacao,120.00,saida
2025-10-12,Uber,transporte,45.00,saida
2025-10-15,Conta de Luz,moradia,180.00,saida
2025-10-20,Academia,saude,99.00,saida
2025-10-25,Combustível,transporte,250.00,saida

HISTORICO DE ATENDIMENTO DO USUARIO (data/historico_atendimento.csv):
data,canal,tema,resumo,resolvido
2025-09-15,chat,CDB,Cliente perguntou sobre rentabilidade e prazos,sim
2025-09-22,telefone,Problema no app,Erro ao visualizar extrato foi corrigido,sim
2025-10-01,chat,Tesouro Selic,Cliente pediu explicação sobre o funcionamento do Tesouro Direto,sim
2025-10-12,chat,Metas financeiras,Cliente acompanhou o progresso da reserva de emergência,sim
2025-10-25,email,Atualização cadastral,Cliente atualizou e-mail e telefone,sim

PRODUTOS DISPONIVEIS PARA ENSINO (data/produtos_financeiros.json):
[
  {
    "nome": "Tesouro Selic",
    "categoria": "renda_fixa",
    "risco": "baixo",
    "rentabilidade": "Selic + 0,097% a.a. (taxa indicativa de compra)",
    "taxa_base_referencia": "Selic meta em 15,00% a.a. (18/03/2026)",
    "aporte_minimo": 185.33,
    "indicado_para": "Reserva de emergência e iniciantes",
    "referencia_data": "2026-03-18",
    "fonte": "Tesouro Direto e Banco Central do Brasil"
  },
  {
    "nome": "CDB Liquidez Diária",
    "categoria": "renda_fixa",
    "risco": "baixo",
    "rentabilidade": "Faixa de 100% a 110% do CDI (varia por banco e prazo)",
    "taxa_base_referencia": "CDI em linha com a Selic, referencia diaria do BCB",
    "aporte_minimo": 100.00,
    "indicado_para": "Quem busca segurança com rendimento diário",
    "referencia_data": "2026-03-18",
    "fonte": "Banco Central do Brasil e praticas de mercado"
  },
  {
    "nome": "LCI/LCA",
    "categoria": "renda_fixa",
    "risco": "baixo",
    "rentabilidade": "Faixa de 88% a 97% do CDI (isento de IR para pessoa fisica)",
    "taxa_base_referencia": "CDI em linha com a Selic, referencia diaria do BCB",
    "aporte_minimo": 1000.00,
    "indicado_para": "Quem pode esperar prazo de carencia e busca eficiencia tributaria",
    "referencia_data": "2026-03-18",
    "fonte": "Banco Central do Brasil e praticas de mercado"
  },
  {
    "nome": "Fundo Imobiliário (FII)",
    "categoria": "fundo",
    "risco": "medio",
    "rentabilidade": "Dividend Yield (DY) observado em muitos fundos entre 9% e 13% a.a., com variacao de cota",
    "aporte_minimo": 100.00,
    "indicado_para": "Perfil moderado que busca diversificacao e renda mensal, aceitando oscilacao",
    "referencia_data": "2026-03-18",
    "fonte": "Mercado secundario de FIIs na B3"
  },
  {
    "nome": "Fundo de Ações",
    "categoria": "fundo",
    "risco": "alto",
    "rentabilidade": "Variavel; pode superar ou ficar abaixo do CDI conforme ciclo e estrategia",
    "aporte_minimo": 100.00,
    "indicado_para": "Perfil arrojado com foco no longo prazo",
    "referencia_data": "2026-03-18",
    "fonte": "Mercado de capitais brasileiro"
  }
]
```

---

## Exemplo de Contexto Montado

O exemplo de contexto montado abaixo, se baiseia nos dados originais da base de conhecimento, mas os sintetiza deixando apenas as informações mais relevantes, otimizando assim o consumo de tokens. Entretanto, vale lembrar que mais importante do que economizar tokens, é ter todas as informações relevantes disponíveis em seu contexto.

```
Dados do Cliente:
- Nome: Mia Sousa
- Perfil: Moderado
- Objetivo: Construir reserva de emergência
- Reserva atual: R$ 10.000 (meta: R$ 15.000)

RESUMO DE GASTOS:
- Moradia: R$ 1.380
- Alimentação: R$ 570
- Transporte: R$ 295
- Saúde: R$ 188
- Lazer: R$ 55,90
- Total de saídas: R$ 2.488,90

PRODUTOS DISPONÍVEIS PARA EXPLICAR:
- Tesouro Selic (risco baixo)
- CDB Liquidez Diária (risco baixo)
- LCI/LCA (risco baixo)
- Fundo Imobiliário - FII (risco médio)
- Fundo de Ações (risco alto)
...
```
