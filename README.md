# 🌍 SpaceRiskIA - Predição de Riscos Ambientais

## 📋 Descrição do Projeto

SpaceRiskIA é um projeto de Machine Learning desenvolvido para prever índices de risco ambiental e de incêndio para diferentes regiões utilizando modelos de regressão. O sistema analisa múltiplas variáveis ambientais e geográficas para calcular o índice de impacto e classificar áreas de alto risco.

## 👥 Equipe de Desenvolvimento

- **Arthur Bobadilla Franchi** - RM 555056
- **Luan Orlandelli Ramos** - RM 554747
- **Jorge Luiz** - RM 554418

## 🎯 Objetivo do Projeto

O SpaceRiskIA tem como objetivo principal fornecer uma ferramenta preditiva para:
- Identificar regiões com maior probabilidade de eventos ambientais adversos
- Auxiliar na tomada de decisões para alocação de recursos de prevenção
- Apoiar o planejamento urbano e ambiental
- Contribuir para a redução de danos causados por incêndios e outros eventos ambientais

## 🛠️ Tecnologias Utilizadas

- **Python** - Linguagem de programação principal
- **Google Colab** - Ambiente de desenvolvimento
- **Pandas** - Manipulação e análise de dados
- **NumPy** - Computação numérica
- **Matplotlib** - Visualização de dados
- **Scikit-learn** - Algoritmos de Machine Learning

## 📊 Descrição do Dataset

O dataset utilizado contém **320 amostras** com **14 colunas**, estruturadas da seguinte forma:

### Variáveis de Entrada (11 features):
| Feature | Descrição | Unidade |
|---------|-----------|---------|
| `temperatura_media_c` | Temperatura média da região | °C |
| `umidade_solo_pct` | Percentual de umidade do solo | % |
| `indice_vegetacao_ndvi` | Índice de vegetação NDVI | 0-1 |
| `chuva_prevista_mm` | Precipitação prevista | mm |
| `vento_kmh` | Velocidade do vento | km/h |
| `proximidade_area_urbana_km` | Distância até área urbana | km |
| `historico_eventos_5anos` | Número de eventos nos últimos 5 anos | contagem |
| `altitude_m` | Altitude da região | metros |
| `inclinacao_terreno_graus` | Inclinação do terreno | graus |
| `densidade_populacional_km2` | Densidade populacional | hab/km² |
| `cobertura_nuvens_pct` | Percentual de cobertura de nuvens | % |

### Variáveis Alvo (2 targets):
- **`indice_impacto`**: Índice contínuo de impacto ambiental (variável principal de predição)
- **`risco_alto`**: Classificação binária de risco (0 = baixo, 1 = alto)

### Identificador:
- **`regiao_id`**: Identificador único da região

## 🤖 Modelo de Machine Learning

### Algoritmo Utilizado
**Regressão Linear Múltipla** - Modelo supervisionado para predição do `indice_impacto`

### Configuração do Modelo
- **Divisão dos dados**: 80% treino / 20% teste
- **Variável alvo**: `indice_impacto`
- **Features utilizadas**: Todas as 11 variáveis de entrada

### 📈 Performance do Modelo

| Métrica | Valor | Interpretação |
|---------|-------|---------------|
| **R² Score** | 0.9744 | 97.44% de variância explicada |
| **MAE** | 3.23 | Erro médio absoluto |
| **RMSE** | 3.99 | Raiz do erro quadrático médio |

> ✅ **Excelente desempenho**: O modelo explica 97.44% da variabilidade dos dados, indicando alta precisão nas predições.

## 🔍 Principais Descobertas

### Fatores de Maior Impacto:

1. **📈 Histórico de Eventos** (+3.717)
   - Maior preditor positivo de risco
   - Regiões com histórico de eventos têm maior probabilidade de novos incidentes

2. **🌳 Índice de Vegetação NDVI** (-36.519)
   - Maior fator de proteção
   - Vegetação densa reduz significativamente o risco ambiental

3. **🌡️ Temperatura Média** (+1.234)
   - Temperaturas elevadas aumentam o risco

4. **💧 Umidade do Solo** (-0.892)
   - Solo úmido reduz o risco de incêndios

5. **🌧️ Chuva Prevista** (-0.567)
   - Precipitação atua como fator protetor

## 📁 Estrutura do Projeto

```
ia_ml_gs01/
│
├── README.md                         
├── SpaceRiskIA_Relatorio.pdf        
│
├── dataset/
│   └── dataset_space_risk_global_solution.csv  
│
└── ipynb/
    └── SpaceRiskAI.ipynb             
```

## 🚀 Como Utilizar

### Pré-requisitos
```bash
# Bibliotecas necessárias
pip install pandas numpy matplotlib scikit-learn
```

### Executando o Projeto

1. **Clone ou baixe o repositório**
   ```bash
   cd ia_ml_gs01
   ```

2. **Abra o notebook no Google Colab ou Jupyter**
   ```bash
   jupyter notebook ipynb/SpaceRiskAI.ipynb
   ```

3. **Execute as células sequencialmente**
   - Carregamento e exploração dos dados
   - Análise exploratória e visualizações
   - Treinamento do modelo
   - Avaliação de performance
   - Análise de coeficientes

### Exemplo de Uso do Modelo

```python
import pandas as pd
from sklearn.linear_model import LinearRegression

# Carregar dados
df = pd.read_csv('dataset/dataset_space_risk_global_solution.csv')

# Preparar features e target
X = df.drop(['regiao_id', 'indice_impacto', 'risco_alto'], axis=1)
y = df['indice_impacto']

# Treinar modelo
model = LinearRegression()
model.fit(X, y)

# Fazer predição
nova_regiao = [[25, 45, 0.6, 10, 15, 5, 2, 500, 10, 100, 30]]
risco_previsto = model.predict(nova_regiao)
print(f"Índice de Impacto Previsto: {risco_previsto[0]:.2f}")
```

## 💡 Resultados e Aplicações

### Aplicações Práticas:

1. **🔥 Prevenção de Incêndios**
   - Identificação de áreas críticas para monitoramento
   - Alocação estratégica de recursos de combate

2. **🏙️ Planejamento Urbano**
   - Orientação para expansão urbana segura
   - Definição de zonas de proteção ambiental

3. **📊 Gestão de Recursos**
   - Priorização de investimentos em prevenção
   - Otimização de equipes de resposta a emergências

4. **🌱 Conservação Ambiental**
   - Identificação de áreas que necessitam reflorestamento
   - Monitoramento de degradação ambiental

5. **⚠️ Sistemas de Alerta**
   - Desenvolvimento de alertas precoces
   - Notificações para populações em risco

### Insights Estratégicos:

- ✅ Regiões com vegetação densa (NDVI alto) apresentam proteção natural significativa
- ✅ Histórico de eventos é o melhor preditor de riscos futuros
- ✅ Combinação de temperatura alta + baixa umidade = risco crítico
- ✅ Monitoramento contínuo de regiões com histórico é essencial

## 📄 Documentação Adicional

Para informações detalhadas sobre a metodologia, análises estatísticas e visualizações, consulte o arquivo **SpaceRiskIA_Relatorio.pdf**.


---

<div align="center">

**SpaceRiskIA** - Prevenção através da Inteligência Artificial 🌍🤖

*Desenvolvido como parte do Global Solution - FIAP 2026*

</div>
