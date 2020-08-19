# Model-Pipeline-Template
:rocket: Data pipeline in Tensorflow to load data into binary tfrecords, train a model, and export it as a frozen graph for easy deployment :rocket:

## Steps:
- `python prep_data.py -h`
  - Example Usage: `python prep_data.py --train-val-test-split 0.8,0.15,0.05 --data-dir '/home/michael/hard_drive/datasets/dogs_vs_cats_data/train/' --data-format image --dict-tensor-fn cat_dog_dict_tensor --image-dims 80,80,3`
- `python train_model.py -h`
  - Example Usage: `python train_model.py --clean --num-epochs 5 --start-summary-at 5 --train-batch-size 110 --model-dir cat_dog_cnn_desktop --model-name cnn_model_fn`
  - Example Usage: `python train_model.py --num-epochs 15 --start-summary-at 5 --train-batch-size 110 --model-dir cat_dog_cnn_desktop --model-name cnn_model_fn model_13`
- `python make_predictions.py -h`
  - Example Usage: `python make_predictions.py --graph-dir cat_dog_cnn_desktop --frozen-graph-names model_10,model_12 --test-data-dir '/home/michael/hard_drive/datasets/dogs_vs_cats_data/test' --output-func cat_dog_classifier_output --output-labels id,label`
- `python export_model.py -h`
  - Example Usage: `python export_model.py --graph-dir cat_dog_cnn_desktop --config-file tfrecord_config.json --model-dir cat_dog_cnn_desktop model_4`