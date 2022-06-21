# ViT-self-dist-DG
# Self-Distilled Vision Transformer for Domain Generalization

The code is build on the top of DomainBed: a PyTorch suite containing benchmark datasets and algorithms for domain generalization, as introduced in [In Search of Lost Domain Generalization](https://arxiv.org/abs/2007.01434).


## Model selection criteria
We computed results on the following model selection
* `IIDAccuracySelectionMethod`: A random subset from the input data of the training source domains.

## Quick start

Download the datasets:

```sh
python3 -m domainbed.scripts.download \
       --data_dir=./domainbed/data
```

Training a single model with an indiviual target domain (test_env) id 0:

```sh
python3 -m domainbed.scripts.train\
       --data_dir=./domainbed/data/PACS/\
       --algorithm ERM-ViT\
       --dataset PACS\
       --test_env 0
```

Launching a sweep: Training model with a all target domains

```sh
python -m domainbed.scripts.sweep launch\
       --data_dir=/my/datasets/path\
       --output_dir=/Sweep Output/path\
       --command_launcher multi_gpu
```


To view the results:

````sh
python -m domainbed.scripts.collect_results\
       --input_dir=/Sweep Output/path --get_recursively True
````



## License

This source code is released under the MIT license, included [here](LICENSE).
