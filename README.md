# aseptic-line

The AAU Smart Production Lab's aseptic filling line, built with AASPIRE: its modules' specs and
generated IEC 61499 programs, their simulator, the example line's AASs (the line, the planar table
and its shuttles, the modules and their components, three products and the process of each), the
and the evaluation of the CIRP paper.

| Folder | What |
| --- | --- |
| `cell/modules/` | The module specs: filling, filling 2, stoppering, capping (`planned/`: inspection; `python/`: loading and unloading, run by modpy) |
| `cell/control/` | The 4diac projects generated from them by modgen (do not edit; regenerate) |
| `cell/sim/` | The Modbus simulator of the modules' equipment, `run_module.py`, an OPC UA client |
| `cell/examples/` | The example line's AASs: products, processes, precedence; `example_line.py` builds, checks and publishes them |
| `cell/eval/` | The CIRP paper's evaluation (each change online and by a restart, the planners timed, the figures) |
| `cell/tests/` | The line's tests: the example line, the vocabulary, and live tests against FORTE, the DMP and the Pis |

The AASPIRE repositories are cloned beside this one (`AAU-AASPIRE/<repo>`): the tools find the
ontologies, the FORTE runtime and the deployment there, and modgen finds this line's `cell/`.

```powershell
python -m modgen                                                  # regenerate cell/control from cell/modules
python cell/examples/example_line.py --out aas --publish http://localhost:8081 --target pi
python -m pytest cell/tests/test_example_line.py cell/tests/test_vocabulary.py
```

The documentation is the [AASPIRE site](https://aaspire.readthedocs.io) ([the line's page](https://github.com/AAU-AASPIRE/aaspire/blob/main/docs/lines/aseptic-line.md));
the team's working notes are in the private `aaspire-internal`. Part of [AASPIRE](https://github.com/AAU-AASPIRE/aaspire).
