# Model Checkpoints

This directory contains serialized model files (`.pkl`) generated during the tomography experiments.

## How to Load
Use the `load_pickle` helper function defined in the notebook or the `QuantumModel.load` static method.

```python
import pickle

def load_pickle(path):
    with open(path, 'rb') as f:
        return pickle.load(f)

# Example
# model = load_pickle('model_track_3qubits.pkl')
```
