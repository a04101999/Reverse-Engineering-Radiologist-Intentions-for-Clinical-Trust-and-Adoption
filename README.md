# Reverse-Engineering-Radiologist-Intentions-for-Clinical-Trust-and-Adoption

This reporsitory is still under developement. The code and data wil be available here for our Journal paper soon.

In the rapidly evolving landscape of medical imaging, the synergy between artificial intelligence (AI) and clinical expertise offers unprecedented opportunities to enhance diagnostic precision. Yet, the "black box" nature of AI models often limits their integration into clinical practice, where transparency and interpretability are important. This paper presents a novel system leveraging Large Multimodal Models (LMM) to bridge the gap between AI predictions and the cognitive processes of radiologists. The system comprises two core modules: Temporally Grounded Intention Detection (TGID) and Region Extraction (RE). The TGID module predicts the intentions underlying the radiologist’s gaze patterns by analyzing eye gaze fixation heatmap videos and corresponding radiology reports, while the RE module extracts regions of interest that align with these intentions, mirroring the radiologist’s diagnostic focus.

## Training of TGID module


References: 

@inproceedings{yang2023vid2seq,
  title={Vid2Seq: Large-Scale Pretraining of a Visual Language Model for Dense Video Captioning},
  author={Yang, Antoine and Nagrani, Arsha and Seo, Paul Hongsuck and Miech, Antoine and Pont-Tuset, Jordi and Laptev, Ivan and Sivic, Josef and Schmid, Cordelia},
  booktitle={CVPR},
  year={2023}
}
