#End-to-End Deep Learning for Person Search


Short name: E2EPersonSearch
Score: 5

# Contributions
## Problem addressed
- real-world scenarios where the annotations of pedestrian bounding boxes are unavailable and the target person needs to be found from whole images

## Idea / Observation
- we investigate how to localize and match query persons from the scene images without relying on the annotations of candidate boxes
- propose an end-to-end deep learning framework to jointly handle both tasks
- a large-scale and scene-diversified person search dataset, which contains 18,184 images, 8,432 persons, and 99,809 annotated bounding boxes.
- Joint optimization brings multiple benefits ... We share a fully convolutional neural network to extract features for detecting pedestrians and producing discriminative re-id features.

## Formulation / Solver / Implementation
1. Utilize VGG16 model for convolutional layers (conv1 and conv5) in FCN.
2. Follow faster rcnn for the pedestrian proposal network
3. From pedestrian proposals, we apply three fully connection layers (fc6-8) to generate final feature for person re-id

## Useful info
1. if the softmax target is very sparse and the minibatch contains only a few label classes, the gradients would be biased on these classes at each SGD iteration
2. It is observed that detec- tors greatly affect the person search performance of baseline method and there is still a big gap between using the ground truth bounding boxes and the automatically detected ones.

# Evaluation
## Dataset
- Own dataset (E2E Person Search)
- There are two parts in the dataset: street snaps and movies.
- Low-resolution Subset and Occlusion Subset

## Metrics
- designed different evaluation protocols by setting the gallery size to 50, 100, 500, 1, 000, 2, 000, and 4, 000
- meanAveraged Precision (mAP): A candidate window is considered as positive if its overlap with the ground truth is larger than 0.5
- top-k matching rate on bounding boxes: A matching is counted if a bounding box among the top-k predicted boxes overlaps with the ground truth larger than the threshold

## Results
- Baseline detector: ACF + Deep detector
- Baseline re-id methods: BoW with cosine distance, DenseSift+ColorHist with Euclidean and KISSME distance metric, IDNet



# Resource
## Project page
http://www.ee.cuhk.edu.hk/~xgwang/PS/dataset.html

## Source code
https://github.com/ShuangLI59/person_search

## Dataset
Need to send request


## Paper reading


## Others

# Questions
(1) How to perform re-id algorithm in current framework?

# Build upon
(1) Performance is low on low-resolution images

# Paper connections
