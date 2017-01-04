# 課題１０レポート　画像のエッジ抽出
##### 次のプログラムを参考にして，エッジ抽出を体験せよ．
標準画像「sun」を原画像とする．この画像は縦684画像，横550画素による正方形のディジタルカラー画像である．

ORG=imread('sun.jpg');  
ORG= rgb2gray(ORG);  
imagesc(ORG); colormap(gray); colorbar;

によって，原画像を読み込み，白黒濃淡画像へ変換し，表示した結果を図１に示す．

![原画像](https://github.com/ReoOgawa/Image-processing-Report/blob/master/Image/Report-10/01.png?raw=true)  
図1 原画像


IMG = edge(ORG,'prewitt'); % エッジ抽出（プレウィット法）
imagesc(IMG); colormap('gray'); colorbar;

によって，プレウィット法によるエッジ抽出を行い，結果を図2に示す．

![原画像](https://github.com/ReoOgawa/Image-processing-Report/blob/master/Image/Report-10/02.png?raw=true)  
図2 プレウィット法によるエッジ抽出画像


IMG = edge(ORG,'sobel'); % エッジ抽出（ソベル法）
imagesc(IMG); colormap('gray'); colorbar;  

によって，ソベル法によるエッジ抽出を行い，結果を図3に示す．

![原画像](https://github.com/ReoOgawa/Image-processing-Report/blob/master/Image/Report-10/03.png?raw=true)  
図3 ソベル法によるエッジ抽出画像

IMG = edge(ORG,'canny'); % エッジ抽出（キャニー法）
imagesc(IMG); colormap('gray'); colorbar;% 画像表示

によって，キャニー法によるエッジ抽出を行い，結果を図4に示す．

![原画像](https://github.com/ReoOgawa/Image-processing-Report/blob/master/Image/Report-10/04.png?raw=true)  
図4 キャニー法によるエッジ抽出画像

プレウィット法は3画素ずつを対にして濃度の変化点を抽出する処理である．  
ソベル法はプレウィット法のオペレータにおいて，中心画素の影響を強調した処理である．  
図2,3よりソベル法はプレウィット法から派生した処理ということもあり，抽出画像は近い結果となっている．  
そしてキャニー法は注目する画素に各種の濃度変化パターンを当てはめ，最も大きい出力を得るパターンにより，その画素点での濃度勾配の大きさおよび方向を検出するものである．  
図4は図2,3と比べ，より特徴を詳細に抽出していることが確認できる．
