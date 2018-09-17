# SemanticSNGAN
An attempt to improve the global coherency of generations.

## Table of Contents
- [SemanticSNGAN](#semanticsngan)
  * [SNGAN Training](#sngan-training)
    + [Inception Scores](#inception-scores)
  * [Experiments](#experiments)
    + [Encoded Representations](#encoded-representations)
      - [SNGAN](#sngan)
      - [VAE](#vae)
    + [Coherency](#coherency)
        * [TRAIN](#train)
        * [TEST](#test)
        * [GENERATED](#generated)

## SNGAN Training

<img src=https://github.com/sudeepkatakol/SemanticSNGAN/blob/master/tf-SNDCGAN-master/Training%20Images/100000.png />

### Inception Scores

#### 5000 Samples
|Iteration| Inception Score|
|------|-----|
10000| 4.477705001831055 	  +- 0.1237875446677208|
20000| 5.79064416885376 	  +- 0.1632663607597351|
30000|  6.127541542053223   +- 0.20145201683044434|
40000 |  6.487113952636719 	+- 0.3289961516857147|
50000 | 6.777251243591309 	+- 0.21267540752887726|
60000 | 6.883315086364746 	+- 0.3300464451313019|
70000 | 7.0580644607543945  +- 0.20164021849632263|
80000 | 6.918496131896973 	+- 0.276136577129364|
90000 | 6.973136901855469 	+- 0.25999584794044495|
100000| 7.235245704650879 	+- 0.25336676836013794|

#### 10000 Samples
|Iteration| Inception Score|
|------|-----|
80000 | 7.06506872177124  +- 0.1578473299741745.
90000 | 7.1522111892700195 +- 0.2032909244298935.
100000 | 7.292139530181885 +- 0.2068527787923813.


## Experiments
Train, Test and (SNGAN) Generated Images 

### Encoded Representations

#### SNGAN
<img src=https://github.com/sudeepkatakol/SemanticSNGAN/blob/master/desktop_plots/SNGAN_Combined_tsne.png />
<img src=https://github.com/sudeepkatakol/SemanticSNGAN/blob/master/desktop_plots/SNGAN_train_tsne.png />
<img src=https://github.com/sudeepkatakol/SemanticSNGAN/blob/master/desktop_plots/SNGAN_test_tsne.png />
<img src=https://github.com/sudeepkatakol/SemanticSNGAN/blob/master/desktop_plots/SNGAN_generated_tsne.png />

#### VAE
Same Architecture

<img src=https://github.com/sudeepkatakol/SemanticSNGAN/blob/master/desktop_plots/VAE_Combined_tsne.png />
<img src=https://github.com/sudeepkatakol/SemanticSNGAN/blob/master/desktop_plots/VAE_train_tsne.png />
<img src=https://github.com/sudeepkatakol/SemanticSNGAN/blob/master/desktop_plots/VAE_test_tsne.png />
<img src=https://github.com/sudeepkatakol/SemanticSNGAN/blob/master/desktop_plots/VAE_generated_tsne.png />


### Coherency
#### Local coherency
Swap 'factor' adjacent columns and measure the change in discriminator output.

#### Global coherency
Interchange patches of image and measure the change in dicriminator output.
##### TRAIN

###### Local
|Factor|Error| Loss|
|------|-----|-----|
2| 1.2407807111740112 | 1.7711739540100098
3| 1.2415285110473633 | 1.761534333229065
4| 1.2353380918502808 | 1.7443026304244995
5| 1.2390804290771484 | 1.7311062812805176
8| 1.2782659530639648 | 1.7316051721572876
16| 2.163848638534546 | 2.960369348526001
32| 6.563145637512207 | 7.842253684997559


###### Global
|Patch size|Error| Loss|
|------|-----|-----|
2| 1.233760952949524 |1.7134640216827393
4| 1.2417927980422974 |1.7185721397399902
8| 1.2918143272399902 |1.7219175100326538
16| 1.4115720987319946 |1.6655635833740234

------------------------------
##### TEST

###### Local
|Factor|Error| Loss|
|------|-----|-----|
2| 1.2032368183135986| 1.7107226848602295
3| 1.200979232788086 | 1.704603910446167
4| 1.1965570449829102 | 1.6959502696990967
5| 1.1987884044647217 | 1.690832495689392
8| 1.2192925214767456 | 1.7302829027175903
16| 2.3913350105285645 | 3.119769334793091
32| 7.208259582519531 | 8.087034225463867

###### Global
|Patch size|Error| Loss|
|------|-----|-----|
2| 1.1856664419174194| 1.6796118021011353
4| 1.1912814378738403| 1.70344078540802
8| 1.234431266784668| 1.7676624059677124
16| 1.32599937915802| 1.8563122749328613

---------------------------------
##### GENERATED

###### Local
|Factor|Error| Loss|
|------|-----|-----|
2| 0.07725143846367316| 1.5875823851381272
3| 0.08501501675830998| 1.586483099728198
4| 0.0993185383165091 |1.585078447409739
5| 0.12122180069080712 |1.587087613085069
8| 0.2680052599729933 |1.6360983655166876
16| 1.9303587317238755| 2.8163385614436858
32| 7.043071914855084 |7.506414942042386

###### Global
|Patch size|Error| Loss|
|------|-----|-----|
2| 0.1258577044087034| 1.5848842750990126
4| 0.21936533588245183| 1.6205765214576051
8| 0.4253772450547564 |1.6988914818216903
16| 0.7839014091903385 |1.848932246878071
