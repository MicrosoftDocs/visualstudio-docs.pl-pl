---
title: Zapisywanie standardowego dokumentu | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], saving standard documents
- projects [Visual Studio SDK], saving standard documents
- persistence, saving standard documents
ms.assetid: d692fedf-b46e-4d60-84bd-578635042235
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 460b948ea7b5bace1b91143d46a4ca2f4c823608
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62859147"
---
# <a name="saving-a-standard-document"></a>Zapisywanie standardowego dokumentu
Środowisko obsługuje Zapisz, Zapisz jako i Zapisz wszystkie polecenia. Gdy użytkownik wybierze **Zapisz**, **Zapisz jako**, lub **Zapisz wszystko** z **pliku** menu lub zamyka rozwiązania skutkuje  **Zapisz wszystko**, odbywa się następujący proces.

 ![Edytor standardowy](../../extensibility/internals/media/public.gif "publicznych") Zapisz, Zapisz jako i Zapisz wszystkie obsługi poleceń dla edytora standardowego

 Ten proces opisano szczegółowo w poniższych krokach:

1. Gdy **Zapisz** i **Zapisz jako** polecenia są zaznaczone, używa środowiska <xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection> service, aby ustalić aktywne okno dokumentu i w ten sposób elementy powinny być zapisywane. Gdy aktywne okno dokumentu jest znany, środowiska znajduje wskaźnik hierarchii i identyfikator elementu (identyfikator elementu) dla dokumentów w uruchomionej tabeli dokumentu. Aby uzyskać więcej informacji, zobacz [uruchamianie tabeli dokumentu](../../extensibility/internals/running-document-table.md).

    Gdy **Zapisz wszystko** polecenie jest zaznaczone, środowisko używa tych informacji w uruchomionej tabeli dokumentu do listy wszystkich elementów do zapisania.

2. Po odebraniu rozwiązania <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> wywołania iteruje zbiór wybranych elementów (czyli udostępnianych przez wiele zaznaczeń <xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection> usługi).

3. Dla każdego elementu w zaznaczeniu odbywa się za wskaźnik hierarchii wywołań <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.IsItemDirty%2A> metodę pozwala ustalić czy **Zapisz** polecenie powinno być włączone. Jeśli co najmniej jednego elementu zostały zmienione, a następnie **Zapisz** polecenie jest włączone. Jeśli hierarchia używa standardowy edytor, następnie delegatów hierarchii, wykonanie zapytania dotyczącego zakłóconych stanu do edytora, wywołując <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2.IsDocDataDirty%2A> metody.

4. Dla każdego wybranego elementu, który został zmieniony, odbywa się za wskaźnik hierarchii wywołań <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.SaveItem%2A> metody w odpowiedniej hierarchii.

    Jest to częsty problem w hierarchii, aby edytować dokument za pomocą edytora standardowego. W tym przypadku dane dokumentu obiekt powinien obsługiwać tego edytora <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2> interfejsu. Odebrane <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.SaveItem%2A> wywołania metody projektu powinien poinformować edytor, który dokument jest zapisywany przez wywołanie metody <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2.SaveDocData%2A> metody na obiekt danych dokumentu. Edytor umożliwia środowisku do obsługi **Zapisz jako** okno dialogowe, wywołując `Query Service` dla <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell> interfejsu. Zwraca wskaźnik do <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell> interfejsu. Edytor następnie należy wywołać <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SaveDocDataToFile%2A> metody przekazywania wskaźnika do edytora <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat> implementacji poprzez `pPersistFile` parametru. Środowisko następnie wykonuje operację zapisywania i zapewnia **Zapisz jako** okno dialogowe edytora. Środowisko wywołuje powrót do edytora za pomocą <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat>.

5. Jeśli użytkownik próbuje zapisać dokument bez tytułu (oznacza to, że wcześniej niezapisane dokumenty), polecenia Zapisz jako faktycznie jest wykonywana.

6. Dla polecenia Zapisz jako środowisko Wyświetla okno dialogowe Zapisz jako z monitem użytkownika o podanie nazwy pliku.

    Jeśli nazwa pliku została zmieniona, a następnie hierarchii odpowiada za aktualizowanie ramki dokumentu buforowanych informacji przez wywołanie metody <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.SetProperty%2A>(VSFPROPID_MkDocument).

   Jeśli **Zapisz jako** polecenia powoduje przeniesienie lokalizacji dokumentu i hierarchii jest wrażliwa na lokalizację dokumentu, a następnie hierarchii jest odpowiedzialny za przekazywanie własności otwartego okna dokumentu do innej hierarchii. Na przykład dzieje się tak Jeśli projekt śledzi, czy plik jest wewnętrzny lub zewnętrzny plik (różne) w odniesieniu do projektu. Aby zmienić własność pliku do projektu różne pliki, należy użyć poniższej procedury.

## <a name="changing-file-ownership"></a>Zmiana własności pliku

#### <a name="to-change-file-ownership-to-the-miscellaneous-files-project"></a>Aby zmienić własność pliku do projektu różne pliki

1. Zapytanie usługi dla <xref:Microsoft.VisualStudio.Shell.Interop.SVsExternalFilesManager> interfejsu.

     Wskaźnik do <xref:Microsoft.VisualStudio.Shell.Interop.IVsExternalFilesManager2> jest zwracana.

2. Wywołaj <xref:Microsoft.VisualStudio.Shell.Interop.IVsExternalFilesManager2.TransferDocument%2A> (`pszMkDocumentNew`, `punkWindowFrame`) metodę, aby przenieść dokument do nowej hierarchii. Hierarchia, wykonując polecenia Zapisz jako wywołuje tę metodę.

## <a name="see-also"></a>Zobacz też
- <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>
- [Otwieranie i zapisywanie elementów projektu](../../extensibility/internals/opening-and-saving-project-items.md)