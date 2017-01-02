# 課題５レポート　判別分析法
##### 判別分析法を用いて画像二値化せよ．
標準画像「cat」を原画像とする．この画像は縦1000画像，横1000画素による正方形のディジタルカラー画像である．

ORG=imread('cat.png');  
ORG= rgb2gray(ORG);  
imagesc(ORG); colormap(gray); colorbar;

によって，原画像を読み込み，白黒濃淡画像へ変換し，表示した結果を図１に示す．

![原画像](https://github.com/ReoOgawa/Image-processing-Report/blob/master/Image/Report-05/01.png?raw=true)  
図1 原画像

imhist(ORG);

によってヒストグラムを表示し，結果を図２に示す．

![原画像](https://github.com/ReoOgawa/Image-processing-Report/blob/master/Image/Report-04/02.png?raw=true)  
図2 ヒストグラム

図2より，40および240周辺が特に多いことが確認できる．
