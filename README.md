- 👋 Hi, I’m @CptSiva
- 👀 I’m interested in ...
- 🌱 I’m currently learning ...
- 💞️ I’m looking to collaborate on ...
- 📫 How to reach me ...

<!---
CptSiva/CptSiva is a ✨ special ✨ repository because its `README.md` (this file) appears on your GitHub profile.
You can click the Preview link to take a look at your changes.
--->
import cv2

# Load the image using OpenCV
image = cv2.imread('IELTS-template.jpg')

# Convert the image to grayscale (required for text detection)
gray_image = cv2.cvtColor(image, cv2.COLOR_BGR2GRAY)

# Load the pre-trained OCR model from OpenCV
ocr = cv2.text.TextDetectorCNN_create('path/to/ocr_model.pb')

# Detect text in the image
results, _ = ocr.detect(gray_image)

# Extract and print the detected text
for detection in results:
    text = detection[0]
    confidence = detection[1]
    x, y = int(detection[2][0][0]), int(detection[2][0][1])
    cv2.putText(image, text, (x, y), cv2.FONT_HERSHEY_SIMPLEX, 1.0, (0, 255, 0), 2)

# Display the image with detected text
cv2.imshow('Detected Text', image)
cv2.waitKey(0)
cv2.destroyAllWindows()

