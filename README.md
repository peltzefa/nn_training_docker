# Training Tensorflow inside Docker to classify pictures
This repo contains all the necessary scripts and information to train an image classification Tensorflow model.

## Teavanist approach
*Tested on Win10 Professional with Tensorflow v. 1.13.1

Thanks to [teavanist (Medium)](https://medium.com/@teavanist/image-classification-using-tensorflow-on-docker-windows-bd7824b05fee)  

### Filesystem
```bash
├───data
│   ├───bear
│   │       001bear.jpg
│   │       ...
│   │
│   └───cat
│           001cat.jpg
│           ...
└───scripts
        label_image.py
        retrain.py
        testimage1.jpg
        ...
```
INFO: The image classes are created from sub folders of the data folder. Example: bear and cat.
1. create folders for every class (name of folder is the label)
2. put images of the class inside them 

That's it.

### Get Docker container

- start container ```docker run -it tensorflow/tensorflow:<version|1.13.1> /bin/bash```
- copy files to container ```docker cp <file path> <container_id>:/image_classification```

### In container
- install the lib that is needed for the retrain.py script: ```pip install tensorflow_hub```
- train: ```python scripts/retrain.py --bottleneck_dir=/bottleneck/ --model_dir=/inception --output_labels=/retrained_labels.txt --output_graph=/retrained_graph.pb --image_dir=data/```
- test: ```python scripts/label_image.py --graph=/retrained_graph.pb --labels=/retrained_labels.txt --input_layer=Placeholder --output_layer=final_result --image=/image_classification/newTrainer/testimage1.jpg```

### Get model and labels from Docker container
- copy files ```docker cp . <container_id>:/retrained_graph.pb``` and ```docker cp . <container_id>:/retrained_labels.txt```
- the logs for TensorBoard are stored under **/tmp/retrain_logs/** (copy them to the host system or forward the TensorBoard port to the host system using the docker argument **-p 6006:6006**)

## TODOs
- [ ] create new Dockerfile  
- [ ] create scripts to start training and testing inside the Docker container  
- [ ] create script to start Docker container with TensorBoard port forwarding