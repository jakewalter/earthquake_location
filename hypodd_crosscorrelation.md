# HypoDDpy: A Quick Guide to Event Relocation

This guide provides instructions on how to install and run the `hypoDDpy` library for relocating seismic events using cross-correlation.

-----

## Installation

To get started, clone the repository from GitHub and run the `pip` install command from within the project directory.

```bash
git clone https://github.com/jakewalter/hypoDDpy.git
cd hypoDDpy
pip install .
```

-----

## Example Usage

The following script demonstrates a complete relocation workflow, from preparing the data to running the final relocation. The code is commented to explain each step.
```python
import glob
from hypoDDpy.utils import fix_picks_catalog
from hypoDDpy.relocator import HypoDDRelocator

cat2 = fix_picks_catalog(cat, project_folder)
cat2.write('catalog_fixed.xml', 'QUAKEML')

relocator = HypoDDRelocator(
    working_dir="relocate1",
    cc_time_before=0.05,
    cc_time_after=0.2,
    cc_maxlag=0.2,
    cc_filter_min_freq=2.0,
    cc_filter_max_freq=14.0,
    cc_p_phase_weighting={"Z": 1.0},
    cc_s_phase_weighting={"E": 1.0, "N": 1.0, "1": 1.0, "2": 1.0},
    cc_min_allowed_cross_corr_coeff=0.6
)

relocator.add_event_files(glob.glob("/data/proj_dir/catalog_fixed.xml"))
relocator.add_waveform_files(glob.glob("/data/proj_dir/20*/mseed"))
relocator.add_station_files(glob.glob("/data/proj_dir/20*.xml"))

relocator.setup_velocity_model(
    model_type="layered_p_velocity_with_constant_vp_vs_ratio",
    layer_tops=[(0, 2.7), (0.3, 2.95), (1.0, 4.15), (1.5, 5.8), (21, 6.3)],
    vp_vs_ratio=1.73
)

relocator.start_relocation(output_event_file="relocated_events.xml")

print("Relocation complete! Results saved to relocated_events.xml.")
```

