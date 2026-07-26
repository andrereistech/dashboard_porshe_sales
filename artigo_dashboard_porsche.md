# 🏎️ De uma planilha de vendas a um dashboard executivo completo: minha jornada com Excel + IA

Nos últimos dias, encarei um desafio dentro da minha trilha na **Aceleração: AI Reports com Excel, GPT Agents e Claude Code** 🚀: peguei uma planilha de vendas comum com linhas, colunas, números 📊 e transformei em uma ferramenta de verdade. Não um gráfico solto no Excel, mas um **dashboard executivo completo**, dos que eu vejo em empresa de tecnologia de verdade: filtros dinâmicos, KPIs, exportação de dados, edição em tempo real. ⚡

O resultado foi o **Dashboard de Análise Executiva de Vendas - PORSHE**, um dashboard construído inteiramente em HTML, sem servidor, sem banco de dados, rodando 100% no navegador 🌐, em parceria com o **Claude AI, da Anthropic** 🤖.

---

## 💭 Por que eu escrevo isso?

Não foi só "pedir para uma IA fazer um dashboard". Foi um processo de várias rodadas de conversa para tomar a melhor decisão de negócio, pensando no cenário real de uma empresa. Enquanto analisava nossa base de dados, fui definindo quais perguntas o dashboard precisava responder, quais KPIs faziam sentido para um gestor comercial, o que eu via de errado em cada versão e o que eu queria melhorar ✋. O Claude foi meu parceiro técnico. Foi ele quem traduziu cada uma das minhas decisões em código, testou, corrigiu e sugeriu quando fazia sentido, ou não.

Para mim, foi um exercício prático de **prompt engineering aplicado a um problema real de negócio** 🎯, e achei interessante compartilhar aqui.

---

## 🛤️ A evolução do projeto

O dashboard passou por cinco grandes rodadas comigo no comando de cada decisão:

1️⃣ **Protótipo inicial**: definimos os filtros básicos (Modelo, Ano, Cidade, Forma de Pagamento) e os KPIs para responder perguntas simples de negócio, com identidade visual inspirada na Porsche Brasil. 🎨

2️⃣ **Fusão e correção**: unifiquei duas versões de dashboard em uma só (pois havia criado uma versão com Ranking e Destaques), aumentei a quantidade de dados fictícios da planilha, e corrigimos um bug real encontrado 🐛 (cards duplicados travados em zero).

3️⃣ **Refinamento de UX**: à medida que o dashboard melhorava, eu pensava em novas coisas e pedi ajustes finos de idioma, cores de gráfico, filtros com busca 🔍, tabela sem necessidade de rolagem lateral, tema claro e escuro 🌗 e opção de troca de idioma 🌎.

4️⃣ **Expansão da base**: com Python (pandas) 🐍 fizemos um script próprio para tratar inconsistências da planilha (datas inválidas, nomes) e expandir minha base de 100 para **200 registros de vendas**, preservando os vendedores reais e respeitando o ano de cada veículo e os demais dados constantes na planilha original.

5️⃣ **Inteligência e produtividade**: para a versão atual e final, pedi lupa 🔍, exportação em PDF 📄 e Excel 📊 em **todos os 29 cards e gráficos**, edição de status de venda ✏️ diretamente na plataforma, e uma seção de "Destaques" 🏆 que exclui vendas canceladas para não distorcer os campeões de vendas.

Todo esse histórico, incluindo o código do meu script Python, está documentado no próprio repositório. 📚

---

## ✨ O que o dashboard entrega hoje?

- 📈 **19 KPIs** organizados em Performance Financeira, Destaques e Indicadores de Portfólio
- 📊 **10 gráficos interativos** (vendas por estado, por vendedor, por modelo, por cidade, por ano-modelo, mix de pagamento, status de entrega, faixas de quilometragem)
- 🔎 **Filtros pesquisáveis** por Modelo, Ano Modelo, Cidade, Estado, Pagamento e Status
- 📄📊 **Exportação individual** de qualquer card ou gráfico em PDF ou Excel
- ✏️ **Edição de status de venda** ao vivo, com recálculo automático de todo o painel
- 🌎🌗 **Troca de idioma** de todo o dashboard para PT/BR ou EN e **opções de tema claro/escuro**, tudo no mesmo arquivo

---

## 🧰 Tecnologias utilizadas

- 🧱 **HTML5 + Tailwind CSS** para a interface
- 📊 **Chart.js + chartjs-plugin-datalabels** para os 10 gráficos interativos
- 📄 **jsPDF + jsPDF-AutoTable** para a exportação de qualquer card/gráfico em PDF
- 📗 **SheetJS (xlsx)** para a exportação de qualquer card/gráfico em Excel
- ⚙️ **JavaScript puro (vanilla JS)** para toda a lógica de filtros, cálculos de KPI e interatividade
- 🐍 **Python + Pandas** para tratar e expandir minha base de dados de 100 para 200 registros
- 📑 **Excel** como fonte original dos dados de vendas
- 🤖 **Claude (Anthropic)** como parceiro de implementação ao longo de todo o processo
- 🐙 **GitHub + GitHub Pages** para versionar o projeto e publicá-lo com um link ao vivo

---

## 🙏 Agradecimentos

Esse projeto nasceu dentro da minha trilha na **Aceleração: AI Reports com Excel, GPT Agents e Claude Code**, da **DIO (Digital Innovation One)** 🎓, e não teria saído do papel sem o que aprendi por lá. Um agradecimento especial ao **Felipe Aguiar — o Felipão da DIO**, pelas aulas magníficas, que me deram a base e, principalmente, a confiança para sair do "gráfico de pizza no Excel" e ir atrás de construir algo no nível de um produto real. Obrigado, DIO. Obrigado, Felipão. 🙏

---

## 🔗 Confira o projeto

- 🔗 **Dashboard ao vivo (GitHub Pages)**: https://andrereistech.github.io/dashboard_porshe_sales/
- 💻 **Repositório completo**: https://github.com/andrereistech/dashboard_porshe_sales
- 👤 **Meu GitHub**: https://github.com/andrereistech
- 💼 **Meu LinkedIn**: https://www.linkedin.com/in/andre-reis-tech/

Se você também está estudando Excel, dados ou IA aplicada, fica o convite: entra no repositório, explora o código, testa os filtros, exporta um PDF. 🚀 E se tiver feedback, comentário ou sugestão, será muito bem-vindo! 💬

---
