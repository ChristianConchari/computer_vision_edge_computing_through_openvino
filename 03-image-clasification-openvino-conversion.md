Execute the following command to convert the model to IR format:
```
mo --use_legacy_frontend --saved_model_dir /intel_image_cnn --input_shape=[1,150,150,3]  
```
The model will be converted to IR format and saved in the current directory. 
