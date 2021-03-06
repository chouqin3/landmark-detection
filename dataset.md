# Facial Landmark Detection Datasets: 300W-Style and AFLW-Style

300W-Style and AFLW-Style are created based on 300W and AFLW, respectively.
They are introduced in [Style Aggregated Network for Facial Landmark Detection](http://openaccess.thecvf.com/content_cvpr_2018/papers/Dong_Style_Aggregated_Network_CVPR_2018_paper.pdf). In a nutshell, I applied three different style changes (light, gray, sketch) to the original facial images of 300W and AFLW.
Together with the original images, 300W-Style and AFLW-Style have four variants of each image in the original 300W and AFLW. In the same time, each variant share the same annotation for facial landmarks.
They are used to facilitate the analysis for facial landmark detection problem.

### Datasets Download
- Download 300W-Style and AFLW-Style from [Google Drive](https://drive.google.com/open?id=14f2lcJVF6E4kIICd8icUs8UuF3J0Mutd) or [Baidu Yun](https://pan.baidu.com/s/1ZMT321lgl2Em8WR3IMjkNw#list/path=%2F), and extract the downloaded files into `~/datasets/`. Since the tgz files for 300W-Style and AFLW-Style are too large to download, I split them into several small parts in the [`300W-Style-Splits`](https://drive.google.com/open?id=1SXAon0mw040C-nvOd4VFN9RO-t19dX5Y) folder and the [`AFLW-Style-Splits`](https://drive.google.com/open?id=12EtnJPpH7VFRmfEwMKamzurTHaK0j8aJ) folder on Google Drive. You can download all parts and use `cat 300W-Style.tgz.parta* > 300W-Style.tgz` and `cat AFLW-Style.tgz.parta* > AFLW-Style.tgz` to get the original tgz file.
- In 300W-Style and AFLW-Style directories, the `Original` sub-directory contains the original images from [300-W](https://ibug.doc.ic.ac.uk/resources/300-W/) and [AFLW](https://www.tugraz.at/institute/icg/research/team-bischof/lrs/downloads/aflw/)
- The sketch, light, and gray style images are used to analyze the image style variance in facial landmark detection.
- For simplification, we change some file names, such as removing the space or unifying the file extension.

In `cluster.py`, we use ResNet-152 to classify the 4 style class of 300W-Style and AFLW-Style, it obtains 93.5% accuracy (training on 300W-Style and evaluating on AFLW-Style), and 96.6% accuracy (training on AFLW-Style and evaluating on 300W-Style).

If you can't download the datasets via the above link, please try:
```
300W-Style : https://drive.google.com/open?id=1wy9ZUSWE4V2WdMbXS3Jkq7kQEYHSpLk1
AFLW-Style : https://drive.google.com/open?id=1y5JrOd86NGHTPZLYLgeqRJzT2T4ACWJe
```

<img src="cache_data/cache/dataset.jpg" width="480">
Figure 1. Our 300W-Style and AFLW-Style datasets. There are four styles, original, sketch, light, and gray.


##### 300W-Style Directory
`300W-Style.tgz` should be extracted into `~/datasets/300W-Style` by typing `tar xzvf 300W-Style.tgz; mv 300W-Convert 300W-Style`.
It has the following structure:
```
--300W-Gray
 --300W ;  afw  ; helen ; ibug ; lfpw
--300W-Light
 --300W ;  afw  ; helen ; ibug ; lfpw
--300W-Sketch
 --300W ;  afw  ; helen ; ibug ; lfpw
--300W-Original
 --300W ;  afw  ; helen ; ibug ; lfpw
--Bounding_Boxes
 --*.mat
```

##### AFLW-Style Directory
`AFLW-Style.tgz` should be extracted into `~/datasets/AFLW-Style` by typing `tar xzvf AFLW-Style.tgz; mv AFLW-Convert AFLW-Style`.
It has the following structure (`annotation` is generated by `python aflw_from_mat.py`):
```
--aflw-Gray
  --0 2 3
--aflw-Light
  --0 2 3
--aflw-Sketch
  --0 2 3
--aflw-Original
  --0 2 3
--annotation
  --0 2 3
```


## Citation
If these two datasets help your research, please cite the following papers:
```
@inproceedings{dong2018san,
   title={Style Aggregated Network for Facial Landmark Detection},
   author={Dong, Xuanyi and Yan, Yan and Ouyang, Wanli and Yang, Yi},
   booktitle={Proceedings of the IEEE Conference on Computer Vision and Pattern Recognition (CVPR)},
   pages={379--388},
   doi={10.1109/CVPR.2018.00047},
   year={2018}
}
```
