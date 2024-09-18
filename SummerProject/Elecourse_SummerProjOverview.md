# CNN LSTM Data Team Co-work Project
## PureCNN, PureLSTM, CNNLSTM code
(1) CNN팀 분석 및 성능 개선 코드  <br/>
growingpenguin_ravdess_savee_tesst_PureCNN.ipynb <br/>
(2) LSTM팀 분석 및 성능 개선 코드  <br/>
growingpenguin_ravdess_savee_tesst_PureLSTM.ipynb <br/>
(3) CNN LSTM팀 협업을 통한 분석 및 성능 개선 코드  <br/>
growingpenguin_ravdess_savee_tesst_CNNLSTM.ipynb <br/>

## Performance
This README provides a detailed comparison between three models:

- **Pure CNN Model**: A traditional convolutional neural network (CNN) with four Conv2D layers for spatial feature extraction.
- **CNN-LSTM Model**: A hybrid model using two Conv2D layers followed by two Long Short-Term Memory (LSTM) layers, combining spatial and temporal feature extraction.
- **Pure LSTM Model**: A model using four LSTM layers to capture sequential dependencies, without any CNN layers.

The comparison covers the model architectures, performance metrics, and their intended purposes.

## Model Structures
### Pure CNN Model
**Architecture**:
- 4 Conv2D layers
- Max Pooling after each Conv2D layer
- Batch Normalization layers
- Dropout layers for regularization
- Flatten layer before the fully connected layers
- 2 Dense layers (128 units, 64 units) followed by Dropout
- Softmax output layer for classification

**Purpose**:
- Suitable for image-based tasks where spatial features need to be extracted.
- Best for static data like image classification.

### CNN-LSTM Model
**Architecture**:
- 2 Conv2D layers for initial spatial feature extraction
- Max Pooling after each Conv2D layer
- Batch Normalization layers
- Flatten and Reshape layers to prepare the data for the LSTM layers
- 2 LSTM layers for capturing sequential dependencies
- Dropout layers for regularization
- 2 Dense layers (128 units, 64 units) followed by Dropout
- Softmax output layer for classification

**Purpose**:
- Suitable for tasks involving both spatial and temporal features.
- Useful for sequential data such as video or time-series data.

### Pure LSTM Model
**Architecture**:
- 4 LSTM layers
- Dropout layers for regularization after each LSTM layer
- 2 Dense layers (128 units, 64 units) followed by Dropout
- Softmax output layer for classification

**Purpose**:
- Ideal for tasks where sequential dependencies are important, without the need for spatial feature extraction (e.g., time-series data, speech, or other sequence-based tasks).

### Performance Metrics

| Metric               | **Pure CNN Model**  | **CNN-LSTM Model** | **Pure LSTM Model**  |
|----------------------|---------------------|--------------------|----------------------|
| **Validation Loss**   | 0.339               | 0.422              | 0.399                |
| **Validation Accuracy**| 89.9%              | 90.4%              | 90.2%                |

### Detailed Comparison

| Feature                   | **Pure CNN Model**          | **CNN-LSTM Model**        | **Pure LSTM Model**         |
|----------------------------|-----------------------------|---------------------------|-----------------------------|
| **Total CNN Layers**        | 4 Conv2D Layers             | 2 Conv2D Layers            | None                        |
| **LSTM Layers**             | None                        | 2 LSTM Layers              | 4 LSTM Layers               |
| **Flatten Layer**           | Yes, before fully connected layers | Yes, before reshaping for LSTM | None                        |
| **Reshape Layer**           | None                        | Reshape used to convert Conv2D output into sequences | None                        |
| **Dropout Layers**          | 3 Dropout layers            | 3 Dropout layers           | 4 Dropout layers            |
| **Fully Connected Layers**  | 2 Dense layers (128, 64 units) | 2 Dense layers (128, 64 units) | 2 Dense layers (128, 64 units) |
| **Output Layer**            | 7-unit Dense layer with softmax activation | 7-unit Dense layer with softmax activation | 7-unit Dense layer with softmax activation |
| **Model Summary**           | Simple architecture with only spatial feature extraction | More complex with both spatial and temporal feature extraction | Simple architecture focused purely on temporal dependencies |
| **Purpose**                 | Suitable for image data (static spatial feature extraction) | Suitable for sequential or temporal data (spatial and temporal feature extraction) | Suitable for pure sequence-based tasks (time-series, speech) |

### Conclusion
- The **Pure CNN Model** achieves a slightly lower validation loss but has comparable validation accuracy to the **CNN-LSTM Model**.
- The **CNN-LSTM Model** performs best for tasks involving both spatial and temporal dependencies, making it ideal for sequential data like time-series or videos.
- The **Pure LSTM Model** is designed for tasks where temporal dependencies are crucial but spatial features are not needed (e.g., time-series forecasting, speech recognition). It performs similarly to the other models but focuses solely on sequential data.

### Usage
- Use the **Pure CNN Model** for tasks like image classification where only spatial features need to be captured.
- Use the **CNN-LSTM Model** for tasks that involve sequential data, such as time-series analysis or video classification, where both spatial and temporal dependencies are important.
- Use the **Pure LSTM Model** for sequence-based tasks (e.g., time-series or speech recognition) where understanding sequential dependencies is key.
