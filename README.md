# own-haar-cascade-for-object-detection
to detect object you can build your own haar cascade 


for run this project you need to follow some steps

1) start server if you use ubuntu then ssh username@hostname
2)clone of opencv you can directly download or use " git clone "https://github.com/Itseez/opencv.git  opencv"
3)run download_image_by_link.py main three function 1)first for get url of images grab them and resize them 2)for negative photos we also need a filter for bad images 3) he last step is we need to create the descriptor file for these negative images

now your project dir looks like this

opencv_workspace
--neg
----negimages.jpg
--opencv
--info
--bg.txt
--pdp.jpg

3)create data folder and run this command "opencv_createsamples -img pdp.jpg -bg bg.txt -info info/info.lst -pngoutput info -maxxangle 0.5 -maxyangle 0.5 -maxzangle 0.5 -num 1950"

4)then for positive vector run "opencv_createsamples -info info/info.lst -num 1950 -w 20 -h 20 -vec positives.vec" command 

and now your project directory look like this
opencv_workspace
--neg
----negimages.jpg
--opencv
--info
--data
--positives.vec --bg.txt
--pdp.jpg

and than run this command "opencv_traincascade -data data -vec positives.vec -bg bg.txt -numPos 1800 -numNeg 900 -numStages 10 -w 20 -h 20"

"nohup opencv_traincascade -data data -vec positives.vec -bg bg.txt -numPos 1800 -numNeg 900 -numStages 10 -w 20 -h 20 &
"
This will allow the command to continue running, even after you close the terminal. You can do more, but you may or may not run out of your 2GB of ram

now run detect_your_object.py 
and that's all it takes too much time just 6 hour yaaa that's true if you are using local server then 
