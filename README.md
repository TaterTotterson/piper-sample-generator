# Piper Sample Generator (Internal Fork)

This fork is maintained only as a dependency for:

- `microWakeWord-Trainer-AppleSilicon`
- `microWakeWord-Trainer-Nvidia-Docker`

It is not intended to be used as a standalone project.

## Scope

- Keeps compatibility with the two trainer repos above.
- Includes the files those repos rely on (`generate_samples.py`, `piper_train`, model metadata JSON files, and related assets/scripts).
- May diverge from upstream whenever needed for trainer stability.

## Usage

Use this repository through the trainer projects.  
Do not rely on this README for standalone setup instructions.
