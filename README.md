# Piper Sample Generator (microWakeWord Fork)

This fork is intentionally trimmed for our wake-word training workflows:

- `microWakeWord-Trainer-AppleSilicon`
- `microWakeWord-Trainer-Nvidia-Docker`

The goal of this repo is only to generate synthetic WAV samples with Piper.

## What Is Kept

- `generate_samples.py`
- Minimal runtime dependency files (`requirements.txt`, `pyproject.toml`)
- `models/en_US-libritts_r-medium.pt.json` (metadata required by the English `.pt` generator)

## What Was Removed

- Upstream Piper training package code (`piper_train/`)
- Audio augmentation script and impulse assets (`augment.py`, `impulses/`)
- Bundled model binaries (`models/*.pt`, `models/*.onnx`)
- Dev/lint helper scripts and config files

## Install

```sh
python3 -m venv .venv
source .venv/bin/activate
python3 -m pip install --upgrade pip
python3 -m pip install -r requirements.txt
```

Or:

```sh
python3 -m pip install -e .
```

## Usage

Generate from a Piper `.onnx` voice:

```sh
python3 generate_samples.py \
  "okay piper" \
  --model /path/to/voice.onnx \
  --max-samples 2000 \
  --output-dir /path/to/output
```

Generate from a Piper `.pt` generator:

```sh
python3 generate_samples.py \
  "okay piper" \
  --model /path/to/generator.pt \
  --max-samples 2000 \
  --batch-size 8 \
  --output-dir /path/to/output
```

Use a text file (one phrase per line):

```sh
python3 generate_samples.py \
  /path/to/phrases.txt \
  --model /path/to/voice.onnx \
  --max-samples 2000 \
  --output-dir /path/to/output
```

## Notes

- `--max-samples` is required.
- You can pass `--model` more than once for `.onnx` models to cycle through voices.
- For `.pt` models, only one `--model` is supported.
- Advanced controls (`--length-scales`, `--noise-scales`, `--noise-scale-ws`, `--max-speakers`) are available via `--help`.

This repo is now maintained as a focused dependency for the two trainer projects above.
