---
title: Zapisywanie dokumentu niestandardowego | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- persistence, saving custom documents
- projects [Visual Studio SDK], saving custom documents
- editors [Visual Studio SDK], saving custom documents
ms.assetid: 040b36d6-1f0a-4579-971c-40fbb46ade1d
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: cf67335b6a12b966eb148b3f8dcaf16339e2a29f
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2019
ms.locfileid: "72724085"
---
# <a name="saving-a-custom-document"></a>Zapisywanie niestandardowego dokumentu
Środowisko obsługuje polecenia **Zapisz**, **Zapisz jako**i **Zapisz wszystkie** . Gdy użytkownik kliknie pozycję **Zapisz**, **Zapisz jako** **lub Zapisz wszystko** w menu **plik** lub zamknie rozwiązanie, co spowoduje wystąpienie poniższego procesu.

 ![Zapisywanie w edytorze klienta](../../extensibility/internals/media/private.gif "Private") Zapisz, Zapisz jako i Zapisz całą obsługę poleceń dla edytora niestandardowego

 Ten proces jest szczegółowo opisany w następujących krokach:

1. W przypadku poleceń **Zapisz** i **Zapisz jako** środowisko używa usługi <xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection>, aby określić okno aktywnego dokumentu, a tym samym elementy, które mają zostać zapisane. Po znalezieniu okna aktywnego dokumentu środowisko odnajdzie wskaźnik hierarchii i identyfikator elementu (itemID) dla dokumentu w uruchomionej tabeli dokumentów. Aby uzyskać więcej informacji, zobacz [Uruchamianie tabeli dokumentów](../../extensibility/internals/running-document-table.md).

     W przypadku polecenia Zapisz wszystko środowisko używa informacji w uruchomionej tabeli dokumentu do skompilowania listy wszystkich elementów do zapisania.

2. Gdy rozwiązanie odbiera wywołanie <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A>, przechodzi przez zestaw wybranych elementów (to znaczy wybór wielokrotny uwidoczniony przez usługę <xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection>).

3. Dla każdego elementu w zaznaczeniu, rozwiązanie używa wskaźnika hierarchii do wywołania metody <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.IsItemDirty%2A>, aby określić, czy polecenie Zapisz menu powinno być włączone. Jeśli co najmniej jeden element jest zanieczyszczony, polecenie Zapisz jest włączone. Jeśli hierarchia używa edytora standardowego, wówczas obiekt delegowany tworzy zapytania o zmieniony stan do edytora przez wywołanie metody <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2.IsDocDataDirty%2A>.

4. Dla każdego wybranego elementu, który jest zanieczyszczony, rozwiązanie używa wskaźnika hierarchii do wywołania metody <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.SaveItem%2A> w odpowiednich hierarchiach.

     W przypadku edytora niestandardowego komunikacja między obiektem danych dokumentu a projektem jest prywatna. W ten sposób wszystkie szczególne problemy związane z trwałością są obsługiwane między tymi dwoma obiektami.

    > [!NOTE]
    > W przypadku zaimplementowania własnej trwałości upewnij się, że Wywołaj metodę <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QuerySaveFiles%2A>, aby zaoszczędzić czas. Ta metoda sprawdza, czy można bezpiecznie zapisać plik (na przykład plik nie jest tylko do odczytu).

## <a name="see-also"></a>Zobacz także
- <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>
- [Otwieranie i zapisywanie elementów projektu](../../extensibility/internals/opening-and-saving-project-items.md)