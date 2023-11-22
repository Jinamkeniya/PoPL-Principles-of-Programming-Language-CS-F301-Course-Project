# PoPL-Principles-of-Programming-Language-CS-F301-Course-Project
Title: Comparative study between Candle, a Rust based ML framework and PyTorch

We have compared the performance of Candle based Rust model of yolov3 with PyTorch based python model of the same.
yolov3 is an object detection model. The code citations have been provided. We have made minor changes in the code to incorporate confidence scores which is a way which we are using to compare the performances of the two.
Another parameter that we are checking for the model accuracy is the number of objects both the models are detecting which we are comparing with what appears correct to the naked eye.
Approximately 







PopL concepts in candle:
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
