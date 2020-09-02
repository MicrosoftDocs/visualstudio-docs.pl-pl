---
title: Zapisywanie dokumentu niestandardowego | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- persistence, saving custom documents
- projects [Visual Studio SDK], saving custom documents
- editors [Visual Studio SDK], saving custom documents
ms.assetid: 040b36d6-1f0a-4579-971c-40fbb46ade1d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f04d588b4becfa778407269849032ea8ec56fb3f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "80705612"
---
# <a name="saving-a-custom-document"></a>Zapisywanie niestandardowego dokumentu
Środowisko obsługuje polecenia **Zapisz**, **Zapisz jako**i **Zapisz wszystkie** . Gdy użytkownik kliknie pozycję **Zapisz**, **Zapisz jako** **lub Zapisz wszystko** w menu **plik** lub zamknie rozwiązanie, co spowoduje wystąpienie poniższego procesu.

 ![Zapisywanie w edytorze klienta](../../extensibility/internals/media/private.gif "Prywatne") Zapisz, Zapisz jako i Zapisz całą obsługę poleceń dla edytora niestandardowego

 Ten proces jest szczegółowo opisany w następujących krokach:

1. W przypadku poleceń **Zapisz** i **Zapisz jako** środowisko używa <xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection> usługi do określenia okna aktywnego dokumentu, a tym samym elementów, które mają zostać zapisane. Po znalezieniu okna aktywnego dokumentu środowisko odnajdzie wskaźnik hierarchii i identyfikator elementu (itemID) dla dokumentu w uruchomionej tabeli dokumentów. Aby uzyskać więcej informacji, zobacz [Uruchamianie tabeli dokumentów](../../extensibility/internals/running-document-table.md).

     W przypadku polecenia Zapisz wszystko środowisko używa informacji w uruchomionej tabeli dokumentu do skompilowania listy wszystkich elementów do zapisania.

2. Gdy rozwiązanie odbiera <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> wywołanie, przechodzi przez zestaw wybranych elementów (to znaczy wybór wielokrotny uwidoczniony przez <xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection> usługę).

3. Dla każdego elementu w zaznaczeniu, rozwiązanie używa wskaźnika hierarchii do wywołania <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.IsItemDirty%2A> metody, aby określić, czy polecenie Zapisz menu powinno być włączone. Jeśli co najmniej jeden element jest zanieczyszczony, polecenie Zapisz jest włączone. Jeśli hierarchia używa edytora standardowego, wówczas obiekt delegowany wykonuje zapytania o zmieniony stan do edytora przez wywołanie <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2.IsDocDataDirty%2A> metody.

4. W przypadku każdego zaznaczonego elementu, który jest zanieczyszczony, rozwiązanie używa wskaźnika hierarchii do wywołania <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.SaveItem%2A> metody w odpowiednich hierarchiach.

     W przypadku edytora niestandardowego komunikacja między obiektem danych dokumentu a projektem jest prywatna. W ten sposób wszystkie szczególne problemy związane z trwałością są obsługiwane między tymi dwoma obiektami.

    > [!NOTE]
    > W przypadku zaimplementowania własnego trwałości należy wywołać <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QuerySaveFiles%2A> metodę w celu zaoszczędzenia czasu. Ta metoda sprawdza, czy można bezpiecznie zapisać plik (na przykład plik nie jest tylko do odczytu).

## <a name="see-also"></a>Zobacz też
- <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>
- [Otwieranie i zapisywanie elementów projektu](../../extensibility/internals/opening-and-saving-project-items.md)
