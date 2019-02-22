---
title: Zarządzanie Cofnij i wykonaj ponownie za pomocą starszej wersji interfejsu API | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - undo management
ms.assetid: 838c0ddf-fdf3-4df1-8d21-79610b8ba0b1
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: adf6a2405ae3d3408f9cf04199ba05dff9232326
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/22/2019
ms.locfileid: "56687799"
---
# <a name="manage-undo-and-redo-by-using-the-legacy-api"></a>Zarządzanie Cofnij i wykonaj ponownie przy użyciu starszej wersji interfejsu API
Edytory musi obsługiwać operacje cofania, które pozwalają użytkownikom odwrotnego ich ostatnich zmian, ich modyfikowania kodu. Większość edytorów zaimplementowane mocy [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] i [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] może mieć Obsługa polecenia Cofnij automatycznie udostępniane przez zintegrowanego środowiska programistycznego (IDE).

## <a name="in-this-section"></a>W tej sekcji
- [Instrukcje: Implementowanie zarządzania cofania](../extensibility/how-to-implement-undo-management.md) zapewnia możliwość cofnięcia edytorów z jednego lub wielu widoków.

- [Instrukcje: Wyczyścić stosu cofania](../extensibility/how-to-clear-the-undo-stack.md) opisano, jak można wyczyścić stosu cofania.

- [Instrukcje: Za pomocą przystawki Zarządzanie połączonego cofania](../extensibility/how-to-use-linked-undo-management.md) Incorporates połączonego cofania zarządzania do edytora.

## <a name="reference"></a>Tematy pomocy
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsChangeTrackingUndoManager> Umożliwia zarządzanie cofania dla edytora, która obsługuje wiele widoków.
