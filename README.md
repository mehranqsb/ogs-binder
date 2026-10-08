# OGS examples on Binder

[Launch the tunnel excavation notebook on Binder](https://mybinder.org/v2/gh/mehranqsb/ogs-binder/main?labpath=01_Tunnel_Excavation_Kirsch%2F01_tunnel_excavation_kirsch.ipynb)

Binder installs OGSTools 0.8 and the OGS executable from the root
`requirements.txt`, plus the system libraries in `apt.txt`.

## Run the tunnel example

1. Push the Binder configuration files to GitHub before launching the link.
2. Open the launch link above and wait for the environment to build.
3. In JupyterLab, select **Run → Run All Cells** in the notebook.
4. Wait for mesh generation, the OGS simulations, and the comparison plots.
   Results are written under `01_Tunnel_Excavation_Kirsch/_out/`.

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
