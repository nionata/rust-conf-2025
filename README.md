# EdgeAI Workshop

## Device Setup

* Setup board
  * Plug in micro-SD
  * Plug in ETH
  * Plug in power

* Connect to RustConf2025_AI

  * Password: `edgeaiworkshop`

* Add SSH config

```bash
Host edgeai
  HostName 172.20.33.104
  User pi
```

## ai-coustics

Noisy speech -> enhanced speech - image based inference

## AI Intro

* Distillation takes huge model and generates a smaller one
* Distillation has been rebranded as synthetic
* Multi-step process, open-r1 (open source version of deepseek paper)
* Bitter lesson
  * develop progressivly more general methods with weaker modeling assumptions
  * simple methods that scale
* HuggingFace tokenizers library is built on top of Rust (including python library)

## AI tools (training and inference)

### Ecosystem

* ONNX is nice as it's an open standard to "compiling" models + weights into a file

### Rust

* burn
  * 
* candle
  *
* tract
  * CPU only
* ort
  * wrapper around ONNX runtime
  * rust as a build system
  * great documentation
  * ONNX is nice as it's an open standard to "compiling" models + weights into a file
  * This is the go-to solution right now
* Static linking CUDA and tensor flow in their library
  * that must be huge, how big is it?

## AI/CV Lecture

* software 2.0
  * software 1.0: source code -> compiler -> binary -> unit test
  * 2.0: dataset -> arch + training -> trained model -> validation bench
  * 2.0 is eating away at 1.0
* edge ai pros
  * scalable w/ number of devices
  * no need for central server
  * Fedterated learning - ea device learns from its own data
* Neural Network
  * Sequential mstatrix multiplications
    * dot product
  * How to use it for CV
    * simply flattening the image into a matrix will not work well
      * no spacial awareness, many unused params
    * fully connected / locally connection (convolutional)
      * maintains spacial context
  * Modern CCN arch (backbones)
    * progress has slown down there since 2020
  * computer vision tasks
    * segmentation - label each pixel with a class
      * SegNet - hourglass CNN
      * U-Net: convolutional networks for biomedical image segmentation
* Transformers
  * general token-processors
    * input -> tokenizer -> transformer
  * different than CNNs
  * Vision Transformer (ViT)
    * Split image into non-overlapping patches
    * Process them like they are "words"
    * O(n^2) complexity
    * Usually, can scale better with data than CNN
  * Video Transformer (ViViT)
* How to choose model?
  * CNN are fast and work best for edge
    * many optimized variants
* Embeddings are like hashes
  * similar, will have them be "closer" (dot product similarity)
* Components
  * model diff are overrated
  * supervision is underrated
* Supervision
  * datasets are usually semi- or not- 
* CNNs
  * Struggle with context/semantics
  * ex. biased towards texture
* Pretext tests
  * Can you tell if the image is mirrored?
    * This takes some context, but there are plently of visual features to use without understanding the context
* Contrastive Learning (self-supervising)
  * Attract crops, changes, etc from the same image
  * Repel similar images
  * Need to do color jitter so model can't cheat
  * Data augmentation is critical
    * programatically generate new variations of the an input
    * cheap + fast
* Compression
  * important...
* HuggingFace
  * GitHub for AI models
* tasks in CV
  * all comes down to Visual question answering

## Workshop

* https://github.com/radu1999/face_auth
* https://github.com/Wyliodrin/part-2-chat-with-llm.git

## LLM Lecture

* Old methods, developed in 80 and 90, when scaled up worked well
* 2017 paper wrote by Google - "Attention is all you need" - intro'd the transformer
* All NLP problems were reduced down to translation - text in to text out
  * T5 (2019)
* Text tokenization = splitting a string into a sequence of tokens
  * most methods so far used either word-level or character-level tokenization
  * Both are inadequate
  * Byte-pair-encoding is the latest tokenization scheme
    * Greedy algorithm
* Performance
  * Smaller models with better training/compute can outperform larger models, there is a sweet spot somewhere
  * Some capabilities only emerge at larger sizes
* Super-fine tuning
  * Started to do embeddings in the prompt
* InstructGPT, 2022
  * This became ChatGPT
* We are running out of source material at this point
  * We can still scale computer
  * Things that are being added are "reasoning", which is part prompt engineering and part program mechanism
  * chain or thoughts / self-consistency / tree of thoughts
* RAG
  * Search documents from the index, the content is then embedded in the original prompt
  * This is prompt/context engineering
* Small models are created from large models (distillation) the same way it worked for CV

## Random NOtes

* TPU/MCU - specific accelarated hardware
* coral ai micro boards with imx and tpu