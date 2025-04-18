# Canonical Loader

A Python module for loading and managing canonical data files with standardized naming conventions. This package provides utilities for extracting metadata from file names, loading data from various file formats, and maintaining data canonicality.

## Features

- Standardized file naming convention support
- Automatic date extraction from file names
- Support for CSV and Excel file formats
- Support for both local file system and AWS S3 storage
- Data transformation between DataFrame and dictionary formats
- Metadata extraction and management
- Canonical data saving with consistent formatting

## Installation

```bash
pip install canonical-loader
```

## Quick Start

### Local Files

```python
from canonical_loader import CanonicalLoader

# Initialize loader with regex pattern and folder path
loader = CanonicalLoader(regex="dataset-menu.*\.csv", file_folder="./dataset-canon")

# Access loaded data
df = loader.get_df()
data = loader.get_data()
metadata = loader.get_meta_data()

# Save data in canonical format
loader.save_data_as_df()
```

### AWS S3

```python
from canonical_loader import S3CanonicalLoader

# Initialize S3 loader with regex pattern, bucket name and prefix
loader = S3CanonicalLoader(regex="dataset-menu.*\.csv", bucket="my-bucket", bucket_prefix="data/")

# Access loaded data
df = loader.get_df()
data = loader.get_data()
metadata = loader.get_meta_data()

# Save data in canonical format
loader.save_data_as_df()
```

## File Naming Convention

The package supports the following file naming patterns:

- `dataset-{name}-at{date_ref}-save{date_save}.{extension}` - Single date reference
- `dataset-{name}-from{start_date}-to{end_date}-save{date_save}.{extension}` - Date range
- `dataset-{name}-between{initial_date}-and{final_date}-save{date_save}.{extension}` - Date interval

## Requirements

- Python >= 3.6
- shining_pebbles >= 0.5.3
- string_date_controller >= 0.1.3
- tqdm
- aws_s3_controller >= 0.7.5 (for S3 support)

## Version History

### 0.2.1 (2025-04-18)
- Fixed import bug due to module name changes
- Ensured proper imports between base and derived classes

### 0.2.0 (2025-04-18)
- Added AWS S3 support via S3CanonicalLoader class
- Refactored code to use inheritance for better maintainability
- Improved file extension handling for Excel files
- Enhanced metadata handling for different storage backends

### 0.1.0 (2025-04-18)
- Initial release
- Basic file loading and metadata extraction
- Support for CSV and Excel files
- Canonical data transformation and saving

## License

This project is licensed under the MIT License - see the LICENSE file for details.

## Author

**June Young Park**  
AI Management Development Team Lead & Quant Strategist at LIFE Asset Management

LIFE Asset Management is a hedge fund management firm that integrates value investing and engagement strategies with quantitative approaches and financial technology, headquartered in Seoul, South Korea.

## Contact

- Email: juneyoungpaak@gmail.com
- Location: TWO IFC, Yeouido, Seoul
