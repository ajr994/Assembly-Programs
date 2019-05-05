# This program computes the first twelve Fibonacci numbers, places them in an array and then prints

      .data
fibs: .word   0 : 12        	# "array" of 12 words to contain Fibonacci values
size: .word  12             	# size of "array" 
      .text
      la   $t0, fibs        	# load address of array
      la   $t5, size        	# load address of size variable
      lw   $t5, 0($t5)      	# load array size
      li   $t2, 1           	# 1 is first and second Fibonacci number
      add.d $f0, $f2, $f4
      sw   $t2, 0($t0)      	# F[0] = 1
      sw   $t2, 4($t0)      	# F[1] = F[0] = 1
      addi $t1, $t5, -2     	# Counter for loop, this will execute (size-2) times
loop: lw   $t3, 0($t0)      	# Get value from array F[n] 
      lw   $t4, 4($t0)      	# Get value from array F[n+1]
      add  $t2, $t3, $t4    	# $t2 = F[n] + F[n+1]
      sw   $t2, 8($t0)      	# Store F[n+2] = F[n] + F[n+1] in array
      addi $t0, $t0, 4      	# increment address of Fibonacci number source
      addi $t1, $t1, -1     	# decrement loop counter
      bgtz $t1, loop        	# repeat if not finished yet.
      la   $a0, fibs        	# first argument for print (array)
      add  $a1, $zero, $t5  	# second argument for print (size)
      jal  print            	# call print routine. 
      li   $v0, 10          	# system call for exit
      syscall               	# exit, note on different OS's this will function differently
		
#########  Routine to print the numbers on one line 

      .data
space:.asciiz  " "          # space to insert between numbers
head: .asciiz "The Fibonacci numbers are:\n"
      .text
print:add  $t0, $zero, $a0  # starting address of array
      add  $t1, $zero, $a1  # initialize loop counter to array size
      la   $a0, head        # load address of print heading
      li   $v0, 4           # specify Print String service
      syscall               # print heading
out:  lw   $a0, 0($t0)      # load Fibonacci number for syscall
      li   $v0, 1           # specify Print Integer service
      syscall               # print Fibonacci number
      la   $a0, space       # load address of spacer for syscall
      li   $v0, 4           # specify Print String service
      syscall               # output string
      addi $t0, $t0, 4      # increment address
      addi $t1, $t1, -1     # decrement loop counter
      bgtz $t1, out         # repeat if not finished
      jr   $ra              # return
