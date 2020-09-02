---
title: Słownik SDK programu Visual Studio | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- glossary [Visual Studio SDK]
ms.assetid: b64d432b-c39b-4904-ad18-3c3218b6e3aa
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 8c189c4c9e06d224d7cef296a2c39e732cbc29f6
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "62538718"
---
# <a name="visual-studio-sdk-glossary"></a>Słownik zestawu Visual Studio SDK
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Ten słownik zawiera definicje terminów używanych w [!INCLUDE[vsipsdk](../includes/vsipsdk-md.md)] dokumentacji programu.  
  
## <a name="terms"></a>Terminologia  
 dodatek  
 Aplikacja narzędziowa, sterownik lub inne oprogramowanie dodane do aplikacji głównej. W zintegrowanym środowisku programistycznym (IDE) programu Visual Studio dodatek jest aplikacją opartą na automatyzacji, która rozszerza możliwości środowiska IDE.  
  
 model automatyzacji  
 Model automatyzacji, znany w poprzednich wersjach programu Visual Studio, jest interfejsem programowania, który zapewnia dostęp do podstawowych procedur, które są dyskami IDE. Dodatki, kreatory i makra używają obiektów w modelu automatyzacji do kontrolowania lub zwiększania funkcjonalności środowiska IDE.  
  
 kontekst interfejsu użytkownika polecenia  
 Skojarzenie identyfikatora GUID z widocznością polecenia interfejsu użytkownika lub elementu, takiego jak pasek narzędzi. Kontekst interfejsu użytkownika polecenia jest w przeciwieństwie do kontekstu wyboru w tym, że nie jest dołączony do okna.  
  
 Kontekst interfejsu użytkownika polecenia może służyć do:  
  
- Przypisz identyfikator GUID do paska narzędzi, który pojawia się po aktywowaniu określonego okna.  
  
- Przypisz identyfikator GUID do dostępności polecenia bez konieczności ładowania lub uruchamiania pakietu VSPackage.  
  
- Przypisz identyfikator GUID, aby miał wpływ na powiązanie z aktywnym kluczem.  
  
- Przypisz identyfikator GUID, aby włączyć rejestrowanie makr.  
  
- Przypisz identyfikator GUID w celu aktywowania trybu debugowania lub przełączania między trybem projektowania i uruchamiania w edytorze.  
  
  składnik  
  Część oprogramowania, która może być częścią funkcji aplikacji bez konieczności posiadania jakichkolwiek istniejących informacji o implementacji oprogramowania. Komunikacja między składnikiem a aplikacją odbywa się wyłącznie za pośrednictwem interfejsów stylów OLE.  
  
  Menedżer składników  
  Usługa, `SOleComponentManager` która zapewnia usługi koordynacji interfejsów innych niż użytkownika dla składników najwyższego poziomu. `SOleComponentManager`Usługa implementuje `IOleComponentManager` interfejs.  
  
  Menedżer interfejsu użytkownika składnika  
  Usługa, `SOleComponentUIManager` która zapewnia usługi koordynacji interfejsu użytkownika. `SOleComponentUIManager`Usługa implementuje `IOleComponentUIManager` `IOleInPlaceComponentUIManager` interfejsy i.  
  
  zbiór kontekstu  
  `IVsUserContext`Obiekt (COM Object) dołączony do składnika środowiska. Ten obiekt zawiera słowa kluczowe wyszukiwania, słowa kluczowe F1 i atrybuty powiązane ze składnikiem. Torby kontekstu wskazują także wszelkie połączone z nimi torby kontekstu.  
  
  Dostawca kontekstu  
  Składnik IDE, z którym jest skojarzony zbiór kontekstowy. Takie składniki obejmują okno narzędzi, Edytor lub hierarchię projektu.  
  
  projektant  
  Interfejs programowania, który umożliwia użytkownikom Manipulowanie elementami interfejsu użytkownika (formularzy, przycisków i innych kontrolek).  
  
  DocData  
  Obiekt COM, który hermetyzuje dane bazowe dokumentu na świecie, w którym istnieje separacja dokumentu/widoku (na przykład w przypadku edytora tekstu może to być bufor tekstowy odpowiadający wszystkim widokom edytora tekstu). Jeśli EditorFactory nie dostarcza tego obiektu, środowisko IDE wygeneruje je w jego imieniu. Zadaniem tego obiektu jest zarządzanie trwałośćmi danych i semantyką udostępniania dla wielu widoków w tym samym czasie `DocData` . Jeśli `DocData` obiekt obsługuje `IOleCommandTarget` interfejs, zostanie dołączony do routingu poleceń UIShell.  
  
  DocObject  
  Technologia używana do hostowania interfejsu użytkownika w obrębie ramki dostarczonej przez hosta. Dokładniej mówiąc, ten termin odnosi się do dowolnego osadzania, które obsługuje `IOleDocument` interfejsy i powiązane z nimi. Ta technologia ma wiele potencjalnych aplikacji, takich jak szczegóły implementacji dokumentów COM, okna narzędzi w Visual Basic 5,0, projektanci ActiveX w Visual Basic 6,0 itd.  
  
  dokument  
  Służy do ogólnego odwoływania się do dokumentu jako całości — zarówno do, jak `DocData` i `DocView` . Na przykład DocumentFrame zawiera a `DocView` , ale zachowuje także odwołanie do w `DocData` celu obsługi trwałości.  
  
  DocView  
  DocObject/osadzanie/WindowPane, za pomocą którego użytkownik może wyświetlać i manipulować podstawowym `DocData` . Należy pamiętać, że użytkownicy nie korzystają z separacji dokumentów i widoków, które są częścią `DocObject` projektu interfejsu. Użytkownicy wykorzystują cały DocObject do działania jako widok, zamiast korzystać z bardziej abstrakcyjnych (i mniej formalnych) koncepcji danych podstawowych znanych jako `DocData` . `DocView` obiekty są zawsze osadzone z obiektami ramki dokumentu (podrzędnymi oknami MDI) IDE.  
  
  DTE  
  `DTE`Obiekt (rozszerzalność narzędzi programistycznych) jest najwyższego poziomu punktu dostępu w modelu automatyzacji programu Visual Studio, który umożliwia programowe Automatyzowanie i rozszerzanie środowiska IDE.  
  
  Dynamiczne okno pomocy  
  Okno narzędzi, które jest implementowane przez środowisko IDE i wyświetla listę słowa kluczowego Lookup lub tematy pomocy F1.  
  
  edytor  
  Kod (Class, CLSID) implementujący `DocView` . Implementuje również `DocData` , czy separacja widoku/danych jest obsługiwana.  
  
  rozszerzenie  
  Funkcja, która modyfikuje, dostosowuje lub dodaje do IDE. Możesz tworzyć rozszerzenia przy użyciu modelu automatyzacji lub pakietów VSPackage.  
  
  Edytor zewnętrzny  
  Edytor, który nie jest specyficzny dla środowiska IDE, takiego jak Microsoft Word. Został on zarejestrowany za pomocą własnych mechanizmów i może być używany poza IDE. Jeśli ten edytor może być osadzony, pojawia się w oknie w IDE. Jeśli nie może być osadzony, zostanie utworzone oddzielne okno najwyższego poziomu.  
  
  hierarchia  
  Drzewo węzłów, każdy węzeł skojarzony z zestawem właściwości.  
  
  niezależny składnik najwyższego poziomu  
  Składnik, który korzysta z niemodalnego okna najwyższego poziomu i może działać efektywnie jako okno aplikacji autonomicznej, ale jest zaimplementowany jako obiekt w procesie. W związku z tym niezależnym składnikiem najwyższego poziomu musi koordynować modalność i usługi pętli komunikatów przy użyciu IDE. Obiekty wewnątrzprocesowe nie mają własnej pętli komunikatów.  
  
  Dostawca informacji  
  Dostawca informacji jest modułem, który może odszukać słowa kluczowe i zwrócić listę tematów w postaci `IVsUserContextItem` obiektów. Aby podać elementy słowa kluczowego F1 i Lookup dla dostawcy informacji, zarejestruj skompilowany plik pomocy (. HxS) z systemem. Tematy pomocy w tych plikach są używane do udostępniania listy tematów wyświetlanych w oknie Pomoc dynamiczna i pokazują, czy użytkownik naciśnie klawisz F1.  
  
  składnik w miejscu  
  Obiekt pakietu VSPackage, który implementuje `IOleInPlaceComponent` interfejs do zarządzania oknem, który jest wizualnie zawarty w oknie dokumentu należącym do IDE. Składniki w miejscu nie uczestniczą w standardowym menu OLE — scalanie; Zamiast tego integrują elementy interfejsu użytkownika z IDE.  
  
  Istnieją dwa typy składników w miejscu: Hardwired składników w miejscu i kontrolek składników.  
  
  Składniki w miejscu Hardwired mają menu, paski narzędzi i polecenia, które są ściśle zintegrowane z interfejsem użytkownika IDE, tak jakby były wbudowane bezpośrednio w IDE.  
  
  Formanty składników nie mają żadnego z elementów interfejsu użytkownika zintegrowanych ze środowiskiem IDE; zamiast nich używają menu, poleceń i pasków narzędzi IDE. Na przykład pogrubienie może służyć do pogrubienia zaznaczonego wyrazu w kontrolce tekstu sformatowanego osadzonego w formularzu. Jednak formanty składników mogą zażądać wyświetlania dynamicznie instalowanych elementów interfejsu użytkownika specyficznych dla składników.  
  
  Usługa języka  
  Zestaw obiektów, który umożliwia deweloperom pakietu VSPackage Implementowanie funkcji edytorów kodu języka komputera, takich jak oznaczanie tekstu i kolorowanie.  
  
  Projekt różnych plików  
  Projekt używany do przechowywania otwartych plików, które nie znajdują się w żadnym projekcie. Lista elementów w tym projekcie nie jest utrwalona.  
  
  projekt  
  Projekty składają się z obiektów hierarchii lub obiektów COM, które implementują `IVsHierarchy` interfejs.  
  
  Projektant lub Edytor specyficzny dla projektu  
  Projektant, którego nie można używać niezależnie od typu projektu. Każdy projektant charakterystyczny dla projektu musi wprowadzić do rejestru informacje o fabryce edytora. IDE może utworzyć wystąpienie projektanta przy każdym otwarciu określonego typu pliku w określonym projekcie.  
  
  okno typu projektu  
  Okno, które stale śledzi obecnie aktywną hierarchię projektu i element z globalnego kontekstu wyboru. Typ projektu — system Windows korzysta z `SVsTrackSelectionEx` usługi, aby ostrzec o zmianach i wyświetlić informacje zwrotne dla użytkownika. Eksplorator rozwiązań jest przykładem okna typu projektu.  
  
  Okno właściwości  
  Wcześniej przeglądarka właściwości.  
  
  projekty oparte na odwołaniach  
  Projekt, który nie wymaga plików dla projektu, musi znajdować się w tym samym katalogu. Zamiast tego odwołania do plików z innych niepowiązanych katalogów są przechowywane i obsługiwane przez sam projekt.  
  
  Uruchamianie tabeli dokumentu  
  Wewnętrzna struktura, za pomocą której IDE utrzymuje listę wszystkich aktualnie otwartych dokumentów. Ta lista zawiera wszystkie otwarte dokumenty w pamięci niezależnie od tego, czy dokumenty są obecnie edytowane. Dokument to każdy zapisany element, obejmujący procedury składowane otwarte w edytorze, pliki w projekcie lub główny plik projektu (na przykład *. vcproj).  
  
  Kontekst zaznaczenia  
  Dane, które są częścią szczegółów każdego okna w IDE i są używane do śledzenia aktywnych wyborów. Kontekst wyboru składa się z:  
  
- Wskaźnik do `IVsHierarchy` interfejsu hierarchii projektu  
  
- Identyfikator elementu elementu projektu.  
  
- Wskaźnik do `ISelectionContainer` interfejsu zapewniającego dostęp do właściwości aktywnych obiektów.  
  
- Tablica wartości elementów.  
  
  usługa  
  Kontrakt zestawu interfejsów COM, które znajdują się w pojedynczym obiekcie COM. Podczas tworzenia usługi identyfikowanej za pomocą identyfikatora GUID należy zdefiniować zestaw interfejsów COM, które wykonują usługę. Obiekty COM używają usług, aby komunikować się ze sobą.  
  
  Narzędzie  
  Grupa powiązanych projektów, z którymi użytkownik pracuje.  
  
  Projektant standardowy  
  Projektant, który może być używany niezależnie od typu projektu. Wszyscy projektanci standardowi muszą wprowadzić informacje o fabryce edytora w rejestrze. IDE może utworzyć wystąpienie projektanta za każdym razem, gdy plik z określonym rozszerzeniem zostanie otwarty. Dane muszą być przechowywane w pliku.  
  
  Edytor standardowy  
  Edytor, który może być używany niezależnie od określonego typu projektu. Takie edytory mają EditorFactories zarejestrowane w rejestrze. Umożliwia to środowisku IDE lokalizowanie i wywoływanie edytora.  
  
  standardowy Edytor systemu operacyjnego  
  Osadzanie, które nie jest specyficzne dla programu Visual Studio. Jest ona zarejestrowana przy użyciu dobrze znanych kluczy Win32 (na przykład Eksplorator Win32 wie, jak wywołać). Jeśli taki Edytor może być osadzony, Edytor nadal będzie widoczny w jego miejscu w środowisku IDE. W przeciwnym razie dla takich edytorów zostanie utworzone oddzielne okno najwyższego poziomu.  
  
  podzbiór kontekstu  
  `IVsUserContext`Obiekt połączony z zbiorem kontekstu. Ten obiekt zawiera słowa kluczowe wyszukiwania, słowa kluczowe F1 i atrybuty wyboru w składniku IDE. Przykłady subcontext zawierają polecenie w oknie narzędzi lub słowo kluczowe w edytorze.  
  
  Lista zadań  
  Okno narzędzi, które jest implementowane przez środowisko IDE i wyświetla listę aktywnych zadań.  
  
  bufor tekstu  
  Nazwa pospolita obiektu `VSTextBuffer` .  
  
  Widok tekstu  
  Nazwa pospolita obiektu `VSTextView` .  
  
  składnik najwyższego poziomu narzędzia  
  Składnik, który działa jako niemodalne okno podręczne, koordynując ściśle z interfejsem użytkownika IDE. Podobnie jak zależne składniki najwyższego poziomu, składniki najwyższego poziomu narzędzia muszą również koordynują usługi w pętli modalnej i komunikatów z IDE.  
  
  składnik najwyższego poziomu  
  Obiekt pakietu VSPackage, który zarządza niemodalnym oknem najwyższego poziomu zamiast w obszarze klienta okna IDE. Składniki najwyższego poziomu implementują `IOleComponent` interfejs, aby korzystać z usług pętli komunikatów, takich jak dostęp do czasu bezczynności.  
  
  Aktywny interfejs użytkownika  
  Obiekt pakietu VSPackage, który jest widoczny i aktualnie ma fokus.  
  
  Hierarchia interfejsu użytkownika  
  Obiekt COM, który implementuje `IVsUIHierarchy` interfejs, aby umożliwić wyświetlanie hierarchii. Okno Hierarchia interfejsu użytkownika implementuje `ISelectionContainer` interfejs, aby zaktualizować okno właściwości; inne okna typu projektu mogą używać tej implementacji, w razie potrzeby.  
  
  VSCT  
  Tabela poleceń programu Visual Studio. Plik. vsct zawiera informacje dotyczące umieszczania i zachowań menu, pasków narzędzi i poleceń w formacie XML.  
  
  Pakietu VSPackage  
  Instalowalne oprogramowanie, które rozszerza środowisko IDE programu Visual Studio przez Współtworzenie co najmniej jednego z następujących elementów: interfejs użytkownika, usługi, typy projektów lub Edytor/Projektant. Pakietu VSPackage składa się z obiektu COM, który implementuje `IVsPackage` interfejs i jeden lub więcej obiektów com implementujących inne interfejsy do obsługi wyboru i innych funkcji. Ponadto pakietu VSPackage ma określone wymagania dotyczące rejestracji.
