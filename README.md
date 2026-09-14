# face-recognition-5pt

CPU-only face recognition pipeline: Haar detection + MediaPipe 5-point landmarks
+ similarity-transform alignment (112x112) + ArcFace ONNX embeddings.

See the accompanying book "Face Recognition with ArcFace ONNX and 5-Point Alignment"
by Gabriel Baziramwabo for full narrative explanation of each stage.

Quick start:
    python -m venv .venv
    source .venv/bin/activate        # Windows: .venv\Scripts\Activate.ps1
    pip install opencv-python numpy onnxruntime scipy tqdm mediapipe
    python -m src.camera             # 1. validate webcam
    python -m src.detect             # 2. validate face detection
    python -m src.landmarks          # 3. validate 5-point landmarks
    python -m src.align              # 4. validate alignment -> 112x112
    # -- plug in real ArcFace ONNX model into models/embedder_arcface.onnx --
    python -m src.embed              # 5. validate embeddings
    python -m src.enroll             # 6. enroll identities
    python -m src.evaluate           # 7. tune threshold  
    python -m src.recognize          # 8. live recognition
