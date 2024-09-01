# Reverse-Engineering-Radiologist-Intentions-for-Clinical-Trust-and-Adoption

This reporsitory is still under developement. The code and data wil be available here for our Journal paper soon.

In the rapidly evolving landscape of medical imaging, the synergy between artificial intelligence (AI) and clinical expertise offers unprecedented opportunities to enhance diagnostic precision. Yet, the "black box" nature of AI models often limits their integration into clinical practice, where transparency and interpretability are important. This paper presents a novel system leveraging Large Multimodal Models (LMM) to bridge the gap between AI predictions and the cognitive processes of radiologists. The system comprises two core modules: Temporally Grounded Intention Detection (TGID) and Region Extraction (RE). The TGID module predicts the intentions underlying the radiologist’s gaze patterns by analyzing eye gaze fixation heatmap videos and corresponding radiology reports, while the RE module extracts regions of interest that align with these intentions, mirroring the radiologist’s diagnostic focus.

### Overview of our proposed system

<img width="1153" alt="Screenshot 2024-09-01 at 12 41 00 PM" src="https://github.com/user-attachments/assets/36034419-47a5-4e66-a578-9991a15f5ad1">

## Training of TGID module

````
python -m torch.distributed.launch --nproc_per_node 8 --use_env dvc.py --epochs=100 --lr=3e-4 --save_dir=vit --batch_size=2 --batch_size_val=2 --schedule="cosine_with_warmup"

````


## Results for EGD-CXR data

We provide the jupyter notebook to reproduce  all our results and plots  on the EGD-CXR data in the jupyter notebook. All the data needed to run the notebook is uploaded. Please refer above data section for the EGD-CXR.


## References: 

@inproceedings{yang2023vid2seq,
  title={Vid2Seq: Large-Scale Pretraining of a Visual Language Model for Dense Video Captioning},
  author={Yang, Antoine and Nagrani, Arsha and Seo, Paul Hongsuck and Miech, Antoine and Pont-Tuset, Jordi and Laptev, Ivan and Sivic, Josef and Schmid, Cordelia},
  booktitle={CVPR},
  year={2023}
}
