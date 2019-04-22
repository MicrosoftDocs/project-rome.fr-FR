---
title: MCDRemoteSystemApp
description: Représente une application sur un système distant qui est disponible pour la connectivité.
keywords: Microsoft, windows, iOS, iPhone, objectiveC, les appareils, Project Rome connectés
ms.openlocfilehash: 28ec3fbe03150cb45c0a554a0499f1a6b657e50d
ms.sourcegitcommit: 945a0f4bda02e3b4eb9a665379c2af9bd5285a53
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59801581"
---
# <a name="class-mcdremotesystemapp"></a><span data-ttu-id="b5391-104">Classe `MCDRemoteSystemApp`</span><span class="sxs-lookup"><span data-stu-id="b5391-104">class `MCDRemoteSystemApp`</span></span> 

```
@interface MCDRemoteSystemApp : NSObject
```  

<span data-ttu-id="b5391-105">Représente une application sur un système distant qui est disponible pour la connectivité.</span><span class="sxs-lookup"><span data-stu-id="b5391-105">Represents an application on a remote system that is available for connectivity.</span></span>

## <a name="properties"></a><span data-ttu-id="b5391-106">Properties</span><span class="sxs-lookup"><span data-stu-id="b5391-106">Properties</span></span>

### <a name="appid"></a><span data-ttu-id="b5391-107">appId</span><span class="sxs-lookup"><span data-stu-id="b5391-107">appId</span></span>
`@property(nonatomic, readonly, nonnull) NSString* appId;`

<span data-ttu-id="b5391-108">Un identificateur unique pour cette application.</span><span class="sxs-lookup"><span data-stu-id="b5391-108">A unique identifier for this application.</span></span>

### <a name="displayname"></a><span data-ttu-id="b5391-109">displayName</span><span class="sxs-lookup"><span data-stu-id="b5391-109">displayName</span></span>
`@property(nonatomic, readonly, nonnull) NSString* displayName;`

<span data-ttu-id="b5391-110">Le nom complet convivial pour cette application.</span><span class="sxs-lookup"><span data-stu-id="b5391-110">The friendly display name for this application.</span></span> <span data-ttu-id="b5391-111">Il s’agit du nom utilisé par l’appareil pour l’identification de Bluetooth.</span><span class="sxs-lookup"><span data-stu-id="b5391-111">This is the name used by the device for Bluetooth identification.</span></span> <span data-ttu-id="b5391-112">Si cela n’a pas été défini ou l’appareil ne prend pas en charge le Bluetooth, ce champ sera vide.</span><span class="sxs-lookup"><span data-stu-id="b5391-112">If this hasn't been set or the device doesn't support Bluetooth, this field will be empty.</span></span>

### <a name="availablebyproximity"></a><span data-ttu-id="b5391-113">availableByProximity</span><span class="sxs-lookup"><span data-stu-id="b5391-113">availableByProximity</span></span>
`@property(nonatomic, readonly, getter=isAvailableByProximity) BOOL availableByProximity;`

<span data-ttu-id="b5391-114">Indique si cette application est actuellement disponible pour la connexion PROXIMALE.</span><span class="sxs-lookup"><span data-stu-id="b5391-114">Indicates whether this application is currently available for proximal connection.</span></span>

### <a name="availablebyspatialproximity"></a><span data-ttu-id="b5391-115">availableBySpatialProximity</span><span class="sxs-lookup"><span data-stu-id="b5391-115">availableBySpatialProximity</span></span>
`@property(nonatomic, readonly, getter=isAvailableBySpatialProximity) BOOL availableBySpatialProximity;`

<span data-ttu-id="b5391-116">Indique si cette application est actuellement disponible pour la connexion partage spatiale.</span><span class="sxs-lookup"><span data-stu-id="b5391-116">Indicates whether this application is currently available for spatial sharing connection.</span></span>

### <a name="attributes"></a><span data-ttu-id="b5391-117">attributs</span><span class="sxs-lookup"><span data-stu-id="b5391-117">attributes</span></span>
`@property(nonatomic, readonly, nonnull) NSDictionary<NSString*, NSString*>* attributes;`

<span data-ttu-id="b5391-118">Dictionnaire de paires clé/valeur qui définit les attributs de cette application.</span><span class="sxs-lookup"><span data-stu-id="b5391-118">A dictionary of key/value pairs defining the attributes of this application.</span></span>

### <a name="appservices"></a><span data-ttu-id="b5391-119">appServices</span><span class="sxs-lookup"><span data-stu-id="b5391-119">appServices</span></span>
`@property(nonatomic, readonly, nullable) NSArray<MCDAppServiceDescription*>* appServices;`

<span data-ttu-id="b5391-120">Un tableau d’instances de MCDAppServiceDescription décrivant les services d’application fournies par cette application pour la connectivité à distance.</span><span class="sxs-lookup"><span data-stu-id="b5391-120">An array of MCDAppServiceDescription instances describing the app services that this application provides for remote connectivity.</span></span>

### <a name="accounts"></a><span data-ttu-id="b5391-121">comptes</span><span class="sxs-lookup"><span data-stu-id="b5391-121">accounts</span></span>
`@property(nonatomic, readonly, nullable) NSArray<MCDConnectedDevicesAccount*>* accounts;`

<span data-ttu-id="b5391-122">Le compte associé à MCDRemoteSystemApp que vous êtes autorisé à connaître.</span><span class="sxs-lookup"><span data-stu-id="b5391-122">The Account associated with the MCDRemoteSystemApp that you have permissions to know about.</span></span> <span data-ttu-id="b5391-123">Élément qui détermine les autorisations est si le MCDConnectedDevicesAccount existe dans le MCDConnectedDevicesAccountManager lorsque le MCDRemoteSystemWatcher est démarré.</span><span class="sxs-lookup"><span data-stu-id="b5391-123">What determines permissions is if the MCDConnectedDevicesAccount exists in the MCDConnectedDevicesAccountManager when the MCDRemoteSystemWatcher is started.</span></span>