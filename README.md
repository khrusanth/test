
# Define the keyword groups
group_1_keywords = ['PF-AF01', 'PF-AN19', 'PF-D02011', 'PF-NOR18']
group_2_keywords = ['ALM-LO', 'TREAS-DU', 'TREAS-BU', 'TREAS-LO', 'BNPPFCTLAY', 'GRS-PA', 'SBIRD-PAR']
group_3_keywords = ['GAP', 'DF', 'BNPPCB', 'BNPPSCF', 'POSCENT-PA', 'TREASUR-PA']

# Open output files in write mode
output_files = {
    'group_1': open('KONDORGA_4035_SDTBASE.txt', 'w'),
    'group_2': open('KONDORBN_4835_SDTBASE.txt', 'w'),
    'group_3': open('KONDORGA_4035A_SDTBASE.txt', 'w'),
    'default': open('KONDORTP_4835_SDTBASE.txt', 'w')
}

# Read and process the input file
with open('kondorfx_4035.txt', 'r') as infile:
    for line in infile:
        line = line.strip()
        if any(keyword in line for keyword in group_1_keywords):
            output_files['group_1'].write(line + '\n')
        elif any(keyword in line for keyword in group_2_keywords):
            output_files['group_2'].write(line + '\n')
        elif any(keyword in line for keyword in group_3_keywords):
            output_files['group_3'].write(line + '\n')
        else:
            output_files['default'].write(line + '\n')

# Close all output files
for f in output_files.values():
    f.close()
