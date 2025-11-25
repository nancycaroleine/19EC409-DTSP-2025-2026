# EXP 1 A : COMPUTATION OF DFT USING DIRECT AND FFT

# AIM: 

# To Obtain DFT and FFT of a given sequence in SCILAB. 

# APPARATUS REQUIRED: 
PC installed with SCILAB. 

# PROGRAM: 
## DIRECT DFT
```
clc;
clear;

xn = input("Enter the sequence in square brackets [ ] : ");

n1 = 0:1:length(xn)-1;


subplot(3,1,1);
plot2d3(n1, xn);
xlabel('Time n');
ylabel('Amplitude xn');
title('Input Sequence');

j = %i;
N = length(xn);
Xk = zeros(1, N);

for k = 0:N-1
    for n = 0:N-1
        Xk(k+1) = Xk(k+1) + xn(n+1) * exp((-j*2*%pi*k*n)/N);
    end
end

disp("DFT Values (Xk):");
for k = 1:N
    realPart = real(Xk(k));
    imagPart = imag(Xk(k));
    
    if abs(imagPart) < 1e-10 then
        printf("%d", round(realPart));
    elseif imagPart > 0 then
        printf("%d+%dj", round(realPart), round(imagPart));
    else
        printf("%d%dj", round(realPart), round(imagPart));
    end
    
    if k < N then
        printf(" , ");
    else
        printf("\n");
    end
end

K1 = 0:1:length(Xk)-1;

magnitude = abs(Xk);
subplot(3,1,2);
plot2d3(K1, magnitude);
xlabel('frequency (Hz)');
ylabel('magnitude (gain)');
title('Magnitude Spectrum');

angle = atan(imag(Xk), real(Xk));
subplot(3,1,3);
plot2d3(K1, angle);
xlabel('frequency (Hz)');
ylabel('Phase');
title('Phase Spectrum');
```

## FFT
```
clc;
clear;

xn = input("Enter the sequence in square brackets [ ] : ");

n1 = 0:1:length(xn)-1;


subplot(3,1,1);
plot2d3(n1, xn);
xlabel('Time n');
ylabel('Amplitude xn');
title('Input Sequence');

j = %i;
N = length(xn);
Xk = zeros(1, N);

for k = 0:N-1
    for n = 0:N-1
        Xk(k+1) = Xk(k+1) + xn(n+1) * exp((-j*2*%pi*k*n)/N);
    end
end

disp("DFT Values (Xk):");
for k = 1:N
    realPart = real(Xk(k));
    imagPart = imag(Xk(k));
    
    if abs(imagPart) < 1e-10 then
        printf("%d", round(realPart));
    elseif imagPart > 0 then
        printf("%d+%dj", round(realPart), round(imagPart));
    else
        printf("%d%dj", round(realPart), round(imagPart));
    end
    
    if k < N then
        printf(" , ");
    else
        printf("\n");
    end
end

K1 = 0:1:length(Xk)-1;

magnitude = abs(Xk);
subplot(3,1,2);
plot2d3(K1, magnitude);
xlabel('frequency (Hz)');
ylabel('magnitude (gain)');
title('Magnitude Spectrum');

angle = atan(imag(Xk), real(Xk));
subplot(3,1,3);
plot2d3(K1, angle);
xlabel('frequency (Hz)');
ylabel('Phase');
title('Phase Spectrum');
```
# OUTPUT: 
## DFT
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/4fa747ad-4ce6-4577-ad55-96f16f28f40c" />
<img width="1920" height="1080" alt="Screenshot (397)" src="https://github.com/user-attachments/assets/df74a19e-0a59-4a6d-86e1-1f3849dd63f4" />

## FFT
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/8475190e-cc6c-4b80-b121-352968232ef0" />
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/40fd6390-3ded-4634-85c1-8ef9316b8377" />

# RESULT: 
Thus DFT using Direct and FFT method is implemented.
