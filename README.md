# tulgu
Пустой файл для лабораторной работы по компьютерному зрению.
Необходимо запустить пустой блан через https://mybinder.org/
Подгрузить библиотеку OpenCV

> pip install opencv-python-headless==4.1.2.30
> pip install opencv-python

Проверить, что библиотека подгрузилась

> import cv2 as cv
> print( cv.__version__ )

Запустить программу по распознаванию цвета, предварительно загрузив нужную картинку:

# Определяем красный картинка
>import cv2
>import numpy as np
>
>img=cv2.imread('cat.jpg')
>hsv = cv2.cvtColor(img,cv2.COLOR_BGR2HSV)
> 
>
>rl=np.array([136,87,111],np.uint8)
>ru=np.array([180,255,255],np.uint8)
>
>red=cv2.inRange(hsv, rl, ru)
>
>kernal = np.ones((5 ,5), "uint8")
>
>red=cv2.dilate(red, kernal)
>res=cv2.bitwise_and(img, img, mask = red)
>
>contours,hierarchy=cv2.findContours(red,cv2.RETR_TREE,cv2.CHAIN_APPROX_SIMPLE)
>
>for pic, contour in enumerate(contours):
>    area = cv2.contourArea(contour)
>    if(area>300):
>
>        x,y,w,h = cv2.boundingRect(contour)
>        img = cv2.rectangle(img,(x,y),(x+w,y+h),(255,255,255),2)
>        cv2.putText(img,"RED ",(x,y),cv2.FONT_HERSHEY_SIMPLEX, 0.7, (0,0,255))
>
>
>isWritten = cv2.imwrite('image1.png', img)
>
>if isWritten:
>    print('Image is successfully saved as file.')

