# Smart-Traffic-Management-System-using-IoT
Project Summary: Addressing the escalating challenges of road traffic, the IoT-based Smart Traffic Management System emerges as a comprehensive solution. Capable of efficiently managing traffic, it provides dedicated pathways for emergency vehicles like fire brigades and ambulances.
import numpy as np
import cv2

cap = cv2.VideoCapture('Delhi.mp4')

kernel = cv2.getStructuringElement(cv2.MORPH_ELLIPSE,(3,3))
fgbg = cv2.bgsegm.createBackgroundSubtractorGMG()

while(1):
    ret, frame = cap.read()

    fgmask = fgbg.apply(frame)
    fgmask = cv2.morphologyEx(fgmask, cv2.MORPH_OPEN, kernel)

    cv2.imshow('frame',fgmask)
    k = cv2.waitKey(30) & 0xff
    if k == 27:
        break

cap.release()
cv2.destroyAllWindows()
