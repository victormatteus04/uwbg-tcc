# Previsão de Materiais 2D com Gap Ultra Largo via Machine Learning

Repositório do Trabalho de Conclusão de Curso (TCC) de Victor Matteus Silva Souza no Instituto de Física da UFG.

## 📘 Contexto

Este projeto busca reproduzir e estender a abordagem da dissertação de mestrado de Joseane Santos Almeida ([PDF disponível](docs/Joseane-Santos-Almeida.pdf)), que utilizou aprendizado de máquina para identificar semicondutores 2D de *gap* ultra largo (UWBG). Com base nesse referencial, desenvolvemos uma pipeline modular em Jupyter Notebooks para análise de dados, modelagem preditiva e triagem de novos materiais com potenciais aplicações em eletrônica de potência e optoeletrônica UV.

## 🎯 Objetivos

- Construir um pipeline de ML para classificação e regressão de *band gaps*.
- Avaliar materiais 2D do banco de dados C2DB.
- Reproduzir os principais resultados da tese de referência.
- Explorar novas predições para estruturas AB2 com descritores atômicos e estatísticos.

## 🗂️ Estrutura do Repositório

```
├── data/                   # Conjuntos de dados
│   ├── raw/               # Dados brutos (ex: C2DB)
│   └── processed/         # Dados tratados (não versionados)
├── docs/                  # Documentação do projeto
│   ├── Joseane-Santos-Almeida.pdf   # Tese de referência
│   └── datasets.ipynb     # Descrição dos dados utilizados
├── notebooks/             # Jupyter Notebooks por etapa
│   └── (em desenvolvimento)
├── scripts/               # Scripts utilitários e pré-processamento
├── models/                # Modelos treinados
├── README.md
└── .gitignore

```

> ⚠️ O arquivo `data/raw/c2db.db` **não é versionado** neste repositório por questões de tamanho e rastreabilidade. Os arquivos `.csv` em `data/processed/` **são versionados** e podem ser usados diretamente para reprodução dos resultados.

## 🧪 Progresso Atual

- [x] Features atômicas e estatísticas geradas
- [ ] Construção dos Datasets
- [ ] Implementação de modelos de classificação
- [ ] Implementação dos modelos de regressão
- [ ] Avaliação de regressão do *band gap*
- [ ] Comparação com resultados da tese
- [ ] Aplicação a novos materiais candidatos

## 📄 Referência Base

**Título:** Predizendo Semicondutores de Gap Ultra Largo com Machine Learning  
**Autora:** Joseane Santos Almeida – Universidade Federal Fluminense, 2021  
[📎 PDF](docs/Joseane-Santos-Almeida.pdf)

## 👤 Autor

Victor Matteus Silva Souza  
Instituto de Física – Universidade Federal de Goiás  
Mat.: 202105201  
Orientador: Prof. Dr. Renato Borges Pontes
```
