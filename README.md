# DAVE

Dahee Kwon · Haeun Lee · Jaesik Choi

This is the official implementation of **Breaking the Lock-in: Diversifying Text-to-Image Generation via Representation Modulation**, published in ICML 2026. [![arXiv](https://img.shields.io/badge/arXiv-2606.06813-b31b1b.svg)](https://arxiv.org/abs/2606.06813)

## Abstract
Recent text-to-image models produce high-quality, prompt-aligned images, but samples generated from the same prompt often look overly similar. We investigate this homogeneity by analyzing intermediate Transformer features and find that their spatial average, or DC component, quickly becomes similar across different seeds early in generation. This early convergence locks generation trajectories into similar outcomes and reduces later variation. Motivated by this, we propose DC Attenuation for diVersity Enhancement (**DAVE**), a training-free representation-level intervention that attenuates the early DC component. DAVE improves prompt-consistent diversity with negligible overhead while maintaining image quality.

![image](./dave-main.png)

## Setup
1) To create the conda environment needed to run the code, run the following command:

```
conda env create -f environment.yaml
conda activate DAVE
```

2) To use our source code, you also need to install diffusers from source "https://github.com/huggingface/diffusers.git":

```
git clone https://github.com/huggingface/diffusers.git
```

4) Please change the source code for diffusers below to the code for diffusers_custom and then install from source:
- diffusers/pipelines/stable_diffusion_3/pipeline_stasble_diffuson_xl.py
- diffusers/models/transformers/transformer_sd3.py

```
cp diffusers_dave/pipeline_stable_diffusion_3.py diffusers/src/diffusers/pipelines/stable_diffusion_3/pipeline_stable_diffusion_3.py
cp diffusers_dave/transformer_sd3.py diffusers/src/diffusers/models/transformers/transformer_sd3.py
cd diffusers
pip install -e .
```  

5) (Optional) If you would like to apply DAVE other than SD3, you could 
 
```
pip install torch==2.1.0 torchvision==0.16.0 torchaudio==2.1.0 --index-url https://download.pytorch.org/whl/cu118
```  

Now, you are ready to play with DAVE!  

## Usage
 1) You can try our method by manually setting the amplification factors in a simple ipython notebook `DAVE-demo.ipynb`.

## Contact 
For questions, research discussions, or collaboration opportunities, please feel free to contact [Dahee Kwon](mailto:dahee.kwon@kaist.ac.kr)
