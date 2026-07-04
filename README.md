# TopoNeuron
TopoNeuron: Learning via Topological Defect Dynamics in Geometric Manifolds
<img width="97" height="20" alt="图片" src="https://github.com/user-attachments/assets/e1acee1d-6b51-4360-8459-f8e2cfac3959" />
<img width="82" height="20" alt="图片" src="https://github.com/user-attachments/assets/16de0092-11df-437b-9ff5-7cfdb5f350c5" />
<img width="196" height="20" alt="图片" src="https://github.com/user-attachments/assets/748e9561-cbf1-4594-9421-2902c59c9641" />
Official implementation of the IEEE TPAMI paper
Authors: Idowu Paul Okuwobi* (Senior Member, IEEE), Jingyuan Liu, Jinsong Wu (Senior Member, IEEE)
"We replace learned weights with geometric consistency."
— TopoNeuron reconstitutes neural computation on a foundation of differential geometry and topological physics.
🔍What is TopoNeuron?
TopoNeuron is a fundamentally new neural primitive that replaces the classical weighted-sum neuron with a dynamical topological defect (e.g., phase vortex) in a curved information manifold.  
Unlike traditional networks:

    ✅ No trainable weights — inference is geometric relaxation under input-induced boundary conditions  
    ✅ Built-in robustness — diffeomorphism-equivariant by construction (Theorem 3)  
    ✅ Ultra-low training energy — 0.03 kWh vs. 720 kWh for ViT-B/16  
    ✅ Physically native — maps directly to analog substrates (superconducting circuits, optical phase arrays)

This repository provides complete, standalone implementations in both MATLAB and Python (for integration with modern ML workflows).
📦 Installation
Option 1: MATLAB (Exact Manuscript Reproduction)

   1 Requirements: MATLAB R2016b or later (tested on R2025b)  
   2 Clone this repo:

   git clone https://github.com/yourname/toponeuron.git
   cd toponeuron
   3 Run the demo:
      demo.m  % Reproduces Figures 1–2 from the paper
   Option 2: Python (Modern ML Integration)

    1 Requirements: Python ≥ 3.8, NumPy, SciPy, Matplotlib  
    2 Install dependencies:
       pip install -r requirements.txt
    3 Run the demo:
       python notebooks/demo.ipynb  # Jupyter notebook reproducing Figures 1–2
    
  ⚡Quick Start
MATLAB
% Create a "8" image
img = zeros(28); 
% ... (image creation code as in manuscript)

% Initialize and run TopoNeuron
config.N = 100; config.Q0 = 2;
[y, Phi, stats] = toponeuron(img(:), config);
fprintf('Output: N=%d, Q=%d, D=%.2f, β=%d\n', y);

Python
from src.toponeuron import TopoNeuron
import numpy as np

# Create input
img = np.zeros((28, 28)) 
# ... (image creation)

# Run inference
tn = TopoNeuron(N=100, Q0=2)
y, stats = tn.forward(img)
print(f"Output: N={y[0]}, Q={y[1]}, D={y[2]:.2f}, β={y[3]}")

📂 Repository Structure
toponeuron/
├── README.md                 # This file
├── LICENSE                   # MIT License
├── reproducibility_checklist.md  # TPAMI compliance
├── matlab/                   # Exact manuscript implementation
│   ├── toponeuron.m          # Core unit (Eq. 3 solver)
│   ├── toponet.m             # Manifold surgery (Fig. 3)
│   ├── train_toponeuron.m    # Topological annealing (Sec 5.3)
│   └── demo.m                # End-to-end demo (Figs 1–2)
├── python/                   # Modern Python implementation
│   ├── src/toponeuron.py     # Core unit
│   ├── notebooks/demo.ipynb  # Jupyter demo
│   └── requirements.txt      # Dependencies
└── figures/                  # Generated figures (S1–S3)

📚 Reproducibility
All experiments in the IEEE TPAMI manuscript are fully reproducible:

    Section 6.3 (Robustness): Use toponet.m with CIFAR-10-C  
    Section 6.5 (Efficiency): Profile with tic/toc in MATLAB or time in Python  
    Section 6.7 (Accuracy Gap): Run augmentation ablations in demo.m  
    Supplementary Figures:  
        generate_fig_s1.m → Strong scaling (28 cores)  
        generate_fig_s2.m → Semantic compression (CIFAR-10/100)  
        generate_fig_s3.m → Superclass separation (ImageNet)

See reproducibility_checklist.md
 for full details.
📖 Citation
If you use this code, please cite our IEEE TPAMI paper:
@article{author2025toponeuron,
  title={TopoNeuron: Learning via Topological Defect Dynamics in Geometric Manifolds},
  author={Idowu Paul Okuwobi* (Senior Member, IEEE), Jingyuan Liu, Jinsong Wu (Senior Member, IEEE)},
  journal={IEEE Transactions on Pattern Analysis and Machine Intelligence},
  year={2026},
  publisher={IEEE}
}

📜 License
MIT License — see LICENSE
 for details.
Academic use is free; commercial licensing available upon request.
🙏 Acknowledgments
This work was supported by [China NSCF]. We thank the IEEE TPAMI reviewers for their insightful feedback that significantly improved this work.
