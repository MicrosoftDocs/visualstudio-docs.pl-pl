---
title: Zapisywanie standardowego dokumentu | Microsoft Docs
description: Dowiedz się więcej na temat procesu, który występuje w przypadku standardowego dokumentu dla typu projektu, który można dodać do środowiska IDE programu Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], saving standard documents
- projects [Visual Studio SDK], saving standard documents
- persistence, saving standard documents
ms.assetid: d692fedf-b46e-4d60-84bd-578635042235
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 18e7fcb73a5ce89fae0936189eada9e3b959a55f
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99958456"
---
# <a name="saving-a-standard-document"></a>Zapisywanie standardowego dokumentu
Środowisko obsługuje polecenia Zapisz, Zapisz jako i Zapisz wszystkie. Gdy użytkownik wybierze pozycję **Zapisz**, **Zapisz jako** lub **Zapisz wszystko** w menu **plik** lub zamknie rozwiązanie, spowoduje to wystąpienie następującego procesu: **Zapisz wszystko**.

 ![Edytor standardowy](../../extensibility/internals/media/public.gif "Publiczne") Zapisz, Zapisz jako i Zapisz całą obsługę poleceń dla edytora standardowego

 Ten proces jest szczegółowo opisany w następujących krokach:

1. Gdy wybrane są polecenia **Zapisz** i **Zapisz jako** , środowisko używa <xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection> usługi do określenia okna aktywnego dokumentu, a tym samym elementów, które powinny być zapisane. Po znalezieniu okna aktywnego dokumentu środowisko odnajdzie wskaźnik hierarchii i identyfikator elementu (itemID) dla dokumentu w uruchomionej tabeli dokumentów. Aby uzyskać więcej informacji, zobacz [Uruchamianie tabeli dokumentów](../../extensibility/internals/running-document-table.md).

    Gdy jest zaznaczone polecenie **Zapisz wszystko** , środowisko używa informacji w uruchomionej tabeli dokumentu do skompilowania listy wszystkich elementów do zapisania.

2. Gdy rozwiązanie odbiera <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> wywołanie, przechodzi przez zestaw wybranych elementów (to znaczy wybór wielokrotny uwidoczniony przez <xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection> usługę).

3. Dla każdego elementu w zaznaczeniu, rozwiązanie używa wskaźnika hierarchii do wywołania <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.IsItemDirty%2A> metody, aby określić, czy polecenie **Zapisz** menu powinno być włączone. Jeśli co najmniej jeden element jest zanieczyszczony, polecenie **Zapisz** jest włączone. Jeśli hierarchia używa edytora standardowego, wówczas obiekt delegowany wykonuje zapytania o zmieniony stan do edytora przez wywołanie <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2.IsDocDataDirty%2A> metody.

4. W przypadku każdego zaznaczonego elementu, który jest zanieczyszczony, rozwiązanie używa wskaźnika hierarchii do wywołania <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.SaveItem%2A> metody w odpowiednich hierarchiach.

    W hierarchii często można edytować dokument przy użyciu standardowego edytora. W takim przypadku obiekt danych dokumentu dla tego edytora powinien obsługiwać <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2> interfejs. Po odebraniu <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.SaveItem%2A> wywołania metody projekt powinien poinformować Edytor, że dokument jest zapisywany przez wywołanie <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2.SaveDocData%2A> metody w obiekcie danych dokumentu. Edytor może pozwolić, aby środowisko obsługiwało okno dialogowe **Zapisywanie jako** , wywołując `Query Service` dla <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell> interfejsu. Zwraca wskaźnik do <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell> interfejsu. Edytor musi następnie wywołać <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SaveDocDataToFile%2A> metodę, przekazując wskaźnik do <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat> implementacji edytora za pomocą `pPersistFile` parametru. Środowisko następnie wykonuje operację zapisywania i udostępnia okno dialogowe **Zapisz jako** dla edytora. Środowisko następnie wywołuje z powrotem do edytora za pomocą <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat> .

5. Jeśli użytkownik podejmuje próbę zapisania dokumentu bez tytułu (czyli poprzednio niezapisanego dokumentu), wówczas jest wykonywane polecenie Zapisz jako.

6. W przypadku polecenia Zapisz jako środowisko wyświetla okno dialogowe Zapisz jako z monitem o nazwę pliku.

    Jeśli nazwa pliku została zmieniona, hierarchia jest odpowiedzialna za aktualizowanie informacji w pamięci podręcznej ramki dokumentu przez wywołanie <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.SetProperty%2A> (VSFPROPID_MkDocument).

   Jeśli polecenie **Zapisz jako** przenosi lokalizację dokumentu, a hierarchia jest wrażliwa na lokalizację dokumentu, hierarchia jest odpowiedzialna za przekazanie własności otwartego okna dokumentu do innej hierarchii. Na przykład dzieje się tak, jeśli projekt śledzi, czy plik jest plikiem wewnętrznym lub zewnętrznym (plik różne) w odniesieniu do projektu. Aby zmienić własność pliku na projekt różne pliki, należy wykonać poniższą procedurę.

## <a name="changing-file-ownership"></a>Zmiana własności pliku

#### <a name="to-change-file-ownership-to-the-miscellaneous-files-project"></a>Aby zmienić własność plików na projekt różne pliki

1. Usługa zapytań dla <xref:Microsoft.VisualStudio.Shell.Interop.SVsExternalFilesManager> interfejsu.

     Wskaźnik do <xref:Microsoft.VisualStudio.Shell.Interop.IVsExternalFilesManager2> jest zwracany.

2. Wywołaj <xref:Microsoft.VisualStudio.Shell.Interop.IVsExternalFilesManager2.TransferDocument%2A> `pszMkDocumentNew` metodę (, `punkWindowFrame` ), aby przesłać dokument do nowej hierarchii. Hierarchia wykonująca polecenie Zapisz jako wywołuje tę metodę.

## <a name="see-also"></a>Zobacz też
- <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>
- [Otwieranie i zapisywanie elementów projektu](../../extensibility/internals/opening-and-saving-project-items.md)
