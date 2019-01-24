---
title: Zapisywanie niestandardowego dokumentu | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- persistence, saving custom documents
- projects [Visual Studio SDK], saving custom documents
- editors [Visual Studio SDK], saving custom documents
ms.assetid: 040b36d6-1f0a-4579-971c-40fbb46ade1d
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 020fdd0f2b315b876790e86b0e16c047cfd44db2
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54760883"
---
# <a name="saving-a-custom-document"></a>Zapisywanie niestandardowego dokumentu
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Obsługuje środowisko **Zapisz**, **Zapisz jako**, i **Zapisz wszystko** poleceń. Kiedy użytkownik kliknie **Zapisz**, **Zapisz jako**, **lub Zapisz wszystko** na **pliku** menu lub zamyka rozwiązania skutkuje Zapisz wszystko, następujące proces.  
  
 ![Zapisywanie w edytorze niestandardowym](../../extensibility/internals/media/private.gif "prywatne")  
Zapisz, Zapisz jako, a następnie Zapisz wszystko obsługi poleceń dla niestandardowego edytora  
  
 Ten proces opisano szczegółowo w poniższych krokach:  
  
1.  Dla **Zapisz** i **Zapisz jako** poleceń, używa środowiska <xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection> service, aby ustalić aktywne okno dokumentu i w ten sposób elementy powinny być zapisywane. Gdy aktywne okno dokumentu jest znany, środowiska znajduje wskaźnik hierarchii i identyfikator elementu (identyfikator elementu) dla dokumentów w uruchomionej tabeli dokumentu. Aby uzyskać więcej informacji, zobacz [uruchamianie tabeli dokumentu](../../extensibility/internals/running-document-table.md).  
  
     Zapisz wszystkie polecenia środowiska używa tych informacji w uruchomionej tabeli dokumentu do kompilacji listę wszystkich elementów do zapisania.  
  
2.  Po odebraniu rozwiązania <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> wywołania iteruje zbiór wybranych elementów (czyli udostępnianych przez wiele zaznaczeń <xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection> usługi).  
  
3.  Dla każdego elementu w zaznaczeniu odbywa się za wskaźnik hierarchii wywołań <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.IsItemDirty%2A> metodę pozwala ustalić, czy polecenie menu Zapisz powinien być włączony. Jeśli co najmniej jeden element jest zanieczyszczony, polecenie Zapisz jest włączone. Jeśli hierarchia używa standardowy edytor, następnie delegatów hierarchii, wykonanie zapytania dotyczącego zakłóconych stanu do edytora, wywołując <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2.IsDocDataDirty%2A> metody.  
  
4.  Dla każdego wybranego elementu, który został zmieniony, odbywa się za wskaźnik hierarchii wywołań <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.SaveItem%2A> metody w odpowiedniej hierarchii.  
  
     W przypadku niestandardowego edytora komunikacji między obiektem danych dokumentów i projektu jest prywatny. W efekcie wszelkie problemy dotyczące trwałości specjalne są obsługiwane między tymi dwoma obiektami.  
  
    > [!NOTE]
    >  W przypadku zastosowania własne trwałości, pamiętaj wywołać <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QuerySaveFiles%2A> metodę, aby zaoszczędzić czas. Ta metoda sprawdza się upewnić, że jest bezpieczne zapisać plik (na przykład plik nie jest tylko do odczytu).  
  
## <a name="see-also"></a>Zobacz też  
 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>   
 [Otwieranie i zapisywanie elementów projektu](../../extensibility/internals/opening-and-saving-project-items.md)
