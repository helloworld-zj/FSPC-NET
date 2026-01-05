# FSPC-NET

Welcome to this repository! This repository hosts the official implementation and supplementary experimental results for the paper **"FSPC-NET: Frequency-Domain Style Perturbation and Pixel-Level Contrastive Learning for Domain-Generalized Medical Image Segmentation"**.

---

## Supplementary Experiments: Parameter Sensitivity Analysis

In response to reviewer feedback, we conducted a parameter sensitivity analysis to evaluate the stability and sensitivity of key hyperparameters in our model.

### Experiment Details
- **Objective**: To assess the model’s performance sensitivity to the EMA momentum coefficient (γ), regularization coefficient (α), and temperature parameter (τ).
- **Method**: Each parameter was varied individually while keeping others fixed, and the corresponding model performance was recorded.
- **Dataset**: Fundus image data from four different domains.

### Results Across Domains
Performance variation across the four fundus domains is visualized below.

**1. On Domain 1:**  
<img width="1500" height="500" alt="myplot11" src="https://github.com/user-attachments/assets/cc9b64f0-7be8-4674-9be2-66cd1b97aa46" />

**2. On Domain 2:**  
<img width="1500" height="500" alt="myplot2" src="https://github.com/user-attachments/assets/1617d3a2-aea8-4988-818d-6a696b8eaaa2" />

**3. On Domain 3:**  
<img width="1500" height="500" alt="myplot3" src="https://github.com/user-attachments/assets/4e2ca473-3fca-491a-b569-4eff6f0ec2c3" />

**4. On Domain 4:**  
<img width="1500" height="500" alt="myplot4" src="https://github.com/user-attachments/assets/01906785-d073-470a-a37e-a99be85f5620" />

### Key Findings
1. **EMA Momentum (γ)**  
   The default value **γ = 0.9** achieves the best balance across all four domains, maximizing inter-domain consistency while maintaining strong performance.

2. **Regularization Coefficient (α)**  
   Domains show notable variation in preference toward style perturbation strength. **α = 0.5** yields the best average performance with acceptable cross-domain variance.

3. **Temperature Parameter (τ)**  
   Model performance is relatively insensitive to τ across domains. **τ = 0.07** is identified as a robust choice, demonstrating the stability of the contrastive learning temperature setting.

### Conclusion  
The sensitivity analysis validates the effectiveness of the selected hyperparameters in multi-center scenarios. Our choices reflect a balanced trade-off among domain-specific performances rather than optimizing for a single domain, offering a practical reference for deploying the model across diverse clinical centers in the future.


---

## Supplementary Experiments: Visualizations of frequency-domain style transfer
This supplementary figure provides qualitative validation of our frequency‑domain style‑transfer procedure, comparing spatial‑domain and frequency‑domain (amplitude‑based) transfers and showing the associated amplitude and phase visualizations to support the claim that amplitude manipulations change appearance while phase preserves structural content.
### Experiment Details
Objective: To visually evaluate how amplitude‑based frequency‑domain operations affect appearance (style) versus content (anatomical structure) compared with a spatial‑domain style‑transfer baseline.
Method: For a paired source/target example, we (1) perform a spatial‑domain style transfer, (2) perform a frequency‑domain style transfer by swapping/perturbing amplitude statistics while keeping phase fixed, and (3) visualize reconstructed RGB images, amplitude maps, and phase maps. A zoomed phase‑residual highlights preserved structural cues.
Data: Example fundus image pair drawn from the datasets used in our study (multi‑center fundus images).
### Visualization (figure)
Layout (columns left → right): Source Domain | Target Domain | Spatial‑Domain Style Transfer | Frequency‑Domain Style Transfer
Rows (top → bottom): Reconstructed RGB image | Amplitude visualization (magnitude/statistics) | Phase visualization | Zoomed phase residual (illustrating preserved structure)
See attached figure for the complete visualization.
[绘图22_english.pdf](https://github.com/user-attachments/files/24428383/22_english.pdf)

### Key Observations and Analysis
Amplitude vs. phase: The amplitude (magnitude) spectrum concentrates global, slowly varying statistics (brightness, contrast, coarse color/texture) that are strongly influenced by scanner/protocol differences. The phase spectrum encodes relative alignment across frequencies and largely determines spatial structure (edges, shapes, and geometry).
Effect of amplitude manipulation: Replacing or perturbing amplitude statistics transfers appearance/style (color, contrast, coarse texture) while preserving phase—hence anatomical boundaries and local morphology remain visually consistent in the frequency‑domain result compared to the spatial‑domain transfer.
Phase residual: The zoomed residual emphasizes that structural elements (vessel/optic‑disc edges and morphology) are better retained after amplitude‑based transfer.
Empirical scope: This decomposition is an inductive bias rather than an absolute separation; its effectiveness is stronger when applied to early encoder features that retain H×W spatial topology.
### Conclusion
The visualization provides qualitative evidence that amplitude‑based frequency operations can simulate domain appearance shifts while largely preserving anatomical content, supporting their use as a lightweight augmentation/robustness tool in multi‑center medical imaging. However, this is a qualitative validation—quantitative cross‑domain performance metrics and structural similarity analyses should complement these results.
