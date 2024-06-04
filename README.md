# Music Transformer: Generating Music with Long-Term Structure

- 2019 ICLR, Cheng-Zhi Anna Huang, Google Brain
- Re-producer : Yang-Kichang
- [paper link](https://arxiv.org/abs/1809.04281) 
- [paper review](https://github.com/SSUHan/PaparReviews/issues/13)

## Abstract

1. This Repository is  compatible with **pytorch**



## Contribution

* Domain: Dramatically reduces the memory footprint, allowing it to scale to musical sequences on the order of minutes.
* Algorithm: Reduced space complexity of Transformer from O(N^2D) to O(ND).



## Representation 

Uses the implementation of:

Sageev Oore, Ian Simon, Sander Dieleman, Douglas Eck, and Karen Simonyan. "This time with feeling: Learning expressive musical performance" arXiv:1808.03715, 2018.

"Which consists of a vocabulary of 128 NOTE_ON events, 128 NOTE_OFFs, 100 TIME_SHIFTs allowing for expressive timing at 10ms and 32 VELOCITY bins for expressive dynamics "

The implementation can be found at the address [https://github.com/jason9693/midi-neural-processor][https://github.com/jason9693/midi-neural-processor] and it's a submodule of this repo

  ![](https://user-images.githubusercontent.com/11185336/51083282-cddfc300-175a-11e9-9341-4a9042b17c19.png)



## Simple Start ( Repository Setting )

```bash
$ git clone https://github.com/jason9693/MusicTransformer-pytorch.git
$ cd MusicTransformer-pytorch
$ git clone https://github.com/jason9693/midi-neural-processor.git midi_processor
```


## Midi Download	

```bash
$ sh dataset/script/{ecomp_piano_downloader, midi_world_downloader, ...}.sh
```

Note: Ecomp piano downloader does not work anymore at the moment!

* These shell files are from [performaceRNN re-built repository](https://github.com/djosix/Performance-RNN-PyTorch) implemented by [djosix](https://github.com/djosix)


## Dataset preprocessing

To turn a directory of MIDI files into a representation that can be read by the model, use:

```bash
$ python preprocess.py datasets/midi/epiano/ datasets/preprocesses/epiano/
```

where midi_load_dir is something like datasets/midi/epiano/, and dataset_save_dir datasets/preprocesses/epiano/


## Trainig

Example:

```bash
$ python3 train.py -c config/base.yml config/train.yml -m trained_models/
```


## Hyper Parameter

* learning rate : 0.0001
* head size : 4
* number of layers : 6
* seqence length : 2048
* embedding dim : 256 (dh = 256 / 4 = 64)
* batch size : 2



## Result

-  Baseline Transformer ( Green, Gray Color ) vs Music Transformer ( Blue, Red Color )

* Loss

  ![loss](readme_src/loss.svg)

* Accuracy

  ![accuracy](readme_src/accuracy.svg)



## Generate Music

```bash
python3 generate.py -c config/base.yml config/generate.yml -m trained_models/
```

## Generated Samples ( Youtube Link )

* click the image.

  [<img src="readme_src/sample_meta.jpeg" width="400"/>](https://www.youtube.com/watch?v=n6pi7QJ6nvk&list=PLVopZAnUrGWrbIkLGB3bz5nitWThIueS2)
