# 課題８レポート　ラベリング
##### 二値化された画像の連結成分にラベルをつけよ．
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

図1の濃度値は次に示す図3より，最小値が4，最大値が250となっている．

![原画像](https://github.com/ReoOgawa/Image-processing-Report/blob/master/Image/Report-07/001.PNG?raw=true)  
図3 図1の最大・最小濃度値

次の処理により，図1の画素のダイナミックレンジを０から２５５に拡大する．  

ORG = double(ORG);  
mn = min(ORG(:));  
mx = max(ORG(:));  
ORG = (ORG-mn)/(mx-mn)*255;  
imagesc(ORG); colormap(gray); colorbar;  

上記の処理によってダイナミックレンジが０から２５５に拡大された結果を図4に示す．

![原画像](https://github.com/ReoOgawa/Image-processing-Report/blob/master/Image/Report-07/03.png?raw=true)  
図4 ダイナミックレンジ拡大画像

ここでORGは図5に示す通り，doubleにより浮動小数点数となっているため，  
ORG = uint8(ORG);  
imhist(ORG);  
によって8 ビット符号なし整数へ変換した結果を図6に示す．  
変換後，濃度ヒストグラムを生成し，表示された結果を図7に示す．

![原画像](https://github.com/ReoOgawa/Image-processing-Report/blob/master/Image/Report-07/double-org.png?raw=true)  
図5 ORG(倍精度浮動小数点数)

![原画像](https://github.com/ReoOgawa/Image-processing-Report/blob/master/Image/Report-07/uint-org.png?raw=true)  
図6 ORG(8 ビット符号なし整数)

![原画像](https://github.com/ReoOgawa/Image-processing-Report/blob/master/Image/Report-07/04.png?raw=true)  
図7 図4の濃度ヒストグラム

図4の濃度値は次に示す図8より，最小値が0，最大値が255となり，ダイナミックレンジが拡大されていることが確認できる．

![原画像](https://github.com/ReoOgawa/Image-processing-Report/blob/master/Image/Report-07/002.PNG?raw=true)  
図8 図4の最大・最小濃度値
