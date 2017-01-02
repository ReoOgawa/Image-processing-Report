# 課題５レポート　判別分析法
##### 判別分析法を用いて画像二値化せよ．
標準画像「cat」を原画像とする．この画像は縦1000画像，横1000画素による正方形のディジタルカラー画像である．

ORG=imread('cat.png');  
ORG= rgb2gray(ORG);  
imagesc(ORG); colormap(gray); colorbar;

によって，原画像を読み込み，白黒濃淡画像へ変換し，表示した結果を図１に示す．

![原画像](https://github.com/ReoOgawa/Image-processing-Report/blob/master/Image/Report-05/01.png?raw=true)  
図1 原画像

判別分析法とは，分離度が最大となるしきい値を求め，自動的に二値化を行う手法である．  
分離度はクラス間分散とクラス内分散との比で求める事ができ，以下の手順によりクラス間分散とクラス内分散を求め二値化を行い，結果を示す．


H = imhist(ORG); %ヒストグラムのデータを列ベクトルEに格納  
myu_T = mean(H);  
max_val = 0;  
max_thres = 1;  
for i=1:255  
C1 = H(1:i); %ヒストグラムを2つのクラスに分ける  
C2 = H(i+1:256);    
n1 = sum(C1); %画素数の算出   
n2 = sum(C2);  
myu1 = mean(C1); %平均値の算出   
myu2 = mean(C2);     
sigma1 = var(C1); %分散の算出   
sigma2 = var(C2);  
sigma_w = (n1 *sigma1+n2*sigma2)/(n1+n2); %クラス内分散の算出  
sigma_B = (n1 *(myu1-myu_T)^2+n2*(myu2-myu_T)^2)/(n1+n2); %クラス間分散の算出  
if max_val<sigma_B/sigma_w  
max_val = sigma_B/sigma_w;  
max_thres =i;  
end;  
end;  
IMG = ORG > max_thres;  
imagesc(IMG); colormap(gray); colorbar;

![原画像](https://github.com/ReoOgawa/Image-processing-Report/blob/master/Image/Report-05/02.png?raw=true)  
図2 判別分析法を用いた二値化画像

図2より，しきい値を境とした二値の画像となっていることが確認できる．
