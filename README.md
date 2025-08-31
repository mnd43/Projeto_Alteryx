# Projeto_Alteryx

## 📊 Projeto de Análise de Movimentações de Produtos com Alteryx

Este projeto foi desenvolvido com o objetivo de praticar habilidades em preparação, transformação e visualização de dados utilizando o Alteryx Designer. Para isso, foram criadas duas bases fictícias e um fluxo completo que simula o acompanhamento de movimentações de produtos em diferentes armazéns.

---

## 🗂️ Bases de Dados Utilizadas

### 1. Cadastro
Contém informações básicas sobre os produtos:
- SKU: Identificador único do produto  
- Nome do Produto  
- Categoria  
- Preço Unitário

### 2. Movimentações
Registra eventos de entrada e saída de produtos:
- SKU  
- Data  
- Quantidade  
- Movimentação: Entrada ou Saída  
- Armazém

---

## 🔧 Etapas do Fluxo no Alteryx

O fluxo foi construído em duas subdivisões a partir da entrada de dados:

- 📥 Input Data  
Importação das duas bases: cadastro de produtos e movimentações.

**PARTE 1:**  
A partir da base Movimentação:
- 🔃 Sort Tool  
Ordenação dos dados por SKU de maneira crescente.
  
- 🧮 Formula Tool  
Criação de coluna calculada "Mov_Ajustada" onde criei uma condição para retornar o valor positivo para entradas e negativo para saídas. 

- 🧮 Formula Tool  
Criação de coluna "Mov_Ajustada_Num", com a conversão dos valores da "Mov_ajustada" para números.

- 📊 Summarize Tool  
Agrupamento dos dados por produto somando o valor da "Mov_Ajustada_Num" para consolidar o saldo final de estoque.

**PARTE 2:**  
A partir da base Cadastro:

- 🔗 Join Tool  
Combinação dos dados de movimentações com os dados de cadastro via campo SKU.

- 🔃 Sort Tool  
Ordenação dos dados por SKU de maneira crescente.

- 🧹 Unique Tool  
Filtragem de registros duplicados para garantir integridade.

- 🔗 Join Tool  
Combinação dos dados de únicos do passo anterior, com as saídas do passo Summarize.
  
- 🧮 Formula Tool  
Criação da coluna "Valor_Estoque" a partir da multiplicação da quantidade em estoque e o preço unitário.

- 📤 Output Data  
Exportação dos resultados finais para um arquivo Excel.

Ainda, adicionei algumas visualizações apenas para analisar alguns dados:

- 📈 Charting Tool  
Visualização gráfica do valor do estoque por armazém;  
Visualização gráfica do valor do estoque por SKU.

---

## 🧠 Aprendizados

Uma vez que utilizei bases fictícias com o intuito de praticar meu conhecimento na ferramenta Alteryx, não foquei em insights sobre as bases em si, mas nas etapas que consegui concluir:
- Integração de múltiplas fontes de dados  
- Aplicação de lógica condicional e cálculos personalizados  
- Criação de gráficos simples dentro do Alteryx  
- Exportação de resultados para uso externo


