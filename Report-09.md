# 課題９レポート　メディアンフィルタと先鋭化
##### メディアンフィルターを適用し，ノイズ除去を体験せよ．
標準画像「cat」を原画像とする．この画像は縦1000画像，横1000画素による正方形のディジタルカラー画像である．

ORG=imread('cat.png');  
ORG= rgb2gray(ORG);  
imagesc(ORG); colormap(gray); colorbar;

によって，原画像を読み込み，白黒濃淡画像へ変換し，表示した結果を図１に示す．

![原画像](https://github.com/ReoOgawa/Image-processing-Report/blob/master/Image/Report-09/01.png?raw=true)  
図1 原画像

次にimnoise関数を用いて原画像にノイズを添付する．

ORG = imnoise(ORG,'salt & pepper',0.02); % ノイズ添付
imagesc(ORG); colormap(gray); colorbar;

によって，ノイズが添付された結果を図2に示す．

![原画像](https://github.com/ReoOgawa/Image-processing-Report/blob/master/Image/Report-09/02.png?raw=true)  
図2 ノイズ添付画像


図2に対して，平滑化フィルタを用い雑音除去を行う．

IMG = filter2(fspecial('average',3),ORG); % 平滑化フィルタ
imagesc(IMG); colormap(gray); colorbar;

によって平滑化フィルタで雑音除去された結果を図3に示す．

![原画像](https://github.com/ReoOgawa/Image-processing-Report/blob/master/Image/Report-09/03.png?raw=true)  
図3 平滑化フィルタ雑音除去画像

図3より，平滑化フィルタによる雑音除去では，まだノイズが残っていることが確認できる．図3に対し更にメディアンフィルタで雑音除去を行う．

IMG = medfilt2(ORG,[3 3]); % メディアンフィルタ
imagesc(IMG); colormap(gray); colorbar;  

によって，メディアンフィルタで雑音除去された結果を図4に示す．

![原画像](https://github.com/ReoOgawa/Image-processing-Report/blob/master/Image/Report-09/04.png?raw=true)  
図4 メディアンフィルタ雑音除去画像

図4より，メディアンフィルタによる雑音除去によって，ノイズはほぼ除去されたことが確認できる．

次にフィルタを設計し，適用させる．

f=[0,-1,0;-1,5,-1;0,-1,0]; % フィルタの設計  
IMG = filter2(f,IMG,'same'); % フィルタの適用  
imagesc(IMG); colormap(gray); colorbar;  

設計したフィルタを図5に示す．図5は鮮鋭化フィルタの一つである４近傍ラプラシアンフィルタである．鮮鋭化フィルタとは輪郭部分を検出して強調する事で，画像を鮮鋭化するというものである．


![原画像](https://github.com/ReoOgawa/Image-processing-Report/blob/master/Image/Report-09/fil.png?raw=true)  
図5 設計フィルタ(４近傍ラプラシアンフィルタ)

図5の設計フィルタを適用した結果を図6に示す．

![原画像](https://github.com/ReoOgawa/Image-processing-Report/blob/master/Image/Report-09/05.png?raw=true)  
図6 設計フィルタ雑音除去画像

図6より，設計フィルタを適用したことで，画像が鮮鋭化されたことが確認できる．  
また画像が全体的に灰色となっているのは，画素値がマイナスの値を多く含むためである．画素値の範囲に基づいて色を割り当てているため，おおよそ中間値にあたる灰色が画像に表れていると考えられる．
