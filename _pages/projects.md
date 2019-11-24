---
permalink: /about/
title: "Projects"
author_profile: true
---


## [mkdataset](https://github.com/hemanth346/mkdataset)

Command line utility to create image datasets from webcam feed or from Video files.

Description : https://pypi.org/project/mkdataset/


#### Usage

---

```
$$ saveimg --help
Usage: saveimg [OPTIONS] NAME

  Capture frame from video feed at set intervals and save them as an
  organized dataset with  images in training, test and validation folders

  Currently supports only for one class name

Options:
  -d, --directory PATH            Directory where images has to be saved,
                                  expects path not string
  -v, --video FILENAME            Video file to parse, default is webCam feed
  -s, --fps INTEGER               Capture rate in seconds per Frame
  -p, --distribution <FLOAT FLOAT FLOAT>...
                                  Distribution of train, test and valid images
                                  to be saved
  -c, --cont BOOLEAN              If train, test and validation images should
                                  have continuity in naming
  -r, --reverse BOOLEAN           If train, test and validation should be
                                  inside class folder unlike class folder
                                  inside these
  --help                          Show this message and exit.

$$
```



# Ongoing Work

## [mkmlproject](https://github.com/hemanth346/mkmlproject)

Command-line utility that creates ML project structure for creating and sharing data science work. Also provides ability to generate pipeline notebooks from predefined templates.

Description : https://github.com/hemanth346/mkmlproject


#### Usage

```
import mkmlproject
mkmlproject create -d 'home_dir' 'Project Name'
mkmlproject render -t 'Template File' -o 'Output Notebook' -d 'Output Location'
mkmlproject config # change default project dir structure and details
```
