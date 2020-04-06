---
title: Zapisywanie standardowego dokumentu | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], saving standard documents
- projects [Visual Studio SDK], saving standard documents
- persistence, saving standard documents
ms.assetid: d692fedf-b46e-4d60-84bd-578635042235
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e8d50a9e62e69f925564717020a51f88620f5f3b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80705553"
---
# <a name="saving-a-standard-document"></a>Zapisywanie standardowego dokumentu
Środowisko obsługuje polecenia Zapisz, Zapisz jako i Zapisz wszystkie. Gdy użytkownik wybierze **polecenie Zapisz**, **Zapisz jako**lub **Zapisz wszystko** z menu **Plik** lub zamknie rozwiązanie, co spowoduje **zapisanie wszystkich,** następuje następujący proces.

 ![Edytor standardowy](../../extensibility/internals/media/public.gif "Public") Obsługa poleceń Zapisz, Zapisz jako i Zapisz wszystkie dla standardowego edytora

 Ten proces jest szczegółowo opisany w następujących krokach:

1. Po wybraniu polecenia **Zapisz** i **Zapisz jako** środowisko <xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection> używa usługi do określenia aktywnego okna dokumentu, a tym samym, jakie elementy powinny zostać zapisane. Po znaniu aktywnego okna dokumentu środowisko znajduje wskaźnik hierarchii i identyfikator elementu (itemID) dla dokumentu w uruchomionej tabeli dokumentów. Aby uzyskać więcej informacji, zobacz [Uruchamianie tabeli dokumentów](../../extensibility/internals/running-document-table.md).

    Po wybraniu polecenia **Zapisz wszystko** środowisko używa informacji w uruchomionej tabeli dokumentów do skompilowania listy wszystkich elementów do zapisania.

2. Gdy rozwiązanie odbiera <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> wywołanie, iteruje za pośrednictwem zestawu wybranych elementów (czyli <xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection> wiele wyborów udostępniane przez usługę).

3. Na każdym elemencie w zaznaczeniu rozwiązanie używa <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.IsItemDirty%2A> wskaźnika hierarchii, aby wywołać metodę, aby określić, czy polecenie **Zapisz** menu powinno być włączone. Jeśli jeden lub więcej elementów jest zabrudzonych, włączona jest funkcja **Zapisz.** Jeśli hierarchia używa edytora standardowego, hierarchia deleguje zapytania o stan <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2.IsDocDataDirty%2A> brudny do edytora, wywołując metodę.

4. Na każdym wybranym elemencie, który jest brudny, rozwiązanie używa wskaźnika hierarchii do wywołania <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.SaveItem%2A> metody w odpowiednich hierarchiach.

    Często hierarchia używa standardowego edytora do edytowania dokumentu. W takim przypadku obiekt danych dokumentu dla <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2> tego edytora powinien obsługiwać interfejs. Po otrzymaniu <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.SaveItem%2A> wywołania metody, projekt powinien poinformować edytora, że <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2.SaveDocData%2A> dokument jest zapisywany przez wywołanie metody na obiekcie danych dokumentu. Edytor może zezwolić środowisku na obsługę okna `Query Service` dialogowego <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell> **Zapisz jako,** wywołując interfejs. Spowoduje to zwraca <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell> wskaźnik do interfejsu. Edytor musi następnie <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SaveDocDataToFile%2A> wywołać metodę, przekazując wskaźnik <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat> do implementacji `pPersistFile` edytora za pomocą parametru. Następnie środowisko wykonuje operację Zapisz i udostępnia okno dialogowe **Zapisywanie jako** dla edytora. Środowisko następnie wywołuje z powrotem do edytora z . <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat>

5. Jeśli użytkownik próbuje zapisać dokument bez tytułu (czyli wcześniej niezapisanego dokumentu), faktycznie wykonywane jest polecenie Zapisz jako.

6. W przypadku polecenia Zapisz jako środowisko wyświetla okno dialogowe Zapisywanie jako, monitując użytkownika o nazwę pliku.

    Jeśli nazwa pliku uległa zmianie, hierarchia jest odpowiedzialna za aktualizowanie informacji buforowanych <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.SetProperty%2A>ramki dokumentu przez wywołanie (VSFPROPID_MkDocument).

   Jeśli polecenie **Zapisz jako** przenosi lokalizację dokumentu, a hierarchia jest wrażliwa na lokalizację dokumentu, hierarchia jest odpowiedzialna za przekazanie własności otwartego okna dokumentu innej hierarchii. Na przykład dzieje się tak, jeśli projekt śledzi, czy plik jest plikiem wewnętrznym lub zewnętrznym (Plik różne) w odniesieniu do projektu. Poniższa procedura umożliwia zmianę własności pliku na projekt Różne pliki.

## <a name="changing-file-ownership"></a>Zmiana własności pliku

#### <a name="to-change-file-ownership-to-the-miscellaneous-files-project"></a>Aby zmienić własność pliku na projekt Różne pliki

1. Usługa zapytań <xref:Microsoft.VisualStudio.Shell.Interop.SVsExternalFilesManager> dla interfejsu.

     Zwracany <xref:Microsoft.VisualStudio.Shell.Interop.IVsExternalFilesManager2> jest wskaźnik.

2. Wywołanie <xref:Microsoft.VisualStudio.Shell.Interop.IVsExternalFilesManager2.TransferDocument%2A> `pszMkDocumentNew`( `punkWindowFrame`, ) metoda, aby przenieść dokument do nowej hierarchii. Hierarchia wykonująca polecenie Zapisz jako wywołuje tę metodę.

## <a name="see-also"></a>Zobacz też
- <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>
- [Otwieranie i zapisywanie elementów projektu](../../extensibility/internals/opening-and-saving-project-items.md)
