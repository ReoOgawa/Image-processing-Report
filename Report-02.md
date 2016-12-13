# 課題２レポート 階調数と疑似輪郭
##### ２階調，４階調，８階調の画像を生成せよ．

標準画像「cat」を原画像とする．この画像は縦1000画像，横1000画素による正方形のディジタルカラー画像である．

ORG=imread('cat.png'); % 原画像の入力   
ORG = rgb2gray(ORG); colormap(gray); colorbar;   
imagesc(ORG); colormap(gray); colorbar;  axis image;pause;  
によって，原画像を読み込み，グレースケールイメージへ変換し表示した結果を図１に示す．なお図１は256階調の画像となっている．

![原画像](https://github.com/ReoOgawa/Image-processing-Report/blob/master/Image/Report-02/01.png?raw=true)  
図1 グレースケールイメージ

２階調画像の生成をするには，256階調を２段階で表せばよいため，半分にあたる128より大きい値と，128未満の値の2階調で表現させればよい．

IMG = ORG>128;  
imagesc(IMG); colormap(gray); colorbar;  axis image;

２階調画像の生成の結果を図２に示す．

![原画像](https://github.com/ReoOgawa/Image-processing-Report/blob/master/Image/Report-02/02.png?raw=true)  
図2 ２階調画像

同様に４階調画像の生成するには，256階調を４段階で表す，すなわち，

IMG0 = ORG>64;  
IMG1 = ORG>128;  
IMG2 = ORG>192;  
IMG = IMG0 + IMG1 + IMG2;  
imagesc(IMG); colormap(gray); colorbar;  axis image;

とする．４階調画像の結果を図３に示す．

![原画像](https://github.com/ReoOgawa/Image-processing-Report/blob/master/Image/Report-02/03.png?raw=true)   
図3 ４階調画像

同様に８階調画像の生成するには，256階調を８段階で表す，すなわち，

IMG0 = ORG>32;  
IMG1 = ORG>64;  
IMG2 = ORG>96;  
IMG3 = ORG>128;  
IMG4 = ORG>160;  
IMG5 = ORG>192;  
IMG6 = ORG>224;  
IMG = IMG0 + IMG1 + IMG2 + IMG3 + IMG4 + IMG5 + IMG6 ;  
imagesc(IMG); colormap(gray); colorbar;  axis image;

![原画像](https://github.com/ReoOgawa/Image-processing-Report/blob/master/Image/Report-02/04.png?raw=true)  図4 ８階調画像

このように256階調を目的の階調の数で分割し，足したものを表示することで生成することができる．また，低い階調で画像を表現すると，明るさや色が緩やかに変化する部分に疑似輪郭と呼ばれる等高線状の縞が発生することが確認できる．
