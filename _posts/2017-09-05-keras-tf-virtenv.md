---
layout: post
title: Create Keras-TF virtual environment
---

When Keras 2.0 came out, I didn't want to upgrade because I had ongoing projects in the original Keras that were incompatible with the new version. So I got in the habit of creating a new Python [virtenv](https://virtualenv.pypa.io/en/stable/userguide/) for every new project and wrote a small script to do this fast. Since it has proven useful to some of my colleagues I am also sharing it here.

```bash
#!/bin/bash

echo "Please specify the /path/and/name for the virtualenv (example: ~/env): "

read virtenvpath

printf 'Your selected path is %s\n' $virtenvpath

eval cd "$(dirname $virtenvpath)"
virtualenv $(basename $virtenvpath)

source $(basename $virtenvpath)/bin/activate

printf "\n and now upgrading\n"
pip install --upgrade pip

printf "\n and now installing numpy, scipy, keras and tensorflow (and their dependencies)"
pip install scipy matplotlib keras tensorflow-gpu Pillow
pip list
```

Notes:
1. Pillow is needed for scipy to work properly and for some reason it is not installed as a dependency with scipy, as numpy does for example.
2. If you don't have keras and tensorflow already installed in your computer you must then make sure that the `~/.keras/keras.json` file exists and that `image_dim_ordering` is set to `tf` or `channels_last` and `backend` is set to `tensorflow`. If you have another version of Keras installed that is older than 2.0, then set `image_dim_ordering` to `tf`. This works with both versions while `channels_last` and `channels_first` only work with Keras 2.

Here is an example of the `~/.keras/keras.json` file for reference:

```
{
    "image_dim_ordering": "tf", 
    "epsilon": 1e-07, 
    "floatx": "float32", 
    "backend": "tensorflow"
}
```



