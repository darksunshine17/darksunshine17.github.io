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
1. Word segmentation and part-of-speech (POS) tagging \
  1.1 Command format
    - C++ version (refer to 1.5 for interface call)
        - `./thulac [-t2s] [-seg_only] [-deli delimeter] [-user userword.txt]` Input and output from the command line
        - `./thulac [-t2s] [-seg_only] [-deli delimeter] [-user userword.txt]` outputfile Use redirection to input and output from text files (note that all are UTF8 text) \\
    - Java version
        - `java -jar THULAC_lite_java_run.jar [-t2s] [-seg_only] [-deli delimeter] [-user userword.txt]` Input and output from the command line
        - `java -jar THULAC_lite_java_run.jar [-t2s] [-seg_only] [-deli delimeter] [-user userword.txt] -input input_file -output output_file` Input and output from a text file (note that all are UTF8 text)
    - Python version (compatible with python2.x and python3.x)\
    Through the python program `import thulac`, create a new class `thulac.thulac(args)`, where `args` are the parameters of the program. After that, single sentence segmentation can be performed by calling `thulac.cut()`. Detail interface params check 1.4. \\

    Python code examples:\
    ```
    import thulac   

    thu1 = thulac.thulac()  # default mode
    text = thu1.cut("我想去成都吃火锅", text=True)  # one sentence segmentation
    print(text)
    ``` 

    Output:\
    ```
    Model loaded succeed
    我_r 想_v 去_v 成都_ns 吃_v 火锅_n
    ```





## Performance comparison with representative word segmentation software
## Part-of-speech tag set
## Different configurations of THULAC
## Get the link
## Precautions
## History

