# KMeans via sklearn (Python2)

A clustering example using [sklearn](https://scikit-learn.org/stable/).

If this is your first time using Binaris, visit our [Getting Started](https://dev.binaris.com/tutorials/python/getting-started/) page to set up your account for free.

The function in this project uses kmeans to quantize an input image potentially reducing the number of unique colors greatly. This can allow for greater color compression of the input image or pleasing filter-esque effects.

## Deploying with pip packages

To deploy a Binaris function that depends on `pip` packages we need to rely on the [Bob tool](https://github.com/binaris/bob). Bob is simple script, which greatly reduces the hassle of building platform-specific python packages. This is accomplished by building the dependencies against the same architecture used by Binaris functions, this way you can guarantee your dependencies will work at runtime.

Outlined below are the steps needed to build with Bob and then subsequently deploy your own kmeans functions.

1. Install Bob somewhere accessible 

    ```bash
    git clone https://github.com/binaris/bob.git
    ```

2. Navigate to the "kmeans-sklearn" directory (the same directory this README is in) and run

    ```bash
    /path/to/bob/build.sh 2
    ```

    > Note: The first run of Bob builds a Docker image and may take a while

3. Deploy your function

    ```bash
    bn deploy public_kmeans_image_quant_py2
    ```

As a final note, keep in mind that you only need to run Bob again if you add or remove pip packages. Changes to the function code itself only require another `bn deploy`.

## Try it out

Visit the URL printed by deploy (for `public_kmeans_image_quant_py2`) in your browser and add the image URL you want to run kmeans on.

_Example URL_

ht&#8203;tps://run.binaris.com/v2/run/0123456789/public_kmeans_image_quant_py2?image_url=https://i.imgur.com/DUSZHiX.jpg

 The optional query param `num_colors` can also be used to modify the number of clusters kmeans used to quantify your image.


_Example URL_

ht&#8203;tps://run.binaris.com/v2/run/0123456789/public_kmeans_image_quant_py2?image_url=https://i.imgur.com/DUSZHiX.jpg&num_colors=16

> Note: "0123456789" is merely a placeholder and should be replaced with your personal Binaris account id

### Example output

Below are example before and after images after running the function with `num_colors=2`

_Before_

![before_kmeans](./res/before_kmeans.jpg)

_After_

![before_kmeans](./res/after_kmeans.png)
