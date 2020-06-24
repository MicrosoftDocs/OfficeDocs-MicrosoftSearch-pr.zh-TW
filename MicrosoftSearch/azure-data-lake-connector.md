---
title: Microsoft 搜尋的 Azure Data Lake connector
ms.author: mounika.narayanan
author: monaray
manager: shohara
ms.audience: Admin
ms.topic: article
ms.service: mssearch
localization_priority: Normal
search.appverid:
- BFB160
- MET150
- MOE150
description: 設定 Azure Data Lake Storage Gen2 connector for Microsoft Search
ms.openlocfilehash: f8cb94e806e619d6dae7258b6c2d708d93afb9a8
ms.sourcegitcommit: 7eda9b621def0659d7e7bc8b989f8adc929cce93
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/24/2020
ms.locfileid: "44861074"
---
# <a name="azure-data-lake-storage-gen2-connector"></a><span data-ttu-id="89b9c-103">Azure Data Lake Storage Gen2 connector</span><span class="sxs-lookup"><span data-stu-id="89b9c-103">Azure Data Lake Storage Gen2 connector</span></span>

<span data-ttu-id="89b9c-104">透過[Azure Data Lake Storage Gen2](https://docs.microsoft.com/azure/storage/blobs/data-lake-storage-introduction) connector，您組織中的使用者便可搜尋檔案及其內容。</span><span class="sxs-lookup"><span data-stu-id="89b9c-104">With the [Azure Data Lake Storage Gen2](https://docs.microsoft.com/azure/storage/blobs/data-lake-storage-introduction) connector, users in your organization can search for files and their content.</span></span> <span data-ttu-id="89b9c-105">此連接器會存取 Azure Data Lake Storage Gen 2 帳戶內，Azure Blob 容器和已啟用階層的資料夾中儲存的資料。</span><span class="sxs-lookup"><span data-stu-id="89b9c-105">This connector accesses data stored in Azure Blob containers and hierarchy-enabled folders within an Azure Data Lake Storage Gen 2 account.</span></span>

<span data-ttu-id="89b9c-106">本文適用于[Microsoft 365](https://www.microsoft.com/microsoft-365)系統管理員或任何設定、執行及監視 Azure Data Lake Storage Gen2 connector 的人員。</span><span class="sxs-lookup"><span data-stu-id="89b9c-106">This article is for [Microsoft 365](https://www.microsoft.com/microsoft-365) administrators or anyone who configures, runs, and monitors an Azure Data Lake Storage Gen2 connector.</span></span> <span data-ttu-id="89b9c-107">它說明如何設定連接器和連接器功能、限制及疑難排解技術。</span><span class="sxs-lookup"><span data-stu-id="89b9c-107">It explains how to configure your connector and connector capabilities, limitations, and troubleshooting techniques.</span></span>

## <a name="connect-to-a-data-source"></a><span data-ttu-id="89b9c-108">連接到資料來源</span><span class="sxs-lookup"><span data-stu-id="89b9c-108">Connect to a data source</span></span>

### <a name="primary-storage-connection-string"></a><span data-ttu-id="89b9c-109">主要儲存連接字串</span><span class="sxs-lookup"><span data-stu-id="89b9c-109">Primary storage connection string</span></span> 
<span data-ttu-id="89b9c-110">在 [**驗證] 和 [config** ] 畫面上，提供主要儲存連接字串。</span><span class="sxs-lookup"><span data-stu-id="89b9c-110">On the **Authentication and config** screen, provide the Primary Storage Connection String.</span></span> <span data-ttu-id="89b9c-111">該字串是允許存取您的儲存體帳戶所需的字串。</span><span class="sxs-lookup"><span data-stu-id="89b9c-111">That string is required to allow access to your storage account.</span></span> <span data-ttu-id="89b9c-112">若要尋找您的連線字串，請移至[azure 入口網站](https://ms.portal.azure.com/#home)，並流覽至[Azure Data Lake Storage Gen2](https://docs.microsoft.com/azure/storage/blobs/data-lake-storage-introduction)帳戶的 [機**碼**] 區段。</span><span class="sxs-lookup"><span data-stu-id="89b9c-112">To find your connection string, go to the [Azure portal](https://ms.portal.azure.com/#home) and navigate to the **Keys** section of the [Azure Data Lake Storage Gen2](https://docs.microsoft.com/azure/storage/blobs/data-lake-storage-introduction) account.</span></span> <span data-ttu-id="89b9c-113">在螢幕上適當的欄位中複製並貼上連接字串。</span><span class="sxs-lookup"><span data-stu-id="89b9c-113">Copy and paste the connection string in the appropriate field on the screen.</span></span>

<span data-ttu-id="89b9c-114">如果您不想要提供**AccountKey** （主要儲存連接字串中的參數），您必須授與我們的圖形連接器服務的讀取權限。</span><span class="sxs-lookup"><span data-stu-id="89b9c-114">If you don't want to provide the **AccountKey** (a parameter in the primary storage connection string), you have to grant read access to our Graph Connectors Service.</span></span> <span data-ttu-id="89b9c-115">在您 Azure Data Lake Storage Gen2 帳戶的 [**存取控制**] 索引標籤中，依照該頁面上的指示，將存取權授與下列應用程式：</span><span class="sxs-lookup"><span data-stu-id="89b9c-115">In the **Access Control** tab of your Azure Data Lake Storage Gen2 account, follow the instructions on that page to grant access to the following app:</span></span>
* <span data-ttu-id="89b9c-116">**第一方應用程式 ID:** 56c1da01-2129-48f7-9355-af6d59d42766</span><span class="sxs-lookup"><span data-stu-id="89b9c-116">**First Party App ID:** 56c1da01-2129-48f7-9355-af6d59d42766</span></span>
* <span data-ttu-id="89b9c-117">**第一方應用程式名稱：** 圖形連接器服務</span><span class="sxs-lookup"><span data-stu-id="89b9c-117">**First Party App Name:** Graph Connector Service</span></span>

### <a name="storage-account-and-queue-notifications-optional"></a><span data-ttu-id="89b9c-118">儲存帳戶和佇列通知（選用）</span><span class="sxs-lookup"><span data-stu-id="89b9c-118">Storage account and queue notifications (Optional)</span></span>
<span data-ttu-id="89b9c-119">可在未來新增圖表連接器服務中即時處理變更的支援。</span><span class="sxs-lookup"><span data-stu-id="89b9c-119">Support to process changes in real time in the Graph Connectors Service might be added in the future.</span></span> <span data-ttu-id="89b9c-120">在這種情況下，我們會監視[Azure Data Lake Storage Gen2](https://docs.microsoft.com/azure/storage/blobs/data-lake-storage-introduction) change 通知儲存在佇列中。</span><span class="sxs-lookup"><span data-stu-id="89b9c-120">In that case, we'll monitor [Azure Data Lake Storage Gen2](https://docs.microsoft.com/azure/storage/blobs/data-lake-storage-introduction) change notifications stored in a queue.</span></span> <span data-ttu-id="89b9c-121">您必須使用與您的 Azure Data Lake Storage Gen2 或其他儲存體帳戶相同的帳戶建立佇列。</span><span class="sxs-lookup"><span data-stu-id="89b9c-121">You'll need to create a queue in the same account as your Azure Data Lake Storage Gen2 or in another storage account.</span></span>

<span data-ttu-id="89b9c-122">建立佇列之後，請移至佇列頁面上的 [**事件**] 索引標籤，以設定**事件訂閱**。</span><span class="sxs-lookup"><span data-stu-id="89b9c-122">After you create a queue, go to the **Events** tab on the queue page to configure **Event Subscription**.</span></span> <span data-ttu-id="89b9c-123">選擇佇列將要接收的所有 Blob 事件，並將該佇列連接至 Azure Data Lake Storage Gen2 帳戶。</span><span class="sxs-lookup"><span data-stu-id="89b9c-123">Choose all the Blob events that the queue will receive, and connect the queue to the Azure Data Lake Storage Gen2 account.</span></span>

## <a name="manage-the-search-schema"></a><span data-ttu-id="89b9c-124">管理搜尋結構描述</span><span class="sxs-lookup"><span data-stu-id="89b9c-124">Manage the search schema</span></span>
<span data-ttu-id="89b9c-125">在 [**管理架構**] 畫面上，您可以選擇變更與 managed 屬性相關聯的架構屬性（可**查詢** **、可**搜尋及可**檢索**）。</span><span class="sxs-lookup"><span data-stu-id="89b9c-125">On the **Manage Schema** screen, you have the option to change the schema attributes (**queryable**, **searchable**, and **retrievable**) associated with the managed properties.</span></span> <span data-ttu-id="89b9c-126">這些 managed 屬性屬性是從[Azure Data Lake Storage Gen2](https://docs.microsoft.com/azure/storage/blobs/data-lake-storage-introduction)帳戶編制索引的資料。</span><span class="sxs-lookup"><span data-stu-id="89b9c-126">These managed property attributes are data indexed from your [Azure Data Lake Storage Gen2](https://docs.microsoft.com/azure/storage/blobs/data-lake-storage-introduction) account.</span></span>

## <a name="manage-search-permissions"></a><span data-ttu-id="89b9c-127">管理搜尋許可權</span><span class="sxs-lookup"><span data-stu-id="89b9c-127">Manage search permissions</span></span>
<span data-ttu-id="89b9c-128">在 [**管理搜尋許可權**] 畫面上，您可以選擇從您的儲存體帳戶中攝取存取控制清單（ACLs）。</span><span class="sxs-lookup"><span data-stu-id="89b9c-128">On the **Manage search permissions** screen, you can choose to ingest the Access Control Lists (ACLs) from your storage account.</span></span> <span data-ttu-id="89b9c-129">當您設定這些搜尋許可權時，會根據指派給已登入之[Azure Active Directory](https://docs.microsoft.com/azure/active-directory/)使用者搜尋內容的許可權來裁切搜尋內容。</span><span class="sxs-lookup"><span data-stu-id="89b9c-129">When these search permissions are set, search content is trimmed based on the permissions assigned to the signed-in [Azure Active Directory](https://docs.microsoft.com/azure/active-directory/) user searching the content.</span></span> <span data-ttu-id="89b9c-130">或者，您也可以選擇讓組織中的所有人都可以看到從您的儲存體帳戶索引的所有內容。</span><span class="sxs-lookup"><span data-stu-id="89b9c-130">Alternatively, you can choose to make all the content indexed from your storage account visible to everyone in your organization.</span></span> <span data-ttu-id="89b9c-131">在此情況下，您組織中的每個人都可以存取您儲存體帳戶中的所有資料。</span><span class="sxs-lookup"><span data-stu-id="89b9c-131">In this case, everyone in your organization will have access to all the data in your storage account.</span></span>
 
## <a name="set-the-refresh-schedule"></a><span data-ttu-id="89b9c-132">設定重新整理排程</span><span class="sxs-lookup"><span data-stu-id="89b9c-132">Set the refresh schedule</span></span>
<span data-ttu-id="89b9c-133">在 [重新整理**設定**] 畫面上，您可以設定增量編目間隔和完整編目間隔。</span><span class="sxs-lookup"><span data-stu-id="89b9c-133">On the **Refresh Settings** screen, you can set the incremental crawl interval and the full crawl interval.</span></span> <span data-ttu-id="89b9c-134">針對增量編目， [Azure Data Lake Storage Gen2](https://docs.microsoft.com/azure/storage/blobs/data-lake-storage-introduction) connector 的預設間隔是15分鐘，完整編目則為一周。</span><span class="sxs-lookup"><span data-stu-id="89b9c-134">The default intervals for the [Azure Data Lake Storage Gen2](https://docs.microsoft.com/azure/storage/blobs/data-lake-storage-introduction) connector are 15 minutes for an incremental crawl and one week for a full crawl.</span></span>
 
## <a name="limitations"></a><span data-ttu-id="89b9c-135">限制</span><span class="sxs-lookup"><span data-stu-id="89b9c-135">Limitations</span></span>
<span data-ttu-id="89b9c-136">目前， [Azure Data Lake Storage Gen2](https://docs.microsoft.com/azure/storage/blobs/data-lake-storage-introduction)多通訊協定存取只適用于美國中西部、West Us、加拿大中央、東 Us、東亞、北歐、東 US2、東南亞、西亞、西 US2 和巴西南部等的地區。</span><span class="sxs-lookup"><span data-stu-id="89b9c-136">Currently, [Azure Data Lake Storage Gen2](https://docs.microsoft.com/azure/storage/blobs/data-lake-storage-introduction) Multi-Protocol Access is available only in the Central US, West Central US, Canada Central, East US, East Asia, North Europe, East US2, South East Asia, West Europe, West US, Australia East, Japan East, West US2, and Brazil South.</span></span>

<span data-ttu-id="89b9c-137">如需更新及詳細資訊，請參閱[在 Azure Data Lake Storage （預覽）上的多協定存取](https://docs.microsoft.com/azure/storage/blobs/data-lake-storage-multi-protocol-access)。</span><span class="sxs-lookup"><span data-stu-id="89b9c-137">For updates and more information, see  [Multi-protocol access on Azure Data Lake Storage (preview)](https://docs.microsoft.com/azure/storage/blobs/data-lake-storage-multi-protocol-access).</span></span>


