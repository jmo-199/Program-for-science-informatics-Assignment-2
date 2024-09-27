# Sequence Analysis Code

## Identifying Information
  - Programmer: Jason Moore
  - Language: Python
  - Version: 1.0
  - Date Submitted: 9/29/2024
  - Description: This script processes genomic sequences stored in a compressed `.fa.gz` file. It performs various tasks like extracting specific letters, generating reverse complements, counting nucleotides in kilobase windows, and outputting nucleotide frequency statistics.

## Required Files
- A `.fa.gz` file containing genomic sequence data. The example file used in the script is `chr1_GL383518v1_alt.fa.gz`, but you can replace it with your own.

## Required Libraries/Packages/Software
- Python 3.x
- `gzip` (pre-installed in Python)
- `NumPy` (`numpy`)
- `Matplotlib` (`matplotlib`)

You can install the required libraries using:
```bash
pip install numpy matplotlib
```

## Instructions for Running the Script

1. **Download the Script**: Save the Python script (e.g., `.py`) locally.
   
2. **Prepare the Input File**: Ensure you have a `.fa.gz` file. Modify the `file_path` variable in the script to point to the location of your file:
    ```python
    file_path = '/path/to/your/file.fa.gz'
    ```

3. **Run the Script**: Execute the following command:
    ```bash
    python sequence_analysis.py
    ```

4. **Verify Output**: 
    - Check the terminal for nucleotide frequencies, specific sequence letters, and other genomic information.
    - If you want to save the output to a file, redirect the script’s output:
      ```bash
      python sequence_analysis.py > output.txt
      ```

## Files Created During Script Execution
- **Reverse Complement Sequence**: The reverse complement of the genomic sequence is generated and printed.
- **Nucleotide Frequencies in Kilobase Windows**: A summary of nucleotide counts (`A`, `C`, `G`, `T`) is printed for each kilobase (1000 base pairs) window.
- **Total Nucleotide Counts**: Total nucleotide counts per kilobase window are calculated and printed.
- **Other Outputs**: Specific letters from the sequence and reverse complement are printed, along with other statistics.

## Features Demonstrated
1. **Sequence Extraction**: The script reads the compressed `.fa.gz` file, extracts the sequence, and removes the header.
   
2. **Complement and Reverse Complement Generation**: 
   - The complement of the sequence is generated using nucleotide mappings (A ↔ T, C ↔ G) and the reverse complement is printed.

3. **Nucleotide Counting**: The script counts nucleotide frequencies (`A`, `C`, `G`, `T`) in kilobase windows and stores them in a dictionary.

4. **Specific Nucleotide Analysis**: The script prints specific letters from both the sequence and the reverse complement at specified positions.

## Contact and Support
Feel free to reach out if you have any questions or need further assistance with this script.
