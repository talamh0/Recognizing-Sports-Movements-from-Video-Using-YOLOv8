## 📊 Evaluation & Results  

We trained three YOLOv8 models to detect **sports movement phases** (start, middle, end).  
Each model was trained and evaluated on a labeled dataset of gym exercises.  

### 🔹 Model Performance  
| Model          | mAP@50   | mAP@50-95 |
|----------------|----------|-----------|
| Start Frames   | 0.9947   | 0.8923    |
| Middle Frames  | 0.9949   | 0.8651    |
| End Frames     | 0.9814   | 0.8324    |

- **Start & Middle Frames** achieved the highest accuracy (mAP@50 ≈ 0.995).  
- **End Frames** had slightly lower performance due to dataset imbalance.  
- **Squat** and **Push-up** classes reached near-perfect detection.  
- **Russian Twist** and **Hammer Curl** performed lower because of limited samples and similarity between movements.  

### 🔹 Model Complexity  
- YOLOv8s (72 layers, ~3M parameters, 8.1 GFLOPs).  
- Efficient for real-time inference.  

### 🔹 Visual Results  
- ![mAP Comparison](graph_for%20mAPs.png)  
- ![All Models – mAP Scores](mAPs%20for%20all%20models.png)  
- ![FLOPs Analysis](FLOPs%20for%20all%20models.png)  
