# DNA Sequence Analysis

This repository contains a Python script for analyzing DNA sequences. The script reads a compressed FASTA file, extracts the sequence, and performs various analyses, including finding specific letters, generating the complement sequence, and counting nucleotide occurrences in kilobase windows.

## Requirements

- Python 3.x
- gzip module

## Usage

1. Clone the repository:
    ```bash
    git clone https://github.com/your-username/dna-sequence-analysis.git
    cd dna-sequence-analysis
    ```

2. Run the script:
    ```python
    import gzip

    file_path = '/content/chr1_GL383518v1_alt.fa.gz'

    with gzip.open(file_path, 'rt') as file:
        file_content = []
        for i, line in enumerate(file):
            file_content.append(line.strip())
            if i > 20:  # Limiting to the first 20 lines for preview
                break

    file_content
    sequence = ''.join(file_content[1:])
    tenth_letter = sequence[9]
    print(tenth_letter)
    seven_hundred_fifty_eighth_letter = sequence[757]
    print(seven_hundred_fifty_eighth_letter)

    complement_mapping = {
        'A': 'T',
        'T': 'A',
        'C': 'G',
        'G': 'C',
        'a': 't',
        't': 'a',
        'c': 'g',
        'g': 'c',
        'N': 'N',  
        'n': 'n'
    }

    # Create the complete sequence
    complement_sequence = ''.join(complement_mapping.get(base, base) for base in sequence)
    # Convert the complement sequence to a list and reverse it
    complement_mapping_list = list(complement_sequence)
    complement_mapping_list.reverse()
    # Convert the reversed list back to a string
    reversed_complement_sequence = ''.join(complement_mapping_list)
    print(reversed_complement_sequence)

    # Printing 79th letter of sequence
    print(reversed_complement_sequence[78])
    # Printing the 500th and 800th letters of the sequence
    print(reversed_complement_sequence[499])
    print(reversed_complement_sequence[799])

    my_dict = {}

    # Define the size of each kilobase window
    kilobase_size = 1000

    # Process the sequence in chunks of 1000 bases
    sequence_length = len(sequence)

    # Iterate through the sequence in kilobase-sized steps
    for i in range(0, sequence_length, kilobase_size):
        # Create a sub-dictionary to hold the counts of each nucleotide
        nucleotide_counts = {'A': 0, 'T': 0, 'C': 0, 'G': 0}
        
        # Determining the start and end of the current kilobase
        start = i
        end = min(i + kilobase_size, sequence_length)
        
        # Slice the sequence for the current kilobase window
        kilobase_sequence = sequence[start:end]
        
        # Count the occurrences of each nucleotide in this window
        for nucleotide in kilobase_sequence:
            if nucleotide in nucleotide_counts:
                nucleotide_counts[nucleotide] += 1
        
        # Store the counts in the nested dictionary with the kilobase range as the key
        my_dict[i] = nucleotide_counts

    print(my_dict)
    print(my_dict[5000]['A'])

    # A list with 4 elements containing the number of times each nucleotide (A,C,G,T) is contained in the first 1000 base pairs.
    first_1000_bp = sequence[:1000]

    a_count = first_1000_bp.count('A')
    c_count = first_1000_bp.count('C')
    g_count = first_1000_bp.count('G')
    t_count = first_1000_bp.count('T')

    nucleotide_counts = [a_count, c_count, g_count, t_count]
    print(nucleotide_counts)

    # Repeat for each kilobase in the dictionary
    for kb_index, letter_counts in my_dict.items():
        print(f"Kilobase {kb_index}:")
        for letter, count in letter_counts.items():
            print(f"  {letter}: {count}")

    all_kb_nucleotide_counts = []
    for kb_index, letter_counts in my_dict.items():
        a_count = letter_counts.get('A', 0)
        c_count = letter_counts.get('C', 0)
        g_count = letter_counts.get('G', 0)
        t_count = letter_counts.get('T', 0)
        nucleotide_counts_for_kb = [a_count, c_count, g_count, t_count]
        all_kb_nucleotide_counts.append(nucleotide_counts_for_kb)

    print(all_kb_nucleotide_counts)

    sum_of_nucleotide_counts = []
    for kb_counts in all_kb_nucleotide_counts:
        sum_of_counts = sum(kb_counts)
        sum_of_nucleotide_counts.append(sum_of_counts)

    print(sum_of_nucleotide_counts)
    ```

## License

This project is licensed under the MIT License - see the LICENSE file for details.

## Acknowledgments

- Thanks to the open-source community for providing valuable resources and tools.
