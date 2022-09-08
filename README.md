# One-line_Diffusion_summary
The repo for studying and sharing diffusion models with Korean.

## Contents
- [Resources](#resources)
  - [Introductory Posts](#introductory-posts)
  - [Introductory Papers](#introductory-papers)
  - [Introductory Videos](#introductory-videos)
- [Papers](#papers)
  - [Vision](#vision)
    - [Must-read papers](#must-read-papers)
    - [Connection with other framworks](#connection-to-others)
    - [Image Generation](#image-generation)
    - [Image space guidance sampling](#generative with conditioned images)
    - [Classifier guidance sampling](#any papers with classifier guidance sampling)
    - [Image Editing](#image-editing)
    - [Text-to-Image](#text-to-image)
    - [Fast Sampling] (#Fast Sampling)

    
  
# Resources
## Introductory Posts

**What are Diffusion Models?** \
[[Website](https://lilianweng.github.io/lil-log/2021/07/11/diffusion-models.html)] \
11 Jul 2021 \
전반적인 Generative 모델에 대한 소개와 Diffusion model의 수식적인 정리가 깔끔하게 되어있음. 복숭아 아이콘 사이트.

**Generative Modeling by Estimating Gradients of the Data Distribution** \
[[Website](https://yang-song.github.io/blog/2021/score/)] \
5 May 2021 \
Yang Song 블로그. Score-based models를 기존의 MCMC 부터 시작하여 차근차근 훑어줌. 추천.

## Introductory Papers

**Understanding Diffusion Models: A Unified Perspective** \
*Calvin Luo* \
arXiv 2022. [[Paper](https://arxiv.org/abs/2208.11970)] \
25 Aug 2022 \
기존 Diffusion 논문들의 notation이 다 달라서 힘든데, 이 논문이 전체적인 정리를 싹 다 해놓음. 구글에서 썼고, VAE에서 부터 classifier guidance까지 수식적으로도 총정리 해둠. 수학 증명이 안되는 부분이 있다면 참고하기 좋음.

## Introductory Videos
*이상윤*\
[[Youtube channel](https://www.youtube.com/channel/UC0xHseqVPJCGy1oNIfJA4VQ)] \
디퓨전관련 스터디 영상을 업로드 해준 채널. 아쉽게도 2022.08 즈음부터 멈추긴 했지만 한국말 설명이라 찾아보면 좋음. \

*디퓨전 전반적인 정리영상*\
[[Youtube](https://youtu.be/uFoGaIVHfoE)] \
제가 발표한 영상입니다. DDPM, DDIM, ADM-G, NCSN, Score-based models, 그리고 여러 모델들의 흐름과 수학을 총정리 했습니다.

# Papers

## Vision

### Must-read papers

**Deep Unsupervised Learning using Nonequilibrium Thermodynamics** \
*Jascha Sohl-Dickstein, Eric A. Weiss, Niru Maheswaranathan, Surya Ganguli* \
ICML 2015. [[Paper](https://arxiv.org/abs/1503.03585)] [[Github](https://github.com/Sohl-Dickstein/Diffusion-Probabilistic-Models)] \
2 Mar 2015 \
Diffusion의 시작. Reverse diffusion process를 통해 데이터를 복구하는 방식을 제안함. 각각의 time step 별 가우시안 분포를 reparameterize 하는 방식의 시초라고 할 수 있다. 하지만 안읽어도 큰 문제는 없음. (DDPM을 이해했다는 전제하에)

**Denoising Diffusion Probabilistic Models** \
*Jonathan Ho, Ajay Jain, Pieter Abbeel* \
NeurIPS 2020. [[Paper](https://arxiv.org/abs/2006.11239)] [[Github](https://github.com/hojonathanho/diffusion)] [[Github2](https://github.com/pesser/pytorch_diffusion)] \
19 Jun 2020 \
DDPM. 읽어야 함. xt를 x0를 가지고 바로 샘플링하는 방식 제안, Loss를 simple하게 만들어도 잘 된다는 것을 보임.

**Improved Denoising Diffusion Probabilistic Models** \
*Alex Nichol<sup>1</sup>, Prafulla Dhariwal<sup>1</sup>* \
ICLR 2021. [[Paper](https://arxiv.org/abs/2102.09672)] [[Github](https://github.com/openai/improved-diffusion)] \
18 Feb 2021 \
사실 필수로 읽어야 하는 논문까지는 아님. 아키텍처의 변화와 스케줄링의 변화를 줌. 하지만 여기저기서 많이 등장하므로 읽어두면 좋음. 중요도는 그리 높지 않음.

**Diffusion Models Beat GANs on Image Synthesis** \
*Prafulla Dhariwal<sup>1</sup>, Alex Nichol<sup>1</sup>* \
arXiv 2021. [[Paper](https://arxiv.org/abs/2105.05233)] [[Github](https://github.com/openai/guided-diffusion)] \
11 May 2021 \
Classifier guidance 방식을 제안한 논문. 정말 많이 쓰이고 있으며 읽어두는 것을 추천.

**Denoising Diffusion Implicit Models**  \
*Jiaming Song, Chenlin Meng, Stefano Ermon* \
ICLR 2021. [[Paper](https://arxiv.org/abs/2010.02502)] [[Github](https://github.com/ermongroup/ddim)] \
6 Oct 2020 \
Marcov chain을 끊고 Deterministic 하게 만든 논문. 수식적으로 복잡하나, 잘 이해해둬야 하는 필수 논문 중 하나.

**Generative Modeling by Estimating Gradients of the Data Distribution** \
*Yang Song, Stefano Ermon* \
NeurIPS 2019. [[Paper](https://arxiv.org/abs/1907.05600)] [[Project](https://yang-song.github.io/blog/2021/score/)] [[Github](https://github.com/ermongroup/ncsn)] \
12 Jul 2019 \
Score-based models의 시초격인 논문. 결국 VE-SDE를 이해하기 위해선 이 논문이 선행되어야 함.

**Score-Based Generative Modeling through Stochastic Differential Equations** \
*Yang Song, Jascha Sohl-Dickstein, Diederik P. Kingma, Abhishek Kumar, Stefano Ermon, Ben Poole* \
ICLR 2021 (Oral). [[Paper](https://arxiv.org/abs/2011.13456)] [[Github](https://github.com/yang-song/score_sde)] \
26 Nov 2020 \
Score-based 와 DDPM을 SDE로 묶어낸 논문. 매우 잘 써진 논문이라 생각하며, 필수적으로 읽어봐야 한다고 생각.

**Variational Diffusion Models** \
*Diederik P. Kingma, Tim Salimans, Ben Poole, Jonathan Ho* \
NeurIPS 2021. [[Paper](https://arxiv.org/abs/2107.00630)] [[Github](https://github.com/revsic/jax-variational-diffwave)] \
1 Jul 2021 \
필수라고 적어놨지만 필자도 아직 안읽었습니다.. SNR을 정의 내린 논문. 그리고 수식적으로 잘 정리된 논문. 조만간 읽고 업데이트 하겠습니다.

### Image Generation

**Score-Based Generative Modeling with Critically-Damped Langevin Diffusion** \
*Tim Dockhorn, Arash Vahdat, Karsten Kreis* \
arXiv 2021. [[Paper](https://arxiv.org/abs/2112.07068)] [[Project](https://nv-tlabs.github.io/CLD-SGM/)] \
14 Dec 2021 \
Nvidia에서 낸 논문으로 기존에 Score-based에 velocity 축을 하나 더 만들어서 수렴도 잘 되고 학습도 빠르게 만듬. 수학적으로 잘 정리되어있어서 좋은 논문.

**Cascaded Diffusion Models for High Fidelity Image Generation** \
*Jonathan Ho<sup>1</sup>, Chitwan Saharia<sup>1</sup>, William Chan, David J. Fleet, Mohammad Norouzi, Tim Salimans* \
arXiv 2021. [[Paper](https://arxiv.org/abs/2106.15282)] [[Project](https://cascaded-diffusion.github.io/)] \
30 May 2021 \
이미지 resolution을 키워가면서 생성하는 방법 소개.

### Connection with other framworks

**Diffusion Autoencoders: Toward a Meaningful and Decodable Representation** \
*Konpat Preechakul, Nattanat Chatthee, Suttisak Wizadwongsa, Supasorn Suwajanakorn* \
CVPR 2022. [[Paper](https://arxiv.org/abs/2111.15640)] [[Project](https://diff-ae.github.io/)] [[Github](https://github.com/phizaz/diffae)] \
30 Dec 2021 \
Diffusion models에 semantic latent를 컨디션으로 주어서 Autoencoder 처럼 만듬. 그래서 latent가 생겼고, manipulation이 가능해짐. 성능 좋고 잘됨.

**DiffuseVAE: Efficient, Controllable and High-Fidelity Generation from Low-Dimensional Latents** \
*Kushagra Pandey, Avideep Mukherjee, Piyush Rai, Abhishek Kumar* \
arXiv 2022. [[Paper](https://arxiv.org/abs/2201.00308)] [[Github](https://github.com/kpandey008/DiffuseVAE)] \
2 Jan 2022 \
제대로 못읽었지만, VAE의 형태를 빌려와서 합친 논문.

**High-Resolution Image Synthesis with Latent Diffusion Models** \
*Robin Rombach<sup>1</sup>, Andreas Blattmann<sup>1</sup>, Dominik Lorenz, Patrick Esser, Björn Ommer* \
arXiv 2021. [[Paper](https://arxiv.org/abs/2112.10752)] [[Github](https://github.com/CompVis/latent-diffusion)] \
20 Dec 2021 \
global AutoEncoder를 학습해서 그 latent 상에서 diffusion을 한 논문. stable-diffusion이 이 논문이다.

**Score-based Generative Modeling in Latent Space** \
*Arash Vahdat<sup>1</sup>, Karsten Kreis<sup>1</sup>, Jan Kautz* \
arXiv 2021. [[Paper](https://arxiv.org/abs/2106.05931)] \
10 Jun 2021
VAE랑 합친 논문. VAE와 Diffusion을 동시에 학습. Diffusion은 VAE의 latent space에서 학습된다.


### Image space guidance sampling

**ILVR: Conditioning Method for Denoising Diffusion Probabilistic Models** \
*Jooyoung Choi, Sungwon Kim, Yonghyun Jeong, Youngjune Gwon, Sungroh Yoon* \
ICCV 2021 (Oral). [[Paper](https://arxiv.org/abs/2108.02938)] [[Github](https://github.com/jychoi118/ilvr_adm)] \
6 Aug 2021 \
이미지를 Low-pass filter 통과시킨 후 합쳐서 원하는 이미지랑 비슷한 이미지 생성

**RePaint: Inpainting using Denoising Diffusion Probabilistic Models** \
*Andreas Lugmayr, Martin Danelljan, Andres Romero, Fisher Yu, Radu Timofte, Luc Van Gool* \
CVPR 2022. [[Paper](https://arxiv.org/abs/2201.09865)] [[Github](https://github.com/andreas128/RePaint)] \
24 Jan 2022 \
Inpainting 논문. 마스크된 영역만 바꿔껴주는 방식을 제안. 여러번 돌리는 방법만 주목해서 보면 됨. 나머진 그닥 필요 없음.

**SDEdit: Image Synthesis and Editing with Stochastic Differential Equations**  \
*Chenlin Meng, Yang Song, Jiaming Song, Jiajun Wu, Jun-Yan Zhu, Stefano Ermon* \
ICLR 2022. [[Paper](https://arxiv.org/abs/2108.01073)] [[Project](https://sde-image-editing.github.io/)] [[Github](https://github.com/ermongroup/SDEdit)] \
2 Aug 2021 \
stroke를 노이즈를 적당히 씌웠다가 샘플링하면 비슷한 색의 real한 이미지를 얻을 수 있음.

### Classifier guidance sampling

**Classifier-Free Diffusion Guidance** \
*Jonathan Ho, Tim Salimans* \
NeurIPS Workshop 2021. [[Paper](https://arxiv.org/abs/2207.12598)] \
28 Sep 2021 \
엄밀히는 classifier guidance가 아니지만 학습할 때 서서히 fade out 하는 논문.

### Image Editing

**Denoising Diffusion Restoration Models** \
*Bahjat Kawar, Michael Elad, Stefano Ermon, Jiaming Song* \
arXiv 2022. [[Paper](https://arxiv.org/abs/2201.11793)] \
27 Jan 2022 \
이미지 자체가 하자가 있다고 생각하고 특정 행렬 곱으로 노이즈나.. 크롭이나.. 그런걸 나타낼 수 있다면 원본을 복구하는 방식 제안.

**Palette: Image-to-Image Diffusion Models** \
*Chitwan Saharia, William Chan, Huiwen Chang, Chris A. Lee, Jonathan Ho, Tim Salimans, David J. Fleet, Mohammad Norouzi* \
NeurlPS 2022. [[Paper](https://arxiv.org/abs/2111.05826)] \
10 Nov 2021 \
별거 안하고 그냥 튜닝해서 모델 하나로 4가지 task에서 SOTA 달성.

### Text-to-Image


### Fast Sampling

**Learning Fast Samplers for Diffusion Models by Differentiating Through Sample Quality** \
*Daniel Watson, William Chan, Jonathan Ho, Mohammad Norouzi \
ICLR 2022. [[Paper](https://openreview.net/forum?id=VFBjuF8HEp)]  \
11 Feb 2022 \
Pre-trained을 fine-tunning 하지 않고 step#를 줄여서 빠르게 sampling 하면서도 FID/IS 를 최대한 유지할 수 있는 방법제시,
diffusion의 object function(ELBO) term을 무시하고, step과 step사이에 sampling하는 paremeter들만 KID loss 를 줘서 train.



, Daniel Watson et al., 2022
