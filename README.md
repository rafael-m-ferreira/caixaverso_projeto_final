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
4. **Proporção de Viagens:**  Viagens nacionais vs. Viagens Internacionais

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

### Concentração por Órgão
* **Maiores Gastadores do Orçamento** : Verificou-se que o Ministério da Justiça é o grande gastador do orçamento federal com relação às viagens, concentrando sozinho 291 milhões de reais gastos em 2026 até agosto. Os ministérios da educação e defesa, seguem em segundo e terceiro lugares respectivamente.

* **Top 10% Que Mais Gastam** : os top 10% gastadores, ie, Ministério da Justiça e Segurança Públicaa, Ministério da Educação e Ministério da Defesa consomem juntos praticamente o mesmo orçamento que os outros 32 órgãos da base. Consumindo aproximadamente 590 milhões de reais só neste ano de 2026 até o  mês de agosto!

* **Gastos com Passagem vs Diárias por Categoria** :  órgãos que gastam muito do orçamento tendem a ter um gasto desproporcional com diárias de hotel. 

### Despesas por Cargo e Sigilo Institucional
* **Cargos Ocultos e Sigilosos:** 
  * Viagens sem cargo preenchido somaram **R$ 483,81 milhões** em gastos totais (média de R$ 3.434,35 e destino preferencial Brasília/DF).
  * Viagens sob a categoria *"Informações Protegidas Por Sigilo"* concentraram **R$ 218,28 milhões** (62.627 viagens), apresentando duração média elevada de **7,5 dias**.
* **Concentração de Destino:** O principal polo atrator das viagens no serviço público federal é a capital federal (**Brasília/DF**).

### Viagens Canceladas: Baixo Volume, Alto Custo Unitário e Baixa Recuperação
* **Proporção:** 98,76% dos afastamentos foram realizados com sucesso e apenas **1,24% (4.731 processos)** foram cancelados.
* **Assimetria de Gastos:** O cancelamento ocorre majoritariamente em viagens de maior complexidade. A mediana do custo em viagens não realizadas é de **R$ 3.437,23**, um valor **119% superior** à mediana das viagens realizadas (**R$ 1.566,92**).
* **Ineficiência na Devolução:** Apenas **13,93%** do valor comprometido em viagens canceladas foi devolvido aos cofres públicos. Cerca de 65,38% dos processos cancelados não registraram qualquer restituição de valores, resultando em um **custo líquido de R$ 18,42 milhões** em viagens não executadas.

### Proporção de Viagens
* **Proporção por âmbito (nacional vs internacional)** : As viagens internacionais são 2,56% dos processos, mas 15,08% do gasto, participação financeira quase seis vezes superior à numérica. São 8.272 viagens que consumiram R$ 146,57 milhões.A viagem internacional mediana custou R$ 13.425,20 contra R$ 1.571,60 da nacional: **8,54 vezes mais**. A distância se mantém no P95 (R$ 45.726,60 contra R$ 7.869,26), indicando patamar de custo distinto ao longo de toda a distribuição, e não efeito de casos extremos.

---

## 🎯 Limitações

### Limitações da Base
* Dados restritos ao período de **janeiro a meados de agosto de 2026** (ano incompleto).
* Informações sobre categorias sensíveis (segurança/sigilo) omitidas pelo Portal da Transparência por razões legais.
* Inviabilidade de atribuir causa unívoca às devoluções apenas pela tabela de viagens sem a justificativa administrativa individualizada.

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