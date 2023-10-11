# **OptiMUS**: Optimization Modeling Using mip Solvers and large language models

This repository contains the official implementation for [**OptiMUS**: Optimization Modeling Using mip Solvers and large language models]([https://arxiv.org/](https://arxiv.org/abs/2310.06116)).

<br>
<br>

![optimus_agent](https://github.com/teshnizi/OptiMUS/assets/48642434/23b1ab19-8248-4aad-8831-02cc895afffd)

## NLP4LP Dataset

You can download the dataset from [https://nlp4lp.vercel.app/](https://nlp4lp.vercel.app/). Please note that NLP4LP is intended and licensed for research use only. The dataset is CC BY NC 4.0 (allowing only non-commercial use) and models trained using the dataset should not be used outside of research purposes.

## Usage

1. Clone this repository
2. Download [NLP4LP dataset zip file](https://nlp4lp.vercel.app/), extract the contents, and replace the empty `datasets/` folder in the root directory of the repo with the downloaded one (beside gpt4or.py):

   <img width="535" alt="image" src="https://github.com/teshnizi/OptiMUS/assets/48642434/e287a0da-ac46-4604-89f6-59d4ee4037b3">

3. Add your OpenAI API key(s) in `configure.py`:

```python
from utils import get_templates

api_keys = [
    # "sk-API-KEY-1",
    # "sk-API-KEY-2",
    # ...
]

# Get templates
templates = get_templates()
...
```

4. Install the requirements using `pip install -r requirements.txt`
5. Run the agent:

   ```bash
   python gpt4or --model gpt-4 --maxtry 5 --mode 105 --verbose True --prob ./datasets/introduction_to_linear_optimization/problem_1
   ```

## Modes and Options:

```bash
options:
  -h, --help           show this help message and exit
  --model MODEL        Model name
  --prob PROB          Problem path
  --stdfname STDFNAME  Description file name
  --maxtry MAXTRY      Maximum attempts
  --human HUMAN        Human test file
  --aug AUG            Number of augmentations. Uses the rephrases generated by using the --rephrase parameter.
  --solver SOLVER      Solver name (cvxpy/gurobi)
  --mode MODE          102: Prompt, 103: Prompt + Debug, 104: Prompt + Debug + AutoTest, 105: Prompt + Debug + Human Test
  --rephrase REPHRASE  Number of rephrases. If more than 0, the agent will only generate rephrases of the problem and will
                       NOT solve the problem. The rephrased instances can then later be used by setting the aug parameter to
                       the number of rephrases.
  --verbose VERBOSE    Verbose mode
```
