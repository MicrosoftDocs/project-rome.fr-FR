---
title: MCDRemoteSystemAppRegistration
description: Cette classe représente une application qui doit être enregistré avec la plateforme d’appareils connectés.
keywords: Microsoft, windows, iOS, iPhone, objectiveC, les appareils, Project Rome connectés
ms.openlocfilehash: 2c931d3eeacd4aa48e1ef22d573bf0325eb5b98b
ms.sourcegitcommit: 945a0f4bda02e3b4eb9a665379c2af9bd5285a53
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58909911"
---
# <a name="class-mcdremotesystemappregistration"></a><span data-ttu-id="3b49d-104">Classe `MCDRemoteSystemAppRegistration`</span><span class="sxs-lookup"><span data-stu-id="3b49d-104">class `MCDRemoteSystemAppRegistration`</span></span> 

```
@interface MCDRemoteSystemAppRegistration : NSObject
```  

<span data-ttu-id="3b49d-105">Cette classe contient toutes les informations sur cette application qui a un autre peut détecter et utiliser.</span><span class="sxs-lookup"><span data-stu-id="3b49d-105">This class contains all of the information about this app that another could discover and use.</span></span>

> [!NOTE] 
> <span data-ttu-id="3b49d-106">MCDRemoteSystemAppRegistration informations doivent être publiées avant la fidèlement les communications sortantes vers une autre application.</span><span class="sxs-lookup"><span data-stu-id="3b49d-106">MCDRemoteSystemAppRegistration information must be published before any outgoing communication to another app is possble.</span></span> <span data-ttu-id="3b49d-107">Il s’agit afin que l’autre application peut savoir comment répondre à cette communication.</span><span class="sxs-lookup"><span data-stu-id="3b49d-107">This is so that the other application can know how to respond to that communication.</span></span>

## <a name="properties"></a><span data-ttu-id="3b49d-108">Properties</span><span class="sxs-lookup"><span data-stu-id="3b49d-108">Properties</span></span>

### <a name="account"></a><span data-ttu-id="3b49d-109">compte</span><span class="sxs-lookup"><span data-stu-id="3b49d-109">account</span></span>
`@property(nonatomic, readonly, nullable) MCDConnectedDevicesAccount* account;`

<span data-ttu-id="3b49d-110">Compte auquel appartient cette inscription.</span><span class="sxs-lookup"><span data-stu-id="3b49d-110">Account that this registration belongs to.</span></span>

### <a name="attributes"></a><span data-ttu-id="3b49d-111">attributs</span><span class="sxs-lookup"><span data-stu-id="3b49d-111">attributes</span></span>
`@property(nonatomic, copy, nullable) NSDictionary<NSString*, NSString*>* attributes;`

 <span data-ttu-id="3b49d-112">Dictionnaire de chaînes qui décrivent les attributs de cette application.</span><span class="sxs-lookup"><span data-stu-id="3b49d-112">Dictionary of strings that describe the attributes of this app.</span></span>

### <a name="appserviceproviders"></a><span data-ttu-id="3b49d-113">appServiceProviders</span><span class="sxs-lookup"><span data-stu-id="3b49d-113">appServiceProviders</span></span>
`@property(nonatomic, copy, nullable) NSArray<id<MCDAppServiceProvider>>* appServiceProviders;`

<span data-ttu-id="3b49d-114">Tableau de AppServiceProviders qui prend en charge de cette application.</span><span class="sxs-lookup"><span data-stu-id="3b49d-114">Array of AppServiceProviders that this app supports.</span></span>

> [!NOTE] 
> <span data-ttu-id="3b49d-115">Un fournisseur de services d’application doit être présent dans ce tableau d’afin de recevoir des connexions entrantes.</span><span class="sxs-lookup"><span data-stu-id="3b49d-115">An app service provider must be present in this array in order to receive incoming connections.</span></span>  <span data-ttu-id="3b49d-116">MCDRemoteSystemAppRegistration.publishAsync() n’a pas besoin d’être appelée pour le fournisseur de services d’application recevoir les demandes.</span><span class="sxs-lookup"><span data-stu-id="3b49d-116">MCDRemoteSystemAppRegistration.publishAsync() does not need to be called for the app service provider to receive requests.</span></span>  

### <a name="launchuriprovider"></a><span data-ttu-id="3b49d-117">launchUriProvider</span><span class="sxs-lookup"><span data-stu-id="3b49d-117">launchUriProvider</span></span>
`@property(nonatomic, readwrite, nullable) id<MCDLaunchUriProvider> launchUriProvider;`

<span data-ttu-id="3b49d-118">Lancer les Uri du fournisseur pour cette application.</span><span class="sxs-lookup"><span data-stu-id="3b49d-118">Launch Uri provider for this app.</span></span>

> [!NOTE] 
> <span data-ttu-id="3b49d-119">Un fournisseur d’uri de lancement doit être stocké dans cette propriété afin de recevoir les demandes entrantes.</span><span class="sxs-lookup"><span data-stu-id="3b49d-119">A launch uri provider must be stored in this property in order to receive incoming requests.</span></span>  <span data-ttu-id="3b49d-120">MCDRemoteSystemAppRegistration.publishAsync() n’a pas besoin d’être appelée pour le fournisseur de services d’application recevoir les demandes.</span><span class="sxs-lookup"><span data-stu-id="3b49d-120">MCDRemoteSystemAppRegistration.publishAsync() does not need to be called for the app service provider to receive requests.</span></span>  

## <a name="constructors"></a><span data-ttu-id="3b49d-121">Constructeurs</span><span class="sxs-lookup"><span data-stu-id="3b49d-121">Constructors</span></span>

### <a name="getforaccount"></a><span data-ttu-id="3b49d-122">getForAccount</span><span class="sxs-lookup"><span data-stu-id="3b49d-122">getForAccount</span></span>
`+(nullable instancetype) getForAccount:(MCDConnectedDevicesAccount* _Nonnull) account
                              platform:(MCDConnectedDevicesPlatform* _Nonnull) platform;`

<span data-ttu-id="3b49d-123">Obtient l’inscription de l’application actuelle du système distant pour le compte.</span><span class="sxs-lookup"><span data-stu-id="3b49d-123">Gets the current remote system app registration for the account.</span></span>

#### <a name="parameters"></a><span data-ttu-id="3b49d-124">Paramètres</span><span class="sxs-lookup"><span data-stu-id="3b49d-124">Parameters</span></span>
* `account` 

<span data-ttu-id="3b49d-125">Compte afin de récupérer l’inscription.</span><span class="sxs-lookup"><span data-stu-id="3b49d-125">Account to retrieve the registration for.</span></span>

* `platform` 

<span data-ttu-id="3b49d-126">Plateforme pour obtenir de l’inscription à partir de.</span><span class="sxs-lookup"><span data-stu-id="3b49d-126">Platform to get registration from.</span></span>

#### <a name="returns"></a><span data-ttu-id="3b49d-127">Returns</span><span class="sxs-lookup"><span data-stu-id="3b49d-127">Returns</span></span>
<span data-ttu-id="3b49d-128">Retourne un objet MCDRemoteSystemAppRegistration pour le compte fourni.</span><span class="sxs-lookup"><span data-stu-id="3b49d-128">Returns an MCDRemoteSystemAppRegistration object for the provided Account.</span></span>

## <a name="methods"></a><span data-ttu-id="3b49d-129">Méthodes</span><span class="sxs-lookup"><span data-stu-id="3b49d-129">Methods</span></span>

### <a name="saveasync"></a><span data-ttu-id="3b49d-130">saveAsync</span><span class="sxs-lookup"><span data-stu-id="3b49d-130">saveAsync</span></span>
`- (void)saveAsync:(nonnull void (^)(BOOL, NSError* _Nullable))callback  __attribute__((deprecated("Use publishAsync instead")));`

<span data-ttu-id="3b49d-131">Enregistre les informations actuellement stockées dans la RemoteSystemAppRegistration telles que les autres applications peuvent les découvrir.</span><span class="sxs-lookup"><span data-stu-id="3b49d-131">Saves the information currently stored in the RemoteSystemAppRegistration such that other applications can discover it.</span></span>

> [!NOTE] 
> <span data-ttu-id="3b49d-132">MCDConnectedDevicesNotificationRegistration doit être inscrit pour cet appel réussisse.</span><span class="sxs-lookup"><span data-stu-id="3b49d-132">MCDConnectedDevicesNotificationRegistration must be registered for this call to succeed.</span></span>

> [!WARNING] 
> <span data-ttu-id="3b49d-133">Déconseillé.</span><span class="sxs-lookup"><span data-stu-id="3b49d-133">Deprecated.</span></span> <span data-ttu-id="3b49d-134">Utilisez publishAsync à la place.</span><span class="sxs-lookup"><span data-stu-id="3b49d-134">Use publishAsync instead.</span></span>

#### <a name="parameters"></a><span data-ttu-id="3b49d-135">Paramètres</span><span class="sxs-lookup"><span data-stu-id="3b49d-135">Parameters</span></span>

* `callback`

<span data-ttu-id="3b49d-136">Le rappel indique le résultat de l’enregistrement des informations.</span><span class="sxs-lookup"><span data-stu-id="3b49d-136">The callback indicates the result of saving the information.</span></span>

### <a name="publishasync"></a><span data-ttu-id="3b49d-137">publishAsync</span><span class="sxs-lookup"><span data-stu-id="3b49d-137">publishAsync</span></span>
`- (void)publishAsync:(nonnull void (^)(MCDRemoteSystemAppRegistrationPublishResult* _Nonnull, NSError* _Nullable))completionBlock;`

<span data-ttu-id="3b49d-138">Publie les informations actuellement stockées dans la MCDRemoteSystemAppRegistration telles que les autres applications peuvent les découvrir.</span><span class="sxs-lookup"><span data-stu-id="3b49d-138">Publishes the information currently stored in the MCDRemoteSystemAppRegistration such that other applications can discover it.</span></span>

> [!NOTE] 
> <span data-ttu-id="3b49d-139">MCDConnectedDevicesNotificationRegistration doit être inscrit pour cet appel réussisse.</span><span class="sxs-lookup"><span data-stu-id="3b49d-139">MCDConnectedDevicesNotificationRegistration must be registered for this call to succeed.</span></span>

#### <a name="parameters"></a><span data-ttu-id="3b49d-140">Paramètres</span><span class="sxs-lookup"><span data-stu-id="3b49d-140">Parameters</span></span>

* `callback`

<span data-ttu-id="3b49d-141">Le rappel indique le résultat de l’enregistrement des informations.</span><span class="sxs-lookup"><span data-stu-id="3b49d-141">The callback indicates the result of saving the information.</span></span>
