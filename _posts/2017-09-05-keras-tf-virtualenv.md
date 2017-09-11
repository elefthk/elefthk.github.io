---
layout: post
title: Keras-TF virtual environment
---

<figure><img src="/images/keras-logo.png" alt="keras_logo" style="width: 70px;"/></figure>
When Keras 2.0 came out, I didn't want to upgrade the whole system because my main project at the time was in Keras 1.2 and incompatible with the new version. So I got in the habit of creating a new Python [virtualenv](https://virtualenv.pypa.io/en/stable/userguide/) for every new project and wrote a small script to do this fast. Since it has recently proven useful to some of my colleagues, I am also sharing it here.

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

printf "\n and now installing numpy, scipy, matplotlib, keras, tensorflow and h5py (for storing model weights) and their requirements"
pip install scipy matplotlib keras tensorflow-gpu Pillow h5py
pip list
```

Notes:
1. Pillow is needed for scipy to work properly and for some reason it is a requirement for scipy, as numpy for example.
2. If you don't have keras and tensorflow already installed in your computer you must then make sure that the ~/.keras/keras.json file exists and that "image_dim_ordering" is set to "tf" or "channels_last" and "backend" is set to "tensorflow". If you have another version of Keras installed that is older than 2.0, then set "image_dim_ordering" to "tf". This works with both versions while "channels_last" and "channels_first" only work with Keras 2.

Here is an example of the ~/.keras/keras.json file for reference:

```
{
    "image_dim_ordering": "tf", 
    "epsilon": 1e-07, 
    "floatx": "float32", 
    "backend": "tensorflow"
}
```



