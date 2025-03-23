# Analysis of the Backpropagation algorithm in a Neural Network

A close friend who is a surgeon in Madrid told me about some research they were conducting. We discussed the data science aspect of it: neural networks being used to understand the reasons and consequences of a particular surgery, based on a machine learning model

While trying to explain the insights and processes of neural networks to my friend, I was reminded of my Data Mining course in Chicago during Fall 2023. Professor Vijay K. Gurbani, from whom I learned so much, explained neural networks in such a simple way that it inspired me to revisit the topic and write a series of short articles. The goal is for any non-expert to understand how these neural networks work behind the scenes, and to shed some light for researchers from different fields (not specifically related to data science) who are leveraging neural networks for their research.

First, as a Spaniard and a scientist, I must acknowledge the genius of RAMÓN Y CAJAL, awarded the Nobel Prize in Medicine in 1906 for his research and discovery of neurons. Neural Networks (NN) aim to imitate our brain and the way neurons interact to enable us to think and feel
Among all the neural networks flooding research these days, I pick the FULLY CONNECTED FEEDFORWARD NEURAL NETWORK sometimes referred to as a MULTILAYER PERCEPTRON (MLP).

![image](https://github.com/user-attachments/assets/c38c6819-aa1c-442a-a442-ecdac9cda1ec)

As shown in the image, there are some inputs and one output: the response we need to take from the system. It can be seen as a “black box” if we do not care about what it is inside. But… let’s be brave enough to take a look at it!!

![image](https://github.com/user-attachments/assets/60ad1077-445f-48c1-8e79-1b61c10ce196)

The image showcases the insights of a certain NN with one input, one hidden layer composed of 3 neurons, and the output. The neurons within the hidden layer use the RelU activation function, while the output neuron uses the “sigmoid”. (Refer to some Math documentation to know more about them and others if needed)

Hidden layers, filled with neurons, connected between layers form a system that, guided by activation functions at each neuron and parameters between layers, ultimately produce a determined output through a process called “forward propagation”.

The question now is whether there is any opportunity to improve the behavior of the neural network, or if we must settle for the first attempt at forward propagation. 
**And what about the analysis of the loss?**

Back in 1998, Yann LeCun, Léon Bottou, Yoshua Bengio, Patrick Haffner published the foundational paper “Gradient-Based Learning Applied to Document Recognition", succeeding in applying backpropagation effectively to train Convolutional Neural Networks (CNNs) for tasks such as document recognition. Backpropagation as a concept was introduced in the 1980s by Rumelhart, Hinton, and Williams.

![image](https://github.com/user-attachments/assets/a1286e84-fb3a-4b6f-918a-ad147d3e5e93)

![image](https://github.com/user-attachments/assets/cc114fa5-465f-4d4b-946e-07ba8b680dd7)

![image](https://github.com/user-attachments/assets/d4c6a3a9-cab9-4281-9361-0e1604fde354)

As shown in the images, the goal is to adjust the value of the weights (w), in order to decrease the loss until reaching the minimum value. This is backpropagation. Neural networks are trained through an iterative process, where the weights (w) are recalculated using the gradient of the weights vector at each step.

There is also a parameter in the iterative formula used to calculate the new weights (w): LEARNING RATE. This learning rate allows us to fine-tune the speed of convergence and control the step size of the updates, balancing the risk of overshooting the minimum with the need for efficient progress.

Lastly, upon closely examining the updated weight values, we notice that the learning rate has a similar influence as the loss. The weight values decrease and shrink until they approach the optimum, close to zero.

All these effects are visualized in the example solved within this article; code included in R.

The next question is:  **can we find an optimal learning rate?**

As we conclude this series on neural networks (NN), it is time to fine-tune NN training by optimizing the learning rate. 

In the process of finding the optimal learning rate, we need to balance:
👉 Convergence Speed: A higher learning rate can speed up convergence but risks overshooting the minimum or making the process unstable.
👉 Model Stability: A lower learning rate ensures stability and precise adjustments but may result in slower training.

![Slide1](https://github.com/user-attachments/assets/b1391792-8410-4aed-b03c-a097636ec701)

The base plot found in https://lnkd.in/gDUKV8Jg introduces the method to calculate the specific plot in our NN example

![Slide2](https://github.com/user-attachments/assets/b056d645-43ce-4dd5-b671-46f19d457998)

in the second image, gradually increase the learning rate during the training process and then capture the loss values for each learning rate.

The calculated range (0.5–1.5) aligns with our expectations based on the loss plot. Although 0.5 results in a slow convergence speed, it serves as a starting point for the fine-tuning process up to 1.5. Values above 1.5 show clear instability and should be discarded.

Thanks for Vijay K. Gurbani your support.
















