# just-simple-test
this is optional


;====================================================================
; Main.asm file generated by New Project wizard
;
; Created:   Cum Mar 11 2016
; Processor: 8086
; Compiler:  MASM32
;
; Before starting simulation set Internal Memory Size 
; in the 8086 model properties to 0x10000
;====================================================================
STAK    SEGMENT PARA STACK 'STACK'
        DW 20 DUP(?)
STAK    ENDS

DATA    SEGMENT PARA 'DATA'
MYDAT    DB 20 DUP(0)
DATA    ENDS

CODE    SEGMENT PARA 'CODE'
        ASSUME CS:CODE, DS:DATA, SS:STAK
START PROC
        MOV AX, DATA
	MOV DS, AX
	
	

ENDLESS:


;0adc 0a9h
;0a1h adc_intr

; 0a8h dac

   MOV CX , 20;
   
   XOR BX , BX
   XOR DX,DX
   
   
   COUNT:
   
   CALL READ_ADC
   
   ADD BL , AL
   ADC  BH , 0
   ADC DX , 0
   
   
   
   
   CALL DELAY
   
   LOOP COUNT
   
   
   MOV AX , BX
   
   MOV CX , 20
   
   
   DIV CX
   
   OUT  0a8h , AL
   

JMP ENDLESS



RET
START ENDP


READ_ADC PROC NEAR

   OUT 0a9h , AL
   
   KONTROL:
   
   IN AL , 0A1H
   
   TEST AL , 80H
   JNZ KONTROL
   
   IN AL , 0a9h;

RET 
READ_ADC ENDP


   
 
DELAY PROC NEAR
   push cx
   
   MOV CX , 3;
   L1:
   
   LOOP L1
   pop cx
   ret
DELAY ENDP
   
   
   
CODE    ENDS
        END START
