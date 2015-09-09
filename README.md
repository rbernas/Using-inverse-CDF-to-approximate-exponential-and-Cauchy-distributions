# Using-inverse-CDF-to-approximate-exponential-and-Cauchy-distributions

%Part 1: Exponential inverse

clear all;


n = 1000; %number of samples
x = zeros(n,1); %initializing of x, the inverse CDF
u = rand(n,1); %samples from the uniform distribution

x = expinv(u, 5); %the inverse CDF of the exponential distribution using samples from the uniform distribution
hist(x); %creatinon of histogram
xlabel('Values of the inverse exponential with lambda = 5');
ylabel('# of Occurrences');
title('Histogram of inverse exponential with lambda = 5');

%separating values of x into 5 equal bins, each with probability 0.2
A = find(x <= expinv(0.2, 5));
B = find(expinv(0.2, 5) < x & x <= expinv(0.4, 5));
C = find(expinv(0.4, 5) < x & x <= expinv(0.6, 5));
D = find(expinv(0.6, 5) < x & x <= expinv(0.8, 5));
E = find(expinv(0.8, 5) < x & x <= expinv(1.0, 5));

%finding the number of values per each bin
length_A = length(A);
length_B = length(B);
length_C = length(C);
length_D = length(D);
length_E = length(E);


E_i = 200; %expected value
%the expected value = 200 per each bin because if we have a total of 1000
%samples, and we separate into 5 equal bins, each with probability 0.2,
%each bin will have 200 number of samples

%calculation of chi_squared
chi_squared = ((length_A - E_i)/(E_i))^2 + ((length_B - E_i)/(E_i))^2 + ((length_C - E_i)/(E_i))^2 + ((length_D - E_i)/(E_i))^2 + ((length_E - E_i)/(E_i))^2

%calculaion of absolute value of chi
chi_abs =  abs(((length_A - E_i)/(E_i))) + abs(((length_B - E_i)/(E_i))) + abs(((length_C - E_i)/(E_i))) + abs(((length_D - E_i)/(E_i))) + abs(((length_E - E_i)/(E_i))) 
