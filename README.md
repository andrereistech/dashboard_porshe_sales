<div align="center">

# 🏁 Porsche Analytics Sales
### Dashboard Executivo de Inteligência Comercial

*Filtros dinâmicos • KPIs em tempo real • Exportação para PDF/Excel • Edição de dados ao vivo • PT/EN*

[![HTML5](https://img.shields.io/badge/HTML5-E34F26?style=flat-square&logo=html5&logoColor=white)](#)
[![JavaScript](https://img.shields.io/badge/JavaScript-F7DF1E?style=flat-square&logo=javascript&logoColor=black)](#)
[![Tailwind CSS](https://img.shields.io/badge/Tailwind_CSS-38B2AC?style=flat-square&logo=tailwind-css&logoColor=white)](#)
[![Chart.js](https://img.shields.io/badge/Chart.js-FF6384?style=flat-square&logo=chart.js&logoColor=white)](#)
[![Python](https://img.shields.io/badge/Python-3776AB?style=flat-square&logo=python&logoColor=white)](#)
[![Pandas](https://img.shields.io/badge/Pandas-150458?style=flat-square&logo=pandas&logoColor=white)](#)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg?style=flat-square)](#)
[![LinkedIn](https://img.shields.io/badge/LinkedIn-Andr%C3%A9_Reis-0A66C2?style=flat-square&logo=linkedin&logoColor=white)](https://www.linkedin.com/in/andre-reis-tech/)

**[🔗 Ver dashboard ao vivo](https://andrereistech.github.io/dashboard_porshe_sales/)** · **[📄 Documentação completa](./documentacao_dashboard_porsche.md)**

</div>

---

## 📌 Sobre o projeto

Dashboard executivo de vendas construído a partir de uma base de **200 transações** da Porsche (dados sanitizados + registros fictícios gerados via script próprio em Python), pensado para responder, em segundos, as perguntas que qualquer gestor comercial faria: *quem são meus vendedores campeões? qual modelo mais vende? em qual praça? qual o faturamento real x cancelado x em andamento?*

Todo o projeto roda **em um único arquivo HTML**, sem servidor, sem banco de dados e sem necessidade de internet — basta abrir no navegador.

> 💡 Este projeto foi construído em parceria com o **Claude (Anthropic)**, em um processo 100% orientado por mim: cada decisão de negócio, prioridade e critério de análise foi definida através de prompts, com o Claude atuando como parceiro técnico de implementação. O processo completo de evolução está documentado em [`documentacao_dashboard_porsche.md`](./documentacao_dashboard_porsche.md).

---

## ✨ Principais funcionalidades

**Análise**
- 19 KPIs organizados em 3 blocos: Performance Financeira, Destaques e Indicadores de Portfólio
- 10 gráficos interativos (vendas por estado, por vendedor, por modelo, por cidade, por ano-modelo, mix de pagamento, status de entrega, faixas de quilometragem)
- Filtros dinâmicos e pesquisáveis: Modelo, Ano Modelo, Cidade, Estado, Forma de Pagamento e Status de Entrega

**Produtividade**
- 🔍 **Lupa** em todos os cards e gráficos — visualize a tabela de dados por trás de qualquer número
- 📄 **Exportação em PDF** de qualquer card ou gráfico, individualmente
- 📊 **Exportação em Excel (.xlsx)** de qualquer card ou gráfico, individualmente
- ✏️ **Edição de status de venda diretamente na plataforma**, com recálculo automático de todos os indicadores

**Experiência**
- 🌗 Alternância entre tema escuro e tema claro
- 🌎 Alternância completa entre português e inglês
- 📱 Layout responsivo

---

## 🛠️ Stack técnica

| Camada | Tecnologia |
|---|---|
| Interface | HTML5 + Tailwind CSS |
| Gráficos | Chart.js + chartjs-plugin-datalabels |
| Exportação PDF | jsPDF + jsPDF-AutoTable |
| Exportação Excel | SheetJS (xlsx) |
| Tratamento e expansão da base de dados | Python + Pandas |
| Fonte de dados original | Planilha Excel sanitizada (100 → 200 registros) |

---

## 🚀 Como usar

**Opção 1 — Direto no navegador (recomendado)**
Acesse: **[andrereistech.github.io/dashboard_porshe_sales](https://andrereistech.github.io/dashboard_porshe_sales/)**

**Opção 2 — Localmente**
```bash
git clone https://github.com/andrereistech/dashboard_porshe_sales.git
cd dashboard_porshe_sales
```
Depois é só abrir o `index.html` em qualquer navegador (duplo clique).

---

## 📂 Estrutura do repositório

```
dashboard_porshe_sales/
├── index.html                          # Dashboard completo (HTML + CSS + JS, tudo embutido)
├── documentacao_dashboard_porsche.md    # Documentação da evolução do projeto e do script de dados
└── README.md                            # Este arquivo
```

---

## 📈 Evolução do projeto

O dashboard passou por 5 rodadas de evolução — do protótipo inicial com filtros básicos até a versão atual, com exportação de dados e edição em tempo real. O histórico completo, incluindo o script Python usado para tratar e expandir a base de dados para 200 registros, está documentado em:

👉 **[documentacao_dashboard_porsche.md](./documentacao_dashboard_porsche.md)**

---

## 👤 Autor

**André Reis**
Projeto desenvolvido como parte de um estudo sobre **Excel + IA aplicada (Claude)** para automação de dashboards executivos.

[![LinkedIn](https://img.shields.io/badge/LinkedIn-0A66C2?style=flat-square&logo=linkedin&logoColor=white)](https://www.linkedin.com/in/andre-reis-tech/)
[![GitHub](https://img.shields.io/badge/GitHub-181717?style=flat-square&logo=github&logoColor=white)](https://github.com/andrereistech)

---

<div align="center">

*Porsche Analytics Sales • Desenvolvido por André Reis Tech • 2026*

</div>
