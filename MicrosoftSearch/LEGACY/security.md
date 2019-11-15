---
title: Microsoft Search 的安全性
ms.author: dawholl
author: dawholl
manager: kellis
ms.date: 9/12/2018
ms.audience: Admin
ms.topic: reference
ms.service: mssearch
localization_priority: Normal
search.appverid:
- BFB160
- MET150
- MOE150
ms.assetid: 50461cb9-8707-46c1-935a-1b9608a98800
ROBOTS: NOINDEX
description: 在使用 Microsoft Search 提供資訊給獲授權使用者的同時，保護企業的資料與使用者
ms.openlocfilehash: f76067890188bdab575a011f444f49211db466d3
ms.sourcegitcommit: 21361af7c244ffd6ff8689fd0ff0daa359bf4129
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/14/2019
ms.locfileid: "38626763"
---
# <a name="security-for-microsoft-search"></a><span data-ttu-id="a9bd7-103">Microsoft Search 的安全性</span><span class="sxs-lookup"><span data-stu-id="a9bd7-103">Security for Microsoft Search</span></span>

> [!IMPORTANT]
> <span data-ttu-id="a9bd7-104">本文章適用 Bing 系統管理入口網站中的 Microsoft Search。</span><span class="sxs-lookup"><span data-stu-id="a9bd7-104">This article applies to the Microsoft Search in Bing admin portal.</span></span> <span data-ttu-id="a9bd7-105">我們正在將入口網站移至 Microsoft 365 系統管理中心，完成之後將會移除 Bing 系統管理入口網站中的 Microsoft Search。</span><span class="sxs-lookup"><span data-stu-id="a9bd7-105">We’re moving the portal to the Microsoft 365 admin center, and then the Microsoft Search in Bing portal will be removed.</span></span> <span data-ttu-id="a9bd7-106">建議您使用 Microsoft 365 系統管理中心來開始。</span><span class="sxs-lookup"><span data-stu-id="a9bd7-106">We recommend that you use the Microsoft 365 admin center to get started.</span></span> <span data-ttu-id="a9bd7-107">[Microsoft Search 概觀](overview-microsoft-search.md)。</span><span class="sxs-lookup"><span data-stu-id="a9bd7-107">[Overview of Microsoft Search](overview-microsoft-search.md).</span></span>

<span data-ttu-id="a9bd7-108">透過企業級的安全性，Microsoft Search 可隨時保護您的使用者與資料。</span><span class="sxs-lookup"><span data-stu-id="a9bd7-108">With enterprise-grade security, Microsoft Search always keeps your users and data protected.</span></span>


## <a name="secure-by-default"></a><span data-ttu-id="a9bd7-109">預設安全性</span><span class="sxs-lookup"><span data-stu-id="a9bd7-109">Secure by default</span></span>

<span data-ttu-id="a9bd7-110">Microsoft Search 能隨時確保提出的要求皆透過 HTTPS。</span><span class="sxs-lookup"><span data-stu-id="a9bd7-110">Microsoft Search always ensures requests are made over HTTPS.</span></span> <span data-ttu-id="a9bd7-111">這道保護能確保連線受到端點對端點加密，強化安全性。</span><span class="sxs-lookup"><span data-stu-id="a9bd7-111">This safeguard ensures the connection is encrypted end-to-end for enhanced security.</span></span>
  
## <a name="authentication-and-authorization-with-azure-active-directory"></a><span data-ttu-id="a9bd7-112">搭配 Azure Active Directory 的驗證與授權</span><span class="sxs-lookup"><span data-stu-id="a9bd7-112">Authentication and authorization with Azure Active Directory</span></span>

<span data-ttu-id="a9bd7-113">Microsoft Search 的驗證已綁定至 Azure Active Directory。</span><span class="sxs-lookup"><span data-stu-id="a9bd7-113">Authentication for Microsoft Search is tied to Azure Active Directory.</span></span> <span data-ttu-id="a9bd7-114">當 Microsoft Search 使用者前往 Bing，Bing 標頭會顯示 Microsoft 帳戶以及公司或學校帳戶的登入選項。</span><span class="sxs-lookup"><span data-stu-id="a9bd7-114">When Microsoft Search users go to Bing, the Bing header will show sign-in options for a Microsoft account as well as a work or school account.</span></span> <span data-ttu-id="a9bd7-115">如果 Bing 無法判斷使用者是否為合格的參與者，使用者可以移至[探索 Microsoft Search](https://www.bing.com/business/explore) 頁面，該頁面會自動將使用者重新導向至組織的登入頁面。</span><span class="sxs-lookup"><span data-stu-id="a9bd7-115">If Bing can't determine whether a user is an eligible participant, users can go to the [Explore Microsoft Search](https://www.bing.com/business/explore) page, where they'll be automatically redirected to your organization's sign-in page.</span></span>
  
<span data-ttu-id="a9bd7-116">使用者僅能透過公司或學校帳戶存取 Microsoft Search。</span><span class="sxs-lookup"><span data-stu-id="a9bd7-116">Users can access Microsoft Search only through a work or school account.</span></span> <span data-ttu-id="a9bd7-117">若要登入，他們必須使用與存取 Office 365 服務 (例如 SharePoint 或 Outlook) 相同的認證。</span><span class="sxs-lookup"><span data-stu-id="a9bd7-117">They need to sign in with the same credentials they use to access Office 365 services such as SharePoint or Outlook.</span></span> <span data-ttu-id="a9bd7-118">個人 Microsoft 帳戶無法用來登入 Microsoft Search。</span><span class="sxs-lookup"><span data-stu-id="a9bd7-118">A personal Microsoft account can't be used to sign in to Microsoft Search.</span></span>
  
<span data-ttu-id="a9bd7-119">使用者無法同時使用 Microsoft 帳戶和公司或學校帳戶登入 Bing。</span><span class="sxs-lookup"><span data-stu-id="a9bd7-119">Users can't be signed in to Bing with both a Microsoft account and a work or school account at the same time.</span></span>
  
## <a name="single-sign-on"></a><span data-ttu-id="a9bd7-120">單一登入</span><span class="sxs-lookup"><span data-stu-id="a9bd7-120">Single sign-on</span></span>

<span data-ttu-id="a9bd7-121">如果使用者已在其他服務 (例如 Outlook 或 SharePoint) 中以公司或學校帳戶通過驗證，那當他們在同個瀏覽器中移至 Bing 時，系統便會自動登入 Microsoft Search。</span><span class="sxs-lookup"><span data-stu-id="a9bd7-121">If a user is already authenticated with their work or school account in another service, such as Outlook or SharePoint, they'll be automatically signed in to Microsoft Search when they go to Bing in the same browser.</span></span> <span data-ttu-id="a9bd7-122">此外，如果使用者登出 Microsoft Search，系統也會自動當他們登出其他服務。</span><span class="sxs-lookup"><span data-stu-id="a9bd7-122">Also, when the user signs out of Microsoft Search, they'll be automatically signed out from other services in the same browser.</span></span>
  
## <a name="communicates-with-the-trusted-cloud-from-the-browser"></a><span data-ttu-id="a9bd7-123">從瀏覽器使用 Trusted Cloud 進行通訊</span><span class="sxs-lookup"><span data-stu-id="a9bd7-123">Communicates with the Trusted Cloud from the browser</span></span>

<span data-ttu-id="a9bd7-124">當使用者以公司或學校帳戶登入時，Bing 會在瀏覽器中下載所需的用戶端資料庫，以取得 Microsoft Search 結果。</span><span class="sxs-lookup"><span data-stu-id="a9bd7-124">When a user signs in with their work or school account, Bing will download the necessary client libraries to the browser to enable Microsoft Search results.</span></span> <span data-ttu-id="a9bd7-125">隨後，當他們搜尋時，瀏覽器內的程式碼會呼叫 Office 365 雲端，以取得工作結果。</span><span class="sxs-lookup"><span data-stu-id="a9bd7-125">Then, when they search, the in-browser code calls the Office 365 cloud to get work results.</span></span> <span data-ttu-id="a9bd7-126">為了執行這項程序，Microsoft Search 會使用專門的 API 層級 C (SOC2 類型 1)，為[符合 Office 365 產業標準和法規的合規性架構](https://download.microsoft.com/download/B/2/7/B27B3EF3-8849-4C18-8BA4-5AD755728620/Compliance%20Framework_customer%20guidance.pdf) (下載 PDF)。</span><span class="sxs-lookup"><span data-stu-id="a9bd7-126">To do this, Microsoft Search uses a dedicated API that is Tier C (SOC2 Type 1) compliant pursuant to the Office 365 [Compliance Framework for Industry Standards and Regulations](https://download.microsoft.com/download/B/2/7/B27B3EF3-8849-4C18-8BA4-5AD755728620/Compliance%20Framework_customer%20guidance.pdf) (PDF download).</span></span> <span data-ttu-id="a9bd7-127">這表示工作結果與工作資料永遠不會流經不符合規範的 Bing 系統。</span><span class="sxs-lookup"><span data-stu-id="a9bd7-127">This means work results and work data never flow through non-compliant Bing systems.</span></span> 
  
## <a name="permissions"></a><span data-ttu-id="a9bd7-128">權限</span><span class="sxs-lookup"><span data-stu-id="a9bd7-128">Permissions</span></span>

<span data-ttu-id="a9bd7-129">從 Office 365 工作負載 (例如 SharePoint 和商務用 OneDrive) 擷取的工作結果，都會在來源經過適當的安全性調整。</span><span class="sxs-lookup"><span data-stu-id="a9bd7-129">Work results retrieved from Office 365 workloads such as SharePoint and OneDrive for Business are security trimmed at the source.</span></span> <span data-ttu-id="a9bd7-130">使用者無法看到像是 Word 文件或 PowerPoint 簡報這類透過 Office 365 檢視或存取的來源。</span><span class="sxs-lookup"><span data-stu-id="a9bd7-130">Users can't see resources such as Word documents or PowerPoint presentations they can't see and access through Office 365.</span></span> <span data-ttu-id="a9bd7-131">使用者只能查看自己的檔案，以及由作者在 SharePoint 中明確或隱含地 (例如透過群組資格) 與他們共用的檔案。</span><span class="sxs-lookup"><span data-stu-id="a9bd7-131">They can only see their own files and files that have been shared with them by the author explicitly or implicitly (through a group membership, for example) in SharePoint.</span></span>
  
## <a name="protects-user-queries-from-the-public-portion-of-bing"></a><span data-ttu-id="a9bd7-132">保護使用者查詢不列入 Bing 的公開部分</span><span class="sxs-lookup"><span data-stu-id="a9bd7-132">Protects user queries from the public portion of Bing</span></span>

<span data-ttu-id="a9bd7-133">由於工作相關的搜尋可能具敏感性質，Microsoft Search 針對 Bing 的公開網頁結果施行一套信任標準以處理這些搜尋。</span><span class="sxs-lookup"><span data-stu-id="a9bd7-133">Because work-related searches may be sensitive, Microsoft Search has implemented a set of trust measures for how these are handled by the public web results part of Bing.</span></span>
  
<span data-ttu-id="a9bd7-134">不論使用者查詢傳回的回應中是否包含一或多個工作結果，系統都會採取下列措施：</span><span class="sxs-lookup"><span data-stu-id="a9bd7-134">Regardless of whether a user query contains one or more work results in the returned response, the following measures are taken:</span></span>
  
- <span data-ttu-id="a9bd7-135">記錄</span><span class="sxs-lookup"><span data-stu-id="a9bd7-135">Logging</span></span> 
  - <span data-ttu-id="a9bd7-136">所有與 Microsoft 搜尋流量相關的搜尋記錄都會匿名處理。</span><span class="sxs-lookup"><span data-stu-id="a9bd7-136">All search logs pertaining to Microsoft Search traffic are de-identified.</span></span> <span data-ttu-id="a9bd7-137">記錄會保留 18 個月。</span><span class="sxs-lookup"><span data-stu-id="a9bd7-137">They're retained for 18 months.</span></span>
  - <span data-ttu-id="a9bd7-138">儲存在這些系統記錄中的查詢僅用於建模和訓練公用功能，例如當滿足一組限制和頻率閾值時，對公用 Web 結果進行自動建議或相關搜尋，這可讓我們相信這些查詢是常見的，而不是特定組織所特有。</span><span class="sxs-lookup"><span data-stu-id="a9bd7-138">Queries stored in these system logs will only be used to model and train public features such as autosuggest or related searches for public web results when a set of restrictions and frequency thresholds are met, which gives us confidence that these queries are common and not specific to a particular organization.</span></span> <span data-ttu-id="a9bd7-139">查詢必須在非 Microsoft 搜尋使用者的相關資料出現很多次，並且查詢不得僅觸發企業搜索結果。</span><span class="sxs-lookup"><span data-stu-id="a9bd7-139">The query must appear a significant amount of times in corelating data from non-Microsoft Search users, and the query must not trigger exclusively enterprise search results.</span></span> <span data-ttu-id="a9bd7-140">不符合這些要求的查詢將與公用的非 Microsoft 搜尋流量分開儲存。</span><span class="sxs-lookup"><span data-stu-id="a9bd7-140">Queries that do not meet these requirements will be stored separately from public, non-Microsoft Search traffic.</span></span>
  - <span data-ttu-id="a9bd7-141">限制存取會透過各種安全機制來管理，包括安全性群組與工程系統中的其他層級。</span><span class="sxs-lookup"><span data-stu-id="a9bd7-141">Restricted access is managed via various secure mechanisms, including security groups and other layers within the engineering system.</span></span>
- <span data-ttu-id="a9bd7-142">搜尋記錄</span><span class="sxs-lookup"><span data-stu-id="a9bd7-142">Search history</span></span>    
  - <span data-ttu-id="a9bd7-143">使用公司或學校帳戶登入時，其他電腦或裝置無法獲得該使用者的搜尋記錄。</span><span class="sxs-lookup"><span data-stu-id="a9bd7-143">When signed in with a work or school account, a user's search history won't be available on other computers or devices.</span></span>
 
- <span data-ttu-id="a9bd7-144">廣告</span><span class="sxs-lookup"><span data-stu-id="a9bd7-144">Advertising</span></span>   
  - <span data-ttu-id="a9bd7-145">絕不會將企業搜尋查詢與廣告客戶分享或建議給廣告客戶。</span><span class="sxs-lookup"><span data-stu-id="a9bd7-145">Enterprise search queries are never shared with or suggested to advertisers.</span></span>
  - <span data-ttu-id="a9bd7-146">永遠不會依據使用者的公司身分識別或組織來投放廣告。</span><span class="sxs-lookup"><span data-stu-id="a9bd7-146">Ads are never targeted to a user based on their work identity or organization.</span></span>
    
## <a name="gdpr"></a><span data-ttu-id="a9bd7-147">GDPR</span><span class="sxs-lookup"><span data-stu-id="a9bd7-147">GDPR</span></span>

<span data-ttu-id="a9bd7-148">Microsoft 在[ 2018 年 5 月 21 日的部落格文章](https://blogs.microsoft.com/on-the-issues/2018/05/21/microsofts-commitment-to-gdpr-privacy-and-putting-customers-in-control-of-their-own-data/)反映了我們對 GDPR 規範，以及 Microsoft 會如何協助企業與組織履行 GDPR 合規性義務的承諾。</span><span class="sxs-lookup"><span data-stu-id="a9bd7-148">The [May 21, 2018, blog post](https://blogs.microsoft.com/on-the-issues/2018/05/21/microsofts-commitment-to-gdpr-privacy-and-putting-customers-in-control-of-their-own-data/) from Microsoft reflects our commitment to GDPR compliance and how Microsoft helps businesses and organizations with their own GDPR compliance obligations.</span></span> <span data-ttu-id="a9bd7-149">您可以在 Microsoft [信任中心常見問題集](https://www.microsoft.com/trustcenter/privacy/gdpr/gdpr-faqs)中找到其他詳細資料。</span><span class="sxs-lookup"><span data-stu-id="a9bd7-149">You can find additional detail in the Microsoft [Trust Center FAQ](https://www.microsoft.com/trustcenter/privacy/gdpr/gdpr-faqs).</span></span> <span data-ttu-id="a9bd7-150">在線上服務中針對組織客戶的客戶資料進行 Microsoft Search 查詢，也會符合第 28 條所述的處理承諾，如[信任中心常見問題集](https://www.microsoft.com/trustcenter/privacy/gdpr/gdpr-faqs)中所反映。</span><span class="sxs-lookup"><span data-stu-id="a9bd7-150">Microsoft Search queries that operate against organizational customers' Customer Data within the Online Services will also meet the processor commitments outlined in Article 28 as reflected in the [Trust Center FAQ](https://www.microsoft.com/trustcenter/privacy/gdpr/gdpr-faqs).</span></span> <span data-ttu-id="a9bd7-151">針對移至公開 Bing 查詢 (來自 Microsoft Search)，Microsoft 為資料控制者，並會依照 GDPR 中所述，去除查詢的身分識別。</span><span class="sxs-lookup"><span data-stu-id="a9bd7-151">With respect to queries from Microsoft Search that go to public Bing, Microsoft is a data controller and has implemented measures to de-identify the queries as outlined under GDPR.</span></span>