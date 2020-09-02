---
title: 'Instrukcje: implementowanie zarządzania cofaniem | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - undo management
ms.assetid: 1942245d-7a1d-4a11-b5e7-a3fe29f11c0b
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 0f3d56ae02718f5dfdf373eeeb6aff774d11931e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "64831119"
---
# <a name="how-to-implement-undo-management"></a>Instrukcje: implementowanie zarządzania cofaniem
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Podstawowym interfejsem używanym do zarządzania cofaniem jest <xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoManager> , który jest implementowany przez środowisko. Aby obsłużyć zarządzanie Cofnij, należy zaimplementować oddzielne jednostki cofania (czyli <xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoUnit> , które mogą zawierać wiele pojedynczych kroków.  
  
 Sposób implementacji zarządzania cofania zależy od tego, czy Edytor obsługuje wiele widoków, czy nie. Procedury dla każdej implementacji opisano szczegółowo w poniższych sekcjach.  
  
## <a name="cases-where-an-editor-supports-a-single-view"></a>Przypadki, w których Edytor obsługuje pojedynczy widok  
 W tym scenariuszu Edytor nie obsługuje wielu widoków. Istnieje tylko jeden edytor i jeden dokument, który obsługuje cofanie. Aby zaimplementować zarządzanie Cofnij, należy wykonać czynności opisane w poniższej procedurze.  
  
#### <a name="to-support-undo-management-for-a-single-view-editor"></a>Aby obsłużyć zarządzanie Cofnij dla edytora pojedynczego widoku  
  
1. Wywołaj `QueryInterface` `IServiceProvider` interfejs w ramce okna dla `IOleUndoManager` , z obiektu widoku dokumentu, aby uzyskać dostęp do Menedżera cofania ( `IID_IOLEUndoManager` ).  
  
2. Gdy widok znajduje się w ramce okna, Pobiera wskaźnik witryny, którego może użyć do wywołania `QueryInterface` `IServiceProvider` .  
  
## <a name="cases-where-an-editor-supports-multiple-views"></a>Przypadki, w których Edytor obsługuje wiele widoków  
 Jeśli masz rozdzielenia dokumentów i widoków, istnieje zazwyczaj jeden Menedżer cofania skojarzony z samym dokumentem. Wszystkie jednostki cofania są umieszczane w jednym menedżerze cofania skojarzonym z obiektem danych dokumentu.  
  
 Zamiast wyświetlania zapytania dla Menedżera cofania, dla którego istnieje jeden dla każdego widoku, obiekt danych dokumentu wywołuje, <xref:Microsoft.VisualStudio.Shell.Interop.ILocalRegistry2.CreateInstance%2A> Aby utworzyć wystąpienie Menedżera cofania, określając identyfikator klasy CLSID_OLEUndoManager. Identyfikator klasy jest zdefiniowany w pliku OCUNDOID. h.  
  
 Korzystając z programu <xref:Microsoft.VisualStudio.Shell.Interop.ILocalRegistry2.CreateInstance%2A> , aby utworzyć własne wystąpienie Menedżera cofania, należy wykonać poniższą procedurę, aby podłączyć Menedżera cofania do środowiska.  
  
#### <a name="to-hook-your-undo-manager-into-the-environment"></a>Aby podłączyć Menedżera cofania do środowiska  
  
1. Wywołanie `QueryInterface` obiektu zwróconego z <xref:Microsoft.VisualStudio.Shell.Interop.ILocalRegistry2> elementu dla `IID_IOleUndoManager` . Przechowaj wskaźnik do <xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoManager> .  
  
2. Wywołanie `QueryInterface` w `IOleUndoManager` dniu `IID_IOleCommandTarget` . Przechowaj wskaźnik do <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> .  
  
3. Przekaż swoje <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> wywołania i do przechowywanego `IOleCommandTarget` interfejsu dla następujących poleceń StandardCommandSet97:  
  
   - cmdidUndo  
  
   - cmdidMultiLevelUndo  
  
   - cmdidRedo  
  
   - cmdidMultiLevelRedo  
  
   - cmdidMultiLevelUndoList  
  
   - cmdidMultiLevelRedoList  
  
4. Wywołanie `QueryInterface` w `IOleUndoManager` dniu `IID_IVsChangeTrackingUndoManager` . Przechowaj wskaźnik do <xref:Microsoft.VisualStudio.TextManager.Interop.IVsChangeTrackingUndoManager> .  
  
    Użyj wskaźnika, aby <xref:Microsoft.VisualStudio.TextManager.Interop.IVsChangeTrackingUndoManager> wywołać <xref:Microsoft.VisualStudio.TextManager.Interop.IVsChangeTrackingUndoManager.MarkCleanState%2A> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsChangeTrackingUndoManager.AdviseTrackingClient%2A> metody,, i <xref:Microsoft.VisualStudio.TextManager.Interop.IVsChangeTrackingUndoManager.UnadviseTrackingClient%2A> .  
  
5. Wywołanie `QueryInterface` w `IOleUndoManager` dniu `IID_IVsLinkCapableUndoManager` .  
  
6. Zadzwoń <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLinkCapableUndoManager.AdviseLinkedUndoClient%2A> do dokumentu, który powinien również implementować <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLinkedUndoClient> interfejs. Gdy dokument zostanie zamknięty, wywołaj polecenie `IVsLinkCapableUndoManager::UnadviseLinkedUndoClient` .  
  
7. Gdy dokument zostanie zamknięty, wywołaj `QueryInterface` Menedżera cofania dla `IID_IVsLifetimeControlledObject` .  
  
8. Wywołanie <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLifetimeControlledObject.SeverReferencesToOwner%2A> .  
  
9. Gdy zmiany są wprowadzane do dokumentu, wywołaj <xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoManager.Add%2A> Menedżera z `OleUndoUnit` klasą. <xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoManager.Add%2A>Metoda zachowuje odwołanie do obiektu, dlatego na ogół zwolnij go bezpośrednio po <xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoManager.Add%2A> .  
  
   `OleUndoManager`Klasa reprezentuje wystąpienie pojedynczego stosu cofania. W takim przypadku istnieje jeden obiekt Menedżera cofania dla jednostki danych śledzony do operacji Cofnij lub Ponów.  
  
> [!NOTE]
> Mimo że obiekt Menedżera cofania jest szeroko używany przez Edytor tekstu, jest to ogólny składnik, który nie ma określonego wsparcia dla edytora tekstu. Jeśli chcesz obsługiwać wykonywanie operacji cofania wielopoziomowego lub ponawiania, możesz użyć tego obiektu.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsChangeTrackingUndoManager>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLifetimeControlledObject>   
 [Instrukcje: czyszczenie stosu cofania](../extensibility/how-to-clear-the-undo-stack.md)
