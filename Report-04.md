# 課題４レポート　画像のヒストグラム
##### 画素の濃度ヒストグラムを生成せよ．
標準画像「cat」を原画像とする．この画像は縦1000画像，横1000画素による正方形のディジタルカラー画像である．

ORG=imread('cat.png');  
ORG= rgb2gray(ORG);  
imagesc(ORG); colormap(gray); colorbar;

によって，原画像を読み込み，白黒濃淡画像へ変換し，表示した結果を図１に示す．

![原画像](https://github.com/ReoOgawa/Image-processing-Report/blob/master/Image/Report-03/01.png?raw=true)  
図1 原画像

IMG = ORG > 64;  
imagesc(IMG); colormap(gray); colorbar;  

上記で輝度値が64以上の画素を1，その他を0に変換し，閾値処理した結果を図２に示す．

![原画像](https://github.com/ReoOgawa/Image-processing-Report/blob/master/Image/Report-03/02.png?raw=true)  
図2 輝度値64以上閾値処理

IMG = ORG > 96;  
imagesc(IMG); colormap(gray); colorbar;  

上記で輝度値が96以上の画素を1，その他を0に変換し，閾値処理した結果を図３に示す．

![原画像](https://github.com/ReoOgawa/Image-processing-Report/blob/master/Image/Report-03/03.png?raw=true)  
図3 輝度値96以上閾値処理

IMG = ORG > 128;  
imagesc(IMG); colormap(gray); colorbar;  

上記で輝度値が128以上の画素を1，その他を0に変換し，閾値処理した結果を図４に示す．

![原画像](https://github.com/ReoOgawa/Image-processing-Report/blob/master/Image/Report-03/04.png?raw=true)  
図4 輝度値128以上閾値処理

IMG = ORG > 192;  
imagesc(IMG); colormap(gray); colorbar;  

上記で輝度値が192以上の画素を1，その他を0に変換し，閾値処理した結果を図５に示す．

![原画像](https://github.com/ReoOgawa/Image-processing-Report/blob/master/Image/Report-03/05.png?raw=true)  
図5 輝度値192以上閾値処理
