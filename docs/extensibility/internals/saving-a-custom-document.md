---
title: Zapisywanie dokumentu niestandardowego | Dokumenty firmy Microsoft
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80705612"
---
# <a name="saving-a-custom-document"></a>Zapisywanie niestandardowego dokumentu
Środowisko obsługuje polecenia **Zapisz,** **Zapisz jako**i Zapisz **wszystkie.** Gdy użytkownik kliknie **polecenie Zapisz**, **Zapisz jako**lub **Zapisz wszystko** w menu **Plik** lub zamknie rozwiązanie, co spowoduje zapisanie wszystkich, następuje następujący proces.

 ![Zapisz edytor klienta](../../extensibility/internals/media/private.gif "Private") Obsługa poleceń Zapisz, Zapisz jako i Zapisz wszystkie dla edytora niestandardowego

 Ten proces jest szczegółowo opisany w następujących krokach:

1. W przypadku poleceń **Zapisz** i **Zapisz** jako <xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection> środowisko używa usługi do określenia okna aktywnego dokumentu, a tym samym, jakie elementy powinny zostać zapisane. Po znaniu aktywnego okna dokumentu środowisko znajduje wskaźnik hierarchii i identyfikator elementu (itemID) dla dokumentu w uruchomionej tabeli dokumentów. Aby uzyskać więcej informacji, zobacz [Uruchamianie tabeli dokumentów](../../extensibility/internals/running-document-table.md).

     W przypadku polecenia Zapisz wszystko środowisko używa informacji w uruchomionej tabeli dokumentów do skompilowania listy wszystkich elementów do zapisania.

2. Gdy rozwiązanie odbiera <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> wywołanie, iteruje za pośrednictwem zestawu wybranych elementów (czyli <xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection> wiele wyborów udostępniane przez usługę).

3. Na każdym elemencie w zaznaczeniu rozwiązanie używa <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.IsItemDirty%2A> wskaźnika hierarchii, aby wywołać metodę, aby określić, czy polecenie Zapisz menu powinno być włączone. Jeśli jeden lub więcej elementów jest zabrudzonych, włączona jest funkcja Zapisz. Jeśli hierarchia używa edytora standardowego, hierarchia deleguje zapytania o stan <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2.IsDocDataDirty%2A> brudny do edytora, wywołując metodę.

4. Na każdym wybranym elemencie, który jest brudny, rozwiązanie używa wskaźnika hierarchii do wywołania <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.SaveItem%2A> metody w odpowiednich hierarchiach.

     W przypadku edytora niestandardowego komunikacja między obiektem danych dokumentu a projektem jest prywatna. W związku z tym wszelkie szczególne obawy trwałości są obsługiwane między tymi dwoma obiektami.

    > [!NOTE]
    > Jeśli zaimplementujesz własną trwałość, <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QuerySaveFiles%2A> należy wywołać metodę, aby zaoszczędzić czas. Ta metoda sprawdza, czy jest bezpieczne, aby zapisać plik (na przykład plik nie jest tylko do odczytu).

## <a name="see-also"></a>Zobacz też
- <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>
- [Otwieranie i zapisywanie elementów projektu](../../extensibility/internals/opening-and-saving-project-items.md)
