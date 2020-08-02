# Emotion Recognition (Project)
These are the main files in the project:
1. build_dataset.py
This file converts the .csv file data obtained from kaggle into .hdf5 file format
To run: 
     ` python build_dataset.py `
     
2. emotion_vggnet.py
This file contains the main model which is inspired from vggnet

3. train_recognizer.py
This file is the main file which reads from the .hdf5 files in batches and does the training of the model. Total epochs entered is 75, but the use of EpochCheckpoint saves the model every 5 epochs in the datasets/fer2013/outputs or the checkpoints directory. Even the plot is stored there.
To run:
      `python train_recognizer.py --checkpoints checkpoints`        (if you are running it from start)
      `python train_recognizer.py --checkpoints checkpoints --model checkpoints/epoch_30.hdf5 --start-epoch 30`      (if you want to resume training from epoch 30 here)
      
4. test_recognizer.py
Once training is complete, the model is saved as .hdf5 file onto the disk in the checkpoints folder. Then we can evaluate our model performance by running this script
To run:
      `python test_recognizer.py --model checkpoints/epoch_75.hdf5`
      
5. realtime_emotion_detector.py
This is the final fruit of the project which can detect emotions in the webcam captured video or a video file provided by user.
To run:
      `python emotion_detector.py --cascade haarcascade_frontalface_default.xml --model checkpoints/epoch_75.hdf5`
