# Consensus Analysis in Academic Peer Review Using Search-Augmented Large Language Models

This repository contains the implementation and data processing pipeline for the paper "Consensus Analysis in Academic Peer Review Using Search-Augmented Large Language Models".

## Repository Structure

```
📂 Automated_Consensus_Analysis/
│── 📜 README.md                      # Project overview, setup instructions, usage  
│── 📜 requirements.txt                # Python dependencies  
│── 📜 .gitignore                      # Ignore unnecessary files (e.g., datasets, logs, cache)  
│── 📜 LICENSE                         # License information  
│── 📜 repository_structure.txt         # Auto-generated repository structure  
│  
├── 📂 data/                            # Dataset storage and processing scripts  
│   ├── 📜 aggregate.py                 # Aggregate extracted data  
│   ├── 📜 convert_json_to_csv.py       # Convert dataset formats  
│   ├── 📜 merge_final.py               # Merge finalized datasets  
│   ├── 📜 merge_search_critique.py     # Merge search results with critiques  
│   ├── 📜 prepare_new_subset.py        # Create a new subset of PeerSum  
│   ├── 📜 prepare_sample_subset.py     # Generate a sample dataset  
│   ├── 📂 processed/                   # Processed dataset storage  
│   │   ├── 📂 consensus_resolution/    # Consensus-related outputs  
│   │   │   ├── 📜 combined_final.csv  
│   │   │   ├── 📜 disagreement_resolution.csv  
│   │   │   ├── 📜 disagreement_resolution_final.csv  
│   │   │   ├── 📜 meta_reviews.csv  
│   │   │   └── 📜 meta_reviews_final.csv  
│   │   ├── 📂 critique_points/         # Extracted critique points  
│   │   │   ├── 📜 critique_points_llm.json  
│   │   │   ├── 📜 critique_points_llm_2.json  
│   │   │   ├── 📜 critique_points_nlp.json  
│   │   │   └── 📜 critique_points_nlp_2.json  
│   │   ├── 📂 disagreement_detection/  # Disagreement detection outputs  
│   │   │   ├── 📜 disagreement_aggregated.csv  
│   │   │   ├── 📜 disagreement_scores_llm.json  
│   │   │   ├── 📜 disagreement_scores_nlp.json  
│   │   │   ├── 📜 metrics.csv  
│   │   └── 📂 search/                  # Search-retrieved evidence  
│   │       ├── 📜 logs.json  
│   │       ├── 📜 papers_with_search_final.csv  
│   │       ├── 📜 search_final_2.json  
│   │       ├── 📜 search_intermediate.json  
│   │       └── 📜 search_intermediate_2.json  
│   ├── 📂 raw/                         # Original dataset files  
│   │   ├── 📜 data-00000-of-00001.arrow  
│   │   ├── 📜 dataset_info.json  
│   │   └── 📜 state.json  
│   ├── 📂 split/                       # Train/Test/Validation splits  
│   │   ├── 📜 sample_subset_train.json  
│   │   ├── 📂 test/                     # Test set  
│   │   │   ├── 📜 data-00000-of-00001.arrow  
│   │   │   ├── 📜 dataset_info.json  
│   │   │   └── 📜 state.json  
│   │   ├── 📂 train/                    # Training set  
│   │   │   ├── 📜 data-00000-of-00001.arrow  
│   │   │   ├── 📜 dataset_info.json  
│   │   │   └── 📜 state.json  
│   │   ├── 📂 val/                      # Validation set  
│   │   │   ├── 📜 data-00000-of-00001.arrow  
│   │   │   ├── 📜 dataset_info.json  
│   │   │   └── 📜 state.json  
│   └── 📜 split_dataset.py              # Split data into subsets  
│  
├── 📂 docs/                            # Research papers and references  
│   ├── 📜 Benchmark on Peer Review Toxic Detection.pdf  
│   ├── 📜 Large Language Models Penetration in Scholarly Writing and Peer Review.pdf  
│   ├── 📜 Paper Quality Assessment Individual Wisdom Metrics.pdf  
│   ├── 📜 ReviewEval An Evaluation Framework for AI-Generated Reviews.pdf  
│  
├── 📂 notebooks/                       # Jupyter notebooks for analysis  
│   ├── 📜 01_Exploratory_Analysis.ipynb  
│   ├── 📜 02_EDA_CritiqueLLM.ipynb  
│   ├── 📜 03_Disagreement_Scores_LLM.ipynb  
│   ├── 📜 04_Search_Result_Analysis.ipynb  
│   ├── 📜 05_Retrieved_Evidences_Analysis.ipynb  
│   ├── 📜 06_Disagreement_Resolution.ipynb  
│   ├── 📜 07_Meta_Review_Comparison.ipynb  
│  
├── 📂 src/                             # Core codebase  
│   ├── 📂 consensus_resolution/        # LLM-based consensus synthesis  
│   │   ├── 📜 disagreement_resolution_deepseek.py  
│   │   └── 📜 meta_review_generation.py  
│   ├── 📂 critique_points_extraction/  # Extract critique points  
│   │   ├── 📜 extract_critique_llm.py  
│   │   └── 📜 extract_critique_nlp.py  
│   ├── 📂 disagreement_detection/      # Disagreement detection  
│   │   ├── 📜 compare_reviews_llm.py  
│   │   └── 📜 compare_reviews_nlp.py  
│   ├── 📂 search_retrieval/            # Search-Augmented Verification  
│   │   └── 📜 search_agent.ipynb  
│  
└── 📜 workflow_drawio.png              # Visual workflow diagram  
```

## Data Processing Pipeline

The data processing workflow includes several Python scripts in the `data/` directory:

- `prepare_sample_subset.py`: Creates initial sample datasets
- `prepare_new_subset.py`: Generates additional data subsets
- `convert_json_to_csv.py`: Converts JSON data to CSV format
- `merge_search_critique.py`: Merges search results with critique data
- `merge_final.py`: Performs final data merging
- `aggregate.py`: Aggregates results
- `split_dataset.py`: Splits data into training and testing sets

## Methodology

Our approach follows a systematic workflow:

1. Data Collection and Preprocessing
2. Search-Augmented Review Analysis
3. Consensus Detection
4. Result Validation

For detailed workflow visualization, see [workflow_drawio.png](workflow_drawio.png).

## Setup

1. Create a Python virtual environment:
```bash
python -m venv venv
source venv/bin/activate  # On Windows: venv\Scripts\activate
```

2. Install dependencies:
```bash
pip install -r requirements.txt
```

3. Configure environment variables:
```bash
cp .env.example .env
# Edit .env with your configuration
```

## Documentation

For more detailed information, refer to the following documents in the `docs/` directory:
- Main Paper: "Consensus Analysis in Academic Peer Review Using Search-Augmented Large Language Models"
- Implementation Details: "Benchmark on Peer Review Toxic Detection.pdf"
- Research Context: "Large Language Models Penetration in Scholarly Writing and Peer Review.pdf"

## MLflow Tracking

Experiment tracking and model artifacts are stored in the `mlruns/` directory. Use MLflow UI to view experiments:

```bash
mlflow ui
```

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.
