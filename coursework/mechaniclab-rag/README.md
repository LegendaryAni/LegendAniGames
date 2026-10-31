# MechanicLab — 遊戲機制 RAG 對話機器人（課堂作業）

本資料夾是原創課堂作業，不是既有遊戲的官方規則。
- RAG01：將 26 節原創設計文件切塊並以 multilingual-e5-small 向量化，建立 FAISS 索引。
- RAG02：透過公開的 rag-data.zip 載入索引，使用 AIsuite + Groq 或無金鑰 Qwen2.5-0.5B-Instruct 備援生成中文回答，並用 Gradio 互動。
- rag-data.zip：27 個檢索區塊，384 維 FAISS 向量，內含原始文件與校驗摘要。
- 使用者必須實際執行 Colab 並提供真實截圖。生成式 AI 曾協助設計文件、Prompt 與程式，不能宣稱完全自行撰寫。
  
**注意：** 此作業尚待 Colab 執行與學校 COOL 正式提交驗證；公開程式碼不代表完成繳交。
