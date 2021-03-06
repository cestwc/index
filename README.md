# index-for-datasets-and-models

Here are a few datasets prepared to be imported into Torchtext. You may find the datasets useful, but probably not. There are also various pretrained models, with different training strategy. The models may even have different architecture. We will not put more information here, since we haven't figured out which model works best.

Certainly, you are confused. Just contact me if you'd like to know more about what's happening here!

## Usage
Supposed you'd like to download a model and a pair of datasets into your current working path
```python
from puller import pull
pull('replace-3-test.json', 'replace-3-train.json', 'nlg-3-5.pt')
```

You are going to get errors for sure if trying to pull a file that is not listed in this index.

We have put two versions in the python file, where the [gdown](https://pypi.org/project/gdown/) version does not work very well for files larger than 100 MB. Thus, we took python code in this stackoverflow [answer](https://stackoverflow.com/questions/25010369/wget-curl-large-file-from-google-drive/39225039#39225039) and use it to replace gdown.

The difference is that the gdown version uses a special url to download files, while the other uses the id of each file.

by the way, you may want to split a dataset into 'train', 'valid' and 'test' like this
```python
from util_dataset import split

train_file, valid_file, test_file = split('fakenewsnet_sm.json', seed = 79, sets = ['train', 'valid', 'test'])
```

or concatenate two or more datasets into one like this
```python
concatenate(train_file, 'some-leverage-dataset.json', destiny = train_file, seed = 79)
```

do remember to shuffle your dataset in the ```iterator```s, as texts from different datasets may have quite different lengths.
