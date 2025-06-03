# 📊 Dados Comerciais (Vendas, Estoque e Fornecedores)

Repositório com datasets de gestão comercial, incluindo vendas, entradas de estoque, cadastro de produtos e fornecedores. Ideal para análises de inventory turnover, previsão de demanda e gestão de supply chain.

## 📂 Estrutura dos Arquivos

| Arquivo                           | Descrição                                                                 |
|-----------------------------------|---------------------------------------------------------------------------|
| `catalogo_produtos.csv`           | Catálogo com preços, custos, unidade de medida e estoque mínimo.         |
| `vendas_produtos_2022.csv`        | Registro diário de vendas (produto, quantidade, data).                   |
| `compras_estoque_2022.csv`        | Entradas de estoque por fornecedor (data, produto, quantidade, custo).   |
| `cadastro_fornecedores.csv`       | Informações de contato dos fornecedores (empresa, e-mail, responsável).  |

## 💡 Casos de Uso

1. **Análise de Vendas**:  
   - Identificar produtos mais vendidos (use `vendas_produtos_2022.csv`).  
   - Calcular sazonalidade (agrupe por mês/trimestre).  

2. **Gestão de Estoque**:  
   - Cruzar `compras_estoque_2022.csv` e `vendas_produtos_2022.csv` para calcular giro de estoque.  
   - Alertas quando estoque atual < `estoque_mínimo` (em `catalogo_produtos.csv`).  

3. **Relatórios Financeiros**:  
   - Margem de lucro por produto (`preço_unitário - custo_unitário`).  

## ⚙️ Como Usar

### Python (Exemplo com Pandas)
```python
import pandas as pd

# Carregar dados de vendas
vendas = pd.read_csv("vendas_produtos_2022.csv", sep=";")
print(vendas.groupby("Produto")["Quantidade Vendida"].sum().sort_values(ascending=False))
