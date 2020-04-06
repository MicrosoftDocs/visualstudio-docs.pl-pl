---
title: Uruchamianie tabeli dokumentów | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- read locks
- running document table (RDT), IVsDocumentLockHolder interface
- running document table (RDT)
- running document table (RDT), edit locks
- document data objects, running document table
ms.assetid: bbec74f3-dd8e-48ad-99c1-2df503c15f5a
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9e6aa882921786b1592922372581beae8c4c2443
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80705567"
---
# <a name="running-document-table"></a>Uruchamianie tabeli dokumentu
IDE przechowuje listę wszystkich aktualnie otwartych dokumentów w wewnętrznej strukturze zwanej uruchomionej tabeli dokumentów (RDT). Ta lista zawiera wszystkie otwarte dokumenty w pamięci, niezależnie od tego, czy te dokumenty są obecnie edytowane. Dokument jest dowolnym elementem, który jest utrwalony, w tym pliki w projekcie lub głównym pliku projektu (na przykład .vcxproj pliku).

## <a name="elements-of-the-running-document-table"></a>Elementy uruchomionej tabeli dokumentów
 Uruchomiona tabela dokumentów zawiera następujące wpisy.

|Element|Opis|
|-------------|-----------------|
|Moniker dokumentu|Ciąg, który jednoznacznie identyfikuje obiekt danych dokumentu. Byłaby to bezwzględna ścieżka pliku dla systemu projektu, który zarządza plikami (na przykład C:\MyProject\MyFile). Ten ciąg jest również używany dla projektów zapisanych w magazynach innych niż systemy plików, takich jak procedury przechowywane w bazie danych. W takim przypadku system projektu można wymyślić unikatowy ciąg, który można rozpoznać i ewentualnie przeanalizować, aby określić, jak przechowywać dokument.|
|Właściciel hierarchii|Obiekt hierarchii, który jest właścicielem dokumentu, <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> reprezentowane przez interfejs.|
|Identyfikator towaru|Identyfikator elementu dla określonego elementu w hierarchii. Ta wartość jest unikatowa dla wszystkich dokumentów w hierarchii, która jest właścicielem tego dokumentu, ale ta wartość nie jest gwarantowana, aby być unikatowe w różnych hierarchiach.|
|Obiekt danych dokumentu|Jest to co najmniej`IUnknown`<br /><br /> Obiektu. IDE nie wymaga żadnego `IUnknown` określonego interfejsu poza interfejsem dla obiektu danych dokumentu edytora niestandardowego. Jednak dla standardowego edytora implementacja <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2> interfejsu edytora jest wymagana do obsługi wywołań trwałości plików z projektu. Aby uzyskać więcej informacji, zobacz [Zapisywanie dokumentu standardowego](../../extensibility/internals/saving-a-standard-document.md).|
|Flagi|Flagi, które kontrolują, czy dokument jest zapisywany, czy blokada odczytu lub edycji jest stosowana i tak dalej, można określić, gdy wpisy są dodawane do RDT. Aby uzyskać więcej <xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS> informacji, zobacz wyliczenie.|
|Edytuj liczbę blokad|Liczba blokad edycji. Blokada edycji wskazuje, że w niektórych edytorach dokument jest otwarty do edycji. Gdy liczba blokad edycji zostanie przesunie się do zera, użytkownik zostanie poproszony o zapisanie dokumentu, jeśli został zmodyfikowany. Na przykład za każdym razem, gdy otwierasz dokument w edytorze za pomocą polecenia **Nowe okno,** blokada edycji jest dodawana dla tego dokumentu w RDT. Aby blokada edycji została ustawiona, dokument musi mieć hierarchię lub identyfikator elementu.|
|Odczyt liczby blokad|Liczba blokad odczytu. Blokada odczytu wskazuje, że dokument jest odczytywany przez niektóre mechanizmy, takie jak kreator. Blokada odczytu przechowuje dokument przy życiu w RDT, wskazując jednocześnie, że nie można edytować dokumentu. Można ustawić blokadę odczytu, nawet jeśli dokument nie ma hierarchii lub identyfikatora elementu. Ta funkcja umożliwia otwarcie dokumentu w pamięci i wprowadzenie go do rdt bez dokumentu należącego do jakiejkolwiek hierarchii. Ta funkcja jest rzadko używana.|
|Uchwyt blokady|Wystąpienie <xref:Microsoft.VisualStudio.Shell.Interop.IVsDocumentLockHolder> interfejsu. Uchwyt blokady jest implementowany przez funkcje, takie jak kreatory, które otwierają i edytują dokumenty poza edytorem. Uchwyt blokady umożliwia funkcji dodanie blokady edycji do dokumentu, aby zapobiec zamknięciu dokumentu podczas jego edycji. Zwykle blokady edycji są dodawane tylko przez okna dokumentów (czyli edytory).|

 Każdy wpis w RDT ma unikatową hierarchię lub identyfikator elementu skojarzony z nim, co zazwyczaj odpowiada jednemu węzłowi w projekcie. Wszystkie dokumenty dostępne do edycji są zazwyczaj własnością hierarchii. Wpisy wprowadzone w formancie RDT, który projekt lub — dokładniej — hierarchia, obecnie jest właścicielem edytowany obiekt danych dokumentu. Korzystając z informacji w RDT, IDE można zapobiec dokument jest otwierany przez więcej niż jeden projekt naraz.

 Hierarchia kontroluje również trwałość danych i używa informacji w RDT do aktualizowania okien dialogowych **Zapisywanie** i **zapisywanie jako.** Gdy użytkownicy modyfikują dokument, a następnie wybierają polecenie **Zakończ** z menu **Plik,** IDE monituje ich o okno dialogowe **Zapisz zmiany,** aby wyświetlić wszystkie projekty i elementy projektu, które są aktualnie modyfikowane. Dzięki temu użytkownicy mogą wybrać, które dokumenty mają być zapisywane. Lista dokumentów do zapisania (czyli tych dokumentów, które mają zmiany) jest generowana z RDT. Wszystkie elementy, które można oczekiwać, aby zobaczyć w oknie dialogowym **Zapisywanie zmian** po zamknięciu aplikacji powinny mieć rekordy w RDT. Współrzędne RDT, które dokumenty są zapisywane i czy użytkownik jest monitowany o operację zapisywania przy użyciu wartości określonych we wpisie Flagi dla każdego dokumentu. Aby uzyskać więcej informacji na temat <xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS> flag RDT, zobacz wyliczenie.

## <a name="edit-locks-and-read-locks"></a>Edytuj blokady i odczytywanie zamków
 Edytuj blokady i odczytywanie blokad znajdują się w RDT. Okno dokumentu zwiększa i zmniejsza blokadę edycji. W związku z tym gdy użytkownik otwiera nowe okno dokumentu, liczba blokady edycji zwiększa się o jeden. Gdy liczba blokad edycji osiągnie zero, hierarchia jest sygnalizowana do utrwalenia lub zapisania danych dla skojarzonego dokumentu. Hierarchia może następnie utrwalać dane w dowolny sposób, w tym utrwalanie jako plik lub jako element w repozytorium. Można użyć <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.LockDocument%2A> metody w <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable> interfejsie, aby dodać blokady <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.UnlockDocument%2A> edycji i odczytu blokad i metody, aby usunąć te blokady.

 Zwykle po wystąpieniu okna dokumentu dla edytora ramka okna automatycznie dodaje blokadę edycji dokumentu w RDT. Jeśli jednak utworzysz niestandardowy widok dokumentu, który nie używa standardowego okna dokumentu <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame> (oznacza to, że nie implementuje interfejsu), należy ustawić własną blokadę edycji. Na przykład w kreatorze dokument jest edytowany bez otwierania w edytorze. Aby blokady dokumentów mają być otwierane przez kreatorów i podobne <xref:Microsoft.VisualStudio.Shell.Interop.IVsDocumentLockHolder> jednostki, te jednostki muszą implementować interfejs. Aby zarejestrować posiadacza blokady dokumentu, wywołanie <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.RegisterDocumentLockHolder%2A> metody i przekazać w <xref:Microsoft.VisualStudio.Shell.Interop.IVsDocumentLockHolder> implementacji. W ten sposób dodaje uchwyt blokady dokumentu do RDT. Innym scenariuszem implementowania uchwytu blokady dokumentu jest otwarcie dokumentu za pośrednictwem specjalnego okna narzędzia. W tym przypadku nie można zamknąć okna narzędzia. Jednak rejestrując się jako posiadacz blokady dokumentu w RDT, IDE <xref:Microsoft.VisualStudio.Shell.Interop.IVsDocumentLockHolder.CloseDocumentHolder%2A> można wywołać implementacji metody, aby monit o zamknięcie dokumentu.

## <a name="other-uses-of-the-running-document-table"></a>Inne zastosowania uruchomionej tabeli dokumentów
 Inne jednostki w IDE używać RDT do uzyskiwania informacji o dokumentach. Na przykład menedżer kontroli źródła używa RDT, aby poinformować system o ponownym załadowaniu dokumentu w edytorze, po uzyskaniu najnowszej wersji pliku. Aby to zrobić, menedżer kontroli źródła wyszukuje pliki w RDT, aby sprawdzić, czy którykolwiek z nich jest otwarty. Jeśli tak, menedżer kontroli źródła najpierw sprawdza, czy hierarchia <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.ReloadItem%2A> implementuje metodę. Jeśli projekt nie implementuje <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.ReloadItem%2A> metody, menedżer kontroli źródła sprawdza <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2.ReloadDocData%2A> implementację metody na obiekcie danych dokumentu bezpośrednio.

 IDE również używa RDT do ponownego powierzchni (przynieść do przodu) otwarty dokument, jeśli użytkownik żąda tego dokumentu. Aby uzyskać więcej informacji, zobacz [Wyświetlanie plików za pomocą polecenia Otwórz plik](../../extensibility/internals/displaying-files-by-using-the-open-file-command.md). Aby ustalić, czy plik jest otwarty w RDT, wykonaj jedną z następujących czynności.

- Zapytanie o moniker dokumentu (czyli pełną ścieżkę dokumentu), aby dowiedzieć się, czy element jest otwarty.

- Użyj hierarchii lub identyfikatora elementu, aby poprosić system projektu o pełną ścieżkę dokumentu, a następnie wyszukać element w rdt.

## <a name="see-also"></a>Zobacz też
- [Użycie flagi RDT_ReadLock](../../extensibility/internals/rdt-readlock-usage.md)
- [Trwałość i uruchamianie tabeli dokumentów](../../extensibility/internals/persistence-and-the-running-document-table.md)
