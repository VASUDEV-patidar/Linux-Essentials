## **🔹 Hard Link और Soft Link (Symbolic Link) in Linux   

Linux में **Hard Link** और **Soft Link (Symbolic Link)** का उपयोग files को refer करने के लिए किया जाता है। ये **shortcut** की तरह काम करते हैं, लेकिन इनके बीच कुछ major differences होते हैं।  

---

## **📌 1. Hard Link Kya Hota Hai?**  
🔹 **Hard Link** एक reference होता है, जो original file के **same inode number** को point करता है।  
🔹 Hard link बनाने के बाद, **original file delete करने पर भी data safe रहता है**।  
🔹 दोनों files एक ही physical data को share करती हैं।  

👉 **Hard Link बनाने की Command:**  
```bash
ln existing_file hard_link_file
```
🔹 Example:  
```bash
ln myfile.txt myfile_hardlink.txt
```

👉 **Hard Link Check करने के लिए:**  
```bash
ls -li myfile.txt myfile_hardlink.txt
```
💡 **Same inode number मिलेगा, क्योंकि दोनों files एक ही data को point करती हैं।**  

---

## **📌 2. Soft Link (Symbolic Link) Kya Hota Hai?**  
🔹 **Soft Link (Symbolic Link)** एक **shortcut** की तरह काम करता है।  
🔹 यह original file को refer करता है, लेकिन **अलग inode number** होता है।  
🔹 अगर original file **delete** हो जाए, तो soft link **काम नहीं करेगा**।  

👉 **Soft Link बनाने की Command:**  
```bash
ln -s existing_file soft_link_file
```
🔹 Example:  
```bash
ln -s myfile.txt myfile_symlink.txt
```

👉 **Soft Link Check करने के लिए:**  
```bash
ls -l myfile_symlink.txt
```
💡 **Soft link arrow (`->`) के साथ show होगा, जिससे पता चलता है कि यह किसी दूसरी file को refer कर रहा है।**  

---

## **📌 3. Difference Between Hard Link and Soft Link**  

| Feature          | Hard Link | Soft Link |
|-----------------|-----------|-----------|
| Inode Number   | Same as original file | Different inode number |
| Storage        | Data को directly point करता है | सिर्फ original file का path store करता है |
| File Deletion  | Original file delete करने पर भी data safe रहता है | Original file delete होने पर link टूट जाता है |
| Different File Systems | सिर्फ **same file system** में काम करता है | **Different file systems** पर काम कर सकता है |
| Directory के लिए Support | **Directly directory पर apply नहीं कर सकते** | **Directories पर apply किया जा सकता है** |

---

## **📌 4. Quick Summary**
✅ **Hard Link** → Data को directly refer करता है, same inode number share करता है, और original file delete करने पर भी safe रहता है।  
✅ **Soft Link** → Shortcut की तरह काम करता है, अलग inode number होता है, और original file delete होने पर break हो जाता है।  
✅ **Hard Link सिर्फ same filesystem में काम करता है, जबकि Soft Link किसी भी filesystem में।**  

