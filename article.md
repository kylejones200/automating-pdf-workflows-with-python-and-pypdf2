---
author: "Kyle Jones"
date_published: "August 23, 2025"
date_exported_from_medium: "November 10, 2025"
canonical_link: "https://medium.com/@kyle-t-jones/automating-pdf-workflows-with-python-and-pypdf2-f36617e17318"
---

# Automating PDF Workflows with Python and PyPDF2 PDFs are everywhere. Contracts, reports, research papers, and scanned
forms often arrive as PDFs. While PDFs are great for sharing, they...

### Automating PDF Workflows with Python and PyPDF2
PDFs are everywhere. Contracts, reports, research papers, and scanned forms often arrive as PDFs. While PDFs are great for sharing, they can be frustrating when you need to combine multiple documents, remove pages, or extract content.

That's where Python comes in. With libraries like **PyPDF2**, you can automate tasks that would otherwise take hours of manual work.

This tutorial will walk you through how to merge multiple PDFs into one file using Python. Along the way, we'll talk about why automation matters and how you can extend the example into your own workflows.

### Why Automate PDFs with Python?
Working with PDFs manually means opening Acrobat or another tool, dragging pages around, and saving new versions. That's fine once in a while, but if you need to repeat the process every day or week, it becomes a drain on your time.

Python helps you:

- **Automate repetitive tasks** --- merging, splitting, or extracting can be done with one script.
- **Ensure consistency** --- the same operations are applied the same way every time.
- **Save time** --- what takes minutes or hours manually runs in seconds with code.

If you've ever thought "there must be a faster way," Python gives you that faster way.

### Getting Started
First, make sure you have the required libraries installed.

``` 
! pip install -r requirements.txt
```

We'll focus on **PyPDF2**, one of the most widely used libraries for PDF manipulation.

### Worked Example: Merging PDFs
Here's a simple script that merges all PDFs in a folder into a single document.

```python
import PyPDF2
from pathlib import Path

def PDFmerge(pdfs, output):
    pdf_write_object = PyPDF2.PdfFileWriter()
    
    for pdf in pdfs:
        pdf_read_object = PyPDF2.PdfFileReader(pdf)
        for page in range(pdf_read_object.numPages):
            pdf_write_object.addPage(pdf_read_object.getPage(page))
    with open(output, 'wb') as final_file_object:
        pdf_write_object.write(final_file_object)
def main(input_folder, output_name):
    pathlist = Path(input_folder).glob('*.pdf')
    pdfs = [str(i) for i in pathlist]
    print("Merging the following PDFs:", pdfs)
    PDFmerge(pdfs, output_name)
    
if __name__ == '__main__':
    main(input_folder='pdfs', output_name='pdfs/merged_document.pdf')
```


### How It Works
The script scans the `pdfs/` folder for any `.pdf` files. It creates a `PdfFileWriter` object.

Each PDF is read page by page and added to the writer. Finally, the combined document is saved as a new file.

That's it --- you've merged multiple PDFs with a few lines of Python.

### Extensions
Once you're comfortable merging PDFs, you can extend this script in many ways:

- **Splitting documents** --- extract only certain pages into a new PDF.
- **Removing pages** --- delete duplicates or unnecessary sections before merging.
- **Extracting text or tables** --- use PyPDF2 or libraries like `pdfplumber` to parse data for analysis.

For example, you could automatically generate a monthly "master report" by merging individual department submissions into one file.

### Further Reading
- [**Book**: [Automate the Boring Stuff with Python](https://automatetheboringstuff.com/), by Al Sweigart (Chapter 15 covers working with PDFs).]
- [**Library**: [PyPDF2 Documentation](https://pythonhosted.org/PyPDF2/).]

### Summary
In this tutorial, you learned how to:

- Use **PyPDF2** to open and merge multiple PDF files.
- Automate PDF handling tasks that are slow and repetitive when done manually.

PDFs don't have to be static and painful to manage. With Python, you can turn them into flexible building blocks in your workflow, saving hours of work and reducing errors.

```python
import PyPDF2
from pathlib import Path

def PDFmerge(pdfs, output):
        
    pdf_write_object = PyPDF2.PdfFileWriter()
    
    for pdf in pdfs:
        pdf_read_object = PyPDF2.PdfFileReader(pdf)
        for page in range(pdf_read_object.numPages):
            pdf_write_object.addPage(pdf_read_object.getPage(page))

    final_file_object = open(output, 'wb')
    pdf_write_object.write(final_file_object)
    final_file_object.close() 
        
def main(input_folder, output_name):

    pathlist = Path(input_folder).glob('*.pdf')

    pdfs = [str(i) for i in pathlist]
    print(pdfs)
    PDFmerge(pdfs, output_name)
    
    
if __name__ == '__main__':
    main(input_folder='pdfs', output_name='pdfs/pdf_filename.pdf')
```
