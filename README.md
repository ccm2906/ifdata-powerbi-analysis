# IFData BCB: análise do Sistema Financeiro Nacional em Power BI

**Projeto 2 de 3** do meu portfólio de análise de dados. Os três projetos usam os mesmos dados públicos do IFData (Banco Central do Brasil), em ferramentas diferentes e com senioridade analítica crescente: **Excel → Power BI → Python**.

<!-- PREENCHER: substituir pelo print da página 1 do relatório -->
![Visão geral do relatório](docs/img/p1_visao_geral.png)

> **Data-base mais recente:** 06/2026 · **Série:** 6 datas-base consecutivas (03/2025 a 06/2026) · **Escopo:** conglomerados financeiros e instituições independentes (1.406 em 06/2026)

**Autor:** [PREENCHER: nome] · [PREENCHER: LinkedIn] · [PREENCHER: e-mail]
**Projeto anterior (Excel):** [PREENCHER: link do repositório em Excel]

---

## Sumário

1. [Resumo executivo](#1-resumo-executivo)
2. [Contexto e objetivo](#2-contexto-e-objetivo)
3. [Perguntas de negócio](#3-perguntas-de-negócio)
4. [O relatório](#4-o-relatório)
5. [Principais resultados](#5-principais-resultados)
6. [Dados](#6-dados)
7. [Metodologia](#7-metodologia)
8. [Validações](#8-validações)
9. [Limitações](#9-limitações)
10. [Próximos passos](#10-próximos-passos-projeto-3-em-python)
11. [Comparativo com a versão em Excel](#11-comparativo-com-a-versão-em-excel)
12. [Estrutura do repositório](#12-estrutura-do-repositório)
13. [Como reproduzir](#13-como-reproduzir)
14. [Competências demonstradas](#14-competências-demonstradas)
15. [English summary](#15-english-summary)
16. [Fonte, licença e contato](#16-fonte-licença-e-contato)

---

## 1. Resumo executivo

O relatório analisa a estrutura, a concentração, o crescimento, a rentabilidade e a rede física do sistema financeiro brasileiro ao longo de seis datas-base. Principais conclusões (06/2026 contra 06/2025, salvo indicação):

1. **Crescimento sem lucro.** Ativo +12,6% e PL +8,3%, mas lucro do trimestre estável (R$ 65,2 bi, +0,6%). O ROE anualizado do trimestre cai de 16,3% para 15,1%, e o ROE dos últimos 12 meses (LTM) de 16,2% (12/2025) para 14,9%.
2. **Mais ativo do que crédito e capital.** Ativo +12,6% e captações +13,1%, contra carteira +8,9%. A alavancagem sobe de 10,7x para 11,2x, e a carteira cai de 43% para 41% do ativo (03/2025 a 06/2026).
3. **Concentração alta no topo, em leve queda.** CR5 de 59,0% (03/2025) para 57,4%; HHI de 791 para 764. Os cinco maiores respondem por 46,4% do crescimento do ativo, contra 57,4% do estoque.
4. **Tamanho não garante rentabilidade.** Entre os cinco maiores, o ROE LTM vai de 8% (BB) a 22% (Itaú). O segmento S2 (ROE 19%) supera o S1 (15%).
5. **Controle de capital importa.** ROE LTM de 11,02% nos públicos, 16,15% nos privados nacionais e 17,95% nos estrangeiros, diferença que vem do ROA e não da alavancagem.
6. **A rede física encolhe.** Agências −13,3% (17.075 para 14.796) e postos +6,2%. Itaú, Bradesco e Santander respondem por 86% da queda líquida de agências do último trimestre.
7. **Geografia é geografia da sede.** SP, DF e RJ concentram 88,9% do ativo. O DF reúne 47,4% das agências porque BB e Caixa têm sede em Brasília.

---

## 2. Contexto e objetivo

Este repositório faz parte de um portfólio com três projetos sobre os mesmos dados, para mostrar evolução técnica e analítica:

| Projeto | Ferramenta | Escopo | Foco |
|---|---|---|---|
| 1 | Excel | Uma data-base (06/2026) | Análise descritiva e visualização |
| **2 (este)** | **Power BI** | **Seis datas-base, modelo dimensional** | **Série temporal, DAX, validação, storytelling** |
| 3 | Python | Seis datas-base | Estatística, segmentação e previsão (planejado) |

**Objetivo:** responder, com rigor metodológico e comparabilidade entre períodos, como o sistema financeiro se estrutura, quem o concentra, como cresce, quão rentável é e como sua rede física está distribuída.

**Público:** recrutadores e gestores de análise de dados. O relatório e este documento mostram o raciocínio, não só o resultado.

---

## 3. Perguntas de negócio

| Bloco | Perguntas |
|---|---|
| A. Estrutura e concentração | Quem são os maiores players e quanto concentram? O sistema ficou mais ou menos concentrado? Como o mercado se divide por controle e segmento? |
| B. Crescimento | Quais instituições e segmentos mais crescem? O crescimento vem de poucos grandes ou é disseminado? |
| C. Intermediação e funding | Quanto do ativo está em crédito e em títulos? Quanto do crédito é financiado por captações? |
| D. Solidez e alavancagem | Quem opera mais alavancado? O capital acompanhou o crescimento do ativo? |
| E. Rentabilidade e eficiência | Quem tem melhor ROA e ROE, de forma comparável entre períodos? O tamanho garante rentabilidade? Quanto cada agência sustenta? Quem opera com pouca ou nenhuma agência? |
| F. Geografia | Onde estão as sedes? Como crédito e rede se distribuem por UF e região? Há UFs com muita rede e pouco crédito, ou o inverso? |

---

## 4. O relatório

O arquivo `powerbi/ifdata_powerbi.pbix` tem quatro páginas de análise, com filtros sincronizados (Data em seleção única, Tipo de Controle e Segmento) e a unidade indicada em cada visual.

| Página | Foco | Principais visuais |
|---|---|---|
| 1. Visão geral | Escala, crescimento e perfil de alocação | Seis cartões, evolução em seis datas, perfil de alocação, Top 5 por ativo, ativo por controle e por segmento |
| 2. Concentração e competição | CR1, CR5, HHI, contribuição ao crescimento | Cartões de concentração, séries de CR5 e HHI, curva Top N, matriz de shares, maiores contribuições |
| 3. Rentabilidade e eficiência | ROE, ROA, alavancagem, lucro trimestral, rede | Séries run-rate e LTM, lucro trimestral, dispersão tamanho × ROE, matriz por controle, eficiência por agência |
| 4. Rede e geografia | Sede por UF e região, agências e postos | Participações por região, Top 5 UFs, rede por controle, rede física dos cinco maiores |

<!-- PREENCHER: prints das páginas -->
| Página 1 | Página 2 |
|---|---|
| ![p1](docs/img/p1_visao_geral.png) | ![p2](docs/img/p2_concentracao.png) |

| Página 3 | Página 4 |
|---|---|
| ![p3](docs/img/p3_rentabilidade.png) | ![p4](docs/img/p4_rede_geografia.png) |

Versão estática do relatório: [`docs/relatorio_ifdata.pdf`](docs/relatorio_ifdata.pdf).

---

## 5. Principais resultados

Cada página termina com um insight no formato **achado → evidência → e daí?**.

### 5.1 Evolução do sistema (valores arredondados)

| Data-base | Instituições | Ativo (R$ tri) | Carteira (R$ tri) | Captações (R$ tri) | PL (R$ tri) | Lucro do trimestre (R$ bi) |
|---|---|---|---|---|---|---|
| 03/2025 | 1.416 | 16,94 | 7,28 | 12,39 | 1,58 | 65,4 |
| 06/2025 | 1.418 | 17,28 | 7,32 | 12,62 | 1,61 | 64,8 |
| 09/2025 | 1.424 | 17,92 | 7,48 | 13,14 | 1,65 | 60,7 |
| 12/2025 | 1.430 | 18,33 | 7,76 | 13,47 | 1,65 | 76,6 |
| 03/2026 | 1.422 | 19,03 | 7,83 | 13,96 | 1,72 | 56,2 |
| 06/2026 | 1.406 | 19,46 | 7,97 | 14,27 | 1,74 | 65,2 |

### 5.2 Visão geral

- **Achado:** o ativo cresce mais do que o crédito e o capital, e o sistema fica mais alavancado.
- **Evidência:** ativo +12,6% e captações +13,1%, contra carteira +8,9% e PL +8,3%. A carteira passa de 43% para 41% do ativo, a alavancagem de 10,7x para 11,2x e o PL/ativo de 9,3% para 9,0%.
- **E daí?** A captação adicional vai mais para títulos (TVM/ativo de 21% para 24%) do que para crédito, e o capital por real de ativo diminui. A base não traz indicadores prudenciais, que complementariam a leitura.
- **Estrutura:** o Itaú tem 14,6% do ativo e os dez maiores, 72,0%. Por controle, 49,9% do ativo está em privados nacionais, 33,4% em públicos e 16,7% em estrangeiros. O segmento S1 concentra 63,2% do ativo.

### 5.3 Concentração e competição

- **Achado:** a leve desconcentração vem dos cinco maiores cedendo espaço às posições 6 a 10. A cauda manteve o peso.
- **Evidência:** Top 5 de 58,7% para 57,4% do ativo (−1,4 p.p.); posições 6 a 10 de 13,1% para 14,7% (+1,5 p.p.); demais instituições de 28,1% para 28,0%. HHI de 786 para 764 e número efetivo de instituições de 12,7 para 13,1. Os cinco maiores explicam 46,4% do crescimento anual do ativo e as posições 6 a 10, 26,7%. As participações por faixa mantêm fixas as dez maiores de 06/2026.
- **E daí?** O ganho de espaço está no segundo escalão (BTG +39%, BNDES +21%), e não em entrantes pequenos. BB e Santander cresceram cerca de 6%, metade do sistema.
- **Outros pontos:** a concentração do crédito é maior que a do ativo (CR5 de 64,6% contra 57,4%). Vinte instituições detêm 81% do ativo. A tendência não é linear: em 03/2026 o HHI sobe antes de cair.

### 5.4 Rentabilidade e eficiência

- **Achado:** a rentabilidade recuou: o lucro ficou estável enquanto o balanço cresceu, e a maior alavancagem só amorteceu a queda do ROE.
- **Evidência:** lucro do 2T26 de R$ 65,2 bi (+0,6% sobre o 2T25), com ativo +12,6% e PL +8,3%. O ROE anualizado do trimestre cai de 16,3% para 15,1% (−1,2 p.p.): −1,7 p.p. por menor ROA (1,52% para 1,36%) e +0,5 p.p. por maior alavancagem. ROE LTM: 16,2% (12/2025), 15,0% (03/2026) e 14,9% (06/2026).
- **E daí?** Crescer o ativo não gerou lucro, e o ROE só se sustenta com mais alavancagem. Os públicos têm ROE de 11% (nacionais 16%, estrangeiros 18%). Os cinco maiores têm 57% do ativo, mas 45% do lucro do trimestre.
- **Por controle:** a diferença de ROE entre estrangeiros e públicos (6,9 p.p.) vem do ROA (+9,6 p.p. a favor dos estrangeiros), parcialmente compensada pela maior alavancagem dos públicos (−2,7 p.p.).
- **Tamanho:** o S2 tem ROE de 19% (alavancagem de 9,9x), acima do S1, com 15% (13,2x). Entre os maiores, o ROE LTM varia de 8% (BB) a 22% (Itaú).
- **Rede:** os cinco maiores têm 78% das agências, 57% do ativo e 45% do lucro. 739 instituições (53% da base) não têm agência e detêm 6,4% do ativo.

### 5.5 Rede e geografia

- **Achado:** o sistema é concentrado nas sedes, mas a rede física segue outra geografia e está encolhendo.
- **Evidência:** SP (50,0%), DF (26,7%) e RJ (12,2%) concentram 88,9% do ativo. O DF tem 47,4% das agências (sede de BB e Caixa). O Sul tem 26% das instituições, 6,3% do ativo e 30% dos postos (cooperativas). Agências: −13,3% em 12 meses (17.075 para 14.796) e postos +6,2%. No 2T26, Itaú, Bradesco e Santander respondem por 86% da queda líquida de agências (−314 de −363).
- **E daí?** A rede física se reduz e parte da perda pode ser migração para postos ou reclassificação (hipótese a confirmar). UF é sede, não cobertura: medir acesso bancário exige dados por município.

---

## 6. Dados

### 6.1 Fonte e escopo

- **Fonte:** [IFData](https://www3.bcb.gov.br/ifdata/), Banco Central do Brasil. Relatório **Resumo**, arquivos **CSV** (que trazem a coluna `Código`).
- **Tipo de instituição:** Conglomerados Financeiros e Instituições Independentes. Os dois grupos não se sobrepõem (`TD` = C ou I), o que evita dupla contagem.
- **Datas-base:** 03/2025, 06/2025, 09/2025, 12/2025, 03/2026 e 06/2026.
- **Unidade:** valores monetários originais em **R$ mil**.

### 6.2 Arquivos e rastreabilidade

Os dados do BC podem ser reapresentados. Por isso cada arquivo registra a data de "documentos entregues até" e a data do download.

| Arquivo | Data-base | Documentos entregues até | Baixado em |
|---|---|---|---|
| `IFData_202503.csv` | 03/2025 | [PREENCHER] | [PREENCHER] |
| `IFData_202506.csv` | 06/2025 | [PREENCHER] | [PREENCHER] |
| `IFData_202509.csv` | 09/2025 | [PREENCHER] | [PREENCHER] |
| `IFData_202512.csv` | 12/2025 | [PREENCHER] | [PREENCHER] |
| `IFData_202603.csv` | 03/2026 | 19/05/2026 | [PREENCHER] |
| `IFData_202606.csv` | 06/2026 | 16/08/2026 | [PREENCHER] |

<!-- PREENCHER: ajustar os nomes dos arquivos aos reais -->

### 6.3 Dicionário de dados

<details>
<summary>Colunas do IFData (Resumo) e composição</summary>

| Coluna | Descrição |
|---|---|
| Instituição Financeira | Nome da instituição ou conglomerado no cadastro do BC |
| Código | Código da instituição ou conglomerado (somente no CSV) |
| TCB | Tipo de Consolidado Bancário: B1, B2, B3S, B3C, B4, N1, N2, N4 |
| SR | Segmento (Resolução nº 4.553/2017): S1 a S5, por porte e atividade internacional |
| TD | Tipo de Consolidação: I (instituição independente) ou C (conglomerado) |
| TC | Tipo de Controle: 1 (público), 2 (privado nacional), 3 (privado com controle estrangeiro) |
| Cidade, UF | Sede da instituição, conforme o cadastro do BC |
| Data | Data-base do relatório |
| Ativo Total | Contas Cosif [1000000009] + [2000000008] |
| Carteira de Crédito | Contas Cosif [1600000007] + [1741000007] + [1810000000] + [1887900009] + [1899600005] |
| Títulos e Valores Mobiliários | Contas Cosif [1300000008] − [1330000009] |
| Passivo Exigível | Conta Cosif [4000000006] |
| Captações | Contas Cosif [4100000009] + [4200000002] + [4300000005] − [4391000007] − [4392000006] + [4600000004] |
| Patrimônio Líquido | Contas Cosif [6000000004] + [7000000003] + [8000000002] |
| Lucro Líquido | Contas Cosif [7000000003] + [8000000002] |
| Número de Agências | Agências, incluídas as sedes (exceto para cooperativas) |
| Número de Postos de Atendimento | Postos de atendimento da instituição |

Descrição completa das contas: [Manual do Cosif](https://www3.bcb.gov.br/aplica/cosif). Atenção: o **PL contém o resultado** (contas 7000000003 e 8000000002 aparecem em PL e em Lucro), então as duas colunas nunca são somadas.

</details>

### 6.4 Unidade monetária

A base mantém os valores em R$ mil (colunas com sufixo `_RS_mil`). As medidas convertem para R$ (× 1.000), e cada visual usa unidade de exibição fixa (trilhões, bilhões ou milhões), indicada no título.

---

## 7. Metodologia

### 7.1 Pipeline

1. **Aquisição:** CSVs brutos guardados em `data/raw/`, sem edição.
2. **Profiling:** contagem de linhas e colunas por data, nulos, duplicidade de `Código` + `Data`, tipos, separador e formato decimal.
3. **Tratamento (Power Query):** função única de importação aplicada às seis datas, empilhamento (*Append*), padronização de tipos, nomes e unidade, e `Data` convertida para o último dia do mês. Nulos de agências tratados com flag, sem remoção de linhas.
4. **Modelagem:** esquema estrela (7.2).
5. **Medidas DAX:** organizadas por tema e comentadas em `docs/medidas_dax.md`.
6. **Validações:** seção 8.
7. **Visualização e storytelling:** quatro páginas com insight no formato achado → evidência → e daí?.

### 7.2 Modelo de dados

| Tabela | Tipo | Grão | Observação |
|---|---|---|---|
| `fato_ifdata` | Fato | Instituição × data | Valores, rede e atributos classificatórios (TCB, SR, TD, TC, Cidade, UF) |
| `dim_instituicao` | Dimensão | Um `Código` | 1.508 linhas; nome mais recente por código |
| `dim_data` | Dimensão | Data-base trimestral | Gerada em DAX, uma linha por data-base |
| `dim_uf` | Dimensão | UF | 27 UFs com região (IBGE) |
| `dim_topn` | Auxiliar | Faixa Top N | Sem relacionamento; alimenta a curva de concentração |

Relacionamentos 1:N, com direção única (a dimensão filtra o fato): `dim_instituicao[Codigo]`, `dim_data[Data]` e `dim_uf[UF]` para `fato_ifdata`.

### 7.3 Decisões de modelagem

| Decisão | Motivo |
|---|---|
| `Código` como chave de acompanhamento | Há 1.647 nomes distintos para 1.508 códigos (renomeações). O nome não é chave confiável |
| Atributos classificatórios no fato | SR, TC e TCB podem mudar entre datas. A classificação vale na **data da observação** |
| Participações, CR e HHI com `ALL` sobre a dimensão | Filtros de visual (como "N primeiros") não alteram o denominador |
| Datas por `EOMONTH`, sem marcar tabela de datas | O calendário é trimestral e o Power BI exige dias contínuos para marcá-lo |
| Comparação de períodos equivalentes | YoY só em 03/2026 e 06/2026; LTM só a partir de 12/2025 |
| Indicadores por agência só para instituições com rede | O IFData não conta agências de cooperativas |
| UF e região são da **sede** | O IFData consolida toda a rede na UF da sede. Não mede cobertura |
| Cor neutra em indicadores de concentração | Mais concentração não é inequivocamente boa ou ruim |

### 7.4 Tratamento do lucro líquido

O lucro é a única variável de **fluxo** da base (as demais são saldos) e é **acumulado dentro do semestre**: março e setembro trazem 3 meses; junho e dezembro, 6 meses. Para validar a regra, comparei razões entre datas-base com o valor esperado em cada hipótese.

| Razão | Esperado: regra semestral | Esperado: acumulado anual | Sistema | Top 5 por ativo |
|---|---|---|---|---|
| Lucro 9/2025 ÷ 12/2025 | ≈ 0,50 | ≈ 0,75 | 0,44 | 0,49 |
| Lucro 12/2025 ÷ 3/2026 | ≈ 2,0 | ≈ 4,0 | 2,44 | 2,17 |
| Lucro 9/2025 ÷ 6/2025 | ≈ 0,50 | ≈ 1,5 | 0,47 | n/d |

Todos os resultados ficaram próximos da hipótese semestral. Os pequenos desvios são compatíveis com a sazonalidade do 4º trimestre.

**Derivação do lucro trimestral:** 1T = março; 2T = junho − março; 3T = setembro; 4T = dezembro − setembro. A subtração é feita **instituição por instituição**, considerando apenas as presentes na data atual, para que entradas e saídas não distorçam o total. Resultado: seis trimestres comparáveis (1T25 a 2T26).

**Rentabilidade:** o indicador principal é o **LTM** (soma de quatro trimestres sobre o saldo final), que elimina a sazonalidade. O **run-rate** (lucro trimestral × 4 sobre o saldo médio) serve para comparar o mesmo trimestre entre anos. O lucro do 4T25 (R$ 76,6 bi) e o do 1T26 (R$ 56,2 bi) fazem o ROE run-rate oscilar entre 18,6% e 13,3%.

### 7.5 Indicadores

| Indicador | Fórmula | Observação |
|---|---|---|
| Participação (share) | Valor da instituição ÷ total do filtro | Independe de filtros de visual |
| CR1, CR5 | Soma das 1 ou 5 maiores participações | Em ativo e em carteira |
| HHI | Σ (share²) × 10.000 | Usado como tendência, não como faixa de antitruste |
| Nº efetivo de instituições | 10.000 ÷ HHI | Instituições de igual tamanho que gerariam o mesmo HHI |
| Crescimento (YoY) | (atual ÷ ano anterior) − 1 | Disponível em 03/2026 e 06/2026 |
| Contribuição ao crescimento | Variação da instituição ÷ variação do total | Inclui entradas e saídas |
| Alavancagem | Ativo ÷ PL | Exclui PL ≤ 0 |
| Lucro trimestral | Ver 7.4 | |
| Lucro LTM | Soma de quatro trimestres | A partir de 12/2025 |
| ROA e ROE LTM | Lucro LTM ÷ ativo (ou PL) final | ROE = ROA × alavancagem, de forma exata |
| ROA e ROE run-rate | Lucro trimestral × 4 ÷ saldo médio | Em 03/2025 usa saldo final |
| Ativo, carteira e lucro por agência | Valor ÷ agências | Só instituições com rede |
| Índice rede/crédito (UF) | % das agências ÷ % da carteira | Reflete a sede, não a cobertura |

### 7.6 Convenções de leitura

- **Variações relativas** em %; **diferenças entre percentuais** (CR, shares, ROE, ROA) em **pontos percentuais (p.p.)**; **HHI** em pontos do índice.
- Rótulos de referência dos cartões indicam se a comparação é anual ou trimestral.
- Quando não há base de comparação (por exemplo, YoY em 2025), o cartão informa isso em vez de exibir zero.

---

## 8. Validações

| Validação | Resultado |
|---|---|
| Regra semestral do lucro (razões em 7.4) | Confirmada |
| `Código` como chave: `dim_instituicao` com 1.508 linhas e relacionamento 1:N sem aviso de muitos-para-muitos | OK |
| Valores de referência do IFData (ex.: Itaú em 06/2026: ativo de R$ 2.845.762.304 mil e lucro do 2T26 de R$ 11.976.553 mil, que é 24.035.567 − 12.059.014) | Conferem |
| Integridade contábil: ativo = passivo exigível + PL (Itaú, 06/2026: diferença de R$ 1 mil, por arredondamento) | OK. [PREENCHER: confirmar `Dif Contabil %` no total] |
| Soma das participações por instituição, UF e região | 100% |
| Totais por região e UF contra o total (1.406 instituições, 14.796 agências, 17.810 postos e R$ 19.458.902.520 mil de ativo) | Conferem |
| Identidade ROE LTM = ROA LTM × alavancagem | OK |
| Coerência entre cartões e tabelas por data | OK |
| Checklists por página (visuais, interações e valores de referência) | Todos atendidos |

---

## 9. Limitações

- **Seis datas** permitem falar em direção, não em tendência estatística. O YoY existe apenas em 03/2026 e 06/2026, e o LTM só a partir de 12/2025.
- **Saldos finais:** o ROE e o ROA LTM usam saldo final, e o run-rate de 03/2025 também, o que faz o YoY de 03/2026 misturar métodos.
- **Entradas e saídas:** o número de instituições varia entre datas (de 1.430 a 1.406). Totais e contribuições comparam conjuntos diferentes. A última data pode ser reapresentada.
- **Concentração:** o HHI e o CR5 usam o ativo total e não definem um mercado relevante. A base mistura bancos, cooperativas e instituições de pagamento.
- **Agências:** o IFData não conta agências de cooperativas. Variações de agências em um trimestre (ex.: Itaú −8,8%) podem refletir reclassificação.
- **Geografia:** UF e cidade são da **sede**, e a rede de cada conglomerado é atribuída à UF da sede. Não há medida de cobertura bancária regional.
- **Classificação:** SR, TC e TCB seguem a data da observação. A variação de ativo entre segmentos pode misturar crescimento e mudança de segmento.
- **Outliers:** instituições com PL baixo geram ROE extremo (ex.: Nubank, 66%) e não devem ser citadas como referência. Indicadores por agência não valem para instituições com pouquíssimas agências (ex.: BNDES, com 5).

---

## 10. Próximos passos (projeto 3 em Python)

Os pontos que o Power BI limita viram o escopo do projeto seguinte:

- Testes estatísticos (correlação entre tamanho e rentabilidade, diferenças entre grupos de controle).
- Segmentação de instituições por perfil (estrutura de balanço, rentabilidade e rede) com clustering.
- Detecção de anomalias e previsão de séries.
- Reaproveitamento do dicionário de dados, das validações e da derivação do lucro trimestral, comparando resultados com este projeto.
- Ampliar a série (datas anteriores a 03/2025, o que permitiria YoY em todo o período) e incluir dados de agências por município para medir cobertura.

---

## 11. Comparativo com a versão em Excel

| Aspecto | Excel (projeto 1) | Power BI (este) |
|---|---|---|
| Datas-base | 1 (06/2026) | 6 (03/2025 a 06/2026) |
| Modelo | Tabela única | Esquema estrela com cinco tabelas |
| Unidade | R$ mil na base, conversão no visual | R$ mil na base, conversão nas medidas e unidades fixas por visual |
| Lucro | Valor do período | Lucro trimestral derivado, LTM e run-rate, com validação |
| Concentração | Participações | CR1, CR5, HHI, número efetivo, contribuição ao crescimento |
| Comparabilidade | Não aplicável | YoY e variação trimestral, com tratamento de lacunas |
| Validação | [PREENCHER] | Testes de integridade e checklists por página |

---

## 12. Estrutura do repositório

```
ifdata-bcb-powerbi/
├── README.md
├── LICENSE
├── .gitignore
├── data/
│   ├── raw/                      # CSVs originais do IFData, sem edição
│   └── dicionario_dados.md
├── powerbi/
│   └── ifdata_powerbi.pbix
├── docs/
│   ├── medidas_dax.md            # medidas por pasta, com comentários
│   ├── metodologia.md            # decisões de modelagem (opcional)
│   ├── relatorio_ifdata.pdf      # versão estática do relatório
│   └── img/                      # prints das páginas
```

---

## 13. Como reproduzir

1. Clone o repositório e instale o **Power BI Desktop** ([PREENCHER: versão utilizada]).
2. Os CSVs estão em `data/raw/`. Se preferir, baixe-os novamente no [IFData](https://www3.bcb.gov.br/ifdata/): data-base, tipo de instituição "Conglomerados Financeiros e Instituições Independentes", relatório "Resumo", formato CSV.
3. Abra `powerbi/ifdata_powerbi.pbix` e, em **Transformar dados > Configurações da fonte de dados**, aponte para a pasta `data/raw/` do seu computador. [PREENCHER: se houver parâmetro de pasta, informar o nome]
4. Atualize o modelo. As datas, o calendário e as dimensões são recalculados.
5. Confira os valores de referência da seção 8 (por exemplo, Itaú em 06/2026).

---

## 14. Competências demonstradas

- **Preparação de dados:** Power Query (função de importação, *Append*, tipos, normalização de datas), profiling e tratamento de chaves inconsistentes.
- **Modelagem dimensional:** esquema estrela, relacionamentos 1:N, decisão entre atributos na dimensão e no fato.
- **DAX:** medidas de variação com `EOMONTH`, `TOPN`, `RANKX`, `SUMX` e `CONCATENATEX`, controle de contexto de filtro (`ALL` e `ALLSELECTED`), tabelas calculadas.
- **Análise financeira:** concentração (CR5, HHI), alavancagem, ROA e ROE (LTM e run-rate), decomposição do ROE.
- **Rigor analítico:** validação de hipóteses sobre os dados (lucro acumulado), testes de integridade, documentação de limitações.
- **Comunicação:** storytelling em quatro páginas, insights em formato achado → evidência → e daí?, unidades e fontes explícitas.

---

## 15. English summary

**IFData BCB: Brazilian financial system analysis in Power BI.** Project 2 of a 3-part portfolio (Excel, Power BI, Python) built on public data from the Central Bank of Brazil (IFData). Six consecutive quarterly snapshots (Mar/2025 to Jun/2026) cover about 1,400 financial conglomerates and independent institutions.

Technical highlights: a star-schema model with a quarterly calendar, custom period-over-period DAX that avoids time-intelligence functions, and a validated treatment of a semester-accumulated profit series (quarterly profit derived by differencing, LTM and run-rate returns). Concentration is measured with CR1, CR5, HHI and effective number of institutions.

Key findings (Jun/2026 vs Jun/2025): assets grew 12.6% while quarterly profit was flat (+0.6%), so ROE fell from 16.3% to 15.1% despite higher leverage; the top 5 institutions hold 57.4% of assets but explain only 46.4% of asset growth; the branch network shrank 13.3% while service points grew 6.2%. Geography reflects headquarters location, not coverage, a limitation documented in the report.

---

## 16. Fonte, licença e contato

- **Fonte dos dados:** Banco Central do Brasil, [IFData](https://www3.bcb.gov.br/ifdata/). Dados públicos, sujeitos a reapresentação. [PREENCHER: confirmar os termos de uso e de citação no site do BCB]
- **Licença do código e da documentação:** [PREENCHER: sugestão MIT]. Os dados mantêm os termos da fonte.
- **Contato:** [PREENCHER: LinkedIn e e-mail]

*Última atualização: 28/10/2026.*
