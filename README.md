# HTML to PDF Converter

A Python script that converts HTML files to PDF format using the `xhtml2pdf` library. Supports both single file conversion and batch processing of entire folders.

## Features

- ✅ Convert single HTML files to PDF
- ✅ Batch convert all HTML files in a folder
- ✅ Preserve folder structure in output
- ✅ Support for embedded CSS styling
- ✅ Command-line interface with multiple modes
- ✅ Built-in DAST Reports conversion mode
- ✅ Progress tracking and error reporting

## Installation

1. Install the required dependencies:
```bash
pip install -r requirements.txt
```

## Usage

### 1. Single File Conversion
```bash
python html_to_pdfConverted.py input.html [output.pdf] [styles.css]
```

**Examples:**
```bash
# Basic conversion
python html_to_pdfConverted.py sample.html

# Specify output file
python html_to_pdfConverted.py sample.html output.pdf

# Include external CSS
python html_to_pdfConverted.py sample.html output.pdf styles.css
```

### 2. Batch Folder Conversion
```bash
python html_to_pdfConverted.py --batch <input_folder> [output_folder]
```

**Examples:**
```bash
# Convert all HTML files in a folder (output to same folder)
python html_to_pdfConverted.py --batch /path/to/html/files

# Convert with different output folder
python html_to_pdfConverted.py --batch /path/to/html/files /path/to/pdf/output
```

### 3. DAST Reports Conversion
```bash
python html_to_pdfConverted.py --dast
```

This mode specifically converts all HTML files in `/Users/gundavarapu.s/Downloads/DAST Reports` to PDF format in the same location.

## Programmatic Usage

You can also use the converter as a Python module:

```python
from html_to_pdfConverted import HTMLToPDFConverter

# Initialize converter
converter = HTMLToPDFConverter()

# Convert single file
converter.convert_file_to_pdf('input.html', 'output.pdf')

# Convert HTML string
html_content = '''
<!DOCTYPE html>
<html>
<head>
    <title>Sample Document</title>
    <style>
        body { font-family: Arial, sans-serif; margin: 40px; }
        h1 { color: #333; }
    </style>
</head>
<body>
    <h1>Hello World</h1>
    <p>This is a sample HTML document.</p>
</body>
</html>
'''

converter.convert_string_to_pdf(html_content, 'sample_output.pdf')

# Batch convert folder
converted_files = converter.batch_convert_folder('/path/to/html/files')
print(f"Converted {len(converted_files)} files")
```

## Requirements

- Python 3.7+
- xhtml2pdf==0.2.17
- reportlab==4.0.4

## Supported Features

- **HTML Elements**: All standard HTML elements
- **CSS Styling**: Embedded and external CSS support
- **Images**: Embedded images (base64) and local image files
- **Tables**: Full table support with styling
- **Fonts**: Standard web fonts
- **Page Layout**: Automatic page breaks and formatting

## Output

- PDF files are created with the same name as the HTML file
- Original folder structure is preserved in batch mode
- Conversion progress is displayed with success/failure indicators
- Summary report shows total conversions and any failures

## Example Output

```
🔍 Converting DAST Reports from: /Users/gundavarapu.s/Downloads/DAST Reports
Found 5 HTML files to convert...
[1/5] Converting: dast report for enrich.html
✅ Successfully converted to: /Users/gundavarapu.s/Downloads/DAST Reports/dast report for enrich.pdf
[2/5] Converting: affiliate dast report.html
✅ Successfully converted to: /Users/gundavarapu.s/Downloads/DAST Reports/affiliate dast report.pdf
...

📊 Conversion Summary:
✅ Successfully converted: 5 files
❌ Failed conversions: 0 files

🎉 DAST Reports conversion completed! 5 files converted.
```

## Troubleshooting

- **File not found errors**: Ensure HTML files exist and paths are correct
- **Permission errors**: Check write permissions for output directories
- **CSS issues**: Ensure CSS is properly embedded or linked
- **Large files**: Processing may take longer for complex HTML files

## License

This project is open source and available under the MIT License.
