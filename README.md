# Experiment--04-Implementation-of-combinational-logic-using-universal-gates
    Implementation of combinational logic using universal-gates
 
## AIM:
    To implement the given logic function using NAND and NOR gates and to verify its operation in Quartus using Verilog programming.

    F=((C'.B.A)'(D'.C.A)'(C.B'.A)')' using NAND gate
    F=(((C.B'.A)+(D.C'.A)+(C.B'.A))')' using NOR gate
## Equipments Required:
    Hardware – PCs, Cyclone II , USB flasher
    Software – Quartus prime
## Theory
    Logic gates are electronic circuits which perform logical functions on one or more inputs to produce one output. 
 ### Using NAND gates
      NAND gate is actually a combination of two logic gates i.e. AND gate followed by NOT gate. So its output is complement of the output of an AND gate.This gate can have minimum two inputs, output is always one. By using only NAND gates, we can realize all logic functions: AND, OR, NOT, X-OR, X-NOR, NOR. So this gate is also called as universal gate. First note that the entire expression is inverted and we have three terms ANDed. This means that we must use a 3-input NAND gate. Each of the three terms is, itself, a NAND expression. Finally, negated single terms can be generates with a 2-input NAND gate acting as an inverted.



 ### Using NOR gates
      NOR gate is actually a combination of two logic gates: OR gate followed by NOT gate. So its output is complement of the output of an OR gate. This gate can have minimum two inputs, output is always one. By using only NOR gates, we can realize all logic functions: AND, OR, NOT, Ex-OR, Ex-NOR, NAND. So this gate is also called universal gate. Designing a circuit with NOR gates only uses the same basic techniques as designing a circuit with NAND gates; that is, the application of deMorgan’s theorem. The only difference between NOR gate design and NAND gate design is that the former must eliminate product terms and the later must eliminate sum terms.

## Procedure:
    Compile and run the verilog program in the quartus software.
    Realize the RTL logic for the same.
    Create a new university program vwf and import nodes using node finder.
    Run functional simulation to obtain the timing diagram.
## Program:
    /*
    Program to implement the given logic function using NAND and NOR gates in quartus using Verilog programming.
    Developed by: Preethi M
    RegisterNumber: 22000091 
    */
  ### Using NAND gate:F=((C'.B.A)'(D'.C.A)'(C.B'.A)')'
       module Universal(a,b,c,d,f);
       input a,b,c,d;
       output f;
       wire p1,q1,r1,s1;
       nand(p1,c,c);
       nand(q1,b,a);
       nand(r1,q1,q1);
       nand(s1,p1,r1);
       wire p2,q2,r2,s2;
       nand(p2,d,d);
       nand(q2,c,a);
       nand(r2,q2,q2);
       nand(s2,p2,r2);
       wire p3,q3,r3,s3;
       nand(p3,b,b);
       nand(q3,c,a);
       nand(r3,q3,q3);
       nand(s3,p3,r3);
       wire x,y;
       nand(x,s1,s2);
       nand(y,x,x);
       nand(f,y,s3);
       endmodule
  ### Using NOR gates: F=(((C.B'.A)+(D.C'.A)+(C.B'.A))')'
       module Universal(a,b,c,d,f);
       input a,b,c,d;
       output f;
       wire p1,q1,q11,q12,r1,r11,r12;
       nor(p1,b,b);
       nor(q11,c,c);
       nor(q12,a,a);
       nor(q1,q11,q12);
       nor(r11,p1,p1);
       nor(r12,q1,q1);
       nor(r1,r11,r12);
       wire p2,q2,q21,q22,r2,r21,r22;
       nor(p2,c,c);
       nor(q21,a,a);
       nor(q22,d,d);
       nor(q2,q21,q22);
       nor(r21,p2,p2);
       nor(r22,q2,q2);
       nor(r2,r21,r22);
       wire x,y;
       nor(x,r1,r2);
       nor(y,r1,r2);
       nor(f,x,y);
       endmodule

## RTL realization:

![UniversalNANDrtl](/images/UniversalNANDrtl.png)
![UniversalNORrtl](/images/UniversalNORrtl.png)

## Timing Diagram:

![UniversalNANDsim](/images/UniversalNANDsim.png)
![UniversalNORsim](/images/UniversalNORsim.png)

## Result:
   Thus the given logic functions are implemented using NAND and NOR gates and their operations are verified using Verilog programming.
