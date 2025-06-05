# EnvXtract

Data extraction and analysis of environmental variables from various geospatial data formats.

## Status

**Active Development** - This project is currently under active development.

## Description

EnvXtract is a Python package designed for extracting and analyzing environmental data from various geospatial file formats including NetCDF and GeoTIFF raster files. The package provides tools for efficient data processing, statistical analysis, and spatial data extraction using polygon and point-based geometries.

## Features

- **Raster Data Extraction**: Extract statistics from GeoTIFF and other raster formats
- **Polygon and Point-based Analysis**: Support for both polygon and point geometries
- **Batch Processing**: Process multiple files efficiently
- **Flexible Statistics**: Calculate various statistical measures (mean, median, std, min, max, etc.)
- **Multiple File Format Support**: NetCDF, GeoTIFF, and other geospatial formats
- **Configurable Processing**: YAML-based configuration for flexible workflows
- **Comprehensive Logging**: Detailed logging for debugging and monitoring

## Installation

### Prerequisites

- Python 3.13 or higher
- uv package manager

### Install from source

```bash
# Clone the repository
git clone https://github.com/MuhammadShafeeque/envXtract.git
cd envxtract

# Install dependencies using uv
uv sync --dev

# Activate the virtual environment
source .venv/bin/activate  # On Linux/Mac
# or
.venv\Scripts\activate     # On Windows
```

### Install as a package

```bash
# Install directly from source
pip install git+https://github.com/MuhammadShafeeque/envXtract.git
```

## Quick Start

### Basic Usage

```python
from envxtract import RasterExtractor

# Initialize the extractor with configuration
extractor = RasterExtractor(config_file="config.yaml")

# Run the extraction
results = extractor.run()

# Save results
results.to_csv("extraction_results.csv")
```

### Command Line Interface

```bash
# Run extraction with configuration file
python -m envxtract.raster_extractor --config config.yaml --output results/

# Process specific files
python -m envxtract.raster_extractor --raster data/raster.tif --vector data/polygons.shp
```

## Configuration

EnvXtract uses YAML configuration files for flexible processing setup. Here's an example configuration:

```yaml
# Example configuration
input:
  raster_files:
    - "data/input/rasters/*.tif"
  vector_file: "data/input/polygons.shp"

processing:
  statistics: ["mean", "median", "std", "min", "max"]
  buffer_distance: 0  # Buffer around geometries
  
output:
  directory: "data/output/"
  format: "csv"  # csv, json, or both
  
logging:
  level: "INFO"
  file: "extraction.log"
```

## Project Structure

```
envxtract/
├── envxtract/              # Main package
│   ├── __init__.py         # Package initialization
│   ├── raster_extractor.py # Main raster extraction functionality
│   ├── nc_processor.py     # NetCDF processing (in development)
│   ├── basic_analysis.py   # Basic analysis tools (in development)
│   └── advanced_analysis.py # Advanced analysis tools (in development)
├── examples/               # Example scripts and notebooks
├── tests/                  # Unit tests
├── data/                   # Sample data and results
└── docs/                   # Documentation
```

## Development

This project uses modern Python development tools:

- **Python 3.13+**: Latest Python features and performance improvements
- **uv**: Fast Python package installer and resolver
- **pytest**: Testing framework
- **rasterio**: Geospatial raster I/O
- **geopandas**: Geospatial data manipulation
- **xarray**: N-dimensional labeled arrays

### Setting up Development Environment

```bash
# Clone and setup
git clone https://github.com/MuhammadShafeeque/envXtract.git
cd envxtract
uv sync --dev

# Run tests
pytest

# Install in development mode
pip install -e .
```

### Running Tests

```bash
# Run all tests
pytest

# Run with coverage
pytest --cov=envxtract

# Run specific test file
pytest tests/test_raster_extractor.py
```

## Data Formats Supported

### Input Formats
- **Raster**: GeoTIFF (.tif, .tiff), NetCDF (.nc), HDF5
- **Vector**: Shapefile (.shp), GeoJSON (.geojson), GeoPackage (.gpkg)

### Output Formats
- **CSV**: Tabular results with statistics
- **JSON**: Structured metadata and results
- **GeoJSON**: Spatial results with geometries

## Contributing

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/amazing-feature`)
3. Commit your changes (`git commit -m 'Add some amazing feature'`)
4. Push to the branch (`git push origin feature/amazing-feature`)
5. Open a Pull Request

### Development Guidelines

- Follow PEP 8 style guidelines
- Add tests for new functionality
- Update documentation for API changes
- Use type hints where appropriate

## Dependencies

### Core Dependencies
- `geopandas`: Geospatial data manipulation
- `rasterio`: Raster I/O and processing
- `xarray`: N-dimensional arrays and NetCDF
- `numpy`: Numerical computations
- `pandas`: Data manipulation and analysis
- `pyyaml`: YAML configuration parsing

### Development Dependencies
- `pytest`: Testing framework
- `build`: Package building
- `twine`: Package publishing
- `bumpver`: Version management

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## Author

**Muhammad Shafeeque**
- Email: shafeequ@uni-bremen.de
- Institution: Alfred Wegener Institute (AWI)
- Department: Data Science Support

## Acknowledgments

- Alfred Wegener Institute for Polar and Marine Research - Data Science Support
- The geospatial Python community for excellent tools and libraries