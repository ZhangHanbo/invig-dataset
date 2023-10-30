
# News

**NEWS!** We have released a new version of InViG dataset including 500K automatically generated human-robot dialogues including a comprehensive suite of benchmark performance: [InViG 500K](https://openivg.github.io), [Paper](https://arxiv.org/abs/2310.12147).

# InViG Dataset

InViG Dataset is a dataset, namely InViG, to step towards end-to-end interactive disambiguation. 

## Citation.   
If you find this dataset useful, please cite:

```latex
@misc{invigdataset,
    title={InViG: Interactive Visual-Language Disambiguation with 21K Human-to-Human Dialogues},
    author={Zhang, Hanbo and Mo, Yuchen and Xu, Jie and Si, Qingyi and Kong, Tao},
    howpublished = {\url{https://github.com/ZhangHanbo/invig-dataset}},
    year={2023}
}
```

## Intro

As is notoriously known, interaction based on natural language is usually ambiguous, making goal-oriented interactive tasks hard for robots to solve. Therefore, we collect 20K human-to-human disambiguation dialogues based on the images filtered from OpenImages. 

## Download

- InViG dataset can be accessed from [🤗jxu124/invig](https://huggingface.co/datasets/jxu124/invig).

    ```
    import datasets
    ds = datasets.load_datasets("jxu124/invig")
    ```

- Images (OpenImages datasets) can be accessed from [here](https://storage.googleapis.com/openimages/web/index.html). 

- A list of image IDs (a filename list) used in the InViG dataset can be obtained through this python scripts

    ```
    import os
    import datasets

    ds = datasets.load_datasets("jxu124/invig")
    file_list = [os.path.basename(i)
        for split in ['train', 'test', 'validation']
            for i in ds[split]['image_path']
    ]
    ```

## Benchmark

### End-to-End Evaluation

(AP@0.99)

|Oracle |Guesser |Questioner |Success Rate|
|-|-|-|-|
|XVLM-Oracle|Vilbert-Guesser|Vilbert-Questioner|35.3%|
|XVLM-Oracle| XVLM-Guesser| XVLM-Questioner| 40.1%|

### Guesser Evaluation

(AP@0.99) Guesser accuracy on ground-truth dialogs

|Guesser Methods| Accuracy|
|-|-|
|Vilbert-Guesser| 55.1%|
|XVLM-Guesser| 59.7%|

### Examples

|Image|Dialogue|对话|
|-|-|-|
|![](./imgs/image.jpg)|"Please pass me that little toy.<br>OK, which one do you want?<br>One of the small boxes in the front.<br>OK, so there are three, which one is it?<br>The purple one.<br>The one on the left?<br>Yes, there is a pearl on it.<br>|请把那个小玩具递给我一下。<br>好的，想要哪个呢？<br>前边的那个小盒里装的其中一个。<br>好的，那有三个呢，是哪个？<br>紫色那个。<br>左边那个？<br>是的，上边有颗珍珠。<br>|
|![](./imgs/image2.jpg)|Can you get me a bottle?<br>Which one do you need?<br>The Coke bottle on the right.<br>Is it a greenish bottle?<br>Yes, it's shorter.<br>OK, here you are.<br>Thank you.<br>|帮我拿一个瓶子可以吗？<br>你需要哪一个？<br>右边的那个可乐瓶。<br>是泛绿色的瓶子吗？<br>是的，它比较矮。<br>好的，给你。<br>谢谢。<br>|
|![](./imgs/image3.jpg)|There are many keyboards here, all kinds.<br>Yes, maybe the functions are different.<br>Yes, there are big and small ones.<br>Which one do you want?<br>A smaller one, easy to carry.<br>Then you choose one.<br>The one in the lower left corner, the space bar it's long is yellow.<br>|这里有许多键盘，各式各样的。<br>是的，可能功能都不一样。<br>是的，有大有小。<br>想要哪个呢？<br>小点的吧，便于携带。<br>那你挑一个。<br>左下角那个吧，它长的那个空格键是黄色的。<br>|

