Real-Time Respiratory Health Monitoring Using Audio & Wearables

RespWear is an AI-driven real-time respiratory health monitoring system that integrates respiratory audio analysis and wearable sensor data to detect breathing abnormalities. The project combines embedded IoT hardware, mobile/wearable sensing, and machine learning to deliver a low-cost, portable, and efficient respiratory monitoring solution suitable for home care, fitness, elder care, and early diagnosis support.

📌 Project Overview
RespWear aims to continuously monitor a user’s breathing through:
✔ Audio signals (captured via MEMS microphone)
✔ Physical chest movement data (from IMU accelerometer & gyroscope)
By fusing these two data streams, the system can detect:
•	Irregular breathing cycles
•	Heavy/exerted breathing
•	Coughing events
•	Motion-induced breathing disturbances
•	Potential apnea indicators
•	Abnormal respiratory patterns during exercise or rest
The project demonstrates how lightweight machine learning models can be deployed on embedded hardware for real-time inference, enabling proactive respiratory health monitoring without external cloud dependencies.

🔧 Hardware Components
The RespWear prototype uses:
•	ESP32-S3 Microcontroller – for real-time processing & wireless transmission
•	ICS-43434 MEMS Microphone – high-quality respiratory sound acquisition
•	BMI160 IMU Sensor – motion, acceleration & chest-expansion tracking
•	Li-Ion Battery – portable power
•	Custom wearable band / chest strap – holds sensors in place

📡 System Workflow
1.	Audio & IMU Data Acquisition
o	Microphone captures breathing sounds
o	IMU sensor tracks chest movement and breathing cycles
2.	Preprocessing
o	Bandpass noise filtering (audio)
o	Timestamp alignment (audio + IMU)
o	Normalization & smoothing
o	Spectrogram & MFCC extraction
3.	Feature Extraction
o	Audio features: MFCCs, spectral contrast, wheeze signatures
o	Motion features: breathing rate, peak-to-peak motion, acceleration cycles
4.	Sensor Fusion
o	Combining audio + wearable motion signal features
o	Improves robustness during noisy environments & movements
5.	Machine Learning Classifier
o	Random Forest (Best-performing embedded-friendly model)
o	Predicts breathing states and abnormalities in real-time
6.	Output & Visualization
o	Real-time detection on the device
o	Optionally streamed to smartphone/PC dashboard
o	Trend graphs, alerts & logs

🧠 Machine Learning Models Used
The following models were tested and compared:
Model	Purpose	Notes
Random Forest	Final deployed classifier	High accuracy, low computation
CNN	Audio pattern recognition	Good results but heavier for MCU
LSTM	Breathing cycle classification	Excellent temporal modeling
Autoencoder	Anomaly detection	Useful for unsupervised tasks
KNN / SVM / Decision Trees	Traditional ML baselines	Used for comparison
Random Forest was selected for deployment due to:
•	Low latency
•	Excellent performance on fused features
•	Low memory footprint
•	High interpretability

📊 Key Features
✔ Real-time respiratory monitoring
✔ Fusion of audio + motion sensor data
✔ Works in noisy or moving environments
✔ Lightweight ML model optimized for ESP32 deployment
✔ Detects multiple breathing anomalies
✔ Portable wearable prototype
✔ Expandable for medical or fitness use cases

📈 Results Summary
•	High accuracy in classifying breathing patterns
•	Robust against background noise (fan, traffic, talking)
•	Reliable even during user movement (walking, jogging)
•	Generalizes well across multiple individuals
•	Embedded inference speed suitable for real-time monitoring
Additional evaluation tools:
•	Confusion Matrix
•	ROC-AUC curves
•	Feature importance maps
•	Spectrogram heatmaps

🧪 Applications
RespWear is suitable for:
•	Home respiratory health tracking
•	Early illness or infection detection
•	Sleep apnea screening support
•	Post-COVID recovery monitoring
•	Sports & fitness breathing analysis
•	Elderly care & assisted living
•	Remote health monitoring / Telemedicine

🛠️ How to Run the Project
1. Hardware Setup
•	Connect ICS-43434 microphone to ESP32-S3 (I2S interface)
•	Connect BMI160 IMU via I2C
•	Upload firmware via Arduino IDE / ESP-IDF
•	Power using Li-ion battery or USB
2. Software Setup
Clone the repository:
git clone https://github.com/paramxsingh/Real-Time-Respiratory-Health-Monitoring-Using-Audio-Wearables.git
cd Real-Time-Respiratory-Health-Monitoring-Using-Audio-Wearables
Install required Python libraries:
pip install -r requirements.txt
3. Train the Model
python train_model.py
4. Deploy to ESP32
Convert the trained model to MicroML format and flash firmware:
python convert_model.py
idf.py flash
5. Visualize Data
python app_dashboard.py

📘 Project Structure
RespWear/
│── data/                # Audio + IMU datasets
│── model/               # Trained ML models
│── firmware/            # ESP32-S3 code
│── preprocessing/        # Scripts for data cleaning
│── feature_extraction/   # MFCC, spectrogram, IMU processing
│── training/             # ML training notebooks + scripts
│── deployment/           # Microcontroller deployment tools
│── dashboard/            # Visualization UI code
│── README.md             # Project documentation
│── requirements.txt      # Python dependencies

🚀 Future Enhancements
•	Add SpO₂, heart rate, and temperature sensors
•	Cloud dashboard + patient history tracking
•	Mobile app (Android/iOS) integration
•	Deep learning models optimized with TensorFlow Lite Micro
•	Clinical validation studies with hospitals
•	Automatic early-warning alerts
•	Battery optimization for long-term wear

📄 License
This project is licensed under the MIT License — free for research and development use.

🤝 Contributing
Contributions are welcome!
Feel free to submit issues or pull requests for improvements.

