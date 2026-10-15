# MathGPT & TeacherGPT — FLAN-T5 Math Generation and Tutoring Interface

This project explores fine-tuning the `google/flan-t5-small` encoder-decoder model to generate step-by-step solutions for math problems, then wrapping the trained checkpoint in a simple TeacherGPT Gradio interface.

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](./LICENSE)

## Workflow

1. Load `mathgpt_dataset.csv`, normalize the column names, keep `problem` and `solution`, remove empty/duplicate problems, and write `mathgpt_dataset_clean.csv`.
2. Tokenize prompts prefixed with `Solve step by step:` and target solutions.
3. Fine-tune `google/flan-t5-small` with PyTorch/AdamW; the source configures 50 epochs and a 90/10 train/validation split.
4. Load the saved `mathgpt_flan_t5_small` checkpoint for generation, including few-shot examples and beam-search settings.
5. Define a Gradio interface that accepts a math problem and displays the generated solution.

## Repository contents and missing prerequisites

| File or artifact | Status in current repository snapshot |
|---|---|
| `mathsgpt_&_teachergpt.py` | Training, generation, and UI code exported from Colab |
| `linechart.png` | Training-versus-validation loss image |
| `mathgpt_dataset.csv` | Expected input; not present in the project directory listing |
| `mathgpt_dataset_clean.csv` | Generated during data preparation; not present in the project directory listing |
| `mathgpt_flan_t5_small/` | Expected trained checkpoint/tokenizer directory; not present in the project directory listing |

**The project is not runnable end to end from the checked-in files alone.** The dataset and saved model/tokenizer checkpoint need to be supplied or recreated. Additionally, `demo.launch()` is commented out in the checked-in script, so the Gradio interface does not start automatically when the file reaches its last line.

## Expected dataset schema

The input CSV must contain two columns (column names are normalized to lowercase):

- `problem` — math question or exercise text.
- `solution` — target worked solution used during fine-tuning.

The existing README describes a small textbook-style dataset, but that CSV is absent from the repository inventory, so its size, licensing, provenance, category balance, and quality cannot be independently verified from the checked-in files.

## Environment and execution

Core libraries used by the source include `pandas`, `torch`, `transformers`, `sentencepiece`, `matplotlib`, and `gradio`. The script is exported from a Colab notebook and calls `display()`, so use it as ordered notebook cells or adapt notebook-only behavior for a conventional Python environment.

To reproduce the workflow, provide the dataset, run the cleaning and training stages in order, confirm the checkpoint directory is created, then uncomment or explicitly launch the Gradio app after loading the saved model.

## Limitations

- Generated math solutions can contain arithmetic or reasoning errors and are not verified by a symbolic math engine or formal test suite.
- The dataset and checkpoint are not supplied in this repository snapshot, limiting independent reproduction.
- The Gradio launcher is commented out, and the TeacherGPT stage assumes that a valid trained checkpoint already exists.
- Training/runtime requirements vary by hardware; GPU execution is optional in the source but may materially affect training time.

## Author

**Shubham Kumar Singh**

## License

This project is licensed under the MIT License. The complete license is available in [`LICENSE`](./LICENSE) and reproduced below.

MIT License

Copyright (c) 2026 Shubham Kumar Singh

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.
