# THULAC Tutorial: An efficient Chinese lexical analysis toolkit

## Software Description

THULAC (THU Lexical Analyzer for Chinese) is a set of Chinese lexical analysis toolkit developed by the Natural Language Processing and Social Humanity Computing Laboratory of Tsinghua University, with Chinese word segmentation and part-of-speech tagging functions. It has strong reliability and accuracy as well as high speed. THULAC has the following characteristics:

1. **Strong Ability**. It is trained using the integrated world's largest artificial word segmentation and part-of-speech tagging Chinese corpus (containing about 58 million chinese characters), and the model has strong tagging capabilities.

2. **High Accuracy**. The accuracy rate is high. The F1 value of word segmentation of this toolkit on the standard data set Chinese Treebank (CTB5) can reach 97.3%, and the F1 value of part-of-speech tagging can reach 92.9%, which is equivalent to the best method on this data set.

3. **Fast Processing Speed**. The speed is faster. The speed of simultaneous word segmentation and part-of-speech tagging is 300KB/s, and it can process about 150,000 words per second. Only the word segmentation speed can reach 1.3MB/s.


## Compile and install

1. **C++ version**
- Run under current path
- make
- Will get thulac and train_c in the current directory
(Thulac needs the support of the model, and the downloaded model needs to be placed in the current directory)

2. **Java version**
- Run the executable jar package directly according to the word segmentation program command format
- To compile by yourself, you need to install Gradle, and then execute gradle build in the project root directory, and the generated files are under build/libs
(Thulac needs the support of the model, and the downloaded model needs to be placed in the current directory)

3. **Python version** (compatible with python2.x and python3.x)
- *Source code download:* \
    Put the thulac file in the directory and reference it by `import thulac` \
(Thulac needs the support of the model, and the downloaded model needs to be placed in the thulac directory.)

- *pip download* \
    `sudo pip install thulac`\
Reference by `import thulac`


## How to use
1. **Word segmentation and part-of-speech (POS) tagging**
- 1.1 **Command format**
    - C++ version (refer to 1.5 for interface call)
        - `./thulac [-t2s] [-seg_only] [-deli delimeter] [-user userword.txt]` Input and output from the command line
        - `./thulac [-t2s] [-seg_only] [-deli delimeter] [-user userword.txt]` outputfile Use redirection to input and output from text files (note that all are UTF8 text) \
    - Java version
        - `java -jar THULAC_lite_java_run.jar [-t2s] [-seg_only] [-deli delimeter] [-user userword.txt]` Input and output from the command line
        - `java -jar THULAC_lite_java_run.jar [-t2s] [-seg_only] [-deli delimeter] [-user userword.txt] -input input_file -output output_file` Input and output from a text file (note that all are UTF8 text)
    - Python version (compatible with python2.x and python3.x)\
    Through the python program `import thulac`, create a new class `thulac.thulac(args)`, where `args` are the parameters of the program. After that, single sentence segmentation can be performed by calling `thulac.cut()`. Detail interface params check 1.4. 

    **Code Examples 1:**
    ```
    import thulac   

    thu1 = thulac.thulac()  # default mode
    text = thu1.cut("我想去成都吃火锅", text=True)  # one sentence segmentation
    print(text)
    ``` 

    **Output:**
    ```
    Model loaded succeed
    我_r 想_v 去_v 成都_ns 吃_v 火锅_n
    ```

    **Code Examples 2:**
    ```
    import thulac   

    thu1 = thulac.thulac()  # default mode
    fall = "不逢北国之秋，已将近十余年了。在南方每年到了秋天，总要想起陶然亭的芦花，钓鱼台的柳影，西山的虫唱，玉泉的夜月，潭柘寺的钟声。在北平即使不出门去罢，就是在皇城人海之中，租人家一椽破屋来住着，早晨起来，泡一碗浓茶、向院子一坐，你也能看得到很高很高的碧绿的天色，听得到青天下驯鸽的飞声。从槐树叶底，朝东细数着一丝一丝漏下来的日光，或在破壁腰中，静对着象喇叭似的牵牛花（朝荣）的蓝朵，自然而然地也能够感觉到十分的秋意。说到了牵牛花，我以为以蓝色或白色者为佳，紫黑色次之，淡红色最下。最好，还要在牵牛花底，教长着几根疏疏落落的尖细且长的秋草，使作陪衬。"
text = thu1.cut(fall, text=True)  # one sentence segmentation
print(text)
    ``` 

    **Output:**
    ```
    不_d 逢_v 北国_s 之_u 秋_g ，_w 已_d 将近_d 十_m 余_m 年_q 了_u 。_w 在_p 南方_s 每年_r 到_v 了_u 秋天_t ，_w 总_d 要_v 想起_v 陶然亭_ns 的_u 芦花_n ，_w 钓鱼台_ns 的_u 柳影_n ，_w 西山_ns 的_u 虫_n 唱_v ，_w 玉泉_ns 的_u 夜月_t ，_w 潭柘寺_ns 的_u 钟声_n 。_w 在_p 北平_ns 即使_c 不_d 出门_v 去_v 罢_v ，_w 就_d 是_v 在_p 皇城_ns 人海_n 之中_f ，_w 租_v 人_n 家_n 一_d 椽_v 破_a 屋_n 来_v 住_v 着_u ，_w 早晨_t 起_f 来_v ，_w 泡_v 一_m 碗_q 浓茶_n 、_w 向_p 院子_n 一_d 坐_v ，_w 你_r 也_d 能_v 看_v 得到_v 很_d 高_a 很_d 高_a 的_u 碧绿_a 的_u 天色_n ，_w 听_v 得_u 到_v 青_a 天下_n 驯鸽_n 的_u 飞声_n 。_w 从_p 槐树_n 叶底_v ，_w 朝_p 东细_s 数_v 着_u 一丝一_m 丝_q 漏_v 下_v 来_v 的_u 日光_n ，_w 或_c 在_p 破壁腰_n 中_f ，_w 静_a 对_v 着_u 象_g 喇叭_n 似_g 的_u 牵牛花_n （_w 朝荣_np ）_w 的_u 蓝朵_n ，_w 自然而然_id 地_u 也_d 能够_v 感觉_v 到_v 十分_m 的_u 秋意_n 。_w 说_v 到_v 了_u 牵_v 牛_n 花_n ，_w 我_r 以为_v 以_p 蓝色_n 或_c 白色者_n 为_v 佳_a ，_w 紫黑色_n 次_g 之_r ，_w 淡红色_n 最_d 下_v 。_w 最_d 好_a ，_w 还要_v 在_p 牵_v 牛_n 花_n 底_f ，_w 教_v 长_v 着_u 几_m 根_q 疏疏落落_a 的_u 尖细_a 且_c 长_a 的_u 秋草_n ，_w 使_v 作_v 陪衬_n 。_w
    ```

    **Code Examples 3:**
    ```
    thu1 = thulac.thulac(seg_only=True)  # Only perform sentence segmentation, no POS tag
    thu1.cut_f("input.txt", "output.txt")  # segmentation of 'input.txt'，output to 'output.txt'
    ```

- 1.2 **Common parameters (C++ version, Java version)**
    - *t2s*------------------Convert the sentence from traditional to simplified
    - *seg_only*-------------only word segmentation, no part-of-speech tagging
    - *deli delimeter*-------Set the separator between words and parts of speech, the default is underscore_
    - *filter*---------------Use a filter to remove some meaningless words, such as "can"
    - *user userword.txt*----Set the user dictionary, the words in the user dictionary will be marked with uw label. Each word in the dictionary is encoded in UTF8 (not available in the python version)
    - *model_dir dir*--------Set the folder where the model file is located, the default is models

- 1.3 **Java version specific parameters**
    - *input input_file*-----Set to read from the file, the default is the command line input
    - *output output_file*---Set the output to the file, the default is the command line output

- 1.4 **Python version interface parameters**
	- *user_path*------------Set the user dictionary, the words in the user dictionary will be marked with uw label. Each word in the dictionary, one line, UTF8 encoding
	- *t2s*------------------default False, whether to convert the sentence from traditional to simplified
	- *just_seg*-------------default is False, when only word segmentation is performed, no part-of-speech tagging
	- *ufilter*--------------default False, whether to use the filter to remove some meaningless words, such as `can`
	- *model_path*-----------Set the folder where the model file is located, the default is models
	- *separator*------------The default is `_`, set the separator between words and parts of speech

- 1.5 **C++ version interface parameters (need to include `include/thulac.h`)**\
- First, you need to instantiate the THULAC class, and then you can call the following interface:
```
int init(const char* model_path = NULL, const char* user_path = NULL, int just_seg = 0, int t2s = 0, int ufilter = 0, char separator ='_');
``` 
- Initialize the program, make custom settings
	- *user_path*------------Set the user dictionary, the words in the user dictionary will be marked with uw label. Each word in the dictionary, one line, UTF8 encoding
	- *t2s*------------------default False, whether to convert the sentence from traditional to simplified
	- *just_seg*-------------default is False, when only word segmentation is performed, no part-of-speech tagging
	- *ufilter*--------------The default is False, whether to use the filter to remove some meaningless words, such as `can`.
	- *model_path*-----------Set the folder where the model file is located, the default is models
	- *separator*------------The default is`_`, set the separator between words and parts of speech

- 1.6 **Use of word segmentation and part-of-speech tagging models** \
THULAC needs the support of word segmentation and part-of-speech tagging models. Users can download them from the download list `THULAC模型 Models_v1.zip` and put them in the root directory of THULAC, or use parameters `-model_dir dir` to specify the location of the model.

2. **Model training**\
The THULAC toolkit provides a model training program `train_c`, and users can use `train_c` to train and obtain the required model of THULAC.
- 2.1 **Command format**
	- ```./train_c [-s separator] [-b bigram_threshold] [-i iteration] training_filename model_filename```
	- Use `training_filename` as the training set, and the trained model name is `model_filename`
- 2.2 **Parameters**
	- `-s` sets the separator between words and parts of speech, the default is slash `/`
	- `-b` sets the threshold of the two-character string, the default is 1
	- `-i` sets the number of training iterations, the default is 15
- 2.3 **Training set format**\
- We use the default separator (slash `/`) as an example with sentences have been tagged with parts of speech, the training set content should be similar as:
```
我/r 爱/vm 北京/ns 天安门/ns
```
- To train a word segmentation model, use the default separator (slash `/`) as an example, and the training set content should be similar as
```
我/ 爱/ 北京/ 天安门/
```
- 2.4 **Use the trained model**\
Overwrite the trained model with the corresponding model in the original models, and then execute the word segmentation program to use the trained model.



## Performance comparison with representative word segmentation software
- We choose [LTP-3.2.0](https://github.com/HIT-SCIR/ltp), [ICTCLAS (2015 version)](http://ictclas.nlpir.org/index_e.html), [jieba (C++ version)](https://github.com/yanyiwu/cppjieba) and other Chinese representative word segmentation software packages for performance comparison with THULAC. We chose Windows as the test environment, and tested the speed and accuracy of different software according to the international Chinese word segmentation evaluation standards published by The Second International Chinese Word Segmentation Bakeoff.
- In the second international Chinese word segmentation test, a total of four units provided test corpus (Academia Sinica, City University, Peking University, Microsoft Research), and the resource [icwb2-data](http://sighan.cs.uchicago.edu/bakeoff2005/) provided by the evaluation included training from these four training set (training), test set (testing), and the standard answer (`icwb2-data/scripts/gold`) of the corresponding test set provided according to the respective word segmentation standards. The `icwb2-data/scripts` directory contains perl script score for automatic scoring of word segmentation.
- We tested the above popular word segmentation software and THULAC in a unified test environment, and the model used was the model that comes with each word segmentation software. THULAC uses the simple model `Model_1` provided with the software. The evaluation environment is `Intel Core i5 2.4 GHz`. The evaluation results are as follows:

	- msr_test (560KB)

| Algorithm     | Time  | Precision | Recall | F-Measure |
| ------------- |:-----:| ---------:| ------:| ---------:|
| LTP-3.2.0	    |3.21s  |  	0.867   | 0.896	 | 0.881     |
|ICTCLAS(2015版)|0.55s	|0.869	    |0.914	 |0.891      |
|jieba(C++版)	|0.26s	|0.814	    |0.809	 | 0.811     |
|THULAC_lite	|0.62s	| 0.877	    | 0.899	 |0.888      |


-
	- pku_test（510KB）	

| Algorithm     | Time  | Precision | Recall | F-Measure |
| ------------- |:-----:| ---------:| ------:| ---------:|
|LTP-3.2.0	    |3.83s	|0.960	    |0.947	 |0.953      |
|ICTCLAS(2015版)	|0.53s	|0.939	    |0.944	 |0.941      |
|jieba(C++版)	|0.23s	|0.850	    |0.784	 |0.816      |
|THULAC_lite	|0.51s	|0.944	    |0.908	 |0.926      |

- In addition to the above evaluation on the standard test set, we also evaluated the speed of each word segmentation tool on big data. The results are as follows:
	- CNKI_journal.txt (51 MB)

| Algorithm     | Time    | Speed      | 
| ------------- |:-------:| ----------:| 
|LTP-3.2.0	    |348.624s |	149.80KB/s |
|ICTCLAS(2015版)	|106.461s |	490.59KB/s |
|jieba(C++版)	|22.558s  |	2314.89KB/s|
|THULAC_lite    |42.625s  |	1221.05KB/s|


## Part-of-speech tag set
1. Universal mark set (applicable to all versions)
```
n/noun 
np/person's_name 
ns/place_name 
ni/organization_name 
nz/other_proper_name
m/numeral 
q/quantifier 
mq/quantifier 
t/time_word 
f/direction_word 
s/location_word
v/verb 
a/adjective 
d/adverb 
h/preceded_by_component 
k/followed_by_component 
i/idiom
j/abbreviation 
r/pronoun 
c/conjunction 
p/preposition 
u/particle 
y/modal_particle
e/interjection 
o/onomatopoeia 
g/morphemes 
w/punctuation 
x/others
```

2. Special mark set (applicable to lite_v1_2 version)
- In order to facilitate the filtering after word segmentation and part-of-speech tagging, in the `v1_2` version, we have added two parts of speech, which can be downloaded and used if necessary.
```
vm/can_wish_verb
vd/directive_verb
```

## Different configurations of THULAC
1. We have attached a simple word segmentation model `Model_1` with the THULAC source code, which only supports word segmentation. The model was trained by the People's Daily sub-word corpus.
2. We have attached the combined word segmentation and part-of-speech tagging model `Model_2` with the THULAC source code, which supports simultaneous word segmentation and part-of-speech tagging. The model is trained by the People's Daily word segmentation and part-of-speech tagging corpus.
3. We also provide more complex, complete and accurate word segmentation and part-of-speech tagging joint model `Model_3` and `word segmentation vocabulary`. The model is obtained by joint training and training of multiple corpora (the corpus includes annotated text from multiple styles and annotated text from People's Daily, etc.). Due to the large model, if there is a need for institutions or individuals, please fill in the [resource application form.doc](http://thulac.thunlp.org/source/shenqingbiao.docx) and send it to *thunlp@gmail.com* for approval, we will send the relevant resources to the contact.

## Get the link
- The THULAC toolkit is divided into two parts. The first part is the algorithm source code part, which can be download from Github without registration; the second part is the algorithm model part. THULAC needs the support of word segmentation and part-of-speech tagging model, which can be obtained Algorithm Model after registration.

1. Algorithm source code lite version
- [THULAC_lite](http://thulac.thunlp.org/message_v1_1)
	- THULAC_lite word segmentation source code (C++ version)	
	- THULAC_lite word segmentation source code (python version)	
	- THULAC_lite word segmentation source code (java version)	
	- THULAC_lite word segmentation java version executable jar package	
	- THULAC model, including word segmentation model and part-of-speech tagging model (lite version)

2. Algorithm source code lite version (github)

- THULAC_lite_C++: THULAC_lite word segmentation source code (C++ version) [link](https://github.com/thunlp/THULAC)
- THULAC_lite_Python:	THULAC_lite word segmentation source code (python version) [link](https://github.com/thunlp/THULAC-Python)	 
- THULAC_lite_Java: THULAC_lite word segmentation source code (java version) [link](https://github.com/thunlp/THULAC-Java)
- THULAC_lite.So: THULAC_lite word segmentation source code (So version) [link](https://github.com/thunlp/THULAC.So)

3. Algorithm model

- THULAC_lite_Model: THULAC model, including word segmentation model and part-of-speech tagging model (lite version) [link](http://thulac.thunlp.org/message_v1_1)
- THULAC pro v1.zip (C++): THULAC model, including more complex and complete word segmentation and part-of-speech tagging models and word segmentation vocabulary [link](http://thulac.thunlp.org/register)
 

## Precautions
- The tool currently only handles UTF8 encoded Chinese text, and will gradually increase the support for other encoding functions, so stay tuned.

## History

| Update time     | update content                                                | 
| --------------- |:-------------------------------------------------------------:| 
|2017-01-17	      |Publish the python version of THULAC word segmentation on pip. |
|2016-10-10	      |Add the so version of THULAC word segmentation.                |
|2016-03-31	      |Increase the python version of THULAC word segmentation.       |
|2016-01-20	      |Increase the Java version of THULAC word segmentation.         |
|2016-01-10	      |Open source THULAC word segmentation tool C++ version.         |

## Open source agreement
1. THULAC is a free and open source code for domestic and foreign universities, research institutes, enterprises and individuals for research purposes.
2. If any organization or individual intends to use THULAC for commercial purposes, please send an email to thunlp@gmail.com to discuss the technology license agreement.
3. Any valuable comments and suggestions on this toolkit are welcome. Please send an email to thunlp@gmail.com.
4. If you publish a paper or obtain scientific research results on the basis of THULAC, please declare that "Tsinghua University THULAC is used" when publishing the paper and applying for the results, and cite it in the following format:
- *Maosong Sun, Xinxiong Chen, Kaixu Zhang, Zhipeng Guo, Zhiyuan Liu. THULAC: An Efficient Lexical Analyzer for Chinese. 2016.*