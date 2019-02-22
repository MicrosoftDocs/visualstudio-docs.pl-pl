---
title: Uruchamianie tabeli dokumentu | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- read locks
- running document table (RDT), IVsDocumentLockHolder interface
- running document table (RDT)
- running document table (RDT), edit locks
- document data objects, running document table
ms.assetid: bbec74f3-dd8e-48ad-99c1-2df503c15f5a
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9c91aa3cbad7fd58fbd819e46f3f3428f68801e9
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/21/2019
ms.locfileid: "56618942"
---
# <a name="running-document-table"></a>Uruchamianie tabeli dokumentu
IDE utrzymuje listę wszystkich aktualnie otwarte dokumenty w wewnętrznej struktury o nazwie uruchomionej tabeli dokumentu (Normalizacją). Ta lista zawiera wszystkie otwarte dokumenty w pamięci, niezależnie od tego, czy te dokumenty są obecnie edytowane. Dokument jest dowolny element, który jest trwały, w tym pliki w projekcie lub w pliku projektu głównego (na przykład plik .vcxproj).

## <a name="elements-of-the-running-document-table"></a>Elementy uruchamianie tabeli dokumentów
 Uruchamianie tabeli dokumentu zawiera następujące wpisy.

|Element|Opis|
|-------------|-----------------|
|Moniker dokumentu|Ciąg, który unikatowo identyfikuje obiekt danych dokumentu. Powinien to być ścieżka bezwzględna do pliku systemu projektu, który zarządza plikami (na przykład C:\MyProject\MyFile). Ten ciąg służy również dla projektów zapisanych w magazynów innych niż systemy plików, takie jak procedur składowanych w bazie danych. W takim przypadku system projektu można wymyślić unikatowy ciąg, który może rozpoznawać i prawdopodobnie analizy w celu ustalenia sposobu przechowywania dokumentu.|
|Właściciel hierarchii|Obiekt hierarchii, która jest właścicielem dokumentu, reprezentowane przez <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> interfejsu.|
|Identyfikator elementu|Identyfikator elementu dla określonego elementu w hierarchii. Ta wartość jest unikatowa wśród wszystkich dokumentów w hierarchii, która jest właścicielem tego dokumentu, ale ta wartość nie musi być unikatowa w obrębie różnych hierarchii.|
|Obiekt danych dokumentu|Jako minimum, to `IUnknown`<br /><br /> obiekt. IDE nie wymaga żadnego konkretnego interfejsu poza `IUnknown` interfejs dla obiektu danych dokumentu niestandardowego edytora. Jednak w przypadku standardowego edytora implementacja edytora <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2> interfejsu jest wymagany do obsługi połączeń trwałości plik z projektu. Aby uzyskać więcej informacji, zobacz [zapisywanie standardowego dokumentu](../../extensibility/internals/saving-a-standard-document.md).|
|Flagi|Flagi określające, czy dokument zostanie zapisany, czy zastosowano blokady odczytu lub edycji i tak dalej, można określić po dodaniu do Normalizacją wpisów. Aby uzyskać więcej informacji, zobacz <xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS> wyliczenia.|
|Edytuj liczbę blokad|Liczba blokad edycji. Edytuj blokadę wskazuje, czy niektóre edytor jest otwarty do edycji dokument. Liczba blokad edycji przejścia na zero, użytkownik jest monitowany można zapisać dokumentu, jeśli został zmodyfikowany. Na przykład za każdym razem, gdy otwarcie dokumentu w edytorze za pomocą **nowe okno** polecenia edycji blokady jest dodawany do tego dokumentu w Normalizacją. Aby blokady edycji, należy ustawić dokument musi posiadać hierarchii lub identyfikator elementu|
|Liczba blokad odczytu|Liczba blokad odczytu. Blokady odczytu wskazuje, czy dokument jest jest do odczytu za pośrednictwem mechanizmu, takich jak kreatora. Blokady odczytu zawiera dokument w Normalizacją wskazujące, że nie można edytować dokumentu. Można ustawić blokadę odczytu, nawet jeśli dokument nie ma hierarchii lub identyfikator elementu Ta funkcja pozwala na otwieranie dokumentu w pamięci, a następnie wprowadź go w Normalizacją bez dokumentu własność dowolnego hierarchii. Ta funkcja jest rzadko używana.|
|Właściciel blokady|Wystąpienie <xref:Microsoft.VisualStudio.Shell.Interop.IVsDocumentLockHolder> interfejsu. Właściciel blokady jest implementowany przez funkcje, takie jak kreatorach, które otwieranie i edytowanie dokumentów, poza edytorem. Właściciel blokady umożliwia funkcji, które można dodać blokady edycji do dokumentu, aby uniemożliwić dokumentu jest zamknięty, gdy jest on nadal edytowany. Normalnie edytować blokady są dodawane tylko przez system windows dokumentu (czyli edytory).|

 Każdy wpis Normalizacją ma unikatowy hierarchii lub skojarzony z nim, identyfikator elementu, która zazwyczaj odnosi się do jednego węzła w projekcie. Zazwyczaj należą wszystkie dokumenty dostępne do edycji przez hierarchię. Wpisy w Normalizacją kontrolować projektu, lub — dokładniej — które hierarchii jest bieżącym właścicielem obiektu danych dokumentu edytowany. Korzystając z informacji w Normalizacją, IDE może uniemożliwić dokument jest otwarty przez więcej niż jeden projekt naraz.

 Hierarchia także kontroluje trwałości danych i używa informacji w Normalizacją, aby zaktualizować **Zapisz** i **Zapisz jako** okien dialogowych. Po modyfikacji dokumentu użytkowników, a następnie wybierz **zakończenia** polecenia **pliku** menu IDE wyświetla monit o ich za pomocą **Zapisz zmiany** okno dialogowe, aby wyświetlić wszystkie projekty i elementy projektu, które są aktualnie modyfikowane. Dzięki temu użytkownicy mogą wybrać, które dokumenty można zapisać. Na liście dokumentów, aby zapisać (czyli tych dokumentów, które mają zmiany) jest generowany na podstawie Normalizacją. Wszystkie elementy, które powinny być widoczne w **Zapisz zmiany** okno dialogowe podczas zamykania aplikacji powinien zawierać rekordy w Normalizacją. Współrzędne Normalizacją, które dokumenty są zapisywane i tego, czy użytkownik jest monitowany o zapisanie operację, używając wartości określonej we wpisie flagi dla każdego dokumentu. Aby uzyskać więcej informacji na temat flagi Normalizacją, zobacz <xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS> wyliczenia.

## <a name="edit-locks-and-read-locks"></a>Edytuj blokad i blokady odczytu
 Edytuj blokad i blokady odczytu znajdują się w Normalizacją. Zwiększa okno dokumentu i zmniejsza wartość blokowania edycji. W związku z tym gdy użytkownik otwiera nowe okno dokumentu, edycji liczbę blokad zwiększa o jeden. Gdy liczba blokad edycji osiągnie zero, hierarchii zasygnalizowania do utrwalenia lub zapisać danych dla skojarzonego dokumentu. Hierarchii można następnie zachować dane w dowolny sposób, w tym utrwalanie jako plik lub jako element w repozytorium. Możesz użyć <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.LockDocument%2A> method in Class metoda <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable> interfejsu, aby dodać edytowania blokad i odczytywania blokad, a <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.UnlockDocument%2A> metoda usuwania tych blokad.

 Zwykle podczas tworzenia wystąpienia okno dokumentu edytora ramki okna automatycznie dodaje blokady edycji dokumentu Normalizacją. Jednak jeśli tworzysz niestandardowy widok dokumentu który nie korzysta z oknem żadnego standardowego dokumentu (czyli nie implementuje <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame> interfejsu), należy ustawić własne blokady edycji. Na przykład w kreatorze, dokument jest edytowany nie jest otwarty w edytorze. Aby blokady dokumentu do otwierania przez kreatory i podobne jednostki, te jednostki muszą implementować <xref:Microsoft.VisualStudio.Shell.Interop.IVsDocumentLockHolder> interfejsu. Aby zarejestrować swoje blokadę dokumentu, należy wywołać <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.RegisterDocumentLockHolder%2A> metody i Przekaż swoje <xref:Microsoft.VisualStudio.Shell.Interop.IVsDocumentLockHolder> implementacji. Spowoduje to dodanie Twojej blokadę dokumentu do Normalizacją. Inny scenariusz implementacji właściciela blokady dokumentu polega na tym, jeśli można otworzyć dokumentu za pomocą okna narzędzie specjalne. W tym wypadku możesz nie będą mieć okna narzędzi, zamknij dokument. Jednak rejestrując jako symbol zastępczy blokady dokumentu w Normalizacją, IDE może wywołać implementacji <xref:Microsoft.VisualStudio.Shell.Interop.IVsDocumentLockHolder.CloseDocumentHolder%2A> metoda monit zamknięciem dokumentu.

## <a name="other-uses-of-the-running-document-table"></a>Inne zastosowania uruchamianie tabeli dokumentów
 Inne jednostki w środowisku IDE Użyj Normalizacją do uzyskania informacji o dokumenty. Na przykład przez menedżera kontroli źródła używa Normalizacją, aby poinformować system w celu ponownego załadowania dokumentu w edytorze po uzyskuje najnowszą wersję pliku. Aby to zrobić, menedżera kontroli źródła wyszukuje pliki w Normalizacją, aby sprawdzić, czy któryś z nich są otwarte. Jeśli są one, a następnie menedżera kontroli źródła najpierw sprawdza, czy hierarchii implementuje <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.ReloadItem%2A> metody. Jeśli projekt nie zawiera implementacji <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.ReloadItem%2A> metody, a następnie źródło sterowania manager sprawdza, czy implementacja <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2.ReloadDocData%2A> metody na obiekt danych dokumentu bezpośrednio.

 IDE używa również Normalizacją do resurface (przesuwanie do przodu) otwartego dokumentu, jeśli użytkownik zażąda tego dokumentu. Aby uzyskać więcej informacji, zobacz [wyświetlanie plików za pomocą polecenia Otwórz plik](../../extensibility/internals/displaying-files-by-using-the-open-file-command.md). Aby ustalić, czy plik jest otwarty w Normalizacją, wykonaj jedną z następujących czynności.

-   Kwerenda dotycząca moniker dokumentu (oznacza to ścieżki pełny dokument) sprawdzić, czy element jest otwarty.

-   Identyfikator hierarchii lub element umożliwia poproś system projektu dla ścieżki pełny dokument, a następnie wyszukaj element Normalizacją.

## <a name="see-also"></a>Zobacz też
- [Użycie flagi RDT_ReadLock](../../extensibility/internals/rdt-readlock-usage.md)
- [Trwałość i uruchamianie tabeli dokumentów](../../extensibility/internals/persistence-and-the-running-document-table.md)