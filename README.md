Face recognition project structure
Our project structure can be seen by examining the output from the tree  command:

Face recognition with OpenCV, Python, and deep learning
$ tree --filelimit 10 --dirsfirst
.
├── dataset
│   ├── shahrukh [10 entries]
│   └── kajol [10 entries]
├── examples
│   ├── example_01.png
│   ├── example_02.png
│   └── example_03.png
├── output
│   └── ddlj_low_output.avi
├── videos
│   └── ddlj_low_scene.mp4
├── search_bing_api.py
├── encode_faces.py
├── recognize_faces_image.py
├── recognize_faces_video.py
├── recognize_faces_video_file.py
└── encodings.pickle


Our project has 4 top-level directories:

dataset/ : Contains face images for six characters organized into subdirectories based on their respective names.
examples/ : Has three face images for testing that are not in the dataset.
output/ : This is where you can store your processed face recognition videos. I’m leaving one of mine in the folder — the classic “lunch scene” from the original Jurassic Park movie.
videos/ : Input videos should be stored in this folder. This folder also contains the “lunch scene” video but it hasn’t undergone our face recognition system yet.
We also have 6 files in the root directory:

search_bing_api.py : Step 1 is to build a dataset (I’ve already done this for you). To learn how to use the Bing API to build a dataset with my script, just see this blog post.
encode_faces.py : Encodings (128-d vectors) for faces are built with this script.
recognize_faces_image.py : Recognize faces in a single image (based on encodings from your dataset).
recognize_faces_video.py : Recognize faces in a live video stream from your webcam and output a video.
recognize_faces_video_file.py : Recognize faces in a video file residing on disk and output the processed video to disk. I won’t be discussing this file today as the bones are from the same skeleton as the video stream file.
encodings.pickle : Facial recognitions encodings are generated from your dataset via encode_faces.py and then serialized to disk.
After a dataset of images is created (with search_bing_api.py ), we’ll run encode_faces.py  to build the embeddings.

From there, we’ll run the recognize scripts to actually recognize the faces.
