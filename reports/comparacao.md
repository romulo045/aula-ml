# Comparação entre r1 e r2

## Alteração feita

O chamado `006` ("bloqueio de acesso") estava rotulado como `comum`. Pela regra
de rotulagem, bloqueio é urgente, então o rótulo foi corrigido para `urgente`
(dataset `chamados-v1` → `chamados-v2`). A partição treino/teste (`split.csv`)
não mudou.

## Métricas (mesma partição de teste, 4 exemplos)

| Métrica | r1 (chamados-v1) | r2 (chamados-v2) |
|---|---|---|
| Acurácia | 0.75 (3/4) | 1.0 (4/4) |
| Recall de urgentes | 0.5 (1/2) | 1.0 (2/2) |
| Recall de comuns | 1.0 (2/2) | 1.0 (2/2) |

## Hashes

| Item | SHA-256 |
|---|---|
| Partição (r1 e r2) | `2ef820171c1a4625fe216e6da67c7c8dcf9d97a08288c0239cd23f1a6961d981` |
| Dataset v1 | `bc3fd86a3a5f598841a58839a9726d901fa7e8361ffe79c5b43873ad8a1328ac` |
| Dataset v2 | `4ca2e29cb930a9161c2a851b3c71f5529dbb812db607ee4a5ea95d2223baa14d` |
| Modelo r1 | `72a3a67936139a3473838a6dcfa7aae1acb4c23467be1ef1056d51d485b94840` |
| Modelo r2 | `7f9d94ca8dd86ccc8ad90b0839613c61a33e2168bd23bf083a4bbe1375f908ac` |

## Verificação em clone limpo (r1)

Clone de `modelo-r1`, `dvc pull` e conferência contra `reports/modelo.json`:

```
OK data/chamados.csv bc3fd86a3a5f598841a58839a9726d901fa7e8361ffe79c5b43873ad8a1328ac
OK data/split.csv 2ef820171c1a4625fe216e6da67c7c8dcf9d97a08288c0239cd23f1a6961d981
OK models/model.json 72a3a67936139a3473838a6dcfa7aae1acb4c23467be1ef1056d51d485b94840
```

Commit selecionado: `599fb15d9a2c4c7285efa668b6745e69b5ce8f62`

## Decisão

**Aceitar r2** para este exercício. Critério: melhorar o recall de urgentes sem
reduzir o recall de comuns, na mesma partição de teste. O recall de urgentes
subiu de 0.5 para 1.0 e o de comuns permaneceu em 1.0.

Limitação: o conjunto de teste tem apenas 4 exemplos, então o resultado ilustra
o efeito da correção neste exercício e não permite generalizar.