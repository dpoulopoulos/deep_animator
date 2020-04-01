# Deep Animator
> Image animation given a driving video sequence and a source image.


Deep Animator is an implementation of [First Order Motion Model for Image Animation](https://papers.nips.cc/paper/8935-first-order-motion-model-for-image-animation) by [Aliaksandr Siarohin](https://github.com/AliaksandrSiarohin), [Stéphane Lathuilière](http://stelat.eu/), [Sergey Tulyakov](http://www.stulyakov.com/), [Elisa Ricci](http://elisaricci.eu/) and [Nicu Sebe](http://disi.unitn.it/~sebe/). 

The source code can be found [here](https://github.com/AliaksandrSiarohin/first-order-model). **This library is a simple transformation of the original code into a shell script for quick experimentation**. This is also an educational effort for the writer. 

## Install

Run `pip install deep-animator` to install the library in your environment.

## How to use

First you need to download the weights of the model [here](https://drive.google.com/file/d/1zqa0la8FKchq62gRJMMvDGVhinf3nBEx/view?usp=sharing). Then just run the following command.

`deep_animate <path_to_the_source_image> <path_to_the_driving_video> <path_to_yaml_conf> <path_to_model_weights>`

* Example of source image [here](https://drive.google.com/file/d/1ACSKOfQUHbSEWmPu4Ndss7bkrPVK5WBR/view?usp=sharing)
* Example of driving video [here](https://drive.google.com/file/d/103PEtO2QO45XwCNLYIzMcW3aRdbOhS1D/view?usp=sharing)

An example YAML file is given below:

```
model_params:
  common_params:
    num_kp: 10
    num_channels: 3
    estimate_jacobian: True
  kp_detector_params:
     temperature: 0.1
     block_expansion: 32
     max_features: 1024
     scale_factor: 0.25
     num_blocks: 5
  generator_params:
    block_expansion: 64
    max_features: 512
    num_down_blocks: 2
    num_bottleneck_blocks: 6
    estimate_occlusion_map: True
    dense_motion_params:
      block_expansion: 64
      max_features: 1024
      num_blocks: 5
      scale_factor: 0.25
  discriminator_params:
    scales: [1]
    block_expansion: 32
    max_features: 512
    num_blocks: 4
    sn: True
```
