# training tensorflow docker image classifier

## teavanist approach
***Tested on Win10 Professional**

Thanks to [teavanist (Medium)](https://medium.com/@teavanist/image-classification-using-tensorflow-on-docker-windows-bd7824b05fee)  

### filesystem
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
### get docker container

- start container ```docker run -it tensorflow/tensorflow /bin/bash```
- copy files to container ```docker cp <File path> <container_id>:/image_classification```

### in container
- ```pip install tensorflow_hub```
- train: ```python scripts/retrain.py --bottleneck_dir=/bottleneck/ --model_dir=/inception --output_labels=/retrained_labels.txt --output_graph=/retrained_graph.pb --image_dir=data/```
- test: ```python scripts/label_image.py --graph=/retrained_graph.pb --labels=/retrained_labels.txt --input_layer=Placeholder --output_layer=final_result --image=/image_classification/newTrainer/testimage1.jpg```

### get model and labels from docker container
- copy files ```docker cp . <container_id>:/retrained_graph.pb``` and ```docker cp . <container_id>:/retrained_labels.txt```

## other projects
- https://github.com/llSourcell/tensorflow_image_classifier does not work anymore