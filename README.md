# rasa_chatbot

## library
1. fasttext: (download .bin [here](https://www.kaggle.com/datasets/aeryss/fasttext-vietnamese-word-vectors-full))
2. underthesea::

## Pipeline

1. Bước token hóa:
- WhitspaceTokenizer: lấy token cách nhau white space/newline/tab bằng thư viện underthesea (vietnamese)

2. Bước trích xuất đặc trưng:
- RegexFeaturizer: cho phép trích xuất đặc trưng tương tự như thư viên re
- LexicalSyntacticFeaturizer: trích xuất đặc trưng bằng từ vựng và cú pháp bằng thư viện spacy
- CountVectorsFeaturizer: trích xuất đặc trưng từ túi từ (bag-of-word)
- CountVectorsFeaturizer: trích xuất đặc trưng từ mô hình n-gram (1, 4)
- FastTextFeaturizer: trích xuất đặc trưng bằng pre-trained FastText model


3. một mạng lưới thàn kinh DIETClassifier sẽ dự đoán ý định (intent) và trích xuất(entity) từ tin nhắn user
Cuối cùng, câu trả lời sẽ được lựa chọn dựa trên intent được dự đoán trước đó và entity.

4. Ánh xạ với các từ đồng nghĩa

5.1. Chọn câu trả lời dựa trên intent và entity

5.2. dự phòng (fallback response) sẽ  được dùng nếu độ tin cậy của dự đoán
dưới một ngưỡng mà ta đã chọn trước.

