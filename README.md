# actionrecognition
<h2>Action Recognition using ConvLSTM approach</h2>
![concLSTM](https://github.com/deepu3007/actionrecognition/assets/116485152/38ba0bd4-159a-4b1a-b5d5-f204101baeb6)


<p>
  Trying to implement and checkout or playing with convLSTM for video action recognition. This is my first try and the code is taken from kaggle
</p>
<hr></hr>
<p>
There are some hardware constraints to run this code,  I tried to run on google colab but there was a crash,
  So requesting to use GPU or TPU for running this and i used the HMDB51 dataset and used only some part of
  the dataset for just testing out the code but the computational limitations were there.First I got the rar
  inported into the code then unrar some classes of videos and created a dataset of festures, labels and video_paths/dir
</p>
<hr></hr>
<h3>
  About Dataset
</h3>
<p>
  The dataset that was created by using HMDB51 videos and classes dataset, I took only some classes almost 10 classes and 
  unrar them to get the videos ready and the created dataset consists of 3 columns namely features, label and video_path.
  Coming to features we actually extracted frames from the videos and store them in the features section of the dataset, the
  label is the class of the video that it belongs to. The video path is the directory in which the video is present is th os.
</p>
<hr></hr>
<h3>
  About the Model
</h3>
![convlstm_model_structure_plot](https://github.com/deepu3007/actionrecognition/assets/116485152/8e29cdd5-e4ea-4633-be35-cc1c67d724be)
<p>
  The convLSTM constructed has the following layers and their parameters sequentially

  _________________________________________________________________
 Layer (type)                Output Shape              Param #   
=================================================================
 conv_lstm2d (ConvLSTM2D)    (None, 20, 62, 62, 4)     1024      
                                                                 
 max_pooling3d (MaxPooling3  (None, 20, 31, 31, 4)     0         
 D)                                                              
                                                                 
 time_distributed (TimeDist  (None, 20, 31, 31, 4)     0         
 ributed)                                                        
                                                                 
 conv_lstm2d_1 (ConvLSTM2D)  (None, 20, 29, 29, 8)     3488      
                                                                 
 max_pooling3d_1 (MaxPoolin  (None, 20, 15, 15, 8)     0         
 g3D)                                                            
                                                                 
 time_distributed_1 (TimeDi  (None, 20, 15, 15, 8)     0         
 stributed)                                                      
                                                                 
 conv_lstm2d_2 (ConvLSTM2D)  (None, 20, 13, 13, 14)    11144     
                                                                 
 max_pooling3d_2 (MaxPoolin  (None, 20, 7, 7, 14)      0         
 g3D)                                                            
                                                                 
 time_distributed_2 (TimeDi  (None, 20, 7, 7, 14)      0         
 stributed)                                                      
                                                                 
 conv_lstm2d_3 (ConvLSTM2D)  (None, 20, 5, 5, 16)      17344     
                                                                 
 max_pooling3d_3 (MaxPoolin  (None, 20, 3, 3, 16)      0         
 g3D)                                                            
                                                                 
 flatten (Flatten)           (None, 2880)              0         
                                                                 
 dense (Dense)               (None, 7)                 20167     
                                                                 
=================================================================
Total params: 53167 (207.68 KB)
Trainable params: 53167 (207.68 KB)
Non-trainable params: 0 (0.00 Byte)
</p>


