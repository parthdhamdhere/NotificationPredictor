# NotificationPredictor
A smart, learning-based system to silence unimportant notifications and protect your focus.

The Problem: The High Cost of Interruption
In today's digital world, our phones are constantly buzzing with notifications. While some are critical ("Your cab has arrived"), most are low-value interruptions ("Get 50% off on pizza!").

For everyone, this constant stream of alerts breaks concentration and drains mental energy. For individuals with neurodivergent minds, such as those with ADHD, the pull of a notification is nearly irresistible, making it incredibly difficult to stay focused on important tasks.

Current notification controls are primitive. You can either turn notifications on or off for an entire app. There is no middle ground and no intelligence. We need a system that understands that the importance of a notification depends on its content, not just its source.

The Solution: A Personalized Attention Shield
FocusGuard is a prototype for a machine learning system that learns your personal notification priorities.

It analyzes the content of each incoming notification and, based on what it has learned from your past behavior, predicts whether a notification is URGENT or can be delivered silently as NORMAL.

Instead of a firehose of alerts, you get a curated stream where only the truly important messages break through, allowing you to reclaim your focus and peace of mind.

✨ Features
Text Classification: Uses Natural Language Processing (NLP) to understand the content and intent of a notification.

Simple & Effective Model: Built with scikit-learn and Logistic Regression to provide a lightweight and accurate prediction engine.

Easy to Train: The model learns from a simple CSV file where you label your own notifications.

Extensible: Designed to be the foundation for a more advanced system, including a potential mobile app.

⚙️ How It Works
The project follows a simple machine learning pipeline:

Data Collection (notifications.csv): You create a dataset by logging your notifications and labeling them as URGENT or NORMAL.

Training (train_model.py):

The script reads your labeled data.

It uses a TfidfVectorizer to convert the notification text into numerical features that a model can understand.

It trains a LogisticRegression classifier on this data.

The trained model and the vectorizer are saved as notification_model.pkl and vectorizer.pkl.

Prediction (predict_notification.py):

The script loads the saved model and vectorizer.

It takes a new, unseen notification text as input.

It uses the vectorizer to prepare the text and the model to predict its priority.

It outputs a decision: "Play sound and vibrate!" or "Deliver silently."

📂 Project Structure
.
├── notification_model.pkl      # (Generated) The trained prediction model
├── notifications.csv           # Your dataset of labeled notifications
├── predict_notification.py     # Script to predict the priority of a new notification
├── README.md                   # You are here!
├── train_model.py              # Script to train the model from your data
└── vectorizer.pkl              # (Generated) The fitted text vectorizer

🚀 Getting Started
Follow these steps to get the prototype up and running on your local machine.

Prerequisites
Python 3.x

pip (Python package installer)

1. Clone the Repository
git clone https://github.com/your-username/FocusGuard.git
cd FocusGuard

2. Install Dependencies
This will install pandas, scikit-learn, and joblib.

pip install -r requirements.txt 
# If you don't have a requirements.txt, run:
# pip install pandas scikit-learn joblib

3. Create Your Dataset
Open the notifications.csv file. Start adding your own notifications, one per line. The more data you add, the smarter your model will become! Aim for at least 100 entries with a good mix of URGENT and NORMAL labels.

id

app_name

notification_text

label

1

Zomato

Your order from Pizza Palace is out for delivery

URGENT

2

Instagram

anshul_mehta and 12 others liked your post

NORMAL

...

...

...

...

4. Train the Model
Run the training script. This will read your CSV and generate the .pkl model files.

python train_model.py

You should see an accuracy report and a confirmation that the model was saved.

5. Make a Prediction!
Use the prediction script to test your newly trained model on a new notification.

python predict_notification.py "Your Amazon package will be delivered today"

Expected Output:

--- Prediction ---
Notification Text: 'Your Amazon package will be delivered today'
Predicted Label: URGENT
Confidence: 95.14%
------------------
Action: 🚨 Play sound and vibrate! 🚨

🗺️ Future Roadmap
This prototype is just the beginning. Here are some ideas for taking this project to the next level:

[ ] Build a Simple UI: Use Streamlit or Flask to create a web interface for easier testing.

[ ] Improve the Model: Incorporate more features like app_name, time_of_day, and sender information (WhatsApp: Mom).

[ ] Create an Android App: The ultimate goal. Use Android's NotificationListenerService to intercept notifications in real-time and apply the model.

[ ] Implement a Feedback Loop: Allow the user to correct the model's predictions on the fly, enabling continuous learning.

🤝 Contributing
This project was born from a personal need and a desire to help others reclaim their focus. Contributions, ideas, and feedback are warmly welcome. Please feel free to open an issue or submit a pull request.

📄 License
This project is licensed under the MIT License. See the LICENSE file for details.
