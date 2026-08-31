# PROJETO FINAL — DS-PY-004 - AGO/SET 2026

### GRUPO
**Rafael Machado, Rafael Bechelli e Quiara Brito**

## 📌 Apresentação da Base de Dados e Perguntas Norteadoras

### Contexto e Fonte dos Dados
O presente estudo analisa as despesas e dinâmicas operacionais das viagens a serviço de servidores e colaboradores públicos federais no ano de **2026** (dados atualizados até 16/08/2026). Os microdados foram extraídos do [Portal da Transparência do Governo Federal](https://portaldatransparencia.gov.br/download-de-dados/viagens), cruzando a base de registros de afastamentos/viagens (`2026_Viagem.csv`) com a base de pagamentos (`2026_Pagamento.csv`) e a base de trechos (`2026_Trecho.csv`).

* **Volume de dados inicial:** 406.083 linhas e 22 colunas.
* **Volume após tratamento/limpeza:** 381.790 processos com efetiva movimentação financeira.
* **Unidade monetária:** Reais (BRL).

---
### Perguntas Norteadoras de Negócio
1. **Concentração por Órgão:** Quais órgãos públicos federais concentram mais recursos financeiros?
2. **Perfil de Despesas por Cargo:** Quais cargos públicos demandam maior volume de gastos, qual a despesa média por deslocamento, tempo médio de duração e destinos preferenciais?
3. **Impacto das Viagens Não Realizadas:** Qual é a proporção de viagens canceladas/não realizadas e qual o impacto financeiro (gasto comprometido vs. recuperado por devolução)?
4. **Composição dos Gastos:** Como se distribuem os desembolsos entre diárias, passagens aéreas/terrestres e outros gastos operacionais?
5. **Urgência e Custos:** Viagens sinalizadas em caráter de urgência apresentam prêmio de custo superior aos deslocamentos com planejamento ordinário?

---

### 📂 ESTRUTURA


```
seu-projeto/
├── README.md                     <- explica o projeto, a base e como reproduzir
├── notebooks/
│   ├── analise.ipynb             <- O notebook contendo a análise feita, sem outputs
│   ├── analise_outputs.ipynb     <- O notebook contendo a análise deita, com outputs
│   ├── 2026_Viagem.csv           <- Base principal (não consta no repo, inserir manualmente)
│   ├── 2026_Pagamento.csv        <- Base auxiliar (não consta no repo, inserir manualmente)
│   ├── 2026_Passagem.csv         <- Base auxiliar (não consta no repo, inserir manualmente)
│   └── 2026_Trecho.csv           <- Base auxiliar (não consta no repo, inserir manualmente)
└── .gitignore
```

---
## 📈 Principais Achados e Insights da Análise Exploratória

### Viagens Canceladas: Baixo Volume, Alto Custo Unitário e Baixa Recuperação
* **Proporção:** 98,72% dos afastamentos foram realizados com sucesso e apenas **1,28% (4.878 processos)** foram cancelados.
* **Assimetria de Gastos:** O cancelamento ocorre majoritariamente em viagens de maior complexidade. A mediana do custo em viagens não realizadas é de **R$ 3.391,74**, um valor **116% superior** à mediana das viagens realizadas (**R$ 1.566,92**).
* **Ineficiência na Devolução:** Apenas **13,68%** do valor comprometido em viagens canceladas foi devolvido aos cofres públicos. Cerca de 66,4% dos processos cancelados não registraram qualquer restituição de valores, resultando em um **custo líquido de R$ 18,81 milhões** em viagens não executadas.

### Despesas por Cargo e Sigilo Institucional
* **Cargos Ocultos e Sigilosos:** 
  * Viagens sem cargo preenchido somaram **R$ 483,81 milhões** em gastos totais (média de R$ 3.434,35 e destino preferencial Brasília/DF).
  * Viagens sob a categoria *"Informações Protegidas Por Sigilo"* concentraram **R$ 218,28 milhões** (62.627 viagens), apresentando duração média elevada de **7,5 dias**.
* **Concentração de Destino:** O principal polo atrator das viagens no serviço público federal é a capital federal (**Brasília/DF**).

---

## 🎯 Conclusões, Limitações e Próximos Passos

### Conclusões para Tomada de Decisão (Visão de Negócio)
1. **Mitigação de Cancelamentos Caros:** Urgência em revisar políticas de emissão antecipada de bilhetes e reservas para itinerários de alto custo, prevendo regras contratuais mais flexíveis de cancelamento com companhias aéreas e hotéis para conter perdas de até R$ 18,8 milhões.
2. **Qualificação Cadastral:** Alta taxa de registros com cargo não informado ou truncado aponta necessidade de travas no sistema de concessão de diárias e passagens (PCDP) para elevar a rastreabilidade dos recursos públicos.

### Limitações da Base
* Dados restritos ao período de **janeiro a meados de agosto de 2026** (ano incompleto).
* Informações sobre categorias sensíveis (segurança/sigilo) omitidas pelo Portal da Transparência por razões legais.
* Inviabilidade de atribuir causa unívoca às devoluções apenas pela tabela de viagens sem a justificativa administrativa individualizada.

### Próximos Passos
* Desenvolvimento de modelo preditivo para identificar risco de cancelamento de passagens.
* Análise de séries temporais de sazonalidade mensal dos gastos nos órgãos de maior orçamento.
* Cruzamento com indicadores de produtividade e cumprimento de metas dos órgãos demandantes.

---

## ⚙️ Como Reproduzir este Projeto

1. Clone o repositório:
   ```bash
   git clone https://github.com/seu-usuario/seu-repositorio.git
   cd seu-repositorio
   ```
2. Crie e ative um ambiente virtual (opcional, mas recomendado):
   ```bash
   python -m venv venv
   source venv/bin/activate  # Linux/Mac
   # ou venv\Scripts\activate no Windows
   ```
3. Instale os pacotes necessários:
   ```bash
   pip install pandas numpy matplotlib seaborn
   ```
4. Baixe as bases `2026_Viagem.csv` e `2026_Pagamento.csv` do [Portal da Transparência](https://portaldatransparencia.gov.br/download-de-dados/viagens) e insira na pasta raiz/dados.
5. Execute o Jupyter Notebook `notebooks/analise.ipynb`.