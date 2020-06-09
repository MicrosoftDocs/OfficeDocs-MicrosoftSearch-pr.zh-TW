---
title: 連接器概述
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
description: Microsoft 搜尋的 Microsoft Graph 連接器概述
ms.openlocfilehash: 0b5420eb4eb93eb257fab30f3e56a20e6456e1b3
ms.sourcegitcommit: 64eea81f8c1db9ee955013462a7b51612fb7d0b7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/08/2020
ms.locfileid: "44604390"
---
# <a name="overview-of-microsoft-graph-connectors"></a><span data-ttu-id="0e769-103">Microsoft Graph 連接器的概述</span><span class="sxs-lookup"><span data-stu-id="0e769-103">Overview of Microsoft Graph connectors</span></span>

<span data-ttu-id="0e769-104">Microsoft 搜尋會索引您的所有[Microsoft 365](https://www.microsoft.com/microsoft-365)資料，讓其可供使用者搜尋。</span><span class="sxs-lookup"><span data-stu-id="0e769-104">Microsoft Search indexes all your [Microsoft 365](https://www.microsoft.com/microsoft-365) data to make it searchable for users.</span></span> <span data-ttu-id="0e769-105">透過 Microsoft Graph 連接器，您的組織可以索引協力廠商資料，以顯示在 Microsoft 搜尋結果中。</span><span class="sxs-lookup"><span data-stu-id="0e769-105">With Microsoft Graph connectors, your organization can index third-party data to appear in Microsoft Search results.</span></span> <span data-ttu-id="0e769-106">協力廠商資料可以位於內部部署或公用或私人雲端。</span><span class="sxs-lookup"><span data-stu-id="0e769-106">The third-party data can be hosted on-premises or in the public or private clouds.</span></span> <span data-ttu-id="0e769-107">連接器展開可在 Microsoft 365 生產力應用程式中搜尋的內容來源類型，以及更廣泛的 Microsoft 生態用。</span><span class="sxs-lookup"><span data-stu-id="0e769-107">Connectors expand the types of content sources that are searchable in your Microsoft 365 productivity apps and the broader Microsoft ecosystem.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="0e769-108">**免責聲明**： microsoft Graph 連接器和 microsoft Search APIs （查詢和索引）目前是針對目標版本中承租人可用的預覽狀態。</span><span class="sxs-lookup"><span data-stu-id="0e769-108">**DISCLAIMER**: Microsoft Graph connectors and Microsoft Search APIs (query and index) are currently in preview status available for tenants in Targeted release.</span></span> <span data-ttu-id="0e769-109">若要在 Microsoft 搜尋中使用連接器，或建立連接器，請選擇進入[目標版本](https://docs.microsoft.com/office365/admin/manage/release-options-in-office-365?view=o365-worldwide)。</span><span class="sxs-lookup"><span data-stu-id="0e769-109">To use connectors with Microsoft Search or to build connectors, opt into [Targeted release](https://docs.microsoft.com/office365/admin/manage/release-options-in-office-365?view=o365-worldwide).</span></span> <span data-ttu-id="0e769-110">若要深入瞭解預覽，請參閱[連接器預覽程式](connectors-preview.md)。</span><span class="sxs-lookup"><span data-stu-id="0e769-110">To learn more about the preview, see [connectors preview program](connectors-preview.md).</span></span>

## <a name="architecture"></a><span data-ttu-id="0e769-111">架構</span><span class="sxs-lookup"><span data-stu-id="0e769-111">Architecture</span></span>

<span data-ttu-id="0e769-112">Microsoft Graph 平臺的下列架構圖表顯示在[Microsoft Search](https://docs.microsoft.com/microsoftsearch/overview-microsoft-search)用戶端中，連接器內容如何透過內容索引傳送至使用者結果。</span><span class="sxs-lookup"><span data-stu-id="0e769-112">The following architectural diagram of the Microsoft Graph platform shows how connector content flows through content indexing to user results in [Microsoft Search](https://docs.microsoft.com/microsoftsearch/overview-microsoft-search) clients.</span></span> <span data-ttu-id="0e769-113">本文說明 Microsoft Graph 連接器資料流程處理常式中的每個主要組建區塊。</span><span class="sxs-lookup"><span data-stu-id="0e769-113">This article explains each of the key building blocks in the Microsoft Graph connectors data flow process.</span></span>

![圖表：內部部署和雲端式資料是由連接器所提取，並由 Microsoft Search API 編制索引，然後 Microsoft Search 服務會將結果傳遞給使用者。](media/highlevel-connectors_FINAL.png)

<span data-ttu-id="0e769-115">API 會為每個資料來源具現化一個連接。</span><span class="sxs-lookup"><span data-stu-id="0e769-115">The API instantiates one connection per data source.</span></span> <span data-ttu-id="0e769-116">然後，API 便會編制索引並儲存資料。</span><span class="sxs-lookup"><span data-stu-id="0e769-116">Then the API indexes and stores the data.</span></span> <span data-ttu-id="0e769-117">已建立的連線會與 Microsoft 搜尋互動，讓使用者可以取得搜尋結果。</span><span class="sxs-lookup"><span data-stu-id="0e769-117">Established connections interact with Microsoft Search, so users can get search results.</span></span>

<span data-ttu-id="0e769-118">您可以在 Microsoft 365 系統[管理中心](https://admin.microsoft.com)內設定所有的 microsoft 建連接器。</span><span class="sxs-lookup"><span data-stu-id="0e769-118">You can configure all the Microsoft-built connectors in the Microsoft 365 [admin center](https://admin.microsoft.com).</span></span> <span data-ttu-id="0e769-119">系統管理中心簡化了使用簡易使用者介面設定連接器的工作。</span><span class="sxs-lookup"><span data-stu-id="0e769-119">The admin center simplifies configuring your connector with a simple user interface.</span></span>

<span data-ttu-id="0e769-120">若要建立資料**源的連線**，系統管理員必須對資料和整個內容存放庫進行驗證存取。</span><span class="sxs-lookup"><span data-stu-id="0e769-120">To create a **connection** to a data source, admins need authenticated access to the data and the entire content repository.</span></span> <span data-ttu-id="0e769-121">資料會送到圖形連接器服務以編制索引。</span><span class="sxs-lookup"><span data-stu-id="0e769-121">The data is fed to the graph connector service for indexing.</span></span>

## <a name="available-connectors"></a><span data-ttu-id="0e769-122">可用連接器</span><span class="sxs-lookup"><span data-stu-id="0e769-122">Available connectors</span></span>

<span data-ttu-id="0e769-123">目前有6個 Microsoft 構建的連接器，而且我們的生態系統合作夥伴可提供超過100的連接器。</span><span class="sxs-lookup"><span data-stu-id="0e769-123">There are currently 6 Microsoft-built connectors, and over 100 connectors are available from our ecosystem partners.</span></span>

<span data-ttu-id="0e769-124">若要從其中一個生態系統合作夥伴預覽連接器，請直接與他們聯繫。</span><span class="sxs-lookup"><span data-stu-id="0e769-124">To preview connectors from one of our ecosystem partners, contact them directly.</span></span> <span data-ttu-id="0e769-125">如需詳細資訊，請參閱[Microsoft Graph 連接器圖庫](connectors-gallery.md)。</span><span class="sxs-lookup"><span data-stu-id="0e769-125">For more information, see the [Microsoft Graph connectors gallery](connectors-gallery.md).</span></span>

<span data-ttu-id="0e769-126">您也可以[建立您自己的連接器](https://docs.microsoft.com/graph/search-concept-overview)。</span><span class="sxs-lookup"><span data-stu-id="0e769-126">You can also [build your own connector](https://docs.microsoft.com/graph/search-concept-overview).</span></span>

### <a name="connectors-by-microsoft"></a><span data-ttu-id="0e769-127">Microsoft 的連接器</span><span class="sxs-lookup"><span data-stu-id="0e769-127">Connectors by Microsoft</span></span>

<span data-ttu-id="0e769-128">Microsoft Graph 連接器預覽版本包含6個 Microsoft 建立的連接器。</span><span class="sxs-lookup"><span data-stu-id="0e769-128">The Microsoft Graph connectors preview release includes 6 Microsoft-built connectors.</span></span> <span data-ttu-id="0e769-129">您可以在系統[管理中心](https://admin.microsoft.com)進行設定，並瞭解如何[設定您的 Microsoft 建連接器](configure-connector.md)。</span><span class="sxs-lookup"><span data-stu-id="0e769-129">You can set them up in the [admin center](https://admin.microsoft.com) and learn how to [Set up your Microsoft-built connector](configure-connector.md).</span></span>

<span data-ttu-id="0e769-130">下列各節提供這些 Microsoft 建立連接器的簡短描述。</span><span class="sxs-lookup"><span data-stu-id="0e769-130">The following sections provide brief descriptions for these Microsoft-built connectors.</span></span> <span data-ttu-id="0e769-131">您可以在每個連接器的連結文章中取得詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="0e769-131">You can get more information in the linked articles for each connector.</span></span>

- <span data-ttu-id="0e769-132">**[Azure Data Lake Storage Gen2](https://docs.microsoft.com/azure/storage/blobs/data-lake-storage-introduction)**。</span><span class="sxs-lookup"><span data-stu-id="0e769-132">**[Azure Data Lake Storage Gen2](https://docs.microsoft.com/azure/storage/blobs/data-lake-storage-introduction)**.</span></span> <span data-ttu-id="0e769-133">透過此 Microsoft Graph 連接器，您組織中的使用者可以搜尋 Azure Blob 容器中儲存的檔案和內容。</span><span class="sxs-lookup"><span data-stu-id="0e769-133">With this Microsoft Graph connector, users in your organization can search for files and content stored in Azure Blob containers.</span></span> <span data-ttu-id="0e769-134">Azure Data Lake Storage Gen2 connector 也會為您指定的 Azure Data Lake Storage Gen2 帳戶中的已啟用階層的資料夾編制索引。</span><span class="sxs-lookup"><span data-stu-id="0e769-134">The Azure Data Lake Storage Gen2 connector also indexes hierarchy-enabled folders in Azure Data Lake Storage Gen2 accounts that you specify.</span></span>
<span data-ttu-id="0e769-135">深入瞭解[Azure Data Lake Storage Gen2 connector](azure-data-lake-connector.md)。</span><span class="sxs-lookup"><span data-stu-id="0e769-135">Learn more about the [Azure Data Lake Storage Gen2 connector](azure-data-lake-connector.md).</span></span>

- <span data-ttu-id="0e769-136">**企業網站**。</span><span class="sxs-lookup"><span data-stu-id="0e769-136">**Enterprise websites**.</span></span> <span data-ttu-id="0e769-137">透過此 Microsoft Graph 連接器，您組織中的使用者可以在任何非 SharePoint 企業網站中搜尋頁面。</span><span class="sxs-lookup"><span data-stu-id="0e769-137">With this Microsoft Graph connector, users in your organization can search over pages in any non-SharePoint enterprise website.</span></span>
<span data-ttu-id="0e769-138">深入瞭解[企業網站連接器](enterprise-web-connector.md)。</span><span class="sxs-lookup"><span data-stu-id="0e769-138">Learn more about the [Enterprise websites connector](enterprise-web-connector.md).</span></span>

- <span data-ttu-id="0e769-139">**檔共用**。</span><span class="sxs-lookup"><span data-stu-id="0e769-139">**File share**.</span></span> <span data-ttu-id="0e769-140">透過此 Microsoft Graph 連接器，您組織中的使用者可以搜尋儲存在內部部署 Windows 檔案共用上的檔案。</span><span class="sxs-lookup"><span data-stu-id="0e769-140">With this Microsoft Graph connector, users in your organization can search for files stored on on-premises Windows file shares.</span></span>
<span data-ttu-id="0e769-141">深入瞭解檔案[共用連接器](file-share-connector.md)。</span><span class="sxs-lookup"><span data-stu-id="0e769-141">Learn more about the [File share connector](file-share-connector.md).</span></span>

- <span data-ttu-id="0e769-142">**[MediaWiki](https://www.mediawiki.org/wiki/MediaWiki)**。</span><span class="sxs-lookup"><span data-stu-id="0e769-142">**[MediaWiki](https://www.mediawiki.org/wiki/MediaWiki)**.</span></span> <span data-ttu-id="0e769-143">使用此 Microsoft Graph 連接器，使用者可以在您的組織以 MediaWiki 所建立的 wiki 網站上搜尋知識文庫文章。</span><span class="sxs-lookup"><span data-stu-id="0e769-143">With this Microsoft Graph connector, users can search for knowledge-base articles on wiki sites your organization creates with MediaWiki.</span></span>
<span data-ttu-id="0e769-144">深入瞭解[MediaWiki 連接器](mediawiki-connector.md)。</span><span class="sxs-lookup"><span data-stu-id="0e769-144">Learn more about the [MediaWiki connector](mediawiki-connector.md).</span></span>

- <span data-ttu-id="0e769-145">**[MICROSOFT SQL server](https://www.microsoft.com/sql-server/sql-server-2017)**。</span><span class="sxs-lookup"><span data-stu-id="0e769-145">**[Microsoft SQL server](https://www.microsoft.com/sql-server/sql-server-2017)**.</span></span> <span data-ttu-id="0e769-146">透過此 Microsoft Graph 連接器，您組織中的使用者可以搜尋內部部署 SQL server 資料庫中的資料。</span><span class="sxs-lookup"><span data-stu-id="0e769-146">With this Microsoft Graph connector, users in your organization can search for data in on-premises SQL server databases.</span></span>
<span data-ttu-id="0e769-147">深入瞭解[MICROSOFT SQL server connector](MSSQL-connector.md)。</span><span class="sxs-lookup"><span data-stu-id="0e769-147">Learn more about the [Microsoft SQL server connector](MSSQL-connector.md).</span></span>

- <span data-ttu-id="0e769-148">**[ServiceNow](https://www.servicenow.com)**。</span><span class="sxs-lookup"><span data-stu-id="0e769-148">**[ServiceNow](https://www.servicenow.com)**.</span></span> <span data-ttu-id="0e769-149">透過此 Microsoft Graph 連接器，您組織中的使用者可以從您的 ServiceNow 實例搜尋知識庫文章。</span><span class="sxs-lookup"><span data-stu-id="0e769-149">With this Microsoft Graph connector, users in your organization can search for knowledge-base articles from your ServiceNow instance.</span></span>
<span data-ttu-id="0e769-150">深入瞭解[ServiceNow 連接器](servicenow-connector.md)。</span><span class="sxs-lookup"><span data-stu-id="0e769-150">Learn more about the [ServiceNow connector](servicenow-connector.md).</span></span>

### <a name="connectors-from-our-partners"></a><span data-ttu-id="0e769-151">合作夥伴的連接器</span><span class="sxs-lookup"><span data-stu-id="0e769-151">Connectors from our partners</span></span>

<span data-ttu-id="0e769-152">我們的生態系統合作夥伴可供預覽超過100個連接器。</span><span class="sxs-lookup"><span data-stu-id="0e769-152">There are over 100 connectors available for preview from our ecosystem partners.</span></span> <span data-ttu-id="0e769-153">若要從其中一個生態系統合作夥伴預覽連接器，請直接與他們聯繫。</span><span class="sxs-lookup"><span data-stu-id="0e769-153">To preview connectors from one of our ecosystem partners, contact them directly.</span></span>
<span data-ttu-id="0e769-154">深入瞭解[Microsoft Graph 連接器圖庫](connectors-gallery.md)中合作夥伴的連接器。</span><span class="sxs-lookup"><span data-stu-id="0e769-154">Learn more about connectors from our partners in the [Microsoft Graph connectors gallery](connectors-gallery.md).</span></span>

### <a name="build-your-own-connector"></a><span data-ttu-id="0e769-155">建立您自己的連接器</span><span class="sxs-lookup"><span data-stu-id="0e769-155">Build your own connector</span></span>

<span data-ttu-id="0e769-156">若要編制自訂資料類型或檔案的索引，開發人員可以在[Microsoft Graph](https://developer.microsoft.com/graph/)中建立連接器。</span><span class="sxs-lookup"><span data-stu-id="0e769-156">To index custom data types or files, developers can create connectors in [Microsoft Graph](https://developer.microsoft.com/graph/).</span></span> <span data-ttu-id="0e769-157">連接器是[建立](https://docs.microsoft.com/graph/search-index-manage-connections)連線並將專案推入 Microsoft 搜尋索引的應用程式。</span><span class="sxs-lookup"><span data-stu-id="0e769-157">A connector is an application that [creates a connection](https://docs.microsoft.com/graph/search-index-manage-connections) and pushes items into the Microsoft Search index.</span></span> <span data-ttu-id="0e769-158">如需詳細資訊，請參閱[為 Microsoft Graph 上的應用程式擴充 Microsoft 搜尋體驗的概述](https://docs.microsoft.com/graph/search-concept-overview)。</span><span class="sxs-lookup"><span data-stu-id="0e769-158">For more information, see the [Overview for extending the Microsoft Search experience for apps on Microsoft Graph](https://docs.microsoft.com/graph/search-concept-overview).</span></span>

### <a name="search-results-with-your-custom-built-connector"></a><span data-ttu-id="0e769-159">使用自訂內置連接器的搜尋結果</span><span class="sxs-lookup"><span data-stu-id="0e769-159">Search results with your custom-built connector</span></span>

<span data-ttu-id="0e769-160">在索引自訂資料之後，開發人員可以[查詢此資料](https://docs.microsoft.com/graph/search-concept-custom-types)。</span><span class="sxs-lookup"><span data-stu-id="0e769-160">After custom data is indexed, developers can [query this data](https://docs.microsoft.com/graph/search-concept-custom-types).</span></span> <span data-ttu-id="0e769-161">您可以在任何應用程式中查看資料。</span><span class="sxs-lookup"><span data-stu-id="0e769-161">You can view your data in any application.</span></span> <span data-ttu-id="0e769-162">如需詳細資訊，請參閱[為 Microsoft Graph 上的應用程式擴充 Microsoft 搜尋體驗的概述](https://docs.microsoft.com/graph/search-concept-overview)。</span><span class="sxs-lookup"><span data-stu-id="0e769-162">For more information, see the [Overview for extending the Microsoft Search experience for apps on Microsoft Graph](https://docs.microsoft.com/graph/search-concept-overview).</span></span>

## <a name="license-requirements"></a><span data-ttu-id="0e769-163">授權需求</span><span class="sxs-lookup"><span data-stu-id="0e769-163">License requirements</span></span>

<span data-ttu-id="0e769-164">若要在搜尋結果中查看連接器的資料，使用者必須具備下列其中一種 Microsoft 365 訂閱：</span><span class="sxs-lookup"><span data-stu-id="0e769-164">To view data from connectors in your search results, users must have one of the following Microsoft 365 subscriptions:</span></span>

- [<span data-ttu-id="0e769-165">適用于企業版 E3 或 E5 的 Microsoft 365</span><span class="sxs-lookup"><span data-stu-id="0e769-165">Microsoft 365 for enterprise E3 or E5</span></span>](https://www.microsoft.com/microsoft-365/compare-all-microsoft-365-plans)

- [<span data-ttu-id="0e769-166">Microsoft 365 教育版 A3 或 A5</span><span class="sxs-lookup"><span data-stu-id="0e769-166">Microsoft 365 Education A3 or A5</span></span>](https://www.microsoft.com/microsoft-365/academic/compare-office-365-education-plans?activetab=tab:primaryr1)