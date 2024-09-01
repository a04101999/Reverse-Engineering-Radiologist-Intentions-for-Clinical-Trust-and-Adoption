# Reverse-Engineering-Radiologist-Intentions-for-Clinical-Trust-and-Adoption

This reporsitory is still under developement. The code and data wil be available here for our Journal paper soon.

In the rapidly evolving landscape of medical imaging, the synergy between artificial intelligence (AI) and clinical expertise offers unprecedented opportunities to enhance diagnostic precision. Yet, the "black box" nature of AI models often limits their integration into clinical practice, where transparency and interpretability are important. This paper presents a novel system leveraging Large Multimodal Models (LMM) to bridge the gap between AI predictions and the cognitive processes of radiologists. The system comprises two core modules: Temporally Grounded Intention Detection (TGID) and Region Extraction (RE). The TGID module predicts the intentions underlying the radiologist’s gaze patterns by analyzing eye gaze fixation heatmap videos and corresponding radiology reports, while the RE module extracts regions of interest that align with these intentions, mirroring the radiologist’s diagnostic focus.

### Overview of our proposed system

<img width="1153" alt="Screenshot 2024-09-01 at 12 41 00 PM" src="https://github.com/user-attachments/assets/36034419-47a5-4e66-a578-9991a15f5ad1">

# DATA 
We have used the EGD-CXR and the REFLACX data for our project. Please find below the data files uploaded.

### EGD-CXR DATA 

#### Prediction from the best model for EGD-CXR  (Test set) 

https://drive.google.com/file/d/1qow004vlqNwCSnzUU_dXeBS6ZnUsy8vU/view?usp=sharing

#### Test set ( Groud-truth file summarized report, Intentions + temporal grounding  ) 

https://drive.google.com/file/d/16ELpup7LT6gIar4iJ9Tm7qZjz2rbPDum/view?usp=sharing

#### Training set ( Groud-truth file , diagnosis + temporal grounding  ) 

https://drive.google.com/file/d/1Cj4R8hcfY0tBo4CbZiDwtKUcZBUfmejg/view?usp=sharing

#### Actual report transcription wihtout summarization using chexpert labeler ( Train + test )

https://drive.google.com/file/d/1Tl2h2YdvS9mRr4q3DfOWbJ9aFlSpg8SA/view?usp=sharing

#### Eye Gaze heatmaps for both the ( Train and Test ) 
We have uploaded some samples of our created fixation heatmaps using the eye gaze data as it is very big to upload for both the train and test sets.

https://drive.google.com/drive/folders/1WF2jzle1D6gVYv4mskypaQHd-9spF42K?usp=sharing

#### Eye Gaze fixation data ( Train and Test ) 
Please use the eye gaze fixation data to create the fixation heatmaps 

https://drive.google.com/file/d/12JfxpAzRthnsEv57qgj0DZlqwVfehVxX/view?usp=sharing

#### Pre-computed video features( Resnet-101) ( Train +Test set ) 

https://drive.google.com/file/d/1piQiRYmljmDgLWrDIU5TmdXWcst9n2ra/view?usp=sharing



## Training of TGID module

Example command to train on the EGD-CXR DATA. Always start with the pretrained model on ActivityNet caption dataset "vid2seq_htmchaptersvitt.pth" (Google)

````
python -m torch.distributed.launch --nproc_per_node 6 --use_env dvc.py     --epochs 250     --lr 3e-4     --load 'vid2seq_htmchaptersvitt.pth'     --save_dir ref_data_summar     --combine_datasets youcook     --combine_datasets_val youcook     --batch_size 8     --batch_size_val 8     --schedule "cosine_with_warmup"     --youcook_features_path clipvit.pth     --youcook_train_json_path train.json     --youcook_val_json_path val.json     --youcook_subtitles_path actual_report.pkl

````
#### finetuned model on the EGD-CXR

https://drive.google.com/file/d/1oTH50PVDMBcX8ew87_Xm13BuFyohmupf/view?usp=sharing
##### Log files created during finetuning 

https://drive.google.com/file/d/1IlgF8nlV4fVqZvf5RnRbhRTTL0ZlyKp7/view?usp=sharing

#### finetuned model on the REFLACX-CXR

https://drive.google.com/drive/folders/1U7jOPrQU8qc16CaCfDGSGCPwWF2brOwk?usp=sharing

##### Log files created during finetuning 
https://drive.google.com/file/d/1qgB7CjaZ8pCoGTwG7gkxz9tiIcFCWNKi/view?usp=sharing

## Results for EGD-CXR data

We provide the jupyter notebook ( CSBJ-results_reproduce_egd-cxr_public_github.ipynb)  to reproduce  all our results and plots  on the EGD-CXR data in the jupyter notebook. All the data needed to run the notebook is uploaded. Please refer above data section for the EGD-CXR.



## References: 

@inproceedings{yang2023vid2seq,
  title={Vid2Seq: Large-Scale Pretraining of a Visual Language Model for Dense Video Captioning},
  author={Yang, Antoine and Nagrani, Arsha and Seo, Paul Hongsuck and Miech, Antoine and Pont-Tuset, Jordi and Laptev, Ivan and Sivic, Josef and Schmid, Cordelia},
  booktitle={CVPR},
  year={2023}
}
