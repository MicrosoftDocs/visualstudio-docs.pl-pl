---
title: Routing poleceń w pakietów VSPackage | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- commands, routing
- command routing, Visual Studio SDK
ms.assetid: a9c7f9ae-3594-4557-a314-8cf76f5f8772
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 957ddcca46365a882609c15c96d666c2848ace6c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "80709555"
---
# <a name="command-routing-in-vspackages"></a>Routing poleceń w pakietów VSPackage
Polecenie jest kierowane w [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] zależności od kontekstu, w którym jest wykonywane. Jest on kierowany z kontekstu początkowego do kontekstu globalnego.

## <a name="in-this-section"></a>W tej sekcji
- [Algorytm routingu poleceń](../../extensibility/internals/command-routing-algorithm.md)

 Opisuje kolejność rozpoznawania poleceń routingu.

- [Dostępność polecenia](../../extensibility/internals/command-availability.md)

 Omówienie routingu poleceń.

- [Polecenia i menu używające zestawów międzyoperacyjnych](../../extensibility/internals/commands-and-menus-that-use-interop-assemblies.md)

 Omawia uwagi dotyczące poleceń routingu między kodem zarządzanym i modelem COM.

## <a name="related-sections"></a>Sekcje pokrewne
- [Obiekty kontekstu wyboru](../../extensibility/internals/selection-context-objects.md)

 Omawia model, w którym można określić fokus kontekstu wyboru użytkownika w oknie.

- [Polecenia, menu i paski narzędzi](../../extensibility/internals/commands-menus-and-toolbars.md)

 Wyjaśnia, jak utworzyć interfejs użytkownika, który obejmuje menu, paski narzędzi i pola kombi poleceń.
