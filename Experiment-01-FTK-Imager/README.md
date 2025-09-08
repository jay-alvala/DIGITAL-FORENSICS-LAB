# Experiment 1: Evidence Acquisition Using AccessData FTK Imager
**Experiment No:** 1  

---

## 🎯 Objective
To acquire forensic evidence from a computer system using **FTK Imager**, including both volatile memory (RAM) and non-volatile memory (hard disks), while maintaining data integrity.

---

## 🛠 Tools Used
- **FTK Imager (AccessData)**  
- Windows OS  
- USB Pen Drive / HDD (for portable usage)  
- Write Blocker (for safe disk mounting)

---

## 📋 Procedure

### 1️⃣ Acquiring Volatile Memory (RAM)
1. Open **FTK Imager** and navigate to the **Capture Memory** icon.  
2. Choose options to include:
   - **Pagefile.sys** – contains overflow RAM data.  
   - **AD1 file** – FTK Imager image file for later use.  
3. Click **Capture Memory** to start acquisition.  
4. Once completed, the memory image will be saved with the extension `.mem`.  

**NOTE:** Pagefile and AD1 files can contain valuable evidence and should be collected.

---

### 2️⃣ Acquiring Non-Volatile Memory (Disk Image)
1. Open **FTK Imager** and select **Create Disk Image**.  
2. Select the source to acquire:
   - Physical drive, logical drive, image file, folder, or CD/DVD.  
   - Use a **write blocker** if connecting external HDDs.  
3. Choose **Physical Drive** and select the drive to acquire.  
4. Select the image format:
   - **Raw (dd)** – standard raw image with no headers/metadata.  
   - **SMART** – Linux-oriented image with headers and sections.  
   - **E01** – proprietary EnCase format with compression & case info.  
   - **AFF/AFF4** – advanced forensic format (non-proprietary).  
5. Enter **case details** (examiner name, date, notes).  
6. Add **destination folder**, **image file name**, and **fragment size** (0 for single file).  
7. Select **Verify images after creation** to confirm hash values.  
8. Click **Start** to acquire the disk image.  

Once acquisition is complete, FTK Imager will generate:
- Disk image file(s)  
- A text report including all acquisition information  
- Verified **hash values**  

---

## 📷 Screenshots
### Volatile Memory (RAM) Capture
![Step 1](Screenshots/e1p1.png)
![Step 2](Screenshots/e1p2.png)
![Step 3](Screenshots/e1p3.png)

### Disk Image Acquisition
![Step 4](Screenshots/e1p4.png)
![Step 5](Screenshots/e1p5.png)
![Step 6](Screenshots/e1p6.png)
![Step 7](Screenshots/e1p7.png)
![Step 8](Screenshots/e1p8.png)

### Verification & Results
![Step 9](Screenshots/e1p9.png)
![Step 10](Screenshots/e1p10.png)
![Step 11](Screenshots/e1p11.png)

---

## ✅ Result
- Successfully acquired volatile and non-volatile memory.  
- Maintained integrity using write blocker and hash verification.  
- Evidence ready for further forensic analysis.

---

## 📂 References
- FTK Imager User Guide – AccessData  
- Lab manual

