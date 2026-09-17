# AIM:
To implement error control coding schemes with linear block codes using MATLAB.

# SOFTWARE REQUIRED: 
  MATLAB

# PROGRAM:
# ERROR CODING
# ENCODING:
clc;

close all;

n = 7;

k = 4;

msg = [1 0 0 1;
       1 0 1 0;
       1 0 1 1];
       
code = encode(msg, n, k, 'cyclic');

msg

code

# ENCODING OUTPUT:
<img width="473" height="322" alt="image" src="https://github.com/user-attachments/assets/571bb5be-3842-4bed-b021-54a948745bd4" />


# DECODING PROGRAM:
clc;

clear all;

close all;

q = 3;

n = 2^q - 1;

k = n - q;

parmat = hammgen(q);

trt = syndtable(parmat);

recd = [1 0 1 1 1 1 0];

syndrome = rem(recd * parmat', 2);

syndrome_de = bi2de(syndrome, 'left-msb');

disp(['syndrome = ', num2str(syndrome_de), ' (decimal) ', ...
      num2str(syndrome), ' (binary)']);

corrvect = trt(1 + syndrome_de, :);

correctedcode = rem(corrvect + recd, 2);

parmat

corrvect

correctedcode

# DECODING OUTPUT:
<img width="415" height="267" alt="image" src="https://github.com/user-attachments/assets/4bdf9c3c-b276-49f9-a531-421f214b671b" />


# RESULT:
Thus encoding and decoding of block codes are performed using MATLAB.
