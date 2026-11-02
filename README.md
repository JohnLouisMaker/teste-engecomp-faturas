# Teste Prático | EngeComp

Programa desenvolvido em Python para processar faturas de energia.

## Como executar

```bash
python3 solucao.py
```

O programa exibe os resultados no terminal e gera `resultado.json` na raiz do projeto.

## Estrutura

- `extracao.py`: extrai os dados das faturas utilizando expressões regulares.
- `validacao.py`: verifica campos obrigatórios, valores e coerência das medições.
- `regras.py`: aplica o acréscimo de 1% às distribuidoras previstas.
- `solucao.py`: coordena o processamento e gera o JSON.

## Decisões técnicas

- Separação dos módulos por responsabilidade.
- Extração linha a linha com expressões regulares.
- Normalização de datas e referências.
- Uso de `Decimal` e `ROUND_HALF_UP` nos cálculos.
- Inconsistências encontradas sem interromper o processamento.
- Campos ausentes representados por `None`.

## Resultados

| Fatura | Status | Consumo faturado | Consumo ajustado |
|---|---|---:|---:|
| 01 | VALIDADA | 3.730 kWh | 3.730,00 kWh |
| 02 | VALIDADA | 4.780 kWh | 4.827,80 kWh |
| 03 | VALIDADA | 1.275 kWh | 1.287,75 kWh |
| 04 | INCONSISTENTE | 4.815 kWh | 4.815,00 kWh |

### Inconsistência: Fatura 04

- Soma dos itens: R$ 4.350,20
- Total declarado: R$ 4.530,20
- Diferença: R$ 180,00

As leituras e os consumos estão coerentes nas quatro faturas. A divergência está na soma dos itens da quarta fatura.

## Análise dos consumos

- **Maior consumo faturado:** 4.815 kWh, unidade consumidora `7009911002`, MERCADO CENTRAL DE ALIMENTOS EIRELI, ENERGIA NORTE S.A.
- **Maior consumo ajustado:** 4.827,80 kWh, unidade consumidora `55-9087341-2`, INDUSTRIA METALURGICA BOA VISTA S/A, CIA LUZ DO VALE.

O acréscimo de 1% foi aplicado à segunda e à terceira faturas.

## Questionário

### 2. Qual foi o desafio mais marcante que você superou no desenvolvimento de uma feature ou ferramenta?

No estágio, desenvolvi uma automação em Python para extrair dados de chamados de um site interno que não possuía API. Inicialmente utilizei Selenium, mas encontrei dificuldades com o carregamento de um modal que exibia as informações (nome, data).

Posteriormente, migrei a automação para Playwright, utilizando ferramentas de IA como apoio durante a transição. Também reorganizei o código em módulos, separando melhor as responsabilidades.

A automação conseguiu coletar mais de 200 chamados em uma execução anterior e, mais recentemente, capturou outros 77 registros (tickets).

### 3. Quais etapas você costuma seguir quando está incerto sobre um problema?

Eu testo possibilidades, investigo a situação e consulto a documentação. Quando não sei algo, procuro estudar e experimentar até encontrar uma solução e entender o que foi feito/aplicado.

Principalmente hoje, com tantas informações e soluções disponíveis na internet, acredito que o importante é saber pesquisar, aplicar o conhecimento na prática, ter persistência e continuar aprendendo.

### 4. O que é PEP8?

É um conjunto de boas práticas para Python. Isso está mais voltado aos nomes claros, indentação organizada. Aplicação de `snake_case` para funções, por exemplo, faz parte do PEP8. Eu já aplico essas normas no meu código, sempre tentando manter um padrão legível.

### 5. No Git, o que são Conventional Commits?

São boas práticas para padronizar mensagens de commit e facilitar a identificação das alterações realizadas. Exemplos que eu mesmo utilizo:

- `feat`: nova funcionalidade.
- `fix`: correção.
- `refactor`: refatoração.
- `test`: testes.

Também podem incluir números de tickets para relacionar alterações às respectivas tarefas.