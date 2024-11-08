<a href="http://hinteval.readthedocs.io/"><img src="https://img.shields.io/static/v1?label=Documentation&message=HintEval&color=20BEFF&logo=Read the Docs"></a>
<a href=""><img src="https://img.shields.io/static/v1?label=Paper&message=ArXiv&color=green&logo=arXiv"></a>
<a href="https://opensource.org/license/apache-2-0"><img src="https://img.shields.io/static/v1?label=License&message=Apache-2.0&color=red"></a>

**HintEval** is a powerful framework designed for both generating and evaluating hints. These hints serve as subtle clues, guiding users toward the correct answer without directly revealing it. As the first tool of its kind, HintEval allows users to create and assess hints from various perspectives.

## 🖥️ Installation

It's recommended to install HintEval in a [virtual environment](https://docs.python.org/3/library/venv.html) using [Python 3.11.9](https://www.python.org/downloads/release/python-3119/). If you're not familiar with Python virtual environments, check out this [user guide](https://packaging.python.org/guides/installing-using-pip-and-virtual-environments/). Alternatively, you can create a new environment using [Conda](https://anaconda.org/anaconda/conda).

### Set up the virtual environment

First, create and activate a virtual environment with Python 3.11.9:

```bash
conda create -n hinteval_env python=3.11.9 --no-default-packages
conda activate hinteval_env
```

### Install PyTorch 2.4.0

You'll need PyTorch 2.4.0 for HintEval. Refer to the [PyTorch installation page](https://pytorch.org/get-started/previous-versions/) for platform-specific installation commands. If you have access to GPUs, it's recommended to install the CUDA version of PyTorch, as many of the evaluation metrics are optimized for GPU use.

### Install HintEval

Once PyTorch 2.4.0 is installed, you can install HintEval via pip:

```bash
pip install hinteval
```

For the latest features, you can install the most recent version from the main branch:

```bash
pip install git+https://github.com/DataScienceUIBK/HintEval
```

## 🏃 Quickstart

This is a small example program you can run to see hinteval in action!

```python
from hinteval.cores import Instance, Question, Hint, Answer
from hinteval.evaluation.convergence import LlmBased

llm = LlmBased(model_name='llama-3-70b', together_ai_api_key='your_api_key', enable_tqdm=True)
instance_1 = Instance(
    question=Question('What is the capital of Austria?'),
    answers=[Answer('Vienna')],
    hints=[Hint('This city, once home to Mozart and Beethoven, is the capital of Austria.')])
instance_2 = Instance(
    question=Question('Who was the president of USA in 2009?'),
    answers=[Answer('Barack Obama')],
    hints=[Hint('He was the first African-American president in U. S. history.')])
instances = [instance_1, instance_2]
results = llm.evaluate(instances)
print(results)
# [[0.91], [1.0]]
metrics = [f'{metric_key}: {metric_value.value}' for
       instance in instances
       for hint in instance.hints for metric_key, metric_value in
       hint.metrics.items()]
print(metrics)
# ['convergence-llm-llama-3-70b: 0.91', 'convergence-llm-llama-3-70b: 1.0']
scores = [hint.metrics['convergence-llm-llama-3-70b'].metadata['scores'] for inst in instances for hint in inst.hints]
print(scores[0])
# {'Salzburg': 1, 'Graz': 0, 'Innsbruck': 0, 'Linz': 0, 'Klagenfurt': 0, 'Bregenz': 0, 'Wels': 0, 'St. Pölten': 0, 'Eisenstadt': 0, 'Sankt Johann impong': 0, 'Vienna': 1}
print(scores[1])
# {'George W. Bush': 0, 'Bill Clinton': 0, 'Jimmy Carter': 0, 'Donald Trump': 0, 'Joe Biden': 0, 'Ronald Reagan': 0, 'Richard Nixon': 0, 'Gerald Ford': 0, 'Franklin D. Roosevelt': 0, 'Theodore Roosevelt': 0, 'Barack Obama': 1}
```

Refer to our [documentation](http://hinteval.readthedocs.io/) to learn more.

## 🪪License
This project is licensed under the Apache-2.0 License - see the [LICENSE](https://opensource.org/license/apache-2-0) file for details.


## 🙏Acknowledgments
Thanks to our contributors and the University of Innsbruck for supporting this project.