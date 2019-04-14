# Help for Scripts

| Parameter Name | Default | Description |
|:---:|:---:|:---:|
|--image_dir|''|Path to folders of labeled images.|
|--output_graph|/tmp/output_graph.pb|Where to save the trained graph.| 
|--intermediate_output_graphs_dir|/tmp/intermediate_graph/|Where to save the intermediate graphs.|
|--intermediate_store_frequency|0|How many steps to store intermediate graph. If "0" then will not store.|
|--output_labels|/tmp/output_labels.txt|Where to save the trained graph\'s labels.|
|--summaries_dir|/tmp/retrain_logs|Where to save summary logs for TensorBoard.|
|--how_many_training_steps|4000|How many training steps to run before ending.|
|--learning_rate|0.01|How large a learning rate to use when training.|
|--testing_percentage|10|What percentage of images to use as a test set.|
|--validation_percentage|10|What percentage of images to use as a validation set.| 
|--eval_step_interval|10|How often to evaluate the training results.|
|--train_batch_size|100|How many images to train on at a time.|
|--test_batch_size|-1|How many images to test on. This test set is only used once, to evaluate the final accuracy of the model after training completes. A value of -1 causes the entire test set to be used, which leads to more stable results across runs.|
|--validation_batch_size|100|How many images to use in an evaluation batch. This validation set is used much more often than the test set, and is an early indicator of how accurate the model is during training. A value of -1 causes the entire validation set to be used, which leads to more stable results across training iterations, but may be slower on large training sets.|
|--print_misclassified_test_images|False|Whether to print out a list of all misclassified test images|
|--bottleneck_dir|/tmp/bottleneck|Path to cache bottleneck layer values as files.|
|--final_tensor_name|final_result|The name of the output classification layer in the retrained graph|
|--flip_left_right|False|Whether to randomly flip half of the training images horizontally.|
|--random_crop|0|A percentage determining how much of a margin to randomly crop off the training images.|
|--random_scale'|0|A percentage determining how much to randomly scale up the size of the training images by.|
|--random_brightness|0|A percentage determining how much to randomly multiply the training image input pixels up or down by.|
|--tfhub_module|https://tfhub.dev/google/imagenet/inception_v3/feature_vector/1')|Which TensorFlow Hub module to use. For more options, search https://tfhub.dev for image feature vector modules.|
|--saved_model_dir|''|Where to save the exported graph.|
|--logging_verbosity'|INFO'|How much logging output should be produced: choices=['DEBUG', 'INFO', 'WARN', 'ERROR', 'FATAL']|