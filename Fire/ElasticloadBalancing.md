# ELB

Use o comando  [modify-target-group-attributes](https://docs.aws.amazon.com/cli/latest/reference/elbv2/modify-target-group-attributes.html) para modificar os atributos

```
  modify-target-group-attributes
--target-group-arn <value>
--attributes <value>
[--cli-input-json <value>]
[--generate-cli-skeleton <value>]
```

## Atraso de cancelamento

Atributo:  `deregistration_delay.timeout_seconds`

## Modo iniciação lenta

Atributo: `slow_start.duration_seconds`.

### Algoritmo de roteamento

com o atributo `load_balancing.algorithm.type`.

