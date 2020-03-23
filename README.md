# EmptyShelfModel
A Convolutional Neural Network that orders images into 1 of 2 categories:
1. Empty Shelf
2. Full Shelf

## Example:
Examples in ./data

Notice these are tested in the last 2 cells of the Jupyter Notebook

## Why
Over the last few weeks, I've seen an enormous number of posts on social media of empty shelves at the grocery store.
Most of the time these are pictures of 1 or 2 empty shelves in an otherwise fully stocked store. While I understand these pictures can be informative, usually, I think these images induce unnecessary panic buying.

If you need proof of this, look no further than the ridiculous hoarding of toilet paper. I wondered how difficult it would be for social media companies to detect if an image depicted an empty shelf before the user posted it, and if so, kindly suggest that they reconsider.
My goal was to make a machine learning model that could act as a proof-of-concept for that vision.
I was so excited to jump on this task as I'm currently self-quarantining and exercising some of my rusty machine learning alg knowledge is better than re-watching The Office for the 6th time.

## Techical details
Using Keras, I wrote a CNN with 2 layers and an output layer. I originally wanted to go with a VGG16 architecture, but after thinking more about the problem I realized that was overkill.
Instead, I removed one of the convoluntional layers but kept the same format:

    Image
      ↓
    Convolutional Layer
      ↓
    Max Pooling
      ↓
    Convolutional Layer
      ↓
    Max Pooling
      ↓
    Flatten
      ↓
    Dense 
      ↓
    Dense
      ↓
    Classification

Although I designed and trained my own model, I found lots of help on Keras specifics from a blog post found [here](https://blog.keras.io/building-powerful-image-classification-models-using-very-little-data.html).
### Number of Images
Finding and obtaining a decent number of images was my main concern. I used a chrome extention to download every available image on google that matched my search, 'Empty shelves grocery store'. Then I hand picked the ones I thought were appropriate for the model.
I rinse and repeated this process to find the images of full shelves. In the end, I only ended up with about ~800 pictures of empty and full shelves.

I orignally wanted to also add in images of other things like: selfies, pets, screenshots, ... Other things people post on social media but theres a problem with this approach. In order for the model to learn the difference between a 'full shelf', an 'empty shelf', and 'Everything else' I would have way more 'Not empty shelf' images. The problem is I could only get my hands on ~450 images of empty shelves. In order to get the best accuracy, I changed the scope of the project (I know, I know, shame on me).

## Results
The results seemed fantastic (~94%) for my admittedly small train and validation data. If you notice, I also test 2 hidden sanity images that aren't part of training or testing data.
The overwhelming trend is that, the higher the epoch, the better the accuracy. Although in some cases, later epochs had worse accuracy than earlier ones.

## Limitations
There are some limitations to this model, including:
1.	There are other pictures that induce panic-buying that aren't captured by this model like, for example, long lines at the grocery store.
2.	I only trained the model to tell the difference between a stocked shelf and an empty shelf.
3.	Due to the lack of images, I worry the model is overfitting the data.
