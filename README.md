## Introduction
An effective lexical analysis platform by DUT-NLP Lab. The code is easy to use.

DUT-Nihao is an open-source toolkit for Chinese lexical analyzer developed by the Natural Language Processing Lab at Dalian University of Technology.

## Demo

We will update this module in the future. (The domain name has not been set.)

## Requirement

For the current release of DUT-Nihao, the requirement of code is limited. We will revise the code to support other versions of pip-packages in the future. If you have any questions, please contact [us](#jumpcontact).

```shell
python:3.5.0 # A higher version is available (e.g., 3.7.0)
pyTorch:1.2.0 # A higher version is available (e.g., 1.4.0;1.7.0)
pytorch_pretrained_bert:0.6.2 # A higher version is available 
```

Due to the size of the pre-trained model (PTM), it must be downloaded by yourself.

The [link](https://github.com/ymcui/Chinese-BERT-wwm) is available, and please choose the `pytorch` version. Note that the PTM is unofficial and you can use it freely. You need cite the work that the [github](https://github.com/ymcui/Chinese-BERT-wwm) introduced. For convince, we are willing to open the PTM by ourselves. If you're also interested in PTM, please contact me ([kaiyuhuang@mail.dlut.edu.cn](mailto:kaiyuhuang@mail.dlut.edu.cn)).

## Workflow

> DUT-Nihao supports single-criterion and multiple-criteria Chinese word segmentation. Due to the specific adaptation, there is a little difference between `single` and `multiple` module. And all files must be **utf-8** code. 
> > - Input format:
> >
> >   Each word is split with a blank character (you can check the format in `data/example/single-train.utf8`).
> >
> >   大连 理工 大学 坐落 于 美丽 的 大连 。
> >
> >   Each word is split with a blank character and a specific tag is added at the beginning of each sentence. (you can check the format in `data/example/multiple-train.utf8`).
> >
> >   pku<@@>大连 理工 大学 坐落 于 美丽 的 大连 。
> >   
> >   msr<@@>大连理工大学 坐落 于 美丽 的 大连 。
> >   
> >   The **dev and test** data have **non-blank** characters, which is different from the format of training data.
> >   
> >   e.g. (you can check the format in `data/example/single-test.utf8` and `data/example/multiple-test.utf8`).
> >   
> >   single: 大连理工大学坐落于美丽的大连。
> >   
> >   multiple: pku<@@>大连理工大学坐落于美丽的大连。
> >   
> >   For convenience, we supply a script for processing the Input file (e.g., whole width to half width, characters generalization). It can convert the sentence into specific format. The script is easy to use without any pip-packages.
> >   
> >   > ```shell
> >   > # convert train data to half-width and generalization format
> >   > python utils.py -f p-train -i input_file -o output_file 
> >   > 
> >   > # convert dev/test data to half-width and generalization format
> >   > python utils.py -f p-test -i input_file -o output_file 
> >   > 
> >   > # add specific tag (e.g., pku,msr,ctb...) into train/dev/test data
> >   > python utils.py -f add-tag -c tag_name -i input_file -o output_file 
> >   > ```
> >   >
> 
>
>> - For training and testing, use the command line `python main.py -c config`. Training and testing details will be printed on the screen. `config` is the configuration of DUT-Nihao. All settings are in the configuration file. The meaning of each parameter is introduced in brief.
> >
> >   > ```shell
> >   > # is the annotation character
> >   > mode = (train/multi-train/test/multi-test)
> >   > load_file = (the path of training or testing file)
> >   > ...
> >   > ```
> >   > 
> > - For post-editing, if you convert your personal file into specific format, we will also supply an auto post-editing code for recovering the half-width and generalization. The `original_file` (example/test.data) represents the original dev/test data.
> >
> >   > ```shell
> >   > python utils.py -f post -io original_file -i segmentation_file -o output_file
> >   > ```
> >   > 

## License

The source code is dual licensed. Open source licensing is under the [BSD-3-Clause](https://opensource.org/licenses/BSD-3-Clause), which allows free use for research purposes. For commercial licensing, please email [kaiyuhuang@mail.dlut.edu.cn](mailto:kaiyuhuang@mail.dlut.edu.cn).

## Citation

Please cite the following paper:

> Kaiyu Huang, Degen Huang, Zhuang Liu, Fengran Mo. [A Joint Multiple Criteria Model in Transfer Learning for Cross-domain Chinese Word Segmentation](https://www.aclweb.org/anthology/2020.emnlp-main.318/). EMNLP 2020.

## Development Team

Project leaders: [Degen Huang](http://faculty.dlut.edu.cn/dlut_nlp/zh_CN/index.htm)

Project members:

Chinese word segmentation: Kaiyu Huang, Hao Yu, Wei Liu, Meng Sun

Machine Translation: Junpeng Liu, Yiming Zhang, Huan Liu


## Contact

<span id='jumpcontact'>Contact us</span>. If you have questions, suggestions and bug reports, please email [kaiyuhuang@mail.dlut.edu.cn](mailto:kaiyuhuang@mail.dlut.edu.cn) or the email of each project member.

## Logs

It is the first release of DUT-Nihao with only Chinese word segmentation module (update on Dec. 2020)