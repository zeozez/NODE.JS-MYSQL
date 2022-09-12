
# tensorflow-DeepFM

This project includes a Tensorflow implementation of DeepFM [1].

# NEWS
- A modified version of DeepFM is used to win the 4th Place for [Mercari Price Suggestion Challenge on Kaggle](https://www.kaggle.com/c/mercari-price-suggestion-challenge). See the slide [here](https://github.com/ChenglongChen/tensorflow-XNN/blob/master/doc/Mercari_Price_Suggesion_Competition_ChenglongChen_4th_Place.pdf) how we deal with fields containing sequences, how we incoporate various FM components into deep model.

# Usage
## Input Format
This implementation requires the input data in the following format:
- [ ] **Xi**: *[[ind1_1, ind1_2, ...], [ind2_1, ind2_2, ...], ..., [indi_1, indi_2, ..., indi_j, ...], ...]*