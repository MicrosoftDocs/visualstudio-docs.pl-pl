---
title: Zarządzanie Cofnij i wykonaj ponownie za pomocą starszej wersji interfejsu API | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - undo management
ms.assetid: 838c0ddf-fdf3-4df1-8d21-79610b8ba0b1
caps.latest.revision: 15
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 7c2133c75b32e56c1a054740bd829bd04cac97cc
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "68194369"
---
# <a name="managing-undo-and-redo-by-using-the-legacy-api"></a>Zarządzanie cofaniem i ponawianiem przy użyciu starszego interfejsu API
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Edytory musi obsługiwać operacje cofania, które pozwalają użytkownikom odwrotnego ich ostatnich zmian, ich modyfikowania kodu. Większość edytorów zaimplementowane mocy [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] i [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] może mieć Obsługa polecenia Cofnij automatycznie udostępniane przez zintegrowanego środowiska programistycznego (IDE).  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Instrukcje: implementowanie zarządzania cofaniem](../extensibility/how-to-implement-undo-management.md)  
 Zapewnia możliwości cofania dla edytorów, przy użyciu jednego lub wielu widoków.  
  
 [Instrukcje: czyszczenie stosu cofania](../extensibility/how-to-clear-the-undo-stack.md)  
 W tym artykule opisano, jak wyczyścić stosu cofania.  
  
 [Instrukcje: używanie dołączonego zarządzania cofaniem](../extensibility/how-to-use-linked-undo-management.md)  
 Łączy w sobie zarządzanie połączonego cofania do edytora.  
  
## <a name="reference"></a>Tematy pomocy  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsChangeTrackingUndoManager>  
 Umożliwia zarządzanie cofania dla edytora, która obsługuje wiele widoków.  
  
## <a name="related-sections"></a>Sekcje pokrewne
