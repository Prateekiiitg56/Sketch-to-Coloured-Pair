# Sketch to Colorization using a Conditional GAN

This project uses a conditional Generative Adversarial Network (cGAN) to colorize anime-style sketches. The model architecture is based on the Pix2Pix paper, which is effective for image-to-image translation tasks.

The entire implementation, from data loading to training and inference, is contained within the `sketch-to-colored-image-generation-using-gan-based.ipynb` notebook.

## How it Works

The model learns a mapping from a source image (a black and white sketch) to a target image (a full-color version).

The two main components are:
- **Generator:** A U-Net-based architecture. It takes a sketch as input and generates what it thinks the colored version should be. The U-Net structure allows information to be passed from the early layers (which see fine details) to the later layers.
- **Discriminator:** A PatchGAN-based classifier. Instead of deciding if the *entire* image is real or fake, it looks at smaller patches of the image and classifies each patch. This encourages the generator to produce more realistic details across the whole image.

The generator and discriminator are trained together in an adversarial process. The generator tries to fool the discriminator, and the discriminator tries to get better at catching the fakes.

## Dataset

This was trained using the "Anime Sketch Colorization Pair" dataset, which contains pairs of sketches and their corresponding colored images. The notebook expects the data in a specific format: each image file should be a horizontal concatenation of the colored image on the left and the sketch on the right.

## How to Use

1.  Open the `sketch-to-colored-image-generation-using-gan-based.ipynb` notebook in an environment like Jupyter Lab or VS Code.
2.  Install the necessary Python libraries, primarily `torch`, `torchvision`, `albumentations`, and `matplotlib`.
3.  Before running, you will need to adjust the file paths for the training and validation data to point to where you have the dataset stored locally.
4.  You can then run the cells sequentially to train the model or load a pre-trained model for inference.
