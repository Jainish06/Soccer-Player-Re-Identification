# Soccer-Player-Re-Identification
Key Components:

1. PlayerTracker Class

Implements advanced centroid tracking with Hungarian algorithm optimization.
Handles player disappearance/reappearance scenarios.
Maintains player history for robust tracking.

2. CrossCameraMapper Class

Main orchestrator for the entire mapping process.
Uses the provided YOLOv11 model for player detection.
Extracts visual and spatial features from detected players.

3. Feature Extraction System

Visual Features: Color histograms (RGB channels) for jersey/appearance matching.
Spatial Features: Aspect ratio and normalized area for body shape consistency.
Temporal Features: Player movement history for trajectory-based matching.

4. Cross-Camera Matching Algorithm

Computes feature similarity using cosine similarity.
Uses Hungarian algorithm for optimal player assignment.
Applies confidence thresholding to ensure reliable mappings.

How It Works:

Detection Phase:

Processes both video feeds using YOLOv11.
Detects players with confidence filtering.
Extracts bounding boxes and centroids.


Tracking Phase:

Tracks players across frames in each video independently.
Handles occlusions and temporary disappearances.
Maintains consistent local IDs within each camera view.


Feature Analysis:

Extracts color and spatial features from each tracked player.
Computes average features across multiple frames for robustness.
Normalizes features for consistent comparison.


Cross-Camera Mapping:

Creates similarity matrix between all player pairs.
Uses Hungarian algorithm to find optimal one-to-one mappings.
Applies confidence thresholding to filter unreliable matches.


ID Consistency:

Maps tacticam player IDs to broadcast player IDs.
Ensures consistent identification across both camera feeds.


Setup:

1). Install required packages:
      pip install ultralytics opencv-python numpy pandas matplotlib seaborn scikit-learn torch tqdm
2). Run the main function:
      main()
3). For full pieline and visualization sidebyside video run the funtion below:
      run_with_visualization()


