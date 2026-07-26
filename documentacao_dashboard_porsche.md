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
- Você enriqueceu a planilha original com **novos registros fictícios**, dobrando a base para 200 linhas de vendas, usando um **script em Python (pandas) desenvolvido por você** especificamente para isso — detalhado na seção 5.
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

## 5. Script Python de tratamento e expansão da base de dados

Para levar a base de 100 para 200 vendas, foi criado um script em Python (usando `pandas`) com as seguintes responsabilidades:

- **Correção de datas inválidas**: quando a data de venda vinha como `INVALID` ou fora de um intervalo aceitável, o script gera uma data plausível, respeitando o ano do modelo do veículo (nunca gera uma venda antes do carro existir).
- **Padronização de nomes de clientes** já existentes (capitalização correta).
- **Expansão para 200 linhas**: reamostra vendas existentes (`sample` com reposição) para criar os registros fictícios que faltam até atingir o total desejado.
- **Novos clientes fictícios**: para cada venda nova, gera um nome de cliente aleatório em inglês (lista de primeiro e último nome).
- **Vendedores reais preservados**: as novas vendas fictícias recebem um vendedor sorteado dentre os vendedores que **já existiam de verdade** na planilha original — ou seja, não foram inventados vendedores novos, apenas mais vendas para o time já existente.
- **Reconstrução do ID de venda**: gera um `sale_id` único e sequencial (`SALE-001`, `SALE-002`, ...) para as 200 linhas finais, evitando duplicidade.
- **Reorganização de colunas**: posiciona a nova coluna de data corrigida (`CorrectData`) logo ao lado do ID da venda, facilitando a leitura da planilha final.

```python
import os
import random
from datetime import datetime, timedelta
import pandas as pd

# 1. Configurações de Caminho
PASTA = r"D:\DIO\Claude"
ARQUIVO_ENTRADA = os.path.join(PASTA, "Planilha Porshe Sanitizada_v2.xlsx")
NOME_ABA = "Sanitized"
ARQUIVO_SAIDA = os.path.join(
    PASTA, "Planilha_Porsche_Sanitizada_200_linhas.xlsx"
)


def gerar_data_valida(ano_veiculo, data_limite_str="2026-07-26"):
  """Gera uma data no formato YYYY-MM-DD respeitando o ano do veículo."""
  data_limite = datetime.strptime(data_limite_str, "%Y-%m-%d")
  try:
    ano = int(str(ano_veiculo).strip())
  except (ValueError, TypeError):
    ano = 2023

  data_inicio = datetime(ano, 1, 1)
  if data_inicio > data_limite:
    data_inicio = datetime(2023, 1, 1)

  dias_diferenca = (data_limite - data_inicio).days
  dias_aleatorios = random.randint(0, max(0, dias_diferenca))
  return (data_inicio + timedelta(days=dias_aleatorios)).strftime("%Y-%m-%d")


def gerar_nome_ingles():
  """Gera nomes de clientes em inglês no padrão Aaaaa Aaaaa."""
  first_names = [
      "James", "John", "Robert", "Michael", "William", "David", "Richard",
      "Joseph", "Thomas", "Charles", "Christopher", "Daniel", "Matthew",
      "Anthony", "Mark", "Donald", "Steven", "Paul", "Andrew", "Joshua",
      "Mary", "Patricia", "Jennifer", "Linda", "Elizabeth", "Barbara",
      "Susan", "Jessica", "Sarah", "Karen", "Lisa", "Nancy", "Betty",
      "Sandra", "Margaret", "Ashley", "Kimberly", "Emily", "Donna", "Michelle",
  ]
  last_names = [
      "Smith", "Johnson", "Williams", "Brown", "Jones", "Garcia", "Miller",
      "Davis", "Rodriguez", "Martinez", "Hernandez", "Lopez", "Gonzalez",
      "Wilson", "Anderson", "Thomas", "Taylor", "Moore", "Jackson", "Martin",
      "Lee", "Perez", "Thompson", "White", "Harris", "Sanchez", "Clark",
      "Ramirez", "Lewis", "Robinson",
  ]
  return f"{random.choice(first_names).capitalize()} {random.choice(last_names).capitalize()}"


def processar_e_expandir_vendas(df_original, total_alvo=200):
  DATA_HOJE = datetime.strptime("2026-07-26", "%Y-%m-%d")
  df = df_original.copy()

  # Identifica colunas chaves
  col_sale_id = [
      c for c in df.columns if "sale_id" in str(c).lower() or "id" in str(c).lower()
  ]
  col_sale_id = col_sale_id[0] if col_sale_id else df.columns[0]

  col_vendedor = [
      c
      for c in df.columns
      if "salesperson" in str(c).lower() or "vendedor" in str(c).lower()
  ]
  col_vendedor = col_vendedor[0] if col_vendedor else None

  col_cliente = [
      c
      for c in df.columns
      if "customer" in str(c).lower() or "client" in str(c).lower()
  ]
  col_cliente = col_cliente[0] if col_cliente else df.columns[2]

  col_ano = [
      c
      for c in df.columns
      if "year" in str(c).lower() or "model_year" in str(c).lower()
  ]
  col_ano = col_ano[0] if col_ano else df.columns[3]

  # Captura a lista dos seus vendedores reais (removendo vazios/inválidos)
  vendedores_reais = []
  if col_vendedor and col_vendedor in df.columns:
    vendedores_reais = (
        df[col_vendedor]
        .dropna()
        .astype(str)
        .str.strip()
        .unique()
        .tolist()
    )
    vendedores_reais = [v for v in vendedores_reais if v.upper() != "INVALID" and v != ""]

  if not vendedores_reais:
    vendedores_reais = [
        "Michael Scott", "Dwight Schrute", "Jim Halpert", "Pam Beesly", "Ryan Howard",
    ]

  # 1. Trata/calcula as datas sem sobreescrever a coluna salesperson
  datas_corrigidas = []
  col_busca_data = (
      "SaleDateSanitized"
      if "SaleDateSanitized" in df.columns
      else df.columns[1]
  )

  for idx, row in df.iterrows():
    val_data = str(row[col_busca_data]).strip()
    ano_modelo = row[col_ano]

    if val_data.upper() == "INVALID" or pd.isna(val_data) or val_data == "":
      datas_corrigidas.append(gerar_data_valida(ano_modelo))
    else:
      try:
        dt_obj = datetime.strptime(str(val_data)[:10], "%Y-%m-%d")
        if dt_obj > DATA_HOJE:
          datas_corrigidas.append(gerar_data_valida(ano_modelo))
        else:
          datas_corrigidas.append(dt_obj.strftime("%Y-%m-%d"))
      except ValueError:
        datas_corrigidas.append(gerar_data_valida(ano_modelo))

  # Adiciona/Atualiza a nova coluna CorrectData
  df["CorrectData"] = datas_corrigidas

  # Formata nomes de clientes originais
  for idx, row in df.iterrows():
    val_cli = str(row[col_cliente]).strip()
    if pd.notna(val_cli) and val_cli.upper() != "INVALID":
      df.at[idx, col_cliente] = " ".join([p.capitalize() for p in val_cli.split()])

  # 2. Reamostragem para criar novas vendas
  linhas_atuais = len(df)
  qtd_novas = max(0, total_alvo - linhas_atuais)

  amostras = df.sample(n=qtd_novas, replace=True).reset_index(drop=True)
  novas_linhas = []

  for idx, row in amostras.iterrows():
    nova_linha = row.to_dict()

    # Atualiza dados aleatórios para as novas vendas
    nova_linha[col_cliente] = gerar_nome_ingles()
    nova_linha["CorrectData"] = gerar_data_valida(nova_linha[col_ano])

    # Sorteia um vendedor da sua equipe real
    if col_vendedor:
      nova_linha[col_vendedor] = random.choice(vendedores_reais)

    novas_linhas.append(nova_linha)

  df_final = pd.concat([df, pd.DataFrame(novas_linhas)], ignore_index=True)

  # 3. Re-geração estrita de sale_id único para TODAS as 200 linhas
  df_final[col_sale_id] = [f"SALE-{i+1:03d}" for i in range(len(df_final))]

  # 4. Reordenação de colunas: CorrectData logo ao lado de sale_id
  colunas_finais = list(df_final.columns)
  if "CorrectData" in colunas_finais:
    colunas_finais.remove("CorrectData")

  pos_id = colunas_finais.index(col_sale_id)
  colunas_finais.insert(pos_id + 1, "CorrectData")

  return df_final[colunas_finais]


def main():
  print("--- INICIANDO PROCESSAMENTO E AJUSTE DE COLUNAS ---")
  print(f"Lendo aba '{NOME_ABA}' do arquivo: {ARQUIVO_ENTRADA}")

  if not os.path.exists(ARQUIVO_ENTRADA):
    print("ERRO: Arquivo nao encontrado.")
    return

  try:
    df = pd.read_excel(ARQUIVO_ENTRADA, sheet_name=NOME_ABA)
    print(f"Linhas originais carregadas: {len(df)}")
  except Exception as e:
    print(f"Erro ao ler a aba '{NOME_ABA}': {e}")
    return

  df_resultado = processar_e_expandir_vendas(df, total_alvo=200)
  print(f"Total final de registros gerados: {len(df_resultado)}")

  df_resultado.to_excel(ARQUIVO_SAIDA, index=False)
  print(f"Sucesso! Base ajustada salva em: {ARQUIVO_SAIDA}")


if __name__ == "__main__":
  main()
```

---

## 6. Ficha técnica

- Um único arquivo `.html`, sem necessidade de internet ou instalação para funcionar.
- Bibliotecas utilizadas (todas embutidas no arquivo, para funcionar offline): Tailwind CSS, Chart.js + plugin de rótulos de dados, jsPDF + AutoTable (exportação em PDF) e SheetJS (exportação em Excel).
- Base de dados: 200 vendas, com modelo, ano, preço, quilometragem, forma de pagamento, cidade, estado, vendedor e status de entrega.
- Tratamento e expansão de dados: script em Python (pandas) descrito na seção 5, responsável por corrigir datas, gerar clientes fictícios e ampliar a base para 200 registros mantendo os vendedores reais.

---

## 7. Créditos

Dashboard idealizado, priorizado e validado por **André Reis**, com o Claude atuando como parceiro de implementação técnica ao longo de várias rodadas de refinamento por prompt.

*Porsche Analytics Sales • Desenvolvido por André Reis Tech • 2026*
