### Recognizing-Sports-Movements-from-Video-Using-YOLOv8
The project focuses on recognizing **sports exercises** from video using **YOLOv8**.  
Each exercise is divided into **three phases**: start, middle, and end, enabling fine-grained recognition of movements.  

###  Objectives  
- Build an AI model capable of detecting sports movements automatically.  
- Support both **fitness applications** and **rehabilitation systems**.  
- Provide phase-level recognition (start → middle → end) for better accuracy.  

###  Dataset  
- Source: **Kaggle Gym Workout Exercises Video Dataset**.  
- Annotation Tool: **Roboflow**.  
- Each exercise is labeled across 3 phases (e.g., `squat_1`, `squat_2`, `squat_3`).  
- Classes included: **Squat, Push-up, Pull-up, Hammer Curl, Russian Twist**.  

###  Methodology  
1. **Data Preparation** – Extract frames and annotate into 3 phases.  
2. **Model Training** – Three YOLOv8 models trained separately for start, middle, end frames.  
3. **Hyperparameter Tuning** – Batch sizes tested (8, 16, 32).  
4. **Evaluation** – Metrics include **mAP@50, mAP@50–95, Precision, Recall**.  

## Evaluation & Results  

We trained three YOLOv8 models to detect **sports movement phases** (start, middle, end).  
Each model was trained and evaluated on a labeled dataset of gym exercises.  

### Example Predictions  
- ![Push-up Prediction](pred.jpg)

- ![pull-up Prediction](pred1.jpg) 

###  Model Performance  
| Model          | mAP@50   | mAP@50-95 |
|----------------|----------|-----------|
| Start Frames   | 0.9947   | 0.8923    |
| Middle Frames  | 0.9949   | 0.8651    |
| End Frames     | 0.9814   | 0.8324    |

- **Start & Middle Frames** achieved the highest accuracy (mAP@50 ≈ 0.995).  
- **End Frames** had slightly lower performance due to dataset imbalance.  
- **Squat** and **Push-up** classes reached near-perfect detection.  
- **Russian Twist** and **Hammer Curl** performed lower because of limited samples and similarity between movements.  

###  Model Complexity  
- YOLOv8s (72 layers, ~3M parameters, 8.1 GFLOPs).  
- Efficient for real-time inference.  

###  Visual Results     
- ![mAP Comparison](Overall%20Comparsion/mAPs%20for%20all%20models.png)  
- ![All Models – mAP Scores](Overall%20Comparsion/FLOPs%20for%20all%20models.png)  
- ![FLOPs Analysis](Overall%20Comparsion/graph_for%20mAPs.png)

##  Built With  

- ![Python](https://img.shields.io/badge/Python-3776AB?style=for-the-badge&logo=python&logoColor=white)  
- ![YOLOv8](https://img.shields.io/badge/YOLOv8-00FFFF?style=for-the-badge&logo=github&logoColor=black)  
- ![Roboflow](https://img.shields.io/badge/Roboflow-FF6F00?style=for-the-badge&logo=roboflow&logoColor=white)  
- ![Kaggle](https://img.shields.io/badge/Kaggle-20BEFF?style=for-the-badge&logo=kaggle&logoColor=white)  
- ![Google Colab](https://img.shields.io/badge/Google%20Colab-F9AB00?style=for-the-badge&logo=googlecolab&logoColor=white)  
- ![Pandas](https://img.shields.io/badge/Pandas-150458?style=for-the-badge&logo=pandas&logoColor=white)  
- ![NumPy](https://img.shields.io/badge/Numpy-013243?style=for-the-badge&logo=numpy&logoColor=white)  
- ![Matplotlib](https://img.shields.io/badge/Matplotlib-3776AB?style=for-the-badge&logo=plotly&logoColor=white)  

---

##  How to Run  

### 1️⃣ Clone the repository  
```bash
pip install -r requirements.txt
```

2️⃣ Install dependencies 
```bash
git clone https://github.com/your-username/Recognizing-Sports-Movements-from-Video-Using-YOLOv8.git
cd Recognizing-Sports-Movements-from-Video-Using-YOLOv8 
```

3️⃣ Train the model
```bash
yolo task=detect mode=train model=yolov8s.pt data=data.yaml epochs=50 imgsz=640
```

4️⃣ Evaluate the model
```bash
yolo task=detect mode=val model=runs/detect/train/weights/best.pt data=data.yaml
```

5️⃣ Run inference on new videos/images
```bash
yolo task=detect mode=predict model=runs/detect/train/weights/best.pt source=path/to/video.mp4
```

 

