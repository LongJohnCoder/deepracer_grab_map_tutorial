# deepracer_grab_map_tutorial

### This tutorial teach you how to get the files from RoboMaker to your local machine

1. Start a training from DeepRacer console, select the track you want to grab
2. Goto `CloudWatch > Logs > /aws/robomaker/SimulationJobs`
   
   ![](https://i.imgur.com/6FPDXud.png)
   ![](https://i.imgur.com/VxmATTf.png)

3. Find the log of the current training by `Last Event Time`
   
   ![](https://i.imgur.com/WOHf3KJ.png)

4. Search for the word `world`, and remember the path for the `.world` file
   
   ![](https://i.imgur.com/VUFiMNB.png)

5. Goto `RoboMaker > Simulation jobs` and go into the running job, open the `Terminal`
   
   ![](https://i.imgur.com/3lO084a.png)
   ![](https://i.imgur.com/Odyt4a6.png)

6. In the terminal `cd` into the path you have seen from CloudWatch log, you will see the files you need are inside the directory. Just archive all the files into a tar file e.g. `map.tar`
   
   ![](https://i.imgur.com/BRdnNu8.png)

7. In your local machine, run the command `nc -l -p <port> > map.tar`, this command will listen to the port, and write any incoming data into the file `map.tar` in your machine

   If your machine is behind a router, you may want to set the port forwarding to route any incoming data for that port to your machine
   
   ![](https://i.imgur.com/ivvQzcw.png)

8. Back to the RoboMaker, run the command `nc <your_local_machine_ip> <port> < /path/to/map.tar`

   This command send the tar file, which you have just made, as byte stream to your local machine. Your local machine will receive it by the `nc` command you are running and save it as a file in your local machine
   
   ![](https://i.imgur.com/IEh7DGw.png)

9. After downloading the file into your local machine, simply unzip it and get the files you want
   
   ![](https://i.imgur.com/eqjx81T.png)  

10. Don’t forget to stop the training
