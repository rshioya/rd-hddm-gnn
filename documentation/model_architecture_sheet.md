# Model architecture sheet

Complete this sheet using the frozen configuration and parameter-export output.

## Fine Mesh GNN

- Encoder layers:
- Processor/message-passing layers:
- Hidden dimension: 64
- Activation:
- Normalization:
- Decoder layers:
- Parameters:

## Coarse residual network

- Number of Parts: 16
- Coarse message-passing layers:
- Hidden dimension:
- Activation:
- Decoder layers:
- Parameters:

## Gate network

- Input: fine hidden feature plus a three-component residual feature
- MLP dimensions: 67–64–1
- Output activation: sigmoid
- Parameters:

## Total

- Trainable parameters: 81,348
- Executed-path parameters: 81,348
