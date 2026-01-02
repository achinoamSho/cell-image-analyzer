# Cell Image Analyzer - Project Proposal

A Python-based image processing tool for automated analysis of cell culture images from brightfield microscopy. This application will detect cells, calculate confluency, estimate cell viability (live vs dead), and provide seeding volume calculations for cell culture workflows.

## Motivation

Working in the tissue culture (TC) room involves repetitive and time-consuming tasks that can be prone to human error. Manual cell counting, confluency estimation, and viability assessment require significant time and can vary between researchers. This project aims to **make our lives easier in the TC room** by:

- **Eliminating manual counting**: No more tedious counting under the microscope or using hemocytometers
- **Reducing subjectivity**: Consistent, objective measurements of confluency and viability across different users
- **Saving time**: Quick analysis of images in seconds instead of minutes and even hours of manual work
- **Improving accuracy**: Automated detection reduces human error in cell counting and confluency estimation
- **Streamlining workflows**: Integrated seeding calculator means no more manual calculations or guesswork when passaging cells
- **Standardizing protocols**: Consistent analysis methods help maintain reproducibility across experiments

Whether you're a student learning cell culture, a technician managing multiple cell lines, or a researcher optimizing culture conditions, this tool helps you work more efficiently and confidently in the TC room 😊

## What Does This Project Do?

This project will automate the analysis of brightfield microscopy images of cell cultures. It will perform the following tasks:

1. **Cell Detection**: Automatically identifies and segments individual cells in brightfield images using advanced image processing algorithms (watershed segmentation or adaptive thresholding)

2. **Viability Estimation**: Classifies cells as live or dead based on morphological features such as:
   - Cell size and shape
   - Brightness/intensity patterns
   - Circularity metrics
   - Texture characteristics

3. **Confluency Calculation**: Computes the percentage of the culture surface covered by cells, providing both:
   - Total confluency (all cells)
   - Live cell confluency
   - Dead cell confluency

4. **Seeding Calculator**: Integrates with cell culture volume calculations to determine how much cell suspension to transfer for achieving desired confluency in destination plates

5. **Visualization**: Provides color-coded overlays on images showing:
   - Green highlights for live cells
   - Red highlights for dead cells

## Input Data

### Expected Input

- **Image Format**: Brightfield microscopy images in common formats:
  - `.png`, `.jpg`, `.jpeg` (RGB or grayscale)
  - `.tif`, `.tiff` (TIFF format, commonly used in microscopy)
  - `.bmp` (Bitmap format)

- **Image Characteristics**:
  - Brightfield microscopy images (no special staining required)
  - Images should have reasonable contrast between cells and background
  - Recommended: Images with consistent lighting and focus
  - Cell cultures at various confluency levels (0-100%)

- **Optional Parameters** (adjustable in the GUI):
  - Detection method (watershed or threshold)
  - Minimum distance between cell centers
  - Darkness threshold for dead cell classification
  - Size threshold for cell filtering

### Expected Output

The application provides several types of output:

1. **Quantitative Metrics**:
   - Total confluency percentage (0-100%)
   - Live cell confluency percentage
   - Dead cell confluency percentage
   - Cell viability percentage
   - Number of live cells detected
   - Number of dead cells detected
   - Total cell count

2. **Visual Output**:
   - Annotated image with color-coded cell overlays:
     - Green: Live cells
     - Red: Dead cells
   - Original image displayed alongside processed results

3. **Seeding Recommendations**:
   - Volume (in µL) to transfer from source plate
   - Based on current confluency, desired confluency, and plate dimensions

4. **Export Capabilities** (future feature):
   - Save analysis results as CSV/JSON
   - Export annotated images
   - Generate analysis reports

## Technicalities

### Prerequisites

- **Python 3.8 or higher**
- **pip** (Python package installer)
- **Git** (for cloning the repository)

### Download/Clone the Repository

```bash
# Clone the repository
git clone https://github.com/yourusername/cell-image-analyzer.git

# Navigate to the project directory
cd cell-image-analyzer
```

Or download as a ZIP file from GitHub and extract it.

### Installation

1. **Create a virtual environment** (recommended):

```bash
# On Windows
python -m venv venv
venv\Scripts\activate

# On macOS/Linux
python -m venv venv
source venv/bin/activate
```

2. **Install dependencies**:

```bash
pip install -r requirements.txt
```

The required packages include:
- `opencv-python` - Image processing and computer vision
- `scikit-image` - Advanced image analysis algorithms
- `numpy` - Numerical computations
- `pandas` - Data manipulation
- `matplotlib` - Plotting and visualization
- `PySide6` - Modern GUI framework (free, LGPL license)
- `scipy` - Scientific computing

### Running the Project

#### Option 1: GUI Application (Recommended)

Launch the graphical user interface:

```bash
python main.py
```

Or:

```bash
python -m gui.main_window
```

**Usage in GUI**:
1. Click "Load Image" to select a cell culture image
2. Adjust analysis parameters if needed
3. Click "Analyze Image" to process the image
4. View results in the results panel
5. Use the seeding calculator to determine transfer volumes

#### Option 2: Command Line Interface (Future)

```bash
python cli.py --image path/to/image.png --method watershed
```

### Running Tests

```bash
# Run all tests
pytest

# Run with verbose output
pytest -v

# Run specific test file
pytest tests/test_image_processing.py

# Run with coverage report
pytest --cov=src --cov-report=html
```

Test files are located in the `tests/` directory and cover:
- Image preprocessing functions
- Cell detection algorithms
- Confluency calculations
- Viability classification
- Edge cases and error handling

### Project Possible Structure

```
cell-image-analyzer/
├── README.md                 # This file
├── requirements.txt          # Python dependencies
├── .gitignore               # Git ignore rules
├── main.py                  # Application entry point
├── src/                     # Source code
│   ├── __init__.py
│   ├── image_processing.py  # Core image analysis
│   ├── cell_detector.py     # Cell detection algorithms
│   ├── confluency_calculator.py
│   └── viability_analyzer.py
├── gui/                     # GUI components
│   ├── __init__.py
│   └── main_window.py        # Main application window
├── tests/                   # Test files
│   └── test_image_processing.py
└── examples/                # Example images and scripts
    └── sample_images/
```


