# Dashboard — CRM Jurídico

Funil comercial-jurídico do escritório Borges Macedo Advocacia, alimentado em tempo real
pela planilha **"CRM - BM Advocacia"** do Google Sheets.

**Acesso exclusivo das lideranças.** Só os perfis **Administração** e **Lideranças** têm
cofre neste painel.

## O que é exibido

| Seção | Conteúdo |
|---|---|
| Resumo Executivo | Análises produzidas, taxa de viabilidade, viável que agendou, atendimentos, no-show, win rate, receita inicial contratada e SLA da análise. Filtro por ano |
| Funil Comercial-Jurídico | Análise → viável → agendado → realizado → contrato, com conversão de cada degrau, participação do topo e perda absoluta na etapa |
| Produção Técnica | Volume mensal por frente (pareceres × diagnósticos), viabilidade e distribuição do tempo de entrega |
| Onde Está o Dinheiro da Análise | Concentração por instituição financeira e por operadora de saúde, com viabilidade e taxa de agendamento de cada recorte |
| Atendimentos e Fechamento | Atendimentos e contratos por mês com win rate mensal, e ranking de motivos de não fechamento |
| Desempenho do Time | Produção por SDR (volume × viabilidade × agendamento) e win rate por closer, com tabela de no-show e ticket médio |
| Produtos Jurídicos | Volume, conversão, ticket e receita inicial por produto |
| Pontos de Atenção | Leitura executiva automática dos números |

## Fontes

| Aba | Papel |
|---|---|
| `Diagnóstico Saúde` | Análise de viabilidade de revisão de plano de saúde — plano, modalidade, mensalidade atual/revisada, restituição |
| `Pareceres Bancários` | Análise de contratos bancários — instituição, tipo de contrato, excesso mensal |
| `Fluxo de Atendimentos ` | Atendimentos, closer, status, honorários e desfecho da negociação |

> A aba de atendimentos tem um **espaço no fim do nome** na planilha
> (`'Fluxo de Atendimentos '`). O range reproduz isso — renomear a aba sem o espaço
> exige ajustar o código.

## Métricas e como são calculadas

- **Taxa de viabilidade** = análises viáveis ÷ análises produzidas.
- **Viável que agendou** = viáveis com "Atendimento agendado? = Sim" ÷ viáveis. É o
  degrau que mede o aproveitamento do trabalho técnico já executado.
- **No-show** = atendimentos com status "No Show" ÷ total de atendimentos.
- **Win rate** = "Cliente Ganho" ÷ (ganhos + perdidos). Considera só os **decididos** —
  atendimentos sem desfecho registrado ficam de fora e são reportados à parte.
- **SLA da análise** = dias entre "Data do envio" e "Data da entrega", com média, mediana
  e percentual entregue em até 1 dia. Valores acima de 120 dias são descartados como erro
  de digitação.
- **Receita inicial contratada** = soma dos honorários iniciais dos contratos ganhos. Não
  inclui o êxito, que é a maior parte da receita do modelo.

## Armadilhas tratadas

- **`Dezembro/99`** nas colunas de mês automático é data vazia, não dezembro de 2099 — é
  descartado do agrupamento temporal.
- Meses são lidos do rótulo (`Agosto/25`) **ou** derivados da data real do atendimento,
  o que for mais confiável.
- Linhas em que o cabeçalho se repete no meio da aba são removidas.
- Colunas do bloco de negociação (upsell, temperatura, próximo passo) estão em grande
  parte vazias na planilha — o painel reporta isso em vez de exibir zero como se fosse
  resultado.
