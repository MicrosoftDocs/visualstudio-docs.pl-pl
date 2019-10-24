---
title: Zapisywanie standardowego dokumentu | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], saving standard documents
- projects [Visual Studio SDK], saving standard documents
- persistence, saving standard documents
ms.assetid: d692fedf-b46e-4d60-84bd-578635042235
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: df93813d339a45689845b82fe4f5a185301b6c74
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2019
ms.locfileid: "72724095"
---
# <a name="saving-a-standard-document"></a>Zapisywanie standardowego dokumentu
Środowisko obsługuje polecenia Zapisz, Zapisz jako i Zapisz wszystkie. Gdy użytkownik wybierze pozycję **Zapisz**, **Zapisz jako**lub **Zapisz wszystko** w menu **plik** lub zamknie rozwiązanie, spowoduje to wystąpienie następującego procesu: **Zapisz wszystko**.

 ![Edytor standardowy](../../extensibility/internals/media/public.gif "Public") Zapisz, Zapisz jako i Zapisz całą obsługę poleceń dla edytora standardowego

 Ten proces jest szczegółowo opisany w następujących krokach:

1. Gdy wybrane są polecenia **Zapisz** i **Zapisz jako** , środowisko używa usługi <xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection>, aby określić okno aktywnego dokumentu, a tym samym elementy, które mają zostać zapisane. Po znalezieniu okna aktywnego dokumentu środowisko odnajdzie wskaźnik hierarchii i identyfikator elementu (itemID) dla dokumentu w uruchomionej tabeli dokumentów. Aby uzyskać więcej informacji, zobacz [Uruchamianie tabeli dokumentów](../../extensibility/internals/running-document-table.md).

    Gdy jest zaznaczone polecenie **Zapisz wszystko** , środowisko używa informacji w uruchomionej tabeli dokumentu do skompilowania listy wszystkich elementów do zapisania.

2. Gdy rozwiązanie odbiera wywołanie <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A>, przechodzi przez zestaw wybranych elementów (to znaczy wybór wielokrotny uwidoczniony przez usługę <xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection>).

3. Dla każdego elementu w zaznaczeniu, rozwiązanie używa wskaźnika hierarchii do wywołania metody <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.IsItemDirty%2A>, aby określić, czy polecenie **Zapisz** menu powinno być włączone. Jeśli co najmniej jeden element jest zanieczyszczony, polecenie **Zapisz** jest włączone. Jeśli hierarchia używa edytora standardowego, wówczas obiekt delegowany tworzy zapytania o zmieniony stan do edytora przez wywołanie metody <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2.IsDocDataDirty%2A>.

4. Dla każdego wybranego elementu, który jest zanieczyszczony, rozwiązanie używa wskaźnika hierarchii do wywołania metody <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.SaveItem%2A> w odpowiednich hierarchiach.

    W hierarchii często można edytować dokument przy użyciu standardowego edytora. W takim przypadku obiekt danych dokumentu dla tego edytora powinien obsługiwać interfejs <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2>. Po odebraniu wywołania metody <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.SaveItem%2A>, projekt powinien poinformować Edytor, że dokument jest zapisywany, wywołując metodę <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2.SaveDocData%2A> w obiekcie danych dokumentu. Edytor może pozwolić, aby środowisko obsługiwało okno dialogowe **Zapisywanie jako** , wywołując `Query Service` dla interfejsu <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell>. Zwraca wskaźnik do interfejsu <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell>. Edytor musi następnie wywołać metodę <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SaveDocDataToFile%2A>, przekazując wskaźnik do implementacji <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat> edytora przy użyciu parametru `pPersistFile`. Środowisko następnie wykonuje operację zapisywania i udostępnia okno dialogowe **Zapisz jako** dla edytora. Środowisko następnie wywołuje z powrotem do edytora przy użyciu <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat>.

5. Jeśli użytkownik podejmuje próbę zapisania dokumentu bez tytułu (czyli poprzednio niezapisanego dokumentu), wówczas jest wykonywane polecenie Zapisz jako.

6. W przypadku polecenia Zapisz jako środowisko wyświetla okno dialogowe Zapisz jako z monitem o nazwę pliku.

    Jeśli nazwa pliku została zmieniona, hierarchia jest odpowiedzialna za aktualizowanie informacji w pamięci podręcznej ramki dokumentu przez wywołanie <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.SetProperty%2A>(VSFPROPID_MkDocument).

   Jeśli polecenie **Zapisz jako** przenosi lokalizację dokumentu, a hierarchia jest wrażliwa na lokalizację dokumentu, hierarchia jest odpowiedzialna za przekazanie własności otwartego okna dokumentu do innej hierarchii. Na przykład dzieje się tak, jeśli projekt śledzi, czy plik jest plikiem wewnętrznym lub zewnętrznym (plik różne) w odniesieniu do projektu. Aby zmienić własność pliku na projekt różne pliki, należy wykonać poniższą procedurę.

## <a name="changing-file-ownership"></a>Zmiana własności pliku

#### <a name="to-change-file-ownership-to-the-miscellaneous-files-project"></a>Aby zmienić własność plików na projekt różne pliki

1. Usługa zapytań dla interfejsu <xref:Microsoft.VisualStudio.Shell.Interop.SVsExternalFilesManager>.

     Zwracany jest wskaźnik do <xref:Microsoft.VisualStudio.Shell.Interop.IVsExternalFilesManager2>.

2. Wywołaj metodę <xref:Microsoft.VisualStudio.Shell.Interop.IVsExternalFilesManager2.TransferDocument%2A> (`pszMkDocumentNew`, `punkWindowFrame`), aby przenieść dokument do nowej hierarchii. Hierarchia wykonująca polecenie Zapisz jako wywołuje tę metodę.

## <a name="see-also"></a>Zobacz także
- <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>
- [Otwieranie i zapisywanie elementów projektu](../../extensibility/internals/opening-and-saving-project-items.md)