import pandas as pd
import plotly.express as px
import streamlit as st

# Configuração da página
st.set_page_config(
    page_title="Dashboard Omnichannel", page_icon="🛍️", layout="wide"
)

st.title("🛍️ Dashboard de E-commerce & Vendas Omnichannel")
st.markdown(
    "Análise integrada de desempenho de vendas entre diferentes canais."
)

# Simulando dados
data = {
    "Canal": [
        "E-commerce",
        "Loja Física",
        "Marketplace",
        "E-commerce",
        "Loja Física",
        "Marketplace",
    ],
    "Categoria": [
        "Eletrônicos",
        "Vestuário",
        "Eletrônicos",
        "Casa",
        "Casa",
        "Vestuário",
    ],
    "Vendas": [15000, 12000, 18000, 8000, 9500, 11000],
    "Data": [
        "2026-01-01",
        "2026-01-01",
        "2026-01-02",
        "2026-01-02",
        "2026-01-03",
        "2026-01-03",
    ],
}
df = pd.DataFrame(data)

# Barra lateral para filtros
st.sidebar.header("Filtros")
canal_selecionado = st.sidebar.multiselect(
    "Selecione o Canal",
    options=df["Canal"].unique(),
    default=df["Canal"].unique(),
)

# Filtrar dados
df_filtrado = df[df["Canal"].isin(canal_selecionado)]

# Exibir métricas principais
total_vendas = df_filtrado["Vendas"].sum()
total_pedidos = len(df_filtrado)

col1, col2 = st.columns(2)
col1.metric("Faturamento Total", f"R$ {total_vendas:,.2f}")
col2.metric("Total de Transações", total_pedidos)

st.markdown("---")

# Gráfico de Vendas por Canal
fig_canal = px.bar(
    df_filtrado,
    x="Canal",
    y="Vendas",
    color="Categoria",
    title="Vendas por Canal e Categoria",
    barmode="group",
)
st.plotly_chart(fig_canal, use_container_width=True)
