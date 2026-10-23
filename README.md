# PMT Flat

[PMT](https://github.com/Mondo-Robotics/PMT) · `multimotionv2_flat.pt`, iteration 19999.

```bash
git clone --recurse-submodules https://github.com/motion-challenge-project/motion-challenge-pmt-flat.git
cd motion-challenge-pmt-flat
uv sync
uv run evaluate.py
# Also measure the complete trajectory after first failure:
uv run evaluate.py --termination none
```

The core downloads and verifies missing data/weights, runs MuJoCo 3.17 batch,
and saves independently checked traces outside Git. Cached files:
`--offline --data /path/to/lafan --weights /path/to/multimotionv2_flat.pt`.

Original PyTorch actor, 286 privileged inputs, torso-relative body poses,
native normalization (`epsilon=0.01`), PD gains, action scale and joint order.
Shared benchmark physics and failure rules are owned by the core.
This is a maintainer adaptation, not an author submission.

See [provenance](provenance.json) and [inference validation](validate_inference.py).
