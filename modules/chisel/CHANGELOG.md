# Changelog

All notable changes to Chisel will be documented in this file.

## [1.2.1] - 2024-11-11

### Added

Database Integration: Implemented SQL database support to store metadata for all processed images, enabling detailed tracking from download through to dataset creation.
JSONL and SQL Storage: Now writes metadata to both JSONL for local use and SQL for centralized data storage.

### Changed

Metadata Handling: Refactored to support new database structure, ensuring seamless transfer of metadata from JSONL to SQL.
Error Handling: Updated to capture and log database-related errors during processing.

## [1.2.0] - 2024-10-23

### Added
- Configuration file support through `config.yaml`
- Multiprocessing capabilities for faster image processing
- Progress bars using `tqdm` for better user feedback
- Enhanced logging system with configurable log levels
- Support for multiple output formats (JPEG, PNG, NumPy arrays)
- Image enhancement features:
  - Brightness adjustment
  - Contrast enhancement
  - Color saturation control
  - Sharpness modification
- Metadata preservation system for Creative Commons attribution

### Changed
- Refactored code structure for better maintainability
- Improved error handling with detailed error messages
- Enhanced duplicate detection using content hashing
- Updated blur detection algorithm for better accuracy
- Optimized memory usage during batch processing

### Fixed
- Issue with incorrect file extensions in output files
- Memory leak during large batch processing
- Error in blur threshold calculation
- Problems with metadata preservation during processing

## [1.1.0] - 2024-10-15

### Added
- Blur detection functionality
- Basic image quality checks
- Support for batch processing
- Initial metadata handling system
- Command-line interface for basic operations
- Basic logging functionality

### Changed
- Improved image resizing algorithm
- Enhanced error handling
- Updated documentation with usage examples
- Restructured project directory

### Fixed
- Issues with image format conversion
- Problems with file path handling
- Memory usage optimization
- Error in dimension calculations

## [1.0.0] - 2024-10-08

### Added
- Initial release of Chisel
- Basic image preprocessing capabilities:
  - Image resizing
  - Format conversion
  - Quality control
- Command-line interface
- Basic error handling
- Documentation:
  - Installation instructions
  - Basic usage guide
  - Command-line arguments reference

### Features
- Support for common image formats (JPEG, PNG)
- Basic quality control parameters
- Simple logging system
- Directory-based processing

