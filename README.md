
# tensorflow-DeepFM

This project includes a Tensorflow implementation of DeepFM [1].

# NEWS
- A modified version of DeepFM is used to win the 4th Place for [Mercari Price Suggestion Challenge on Kaggle](https://www.kaggle.com/c/mercari-price-suggestion-challenge). See the slide [here](https://github.com/ChenglongChen/tensorflow-XNN/blob/master/doc/Mercari_Price_Suggesion_Competition_ChenglongChen_4th_Place.pdf) how we deal with fields containing sequences, how we incoporate various FM components into deep model.

# Usage
## Input Format
This implementation requires the input data in the following format:
- [ ] **Xi**: *[[ind1_1, ind1_2, ...], [ind2_1, ind2_2, ...], ..., [indi_1, indi_2, ..., indi_j, ...], ...]*
    - *indi_j* is the feature index of feature field *j* of sample *i* in the dataset
- [ ] **Xv**: *[[val1_1, val1_2, ...], [val2_1, val2_2, ...], ..., [vali_1, vali_2, ..., vali_j, ...], ...]*
    - *vali_j* is the feature value of feature field *j* of sample *i* in the dataset
    - *vali_j* can be either binary (1/0, for binary/categorical features) or float (e.g., 10.24, for numerical features)
- [ ] **y**: target of each sample in the dataset (1/0 for classification, numeric number for regression)

Please see `example/DataReader.py` an example how to prepare the data in required format for DeepFM.

## Init and train a model
```
import tensorflow as tf
from sklearn.metrics import roc_auc_score

# params
dfm_params = {
    "use_fm": True,
    "use_deep": True,
    "embedding_size": 8,
    "dropout_fm": [1.0, 1.0],
    "deep_layers": [32, 32],
    "dropout_deep": [0.5, 0.5, 0.5],
    "deep_layers_activation": tf.nn.relu,
    "epoch": 30,
    "batch_size": 1024,
    "learning_rate": 0.001,
    "optimizer_type": "adam",