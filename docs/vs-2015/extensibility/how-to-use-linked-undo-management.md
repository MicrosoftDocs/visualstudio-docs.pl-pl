---
title: 'Porady: Użyj przystawki Zarządzanie połączonego cofania | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - linked undo management
ms.assetid: af5cc22a-c9cf-45b1-a894-1022d563f3ca
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 2a5da4b7c25ab97356798fe8c2db184982fc885d
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51739300"
---
# <a name="how-to-use-linked-undo-management"></a>Porady: Użyj przystawki Zarządzanie połączonego cofania
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Połączonego cofania umożliwia użytkownikowi Cofnij równocześnie w tej samej zmiany w wielu plikach. Na przykład zmiany w tekście jednoczesnych na wiele plików programów, takich jak plik nagłówkowy i plik Visual C++ jest transakcji połączonego cofania. Funkcja połączonego cofania jest wbudowana w implementacji środowiska menedżera cofania i <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLinkedUndoTransactionManager> umożliwia manipulowanie tej możliwości. Połączonego cofania jest implementowany przez nadrzędnej jednostki cofania, który można połączyć cofania osobnych stosów ze sobą, aby być traktowane jako jednostka pojedynczą czynność cofnięcia. W poniższej sekcji opisano szczegółowo procedurę za pomocą połączonego cofania.  
  
### <a name="to-use-linked-undo"></a>Aby użyć połączonego cofania  
  
1.  Wywołaj `QueryService` na `SVsLinkedUndoManager` uzyskać wskaźnik do `IVsLinkedUndoTransactionManager`.  
  
2.  Tworzenie początkowej nadrzędnej jednostki połączonego cofania, wywołując <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLinkedUndoTransactionManager.OpenLinkedUndo%2A>. Spowoduje to punkt początkowy dla zestawu cofnięcie stosów mają być grupowane w stosy połączonego cofania. W `OpenLinkedUndo` metody należy również określić, czy połączonego cofania strict lub nieścisłym. Zachowanie non-strict połączonego cofania oznacza, że zamknąć niektóre dokumenty z połączonego cofania elementów równorzędnych i nadal pozostanie innych połączone cofanie elementów równorzędnych na ich stosów. Zachowanie Strict połączonego cofania Określa, że można cofnąć, razem lub w ogóle nie wszystkie stosy element równorzędny połączonego cofania. Dodaj kolejne połączone cofnięcie stosów, wywołując [IOleUndoManager::Add](http://msdn.microsoft.com/library/windows/desktop/ms680135) metody.  
  
3.  Wywołaj <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLinkedUndoTransactionManager.CloseLinkedUndo%2A> konieczne przywrócenie początkowej kopii wszystkich jednostek połączonego cofania jako jeden.  
  
    > [!NOTE]
    >  Aby zaimplementować Zarządzanie połączonego cofania w edytorze, Dodaj zarządzania cofania. Aby uzyskać więcej informacji dotyczących implementowania połączonego cofania zarządzania, zobacz [porady: Implementowanie zarządzania Cofnij](../extensibility/how-to-implement-undo-management.md).  
  
## <a name="see-also"></a>Zobacz też  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompoundAction>   
 [IOleParentUndoUnit](http://msdn.microsoft.com/library/windows/desktop/ms682151)   
 [IOleUndoUnit](http://msdn.microsoft.com/library/windows/desktop/ms678476)   
 [Instrukcje: implementowanie zarządzania cofaniem](../extensibility/how-to-implement-undo-management.md)

