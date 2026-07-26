# Porsche Analytics Sales — Documentação do Dashboard Executivo

**Desenvolvido por:** André Reis
**Ferramentas:** Excel (planilha-fonte) + Claude (construção e evolução do dashboard)
**Formato de entrega:** arquivo único em HTML, sem dependências externas, pronto para abrir em qualquer navegador

---

## 1. Sobre este projeto

Este dashboard nasceu de uma planilha de vendas da Porsche (`Planilha_Porshe_Sanitizada.xlsx`) e foi construído de forma **iterativa e colaborativa**: a cada rodada, eu defini o que precisava mudar, melhorar ou corrigir através de prompts, e o Claude traduziu essas decisões em código (HTML, CSS e JavaScript), sempre alinhando o resultado comigo antes de seguir para a etapa seguinte. Ou seja: **as decisões de produto, negócio e prioridade foram minhas — o Claude foi o parceiro técnico de implementação.**

O resultado é uma peça só, sem servidor e sem banco de dados: um arquivo `.html` que já carrega os dados, os gráficos e toda a lógica de análise dentro dele.

---

## 2. Linha do tempo da evolução

### Versão 1 — Protótipo inicial
- Primeiro dashboard gerado a partir da planilha original (100 registros), com os 4 filtros pedidos (Modelo, Model Year, Cidade, Forma de Pagamento) e KPIs básicos para responder às primeiras perguntas de negócio: modelo mais vendido por cidade, ano-modelo com maior saída e um panorama geral de popularidade por praça.
- Paleta e identidade visual inspiradas no site oficial da Porsche Brasil.

### Versão 2 — Fusão de dois dashboards em um só
- Recebi dois arquivos HTML distintos (um mais executivo, outro mais simples) e pedi para uni-los em uma única peça, aproveitando o melhor dos dois.
- Corrigido um bug real encontrado por mim no print: cards de KPI duplicados com o mesmo ID, que travavam em zero.
- Base de dados trocada de valores fictícios para os **dados reais da planilha**.
- Ampliação forte do número de KPIs e gráficos (de poucos indicadores para uma cobertura completa: performance financeira, ranking de vendedores, modelos, cidades, ano-modelo, forma de pagamento e status de entrega).

### Versão 3 — Refinamento de UX e correções pontuais
- Título do dashboard padronizado em português e inglês.
- Ajuste de rótulos (ex: "Ano Modelo" em vez do termo em inglês).
- Padrão de cores dos gráficos revisado para evitar cortes de rótulo e remover linhas de grade.
- Substituição dos gráficos de rosca (que não funcionavam bem com muitas categorias) por gráficos de barra.
- Tabela de registros com busca e filtros por coluna, e ajuste de layout para não depender de rolagem lateral.
- Tema claro redesenhado (misto de branco, cinza e vermelho) e rodapé com a assinatura do projeto.
- Datas padronizadas no formato dd/mm/aaaa.

### Versão 4 — Ampliação da base de dados (100 → 200 vendas)
- Você enriqueceu a planilha original com **novos registros fictícios**, dobrando a base para 200 linhas de vendas.
- Foi utilizado um **script em Python (usando a biblioteca pandas)** para tratar essa nova planilha a cada atualização: leitura do arquivo Excel, validação de datas, padronização de nomes de vendedores, mapeamento de siglas de estado, conversão de status de entrega em grupos de negócio (Concluída / Em Andamento / Cancelada) e exportação para o formato de dados que o dashboard consome. Esse processo de tratamento é o que garante que qualquer nova versão da planilha entre no dashboard sem quebrar nenhum cálculo.
- Reformulação do bloco de **Performance Financeira**, com cards mais precisos: total de vendas registradas (todas, independente do status), valor total registrado, total de vendas concluídas, faturamento (somando só as concluídas), vendas e valor em andamento, vendas e valor cancelados.
- Prévia genérica de veículo (adicionada e depois removida a seu pedido, por não ter agregado valor visual ao painel).

### Versão 5 — Versão atual: inteligência, exportação e edição
- **Seção "Destaques" recalculada para não considerar vendas canceladas** — o vendedor, o carro e o estado campeões agora refletem apenas negócios concluídos ou em andamento, evitando distorção por cancelamentos.
- **Lupa + exportação em todos os cards e gráficos**: cada um dos 29 elementos visuais do dashboard (KPIs e gráficos) ganhou três ícones de ação:
  - 🔍 **Ver dados** — abre uma janela com a tabela detalhada por trás daquele número ou gráfico específico;
  - 📄 **Exportar em PDF** — gera um PDF já formatado daquele recorte de dados;
  - 📊 **Exportar em Excel** — gera um `.xlsx` com os mesmos dados, pronto para reaproveitar em outra análise.
- **Padronização dos filtros**: todos os campos de filtro (Modelo, Ano Modelo, Cidade, Estado, Pagamento, Status) agora seguem o mesmo padrão visual da tabela — mostram "Todos" com uma seta indicando lista suspensa e, ao clicar, é possível digitar para pesquisar dentro da própria lista.
- **Edição de status da venda dentro da plataforma**: na tabela de registros, o status de cada venda virou um campo editável. É possível reclassificar uma venda (por exemplo, de "Pending" para "Delivered") diretamente no dashboard, e todos os KPIs, gráficos e destaques recalculam automaticamente. Essa alteração vive apenas na sessão aberta no navegador — para torná-la permanente, o caminho é exportar o Excel atualizado pelo próprio botão de exportação.

---

## 3. Funcionalidades de visualização e impressão dos dados

Um dos pontos altos desta versão é a possibilidade de **explorar e extrair qualquer informação do dashboard**, não só olhar para ela:

| Ação | O que faz |
|---|---|
| 🔍 Lupa | Mostra, em uma janela, exatamente quais linhas de venda compõem aquele card ou gráfico |
| 📄 PDF | Gera um documento PDF formatado (com cabeçalho, título e tabela) daquele recorte específico |
| 📊 Excel | Gera uma planilha `.xlsx` com os mesmos dados, pronta para reaproveitar em outra análise |

Isso transforma o dashboard em uma ferramenta de trabalho, e não apenas em uma visualização estática — qualquer usuário pode "furar" um número e entender de onde ele vem, ou levar aquele recorte para uma reunião impresso ou em planilha.

---

## 4. Seleção de idioma e de tema

- **PT/EN**: um botão no cabeçalho alterna todo o dashboard entre português e inglês — títulos, filtros, KPIs, textos de insight e tabela — sem precisar de duas versões separadas do arquivo.
- **Tema claro/escuro**: outro botão alterna a identidade visual entre um tema escuro (preto/vermelho, inspirado na Porsche) e um tema claro (branco e cinza com acentos vermelhos), mantendo a leitura confortável em diferentes ambientes de apresentação.

---

## 5. Ficha técnica

- Um único arquivo `.html`, sem necessidade de internet ou instalação para funcionar.
- Bibliotecas utilizadas (todas embutidas no arquivo, para funcionar offline): Tailwind CSS, Chart.js + plugin de rótulos de dados, jsPDF + AutoTable (exportação em PDF) e SheetJS (exportação em Excel).
- Base de dados: 200 vendas, com modelo, ano, preço, quilometragem, forma de pagamento, cidade, estado, vendedor e status de entrega.
- Tratamento de dados: script em Python (pandas) para leitura, limpeza e conversão da planilha original para o formato consumido pelo dashboard.

---

## 6. Créditos

Dashboard idealizado, priorizado e validado por **André Reis**, com o Claude atuando como parceiro de implementação técnica ao longo de várias rodadas de refinamento por prompt.

*Porsche Analytics Sales • Desenvolvido por André Reis Tech • 2026*
