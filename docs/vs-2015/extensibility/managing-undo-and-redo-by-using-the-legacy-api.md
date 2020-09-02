---
title: Zarządzanie Cofnij i wykonaj ponownie przy użyciu starszej wersji interfejsu API | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68194369"
---
# <a name="managing-undo-and-redo-by-using-the-legacy-api"></a>Zarządzanie cofaniem i ponawianiem przy użyciu starszego interfejsu API
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Edytory muszą obsługiwać operacje cofania, które umożliwiają użytkownikom odwracanie ostatnich zmian podczas modyfikowania kodu. Większość edytorów implementowanych w ramach [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] i [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] może mieć możliwość cofnięcia pomocy technicznej automatycznie zapewnianej przez zintegrowane środowisko programistyczne (IDE).  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Instrukcje: implementowanie zarządzania cofaniem](../extensibility/how-to-implement-undo-management.md)  
 Zapewnia możliwość cofnięcia dla edytorów z pojedynczym lub wieloma widokami.  
  
 [Instrukcje: czyszczenie stosu cofania](../extensibility/how-to-clear-the-undo-stack.md)  
 Opisuje sposób czyszczenia stosu cofania.  
  
 [Instrukcje: używanie dołączonego zarządzania cofaniem](../extensibility/how-to-use-linked-undo-management.md)  
 Obejmuje w edytorze połączone zarządzanie Cofnij.  
  
## <a name="reference"></a>Dokumentacja  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsChangeTrackingUndoManager>  
 Zapewnia zarządzanie Cofnij dla edytora, który obsługuje wiele widoków.  
  
## <a name="related-sections"></a>Sekcje pokrewne
