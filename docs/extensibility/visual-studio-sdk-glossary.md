---
title: Słownik zestawu SDK programu Visual Studio | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- glossary [Visual Studio SDK]
ms.assetid: b64d432b-c39b-4904-ad18-3c3218b6e3aa
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 8b036142e119157d04dcf971a4bbbba984394956
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53987787"
---
# <a name="visual-studio-sdk-glossary"></a>Słownik usługi Visual Studio SDK
W tym słowniku zawiera definicje dla terminów używanych w [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] dokumentacji.  
  
## <a name="terms"></a>Warunki  
 Dodatek  
 Aplikacja narzędziowa, sterownika lub innego oprogramowania dodanych do głównej aplikacji. W programie Visual Studio zintegrowane środowisko programistyczne (IDE) dodatek jest aplikacji na podstawie Automation, która rozszerza możliwości środowiska IDE.  
  
 model automatyzacji  
 Model automatyzacji, znane w poprzednich wersjach programu Visual Studio jako modelu rozszerzalności jest interfejs programowania, który zapewnia dostęp do podstawowych procedury tego dysku IDE. Dodatki, kreatory i makra używać obiektów w modelu automatyzacji, aby formant lub rozszerzanie funkcji środowiska IDE.  
  
 polecenie kontekstu interfejsu użytkownika  
 Skojarzenie identyfikatora GUID z widoczności poleceń interfejsu użytkownika lub element, takie jak pasek narzędzi. Polecenie kontekstu interfejsu użytkownika różni się od kontekst zaznaczenia w tym, że nie jest dołączona do okna.  
  
 Polecenie kontekstu interfejsu użytkownika mogą służyć do:  
  
- Identyfikator GUID należy przypisać do paska narzędzi, który pojawia się po aktywowaniu określonego okna.  
  
- Przypisz identyfikator GUID do sprawdzania dostępności polecenia bez konieczności ładowania lub uruchamiania pakietu VSPackage.  
  
- Przypisz GUID wpływa na aktywne powiązanie klucza.  
  
- Przypisz identyfikator GUID, aby włączyć rejestrowanie makra.  
  
- Przypisz identyfikator GUID, aby uaktywnić tryb debugowania lub można przełączać się między projektowania a tryb wykonywania w edytorze.  
  
  składnik  
  Fragment oprogramowania, które mogą być wykonane część funkcji aplikacji bez tej aplikacji, mających wszelkie istniejące informacje na temat wdrażania oprogramowania. Komunikacja między składnikiem i aplikacji odbywa się wyłącznie za pośrednictwem interfejsów styl OLE.  
  
  Menedżer składników  
  Usługa `SOleComponentManager`, który zapewnia interfejs niezwiązanych z użytkownikiem koordynacji składników usług dla najwyższego poziomu. `SOleComponentManager` Usługi implementuje `IOleComponentManager` interfejsu.  
  
  Składnik interfejsu użytkownika Menedżera  
  Usługa `SOleComponentUIManager`, zapewniającą usług koordynacji interfejsu użytkownika. `SOleComponentUIManager` Usługi implementuje `IOleComponentUIManager` i `IOleInPlaceComponentUIManager` interfejsów.  
  
  zbiór kontekstu  
  `IVsUserContext` Obiektu (obiekt COM) dołączone do składnika środowiska. Ten obiekt zawiera wyszukiwania słów kluczowych, **F1** słów kluczowych i atrybuty, które odnoszą się do składnika. Zbiory kontekstu wskaż również wszelkie zbiory kontekst podrzędny, które są powiązane z nimi.  
  
  dostwcy kontekstu  
  Składnik w IDE, do którego ma zbiór kontekstu skojarzone z nią. Takie składniki obejmują okna narzędzi, Edytor lub projekt hierarchii.  
  
  projektant  
  Interfejs programowania, który umożliwia użytkownikom zarządzanie elementów interfejsu użytkownika (formularze, przyciski i inne formanty).  
  
  DocData  
  Obiekt COM, zawieranie danych bazowych dokumentu w świecie, w których separacji dokument/widok (na przykład w przypadku edytora tekstu, to będzie bufor tekstowy podstawowych wszystkich widoków edytora tekstu). Jeśli ten obiekt nie podany element EditorFactory, są produkowane IDE, jeden w jej imieniu. Odpowiedzialność za ten obiekt jest zarządzanie funkcji trwałości danych i udostępniania semantyki dla wielu widoków to samo `DocData`. Jeśli `DocData` obiekt obsługuje `IOleCommandTarget` interfejsu, jest on zawarty w routingu poleceń UIShell.  
  
  DocObject  
  Technologia używana do obsługi interfejsu użytkownika w ramce udostępniane przez hosta. Dokładniej mówiąc, określenie to odnosi się do dowolnej osadzania, który obsługuje `IOleDocument` i powiązanych interfejsów. Ta technologia ma wiele potencjalnych aplikacji, takich jak szczegółowo opisuje implementacja modelu COM, dokumentów, okien narzędzi w języku Visual Basic 5.0, ActiveX projektantów w Visual Basic 6.0 i tak dalej.  
  
  dokument  
  Umożliwia odwoływanie się ogólną do dokumentu jako całości — zarówno `DocData` i `DocView`. Na przykład zawiera DocumentFrame `DocView`, ale zachowuje także odwołania do `DocData` do obsługi trwałości.  
  
  DocView  
  DocObject/Embedding/nagład, z którą użytkownik wchodzi w interakcję na wyświetlanie i manipulowanie bazowego `DocData`. Użytkownicy nie korzystają z separacji dokument/widok, który jest częścią `DocObject` projekt interfejsu. Użytkownicy używać całej DocObject do działania jako widok zamiast używania notacji bardziej abstrakcyjnego (i mniej formalny) w danych bazowych, nazywany `DocData`. `DocView` obiekty zawsze są osadzane z obiektami ramki dokumentu (oknami podrzędnymi MDI) środowiska IDE.  
  
  DTE  
  `DTE` Obiekt (rozszerzalność narzędzi rozwoju) jest punktem dostępu najważniejsze w modelu automatyzacji programu Visual Studio, dzięki czemu można programowo zautomatyzować i rozszerzyć środowisko IDE.  
  
  Dynamiczne okna Pomoc  
  Okna narzędzi, który jest implementowany przez środowisko IDE i wyświetla listę wyszukiwania słów kluczowych lub **F1** tematy Pomocy.  
  
  edytor  
  Kod (CLSID klasy), który implementuje `DocView`. Implementuje także `DocData` Jeśli rozdzielenie widoku i danych jest obsługiwana.  
  
  rozszerzenie  
  Funkcja, która modyfikuje, dostosowuje i dodaje do środowiska IDE. Możesz utworzyć rozszerzeń przy użyciu modelu automatyzacji lub pakietów VSPackage.  
  
  edytor zewnętrzny  
  Edytor, który nie jest specyficzne dla środowiska IDE, takiego jak Microsoft Word. Ona został zarejestrowany za pomocą swoje własne mechanizmy i może służyć poza IDE. Jeśli ten edytor może być osadzony, pojawia się w obrębie okna w IDE. Jeśli nie można osadzić, tworzona jest osobnym oknie najwyższego poziomu.  
  
  hierarchia  
  Drzewo węzłów, każdy węzeł skojarzone z zestawem właściwości.  
  
  niezależnie od najwyższego poziomu składnika  
  Składnik, który używa jest niemodalne okno dialogowe najwyższego poziomu może efektywnie działać jako okno aplikacji autonomicznej, ale jest implementowany jako obiekt w procesie. W związku z tym niezależne składnik najwyższego poziomu skoordynować modalności i usługi pętli komunikatów w środowisku IDE. W trakcie obiekty nie mają własne pętli komunikatów.  
  
  informacje o dostawcy  
  Dostawca informacji jest moduł, który można wyszukiwać słowa kluczowe i zwrócić listę tematów, w postaci `IVsUserContextItem` obiektów. Aby zapewnić **F1** i wyszukiwania słów kluczowych elementów dla dostawcy informacji, zarejestruj skompilowanego pliku pomocy (*. HxS*) w systemie. Tematy pomocy, w tych plikach zawierają listę tematów, wyświetlana w oknie Pomoc dynamiczna a czy użytkownik naciśnie **F1**.  
  
  składnik w miejscu  
  Obiekt pakietu VSPackage, który implementuje `IOleInPlaceComponent` interfejsu do zarządzania oknem, które wizualnie znajduje się w oknie dokumentu należące do środowiska IDE. Składniki w miejscu nie są używane w standardowych OLE-scalanie menu; Zamiast tego mogą zintegrować ich elementy interfejsu użytkownika IDE.  
  
  Istnieją dwa typy składników w miejscu: hardwired w miejscu składników i formantów składników.  
  
  Składniki w miejscu Hardwired ma menu, paski narzędzi i poleceń, które są ściśle zintegrowane interfejsu użytkownika IDE, stanowiący, jeśli zostały utworzone bezpośrednio w środowisku IDE.  
  
  Formanty składników nie ma swoje własne elementy interfejsu użytkownika, zintegrowane środowisko IDE; Zamiast tego użyć ich menu, poleceń i paski narzędzi IDE. Na przykład pogrubienie polecenie może służyć do pogrubienie zaznaczonego wyrazu w ramach kontrolki tekstu sformatowanego osadzone w formularzu. Jednak składnik kontrolki mogą poprosić o wyświetlane dynamicznie zainstalowanych elementów interfejsu użytkownika specyficznych dla składnika.  
  
  Usługa językowa  
  Zestaw obiektów, które umożliwia deweloperom pakietu VSPackage we wdrażaniu funkcji komputera edytory kodu języka, takich jak tekst znakowania i kolorowanie.  
  
  Projekt różne pliki  
  Projekt używany do domu otwartych plików, które nie znajdują się w każdym projekcie. Nie była utrzymywana, na liście elementów w tym projekcie.  
  
  projekt  
  Projekty są tworzone przez obiekty w hierarchii, lub obiektów COM, które implementują `IVsHierarchy` interfejsu.  
  
  specyficzne dla projektu projektancie lub edytorze  
  Projektant, którego nie można użyć niezależnie od typu projektu. Wszystkich projektantów specyficzne dla projektu, należy wprowadzić swoje informacje fabryka edytora w rejestrze. IDE następnie można utworzyć wystąpienie projektanta przy każdym otwarciu określonego typu pliku w określonym projekcie.  
  
  Okno typu projektu  
  Okno, które stale śledzi hierarchii aktualnie aktywnego projektu i elementu z kontekstu globalnego zaznaczenia. Użyj typu projektu windows `SVsTrackSelectionEx` usługę do wyzwalania alertu, zmian środowiska IDE i wyświetlić opinie do użytkownika. Eksplorator rozwiązań znajduje się przykład okna typu projektu.  
  
  Okno właściwości  
  Wcześniej przeglądarkę właściwości.  
  
  Projekty oparte na odwołanie  
  Projekt, który nie wymaga, aby pliki w projekcie, w tym samym katalogu. Zamiast tego odwołania do plików z innych katalogów niepowiązanych są przechowywane i obsługiwane przez samym projekcie.  
  
  Uruchamianie tabeli dokumentu  
  Struktury wewnętrznej za pomocą którego IDE utrzymuje listę wszystkich aktualnie otwarte dokumenty. Lista zawiera wszystkie otwarte dokumenty w pamięci, niezależnie od tego, czy dokumenty są obecnie edytowane. Dokument jest dowolny element, który jest zapisywana, w tym procedury składowane otwartych w edytorze, pliki w projekcie lub w pliku projektu głównego (na przykład plik *.vcproj).  
  
  Kontekst zaznaczenia  
  Dane, które jest częścią szczegóły każdego okna w IDE i jest używane do śledzenia aktywnego zaznaczenia. Kontekst zaznaczenia składa się z:  
  
- Wskaźnik do `IVsHierarchy` interfejsu hierarchii projektu  
  
- Identyfikator elementu elementu projektu.  
  
- Wskaźnik do `ISelectionContainer` interfejsu, zapewniając dostęp do właściwości dla obiektów active.  
  
- Tablica wartości elementu.  
  
  usługa  
  Kontrakt zestaw interfejsów COM, który znajduje się w jednym obiekcie COM. Podczas tworzenia usługi, który jest identyfikowany przez identyfikator GUID, należy zdefiniować zestaw interfejsów COM, który zajmuje się usługi. Obiekty COM za pomocą usług do komunikowania się ze sobą.  
  
  Rozwiązanie  
  Grupa powiązanych projektów, z którymi użytkownik pracuje.  
  
  Standardowa projektanta  
  Projektant, który może służyć jako niezależne od typu projektu. Wszystkie standardowe projektantów należy wprowadzić swoje informacje fabryka edytora w rejestrze. IDE następnie można utworzyć wystąpienie projektanta przy każdym otwarciu plików z określonym rozszerzeniem. Dane muszą zostać zachowane w pliku.  
  
  Edytor standardowy  
  Edytor, który może służyć jako niezależne od dowolnego określonego typu projektu. Takie edytorów EditorFactories zarejestrowany w rejestrze. Dzięki temu środowisko IDE do lokalizowania i wywoływanie edytora.  
  
  Edytor standardowy system operacyjny  
  Osadzanie nie dotyczące programu Visual Studio. Jest ona zarejestrowana przy użyciu dobrze znanych kluczy systemu Win32 (na przykład Eksploratora Win32 wie, jak wywołać). Jeśli takie edytora mogą być osadzone, Edytor wciąż pokazuje w jego miejsce w środowisku IDE. W przeciwnym razie oddzielne okno najwyższego poziomu jest tworzony dla takich edytorów.  
  
  kontekst podrzędny zbioru  
  `IVsUserContext` Obiekt powiązany pakiet z kontekstu. Obiekt przechowuje wyszukiwania słów kluczowych, **F1** słów kluczowych i atrybuty do wyboru w składniku IDE. Kontekst podrzędny przykładami polecenia w oknie narzędzia lub słowa kluczowego w edytorze.  
  
  Lista zadań  
  Okna narzędzi, który jest implementowany przez środowisko IDE i wyświetla listę aktywnych zadań.  
  
  Bufor tekstowy  
  Nazwa pospolita obiektu `VSTextBuffer`.  
  
  Widok tekstu  
  Nazwa pospolita obiektu `VSTextView`.  
  
  Narzędzie najwyższego poziomu składnika  
  Składnik, który działa jako okno podręczne niemodalne, ściśle koordynowanie przy użyciu interfejsu użytkownika IDE. Podobnie jak niezależnych składniki najwyższego poziomu składników najwyższego poziomu narzędzia również skoordynować modalności i usługi pętli komunikatów w środowisku IDE.  
  
  składnik najwyższego poziomu  
  Obiekt pakietu VSPackage, który zarządza niemodalne okno zamiast obszaru klienckiego okna środowiska IDE. Najwyższego poziomu składniki implementują `IOleComponent` interfejsu, aby móc korzystać z usługi pętli komunikatów, takich jak dostęp do czasu bezczynności.  
  
  Aktywne interfejsu użytkownika  
  Obiekt pakietu VSPackage, który jest widoczny i aktualnie jest ustawiony fokus.  
  
  Hierarchii interfejsu użytkownika  
  Obiekt COM, który implementuje `IVsUIHierarchy` interfejs umożliwia wyświetlanie hierarchii. Implementuje okno hierarchii interfejsu użytkownika `ISelectionContainer` współpracować w celu aktualizacji w oknie właściwości; innych typów projektów systemu windows można użyć tej implementacji, w razie potrzeby.  
  
  VSCT  
  Tabela poleceń programu Visual Studio. Pliku vsct zawiera informacje na temat umieszczania i zachowań, menu, paski narzędzi i poleceń w formacie XML.  
  
  Pakietu VSPackage  
  Do zainstalowania część oprogramowania, które rozszerza środowiska IDE programu Visual Studio, przyczyniając się co najmniej jeden z następujących elementów: interfejs użytkownika, usługi, typy projektów lub Projektant/Edytor. Pakietu VSPackage składa się z obiektu COM, który implementuje `IVsPackage` interfejsu i jeden lub więcej innych obiektów COM, które implementują inne interfejsy do obsługi zaznaczenia i inne funkcje. Ponadto pakietu VSPackage ma wymagania dotyczące określonej rejestracji.