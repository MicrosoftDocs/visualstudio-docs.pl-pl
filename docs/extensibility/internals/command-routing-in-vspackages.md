---
title: Routing poleceń w pakietów VSPackage | Microsoft Docs
description: Informacje o routingu poleceń w programie pakietów VSPackage oraz o sposobie kierowania poleceń na podstawie kontekstu, w którym są wykonywane w programie Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- commands, routing
- command routing, Visual Studio SDK
ms.assetid: a9c7f9ae-3594-4557-a314-8cf76f5f8772
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 35ab5e7989fdeb46592f38cb7e55854885e076d1
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2021
ms.locfileid: "105057302"
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
