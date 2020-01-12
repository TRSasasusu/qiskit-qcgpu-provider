
# Qiskit QCGPU Provider (CUDA version)

This module contains [Qiskit](https://www.qiskit.org/) 
simulators using the CUDA based [QCGPU](https://github.com/TRSasasusu/qcgpu/tree/feature/cuda-bydefault) library.

This provider adds two quantum circuit simulators, which are:

* Statevector simulator - returns the statevector of a quantum circuit applied to the |0> state
* Qasm simulator - simulates a qasm quantum circuit that has been compiled to run on the simulator.

These simulation backends take advantage of the GPU or other CUDA devices.

## Installation

First of all, you have to install [TRSasasusu/qcgpu (cuda-bydefault)](https://github.com/TRSasasusu/qcgpu/tree/feature/cuda-bydefault).

Then, you can install this module:

```bash
$ git clone https://github.com/TRSasasusu/qiskit-qcgpu-provider
$ cd qiskit-qcgpu-provider
$ git checkout feature/cuda
$ python ./setup.py bdist_wheel
$ pip install dist/*.whl
```


## Usage

Simply replace

```python
backend = Aer.get_backend('qasm_simulator') # or 'statevector_simulator'
```

with

```python
from qiskit_qcgpu_provider import QCGPUProvider
backend = QCGPUProvider().get_backend('qasm_simulator') # or 'statevector_simulator'
```

The usage of this backend with Qiskit is shown in the [usage example](https://github.com/TRSasasusu/qiskit-qcgpu-provider/tree/feature/cuda/examples)

For more information on Qiskit and quantum simulations, look at the Qiskit tutorials and the [Qiskit instructions page](https://github.com/Qiskit/qiskit-terra)

## Benchmarking

To benchmark this simulator against the `BasicAer` `qasm_simulator`,
you can run

```bash
$ python3 benchmark.py --samples 15  --qubits 5 --single True
```

## License

This project uses the [Apache License Version 2.0 software license.](https://www.apache.org/licenses/LICENSE-2.0)
