---
title: MCDRemoteSystemWatcherError
description: Contient des valeurs describe une erreur rencontrée par un objet de l’Observateur système distant pendant le processus de découverte.
keywords: Microsoft, windows, iOS, iPhone, objectiveC, les appareils, Project Rome connectés
ms.openlocfilehash: 3f65614396377b154b2a37493b8271ac54afb6fd
ms.sourcegitcommit: 945a0f4bda02e3b4eb9a665379c2af9bd5285a53
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59801721"
---
# <a name="enum-mcdremotesystemwatchererror"></a><span data-ttu-id="8f685-104">Enum `MCDRemoteSystemWatcherError`</span><span class="sxs-lookup"><span data-stu-id="8f685-104">enum `MCDRemoteSystemWatcherError`</span></span> 

```
typedef NS_ENUM(NSInteger, MCDRemoteSystemWatcherError)
```  
 <span data-ttu-id="8f685-105">Contient des valeurs describe une erreur rencontrée par un objet de l’Observateur système distant pendant le processus de découverte.</span><span class="sxs-lookup"><span data-stu-id="8f685-105">Contains values that the describe an error encountered by a remote system watcher object during the discovery process.</span></span>

## <a name="fields"></a><span data-ttu-id="8f685-106">Champs</span><span class="sxs-lookup"><span data-stu-id="8f685-106">Fields</span></span>

| <span data-ttu-id="8f685-107">Nom</span><span class="sxs-lookup"><span data-stu-id="8f685-107">Name</span></span>                              | <span data-ttu-id="8f685-108">Value</span><span class="sxs-lookup"><span data-stu-id="8f685-108">Value</span></span> | <span data-ttu-id="8f685-109">Description</span><span class="sxs-lookup"><span data-stu-id="8f685-109">Description</span></span>                    |
|:----------------------------------|:------|:-------------------------------|
| <span data-ttu-id="8f685-110">MCDRemoteSystemWatcherErrorUnknown</span><span class="sxs-lookup"><span data-stu-id="8f685-110">MCDRemoteSystemWatcherErrorUnknown</span></span> | <span data-ttu-id="8f685-111">0</span><span class="sxs-lookup"><span data-stu-id="8f685-111">0</span></span> | <span data-ttu-id="8f685-112">L’Observateur a rencontré une erreur inconnue.</span><span class="sxs-lookup"><span data-stu-id="8f685-112">The watcher encountered an unknown error.</span></span> |
| <span data-ttu-id="8f685-113">MCDRemoteSystemWatcherErrorInternetNotAvailable</span><span class="sxs-lookup"><span data-stu-id="8f685-113">MCDRemoteSystemWatcherErrorInternetNotAvailable</span></span> | <span data-ttu-id="8f685-114">1</span><span class="sxs-lookup"><span data-stu-id="8f685-114">1</span></span> | <span data-ttu-id="8f685-115">L’erreur s’est produite, car la connexion Internet a été perdue.</span><span class="sxs-lookup"><span data-stu-id="8f685-115">The error occurred because the Internet connection was lost.</span></span> |
| <span data-ttu-id="8f685-116">MCDRemoteSystemWatcherErrorAuthenticationError</span><span class="sxs-lookup"><span data-stu-id="8f685-116">MCDRemoteSystemWatcherErrorAuthenticationError</span></span> | <span data-ttu-id="8f685-117">2</span><span class="sxs-lookup"><span data-stu-id="8f685-117">2</span></span> | <span data-ttu-id="8f685-118">L’erreur s’est produite, car un ConnectedDevicesAccount utilisé pour exécuter la découverte n’a pas pu être authentifié.</span><span class="sxs-lookup"><span data-stu-id="8f685-118">The error occurred because a ConnectedDevicesAccount being used to run the discovery could not be authenticated.</span></span> | 
