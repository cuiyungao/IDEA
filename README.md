# IDEA
Release code and data for the ICSE'18 paper: Online App Review Analysis for Identifying Emerging Issues. IDEA (IDentifying Emerging issues from App reviews) is a framework for detecting emerging issues from time-sensitive data.

The highlights of the framework lie in the online topic modeling, which considers the previous topic distributions explicitly and improves [OLDA](http://ieeexplore.ieee.org/document/4781095/), and topic labeling, which automatically interprets each topic with the most relevant phrases and sentences. More details can be referred to the following paper:

> Cuiyun Gao, Jichuan Zeng, Michael Lyu, Irwin King, and Weiwen Qiu. Online App Review Analysis for Identifying Emerging Issues. ICSE 2018.


## Data Format
Input raw reviews should be saved as the following format per line. The attributes are separated by `******`, and only the first five attributes are necessary. The number of attributes should be claimed in the variable `InfoNum` under the `[Info]` section. Here, `InfoNum=6`.

```
rating******review text******title******date******version******nation
```

## Usage
1. Download necessary nltk packages with:

```
$ python
>> import nlkt
>> nltk.download('averaged_perceptron_tagger')
>> nltk.download('stopwords')
```

2. **Notice:** If this is the first time to use IDEA in your computer, you need to compile pyx and c. Also make sure `_lda.c` and `_lda.so` have been deleted before running the command. Under the `src` folder, run:

```
$ python build_pyx.py build_ext --inplace
```

3. Finally, run the main program. This may take several minutes.

```
$ python main.py
```

You can modify the parameters for the inputs and outputs in the `config.ini` file easily.

## Visualization
1. The source code for visualization is under the folder `visualization`. To prepare the input for visualize, we firstrun

```
$ python get_input <result_folder> <K>
result_folder     the output dir of IDEA, should contain apk name, e.g., '../result/youtube/'
K     the number of topics
```

2. Use localhost server to display the topic river. For Python 2, run `$ python -m SimpleHTTPServer 7778`, while for Python 3, run `python -m http.server 7778`. `7778` is the port number for viewing the visualization, e.g., for localhost, here we type `localhost:7778` in the browser.

**For Linux or Mac:**, can simply run:

```
$ bash visualize.sh <result_folder> <K>
```

## Validation
1. Download the word2vec model trained on 4 millions app reviews from this [link](https://www.dropbox.com/s/et4n6sj3k94ku2s/wv.zip?dl=0), and unzip the directory in the `model` folder.

2. Uncomment the code of line 486 in `main.py`, and run the script.

```
$ python main.py
```

## Related Link
* [Paper website], you can see more details about the experiments.

## History