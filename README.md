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

## Checkpoint source

[Mondo-Robotics/PMT](https://github.com/Mondo-Robotics/PMT/blob/1a92390077d329d22cbcdbf89c4a5c982003fbc8/README.md) · [multimotionv2_flat.pt](https://huggingface.co/datasets/aCodeDog/PMT-assets/blob/38f9f7dba893385c6219620b72314396247c9e82/checkpoints/pretrained/multimotionv2_flat.pt). Author-released checkpoint.

The adapter pins this published artifact by SHA256. Artifact identity is separate from inference parity.

One `uv run evaluate.py` rolls out each complete motion once, then verifies the trace.
The same trajectory provides success, completion and all six MPBPE values in one
`result.json`, with one source revision. No branch switching is needed.
