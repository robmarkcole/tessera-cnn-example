See https://toao.com/blog/earth-observation-budget-solar-farms-tiny-model for an explanation of this codebase

This project uses [uv](https://github.com/astral-sh/uv)

## Running this project

First you will want to download the OSM solar farm UK data and prepare the tiles:

```
uv run prepare.py --download
```

then training (assumes a GPU)

```
uv run train.py
```

finally evaluate

```
uv run evaluate.py
```
