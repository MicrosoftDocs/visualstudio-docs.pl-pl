---
title: Polecenie routingu w pakietach VSPackage | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- commands, routing
- command routing, Visual Studio SDK
ms.assetid: a9c7f9ae-3594-4557-a314-8cf76f5f8772
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 5749875a440a3122a06b81ae9d721e75ded6202c
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62862020"
---
# <a name="command-routing-in-vspackages"></a>Routing poleceń w pakietach VSPackage
Polecenie odbywa się w [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] na podstawie kontekstu, w którym jest wykonywany. Z kontekstu początkową na zewnątrz jest kierowany do kontekstu globalnego.

## <a name="in-this-section"></a>W tej sekcji
- [Algorytm routingu poleceń](../../extensibility/internals/command-routing-algorithm.md)

 W tym artykule opisano kolejność rozpoznawania routingu poleceń.

- [Dostępność poleceń](../../extensibility/internals/command-availability.md)

 W tym artykule omówiono, routing poleceń.

- [Polecenia i menu, które używają zestawów międzyoperacyjnych](../../extensibility/internals/commands-and-menus-that-use-interop-assemblies.md)

 W tym artykule omówiono zagadnienia dotyczące polecenia routingu między kodem zarządzanym i modelu COM.

## <a name="related-sections"></a>Sekcje pokrewne
- [Wybór obiektów kontekstu](../../extensibility/internals/selection-context-objects.md)

 W tym artykule omówiono model jaki sposób można określić użytkownika wybór kontekstu fokus w oknie.

- [Polecenia, menu i paski narzędzi](../../extensibility/internals/commands-menus-and-toolbars.md)

 Wyjaśnia, jak utworzyć interfejs użytkownika, który zawiera menu, paski narzędzi i pola kombi polecenia.