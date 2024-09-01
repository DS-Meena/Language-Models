Let's create a transformer model from scratch using TensorFlow to generate love poems. This process involves four key steps:

1. Data Preparation
2. Model Architecture
3. Training
4. Poem Generation

### 1. Data Preparation

input sequences:
[[141, 1000],
 [141, 1000, 28],
 [141, 1000, 28, 865],
 [141, 1000, 28, 865, 63],
 [141, 1000, 28, 865, 63, 9],
 [141, 1000, 28, 865, 63, 9, 676],
 [141, 1000, 28, 865, 63, 9, 676, 112],
 [141, 1000, 28, 865, 63, 9, 676, 112, 1],
 [141, 1000, 28, 865, 63, 9, 676, 112, 1, 76],
 [141, 1000, 28, 865, 63, 9, 676, 112, 1, 76, 15]]

Padded sequences
array([[   0,    0,    0, ...,    0,  141, 1000],
       [   0,    0,    0, ...,  141, 1000,   28],
       [   0,    0,    0, ..., 1000,   28,  865]], dtype=int32)

Predictor and labels:
Label is one word ahead of predictor.
```
(array([  0,   0,   0, ...,   0,   0, 141], dtype=int32),
 array([   0,    0,    0, ...,    0,  141, 1000], dtype=int32))
```

With character level encoding
ResourceExhaustedError                    Traceback (most recent call last)
Cell In[13], line 1
----> 1 model.fit(X, y, epochs=1, batch_size=32)

Out of memory while trying to allocate 38993012992 bytes.
	 [[{{node StatefulPartitionedCall}}]]
Hint: If you want to see a list of allocated tensors when OOM happens, add report_tensor_allocations_upon_oom to RunOptions for current allocation info. This isn't available when running in Eager mode.
 [Op:__inference_one_step_on_iterator_4625]