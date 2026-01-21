%pip install langchain langchain-community pymupdf langchain-openai chromadb pydantic
%restart_python
import os
from langchain_community.document_loaders import PyMuPDFLoader
pdf_path = "/Volumes/workspace/default/volume2/Healthcare1.pdf" #variable pdf_path
def load_pdf_with_langchain(pdf_path): #Defines a function
    loader = PyMuPDFLoader(pdf_path) #Creates a loader instance
    documents = loader.load()  # Load the PDF into LangChain’s document format 
    print (f"successfully loaded {len(documents)} document chunks from the pdf.") #Prints a status message using an f-string
    return documents
pdf_path = "/Volumes/workspace/default/volume2/Healthcare1.pdf" #Storing the location in variable
docs = load_pdf_with_langchain(pdf_path) # Extract the document chunks
# Let's view the first couple of chunks to see what we got
print("\n Sample Extracted Content:") #Prints a blank line (\n) then prints the text
for i, doc in enumerate(docs[:4]): #loop over the first 4 document page
    print(f"\n--- Chunk {i + 1} ---") #i + 1 is used to start  numbering at 1 instead of 0    
with open("/tmp/healthcare1_chunks.txt", "w", encoding="utf-8") as f: # Save chunks to a text file in /tmp
    for i, doc in enumerate(docs, start=1):
        f.write(f"--- Chunk {i} ---\n")
        f.write(doc.page_content + "\n\n")
from pathlib import Path

out_dir = Path("/Volumes/workspace/default/volume2/chunks")
out_dir.mkdir(
    parents=True,
    exist_ok=True
)

for i, doc in enumerate(docs, start=1):
    (out_dir / f"chunk_{i:04d}.txt").write_text(
        doc.page_content,
        encoding="utf-8"
    )

print(f"Saved {len(docs)} chunk files under {out_dir}")
