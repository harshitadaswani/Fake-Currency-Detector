%clear all;
close all;
Ireal = imread('/MATLAB Drive/100.png'); % Real
Iscaned = imread('/MATLAB Drive/fake3.png'); % scaned

%%//Pre-analysis
hsvImageReal = rgb2hsv(Ireal);
hsvImagescaned = rgb2hsv(Iscaned);
figure;
imshow([hsvImageReal(:,:,1) hsvImageReal(:,:,2) hsvImageReal(:,:,3)]);
title('First pre process');
figure;
imshow([hsvImagescaned(:,:,1) hsvImagescaned(:,:,2) hsvImagescaned(:,:,3)]);
title('Second pre process');

%%//Initial segmentation
croppedImageReal = hsvImageReal(:,90:95,:);
croppedImagescaned = hsvImagescaned(:,93:98,:);
satThresh = 0.4;
valThresh = 0.3;
BWImageReal = (croppedImageReal(:,:,2) > satThresh & croppedImageReal(:,:,3) < valThresh);
figure;
subplot(1,2,1);
imshow(BWImageReal);
title('First Image initial segment');
BWImagescaned = (croppedImagescaned(:,:,2) > satThresh & croppedImagescaned(:,:,3) < valThresh);
subplot(1,2,2);
imshow(BWImagescaned);
title('Second Image initial segment');

%%//Post-process
se = strel('line', 6, 90);
BWImageCloseReal = imclose(BWImageReal, se);
BWImageClosescaned = imclose(BWImagescaned, se);
figure;
subplot(1,2,1);
imshow(BWImageCloseReal);
title('First Image Post Process');
subplot(1,2,2);
imshow(BWImageClosescaned);
title('Second Image Post Process');

%%//Area open the image
figure;
areaopenReal = bwareaopen(BWImageCloseReal, 15);
subplot(1,2,1);
imshow(areaopenReal);
title('First Area Open Image');
subplot(1,2,2);
areaopenscaned = bwareaopen(BWImageClosescaned, 15);
imshow(areaopenscaned);
title('Second Area Open Image');

%//Count how many objects there are
[~,countReal] = bwlabel(areaopenReal);
[~,countscaned] = bwlabel(areaopenscaned);
disp(['The total number of black lines for the real note is: ' num2str(countReal)]);
disp(['The total number of black lines for the scaned note is: ' num2str(countscaned)]);