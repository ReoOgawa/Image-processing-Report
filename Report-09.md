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


f=[0,-1,0;-1,5,-1;0,-1,0]; % フィルタの設計
IMG = filter2(f,IMG,'same'); % フィルタの適用
imagesc(IMG); colormap(gray); colorbar; % 画像の表示
