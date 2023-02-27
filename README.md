# Project Name: Fake Task Detection using Traditional Machine Learning Models and GAN
Introduction
In this project, we trained two traditional machine learning models, Random Forest and AdaBoost, to detect fake tasks using an existing dataset that contains both real and fake tasks. We then used a GAN neural network to generate fake tasks, mixed them with the original dataset, and tested the performance of the two trained models. Finally, we used the discriminator of the GAN network as a first layer detector of the generated fake tasks to evaluate the impact on the performance of the traditional machine learning models.

# Data and EDA
We read the provided data, which is called "MCSDatasetNEXTCONLab," and split it into training and testing datasets. We removed the ID column from the data, and since the training dataset was not balanced, we used an oversampling technique to balance it.
  - Before OverSampling VS After OverSampling 
  ![image](https://user-images.githubusercontent.com/55872010/221592408-8787e747-5200-48fd-b1e7-689278e7dc28.png) ![image](https://user-images.githubusercontent.com/55872010/221592674-0bf5d349-7474-452e-8225-cf8e7540dd05.png)


# Building ML models
We built two classifiers, Random Forest and AdaBoost, and trained them on the original testing dataset without any generated samples by GAN. The Random Forest classifier performed better than AdaBoost, as shown in the following figure.
![image](https://user-images.githubusercontent.com/55872010/221594271-d0136ddb-5b38-43a8-ac45-c3115483424d.png)

# GAN
Before building the Generator or Discriminator, we scaled the data to improve the model's performance. We built the Generator and Discriminator models using code and combined them to build the GAN model. Finally, we trained the GAN model to generate new fake data.

# Generate Fake Data
We generated fake data using the trained Generator model, and then applied reverse transforming to transform the scaled data to the real data.

# Test Random Forest and AdaBoost models on Mixed data
We mixed the generated fake data with the original testing dataset, and tested the performance of the Random Forest and AdaBoost models. The Random Forest model performed better than AdaBoost, as shown in the figure below.
![image](https://user-images.githubusercontent.com/55872010/221594779-7e985105-0018-4d9c-8b40-e894ed83311e.png)

# Cascaded Framework
We used the discriminator as a first filtering layer, where only the samples classified as real passed to the second layer to be tested again on the Random Forest and AdaBoost models. The Random Forest model performed better than AdaBoost.
![image](https://user-images.githubusercontent.com/55872010/221595143-fe0e19cf-fb40-4d51-8271-7b7132277897.png)

# Conclusion
In conclusion, the traditional machine learning models, Random Forest and AdaBoost, performed well in identifying the fake tasks in the original dataset. However, when we generated fake data and mixed it with the testing dataset, the performance of the two models decreased, indicating that the GAN generated data was close to the real data. When we used the discriminator as a first layer classifier, the performance of the two models also decreased, suggesting that the discriminator classified some samples incorrectly, which means that the discriminator is not as good as generator in doing its job, so in future its suggested to enhance the GAN model by enhancing the performance of the discriminator. Overall, the Random Forest classifier had better performance in classifying the fake tasks.

# Contribution
This project is open for contributions. If you would like to contribute, please follow these steps:

    1- Fork the repository
    2- Create a new branch for your changes
    3- Make your changes and commit them with a descriptive message
    4- Push your changes to your forked repository
    5- Create a pull request to merge your changes into the main branch of this repository
We welcome any contributions including bug fixes, new features, improvements to the existing code, documentation, and examples.

By contributing to this project, you agree to license your contributions under the Apache License 2.0. Please make sure that all contributions comply with the license.
