# 課題６レポート　画像の二値化
##### 下記のプログラムを参考にして画像を二値化せよ．
標準画像「cat」を原画像とする．この画像は縦1000画像，横1000画素による正方形のディジタルカラー画像である．

ORG=imread('cat.png');  
ORG= rgb2gray(ORG);  
imagesc(ORG); colormap(gray); colorbar;

によって，原画像を読み込み，白黒濃淡画像へ変換し，表示した結果を図１に示す．

![原画像](https://github.com/ReoOgawa/Image-processing-Report/blob/master/Image/Report-06/01.png?raw=true)  
図1 原画像

IMG = ORG>128;  
imagesc(IMG); colormap(gray); colorbar;

によって，輝度値が128以上の画素を1，その他を0として二値化した結果を図2に示す．

![原画像](https://github.com/ReoOgawa/Image-processing-Report/blob/master/Image/Report-06/02.png?raw=true)  
図2 閾値128の二値化画像

IMG = dither(ORG);  
imagesc(IMG); colormap(gray); colorbar;  

によって，ディザ法による二値化を行い，結果を図3に示す．

![原画像](https://github.com/ReoOgawa/Image-processing-Report/blob/master/Image/Report-06/03.png?raw=true)  
図3 ディザ法による二値化画像

ディザ法とはハーフトーン処理の技術の1つである．  
ハーフトーン処理とは輝度が0と255の色だけを用いてハーフトーン(中間色)を表現しようとする技術であり，２値しか出力できない表示装置でなんとかグレースケールを表現しようとしたものである．  
図2,3よりディザ法による二値化画像の方が，閾値128の二値化画像より原画像に近い結果が得られることが確認できた．
