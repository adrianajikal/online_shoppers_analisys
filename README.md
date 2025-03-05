# 🛍️ Projeto: Clusterização Hierárquica - Comportamento de Navegação em E-commerce

## 📋 Descrição do Projeto

Este projeto faz parte do curso da EBAC e tem como objetivo aplicar **técnicas de agrupamento hierárquico** para segmentar usuários de um e-commerce, utilizando a base de dados **Online Shoppers Purchasing Intention**.  
A ideia é entender se diferentes perfis de navegação resultam em diferentes propensões de compra, ajudando a empresa a personalizar suas estratégias de marketing.

---

## 📊 Base de Dados

- Fonte: [Online Shoppers Intention Dataset - UCI](https://archive.ics.uci.edu/ml/datasets/Online+Shoppers+Purchasing+Intention+Dataset)
- Tamanho: 12.330 sessões de usuários em um período de 12 meses.
- Cada linha representa uma sessão única, com dados sobre comportamento de navegação, características da data e informações técnicas da sessão.

---

## 🎯 Objetivo

> Agrupar sessões de acesso ao e-commerce com base no comportamento de navegação e em características da data, para identificar perfis distintos de usuários e suas diferentes propensões de compra.

---

## ⚙️ Metodologia

1. **Seleção de variáveis**:  
   Variáveis relacionadas à navegação e contexto temporal foram escolhidas para o agrupamento, excluindo variáveis técnicas (sistema, browser, região) e a variável alvo (`Revenue`).

2. **Pré-processamento**:
    - Tratamento de variáveis qualitativas (`Month` e `Weekend`).
    - Normalização das variáveis quantitativas com `StandardScaler`.
    - Exclusão da variável `Revenue` (evitar vazamento de dados).

3. **Clusterização Hierárquica**:
    - Algoritmo: `AgglomerativeClustering` do scikit-learn.
    - Distância: Ward (minimiza variância interna).
    - Avaliamos 2 soluções: com 3 e 4 clusters.

4. **Avaliação dos Grupos**:
    - Análise descritiva de cada cluster.
    - Cruzamento dos clusters com a variável `Revenue` para entender propensão à compra.
    - Análise de qualidade de navegação via `BounceRates`.

5. **Decisão Final**:
    - Optamos por usar a solução com 4 clusters, por sua melhor capacidade de separar grupos estratégicos.

---

## 📊 Variáveis Utilizadas no Agrupamento

| Variável | Descrição |
|---|---|
| Administrative | Número de acessos a páginas administrativas |
| Administrative_Duration | Tempo em páginas administrativas |
| Informational | Número de acessos a páginas informativas |
| Informational_Duration | Tempo em páginas informativas |
| ProductRelated | Número de acessos a páginas de produtos |
| ProductRelated_Duration | Tempo em páginas de produtos |
| BounceRates | Taxa de rejeição |
| ExitRates | Taxa de saída |
| PageValues | Valor médio das páginas visitadas antes da compra |
| SpecialDay | Proximidade com datas especiais |
| Month | Mês da sessão (convertido para número) |
| Weekend | Se foi final de semana (0 ou 1) |

---

## 📈 Resultados

| Cluster | Nome | Perfil | Propensão à compra (Revenue) | Bounce Rate |
|---|---|---|---|---|
| 0 | Visitantes Normais | Navegação equilibrada, foco em produtos | 15,74% | 1,08% |
| 1 | Visitantes Rápidos | Sessões curtas, altas taxas de saída e rejeição | 0,39% | 19,23% |
| 2 | Visitantes Engajados | Sessões longas e completas, foco em produtos e informações | **25,98%** (melhor grupo) | **0,68%** |
| 3 | Visitantes Sazonais | Sessões próximas de datas especiais, comportamento misto | 7,77% | 1,69% |

---

## 🚀 Conclusões

- **O Cluster 2 (Visitantes Engajados)** é o grupo mais valioso para a empresa, combinando a maior propensão de compra com a navegação de maior qualidade.
- **O Cluster 1 (Visitantes Rápidos)** representa sessões problemáticas, com baixa qualidade e praticamente nenhuma conversão.
- **O Cluster 3 (Visitantes Sazonais)** oferece uma grande oportunidade para campanhas promocionais em datas especiais.
- Essa segmentação fornece insights estratégicos para otimizar campanhas, melhorar a experiência de navegação e ajustar estratégias de retenção.

---

## 📂 Arquivo do Projeto

| Arquivo | Descrição |
|---|---|
| online_shoppers_revenue.ipynb | Notebook completo com todo o fluxo de análise e clusterização |

---

## 💻 Como executar

1. Clone este repositório:
    ```bash
    git clone https://github.com/seu-usuario/seu-repositorio.git
    ```
2. Instale as bibliotecas necessárias:
    ```bash
    pip install -r requirements.txt
    ```
3. Execute o notebook:
    ```bash
    jupyter notebook online_shoppers_revenue.ipynb
    ```
---

## 🛠️ Tecnologias utilizadas

- Python 3.11
- Pandas
- Scikit-learn
- Matplotlib
- Seaborn
- Scipy

---

## ✨ Autor
Adriana Jikal
Aluno(a) do curso de Ciência de Dados da EBAC

