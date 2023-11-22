# PoPL-Principles-of-Programming-Language-CS-F301-Course-Project
## Title: Comparative study between Candle, a Rust based ML framework and PyTorch
## Members : Ayush Ghatalia(2021A7PS2571G), Veer Shah(2021A7PS2535G), Jinam Keniya(2021A7PS1622G)

## Problem Statement
We aim to test Candle (which is a machine learning framework in Rust) against Pytorch using a model of yolov3. 
Python based frameworks like PyTorch have huge overhead. Candle allows deployment of lightweight binaries.
We have utilised confidence scores to test accuracy.
Another parameter that we are checking for the model accuracy is the number of objects both the models are detecting which we are comparing with what appears correct to the naked eye.


## Software Used
1) candle-nn library
2) candle-core library
3) numpy library
4) PyTorch library

## citations
We have taken the candle code from the official documentation of candle by huggingface, and the pytorch model from YOLOV3-Object-Detection-with-OpenCV




## POPL concepts in candle:
1. The use of structs ("Block", "Darknet", "Accumulator") provides clear ownership boundaries and encapsulation, preventing unintended access or modification of internal data
2. The use of Result enum in most functions for error handling ensures that errors are explicitly handled, preventing unexpected failures that could lead to memory corruption. For example:
   ```
   pub fn parse_config<T: AsRef<Path>>(path: T) -> Result<Darknet> 
   ```
3. The use of clone() in certain places, such as when cloning parameters in the finish_block method, indicates a conscious decision to transfer ownership of data, preventing unintended shared mutable references. For example:
   ```
   parameters: self.parameters.clone(),
   ```
4. The use of self and &mut self in methods indicates ownership transfer or mutable borrowing, ensuring that ownership rules are followed.
5. Immutable data structures, like BTreeMap for parameters, are used in a way that promotes immutability. This is a good practice for preventing unintended modifications.
   ```
   parameters: BTreeMap<String, String>,
   ```

## Potential for future work:
Model loading time for candle is much lesser than pytorch. However, the inference time for running yolov3 in candle is greater. Our goal will be to try and find a way to somehow bring down the inference time in candle.
Also, we would compare the performances of various models such as classification and segmentation. There are many ways of comparing performances in classification models such as accuracy, confusion matrix, F1 score, etc. In segmentation, IoU(intersection over union) can be used to compare performance. This way, we might get an overall view if candle is more efficient than pytorch or not.
