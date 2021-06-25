---
title: Uruchamianie programu Document Table | Microsoft Docs
description: Dowiedz się, jak Visual Studio IDE utrzymuje tabelę uruchomionych dokumentów, która zawiera wszystkie otwarte dokumenty w pamięci.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- read locks
- running document table (RDT), IVsDocumentLockHolder interface
- running document table (RDT)
- running document table (RDT), edit locks
- document data objects, running document table
ms.assetid: bbec74f3-dd8e-48ad-99c1-2df503c15f5a
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: d260534d58853afc6b84ba484eb3a806250e2aa6
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/25/2021
ms.locfileid: "112900411"
---
# <a name="running-document-table"></a>Uruchamianie tabeli dokumentu
Ide przechowuje listę wszystkich obecnie otwartych dokumentów w wewnętrznej strukturze nazywanej tabelą uruchomionych dokumentów (RDT). Ta lista zawiera wszystkie otwarte dokumenty w pamięci, niezależnie od tego, czy te dokumenty są obecnie edytowane. Dokument to dowolny utrwalony element, w tym pliki w projekcie lub głównym pliku projektu (na przykład plik vcxproj).

## <a name="elements-of-the-running-document-table"></a>Elementy uruchomionej tabeli dokumentów
 Uruchomiona tabela dokumentów zawiera następujące wpisy.

|Element|Opis|
|-------------|-----------------|
|Moniker dokumentów|Ciąg jednoznacznie identyfikujący obiekt danych dokumentu. Jest to bezwzględna ścieżka pliku dla systemu projektu, który zarządza plikami (na przykład C:\MyProject\MyFile). Ten ciąg jest również używany w przypadku projektów zapisywanych w magazynach innych niż systemy plików, takich jak procedury składowane w bazie danych. W takim przypadku system projektu może wymyślić unikatowy ciąg, który może rozpoznać i być może przesądzi w celu określenia sposobu przechowywania dokumentu.|
|Właściciel hierarchii|Obiekt hierarchii, który jest właścicielem dokumentu, reprezentowany przez <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> interfejs.|
|Identyfikator elementu|Identyfikator elementu dla określonego elementu w hierarchii. Ta wartość jest unikatowa wśród wszystkich dokumentów w hierarchii, które są właścicielami tego dokumentu, ale ta wartość nie musi być unikatowa w różnych hierarchiach.|
|Obiekt danych dokumentu|Co najmniej jest to `IUnknown`<br /><br /> Obiektu. Ide nie wymaga żadnego konkretnego interfejsu poza interfejsem dla obiektu danych dokumentów `IUnknown` edytora niestandardowego. Jednak w przypadku edytora standardowego implementacja interfejsu w edytorze jest wymagana do obsługi wywołań trwałości plików <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2> z projektu. Aby uzyskać więcej informacji, zobacz [Zapisywanie dokumentu standardowego](../../extensibility/internals/saving-a-standard-document.md).|
|Flagi|Flagi, które kontrolują, czy dokument jest zapisywany, czy jest stosowana blokada odczytu lub edycji itp., można określić podczas dodaniu wpisów do RDT. Aby uzyskać więcej informacji, zobacz <xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS> wyliczenie .|
|Edytowanie liczby blokad|Liczba blokad edycji. Blokada edycji wskazuje, że w niektórych edytorach dokument jest otwarty do edycji. Gdy liczba blokad edycji zostanie zmieniona na zero, użytkownik zostanie poproszony o zapisanie dokumentu, jeśli został zmodyfikowany. Na przykład za każdym razem, gdy otwierasz dokument w edytorze za pomocą polecenia Nowe okno, do tego dokumentu w RDT jest dodawana blokada edycji.  Aby można było ustawić blokadę edycji, dokument musi mieć identyfikator hierarchii lub elementu.|
|Liczba blokad odczytu|Liczba blokad odczytu. Blokada odczytu wskazuje, że dokument jest odczytywany za pomocą pewnego mechanizmu, takiego jak kreator. Blokada odczytu przechowuje dokument o aktywności w RDT, wskazując, że dokumentu nie można edytować. Blokadę odczytu można ustawić nawet wtedy, gdy dokument nie ma hierarchii ani identyfikatora elementu. Ta funkcja umożliwia otwarcie dokumentu w pamięci i wprowadzenie go w RDT bez posiadania dokumentu w żadnej hierarchii. Ta funkcja jest rzadko używana.|
|Uchwyt blokady|Wystąpienie <xref:Microsoft.VisualStudio.Shell.Interop.IVsDocumentLockHolder> interfejsu. Uchwyt blokady jest implementowany przez funkcje, takie jak kreatory, które otwierają i edytują dokumenty poza edytorem. Uchwyt blokady umożliwia funkcji dodanie blokady edycji do dokumentu, aby zapobiec zamknięciu dokumentu, gdy jest on nadal edytowany. Zwykle blokady edycji są dodawane tylko przez okna dokumentów (czyli edytory).|

 Z każdym wpisem w RDT jest skojarzona unikatowa hierarchia lub identyfikator elementu, co zazwyczaj odpowiada jednemu węzłem w projekcie. Wszystkie dokumenty dostępne do edycji są zwykle własnością hierarchii. Wpisy wprowadzone w RDT kontrolują, który projekt lub — dokładniej — która hierarchia jest obecnie właścicielem edytowanego obiektu danych dokumentu. Korzystając z informacji w RDT, ide może uniemożliwić otwarcie dokumentu przez więcej niż jeden projekt na raz.

 Hierarchia kontroluje również trwałość danych i używa informacji w RDT  do **aktualizowania** okien dialogowych Zapisz i Zapisz jako. Gdy użytkownicy zmodyfikują dokument, a następnie wybiorą polecenie  **Exit** z **menu** Plik, w ideu zostanie wyświetlony monit z oknie dialogowym Zapisywanie zmian, aby wyświetlić wszystkie projekty i elementy projektu, które są obecnie modyfikowane. Dzięki temu użytkownicy mogą wybrać dokumenty do zapisania. Lista dokumentów do zapisania (czyli dokumentów, które mają zmiany) jest generowana z RDT. Wszystkie elementy, które powinny  być wyświetlane w oknie dialogowym Zapisywanie zmian po zakończeniu pracy z aplikacją, powinny mieć rekordy w RDT. RdT koordynuje, które dokumenty są zapisywane i czy użytkownik jest monitowany o operację zapisywania przy użyciu wartości określonych we wpisie Flagi dla każdego dokumentu. Aby uzyskać więcej informacji na temat flag RDT, zobacz <xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS> wyliczenie.

## <a name="edit-locks-and-read-locks"></a>Edytowanie blokad i blokad odczytu
 Edytuj blokady i blokady odczytu znajdują się w RDT. Okno dokumentu zwiększa i zmniejsza blokadę edycji. W związku z tym, gdy użytkownik otworzy nowe okno dokumentu, liczba blokad edycji zwiększa się o jeden. Gdy liczba blokad edycji osiągnie zero, zostanie zasygnalizowana hierarchia, aby utrwalić lub zapisać dane dla skojarzonego dokumentu. Hierarchia może następnie utrwalać dane w dowolny sposób, w tym utrwalać jako plik lub jako element w repozytorium. Możesz użyć metody w interfejsie, aby dodać blokady edycji i blokady odczytu, a także metodę , <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.LockDocument%2A> <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable> aby usunąć te <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.UnlockDocument%2A> blokady.

 Zwykle podczas wystąpienia okna dokumentu dla edytora ramka okna automatycznie dodaje blokadę edycji dokumentu w RDT. Jeśli jednak utworzysz niestandardowy widok dokumentu, który nie używa standardowego okna dokumentu (czyli nie implementuje interfejsu), musisz ustawić własną blokadę <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame> edycji. Na przykład w kreatorze dokument jest edytowany bez konieczności jego otwarcia w edytorze. Aby blokady dokumentów były otwierane przez kreatory i podobne jednostki, te jednostki muszą implementować <xref:Microsoft.VisualStudio.Shell.Interop.IVsDocumentLockHolder> interfejs. Aby zarejestrować właściciela blokady dokumentu, wywołaj <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.RegisterDocumentLockHolder%2A> metodę i przekaż <xref:Microsoft.VisualStudio.Shell.Interop.IVsDocumentLockHolder> implementację. Powoduje to dodanie właściciela blokady dokumentu do RDT. Innym scenariuszem implementacji posiadacza blokady dokumentu jest otwarcie dokumentu za pomocą specjalnego okna narzędzi. W tym przypadku nie można zamknąć okna narzędzia. Jednak rejestrując się jako właściciel blokady dokumentu w RDT, ide może wywołać implementację metody , aby <xref:Microsoft.VisualStudio.Shell.Interop.IVsDocumentLockHolder.CloseDocumentHolder%2A> monitować o zamknięcie dokumentu.

## <a name="other-uses-of-the-running-document-table"></a>Inne zastosowania uruchomionej tabeli dokumentów
 Inne jednostki w idee używają RDT do uzyskiwania informacji o dokumentach. Na przykład menedżer kontroli źródła używa RDT, aby poinformować system o ponownym załadowaniu dokumentu w edytorze po uzyskaniu najnowszej wersji pliku. Aby to zrobić, menedżer kontroli źródła wyszukuje pliki w RDT, aby sprawdzić, czy którekolwiek z nich są otwarte. Jeśli tak, menedżer kontroli źródła najpierw sprawdza, czy hierarchia implementuje <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.ReloadItem%2A> metodę . Jeśli projekt nie implementuje metody , menedżer kontroli źródła sprawdza bezpośrednio implementację metody w obiekcie danych <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.ReloadItem%2A> <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2.ReloadDocData%2A> dokumentu.

 Ide używa również RDT do ponownego (przynieś naprzód) otwartego dokumentu, jeśli użytkownik zażąda tego dokumentu. Aby uzyskać więcej informacji, zobacz [Wyświetlanie plików za pomocą otwórz plik polecenia](../../extensibility/internals/displaying-files-by-using-the-open-file-command.md). Aby określić, czy plik jest otwarty w RDT, wykonaj jedną z następujących czynności.

- Zapytanie o moniker dokumentu (czyli pełną ścieżkę dokumentu), aby dowiedzieć się, czy element jest otwarty.

- Użyj hierarchii lub identyfikatora elementu, aby poprosić system projektu o pełną ścieżkę dokumentu, a następnie odszukaj element w RDT.

## <a name="see-also"></a>Zobacz też
- [Użycie flagi RDT_ReadLock](../../extensibility/internals/rdt-readlock-usage.md)
- [Trwałość i uruchamianie tabeli dokumentów](../../extensibility/internals/persistence-and-the-running-document-table.md)
