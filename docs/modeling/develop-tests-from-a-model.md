---
title: Opracowywanie testów na podstawie modelu
description: Dowiedz się, jak używać wymagań i modeli architektonicznych do organizowania testów systemu i jego składników.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- tests and requirements
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: dadffd0a2950d55145b24d3172564eb572f98d70
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/19/2021
ms.locfileid: "112389153"
---
# <a name="develop-tests-from-a-model"></a>Opracowywanie testów na podstawie modelu
Wymagania i modele architektoniczne ułatwiają organizowanie testów systemu i jego składników. Takie rozwiązanie pomaga w przetestowaniu wymagań, które są ważne dla użytkowników i innych uczestników projektu, oraz pomaga szybko aktualizować testy po zmianie wymagań. Jeśli używasz [!INCLUDE[TCMext](../misc/includes/tcmext_md.md)] funkcji , możesz również zachować połączenia między modelami i testami.

 Aby sprawdzić, które wersje usługi Visual Studio obsługują te funkcje, zobacz Obsługa wersji dla architektury [i narzędzi do modelowania.](../modeling/analyze-and-model-your-architecture.md#VersionSupport)

## <a name="system-and-subsystem-testing"></a>Testowanie systemu i podsystemu
 *Testowanie systemu,* nazywane również *testowaniem akceptacyjną,* oznacza testowanie, czy potrzeby użytkowników zostały spełnione. Takie testy dotyczą widocznego na zewnątrz zachowania systemu, a nie projektu wewnętrznego.

 Testy systemu są bardzo przydatne podczas rozszerzania lub przeprojektowania systemu. Pomagają one uniknąć wprowadzania usterek podczas zmiany kodu.

 Podczas planowania zmiany lub rozszerzenia systemu warto rozpocząć od zestawu testów systemowych, które są uruchamiane w istniejącym systemie. Następnie możesz rozszerzyć lub dostosować testy, aby przetestować nowe wymagania, wprowadzić zmiany w kodzie i ponownie uruchomić kompletny zestaw testów.

 Podczas opracowywania nowego systemu można rozpocząć tworzenie testów zaraz po rozpoczęciu opracowywania. Definiując testy przed opracowaniem poszczególnych funkcji, można przechwytywać dyskusje dotyczące wymagań w bardzo konkretny sposób.

 Testowanie podsystemu stosuje te same zasady do głównych składników systemu. Każdy składnik jest testowany oddzielnie od innych składników. Testy podsystemu koncentrują się na zachowaniu widocznym w interfejsach użytkownika składnika lub interfejsie API.

## <a name="deriving-system-tests-from-a-requirements-model"></a>Wyprowadzanie testów systemowych z modelu wymagań
 Można utworzyć i zachować relację między testami systemowymi i modelem wymagań. Aby ustanowić tę relację, należy napisać testy, które odpowiadają głównym elementom modelu wymagań. Visual Studio pomaga w utrzymaniu tej relacji, umożliwiając tworzenie połączeń między testami i częściami modelu. Aby uzyskać więcej informacji na temat modeli wymagań, zobacz [Model user requirements (Wymagania użytkownika modelu).](../modeling/model-user-requirements.md)

### <a name="write-tests-for-each-use-case"></a>Pisanie testów dla każdego przypadku użycia
 Jeśli używasz funkcji , możesz utworzyć grupę testów dla każdego przypadku użycia zdefiniowanego [!INCLUDE[TCMext](../misc/includes/tcmext_md.md)] w modelu wymagań. Jeśli na przykład masz przypadek użycia Zamów jedzenie, który obejmuje tworzenie zamówienia i dodawanie elementu do zamówienia, możesz utworzyć testy zarówno dla ogólnego, jak i bardziej szczegółowego z tych przypadków użycia.

 Poniższe wskazówki mogą być przydatne:

- Każdy przypadek użycia powinien mieć kilka testów dla głównych ścieżek i wyjątkowe wyniki.

- Opisujący przypadek użycia w modelu wymagań, ważniejsze jest zdefiniowanie jego postkondycji, czyli celu, który zostanie osiągnięty, niż szczegółowe opisanie procedur, które użytkownik stosuje w celu osiągnięcia tego celu. Na przykład po zamówieniu zamówienia na jedzenie może być to, że restauracji przygotowuje jedzenie dla klienta i że klient zapłacił. Postcondition to kryterium, które powinny zostać zweryfikowane przez testy.

- Oddzielne testy należy opierać na oddzielnych klauzulach postcondition. Na przykład utwórz oddzielne testy w celu powiadomienia restauracji o zamówieniu i w celu podjęcia płatności od klienta. To oddzielenie ma następujące zalety:

  - Zmiany różnych aspektów wymagań często zachodzą niezależnie. Rozdzielenie testów na różne aspekty w ten sposób ułatwia aktualizowanie testów w przypadku zmiany wymagań.

  - Jeśli plan rozwoju implementuje jeden aspekt przypadku użycia przed innym, możesz włączyć testy oddzielnie w trakcie opracowywania.

- Podczas projektowania testów należy oddzielić wybór danych testowych od kodu lub skryptu, który określa, czy postcondition został osiągnięty. Na przykład test prostej funkcji arytmetycznej może być: Dane wejściowe 4; Sprawdź, czy dane wyjściowe to 2. Zamiast tego zaprojektuj skrypt w następujący sposób: Wybierz dane wejściowe; Pomnóż dane wyjściowe samodzielnie i sprawdź, czy wynik jest oryginalnymi wejściami. Ten styl umożliwia zmianę danych wejściowych testu bez zmiany głównej treści testu.

#### <a name="linking-tests-to-use-cases"></a>Łączenie testów z przypadkami użycia
 Jeśli używasz programu do projektowania i uruchamiania testów, możesz zorganizować testy w ramach wymagań, przypadków użycia lub elementów roboczych [!INCLUDE[TCMlong](../modeling/includes/tcmlong_md.md)] historii użytkownika. Te elementy robocze można połączyć w celu zastosowania przypadków użycia w modelu. Dzięki temu można szybko śledzić zmiany wymagań w testach oraz śledzić postęp każdego przypadku użycia.

###### <a name="to-link-tests-to-a-use-case"></a>Aby połączyć testy z przypadekem użycia

1. W [!INCLUDE[TCMlong](../modeling/includes/tcmlong_md.md)] programie utwórz wymaganie i utwórz na nim zestaw testów.

    Wymagane jest utworzenie elementu roboczego w programie [!INCLUDE[vstsTfsShort](../modeling/includes/vststfsshort_md.md)] . Może to być element pracy User Story, Requirement lub Use Case (Przypadek użycia) w zależności od szablonu procesu używanego w projekcie z programem Team Foundation. Aby uzyskać więcej informacji, zobacz About Agile tools and Agile project management (Informacje o [narzędziach Agile i zarządzaniu projektami Agile).](/azure/devops/boards/backlogs/backlogs-overview?view=vsts&preserve-view=true)

2. Połącz element pracy wymagania z co najmniej jednym przypadkiem użycia w modelu.

    Na diagramie przypadków użycia kliknij prawym przyciskiem myszy przypadek użycia, a następnie kliknij **polecenie Połącz z elementem pracy.**

3. Dodaj do zestawu testów przypadki testowe, które weryfikują przypadki użycia.

   Zazwyczaj każdy artykuł użytkownika lub element pracy dotyczący wymagań będzie łączyć się z kilkoma przypadkami użycia w modelu, a każdy przypadek użycia będzie łączyć się z kilkoma artykułami użytkownika lub wymaganiami. Jest to spowodowane tym, że każda historia użytkownika lub wymaganie obejmuje zestaw zadań, które opracowywuje kilka przypadków użycia. Na przykład we wczesnej iteracji projektu możesz opracowywać podstawowe informacje o użytkowniku, w których klient może wybierać elementy z katalogu i je dostarczać. W późniejszej iteracji może się okazać, że użytkownik płaci podczas realizacji zamówienia, a dostawca otrzymuje pieniądze po wysłaniem towarów.  Każda historia dodaje klauzulę do postcondition przypadku użycia Order Goods.

   Możesz utworzyć oddzielne linki od wymagań do klauzul postcondition, pisząc te klauzule w oddzielnych komentarzach na diagramie przypadków użycia. Możesz połączyć każdy komentarz z wymaganym elementem pracy i połączyć komentarz z przypadekem użycia na diagramie.

### <a name="base-tests-on-the-requirements-types"></a>Testy podstawowe typów wymagań
 Typy modelu wymagań, czyli klasy, interfejsy i wyliczenia, opisują koncepcje i relacje pod względem sposobu, w jaki użytkownicy myślą o swojej firmie i komunikują się z nimi. Wyklucza typy, które dotyczą tylko wewnętrznego projektu systemu.

 Zaprojektuj testy pod kątem tych typów wymagań. Dzięki temu można mieć pewność, że w przypadku omówienia zmian wymagań można łatwo powiązać zmiany z niezbędnymi zmianami w testach. Umożliwia ona omawianie testów i ich zamierzonych wyników bezpośrednio z użytkownikami i innymi uczestnikami projektu. Oznacza to, że potrzeby użytkowników mogą być utrzymywane poza procesem projektowania i uniknąć przypadkowego projektowania testów wokół możliwych wad projektu.

 W przypadku testów ręcznych ta praktyka obejmuje spełnianie słownictwa modelu wymagań w skryptach testowych. W przypadku testów automatycznych ta praktyka obejmuje użycie diagramów klas wymagań jako podstawy dla kodu testowego oraz utworzenie funkcji accessor i updater w celu połączenia modelu wymagań z kodem.

 Na przykład model wymagań może zawierać typy Menu, Element menu, Kolejność i skojarzenia między nimi. Ten model reprezentuje informacje, które są przechowywane i zajmuje się nim system zamawiania potraw, ale nie reprezentuje złożonej części jego implementacji. W systemie operacyjnym może być kilka różnych realizacji każdego typu, w bazach danych, w interfejsach użytkownika i interfejsach API. W systemie rozproszonym może być kilka wariantów każdego wystąpienia przechowywanych w różnych częściach systemu w tym samym czasie.

 Aby przetestować przypadek użycia, taki jak Dodawanie elementu do zamówienia, metoda testowa może zawierać kod podobny do następującego:

```
Order order = ... ; // set up an order
// Store prior state:
int countBefore = order.MenuItems.Count;
// Perform use case:
MenuItem chosenItem = ...; // choose an item
AddItemToOrder (chosenItem, order);
// Verify part of postcondition:
int countAfter = order.MenuItems.Count;
Assert (countAfter == countBefore = 1);
```

 Zwróć uwagę, że ta metoda testowa używa klas modelu wymagań. Skojarzenia i atrybuty są realizowane jako właściwości .NET.

 Aby to działało, właściwości klas muszą być zdefiniowane jako funkcje tylko do odczytu lub obiekty dostępu, które mają dostęp do systemu w celu pobrania informacji o bieżącym stanie. Metody symulują przypadki użycia, takie jak AddItemToOrder, muszą prowadzić system za pośrednictwem interfejsu API lub warstwy poniżej interfejsu użytkownika. Konstruktory obiektów testowych, takich jak Order i MenuItem, muszą również napędzać system do tworzenia odpowiednich elementów wewnątrz systemu.

 Wiele z nich będzie już dostępnych za pośrednictwem normalnego interfejsu API aplikacji. Jednak w celu włączenia testów może być konieczne napisane kilka dodatkowych funkcji. Te dodatkowe metody dostępu i aktuaktory są czasami nazywane "instrumentacją testów". Ponieważ są one zależne od wewnętrznego projektu systemu, to deweloperzy systemu są odpowiedzialni za ich dostarczenie, podczas gdy testerzy piszą kod testów pod względem modelu wymagań.

 Podczas pisania testów automatycznych można użyć testów ogólnych do opakowywania metody dostępu i aktualizujące.

### <a name="tests-for-business-rules"></a>Testy Business Rules
 Niektóre wymagania nie są bezpośrednio związane z żadnym jednym przypadekem użycia. Na przykład firma DinnerNow umożliwia klientom wybór spośród wielu menu, ale wymaga, aby w każdym zamówieniu wszystkie wybrane elementy pochodziły z jednego menu. Tę regułę biznesową można wyrazić jako niezmienne skojarzenia między zamówieniami, menu i elementami w modelu klasy wymagań.

 Niezmienna reguła tego rodzaju zarządza nie tylko wszystkimi obecnie zdefiniowanymi przypadkami użycia, ale także wszystkimi innymi przypadkami użycia, które zostaną zdefiniowane później. W związku z tym warto napisać go niezależnie od każdego przypadku użycia i przetestować niezależnie od przypadków użycia.

## <a name="deriving-subsystem-tests-from-models"></a>Wyprowadzanie testów podsystemu z modeli
 W projekcie wysokiego poziomu dużego systemu można zidentyfikować składniki lub podsystemy. Reprezentują one części, które można oddzielnie zaprojektować, znajdują się na różnych komputerach lub są modułami wielokrotnego użytku, które można ponownie pokomunikować na wiele sposobów.

 Do każdego składnika można zastosować te same zasady, które są stosowane w przypadku kompletnego systemu. W dużym projekcie każdy składnik może mieć własny model wymagań. W mniejszych projektach można utworzyć model architektury lub projekt wysokiego poziomu, aby pokazać główne składniki i ich interakcje. Aby uzyskać więcej informacji, zobacz [Model your app's architecture (Modelowanie architektury aplikacji).](../modeling/model-your-app-s-architecture.md)

 W obu przypadkach można ustanowić relację między elementami modelu i testami podsystemu w taki sam sposób, jak między modelem wymagań a testami systemowymi.

### <a name="isolate-components-with-provided-and-required-interfaces"></a>Izolowanie składników za pomocą interfejsów dostarczanych i wymaganych
 Warto zidentyfikować wszystkie zależności, które składnik ma w innych częściach systemu lub usług zewnętrznych, i reprezentować je jako wymagane interfejsy. To ćwiczenie zwykle prowadzi do pewnego przeprojektowania, który pozostawia składnik znacznie bardziej oddzielony i łatwo oddzielony od pozostałej części projektu.

 Zaletą tego oddzielania jest to, że składnik może być wykonywany w celu testowania przez zastąpienie makietą obiektów usług, których zwykle używa. Są to składniki, które są ustawione na potrzeby testowania. Makietowy składnik udostępnia interfejs wymagany przez składnik, który odpowiada na zapytania przy użyciu symulowanych danych. Makiety składników stanowią część pełnego zestawu testów, który można połączyć ze wszystkimi interfejsami składnika.

 Zaletą testowania makiety jest to, że można opracować składnik, podczas gdy inne składniki, których usługi będą z niego korzystać, są nadal w trakcie opracowywania.

## <a name="maintain-the-relationships-between-tests-and-model"></a>Utrzymywanie relacji między testami i modelem
 W typowym projekcie, który wykonuje iterację co kilka tygodni, przegląd wymagań jest przeprowadzany blisko początku każdej iteracji. Na spotkaniu omówiono funkcje, które mają zostać dostarczone w następnej iteracji. Model wymagań może służyć do omówienia pojęć, scenariuszy i sekwencji akcji, które zostaną opracowane. Interesariusze biznesowi ustawiają priorytety, deweloperzy szacują, a testerzy zapewniają poprawne przechwycenie oczekiwanego zachowania każdej funkcji.

 Pisanie testów jest najskuteczniejszym sposobem definiowania wymagania, a także efektywnym sposobem zapewnienia, że osoba ma jasne zrozumienie, co jest wymagane. Jednak chociaż pisanie testów trwa zbyt długo podczas warsztatów specyfikacji, tworzenie modeli może być wykonywane znacznie szybciej.

 Z punktu widzenia testowania model wymagań może być widoczny jako skrócony model testów. Dlatego ważne jest zachowanie relacji między testami i modelem w całym projekcie.

## <a name="attaching-test-cases-to-model-elements"></a><a name="Attaching"></a> Dołączanie przypadków testowych do elementów modelu
 Jeśli projekt używa [!INCLUDE[TCMlong](../modeling/includes/tcmlong_md.md)] interfejsu , możesz połączyć testy z elementami w modelu. Dzięki temu można szybko znaleźć testy, na które ma wpływ zmiana wymagań, i ułatwia śledzenie zakresu, w jakim został zrealizowany wymóg.

 Testy można połączyć ze wszystkimi rodzajami elementów. Oto kilka przykładów:

- Połącz przypadek użycia z testami, które go przećwiczyć.

- Zapisz klauzule postcondition (celu) przypadku użycia w komentarzach połączonych z przypadekem użycia, a następnie połącz testy z każdym komentarzem.

- Napisz niezmienne reguły w komentarzach na diagramach klas lub diagramach aktywności i połącz je z testami.

- Łączenie testów z diagramem aktywności lub z poszczególnymi działaniami.

- Połącz zestaw testów ze składnikiem lub podsystemem, który testuje.

#### <a name="to-link-tests-to-a-model-element-or-relationship"></a>Aby połączyć testy z elementem modelu lub relacją

1. W [!INCLUDE[TCMlong](../modeling/includes/tcmlong_md.md)] programie utwórz wymaganie i utwórz na nim zestaw testów.

    Wymagane jest utworzenie elementu roboczego w programie [!INCLUDE[vstsTfsShort](../modeling/includes/vststfsshort_md.md)] . Może to być element pracy User Story, Requirement lub Use Case (Przypadek użycia) w zależności od szablonu procesu używanego w projekcie z programem Team Foundation. Aby uzyskać więcej informacji, zobacz About Agile tools and Agile project management (Informacje o [narzędziach Agile i zarządzaniu projektami Agile).](/azure/devops/boards/backlogs/backlogs-overview?view=vsts&preserve-view=true)

2. Połącz element pracy wymagania z co najmniej jednym elementem w modelu.

    Na diagramie modelowania kliknij prawym przyciskiem myszy element, komentarz lub relację, a następnie kliknij polecenie **Połącz z elementem pracy.**

3. Dodaj do zestawu testów przypadki testowe, które weryfikują wymaganie wyrażone w elemencie modelu.

## <a name="see-also"></a>Zobacz też

- [Tworzenie modeli aplikacji](../modeling/create-models-for-your-app.md)
- [Wymagania modelu użytkownika](../modeling/model-user-requirements.md)
- [Modelowanie architektury aplikacji](../modeling/model-your-app-s-architecture.md)
- [Analizowanie i modelowanie architektury](../modeling/analyze-and-model-your-architecture.md)
