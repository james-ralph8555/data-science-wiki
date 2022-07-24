---
tags:
  - ComputerVision
---
- Assigns labels to an image
- Takes RecordIO format (not protobuf), or jpg or png with a .lst annotation file
- Accepts augmented manifest image format, and using this format allows pipe mode
- Uses a ResNet [[Convolutional Neural Networks|CNN]], can train from scratch or do transfer learning from imageNet
- Hyperparameters: the usual
- Uses GPU for training, multi-GPU and multi-machine allowed
