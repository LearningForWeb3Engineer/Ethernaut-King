# Ethernaut-King

Ethernaut King解題思路

<img width="513" height="467" alt="{0D497D49-B55E-4CCE-89C9-CB305D021600}" src="https://github.com/user-attachments/assets/ec9721a9-583c-4317-8a7c-b548902da2e1" />

***這題是在講解如果再receive()出現revert()所發生的情況***

這個挑戰的目標是要讓關卡無法重獲王位:關鍵就在於第二步的「舊王退款」邏輯

我們先部屬合約並傳入高於原本實例地址裡面的prize變成王之後再部屬攻擊合約

攻擊合約的內容很簡單:

<img width="590" height="417" alt="{5AF8AD51-E04B-4F39-9F47-2B1736C7B820}" src="https://github.com/user-attachments/assets/68226c76-0fbd-4e6d-b579-0481a855f10e" />


在receive()可以發現我們寫了revert，代表經過receive之後都會被退回，用意是如果有其他挑戰者現在的王(我們)，就算prize數量大於我們，都會被revert，所以king永遠都會是我們

Tips:這是經典的區塊鏈拒絕服務 (Denial of Service, DoS)攻擊。
