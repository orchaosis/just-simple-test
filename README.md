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
	
	
	mov cx ,0ffffh;
	
	mov SI ,0
ENDLESS:


    
  ; OUT 0a9h , AL
      
      
     ; CALL CONTROL
     ; ADD BL , AL
     ; ADC BH , 0
     ; ADC DX , 0
      
     ;  dec cx 
     ; jz az
     ; da:
     ; az:
     ; CALL DELAY
      
      
     
     ; MOV AL ,1
      ;OUT 0a8h , AL

    
      

     ; jmp endLESS;
     
      ;  ADC adresi 0a9H
      ;  ADC_I adresi ,0a1h
      ;  DAC adresi 0a8h
      
      
      
      OUT 0a9h , AL

      
      XOR DX , DX
      XOR BX, BX 
      
      MOV CX ,  43
      L1:
      
      CALL CONTROL
      
     
      
      ADD BL , AL
      ADC BH , 0
      ADC DX , 0
      
     
     ; CALL DELAY; delay çok küçük olmali
      

      LOOP L1
      
      
      MOV CX ,43
      MOV AX , BX
      
      DIV CX 
      
      OUT 0A8H , AL
      
      

JMP ENDLESS
RET
START ENDP

CONTROL PROC NEAR
     BLOCK:
     
      in al, 0a1h
      test al, 80H
      JNZ BLOCK;
      
       IN AL , 0A9H
     
   RET
CONTROL ENDP
   
   
 
DELAY PROC NEAR
   PUSH CX
   ;MOV CX , 0FFFFH;
   
   ;5
   MOV CX , 06;
     COUNT:
     LOOP COUNT
   POP CX
   RET
DELAY ENDP
   
   
   
CODE    ENDS
        END START



