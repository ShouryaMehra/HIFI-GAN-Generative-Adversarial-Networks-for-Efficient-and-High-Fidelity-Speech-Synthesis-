# HiFi-GAN: Generative Adversarial Networks for Efficient and High Fidelity Speech Synthesis

**Abstract :**
Several recent work on speech synthesis have employed generative adversarial networks (GANs) to produce raw waveforms. 
Although such methods improve the sampling efficiency and memory usage, their sample quality has not yet reached that of autoregressive and flow-based generative models.
In this work, we propose HiFi-GAN, which achieves both efficient and high-fidelity speech synthesis. 
As speech audio consists of sinusoidal signals with various periods, we demonstrate that modeling periodic patterns of an audio is crucial for enhancing sample quality. 
A subjective human evaluation (mean opinion score, MOS) of a single speaker dataset indicates that our proposed method demonstrates similarity to human quality while generating 22.05 kHz high-fidelity audio 167.9 times faster than real-time on a single V100 GPU. We further show the generality of HiFi-GAN to the mel-spectrogram inversion of unseen speakers and end-to-end speech synthesis. Finally, a small footprint version of HiFi-GAN generates samples 13.4 times 
faster than real-time on CPU with comparable quality to an autoregressive counterpart.

Visit [demo website](https://jik876.github.io/hifi-gan-demo/) for audio samples.


## Pre-requisites
1. Python >= 3.6
2. Clone this repository.
3. Install python requirements. Please refer [requirements.txt](requirements.txt)
4. Download and extract the [LJ Speech dataset](https://keithito.com/LJ-Speech-Dataset/).
And move all wav files to `LJSpeech-1.1/wavs`

## Pretrained Model
You can also use pretrained models we provide.
[Download pretrained models](https://drive.google.com/drive/folders/1-eEYTB5Av9jNql0WGBlRoi-WH2J7bp5Y?usp=sharing)
Details of each folder are as in follows:

|Folder Name|Generator|Dataset|Fine-Tuned|
|------|---|---|---|
|LJ_V1|V1|LJSpeech|No|
|LJ_V2|V2|LJSpeech|No|
|LJ_V3|V3|LJSpeech|No|
|LJ_FT_T2_V1|V1|LJSpeech|Yes ([Tacotron2](https://github.com/NVIDIA/tacotron2))|
|LJ_FT_T2_V2|V2|LJSpeech|Yes ([Tacotron2](https://github.com/NVIDIA/tacotron2))|
|LJ_FT_T2_V3|V3|LJSpeech|Yes ([Tacotron2](https://github.com/NVIDIA/tacotron2))|
|VCTK_V1|V1|VCTK|No|
|VCTK_V2|V2|VCTK|No|
|VCTK_V3|V3|VCTK|No|
|UNIVERSAL_V1|V1|Universal|No|
Download and store the extracted files in your root directory. 
We provide the universal model with discriminator weights that can be used as a base for transfer learning to other datasets.


## Inference from wav file
1. Make `test_files` directory and copy wav files into the directory.
2. Run the following command.
3. The generator path is the above mentioned root file location you have stored ur generator in.
    ```
    python inference.py --checkpoint_file [generator checkpoint file path]
    ```
Generated wav files are saved in `generated_files` by default.
You can change the path by adding `--output_dir` option.


