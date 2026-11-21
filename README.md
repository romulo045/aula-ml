# aula-ml

Versionamento de dados e modelos com Git e DVC (Atividade Prática 07, CK0444).

## Pré-requisitos

- Git
- Python 3.10 ou superior (o classificador usa só a biblioteca padrão)
- DVC 3 (`pip install 'dvc>=3,<4'`)

## Armazenamento DVC

Os CSVs e o modelo ficam no armazenamento local `../dvc-storage`, configurado
como remote padrão (`storage`) em `.dvc/config`. O GitHub guarda apenas os
commits, as tags, os descritores `.dvc` e os relatórios.

Para restaurar, a pasta `dvc-storage` precisa estar ao lado do clone
(mesmo computador). Confira com `dvc remote list`.

## Restaurar uma versão

```bash
git clone https://github.com/romulo045/aula-ml.git aula-ml-restauracao
cd aula-ml-restauracao
git switch --detach modelo-r1   # ou dados-v1, dados-v2, modelo-r2
dvc pull
```

Depois confira os hashes de `data/chamados.csv`, `data/split.csv` e
`models/model.json` contra `reports/modelo.json`.

## Tags

| Tag | Conteúdo |
|---|---|
| `dados-v1` | Dataset inicial, com erro de anotação no ID 006 |
| `modelo-r1` | Modelo treinado com `chamados-v1` |
| `dados-v2` | Dataset com o rótulo do ID 006 corrigido |
| `modelo-r2` | Modelo treinado com `chamados-v2` |

## Treinar

```bash
python3 src/train.py chamados-rN
```