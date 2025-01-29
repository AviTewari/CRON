# Daily Number Incrementer

A Python script that automatically increments a number in a text file, commits the change to Git, and updates a cron job to run the script at a new random time daily.
## Setup

1. Clone this repository:

```bash
git clone https://github.com/AviTewari/CRON
cd CRON
```

2.  Run the script

The script can be run without dependencies besides the Python standard library,
simply by running

```bash
python update_number.py
```

You might want to run the script manually for the first time to verify it works
before setting up a cronjob

3. # Optional: If you prefer to ensure the script runs at a fixed time initially, you can manually set up a cron job:
   However, if you wish to use LLM-based commit message generation, you need to
   install [uv](https://docs.astral.sh/uv) to manage dependencies.
   The first time you run it, it will download packages required for its execution
   and also a large language model from Hugging Face

```bash
# Use LLM
FANCY_JOB_USE_LLM=true uv run python update_number.py
```

3. Setup a cron job to run the script daily:

```bash
crontab -e
```

Add the following line to the crontab file:

```bash
0 6 * * * cd /path/to/your/repo && python update_number.py
# or with LLM
0 6 * * * cd /path/to/your/repo && FANCY_JOB_USE_LLM=true uv run python update_number.py
```

This will initially run the script at 6am the next day.

## Usage

The script will increment the number in `number.txt` and commit the change to git. You can modify the script to increment by any value or use a different file to store the number.
