# <center>GDAL常用命令</center>
### 矢量格式坐标转换
#### 坐标转换
```
ogr2ogr -f  format_name -t_srs EPSG:4326 output.* input.*
```
#### 格式转换
```
ogr2ogr -f  format_name  output.* input.*
```
### 栅格像素深度
```
gdal_translate -ot Byte -of GTiff input.tif output.tif
```
### 栅格无损压缩
```
-co "BIGTIFF=YES"：数据量大的时候可以使用。
gdal_translate -co "COMPRESS=LZW"  -co "BIGTIFF=YES" input.tif output.tif
```
### 栅格重投影
```
gdalwarp -t_srs EPSG:4326 input.tif output.tif
```
### osgb转tif
```
转换软件： DasViewer。输出的栅格数据没有坐标系。
```
```
用gdalwarp工具进一步处理。-s_srs参数设定原始坐标系，-t_srs指定输出数据的坐标系，-srcnodata  -dstnodata 这两个参数用于去掉背景黑色。
gdalwarp -s_srs EPSG:4544 -t_srs EPSG:4326 -srcnodata 0 -dstnodata 255 input.tif output.tif
```
