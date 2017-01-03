# 課題７レポート　ダイナミックレンジの拡大
##### 画素のダイナミックレンジを０から２５５にせよ．
標準画像「cat」を原画像とする．この画像は縦1000画像，横1000画素による正方形のディジタルカラー画像である．

ORG=imread('cat.png');  
ORG= rgb2gray(ORG);  
imagesc(ORG); colormap(gray); colorbar;

によって，原画像を読み込み，白黒濃淡画像へ変換し，表示した結果を図１に示す．

![原画像](https://github.com/ReoOgawa/Image-processing-Report/blob/master/Image/Report-07/01.png?raw=true)  
図1 原画像

imhist(ORG);  

によって，図1の濃度ヒストグラムを生成し，表示された結果を図2に示す．

![原画像](https://github.com/ReoOgawa/Image-processing-Report/blob/master/Image/Report-07/02.png?raw=true)  
図2 図1の濃度ヒストグラム

ORG = double(ORG);  
mn = min(ORG(:));  
mx = max(ORG(:));  
ORG = (ORG-mn)/(mx-mn)*255;  
imagesc(ORG); colormap(gray); colorbar;
