# 🌍 Impacto das Emissões de Gases Poluentes na Saúde Respiratória — Baixada Santista

Análise exploratória e preditiva investigando a relação entre a emissão de gases poluentes e as internações hospitalares por doenças respiratórias nos 9 municípios da Baixada Santista (SP), no período de 2007 a 2024.

![Python](https://img.shields.io/badge/Python-3.13-blue?logo=python&logoColor=white)
![Pandas](https://img.shields.io/badge/Pandas-Data%20Wrangling-150458?logo=pandas&logoColor=white)
![Scikit--learn](https://img.shields.io/badge/scikit--learn-Machine%20Learning-F7931E?logo=scikitlearn&logoColor=white)
![SHAP](https://img.shields.io/badge/SHAP-Interpretability-8A2BE2)
![Status](https://img.shields.io/badge/Status-Concluído-success)

## 📌 Objetivo

Investigar se existe correlação estatística entre o volume de emissão de gases (dados do SEEG) e o índice de internações por doenças respiratórias (dados do DATASUS) nos municípios da Baixada Santista, e treinar um modelo de classificação capaz de identificar cenários de alta ou baixa internação a partir dos indicadores ambientais.

## 🗂️ Fontes de dados

| Fonte | Descrição |
|---|---|
| **SEEG** (Sistema de Estimativas de Emissões e Remoções de GEE) | Emissões de gases de efeito estufa por setor, categoria e município (1970–2024) |
| **DATASUS/SIH** | Internações hospitalares por doenças respiratórias (CID-10, Capítulo X) por município |

> Ambos os datasets são públicos, oficiais e anonimizados — sem dados pessoais sensíveis, em conformidade com a LGPD (Lei nº 13.709/2018).

## 🔬 Metodologia

1. **Limpeza e transformação** — conversão dos datasets de formato largo para longo (`melt`), padronização de nomes de municípios via regex, tratamento de valores ausentes e remoção de outliers extremos de digitação.
2. **Integração** — agregação das emissões por cidade/ano e cruzamento (`merge`) com os dados de internação.
3. **Análise exploratória** — estatística descritiva, boxplots, histogramas e séries temporais.
4. **Teste de correlação de Pearson** — validação estatística da associação entre as variáveis.
5. **Machine Learning** — Árvore de Decisão para classificar cenários de alta/baixa internação a partir dos dados de emissão, com avaliação por acurácia, F1-score e matriz de confusão.
6. **Interpretabilidade (SHAP)** — identificação de quais variáveis mais influenciam as previsões do modelo.

## 📊 Principais resultados

- Correlação de Pearson **global** entre emissões e internações: **r = 0,65** (p = 0,0036) — associação moderada a forte, estatisticamente significativa (p < 0,05).
- No recorte por município, **São Vicente** (r = +0,65, p = 0,003) apresentou correlação positiva significativa; **Peruíbe** apresentou correlação negativa significativa, mas esse resultado é afetado por lacunas nos dados originais daquela cidade (2015–2019 e 2023).
- **Santos** se destaca como outlier estrutural, concentrando o maior volume de internações da região — coerente com seu papel de polo hospitalar da Baixada Santista.
- A correlação identificada é exploratória: não implica causalidade, já que fatores como clima, perfil etário e capacidade de atendimento também influenciam as internações.

## 🛠️ Tecnologias utilizadas

- **Python** (Pandas, NumPy)
- **Matplotlib / Seaborn** — visualização de dados
- **SciPy** — testes estatísticos (correlação de Pearson)
- **Scikit-learn** — Árvore de Decisão (classificação)
- **SHAP** — interpretabilidade de modelo

## 📁 Estrutura do repositório

```
├── environmental_health_analysis.ipynb   # Notebook com toda a análise
├── Projeto_PCG.pdf                       # Relatório completo do projeto
└── README.md
```

## 🚀 Como executar

1. Clone este repositório.
2. Instale as dependências:
   ```bash
   pip install pandas numpy matplotlib seaborn scipy scikit-learn shap openpyxl
   ```
3. Abra o notebook `environmental_health_analysis.ipynb` no Jupyter, Google Colab ou VS Code.
4. Ajuste os caminhos dos arquivos de dados (`DATASET_EMISSAO.xlsx` e `INTERNACAO.xlsx`) conforme sua estrutura local.

## 👥 Autores

Projeto desenvolvido para o componente de Pesquisa Curricularizada de Graduação — Universidade Católica de Santos (2026).

- Henrique Lício Nievas Barbosa
- Levi Freihat
- Rhuan Miguel Lima dos Santos
- Yasmin Vitória Ferreira da Cruz Santos

## 📄 Fontes

- SEEG — Sistema de Estimativas de Emissões e Remoções de GEE ([seeg.eco.br](https://seeg.eco.br/))
- DATASUS — Departamento de Informática do SUS ([datasus.saude.gov.br](https://datasus.saude.gov.br/))
