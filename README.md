# Decentralised Enterprise Knowledge Graph: Query and Reply experimentations results

## School toy dataset

This dataset have been created for testing purposes and represent the running example of the DEKG Query/Reply approach. It contains both relational database content and tabular documents.

| Query (Natural Language) | Conjunctive Query | Query Type | Time (average 10 queries) | Semantic links used | Number of queried types on BV | Number of queried types on GS | Grouped results | Reply volume (number of elements) |
|---|---|---|---|---|---|---|---|---|
| All People which are Teachers, and similar data | { p \| ∃(∅) ∧ ηp(p) = People ∧ p.Type = "Teacher" ∧ B } | Single Node subtype + Broad selection | 41.044ms | 0 | 1 | 1 | 0 | 4 |
| All People | { p \| ∃(∅) ∧ ηp(p) = People } | Single Node type selection | 41.586ms | 2 | 1 | 3 | 2 | 7 |
| All People, Classes and similar types, linked together with a People-Class or similar relationship | { p, pc, c \| ∃(∅) εDE(p, pc, c) ∧ ηp(p) = People ∧ ηp(c) = Class ∧ ξp(pc) = People-Class ∧ B } | 1deg Relationship selection | 28.304ms | 4 | 3 | 7 | 2 | 10 |
| All People, Classes, linked together with a People-Class, plus all Grades | { p, pc, c, g \| ∃(∅) εDE(p, pc, c) ∧ ηp(p) = People ∧ ηp(c) = Class ∧ ξp(pc) = People-Class ∧ ηp(g) = Grades } | 1deg Relationship selection + single node selection | 40.213ms | 4 | 4 | 8 | 2 | 12 |

## France OpenData

This Dataset is built against three France OpenData sets: two french Toulouse city Opendata (Communes Toulouse - https://data.toulouse-metropole.fr/explore/dataset/communes/information/, accessed 2021-05-11) and Code postaux Toulouse (https://data.toulouse-metropole.fr/explore/dataset/codes-postaux-de-toulouse/information/, accessed 2021-05-11) containing data on all Cities of Toulouse and ZIP Codes; and a COVID-19 dataset from France (Centres de Vaccination - https://www.data.gouv.fr/fr/datasets/relations-commune-cms/, accessed 2021-05-11) representing all available vaccination centres in France. Data has been fetched using their REST API.

| Query (Natural Language) | Conjunctive Query | Query Type | Time (average 10 queries) | Semantic links used | Number of queried types on BV | Number of queried types on GS | Grouped results | Reply volume (number of elements) |
|---|---|---|---|---|---|---|---|---|
| All Cities | { c \| ∃(∅) ∧ ηp(c) = Cities } | Single Node type selection | 48.356ms | 0 | 1 | 1 | 0 | 37 |
| All Cities and similar | { c \| ∃(∅) ∧ ηp(c) = Cities ∧ B } | Single Node broad type selection | 40.511ms | 0 | 1 | 1 | 0 | 37 |
| All entities | { d \| ∃(∅) ∧ ηp(d) = * } | All nodes selection | 89.536ms | 0 | 3 | 3 | 0 | 2366 |

## Team of Teams survey data company

This dataset has been extracted from internal employee survey, representing each employee skills level, field of work, and also hobbies as two CSV documents. The documents contains a few lines but a lot of columns. Data is anonymised.

| Query (Natural Language) | Conjunctive Query | Query Type | Time (average 10 queries) | Semantic links used | Number of queried types on BV | Number of queried types on GS | Grouped results | Reply volume (number of elements) |
|---|---|---|---|---|---|---|---|---|
| All employees general skills | { e \| ∃(∅) ∧ ηp(e) = Employee-Skills-1 } | Single node type | 98.014ms | 0 | 1 | 1 | 0 | 34 |
| All employees specific skills | { e \| ∃(∅) ∧ ηp(e) = Employee-Skills-2 } | Single node type | 130.177ms | 0 | 1 | 1 | 0 | 40 |
| All employees skills | { e1, e2 \| ∃(∅) ∧ ηp(e1) = Employee-Skills-1 ∧ ηp(e2) = Employee-Skills-2 ∧ e1.id = e2.id } | Two node types selection | 215.386ms | 0 | 2 | 2 | 0 | 68 |
