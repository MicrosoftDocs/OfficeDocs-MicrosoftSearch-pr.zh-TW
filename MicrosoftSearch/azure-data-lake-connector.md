---
title: Microsoft 搜尋的 Azure Data Lake Graph 連接器
ms.author: mecampos
author: mecampos
manager: umas
audience: Admin
ms.audience: Admin
ms.topic: article
ms.service: mssearch
localization_priority: Normal
search.appverid:
- BFB160
- MET150
- MOE150
description: 設定 Azure Data Lake Storage Gen2 Graph connector for Microsoft Search
ms.openlocfilehash: 2bb9570bc3b0a5adef7ac72ea1620c4f22a8aefb
ms.sourcegitcommit: f76ade4c8fed0fee9c36d067b3ca8288c6c980aa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2021
ms.locfileid: "50508884"
---
<!---Previous ms.author: monaray --->

# <a name="azure-data-lake-storage-gen2-graph-connector"></a>Azure Data Lake Storage Gen2 Graph connector

Azure Data Lake Storage Gen2 Graph connector 可讓您組織中的使用者搜尋 [Azure Blob 儲存區](https://docs.microsoft.com/azure/storage/blobs/storage-blobs-introduction) 和 [Azure Data Lake Gen 2 儲存體](https://docs.microsoft.com/azure/storage/blobs/data-lake-storage-introduction) 帳戶中儲存的檔案。

> [!NOTE]
> 請閱讀 [**您的圖形連接器文章設定**](configure-connector.md) ，以瞭解一般圖表連接器設定指示。

本文適用于任何設定、執行及監視 Azure Data Lake Storage Gen2 connector 的人員。 它會補充一般設定程式，並顯示只適用于 Azure Data Lake Storage Gen2 connector 的指示。 本文也包含 [限制](#limitations)的相關資訊。

在本文中，我們使用 *Azure Storage* 做為 [Azure Blob 儲存區](https://docs.microsoft.com/azure/storage/blobs/storage-blobs-introduction) 和 [Azure Data Lake Gen 2 儲存區](https://docs.microsoft.com/azure/storage/blobs/data-lake-storage-introduction)的一般字詞。

## <a name="step-1-add-a-graph-connector-in-the-microsoft-365-admin-center"></a>步驟1：在 Microsoft 365 系統管理中心新增圖表連接器

遵循一般 [設定指示](https://docs.microsoft.com/microsoftsearch/configure-connector)。
<!---If the above phrase does not apply, delete it and insert specific details for your data source that are different from general setup instructions.-->

## <a name="step-2-name-the-connection"></a>步驟2：命名連線

遵循一般 [設定指示](https://docs.microsoft.com/microsoftsearch/configure-connector)。
<!---If the above phrase does not apply, delete it and insert specific details for your data source that are different from general setup instructions.-->

## <a name="step-3-configure-the-connection-settings"></a>步驟3：設定連接設定

輸入您的主要儲存體連接字串。 此字串是允許存取您的儲存體帳戶所需的字串。 若要尋找您的連線字串，請移至 [Azure 入口網站](https://ms.portal.azure.com/#home) ，並流覽至相關 Azure 儲存體帳戶的 [機 **碼** ] 區段。

如果您不想要在主要儲存連接字串) 中提供 **AccountKey** (參數，請授與下列角色的圖形連接器服務存取權：

* 儲存體 Blob 資料讀取器
* 儲存佇列資料參與者
* 儲存 Blob Delegator

流覽至您的 Azure 儲存體帳戶的 [ **存取控制** ] 索引標籤，然後依照這裡的指示，將存取權授與下列應用程式：

* **第一方應用程式 ID:** 56c1da01-2129-48f7-9355-af6d59d42766
* **第一方應用程式名稱：** 圖形連接器服務

### <a name="storage-account-and-queue-notifications-optional"></a>儲存帳戶和佇列通知 (選用) 

可在未來新增圖表連接器服務中即時處理變更的支援。 在此情況下，我們會監視儲存在佇列中的 Azure 儲存體變更通知。 您必須使用與您的 Azure 儲存體帳戶相同的帳戶建立佇列。

建立佇列之後，請移至佇列頁面上的 [ **事件** ] 索引標籤，以設定 **事件訂閱**。 選擇佇列將要接收的所有 Blob 事件，並將該佇列連接至 Azure 儲存體帳戶。

## <a name="step-4-assign-property-labels"></a>步驟4：指派屬性標籤

您可以從選項的功能表中選擇，將 source 屬性指派給每個標籤。 這個步驟不是必要的，具有一些屬性標籤會提升搜尋相關性，並確保使用者的更好搜尋結果。

## <a name="step-5-manage-schema"></a>步驟5：管理架構

在 [ **管理架構** ] 畫面上，您可以變更與屬性相關聯的架構屬性、選項為 **查詢**、 **搜尋**、 **檢索** 及 **精煉**。 您也可以新增選擇性別名，並選擇 **Content** 屬性。

## <a name="step-6-manage-search-permissions"></a>步驟6：管理搜尋許可權

### <a name="azure-data-lake-gen-2"></a>Azure Data Lake Gen 2

您可以選擇從您的 [Azure Data Lake Gen 2 儲存體](https://docs.microsoft.com/azure/storage/blobs/data-lake-storage-introduction) 帳戶中 (ACLs) 上插入存取控制清單。 當您設定這些搜尋許可權時，會根據使用者在 [Azure Active Directory](https://docs.microsoft.com/azure/active-directory/)中簽署的許可權來裁切搜尋內容。 或者，您也可以選擇讓組織中的所有人都可以看到從您的儲存體帳戶索引的所有內容。 在此情況下，您組織中的每個人都可以存取您儲存體帳戶中的所有資料。

Azure Data Lake Storage Gen2 Graph connector 支援 **所有人都** 可以看到的搜尋許可權，或 **只有存取此資料來源的人員**。 可以存取每個專案的組織中的使用者看不見搜尋結果中顯示的索引資料。

### <a name="azure-blob-storage"></a>Azure Blob 儲存體

若要連線至 [Azure Blob 儲存](https://docs.microsoft.com/azure/storage/blobs/storage-blobs-introduction)，您組織中的所有人都會看到所有從設定之來源編制索引的內容。 Azure Blob 儲存區的 Blob 層級不支援存取控制清單。

## <a name="step-7-set-the-refresh-schedule"></a>步驟7：設定重新整理排程

在 [重新整理 **設定** ] 畫面上，您可以設定增量編目間隔和完整編目間隔。 針對增量編目，Azure Data Lake Storage Gen2 connector 的預設間隔是15分鐘，完整編目則為一周。

## <a name="step-8-review-connection"></a>步驟8：檢查連線

遵循一般 [設定指示](https://docs.microsoft.com/microsoftsearch/configure-connector)。
<!---If the above phrase does not apply, delete it and insert specific details for your data source that are different from general setup instructions.-->

<!---## Troubleshooting-->
<!---Insert troubleshooting recommendations for this data source-->

## <a name="limitations"></a>限制

無法針對 Azure Data Lake Storage Gen2 來源及另一種方式，重新設定 Azure Blob 儲存的已發佈連線。 在這種情況下，建議您設定新的連線。

此外，檔案的大小必須為 4 MB 或更少的時間，才能進行編目。 目前支援的檔案類型包括：

* Word (.docx、.docm、dotx、normal.dotm) 
* PowerPoint ( pptm，.pptx，potm，potx，ppam，. ppsm，. ppsx) 
* Excel ( .xlsx，xlsm) 
* 舊版 Office 格式 ( .doc、.dot 等 ) 
* Text ( .txt) 
* HTML
* PDF

不支援像影像 ( .jpg、.bmp 等 ) 等二進位檔案。 例如，如果 .docx 檔案只包含影像，它可能會略過，因為它未傳回任何內容。
