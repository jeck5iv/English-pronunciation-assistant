# English Pronunciation in Context

**Retrieve timestamped examples of a word or phrase in spoken English.**

A small Python application for language learning. It indexes video subtitles in SQLite, searches for a requested phrase and returns links that start close to the matching passage. A Flask interface makes the search available through a simple form.

## Data flow

Video captions → SQLite index → phrase lookup → timestamped video links.

| Component | Source |
| --- | --- |
| Web form and result page | [app.py](app.py), [templates](templates/) |
| Query and timestamp construction | [db_search.py](db_search.py) |
| Caption ingestion and database creation | [db_creation](db_creation/) |
| Search settings | [config.py](config.py) |

## Run locally

```bash
python -m venv .venv
source .venv/bin/activate
python -m pip install Flask tqdm
python app.py
```

Open the local address printed by Flask and enter a word or phrase. The original ingestion path uses TED subtitle endpoints; availability depends on the external service and has not been rechecked in this documentation update.

`VIDEOS_COUNT` controls how many video identifiers the ingestion process examines. `VIDEO_PART_DURATION` controls how far before a match playback begins. Increasing the corpus also increases initial ingestion time.

This repository is an early applied text-retrieval project. My current research in [statistical forecasting](https://github.com/jeck5iv/highload-context-ensemble-forecasting) and [language-model adaptation](https://github.com/jeck5iv/PersonalLLM-LoRA-Style-Adaptation) is documented separately.
