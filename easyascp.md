# easyascp

## 1. Download IBM aspera connect
as per instructions: https://www.ibm.com/aspera/connect/
## 2. Find installation location of 'ascp' and 'asperaweb_id_dsa.openssh'
### 2a. Mac
~/Applications/Aspera\ Connect.app/Contents/Resources/ascp
~/Applications/Aspera\ Connect.app/Contents/Resources/asperaweb_id_dsa.openssh

### 2a. Ubuntu
 /home/$USER/.aspera/connect/bin/ascp
 /home/$USER/.aspera/connect/etc/asperaweb_id_dsa.openssh

## 3. Create script
easyascp (Ubuntu)
```
#!/bin/bash
# shortcut for ascp downloads
new_ftp=$(echo $1 | sed 's/ftp.sra.ebi.ac.uk\//era-fasp@fasp.sra.ebi.ac.uk:/g')
/home/$USER/.aspera/connect/bin/ascp -QT -l 300m -P33001 -i /home/$USER/.aspera/connect/etc/asperaweb_id_dsa.openssh $new_ftp .
```
easyascp (Mac)
```
#!/bin/bash
# shortcut for ascp downloads
new_ftp=$(echo $1 | sed 's/ftp.sra.ebi.ac.uk\//era-fasp@fasp.sra.ebi.ac.uk:/g')
~/Applications/Aspera\ Connect.app/Contents/Resources/ascp -QT -l 300m -P33001 -i ~/Applications/Aspera\ Connect.app/Contents/Resources/asperaweb_id_dsa.openssh $new_ftp .
```
## 4. Run easyascp
`easyascp ftp.sra.ebi.ac.uk/vol1/fastq/SRR881/000/SRR8810710/SRR8810710.fastq.gz`
