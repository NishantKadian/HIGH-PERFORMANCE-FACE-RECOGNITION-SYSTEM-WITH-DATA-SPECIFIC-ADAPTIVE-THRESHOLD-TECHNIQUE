# HIGH-PERFORMANCE-FACE-RECOGNITION-SYSTEM-WITH-DATA-SPECIFIC-ADAPTIVE-THRESHOLD-TECHNIQUE
The respository contains the code files of my MS thesis "HIGH PERFORMANCE FACE RECOGNITION SYSTEM WITH DATA  SPECIFIC ADAPTIVE THRESHOLD TECHNIQUE"
Install the Requirements $ pip install -r requirements.txt
For new appraoch of using -L2 distance as similarity score measure  as proposed in the research use the folder "-L2 distance similarity score approach" .It has all the code files.
For old appraoch of using dot product as similarity score measure  as proposed in the research use the folder "Dot product similarity score approach" .It has all the code files.
The following steps will be same for both the appraoches but the code  files are in different folders , so use them accordingly.
Dump embedding
- Use FaceNet (reproduce result in paper)
We used FaceNet(https://github.com/davidsandberg/facenet)  model version 20170512-110547 to generate embedding of color_FERET, LFW and Adience in our experiments. You can find the embeddings under the data repository. We shuffle each dataset for 10 times so that the register orders are different. Then we compute the average accuracy from these 10 experiments.

Download FaceNet model 20170512-110547, unzip, and put in the same directory.
$ python dump_embeddings.py --model 20170512-110547/ [data_dir] Please follow the instruction to set up your dataset directory.
- Use your own deep learning model
Generate features with fixed dimension (e.g 128 or 256) with your chosen model and save them into a csv file with the following format:
   [image_name], [features], [threshold(initial value = 0)], [path_to_image]
You can check the csv file under the data repository for reference
2. Run simulation and evaluation with adaptive threshold (with color_FERET)
Run simulation: If max_compare_num is less than 1, the program will compare the registering embedding with all the embeddings sotred in the simulated database, which is the experiments conducted in our paper. (It will take a lot of time)
$ python simulator_v4_adaptive_thd.py data/color_FERET --max_compare_num 100
Compute average accuracy from 10 experiments
$ python get_avg_accuracy.py result/Simulator_v4_features_color_FERET_v


The code has been taken from the repository https://github.com/ivclab/Online-Face-Recognition-and-Authentication#1-dump-embedding and has been modified according to my requirement.
