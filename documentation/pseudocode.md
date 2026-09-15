# Pseudocode

## Residual restriction

```text
for each fine node i:
    r_obs[i] = sensor_mask[i] * (observed[i] - fine_prediction[i])
for each Part p:
    denominator = sum(area[i] * sensor_mask[i] for i in Part p)
    r_part[p] = sum(area[i] * r_obs[i] for i in Part p) / (denominator + epsilon)
    sensor_present[p] = 1 if denominator > 0 else 0
```

## Partition repair

```text
for each Part label:
    find connected components in the induced fine graph
    retain the primary component
    reassign each secondary component to an adjacent Part using the documented deterministic rule
verify: exactly 16 nonempty, connected, balanced Parts
```

## Coarse graph construction

```text
create one coarse node per repaired Part
add a coarse edge when any fine edge crosses the corresponding Part boundary
```

## Prolongation and gating

```text
for each fine node i:
    own = part_correction[part(i)]
    neighbor_mean = mean(part_correction[q] for q adjacent across fine edges)
    prolonged[i] = (1 - beta[i]) * own + beta[i] * neighbor_mean
    local_gate[i] = sigmoid(gate_mlp(fine_hidden[i], residual_features[i]))
output[i] = fine_prediction[i] + alpha * global_gate * local_gate[i] * prolonged[i]
```
