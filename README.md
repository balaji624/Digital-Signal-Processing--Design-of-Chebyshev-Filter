## Digital-Signal-Processing--Design-of-Chebyshev-Filter
## AIM:
To design of 2nd order Low Pass Chebyshev Filter using using Bilinear Transformation 
## SOFTWARE REQUIRED: 
MAT LAB R2012
## ALGORITHM: 
Step 1: Open MAT LAB. Write the program. 

Step 2: Read the values of Ap,As,Pass band frequency,Stop band frequency.

Step 3: Initialise some conditions to find out the order (N) value.

Step 4: Find out the transfer function of the filter and magnitude of that filter. 

Step 5: Plot the magnitude spectrum with x-label and y-label with suitable title. 

Step 6: Terminate the program. 

## PROGRAM:
```
%Balaji v 212223050008

clc
clear all
close all

Ap = 0.707;
As = 0.3;
wp = pi/2;
ws = 3*pi/4;
T = 0.25;

omega_p=(2/T)*tan(wp/2);
omega_s=(2/T)*tan(ws/2);
alpha_p=-20*log10(Ap);
alpha_s=-20*log10(As);

[N wc]=cheb1ord(omega_p,omega_s,alpha_p,alpha_s,'s');
[num,den]=cheby1(N,alpha_p,1,'s');
display('normalised transfer function');
hs=tf(num,den);
[num1,den1]=cheby1(N,alpha_p,wc,'s');
display('unnormalised transfer function');
hs1=tf(num1,den1);
[numz,denz]=bilinear(num1,den1,1/T);
hz=tf(numz,denz,T);
display('digital transfer function');
w=0:pi/16:pi;
y=freqz(numz,denz,w);

%MAGNITUDE SPECTRUM
y1=abs(y);
plot(w,y1);
xlabel('frequency');
ylabel('magnitude');
title('magnitude response chebyshev lpf:');
```

## OUTPUT:
<img width="1919" height="1017" alt="image" src="https://github.com/user-attachments/assets/5d8f824a-67f7-4602-96c5-c9f4fefd8fa2" />


## RESULT:
![IMG_20260406_194138](https://github.com/user-attachments/assets/a7cb5a62-05b2-4489-8c2a-38c478852fea)



