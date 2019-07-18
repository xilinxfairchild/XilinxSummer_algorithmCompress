# Xilinx_quantization

When our training is OK, there are two files generated.
For example, float.prototxt and float.caffemodel.

We should convert them to fixed-point type because cost performance of float-point type is lower than that of fixed-point type.
And we choose DNNDK as our tool to finish that requirement.

Assuming that your initial files are float.prototxt and float.caffemodel.

STEP1
locate the position of those files with the command 'cd'.

STEP2
use a series of command of decent to implement quantization.
For more details, you can search for ug1331 and ug1327 in Xilinx official website.

decent     quantize                            
           -model float.prototxt         
           -weights float.caffemodel      
           -output_dir decent_output            
           -method 1 
           
each command has its meaning and you can rewrite your own command with the help of ug1327 and yg1331

Be careful of the command of decent or decent-cpu according to your own environment.




# XilinxSummer_compilation

When our quantization is OK, there are two files generated.
For example, deploy.prototxt and deploy.caffemodel.

We should convert them to '.elf'file for Ultra96 
And we choose DNNDK as our tool to finish that requirement.

Assuming that your initial files are deploy.prototxt and deploy.caffemodel.

STEP1
locate the position of those files with the command 'cd'.

STEP2
use a series of command of decent to implement quantization.
For more details, you can search for ug1331 and ug1327 in Xilinx official website.

dnnc   --prototxt=deploy.prototxt            
       --caffemodel=deploy.caffemodel      
       --output_dir=dnnc_output                  
       --net_name=resnet50                       
       --dpu=4096FA                              
       --mode=debug                             
       --cpu_arch=arm64                         
       --abi=0   
           
each command has its meaning and you can rewrite your own command with the help of ug1327 and yg1331

Be careful of the command of dpu type and you should select the type with the help of your design of hardware. And cpu type depends on your board.
