---
title: Uruchamianie tabeli dokumentu | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- read locks
- running document table (RDT), IVsDocumentLockHolder interface
- running document table (RDT)
- running document table (RDT), edit locks
- document data objects, running document table
ms.assetid: bbec74f3-dd8e-48ad-99c1-2df503c15f5a
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4645899e8c4cd73758316a3c2a8d74ccb169aa2d
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2019
ms.locfileid: "72724072"
---
# <a name="running-document-table"></a>Uruchamianie tabeli dokumentu
Środowisko IDE zachowuje listę wszystkich aktualnie otwartych dokumentów w wewnętrznej strukturze o nazwie uruchomiona tabela dokumentów (RDT). Ta lista zawiera wszystkie otwarte dokumenty w pamięci, bez względu na to, czy te dokumenty są obecnie edytowane. Dokument to wszelkie elementy, które są utrwalane, w tym pliki w projekcie lub główny plik projektu (na przykład plik. vcxproj).

## <a name="elements-of-the-running-document-table"></a>Elementy uruchomionej tabeli dokumentów
 W uruchomionej tabeli dokumentu znajdują się następujące wpisy.

|Element|Opis|
|-------------|-----------------|
|Moniker dokumentu|Ciąg, który jednoznacznie identyfikuje obiekt danych dokumentu. Jest to bezwzględna ścieżka pliku dla systemu projektu, który zarządza plikami (na przykład C:\MyProject\MyFile). Ten ciąg jest również używany w przypadku projektów zapisanych w magazynach innych niż systemy plików, takich jak procedury składowane w bazie danych. W takim przypadku system projektu może wyznaczyć unikatowy ciąg, który może rozpoznać i ewentualnie analizować, aby określić sposób przechowywania dokumentu.|
|Właściciel hierarchii|Obiekt hierarchii, który jest właścicielem dokumentu, w postaci reprezentowanej przez interfejs <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>.|
|Identyfikator elementu|Identyfikator elementu dla określonego elementu w hierarchii. Ta wartość jest unikatowa wśród wszystkich dokumentów w hierarchii, które są własnością tego dokumentu, ale ta wartość nie ma gwarancji, aby była unikatowa w różnych hierarchiach.|
|Obiekt danych dokumentu|Jest to `IUnknown`<br /><br /> Stream. IDE nie wymaga żadnego określonego interfejsu poza interfejsem `IUnknown` dla obiektu danych dokumentu niestandardowego edytora. Jednak w przypadku edytora standardowego implementacja edytora interfejsu <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2> jest wymagana do obsługi wywołań trwałości plików z projektu. Aby uzyskać więcej informacji, zobacz [Zapisywanie standardowego dokumentu](../../extensibility/internals/saving-a-standard-document.md).|
|Flagi|Flagi kontrolujące, czy dokument jest zapisywany, czy zastosowana jest blokada odczytu lub edycji i tak dalej, można określić podczas dodawania wpisów do RDT. Aby uzyskać więcej informacji, zobacz Wyliczenie <xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS>.|
|Edytuj liczbę blokad|Liczba blokad edycji. Blokada edycji wskazuje, że dokument jest otwarty do edycji. Po przeniesieniu liczby blokad edycji na zero użytkownik jest monitowany o zapisanie dokumentu, jeśli został zmodyfikowany. Na przykład za każdym razem, gdy otwierasz dokument w edytorze przy użyciu **nowego okna** polecenie, w RDT zostanie dodana blokada edycji. Aby można było ustawić blokadę edycji, dokument musi mieć identyfikator hierarchii lub elementu.|
|Liczba blokad odczytu|Liczba blokad odczytu. Blokada odczytu wskazuje, że dokument jest odczytywany za pomocą pewnego mechanizmu, takiego jak Kreator. Blokada odczytu utrzymuje dokument aktywny w RDT, a jednocześnie wskazuje, że nie można edytować dokumentu. Można ustawić blokadę odczytu nawet wtedy, gdy dokument nie ma hierarchii lub identyfikatora elementu. Ta funkcja umożliwia otwieranie dokumentu w pamięci i wprowadzanie go w RDT bez użycia dokumentu przez żadną hierarchię. Ta funkcja jest rzadko używana.|
|Symbol zastępczy blokady|Wystąpienie interfejsu <xref:Microsoft.VisualStudio.Shell.Interop.IVsDocumentLockHolder>. Posiadacz blokady jest implementowany przez funkcje, takie jak kreatory otwierające i edytujące dokumenty poza edytorem. Posiadacz blokady pozwala funkcji dodać blokadę edycji do dokumentu, aby zapobiec zamykaniu dokumentu, gdy nadal jest edytowany. Zwykle blokady edycji są dodawane tylko przez okna dokumentów (czyli edytorów).|

 Każdy wpis w RDT ma unikatową hierarchię lub skojarzony identyfikator elementu, który zwykle odnosi się do jednego węzła w projekcie. Wszystkie dokumenty dostępne do edycji są zwykle własnością hierarchii. Wpisy wprowadzone w RDT kontrolować, który projekt lub — dokładniej — która hierarchia aktualnie jest właścicielem obiektu danych dokumentu. Korzystając z informacji w RDT, IDE może uniemożliwić otwieranie dokumentu przez więcej niż jeden projekt w danym momencie.

 Hierarchia również kontroluje trwałość danych i używa informacji w RDT, aby zaktualizować okna dialogowe **Zapisz** i **Zapisz jako** . Gdy użytkownicy modyfikują dokument, a następnie wybierzesz polecenie **Zakończ** z menu **plik** , IDE wyświetli monit z oknem dialogowym **Zapisz zmiany** , aby wyświetlić wszystkie projekty i elementy projektu, które są obecnie modyfikowane. Dzięki temu użytkownicy mogą wybrać dokumenty do zapisania. Lista dokumentów do zapisania (czyli dokumentów, które mają zmiany) jest generowana z RDT. Wszystkie elementy, które powinny być widoczne w oknie dialogowym **Zapisywanie zmian** podczas zamykania aplikacji, powinny mieć rekordy w RDT. RDT koordynuje, które dokumenty są zapisywane i czy użytkownik jest monitowany o operację zapisywania przy użyciu wartości określonych we wpisie flag dla każdego dokumentu. Aby uzyskać więcej informacji na temat flag RDT, zobacz Wyliczenie <xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS>.

## <a name="edit-locks-and-read-locks"></a>Edytuj blokady i blokady odczytu
 Edytowanie blokad i blokad odczytu znajduje się w RDT. Okno dokumentu zwiększa i zmniejsza blokadę edycji. W tym przypadku, gdy użytkownik otworzy nowe okno dokumentu, liczba blokad jest zwiększana o jeden. Gdy liczba blokad edycji osiągnie wartość zero, hierarchia jest zapisywana w celu utrwalenia lub zapisania danych dla skojarzonego dokumentu. Hierarchia może następnie przechowywać dane w dowolny sposób, w tym utrwalać jako plik lub jako element w repozytorium. Za pomocą metody <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.LockDocument%2A> w interfejsie <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable> można dodać blokady edycji i blokady odczytu oraz metodę <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.UnlockDocument%2A>, aby usunąć te blokady.

 Zwykle po utworzeniu wystąpienia okna dokumentu dla edytora ramka okna automatycznie dodaje blokadę edycji dla dokumentu w RDT. Jeśli jednak utworzysz niestandardowy widok dokumentu, który nie korzysta z standardowego okna dokumentu (oznacza to, że nie implementuje interfejsu <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame>), należy ustawić własną blokadę edycji. Na przykład w Kreatorze dokument jest edytowany bez otwierania w edytorze. Aby blokady dokumentów były otwierane przez kreatory i podobne jednostki, te jednostki muszą implementować interfejs <xref:Microsoft.VisualStudio.Shell.Interop.IVsDocumentLockHolder>. Aby zarejestrować posiadacza blokady dokumentu, wywołaj metodę <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.RegisterDocumentLockHolder%2A> i przekaż implementację <xref:Microsoft.VisualStudio.Shell.Interop.IVsDocumentLockHolder>. Spowoduje to dodanie właściciela blokady dokumentu do RDT. Innym scenariuszem implementacji posiadacza blokady dokumentu jest otwarcie dokumentu za pomocą specjalnego okna narzędzi. W tym przypadku nie jest możliwe, aby okno narzędzia zostało zamknięte. Jednak przez zarejestrowanie jako posiadacza blokady dokumentu w RDT, IDE może wywołać implementację metody <xref:Microsoft.VisualStudio.Shell.Interop.IVsDocumentLockHolder.CloseDocumentHolder%2A> w celu wyświetlenia monitu o zamknięcie dokumentu.

## <a name="other-uses-of-the-running-document-table"></a>Inne zastosowania uruchomionej tabeli dokumentów
 Inne jednostki w IDE używają RDT, aby uzyskać informacje o dokumentach. Na przykład Menedżer kontroli źródła używa RDT do informowania systemu o konieczności ponownego załadowania dokumentu w edytorze, po uzyskaniu najnowszej wersji pliku. W tym celu Menedżer kontroli źródła wyszukuje pliki w RDT, aby sprawdzić, czy którykolwiek z nich jest otwarty. Jeśli są, Menedżer kontroli źródła najpierw sprawdza, czy w hierarchii implementuje metodę <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.ReloadItem%2A>. Jeśli projekt nie implementuje metody <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.ReloadItem%2A>, Menedżer kontroli źródła sprawdza implementację metody <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2.ReloadDocData%2A> bezpośrednio w obiekcie danych dokumentu.

 IDE używa również RDT do przenoszenia (Przesuń na wierzch) otwartego dokumentu, jeśli użytkownik zażąda tego dokumentu. Aby uzyskać więcej informacji, zobacz [Wyświetlanie plików przy użyciu polecenia Otwórz plik](../../extensibility/internals/displaying-files-by-using-the-open-file-command.md). Aby określić, czy plik jest otwarty w RDT, wykonaj jedną z następujących czynności.

- Zapytanie o moniker dokumentu (czyli pełną ścieżkę dokumentu), aby dowiedzieć się, czy element jest otwarty.

- Użyj hierarchii lub identyfikatora elementu, aby poprosił system projektu o pełną ścieżkę dokumentu, a następnie wyszukać element w górę w RDT.

## <a name="see-also"></a>Zobacz także
- [Użycie flagi RDT_ReadLock](../../extensibility/internals/rdt-readlock-usage.md)
- [Trwałość i uruchamianie tabeli dokumentów](../../extensibility/internals/persistence-and-the-running-document-table.md)