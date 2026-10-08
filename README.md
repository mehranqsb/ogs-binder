# OGS examples on Binder

| Example | Launch in your browser |
| --- | --- |
| 01 — Tunnel excavation / Kirsch benchmark | [Launch 01](https://mybinder.org/v2/gh/mehranqsb/ogs-binder/main?labpath=01_Tunnel_Excavation_Kirsch%2F01_tunnel_excavation_kirsch.ipynb) |
| 02 — Fault-controlled injection / LIE vs. EFPM | [Launch 02](https://mybinder.org/v2/gh/mehranqsb/ogs-binder/main?labpath=02_LIE_EFPM_Fault-Controlled_Injection%2F02_lie_efpm_injection.ipynb) |
| 03 — Heated tunnel / TRM | [Launch 03](https://mybinder.org/v2/gh/mehranqsb/ogs-binder/main?labpath=03_TRM_Heated_Tunnel_FE_Experiment%2F03_trm_heated_tunnel.ipynb) |

The examples come from `OGS_Course_2026`. Notebooks, input files, mesh/project
generators, figures, and supporting data are included. Previous simulation
outputs, Python caches, notebook checkpoints, and the legacy THM archive are
excluded. Each notebook regenerates its simulation results.

Binder uses Python 3.11 as specified in `runtime.txt`, and installs
OGSTools 0.8 and the OGS executable from the root
`requirements.txt`, plus the system libraries in `apt.txt`.
The `postBuild` script checks the notebook imports and OGS executable during
the image build.

## Run an example

1. Push the Binder configuration files to GitHub before launching the link.
2. Open the launch link for the example above and wait for the environment to build.
3. In JupyterLab, select **Run → Run All Cells** in the notebook.
4. Wait for mesh generation, the OGS simulations, and the comparison plots.
   Example 01 and 03 results are written under their `_out/` folders.
   Example 02 results are written under `SingleFractureMedium/*/_out_*`
   and `DoubleFractureMedium/*/_out_*` inside its folder.

The first code cell selects the example's working directory automatically.
Example 03 runs several coupled simulations and can require more time and
memory than the other examples. Full Binder simulation runs have not yet
been verified for the newly added examples.

To check OGS first, open **File → New → Terminal** in Binder and run:

```bash
ogs --version
```

If the notebook reports that project files were not found, restart its kernel
and run this in a new cell before the other cells:

```python
import os
from pathlib import Path

example = Path.cwd() / "01_Tunnel_Excavation_Kirsch"
if not example.is_dir():
    example = Path.cwd()
os.environ["KIRSCH_PROJECT_ROOT"] = str(example.resolve())
```

Binder sessions are temporary. Download any results you want to keep before
closing the session. The first build can take several minutes.
