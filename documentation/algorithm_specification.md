# Algorithm specification

## Algorithm 1: RD-HDDM-GNN prediction

**Inputs:** fine mesh graph, fine-node features, sensor mask, observed normalized temperatures, connected Part assignment, coarse adjacency, trained parameters, correction scale.

1. Predict the normalized fine-node field using the fine Mesh GNN.
2. Compute sensor observation residuals only at sensor nodes.
3. Restrict residuals to Parts using sensor-area-weighted averaging.
4. Append the sensor-presence indicator and Part descriptors.
5. Propagate the Part representation over the coarse adjacency graph.
6. Decode one correction for each Part.
7. Repair/prolong the Part corrections to fine nodes using the boundary-aware blend.
8. Compute the nodewise local gate and scalar global gate.
9. Add the scaled gated correction to the fine prediction.

The hierarchy contributes only a correction and cannot generate an independent field.
