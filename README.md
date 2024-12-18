# TCGA_downloads

This guide is mostly applicable to controlled data access in GDC. Almost all types of data are accessible through GDC/TCGABiolinks/GenomicDataCommons, including patient-specific HLA allele calls. Exome or RNA-seq data can be downloaded depending on your HLA-caller. **arcasHLA** is a preferred caller as it calls **MHC Class I and Class II** using RNA-Seq BAMs ([arcasHLA GitHub](https://github.com/RabadanLab/arcasHLA)).

---

### Steps for Controlled Data Access:

1. For controlled data from the GDC portal, you will need to acquire an **eRA Commons** account. This is typically managed through an administrator at your institution.  
   Once you log in with your eRA credentials ([eRA Login](https://public.era.nih.gov/commonsplus/public/login.era?TARGET=https%3A%2F%2Fpublic.era.nih.gov%3A443%2Fcommonsplus%2Fhome.era)), you will also need **dbGaP access**. Access to dbGaP is granted through a PI (Principal Investigator) who already has access and can add you to the list of approved personnel.

2. Once access is granted through **dbGaP** and **eRA Commons**, proceed to the [GDC Portal](https://portal.gdc.cancer.gov/).

3. In the search box, type the desired cohort or project name (e.g., "TCGA-LUAD").

4. For **BAM downloads**:  
   - Select **"Sequencing Reads"**.  
   - On the next page, select **"bam"** in the left-hand side panel.  
   - Choose **RNA-Seq**, **WGS**, or **WXS** depending on your requirement.

5. Download a **Manifest** file from the **top-right-hand button** on the portal.  
   *(An example of the manifest file is attached.)*

6. To map UUIDs to TCGA barcodes from the manifest file, use the script `manifest_to_TCGA_ID.R`.

---

### Downloading BAM Files Using gdc-client:

You will need a **user token** from the GDC web portal:  
- Under your username, download the token file.

To download BAM files, use the following command:  

```bash
gdc-client download -t gdc-user-token.2021-04-02.txt -m manifest-example.txt
