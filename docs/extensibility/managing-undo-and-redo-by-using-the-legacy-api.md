---
title: Zarządzanie Cofnij i wykonaj ponownie za pomocą starszej wersji interfejsu API | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - undo management
ms.assetid: 838c0ddf-fdf3-4df1-8d21-79610b8ba0b1
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a8a93b4fd12cd9a0bd2e5a5f3c70486e370545a9
ms.sourcegitcommit: 12f2851c8c9bd36a6ab00bf90a020c620b364076
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2019
ms.locfileid: "66747650"
---
# <a name="manage-undo-and-redo-by-using-the-legacy-api"></a>Zarządzanie Cofnij i wykonaj ponownie przy użyciu starszej wersji interfejsu API
Edytory musi obsługiwać operacje cofania, które pozwalają użytkownikom odwrotnego ich ostatnich zmian, ich modyfikowania kodu. Większość edytorów zaimplementowane mocy [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] i .NET Framework może mieć Obsługa polecenia Cofnij automatycznie udostępniane przez zintegrowanego środowiska programistycznego (IDE).

## <a name="in-this-section"></a>W tej sekcji
- [Instrukcje: Implementowanie zarządzania cofania](../extensibility/how-to-implement-undo-management.md) zapewnia możliwość cofnięcia edytorów z jednego lub wielu widoków.

- [Instrukcje: Wyczyścić stosu cofania](../extensibility/how-to-clear-the-undo-stack.md) opisano, jak można wyczyścić stosu cofania.

- [Instrukcje: Za pomocą przystawki Zarządzanie połączonego cofania](../extensibility/how-to-use-linked-undo-management.md) Incorporates połączonego cofania zarządzania do edytora.

## <a name="reference"></a>Tematy pomocy
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsChangeTrackingUndoManager> Umożliwia zarządzanie cofania dla edytora, która obsługuje wiele widoków.
