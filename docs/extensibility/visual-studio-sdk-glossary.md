---
title: Słowniczek SDK programu Visual Studio | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- glossary [Visual Studio SDK]
ms.assetid: b64d432b-c39b-4904-ad18-3c3218b6e3aa
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 332e606e689e9394f2fcdc8cbc902e2d4a6e5ab5
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80698167"
---
# <a name="visual-studio-sdk-glossary"></a>Słowniczek SDK programu Visual Studio
Ten glosariusz zawiera definicje terminów, które są używane w [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] dokumentacji.

## <a name="terms"></a>Warunki
 dodatek Aplikacja narzędziowa, sterownik lub inne oprogramowanie dodane do aplikacji podstawowej. W zintegrowanym środowisku programistycznym programu Visual Studio (IDE) dodatek jest aplikacją opartą na automatyzacji, która rozszerza możliwości IDE.

 model automatyzacji Model automatyzacji, znany w poprzednich wersjach programu Visual Studio jako model rozszerzalności, jest interfejsem programowania, który daje dostęp do podstawowych procedur, które napędzają IDE. Dodatki, kreatory i makra używają obiektów w modelu automatyzacji do kontrolowania lub rozszerzania funkcji IDE.

 command UI context Association of a GUID with the visibility of a UI command command (Narzędzie interfejsu użytkownika) skojarzenie identyfikatora GUID z widocznością polecenia interfejsu użytkownika lub elementu, takiego jak pasek narzędzi. Kontekst interfejsu użytkownika polecenia różni się od kontekstu wyboru, ponieważ nie jest dołączony do okna.

 Kontekst interfejsu użytkownika polecenia może służyć do:

- Przypisz identyfikator GUID do paska narzędzi, który pojawia się po uaktywnieniu określonego okna.

- Przypisz identyfikator GUID do dostępności polecenia bez konieczności ładowania lub uruchamiania vsPackage.

- Przypisz identyfikator GUID, aby wpłynąć na aktywne powiązanie kluczy.

- Przypisz identyfikator GUID, aby włączyć nagrywanie makr.

- Przypisz identyfikator GUID, aby włączyć tryb debugowania lub przełączać się między trybem projektowania i uruchamiania w edytorze.

  składnik Oprogramowanie, które może być częścią funkcjonalności aplikacji bez tej aplikacji posiadającej jakiekolwiek wcześniej istniejące informacje o implementacji oprogramowania. Komunikacja między składnikiem a aplikacją odbywa się wyłącznie za pośrednictwem interfejsów stylu OLE.

  menedżer składników Usługa, `SOleComponentManager`która zapewnia usługi koordynacji interfejsu nienawiązanego użytkownika dla składników najwyższego poziomu. Usługa `SOleComponentManager` implementuje `IOleComponentManager` interfejs.

  component UI manager `SOleComponentUIManager`A service, which provides user interface coordination services. Usługa `SOleComponentUIManager` implementuje `IOleComponentUIManager` i `IOleInPlaceComponentUIManager` interfejsy.

  torba kontekstowa Obiekt `IVsUserContext` (obiekt COM) dołączony do składnika środowiska. Ten obiekt zawiera słowa kluczowe wyszukiwania, słowa kluczowe **F1** i atrybuty, które odnoszą się do składnika. Torby kontekstowe dodatkowo wskazują na wszystkie torby podkontekstowe, które są z nimi powiązane.

  context provider Składnik w IDE, który ma element kontekstu skojarzone z nim. Takie składniki obejmują okno narzędzia, edytor lub hierarchię projektu.

  projektant Interfejs programowania, który umożliwia użytkownikom manipulowanie elementami interfejsu użytkownika (formularze, przyciski i inne formanty).

  DocData A COM obiekt hermetyzujący podstawowe dane dokumentu w świecie, w którym istnieje separacja dokumentu/widoku (na przykład w przypadku edytora tekstu, byłby to bufor tekstu leżący u podstaw wszystkich widoków edytora tekstu). Jeśli EditorFactory nie dostarcza tego obiektu, IDE produkuje jeden w jego imieniu. Odpowiedzialność tego obiektu polega na zarządzaniu trwałością danych i semantyzą `DocData`udostępniania dla wielu widoków nad tym samym . Jeśli `DocData` obiekt obsługuje `IOleCommandTarget` interfejs, jest on zawarty w routingu polecenia UIShell.

  Technologia DocObject używana do hostowania interfejsu użytkownika w ramce dostarczonej przez hosta. W szczególności termin ten odnosi się do każdego `IOleDocument` osadzania, który obsługuje i powiązanych interfejsów. Ta technologia ma wiele potencjalnych zastosowań, takich jak szczegóły implementacji dokumentów COM, okna narzędzi w języku Visual Basic 5.0, projektanci ActiveX w języku Visual Basic 6.0 i tak dalej.

  dokument Używany do ogólnego odwoływania się do `DocData` dokumentu `DocView`jako całości — zarówno Na przykład DocumentFrame zawiera `DocView`, ale zachowuje również odwołanie `DocData` do do obsługi trwałości.

  DocView DocObject/Embedding/WindowPane, z którym użytkownik wchodzi w interakcję, aby wyświetlić i manipulować podstawową `DocData`. Użytkownicy nie korzystają z separacji Dokument/Widok, `DocObject` która jest częścią projektu interfejsu. Użytkownicy używają całego DocObject do działania jako widok zamiast używać bardziej abstrakcyjne (i `DocData`mniej sformalizowane) pojęcie podstawowych danych, znany jako . `DocView`obiekty są zawsze osadzone z obiektami ramki dokumentu (okna podrzędne MDI) IDE.

  DTE `DTE` (Rozszerzalność narzędzi programistycznych) obiekt jest najwyższym punktem dostępu w modelu automatyzacji programu Visual Studio, który umożliwia programowo zautomatyzować i rozszerzyć IDE.

  Okno Pomocy dynamicznej Okno Narzędzia zaimplementowane przez IDE wyświetla listę słów kluczowych wyszukiwania lub tematów Pomocy **F1.**

  editor Code (class, CLSID), `DocView`który implementuje . Implementuje `DocData` również, jeśli widok i separacja danych jest obsługiwana.

  rozszerzenie Funkcja, która modyfikuje, dostosowuje lub dodaje do IDE. Rozszerzenia można utworzyć przy użyciu modelu automatyzacji lub VSPackages.

  edytor zewnętrzny Edytor, który nie jest specyficzny dla IDE, takich jak Microsoft Word. Został on zarejestrowany za pośrednictwem własnych mechanizmów i może być używany poza IDE. Jeśli ten edytor może być osadzony, pojawia się w oknie w IDE. Jeśli nie można go osadzać, zostanie utworzone oddzielne okno najwyższego poziomu.

  hierarchia Drzewo węzłów, każdy węzeł skojarzony z zestawem właściwości.

  niezależny składnik najwyższego poziomu Składnik, który używa niemodowego okna najwyższego poziomu i może skutecznie działać jako autonomiczne okno aplikacji, ale jest implementowany jako obiekt w procesie. W związku z tym niezależny składnik najwyższego poziomu musi koordynować usługi modalności i pętli komunikatów z IDE. Obiekty w toku nie mają własnej pętli komunikatów.

  dostawca informacji Dostawca informacji jest modułem, który może wyszukiwać słowa kluczowe `IVsUserContextItem` i zwracać listę tematów w postaci obiektów. Aby udostępnić elementy klawiszy kluczowych **F1** i wyszukiwania dla dostawcy informacji, zarejestruj skompilowany plik Pomocy (*. HxS*) z systemem. Tematy Pomocy w tych plikach zawierają listę tematów wyświetlanych w oknie Pomoc dynamiczna i pokazano, czy użytkownik naciśnie **klawisz F1**.

  składnik w miejscu A VSPackage obiektu, który implementuje `IOleInPlaceComponent` interfejs do zarządzania okno, które jest wizualnie zawarte w oknie dokumentu własnością IDE. Składniki w miejscu nie uczestniczą w standardowym łączeniu menu OLE; zamiast tego integrują swoje elementy interfejsu użytkownika do IDE.

  Istnieją dwa typy komponentów w miejscu: komponenty przewodowe w miejscu i elementy sterujące.

  Składniki w miejscu z łączoną przewodami mają menu, paski narzędzi i polecenia, które są ściśle zintegrowane z interfejsem użytkownika IDE, wyglądające tak, jakby były wbudowane bezpośrednio w IDE.

  Formanty składników nie mają żadnych własnych elementów interfejsu użytkownika zintegrowanych z IDE; Zamiast tego używają menu IDE, poleceń i pasków narzędzi. Na przykład polecenie Pogrubienie może służyć do pogrubienia zaznaczonego wyrazu w formancie tekstu sformatowanego osadzonego w formularzu. Jednak formanty składników można zażądać, aby dynamicznie zainstalowane elementy interfejsu użytkownika specyficzne dla składnika być wyświetlane.

  usługa językowa Zestaw obiektów, który umożliwia deweloperom VSPackage implementowanie funkcji edytorów kodów języka komputerowego, takich jak oznaczanie tekstu i kolorowanie.

  Różne pliki projektu projektu używane do domu otwarte pliki, które nie są w żadnym projekcie. Lista elementów w tym projekcie nie jest utrwalona.

  projekty projektu są wykonane z hierarchy obiektów lub `IVsHierarchy` obiektów COM, które implementują interfejs.

  projektant lub edytor specyficzny dla projektu Projektant, którego nie można używać niezależnie od typu projektu. Wszyscy projektanci specyficyjni w projekcie muszą wprowadzić informacje o fabryce edytora w rejestrze. IDE następnie można utworzyć wystąpienie projektanta, gdy określony typ pliku jest otwarty w określonym projekcie.

  okno typu projektu Okno, które stale śledzi aktualnie aktywną hierarchię projektu i element z kontekstu wyboru globalnego. Okna typu projektu `SVsTrackSelectionEx` używają usługi do ostrzegania IDE o zmianach i wyświetlania opinii dla użytkownika. Eksplorator rozwiązań jest przykładem okna typu projektu.

  Okno Właściwości poprzednio przeglądarka właściwości.

  projekty referencyjne Project, który nie wymaga plików dla projektu, aby znajdować się w tym samym katalogu. Zamiast tego odwołania do plików z innych niepowiązanych katalogów są przechowywane i obsługiwane przez sam projekt.

  uruchamianie tabeli dokumentów Struktura wewnętrzna, za pomocą której IDE przechowuje listę wszystkich aktualnie otwartych dokumentów. Lista zawiera wszystkie otwarte dokumenty w pamięci, niezależnie od tego, czy dokumenty są obecnie edytowane. Dokument jest dowolnym elementem, który jest zapisywany, w tym procedury przechowywane otwarte w edytorze, pliki w projekcie lub głównym pliku projektu (na przykład *.vcproj pliku).

  kontekst wyboru Dane, które są częścią szczegółów każdego okna w IDE i jest używany do śledzenia aktywnych wyborów. Kontekst selekcji składa się z:

- Wskaźnik do `IVsHierarchy` interfejsu hierarchii projektu

- Identyfikator elementu elementu projektu.

- Wskaźnik do `ISelectionContainer` interfejsu zapewniającego dostęp do właściwości aktywnych obiektów.

- Tablica wartości elementu.

  usługa Umowa dla zestawu interfejsów COM, który znajduje się w jednym obiekcie COM. Podczas tworzenia usługi, która jest identyfikowana przez identyfikator GUID, należy zdefiniować zestaw interfejsów COM, który wykonuje usługę. Obiekty COM używają usług do komunikowania się ze sobą.

  rozwiązanie Grupa powiązanych projektów, z którymi użytkownik pracuje.

  standardowy projektant Projektant, który może być używany niezależnie od typu projektu. Wszyscy projektanci standardowi muszą wprowadzić informacje o fabryce edytora w rejestrze. IDE następnie można utworzyć wystąpienia projektanta, gdy plik z określonym rozszerzeniem jest otwarty. Dane muszą być zachowywane w pliku.

  standardowy edytor, który może być używany niezależnie od określonego typu projektu. Tacy redaktorzy mają EditorFactories zarejestrowanych w rejestrze. Dzięki temu IDE do zlokalizowania i wywołania edytora.

  standardowy edytor systemu operacyjnego Osadzanie, które nie jest specyficzne dla programu Visual Studio. Jest zarejestrowany przy użyciu dobrze znanych kluczy Win32 (na przykład Eksplorator Win32 wie, jak wywołać). Jeśli taki edytor może być osadzony, edytor nadal pojawia się w jego miejscu w IDE. W przeciwnym razie dla takich edytorów zostanie utworzone oddzielne okno najwyższego poziomu.

  torba podtekstowa Obiekt `IVsUserContext` połączony z workiem kontekstowym. Obiekt przechowuje słowa kluczowe wyszukiwania, słowa kluczowe **F1** i atrybuty zaznaczenia w składniku IDE. Przykłady podkontekstu obejmują polecenie w oknie narzędzia lub słowo kluczowe w edytorze.

  Okno Narzędzia listy zadań, które jest implementowane przez IDE i wyświetla listę aktywnych zadań.

  buforu tekstu Nazwa `VSTextBuffer`zwyczajowa obiektu .

  Widok tekstu Nazwa pospolita obiektu `VSTextView`.

  narzędzie najwyższego poziomu składnik, który działa jako niemodowe okno podręczne, ściśle koordynując z interfejsem użytkownika IDE. Podobnie jak niezależne składniki najwyższego poziomu, składniki najwyższego poziomu narzędzia muszą również koordynować usługi modalności i pętli komunikatów z IDE.

  składnik najwyższego poziomu A VSPackage obiektu, który zarządza niemodalnym oknie najwyższego poziomu zamiast obszaru klienta okna IDE. Składniki najwyższego poziomu `IOleComponent` implementują interfejs, aby korzystać z usług pętli komunikatów, takich jak dostęp do czasu bezczynności.

  Aktywny obiekt A VSPackage, który jest widoczny i aktualnie ma fokus.

  Hierarchia interfejsu użytkownika Obiekt COM, `IVsUIHierarchy` który implementuje interfejs, aby umożliwić wyświetlanie hierarchii. Okno hierarchii interfejsu użytkownika `ISelectionContainer` implementuje interfejs, aby zaktualizować okno Właściwości; inne okna typu projektu można użyć tej implementacji, w razie potrzeby.

  Tabela poleceń programu VSCT Visual Studio. Plik vsct zawiera informacje o rozmieszczeniu i zachowaniach menu, pasków narzędzi i poleceń w formacie XML.

  VSPackage Instalowalny kawałek oprogramowania, który rozszerza IDE programu Visual Studio, współtwórcą co najmniej jednego z następujących elementów: interfejs użytkownika, usługi, typy projektów lub edytor/projektant. VsPackage składa się z obiektu COM, który implementuje `IVsPackage` interfejs i jeden lub więcej innych obiektów COM, które implementują inne interfejsy do obsługi zaznaczenia i innych funkcji. Ponadto VSPackage ma określone wymagania dotyczące rejestracji.
