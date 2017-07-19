# Retrain-Inception
Retraining the final layer of Google's Inception (TensorFlow)


## Step1: Download the pre-trained model and the required scripts.
git clone https://github.com/akashsonth/Retrain-Inception
cd Retrain-Inception


## Step2: Setup the image folder
This step involves setting up the folder structure so that tensorflow can pick up the classes easily. Let’s assume that you want to train 5 new flower types, say “roses”, “tulips”, “dandelions”, “mayflower”, and “marigold”. To create the folder structure,

1. Create one folder for each flower type. The name of the folder will be the name of the class ( in this case, that particular flower).
2. Add all the images of the flowers into its respective folders. Eg; all images of roses go into the “roses” folder.
3. Add all the folders into another parent folder, say, “flowers”.
At the end of this exercise, you will have the following structure:
~/flowers
 
~/flowers/roses/img1.jpg
 
~/flowers/roses/img2.jpg
 
...
 
~/flowers/tulips/tulips_img1.jpg
 
~/flowers/tulips/tulips_img2.jpg
 
~/flowers/tulips/tulips_img3.jpg
 
...

Note: All the images must be in jpg format
 
 
## Step 3: Running the re-training script
python retrain.py --model_dir ./inception --image_dir ~/flowers --output_graph ./output --how_many_training_steps 500


## Step 4: Getting the labels and output file
1. Rename the file named 'output' which is formed after Step 3 to 'output.pb'
2. Copy the file output_lables.txt from tmp folder in root directory to Retrain-Inception directory
3. Rename the copied file in Retrain-Inception to labels.txt


## Step 5: Testing the retrained model
python retrain_model_classifier.py <image_path>
#following is an example of classifying an image present in Pictures directory 
python retrain_model_classifier.py /home/akshay/Pictures/test_image_flower.jpg
 
#following is an example output
 
"""
 
rose ( score=0.78)
 
tulips( score=0.14)
 
others( score =0.02)
