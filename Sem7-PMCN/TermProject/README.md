## Measurement of QoS of Real-time Video Transmissions

### Running the code

####To start the mininet network

    sudo ./run.sh
    
This creates the network with the butterfly topology and also the bandwidths of the links and queue sizes at the switches are set.

-----------------------------------------------------------------------------------------------------------------------

####Opening terminals for individual hosts in the virtual network

    xterm h1 h2 h3 h4
    
This creates xterm for each host present in the network.

-----------------------------------------------------------------------------------------------------------------------

####Streaming a video from host "h1" to host "h2"

  In the terminal of host h1, start vlc using the command
  
    vlc-wrapper &
    
  Now stream any video using RTP/MPEG Transport stream present in VLC. In the address field during streaming, use the IP address of the host h2 (10.0.0.2).
  
  In the terminal of host h2,
  
  To receive the stream 
    
    vlc-wrapper -vvv rtp://10.0.0.2:5004
    
  To save the stream to a file
  
    vlc-wrapper -vvv rtp://10.0.0.2:5004 --sout=file/ts:my_video.mp4
  
-----------------------------------------------------------------------------------------------------------------------


####Non real-time flow creation from host h1 to h2

  In the terminal of host h1,
  
    sudo service apache2 restart
    
  Suppose "file.tar.gz" is located in the host h1 (in the "www" directory) which is to be received.
  
  In the terminal of host h2,
    
    wget 10.0.0.1/file.tar.gz
  

-----------------------------------------------------------------------------------------------------------------------


####Monitoring buffer occupancy during a transmission

  Before starting the transmission between the hosts, start monitoring from the main terminal using the command
  
    sudo ./monitor.sh EXPERIMENT_NAME
    
  After the transmission is complete, stop monitoring and to plot the buffer occupancy diagram, use this command
    
    sudo ./plot_figures.sh EXPERIMENT_NAME
  
  A buffer occupancy plot is created for the monitored time, with "EXPERIMENT_NAME" present in its file name.
  
-----------------------------------------------------------------------------------------------------------------------

