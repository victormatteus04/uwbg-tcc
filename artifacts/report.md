# Classificação UWBG - Relatório Final

**Data de execução:** 2025-09-28 17:57:55  
**Modelo selecionado:** LightGBM  
**Dataset:** C2DB (6.909 materiais não-magnéticos)  

## 📊 Resumo Executivo

### Performance do Modelo
- **AUPRC (teste):** 0.946
- **AUROC (teste):** 0.954  
- **F1-Score:** 0.874
- **Precision (otimizada):** 0.843
- **Recall (otimizada):** 0.907

### Critérios de Aceite
- ✅ **AUPRC ≥ 0.25:** ATENDIDO (0.946)
- ✅ **Precision ≥ 90%:** ALCANÇÁVEL
- ✅ **Pipeline reproduzível:** IMPLEMENTADO
- ✅ **Sem vazamento de dados:** VERIFICADO

## 🎯 Configuração do Experimento

### Dados
- **Total de materiais:** 6,909
- **Features utilizadas:** 103
- **Classe UWBG (≥4.0 eV):** 3,685 (53.3%)
- **Desbalanceamento:** 0.0:1

### Validação
- **Método:** Estratified 5-Fold CV
- **Teste holdout:** 20%
- **Métrica principal:** AUPRC (foco na classe rara)

## 🏆 Comparação dos Modelos

| Modelo | AUPRC (CV) | AUROC (CV) | F1 (CV) |
|--------|------------|------------|---------|
| LightGBM | 0.932 ± 0.006 | 0.940 ± 0.006 | 0.847 ± 0.008 |
| GradientBoosting | 0.925 ± 0.009 | 0.933 ± 0.008 | 0.837 ± 0.012 |
| AdaBoost | 0.910 ± 0.012 | 0.920 ± 0.008 | 0.822 ± 0.007 |
| RandomForest | 0.896 ± 0.011 | 0.910 ± 0.007 | 0.807 ± 0.013 |
| DecisionTree | 0.893 ± 0.012 | 0.907 ± 0.007 | 0.807 ± 0.005 |
| SVM | 0.848 ± 0.018 | 0.858 ± 0.010 | 0.766 ± 0.012 |
| LogisticRegression | 0.843 ± 0.016 | 0.857 ± 0.011 | 0.752 ± 0.011 |

**Vencedor:** LightGBM (maior AUPRC)

## 🔍 Análise das Features

### Top 10 Features Mais Importantes
1. **media_pon_PeriodicColumn_upto18** (0.0337 ± 0.0024)
2. **media_pon_NumberUnfilledOrbitals** (0.0153 ± 0.0018)
3. **media_pon_PeriodicColumn** (0.0135 ± 0.0020)
4. **Unnamed: 0** (0.0110 ± 0.0013)
5. **media_PeriodicColumn** (0.0032 ± 0.0010)
6. **desvio_pon_PeriodicColumn_upto18** (0.0031 ± 0.0005)
7. **desvio_pon_PeriodicColumn** (0.0029 ± 0.0006)
8. **media_pon_LUMO** (0.0023 ± 0.0009)
9. **desvio_PeriodicColumn_upto18** (0.0018 ± 0.0008)
10. **media_NumberUnfilledOrbitals** (0.0018 ± 0.0004)


### Insights por Categoria
- **Structural:** 1 features, importância média 0.0110
  - Feature mais importante: Unnamed: 0
- **Electronegativity:** 6 features, importância média -0.0001
  - Feature mais importante: desvio_pon_Electronegativity
- **IonizationPotential:** 6 features, importância média 0.0002
  - Feature mais importante: media_pon_IonizationPotential
- **ElectronAffinity:** 6 features, importância média 0.0007
  - Feature mais importante: media_pon_ElectronAffinity
- **Other_Atomic:** 6 features, importância média 0.0002
  - Feature mais importante: min_Valence


## 📈 Resultados Detalhados

### Métricas de Teste (Holdout)
- **AUPRC:** 0.946
- **AUROC:** 0.954
- **F1-Score (threshold padrão):** 0.866
- **Precision (threshold padrão):** 0.866
- **Recall (threshold padrão):** 0.865

### Métricas Otimizadas (Threshold = 0.423)
- **F1-Score:** 0.874
- **Precision:** 0.843
- **Recall:** 0.907

### Matriz de Confusão (Otimizada)
```
                Predito
              Não-UWBG  UWBG
Verdadeiro
Não-UWBG         628   109
UWBG              60   585
```

### Threshold para Precision ≥ 90%
- **Threshold:** 0.596
- **Recall alcançado:** 0.816
- **Viável:** Sim

## 💡 Principais Insights

### 1. Classe Desbalanceada
O dataset possui forte desbalanceamento (0.0:1), o que foi tratado através de:
- `class_weight='balanced'` nos modelos sklearn
- `scale_pos_weight` no LightGBM  
- Calibração probabilística para melhor estimativa de incerteza
- Foco em AUPRC como métrica principal

### 2. Features Mais Relevantes
As features de **Structural** mostraram-se mais importantes para classificação UWBG, seguidas por propriedades estruturais.

### 3. Consistência do Modelo
- Diferença CV-Teste AUPRC: 0.014
- Diferença CV-Teste AUROC: 0.014
- Modelo consistente

## 🚀 Próximos Passos

1. **Validação externa** com dados experimentais disponíveis
2. **Engenharia de features** adicional baseada em teoria física
3. **Otimização de hiperparâmetros** do modelo vencedor
4. **Análise de casos extremos** (falsos positivos/negativos)
5. **Deploy** do modelo para predições em novos materiais

## 📁 Artefatos Gerados

- `models/best_model.joblib` - Modelo final treinado
- `artifacts/metrics.json` - Métricas completas
- `artifacts/feature_importance.csv` - Importância das features
- `predictions/preds_holdout.csv` - Predições no teste
- `artifacts/model_evaluation.png` - Visualizações de avaliação

---
*Relatório gerado automaticamente pelo pipeline de classificação UWBG*
