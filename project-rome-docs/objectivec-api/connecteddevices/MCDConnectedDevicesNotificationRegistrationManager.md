---
title: MCDConnectedDevicesNotificationRegistrationManager
description: Gère l’inscription pour la notification de cloud Rome pour tous les comptes.
keywords: Microsoft, windows, iOS, iPhone, objectiveC, les appareils, Project Rome connectés
ms.openlocfilehash: d4f5f7963514795e3e296d9bdb42b1811af4f7cc
ms.sourcegitcommit: 945a0f4bda02e3b4eb9a665379c2af9bd5285a53
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58909901"
---
# <a name="class-mcdconnecteddevicesnotificationregistrationmanager"></a><span data-ttu-id="937b1-104">Classe `MCDConnectedDevicesNotificationRegistrationManager`</span><span class="sxs-lookup"><span data-stu-id="937b1-104">class `MCDConnectedDevicesNotificationRegistrationManager`</span></span> 

```
@interface MCDConnectedDevicesNotificationRegistrationManager : NSObject
```  
<span data-ttu-id="937b1-105">Gère l’inscription pour la notification de cloud de plateforme appareils connectés pour tous les comptes.</span><span class="sxs-lookup"><span data-stu-id="937b1-105">Manages the registration for the Connected Devices platform cloud notification for all accounts.</span></span>

<span data-ttu-id="937b1-106">MCDConnectedDevicesNotificationRegistrationManager gère les informations de notification inscrits pour chaque compte.</span><span class="sxs-lookup"><span data-stu-id="937b1-106">MCDConnectedDevicesNotificationRegistrationManager manages the notification information registered for each account.</span></span> <span data-ttu-id="937b1-107">N’importe quel moment les informations de notification d’une application changent (par exemple, avec APNS son jeton), ou lorsque les informations de notification arrive à expiration, une application doit réinscrire ses informations.</span><span class="sxs-lookup"><span data-stu-id="937b1-107">Any time an app's notification information changes (for example, when APNS changes its token), or when the notification information is expiring, an app should re-register its information.</span></span> <span data-ttu-id="937b1-108">Si une application considère uniquement les réponses pour les communications sortantes, une inscription d’interrogation peut être utilisée.</span><span class="sxs-lookup"><span data-stu-id="937b1-108">If an application only cares about responses to outgoing communication, a Polling registration may be used.</span></span>

> [!NOTE] 
> <span data-ttu-id="937b1-109">Informations de notification doivent être enregistrées avant de nombreux scénarios ConnectedDevices ne fonctionnent pas correctement.</span><span class="sxs-lookup"><span data-stu-id="937b1-109">Notification information must be registered before many ConnectedDevices scenarios will work successfully.</span></span> 

## <a name="properties"></a><span data-ttu-id="937b1-110">Properties</span><span class="sxs-lookup"><span data-stu-id="937b1-110">Properties</span></span>

### <a name="registrationstatechanged"></a><span data-ttu-id="937b1-111">registrationStateChanged</span><span class="sxs-lookup"><span data-stu-id="937b1-111">registrationStateChanged</span></span>
`@property(nonatomic, readonly, nonnull) MCDEvent<MCDConnectedDevicesNotificationRegistrationManager*, MCDConnectedDevicesNotificationRegistrationStateChangedEventArgs*>* registrationStateChanged;`

<span data-ttu-id="937b1-112">Événements pour informer l’application quand état de l’inscription de notification change pour un compte.</span><span class="sxs-lookup"><span data-stu-id="937b1-112">Event to let the app know when notification registration state changes for an account.</span></span> 

## <a name="methods"></a><span data-ttu-id="937b1-113">Méthodes</span><span class="sxs-lookup"><span data-stu-id="937b1-113">Methods</span></span>

### <a name="registerforaccountasync"></a><span data-ttu-id="937b1-114">registerForAccountAsync</span><span class="sxs-lookup"><span data-stu-id="937b1-114">registerForAccountAsync</span></span>
`- (void) registerForAccountAsync:(MCDConnectedDevicesAccount* _Nonnull)account registration:(MCDConnectedDevicesNotificationRegistration* _Nonnull)notificationRegistration callback:(nonnull void (^)(BOOL, NSError* _Nullable))callback __attribute__((deprecated("Use registerAsync instead")));`

<span data-ttu-id="937b1-115">Inscrire le compte donné avec les informations d’inscription de notification donnée.</span><span class="sxs-lookup"><span data-stu-id="937b1-115">Register the given account with the given notification registration information.</span></span> <span data-ttu-id="937b1-116">Cette opération crée un canal de notification afin que cette application peut être avertie de nouvelles informations d’appareils connectés pour ce compte.</span><span class="sxs-lookup"><span data-stu-id="937b1-116">This creates a notification channel so that this application can be notified about new Connected Devices information for this account.</span></span> <span data-ttu-id="937b1-117">Notez que les autres applications ne peuvent pas communiquer avec cette application à l’aide de ce canal de notification jusqu'à ce que les informations de MCDRemoteSystemAppRegistration sont publiées.</span><span class="sxs-lookup"><span data-stu-id="937b1-117">Note that other applications can not communicate with this app using this notification channel until the MCDRemoteSystemAppRegistration information is published.</span></span>

> [!WARNING]
> <span data-ttu-id="937b1-118">Cette fonction est déconseillée.</span><span class="sxs-lookup"><span data-stu-id="937b1-118">This function is deprecated.</span></span> <span data-ttu-id="937b1-119">Utilisez plutôt registerAsync.</span><span class="sxs-lookup"><span data-stu-id="937b1-119">Please use registerAsync instead.</span></span>

#### <a name="parameters"></a><span data-ttu-id="937b1-120">Paramètres</span><span class="sxs-lookup"><span data-stu-id="937b1-120">Parameters</span></span> 
* `account` 

<span data-ttu-id="937b1-121">Compte pour lequel enregistrer les informations de notification.</span><span class="sxs-lookup"><span data-stu-id="937b1-121">Account for which to register notification information.</span></span>

* `notificationRegistration` 

<span data-ttu-id="937b1-122">Informations de notification pour vous inscrire.</span><span class="sxs-lookup"><span data-stu-id="937b1-122">Notification information to register.</span></span>

* `callback` 

<span data-ttu-id="937b1-123">Le rappel bénéficient ainsi d’if l’inscription s’est terminée correctement.</span><span class="sxs-lookup"><span data-stu-id="937b1-123">The callback result for if the registration completed successfully.</span></span>

### <a name="registerasync"></a><span data-ttu-id="937b1-124">registerAsync</span><span class="sxs-lookup"><span data-stu-id="937b1-124">registerAsync</span></span>
`- (void) registerAsync:(MCDConnectedDevicesAccount* _Nonnull)account registration:(MCDConnectedDevicesNotificationRegistration* _Nonnull)notificationRegistration completion:(nonnull void (^)(MCDConnectedDevicesNotificationRegistrationResult* _Nonnull, NSError* _Nullable))callback;`

<span data-ttu-id="937b1-125">Inscrire le compte donné avec les informations d’inscription de notification donnée.</span><span class="sxs-lookup"><span data-stu-id="937b1-125">Register the given account with the given notification registration information.</span></span> <span data-ttu-id="937b1-126">Cette opération crée un canal de notification afin que cette application peut être avertie de nouvelles informations d’appareils connectés pour ce compte.</span><span class="sxs-lookup"><span data-stu-id="937b1-126">This creates a notification channel so that this application can be notified about new Connected Devices information for this account.</span></span> <span data-ttu-id="937b1-127">Notez que les autres applications ne peuvent pas communiquer avec cette application à l’aide de ce canal de notification jusqu'à ce que les informations de MCDRemoteSystemAppRegistration sont publiées.</span><span class="sxs-lookup"><span data-stu-id="937b1-127">Note that other applications can not communicate with this app using this notification channel until the MCDRemoteSystemAppRegistration information is published.</span></span>

#### <a name="parameters"></a><span data-ttu-id="937b1-128">Paramètres</span><span class="sxs-lookup"><span data-stu-id="937b1-128">Parameters</span></span> 
* `account` 

<span data-ttu-id="937b1-129">Compte pour lequel enregistrer les informations de notification.</span><span class="sxs-lookup"><span data-stu-id="937b1-129">Account for which to register notification information.</span></span>

* `notificationRegistration` 

<span data-ttu-id="937b1-130">Informations de notification pour vous inscrire.</span><span class="sxs-lookup"><span data-stu-id="937b1-130">Notification information to register.</span></span>

* `callback` 

<span data-ttu-id="937b1-131">Le rappel bénéficient ainsi d’if l’inscription s’est terminée correctement.</span><span class="sxs-lookup"><span data-stu-id="937b1-131">The callback result for if the registration completed successfully.</span></span>

### <a name="getnotificationregistrationstateforaccount"></a><span data-ttu-id="937b1-132">getNotificationRegistrationStateForAccount</span><span class="sxs-lookup"><span data-stu-id="937b1-132">getNotificationRegistrationStateForAccount</span></span>
`- (MCDConnectedDevicesNotificationRegistrationState) getNotificationRegistrationStateForAccount:(MCDConnectedDevicesAccount* _Nonnull)account;`

<span data-ttu-id="937b1-133">Récupérer l’état de l’inscription de notification en cours pour le compte donné.</span><span class="sxs-lookup"><span data-stu-id="937b1-133">Retrieve the current notification registration state for the given account.</span></span> <span data-ttu-id="937b1-134">Les informations de notification qui sont inscrit arriveront à expiration (utile si l’application est désinstallée ou pas exécutée dans beaucoup de temps).</span><span class="sxs-lookup"><span data-stu-id="937b1-134">The notification information that is registered will eventually expire (useful if the app is uninstalled or not run in a very long time).</span></span> <span data-ttu-id="937b1-135">Une application doit enregistrez à nouveau ses informations de notification lors de l’inscription de l’état arrivant à expiration ou a expiré.</span><span class="sxs-lookup"><span data-stu-id="937b1-135">An app should re-register its notification information when the registration is expiring / expired.</span></span> 

#### <a name="parameters"></a><span data-ttu-id="937b1-136">Paramètres</span><span class="sxs-lookup"><span data-stu-id="937b1-136">Parameters</span></span> 
* `account`

<span data-ttu-id="937b1-137">Compte pour lequel obtenir l’état de l’inscription.</span><span class="sxs-lookup"><span data-stu-id="937b1-137">Account for which to get registration state.</span></span>

#### <a name="returns"></a><span data-ttu-id="937b1-138">Returns</span><span class="sxs-lookup"><span data-stu-id="937b1-138">Returns</span></span>

<span data-ttu-id="937b1-139">État de l’inscription de notification.</span><span class="sxs-lookup"><span data-stu-id="937b1-139">State of the notification registration.</span></span>
