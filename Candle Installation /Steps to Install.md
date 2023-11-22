Without Cuda support:

Create a new app and add candle-core as follows:

```
cargo new myapp
cd myapp
cargo add --git https://github.com/huggingface/candle.git candle-core
```
Finally, run cargo build to make sure everything can be correctly built.

```
cargo build
```
