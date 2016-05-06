# TPG
import RPi.GPIO as GPIO
import time
import pygame
#TRIG = 11
#ECHO = 7
#LED = 35 

#TRIG = 13
#ECHO = 12 
#LED = 37

#TRIG = 16 
#ECHO = 15
#LED = 40

#TRIG = 29
#ECHO = 22 
#LED = 38
GPIO.setwarnings(False)
GPIO.setmode(GPIO.BOARD)

GPIO.setup(11, GPIO.OUT)
GPIO.setup(7, GPIO.IN)
GPIO.setup(35, GPIO.OUT)

GPIO.setup(13, GPIO.OUT)
GPIO.setup(12, GPIO.IN)
GPIO.setup(37, GPIO.OUT)

GPIO.setup(16, GPIO.OUT)
GPIO.setup(15, GPIO.IN)
GPIO.setup(40, GPIO.OUT)

GPIO.setup(29, GPIO.OUT)
GPIO.setup(22, GPIO.IN)
GPIO.setup(38, GPIO.OUT)

GPIO.setup(24, GPIO.OUT)
GPIO.setup(26, GPIO.IN)


e=4
r=15
while True:
    a=0
    b=0
    c=0
    d=0
    f=0
    for i in range(5):
        GPIO.output(11, False)
        time.sleep(0.1)
        GPIO.output(11, True)
        time.sleep(0.01)
        GPIO.output(11, False)
        while GPIO.input(7)==0:
          pulse_start = time.time()
        
        while GPIO.input(7)==1:
          pulse_end = time.time()
      
        pulse_duration = pulse_end - pulse_start
        distance = pulse_duration * 17150
        distance = round(distance, 2)
        print "Parking 1:",distance,"cm"
        if distance < r :
                
                a=a+1
        print "A:",a,"number" 

    for i in range(5):
        GPIO.output(13, False)
        time.sleep(0.1)
        GPIO.output(13, True)
        time.sleep(0.01)
        GPIO.output(13, False)
        while GPIO.input(12)==0:
          pulse_start1 = time.time()
        
        while GPIO.input(12)==1:
          pulse_end1 = time.time()
        
        pulse_duration1 = pulse_end1 - pulse_start1
        distance1 = pulse_duration1 * 17150
        distance1 = round(distance1, 2)
        print "Praking 2:",distance1,"cm"
        if distance1 < r:
                
                b=b+1
        print "B:",b,"number" 
       
    for i in range(5):
        GPIO.output(16, False)
        time.sleep(0.1)
        GPIO.output(16, True)
        time.sleep(0.01)
        GPIO.output(16, False)
        while GPIO.input(15)==0:
          pulse_start2 = time.time()
        
        while GPIO.input(15)==1:
          pulse_end2 = time.time()
        
        pulse_duration2 = pulse_end2 - pulse_start2
        distance2 = pulse_duration2 * 17150
        distance2 = round(distance2, 2)
        print "Parking 3:",distance2,"cm"
        if distance2 < r:
                
                c=c+1
        print "C:",c,"number"   
    for i in range(5):
        GPIO.output(29, False)
        time.sleep(0.1)
        GPIO.output(29, True)
        time.sleep(0.01)
        GPIO.output(29, False)
        while GPIO.input(22)==0:
          pulse_start3 = time.time()
        
        while GPIO.input(22)==1:
          pulse_end3 = time.time()
        
        pulse_duration3 = pulse_end3 - pulse_start3
        distance3 = pulse_duration3 * 17150
        distance3 = round(distance3, 2)
        print "Parking 4:",distance3,"cm"
        if distance3 < r:
                d=d+1
        print "D:",d,"number"
    for i in range(5):
        GPIO.output(24, False)
        time.sleep(0.1)
        GPIO.output(24, True)
        time.sleep(0.01)
        GPIO.output(24, False)
        while GPIO.input(26)==0:
          pulse_start4 = time.time()
        
        while GPIO.input(26)==1:
          pulse_end4 = time.time()
        
        pulse_duration4 = pulse_end4 - pulse_start4
        distance4 = pulse_duration4 * 17150
        distance4 = round(distance4, 2)
        print "Gate:",distance4,"cm"
        if distance4 < r:
                f=f+1
        print "F:",f,"number"         
    for j in range (3):
                if a>e:
                   GPIO.output(35,True)
                   time.sleep(2)
                else:
                   GPIO.output(35,False)
                if b>e:
                   GPIO.output(37,True)
                   time.sleep(2)
                else:
                   GPIO.output(37,False)
                if c>e:
                   GPIO.output(40,True)
                   time.sleep(2)
                else:
                   GPIO.output(40,False)
                if d>e:
                   GPIO.output(38,True)
                   time.sleep(2)
                else:
                   GPIO.output(38,False)
                if f>e:
                    print "someone parked in front of the gate"
                    pygame.mixer.init()
                    pygame.mixer.music.load('/home/pi/Desktop/vv.mp3')
                    pygame.mixer.music.play()
                    while pygame.mixer.music.get_busy()==True:
                        continue


