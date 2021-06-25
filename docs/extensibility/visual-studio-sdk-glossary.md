---
title: Słownik Visual Studio SDK | Microsoft Docs
description: Ten słownik zawiera definicje terminów używanych w dokumentacji Visual Studio SDK.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- glossary [Visual Studio SDK]
ms.assetid: b64d432b-c39b-4904-ad18-3c3218b6e3aa
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 49e91a64220882eea196819a1860052dc871bec4
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/25/2021
ms.locfileid: "112905426"
---
# <a name="visual-studio-sdk-glossary"></a>Visual Studio zestawu SDK
Ten słownik zawiera definicje terminów używanych w [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] dokumentacji.

## <a name="terms"></a>Terminologia
 add-in (dodatek) Aplikacja narzędziowa, sterownik lub inne oprogramowanie dodane do aplikacji podstawowej. W Visual Studio zintegrowanego środowiska projektowego (IDE) dodatek jest aplikacją opartą na automatyzacji, która rozszerza możliwości środowiska IDE.

 model automatyzacji Model automatyzacji, znany w poprzednich wersjach programu Visual Studio jako model rozszerzalności, to interfejs programowania, który zapewnia dostęp do podstawowych procedur, które są podstawą środowiska IDE. Dodatki, kreatory i makra używają obiektów w modelu automatyzacji do kontrolowania lub rozszerzania funkcjonalności środowiska IDE.

 kontekst interfejsu użytkownika polecenia Skojarzenie identyfikatora GUID z widocznością polecenia interfejsu użytkownika lub elementu, takiego jak pasek narzędzi. Kontekst interfejsu użytkownika polecenia różni się od kontekstu wyboru tym, że nie jest dołączony do okna.

 Kontekst interfejsu użytkownika polecenia może służyć do:

- Przypisz identyfikator GUID do paska narzędzi wyświetlanego po aktywowaniu określonego okna.

- Przypisz identyfikator GUID do dostępności polecenia bez konieczności ładowania ani uruchamiania pakietów VSPackage.

- Przypisz identyfikator GUID, aby wpłynąć na aktywne powiązanie klucza.

- Przypisz identyfikator GUID, aby włączyć rejestrowanie makr.

- Przypisz identyfikator GUID, aby aktywować tryb debugowania lub przełączać się między trybem projektowania i uruchamiania w edytorze.

  component (składnik) Element oprogramowania, który może być częścią funkcjonalności aplikacji, bez konieczności posiadania żadnych wcześniej istniejących informacji o implementacji oprogramowania. Komunikacja między składnikiem a aplikacją jest wyłącznie za pośrednictwem interfejsów stylu OLE.

  menedżer składników Usługa, , która zapewnia usługi koordynacji interfejsu użytkownika dla `SOleComponentManager` składników najwyższego poziomu. Usługa `SOleComponentManager` implementuje `IOleComponentManager` interfejs .

  menedżer interfejsu użytkownika składnika Usługa `SOleComponentUIManager` , która zapewnia usługi koordynacji interfejsu użytkownika. Usługa `SOleComponentUIManager` implementuje `IOleComponentUIManager` `IOleInPlaceComponentUIManager` interfejsy i .

  context bag `IVsUserContext` Obiekt (obiekt COM) dołączony do składnika środowiska. Ten obiekt przechowuje słowa kluczowe wyszukiwania, **słowa kluczowe F1** i atrybuty, które odnoszą się do składnika. Dodatkowe tony kontekstowe wskazują wszystkie połączone z nimi tony podkontekstu.

  dostawca kontekstu Składnik w idee, który ma skojarzony z nim torbę kontekstową. Takie składniki obejmują okno narzędzi, edytor lub hierarchię projektu.

  designer Interfejs programowania, który umożliwia użytkownikom manipulowanie elementami interfejsu użytkownika (formularzami, przyciskami i innymi kontrolkami).

  DocData obiekt COM hermetyzuje dane bazowe dokumentu w świecie, w którym istnieje separacja dokumentów/widoków (na przykład w przypadku edytora tekstów będzie to bufor tekstowy źródłowy wszystkich widoków edytora tekstów). Jeśli editorFactory nie poda tego obiektu, IDE produkuje go w jego imieniu. Ten obiekt jest odpowiedzialny za zarządzanie trwałością danych i semantyką udostępniania dla wielu widoków w tym samym obiekcie `DocData` . Jeśli obiekt `DocData` obsługuje `IOleCommandTarget` interfejs, jest uwzględniony w routingu poleceń w programie UIShell.

  Technologia DocObject używana do hostowania interfejsu użytkownika w ramce dostarczonej przez hosta. Dokładniej rzecz ujmując, ten termin odnosi się do każdego osadzania, które obsługuje `IOleDocument` interfejsy i powiązane. Ta technologia ma wiele potencjalnych aplikacji, takich jak szczegóły implementacji dokumentów COM, okna narzędzi w programie Visual Basic 5.0, projektanci ActiveX w wersji Visual Basic 6.0 itp.

  dokument używany do ogólnego odwołującego się do dokumentu jako całości — zarówno do , `DocData` jak i `DocView` do . Na przykład documentFrame zawiera , ale zachowuje również odwołanie do właściwości w celu `DocView` `DocData` obsługi trwałości.

  DocView The DocObject/Embedding/WindowPane with which the user interacts to view and manipulate the underlying `DocData` . Użytkownicy nie mogą korzystać z separacji dokumentów/widoków, która jest częścią `DocObject` projektu interfejsu. Użytkownicy używają całego docObject, aby działać jako widok, zamiast korzystać z bardziej abstrakcyjnego (i mniej sformalizowanego) myślenia o danych bazowych nazywanych `DocData` . `DocView` Obiekty są zawsze osadzone za pomocą obiektów ramek dokumentów (okien podrzędnych MDI) środowiska IDE.

  DTE Obiekt (rozszerzalność narzędzi programistylnych) jest najwyższym punktem dostępu w modelu automatyzacji usługi Visual Studio, który umożliwia programowe automatyzowanie i rozszerzanie `DTE` środowiska IDE.

  Okno narzędzi dynamicznego okna pomocy, które jest implementowane przez ideę i wyświetla listę słów kluczowych wyszukiwania lub **tematów pomocy F1.**

  edytor kodu (klasa, CLSID), który implementuje `DocView` . Implementuje również, `DocData` jeśli widok i separacja danych są obsługiwane.

  rozszerzenie Funkcja, która modyfikuje, dostosowuje lub dodaje do środowiska IDE. Rozszerzenia tworzy się przy użyciu modelu automatyzacji lub pakietów VSPackage.

  edytor zewnętrzny Edytor, który nie jest specyficzny dla środowiska IDE, taki jak Program Microsoft Word. Został on zarejestrowany za pomocą własnych mechanizmów i może być używany poza ideą IDE. Jeśli ten edytor można osadzić, jest on wyświetlany w oknie w idee. Jeśli nie można go osadzić, tworzone jest oddzielne okno najwyższego poziomu.

  hierarchia Drzewo węzłów, każdy węzeł skojarzony z zestawem właściwości.

  niezależny składnik najwyższego poziomu Składnik, który używa nie moderowego okna najwyższego poziomu i może działać efektywnie jako autonomiczne okno aplikacji, ale jest implementowane jako obiekt w procesie. W związku z tym niezależny składnik najwyższego poziomu musi koordynować współzależność i usługi pętli komunikatów ze środowiskaMI IDE. Obiekty w procesie nie mają własnej pętli komunikatów.

  dostawca informacji Dostawca informacji to moduł, który może wyszukiwać słowa kluczowe i zwracać listę tematów w postaci `IVsUserContextItem` obiektów. Aby zapewnić **F1 i** elementy słów kluczowych wyszukiwania dla dostawcy informacji, zarejestruj skompilowany plik pomocy (*. HxS*) z systemem. Tematy Pomocy w tych plikach zawierają listę tematów wyświetlanych w oknie Pomoc dynamiczna oraz informacje o tym, czy użytkownik naciska **klawisz F1.**

  składnik w miejscu Obiekt VSPackage, który implementuje interfejs do zarządzania oknem, które jest wizualnie zawarte w oknie dokumentu należącym `IOleInPlaceComponent` do środowiska IDE. Składniki w miejscu nie uczestniczą w standardowym scalania menu OLE; Zamiast tego integrują swoje elementy interfejsu użytkownika ze środowiskami IDE.

  Istnieją dwa typy składników w miejscu: twarde składniki w miejscu i kontrolki składników.

  Twarde składniki w miejscu mają menu, paski narzędzi i polecenia, które są ściśle zintegrowane z interfejsem użytkownika środowiska IDE, wyglądając tak, jakby były wbudowane bezpośrednio w idee IDE.

  Kontrolki składników nie mają żadnych własnych elementów interfejsu użytkownika zintegrowanych ze środowiskami IDE; Zamiast tego używają menu, poleceń i pasków narzędzi środowiska IDE. Na przykład polecenie Bold może służyć do pogrubienia wybranego wyrazu w kontrolce tekstu sformatowanego osadzonej w formularzu. Jednak kontrolki składników mogą żądać, aby dynamicznie instalowane elementy interfejsu użytkownika specyficzne dla składnika były wyświetlane.

  usługa językowa Zestaw obiektów, który umożliwia deweloperom pakietów VSPackage implementowanie funkcji edytorów kodu języka komputerowego, takich jak oznaczanie tekstu i kolorowanie.

  Projekt Różne pliki służy do domu otwartych plików, które nie są w żadnym projekcie. Lista elementów w tym projekcie nie jest utrwalana.

  Project Projects składa się z obiektów hierarchii lub obiektów COM, które implementują `IVsHierarchy` interfejs.

  projektant lub edytor specyficzny dla projektu Projektant, który nie może być używany niezależnie od typu projektu. Wszyscy projektanci specyficzni dla projektu muszą wprowadzić informacje o fabryce edytora w rejestrze. Ide może następnie utworzyć wystąpienia projektanta za każdym razem, gdy określony typ pliku zostanie otwarty w konkretnym projekcie.

  okno typu projektu Okno, które stale śledzi aktualnie aktywną hierarchię projektu i element z globalnego kontekstu wyboru. Okna typu projektu używają usługi do powiadamiania środowiska IDE o zmianach i wyświetlania opinii `SVsTrackSelectionEx` użytkownikowi. Eksplorator rozwiązań to przykład okna typu projektu.

  okno Właściwości wcześniej przeglądarka właściwości.

  projekty oparte na odwołaniach Projekt, który nie wymaga, aby pliki projektu zostały w tym samym katalogu. Zamiast tego odwołania do plików z innych niepowiązanych katalogów są przechowywane i utrzymywane przez sam projekt.

  uruchamianie tabeli dokumentów Struktura wewnętrzna, za pomocą której idee przechowuje listę wszystkich obecnie otwartych dokumentów. Lista zawiera wszystkie otwarte dokumenty w pamięci niezależnie od tego, czy dokumenty są obecnie edytowane. Dokument to dowolny zapisany element, w tym procedury składowane otwierane w edytorze, pliki w projekcie lub główny plik projektu (na przykład plik *.vcproj).

  kontekst wyboru Dane, które są częścią szczegółów każdego okna w idee i są używane do śledzenia aktywnych wyborów. Kontekst wyboru składa się z:

- Wskaźnik do `IVsHierarchy` interfejsu hierarchii projektu

- Identyfikator elementu projektu.

- Wskaźnik do `ISelectionContainer` interfejsu zapewniającego dostęp do właściwości dla aktywnych obiektów.

- Tablica wartości elementów.

  service Kontrakt dla zestawu interfejsów COM, który znajduje się w jednym obiekcie COM. Podczas tworzenia usługi, która jest identyfikowana przez identyfikator GUID, należy zdefiniować zestaw interfejsów COM, które wykonuje usługę. Obiekty COM używają usług do komunikowania się ze sobą.

  solution (rozwiązanie) Grupa powiązanych projektów, z którymi pracuje użytkownik.

  projektant standardowy Projektant, który może być używany niezależnie od typu projektu. Wszyscy projektanci standardowi muszą wprowadzić informacje o fabryce edytora w rejestrze. Ide może następnie utworzyć wystąpienia projektanta za każdym razem, gdy zostanie otwarty plik z określonym rozszerzeniem. Dane muszą zostać utrwalone w pliku.

  Edytor standardowy, który może być używany niezależnie od dowolnego typu projektu. Takie edytory mają zarejestrowane w rejestrze edytory EditorFactories. Dzięki temu idee IDE mogą zlokalizować i wywołać edytor.

  standardowy edytor systemu operacyjnego Osadzanie, które nie Visual Studio specyficzne dla systemu. Jest on rejestrowany przy użyciu dobrze znanych kluczy Win32 (na przykład Eksplorator Win32 wie, jak to wywołać). Jeśli taki edytor może być osadzony, edytor nadal jest w jego miejscu w idee IDE. W przeciwnym razie dla takich edytorów zostanie utworzone oddzielne okno najwyższego poziomu.

  subcontext bag Obiekt `IVsUserContext` połączony z torbą kontekstową. Obiekt przechowuje słowa kluczowe wyszukiwania, **słowa kluczowe F1** i atrybuty dla zaznaczenia w składniku IDE. Przykłady podkontekstu to polecenie w oknie narzędzia lub słowo kluczowe w edytorze.

  Okno narzędzia listy zadań implementowane przez ideę i wyświetla listę aktywnych zadań.

  bufor tekstowy Nazwa pospolita obiektu `VSTextBuffer` .

  Widok tekstowy Nazwa pospolita obiektu `VSTextView` .

  narzędzie składnik najwyższego poziomu Składnik, który działa jako nie moderowe okno podręczne, ściśle koordynujący się z interfejsem użytkownika środowiska IDE. Podobnie jak niezależne składniki najwyższego poziomu, składniki najwyższego poziomu narzędzi muszą również koordynować współzależność i usługi pętli komunikatów ze środowiskaMI IDE.

  składnik najwyższego poziomu Obiekt VSPackage, który zarządza niespokojnym oknem najwyższego poziomu zamiast obszarem klienta okna IDE. Składniki najwyższego poziomu implementują `IOleComponent` interfejs, aby korzystać z usług pętli komunikatów, takich jak dostęp do czasu bezczynności.

  Aktywny interfejs użytkownika Obiekt VSPackage, który jest widoczny i aktualnie ma fokus.

  Hierarchia interfejsu użytkownika obiekt COM, który implementuje `IVsUIHierarchy` interfejs w celu umożliwienia wyświetlania hierarchii. Okno hierarchii interfejsu użytkownika implementuje interfejs do aktualizowania okno Właściwości. Inne okna typu projektu mogą używać tej `ISelectionContainer` implementacji, jeśli jest to wymagane.

  Tabela poleceń Visual Studio VSCT. Plik vsct zawiera informacje o umieszczaniu i zachowaniu menu, pasków narzędzi i poleceń w formacie XML.

  VSPackage (PAKIET VSPackage) Instalowalny element oprogramowania rozszerzający ideę Visual Studio przez współtworowanie co najmniej jednego z następujących elementów: interfejs użytkownika, usługi, typy projektów lub edytor/projektant. Pakiet VSPackage składa się z obiektu COM, który implementuje interfejs i co najmniej jeden inny obiekt COM, który implementuje inne interfejsy do obsługi wyboru i `IVsPackage` innych funkcji. Ponadto pakiet VSPackage ma określone wymagania dotyczące rejestracji.
