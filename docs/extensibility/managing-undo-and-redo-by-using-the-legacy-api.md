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
ms.openlocfilehash: c43dc4892f1cf2a938a4ed29fc68bc55e99cc05e
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "54948131"
---
# <a name="manage-undo-and-redo-by-using-the-legacy-api"></a>Zarządzanie Cofnij i wykonaj ponownie przy użyciu starszej wersji interfejsu API
Edytory musi obsługiwać operacje cofania, które pozwalają użytkownikom odwrotnego ich ostatnich zmian, ich modyfikowania kodu. Większość edytorów zaimplementowane mocy [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] i [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] może mieć Obsługa polecenia Cofnij automatycznie udostępniane przez zintegrowanego środowiska programistycznego (IDE).  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Instrukcje: Implementowanie cofania zarządzania](../extensibility/how-to-implement-undo-management.md)  
 Zapewnia możliwości cofania dla edytorów, przy użyciu jednego lub wielu widoków.  
  
 [Instrukcje: Wyczyścić stosu cofania](../extensibility/how-to-clear-the-undo-stack.md)  
 W tym artykule opisano, jak wyczyścić stosu cofania.  
  
 [Instrukcje: Za pomocą przystawki Zarządzanie połączonego cofania](../extensibility/how-to-use-linked-undo-management.md)  
 Łączy w sobie zarządzanie połączonego cofania do edytora.  
  
## <a name="reference"></a>Tematy pomocy  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsChangeTrackingUndoManager>  
 Umożliwia zarządzanie cofania dla edytora, która obsługuje wiele widoków.  
