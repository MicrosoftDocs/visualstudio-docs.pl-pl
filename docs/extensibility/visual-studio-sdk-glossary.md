---
title: Słownik SDK programu Visual Studio | Microsoft Docs
description: Ten słownik zawiera definicje terminów używanych w dokumentacji zestawu SDK programu Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- glossary [Visual Studio SDK]
ms.assetid: b64d432b-c39b-4904-ad18-3c3218b6e3aa
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 3b6ca48ef867aea11bcc5b5be85e4f8d85f07f0a
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2021
ms.locfileid: "105062554"
---
# <a name="visual-studio-sdk-glossary"></a>Słownik SDK programu Visual Studio
Ten słownik zawiera definicje terminów używanych w [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] dokumentacji programu.

## <a name="terms"></a>Terminologia
 dodatek aplikacji narzędziowej, sterownika lub innego oprogramowania dodanego do aplikacji głównej. W zintegrowanym środowisku programistycznym (IDE) programu Visual Studio dodatek jest aplikacją opartą na automatyzacji, która rozszerza możliwości środowiska IDE.

 model automatyzacji model automatyzacji, znany w poprzednich wersjach programu Visual Studio jako model rozszerzalności, to interfejs programowania, który zapewnia dostęp do podstawowych procedur, które są dyskami IDE. Dodatki, kreatory i makra używają obiektów w modelu automatyzacji do kontrolowania lub zwiększania funkcjonalności środowiska IDE.

 Skojarzenie kontekstu interfejsu wiersza polecenia dla identyfikatora GUID z widocznością polecenia interfejsu użytkownika lub elementu, takiego jak pasek narzędzi. Kontekst interfejsu użytkownika polecenia jest w przeciwieństwie do kontekstu wyboru w tym, że nie jest dołączony do okna.

 Kontekst interfejsu użytkownika polecenia może służyć do:

- Przypisz identyfikator GUID do paska narzędzi, który pojawia się po aktywowaniu określonego okna.

- Przypisz identyfikator GUID do dostępności polecenia bez konieczności ładowania lub uruchamiania pakietu VSPackage.

- Przypisz identyfikator GUID, aby miał wpływ na powiązanie z aktywnym kluczem.

- Przypisz identyfikator GUID, aby włączyć rejestrowanie makr.

- Przypisz identyfikator GUID w celu aktywowania trybu debugowania lub przełączania między trybem projektowania i uruchamiania w edytorze.

  składnik oprogramowania, który może być częścią funkcji aplikacji bez konieczności posiadania jakichkolwiek istniejących wcześniej informacji o implementacji oprogramowania. Komunikacja między składnikiem a aplikacją odbywa się wyłącznie za pośrednictwem interfejsów stylów OLE.

  Menedżer składników A usługa, `SOleComponentManager` która zapewnia usługi koordynacji interfejsów innych niż użytkownika dla składników najwyższego poziomu. `SOleComponentManager`Usługa implementuje `IOleComponentManager` interfejs.

  składnik Menedżera interfejsu użytkownika usługi, `SOleComponentUIManager` , która zapewnia usługi koordynacji interfejsów użytkowników. `SOleComponentUIManager`Usługa implementuje `IOleComponentUIManager` `IOleInPlaceComponentUIManager` interfejsy i.

  zbiór kontekstowy `IVsUserContext` obiekt (Object com) dołączony do składnika środowiska. Ten obiekt zawiera słowa kluczowe wyszukiwania, słowa kluczowe **F1** i atrybuty powiązane ze składnikiem. Torby kontekstu wskazują także wszelkie połączone z nimi torby kontekstu.

  Dostawca kontekstu składnik w IDE, z którym jest skojarzony zbiór kontekstowy. Takie składniki obejmują okno narzędzi, Edytor lub hierarchię projektu.

  Projektant jest interfejsem programowania, który umożliwia użytkownikom Manipulowanie elementami interfejsu użytkownika (formularzy, przycisków i innych kontrolek).

  DocData obiekt COM, który hermetyzuje dane bazowe dokumentu na świecie, w którym istnieje separacja dokumentu/widoku (na przykład w przypadku edytora tekstu, będzie to bufor tekstowy dla wszystkich widoków edytora tekstu). Jeśli EditorFactory nie dostarcza tego obiektu, IDE wytwarza je w jego imieniu. Zadaniem tego obiektu jest zarządzanie trwałośćmi danych i semantyką udostępniania dla wielu widoków w tym samym czasie `DocData` . Jeśli `DocData` obiekt obsługuje `IOleCommandTarget` interfejs, zostanie uwzględniony w routingu poleceń UIShell.

  Technologia DocObject używana do hostowania interfejsu użytkownika w obrębie ramki dostarczonej przez hosta. Dokładniej mówiąc, ten termin odnosi się do dowolnego osadzania, które obsługuje `IOleDocument` interfejsy i powiązane z nimi. Ta technologia ma wiele potencjalnych aplikacji, takich jak szczegóły implementacji dokumentów COM, okna narzędzi w Visual Basic 5,0, projektanci ActiveX w Visual Basic 6,0 itd.

  dokument używany do ogólnego odwoływania się do dokumentu jako całości — zarówno do, jak `DocData` i `DocView` . Na przykład DocumentFrame zawiera a `DocView` , ale zachowuje także odwołanie do w `DocData` celu obsługi trwałości.

  DocView DocObject/osadzanie/WindowPane, za pomocą którego użytkownik może wyświetlać i manipulować podstawowym `DocData` . Użytkownicy nie korzystają z separacji dokumentów i widoków, które są częścią `DocObject` projektu interfejsu. Użytkownicy wykorzystują cały DocObject do działania jako widok, zamiast korzystać z bardziej abstrakcyjnych (i mniej formalnych) koncepcji danych podstawowych znanych jako `DocData` . `DocView` obiekty są zawsze osadzone z obiektami ramki dokumentu (podrzędnymi oknami MDI) IDE.

  DTE, `DTE` obiekt (rozszerzalność narzędzi programistycznych) to najbardziej górny punkt dostępu w modelu automatyzacji programu Visual Studio, który umożliwia programowe Automatyzowanie i rozszerzanie środowiska IDE.

  Okno narzędzia okna pomocy dynamicznej, które jest implementowane przez środowisko IDE i wyświetla listę słowa kluczowego Lookup lub tematy pomocy **F1** .

  Kod edytora (Class, CLSID) implementujący `DocView` . Implementuje również `DocData` , czy widok i separacja danych są obsługiwane.

  rozszerzenie funkcji, która modyfikuje, dostosowuje lub dodaje do środowiska IDE. Możesz tworzyć rozszerzenia przy użyciu modelu automatyzacji lub pakietów VSPackage.

  Edytor zewnętrzny edytor, który nie jest specyficzny dla środowiska IDE, takiego jak Microsoft Word. Został on zarejestrowany za pomocą własnych mechanizmów i może być używany poza IDE. Jeśli ten edytor może być osadzony, pojawia się w oknie w IDE. Jeśli nie można go osadzić, zostanie utworzone oddzielne okno najwyższego poziomu.

  Drzewo hierarchii węzłów, każdy węzeł skojarzony z zestawem właściwości.

  niezależny składnik najwyższego poziomu składnika, który korzysta z niemodalnego okna najwyższego poziomu i może działać efektywnie jako okno aplikacji autonomicznej, ale jest zaimplementowany jako obiekt w procesie. W związku z tym niezależnym składnikiem najwyższego poziomu musi koordynować modalność i usługi pętli komunikatów przy użyciu IDE. Obiekty wewnątrzprocesowe nie mają własnej pętli komunikatów.

  Dostawca informacji dostawca informacji jest modułem, który może wyszukiwać słowa kluczowe i zwracać listę tematów w postaci `IVsUserContextItem` obiektów. Aby podać elementy słowa kluczowego **F1** i Lookup dla dostawcy informacji, zarejestruj skompilowany plik pomocy (*. HxS*) z systemem. Tematy pomocy w tych plikach zawierają listę tematów wyświetlanych w oknie Pomoc dynamiczna i pokazują, czy użytkownik naciśnie klawisz **F1**.

  składnik w miejscu obiekt pakietu VSPackage, który implementuje `IOleInPlaceComponent` interfejs do zarządzania oknem, który jest wizualnie zawarty w oknie dokumentu należącym do IDE. Składniki w miejscu nie uczestniczą w standardowym menu OLE — scalanie; Zamiast tego integrują elementy interfejsu użytkownika z IDE.

  Istnieją dwa typy składników w miejscu: Hardwired składników w miejscu i kontrolek składników.

  Składniki w miejscu Hardwired mają menu, paski narzędzi i polecenia, które są ściśle zintegrowane z interfejsem użytkownika IDE, tak jakby były wbudowane bezpośrednio w IDE.

  Kontrolki składników nie mają żadnego z elementów interfejsu użytkownika zintegrowanych ze środowiskiem IDE; zamiast nich używają menu, poleceń i pasków narzędzi IDE. Na przykład pogrubienie może służyć do pogrubienia zaznaczonego wyrazu w kontrolce tekstu sformatowanego osadzonego w formularzu. Jednak formanty składników mogą zażądać wyświetlania dynamicznie instalowanych elementów interfejsu użytkownika specyficznych dla składników.

  Usługa językowa zestaw obiektów, które umożliwiają deweloperom pakietu VSPackage Implementowanie funkcji edytorów kodu języka komputera, takich jak oznaczanie tekstu i kolorowanie.

  Projekt projektu różne pliki używany do przechowywania otwartych plików, które nie są w żadnym projekcie. Lista elementów w tym projekcie nie jest utrwalona.

  Projekty projektu składają się z obiektów hierarchii lub obiektów COM, które implementują `IVsHierarchy` interfejs.

  Projektant lub Edytor specyficzny dla projektu Projektant, którego nie można używać niezależnie od typu projektu. Każdy projektant charakterystyczny dla projektu musi wprowadzić do rejestru informacje o fabryce edytora. IDE może utworzyć wystąpienie projektanta przy każdym otwarciu określonego typu pliku w określonym projekcie.

  okno typu projektu okno, które stale śledzi obecnie aktywną hierarchię projektu i element z globalnego kontekstu wyboru. Typ projektu — system Windows korzysta z `SVsTrackSelectionEx` usługi, aby ostrzec o zmianach i wyświetlić informacje zwrotne dla użytkownika. Eksplorator rozwiązań jest przykładem okna typu projektu.

  Okno Właściwości poprzednio przeglądarką właściwości.

  Projekt projektów opartych na odwołaniach, który nie wymaga plików dla projektu, musi znajdować się w tym samym katalogu. Zamiast tego odwołania do plików z innych niepowiązanych katalogów są przechowywane i obsługiwane przez sam projekt.

  Uruchamianie wewnętrznej struktury tabeli dokumentów, za pomocą której IDE utrzymuje listę wszystkich aktualnie otwartych dokumentów. Lista zawiera wszystkie otwarte dokumenty w pamięci, niezależnie od tego, czy dokumenty są obecnie edytowane. Dokument to każdy zapisany element, obejmujący procedury składowane otwarte w edytorze, pliki w projekcie lub główny plik projektu (na przykład *. vcproj).

  Dane kontekstu wyboru, które są częścią szczegółów każdego okna w IDE i są używane do śledzenia aktywnych wyborów. Kontekst wyboru składa się z:

- Wskaźnik do `IVsHierarchy` interfejsu hierarchii projektu

- Identyfikator elementu elementu projektu.

- Wskaźnik do `ISelectionContainer` interfejsu zapewniającego dostęp do właściwości aktywnych obiektów.

- Tablica wartości elementów.

  Obsługa kontraktu zestawu interfejsów COM, które znajdują się w pojedynczym obiekcie COM. Podczas tworzenia usługi identyfikowanej za pomocą identyfikatora GUID należy zdefiniować zestaw interfejsów COM, które wykonują usługę. Obiekty COM używają usług, aby komunikować się ze sobą.

  Grupa rozwiązań powiązanych projektów, których użytkownik pracuje.

  Projektant standardowy Projektant, który może być używany niezależnie od typu projektu. Wszyscy projektanci standardowi muszą wprowadzić informacje o fabryce edytora w rejestrze. IDE może utworzyć wystąpienie projektanta za każdym razem, gdy plik z określonym rozszerzeniem zostanie otwarty. Dane muszą być przechowywane w pliku.

  standardowy Edytor edytora, który może być używany niezależnie od określonego typu projektu. Takie edytory mają EditorFactories zarejestrowane w rejestrze. Umożliwia to środowisku IDE lokalizowanie i wywoływanie edytora.

  standardowy Edytor systemu operacyjnego osadzanie, które nie jest specyficzne dla programu Visual Studio. Jest ona zarejestrowana przy użyciu dobrze znanych kluczy Win32 (na przykład Eksplorator Win32 wie, jak wywołać). Jeśli taki Edytor może być osadzony, Edytor nadal pojawia się w jego miejscu w środowisku IDE. W przeciwnym razie dla takich edytorów zostanie utworzone oddzielne okno najwyższego poziomu.

  zbiór podkontekstu `IVsUserContext` obiekt połączony z zbiorem kontekstu. Obiekt zawiera słowa kluczowe wyszukiwania, słowa kluczowe **F1** i atrybuty wyboru w składniku IDE. Przykłady subcontext zawierają polecenie w oknie narzędzi lub słowo kluczowe w edytorze.

  Okno narzędzia listy zadań zaimplementowane przez środowisko IDE i wyświetla listę aktywnych zadań.

  Nazwa pospolita bufora tekstu dla obiektu `VSTextBuffer` .

  Nazwa pospolita widoku tekstu dla obiektu `VSTextView` .

  składnik najwyższego poziomu narzędzia, który działa jako niemodalne okno podręczne, koordynujące się ściśle z interfejsem użytkownika IDE. Podobnie jak zależne składniki najwyższego poziomu, składniki najwyższego poziomu narzędzia muszą również koordynują usługi w pętli modalnej i komunikatów z IDE.

  składnik najwyższego poziomu obiekt pakietu VSPackage, który zarządza niemodalnym oknem najwyższego poziomu zamiast w obszarze klienta okna IDE. Składniki najwyższego poziomu implementują `IOleComponent` interfejs, aby korzystać z usług pętli komunikatów, takich jak dostęp do czasu bezczynności.

  Interfejs użytkownika aktywny obiekt pakietu VSPackage, który jest widoczny i aktualnie ma fokus.

  Hierarchia interfejsu użytkownika obiektu COM, który implementuje `IVsUIHierarchy` interfejs, aby umożliwić wyświetlanie hierarchii. Okno Hierarchia interfejsu użytkownika implementuje `ISelectionContainer` interfejs, aby zaktualizować okno właściwości; inne okna typu projektu mogą używać tej implementacji, w razie potrzeby.

  VSCT tabelę poleceń programu Visual Studio. Plik. vsct zawiera informacje dotyczące umieszczania i zachowań menu, pasków narzędzi i poleceń w formacie XML.

  Pakietu VSPackage instalowalne oprogramowanie, które rozszerza środowisko IDE programu Visual Studio, dodając co najmniej jedną z następujących elementów: interfejs użytkownika, usługi, typy projektów lub Edytor/Projektant. Pakietu VSPackage składa się z obiektu COM, który implementuje `IVsPackage` interfejs i jeden lub więcej obiektów com implementujących inne interfejsy do obsługi wyboru i innych funkcji. Ponadto pakietu VSPackage ma określone wymagania dotyczące rejestracji.
