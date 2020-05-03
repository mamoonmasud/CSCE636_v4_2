# CSCE636_v4_2
GitHub repo containing the codes for the final submission of the Action Recognition Project (Dense Net Architecture)  
These files are part of the course project for the Course CSCE 636 : Deep Learning by Dr. Anxiao Jiang Final Submission:


The dataset for this submission was the same as the previous one, and more focus was on improving the model, increasing the accuracy and decreasing the validation and training loss. The first task was to improve on the same architecture as the previous one, varying the hyper-parameters, and tuning the model architecture. 
For the Long-term Recurrent Convolutional Network (LRCN) architecture (as in the previous submission), the LSTM layer was exchanged with a Gated Recurrent Unit (GRU), and the learning units for the layer were also increased from 128 to 256, as well as the neurons in the dense layers proceeding the GRU layers. This, however, resulted in lower performance on metrics, and the validation accuracy was 76%, down from 84% in the earlier case. With LRCN, the advantage is that we did end-to-end training, but since we took only 15 frames per video, we were not able to incorporate the entire temporal range. The stunted temporal range problem can be compensated by using longer clips, but we are limited due to memory and computational constraints.
 
Architecture
For this submission, different architectures were tried, but the best results were achieved for Temporal 3D Convolutional Networks [5]. This architecture employs transfer learning as well as extends the work from I3D. Diba et.al [5] have devised a new technique for supervising transfer learning between pre-trained 2D ConvNet architecture and Temporal 3D ConvNet. The 2D pre-trained network & the temporal 3D network are both presented frames from the videos, however, the frames could be from the same or different videos. If the architecture is presented with clips from the same video, it is trained to predict the class, while if it is presented with the frames from different videos, it is trained to predict the error. 
 
Figure 1: The architecture for knowledge transfer from pre-trained 2D Conv-Net to 3D Conv-Net. [5]

Our architecture uses pretrained Dense Net for this purpose. This architecture has a Temporal Transition Layer (TTL)/Temporal Pooling Layer stacked after the Dense Layers in the I3D model. This enables in capturing the different temporal depths. Multi-depth pooling is achieved by pooling with kernels of varying temporal sizes. 

Model Weights are shared over Google Drive as they are larger than 25mb
