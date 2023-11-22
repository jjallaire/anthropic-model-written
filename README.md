## OpenAI Eval: Anthropic Model-Written Evaluation Datasets

This repository converts Anthropic's Model-Written Evaluation Datasets (<https://github.com/anthropics/evals>) into runnable [OpenAI Evals](https://github.com/openai/evals). These datasets were originally used for the paper on [Discovering Language Model Behaviors with Model-Written Evaluations](https://arxiv.org/abs/2212.09251).

### Running Evals

The repository includes a `registry` folder suitable for passing as the `--registry_path` argument to `oaieval` (see the documentation for more details on the mechanics of [Running Evals](https://github.com/openai/evals/blob/main/docs/run-evals.md)). For example, here we run the `agreeableness` eval (note we also pass `--max-samples 20` to limit the time/expense as this is just an example command):

```bash
oaieval --registry_path registry --max_samples 20 gpt-3.5-turbo agreeableness 
```

There are 4 `eval_sets` corresponding to the 4 datasets provided in the repository:

1. `persona/`: Datasets testing models for various aspects of their behavior related to their stated political and religious views, personality, moral beliefs, and desire to pursue 
potentially dangerous goals (e.g., self-preservation or power-seeking).

2. `sycophancy/`: Datasets testing models for whether or not they repeat back a user's view to various questions (in philosophy, NLP research, and politics)

3. `advanced-ai-risk/`: Datasets testing models for various behaviors related to catastrophic risks from advanced AI systems (e.g., ). These datasets were generated in a few-shot manner. We also include human-written datasets collected by Surge AI for reference and comparison to our generated datasets.

4. `winogender/`: Larger, model-generated version of the Winogender Dataset ([Rudinger et al., 2018](https://arxiv.org/abs/1804.09301)). Includes the names of occupation titles that were generated to create the dataset (alongside occupation gender statistics from the Bureau of Labor Statistics)


### Generating Evals

To reproduce the generation of the evals, first clone the Anthropic evals repo as follows:

```bash
git clone https://github.com/anthropics/evals anthropics-evals
```

Then, run the `generate.py` script to generate the evals in the `registry` directory:

```bash
python3 generate.py
```


