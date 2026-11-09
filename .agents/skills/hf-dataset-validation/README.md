# Dataset Validation Tutorial

This project follows the Hugging Face Context Course example:
https://huggingface.co/learn/context-course/en/unit1/building-skills

## Sample dataset

`test_data/sample.csv` is a tiny, manually written tutorial fixture, not a
representative training or evaluation dataset. It contains three records in
UTF-8 CSV format with a header row.

| Column | Contents |
| --- | --- |
| `text` | Example text strings |
| `label` | Integer example labels (`0` or `1`); class meanings are not defined |
| `split` | Example partition names: two `train` records and one `test` record |

## Creation and preprocessing

The three records were entered directly from the course example. No external
data was collected. No cleaning, normalization, deduplication, imputation,
tokenization, or automatic split generation was performed. Split values were
assigned in the example. Validation reads the CSV without modifying it;
pandas infers column types and recognizes its default missing-value markers.

The current sample has three rows, three columns, no missing values, and no
duplicate rows.

## Run locally

From this directory, install the dependency into the Python you use to run
the scripts:

```bash
python3 -m pip install pandas
python3 scripts/validate_dataset.py test_data/sample.csv
python3 scripts/generate_report.py test_data/sample.csv
```

`validate_dataset.py` prints a JSON report containing row counts, column names,
inferred types, missing-value counts when present, and warnings for duplicates
or whitespace-only strings. It exits with status 1 on file-reading errors.
`generate_report.py` prints a text summary and general recommendations.

These tutorial scripts do not enforce required columns, label meanings,
allowed split values, or separation between training and test examples. They
support CSV input. Passing these checks does not establish fitness for training.
The text report prints its documentation and license recommendations on every
run, even when these files already exist.

## License and attribution

The Python helper scripts and sample records come from the course linked above.
The course's example skill declares MIT in its license metadata; this tutorial
project uses MIT (see `LICENSE`). No license is asserted for other datasets you
may validate with these tools.
