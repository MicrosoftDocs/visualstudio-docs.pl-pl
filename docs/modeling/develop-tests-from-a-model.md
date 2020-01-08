---
title: Opracowywanie testów na podstawie modelu
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- tests and requirements
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2981d510b5f56b89a2cb68d1a6bee93222d71b3b
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/01/2020
ms.locfileid: "75596661"
---
# <a name="develop-tests-from-a-model"></a>Opracowywanie testów na podstawie modelu
Aby ułatwić organizowanie testów systemu i jego składników, można użyć wymagań i modeli architektonicznych. Dzięki temu można sprawdzić wymagania, które są ważne dla użytkowników i innych uczestników projektu, oraz ułatwić szybkie aktualizowanie testów w przypadku zmiany wymagań. Jeśli używasz [!INCLUDE[TCMext](../misc/includes/tcmext_md.md)], możesz również zachować linki między modelami i testami.

 Aby sprawdzić, które wersje programu Visual Studio obsługują te funkcje, zobacz [Obsługa wersji dla narzędzi architektury i modelowania](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

## <a name="system-and-subsystem-testing"></a>Testowanie systemu i podsystemu
 *Testowanie systemu,* znane także jako *testowanie akceptacji*, oznacza, że są spełnione potrzeby użytkowników. Takie testy są związane z zewnętrznym zachowaniem systemu, a nie projektem wewnętrznym.

 Testy systemowe są bardzo cenne podczas rozszerzania lub ponownego projektowania systemu. Pozwala to uniknąć wprowadzania usterek podczas zmiany kodu.

 Jeśli planujesz zmianę lub rozszerzenie systemu, warto zacząć od zestawu testów systemu, które są uruchamiane w istniejącym systemie. Następnie można zwiększyć lub dostosować testy, aby przetestować nowe wymagania, wprowadzić zmiany w kodzie i ponownie uruchomić kompletny zestaw testów.

 Podczas tworzenia nowego systemu możesz rozpocząć tworzenie testów zaraz po rozpoczęciu opracowywania. Definiując testy przed rozpoczęciem opracowywania każdej funkcji, można przechwycić dyskusje dotyczące wymagań w bardzo konkretny sposób.

 Testowanie podsystemu stosuje te same zasady do głównych składników systemu. Każdy składnik jest testowany niezależnie od innych składników. W podsystemie testy są skoncentrowane na zachowaniu widocznym w interfejsach użytkownika lub interfejsie API składnika.

## <a name="deriving-system-tests-from-a-requirements-model"></a>Wyprowadzanie testów systemowych z modelu wymagań
 Można tworzyć i obsługiwać relacje między testami systemowymi i modelem wymagań. Aby ustanowić tę relację, należy napisać testy, które odpowiadają głównym elementom modelu wymagań. Program Visual Studio pomaga zachować tę relację, umożliwiając tworzenie linków między testami i częściami modelu. Aby uzyskać więcej informacji na temat modeli wymagań, zobacz [wymagania dotyczące modelu użytkownika](../modeling/model-user-requirements.md).

### <a name="write-tests-for-each-use-case"></a>Testy zapisu dla każdego przypadku użycia
 Jeśli używasz [!INCLUDE[TCMext](../misc/includes/tcmext_md.md)], możesz utworzyć grupę testów dla każdego przypadku użycia zdefiniowanego w modelu wymagań. Na przykład jeśli masz posiłek na przypadek użycia, który obejmuje tworzenie zamówienia i Dodawanie elementu do zamówienia, możesz utworzyć testy dla całości i bardziej szczegółowych informacji o tych przypadkach użycia.

 Te wskazówki mogą być przydatne:

- Każdy przypadek użycia powinien mieć kilka testów, dla ścieżek głównych i wyjątkowe wyniki.

- Podczas opisywania przypadku użycia w modelu wymagań jest bardziej ważne, aby zdefiniować jego błąd warunku końcowego, czyli cel, który został osiągnięty, niż szczegółowo opisać procedury, które użytkownik może wykonać w celu osiągnięcia celu. Na przykład błąd warunku końcowego w kolejności postanowień może być, że restauracja przeniesie posiłk dla klienta i zapłacił klientowi. Błąd warunku końcowego to kryterium, aby testy były weryfikowane.

- Podstawowe testy na oddzielnych klauzulach błąd warunku końcowego. Na przykład można utworzyć osobne testy do powiadamiania restauracji o zamówieniach, a w przypadku dokonywania płatności od klienta. Ten rozdział ma następujące zalety:

  - Zmiany w różnych aspektach wymagań często występują niezależnie. Oddzielając testy do różnych aspektów w ten sposób, można ułatwić aktualizowanie testów w przypadku zmiany wymagań.

  - Jeśli plan rozwoju implementuje jeden aspekt przypadku użycia przed innym, można włączyć testy oddzielnie jako postęp opracowywania.

- Podczas projektowania testów należy oddzielić wybór danych testowych od kodu lub skryptu, który określa, czy błąd warunku końcowego został osiągnięty. Przykładowo można testować prostą funkcję arytmetyczną: dane wejściowe 4; Sprawdź, czy dane wyjściowe to 2. Zamiast tego Zaprojektuj skrypt jako: Wybierz dane wejściowe; Pomnóż dane wyjściowe przez siebie i sprawdź, czy wynik jest oryginalnymi danymi wejściowymi. Ten styl umożliwia różnicowanie danych wejściowych testów bez zmiany głównej treści testu.

#### <a name="linking-tests-to-use-cases"></a>Łączenie testów z przypadkami użycia
 Jeśli używasz [!INCLUDE[TCMlong](../modeling/includes/tcmlong_md.md)] do projektowania i uruchamiania testów, możesz organizować testy w obszarze wymagania, przypadek użycia lub elementy robocze scenariusza użytkownika. Można połączyć te elementy robocze z przypadkami użycia w modelu. Dzięki temu można szybko śledzić wymagania zmian w testach i pomóc śledzić postęp każdego przypadku użycia.

###### <a name="to-link-tests-to-a-use-case"></a>Aby połączyć testy z przypadkiem użycia

1. W [!INCLUDE[TCMlong](../modeling/includes/tcmlong_md.md)]Utwórz wymaganie i podstawowy zestaw testów.

    To wymaganie tworzone jest elementem roboczym w [!INCLUDE[vstsTfsShort](../modeling/includes/vststfsshort_md.md)]. Może to być scenariusz użytkownika, wymaganie lub element roboczy przypadku użycia, w zależności od szablonu procesu używanego przez projekt z programem Team Foundation. Aby uzyskać więcej informacji, zobacz [Informacje o narzędziach Agile i zarządzaniu projektami Agile](/azure/devops/boards/backlogs/backlogs-overview?view=vsts).

2. Połącz element roboczy wymaganie z co najmniej jednym przypadkiem użycia w modelu.

    W diagramie przypadku użycia kliknij prawym przyciskiem myszy przypadek użycia, a następnie kliknij pozycję **Połącz z elementem roboczym**.

3. Dodaj do zestawu testów, przypadków testowych, które weryfikują przypadki użycia.

   Zwykle każdy scenariusz użytkownika lub element roboczy wymagania będzie łączyć się z kilkoma przypadkami użycia w modelu, a każdy przypadek użycia będzie łączyć się z kilkoma scenariuszami lub wymaganiami użytkownika. Wynika to z faktu, że każdy scenariusz użytkownika lub wymóg obejmuje zestaw zadań, które opracowują kilka przypadków użycia. Na przykład we wczesnej iteracji projektu można opracowywać podstawową historię użytkownika, w której klient może wybrać elementy z katalogu i dostarczyć je. W późniejszej iteracji historia może polegać na tym, że użytkownik płaci przy wypełnianiu zamówienia, a Dostawca otrzymuje pieniądze po wysłaniu towarów.  Każda historia dodaje klauzulę do błąd warunku końcowego przypadku użycia zamówienia towarów.

   Można utworzyć oddzielne linki od wymagań do klauzul błąd warunku końcowego, pisząc te klauzule w osobnych komentarzach na diagramie przypadków użycia. Można połączyć każdy komentarz z elementem roboczym wymagania i połączyć komentarz z przypadkiem użycia na diagramie.

### <a name="base-tests-on-the-requirements-types"></a>Podstawowe testy dotyczące typów wymagań
 Typy, czyli klasy, interfejsy i wyliczenia, modelu wymagań opisują koncepcje i relacje w kontekście sposobu, w jaki użytkownicy uważają i komunikują się z firmą. Wyklucza on tylko te typy, które są objęte wewnętrznym projektem systemu.

 Zaprojektuj testy pod warunkiem tych typów wymagań. Takie rozwiązanie pomaga zapewnić, że w przypadku omówienia zmian w wymaganiach można łatwo powiązać zmiany w koniecznych zmianach w testach. Umożliwia to omawianie testów i ich zamierzonych wyników bezpośrednio z użytkownikami końcowymi i innymi uczestnikami. Oznacza to, że potrzeby użytkowników mogą być utrzymywane poza procesem tworzenia i pozwala uniknąć niezamierzonego projektu testów wokół możliwych wad w projekcie.

 W przypadku ręcznych testów ta metoda obejmuje przestrzeganie słownictwa modelu wymagań w skryptach testowych. W przypadku testów automatycznych to rozwiązanie obejmuje użycie diagramów klas wymagań jako podstawy dla kodu testowego, a także utworzenie funkcji akcesora i Aktualizator w celu połączenia modelu wymagań z kodem.

 Na przykład model wymagań może zawierać menu typy, element menu, kolejność i skojarzenia między nimi. Ten model reprezentuje informacje przechowywane i rozpatrywane przez system porządkowania posiłków, ale nie reprezentuje złożoności jego implementacji. W systemie operacyjnym może istnieć kilka różnych sposobów realizacji poszczególnych typów, w bazach danych, interfejs użytkownika i interfejsy API. W systemie rozproszonym może istnieć kilka wariantów każdego wystąpienia przechowywanych w różnych częściach systemu w tym samym czasie.

 Aby przetestować przypadek użycia, taki jak dodanie elementu do zamówienia, metoda testowa może zawierać kod podobny do tego:

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

 Należy zauważyć, że ta metoda testowa używa klas modelu wymagań. Skojarzenia i atrybuty są prawdziwe jako właściwości platformy .NET.

 Aby to zrobić, właściwości klas muszą być zdefiniowane jako funkcje tylko do odczytu lub metody dostępu, które uzyskują dostęp do systemu w celu pobrania informacji o jego bieżącym stanie. Metody symulowania przypadków użycia, takie jak AddItemToOrder, muszą określać system za pomocą interfejsu API lub warstwy pod interfejsem użytkownika. Konstruktory obiektów testowych, takich jak Order i MenuItem, muszą również nawiązać system w celu utworzenia odpowiednich elementów w systemie.

 Wiele metod dostępu i aktualizacji będzie już dostępnych za pomocą normalnego interfejsu API aplikacji. Jednak niektóre dodatkowe funkcje mogą być zapisywane w celu włączenia testów. Te dodatkowe metody dostępu i Updates są czasami nazywane "Instrumentacją testów". Ponieważ są one zależne od wewnętrznego projektu systemu, odpowiadają deweloperom systemu na ich dostarczenie, podczas gdy testerzy zapisują kod testów pod warunkiem modelu wymagań.

 Podczas pisania automatycznych testów można użyć testów ogólnych, aby zawijać metody dostępu i Updates.

### <a name="tests-for-business-rules"></a>Testy dla reguł firmy
 Niektóre wymagania nie są bezpośrednio związane z żadnym przypadkiem użycia. Na przykład firma DinnerNow umożliwia klientom wybór spośród wielu menu, ale wymaga, aby w każdym porządku wszystkie wybrane elementy pochodzą z jednego menu. Ta reguła biznesowa może być wyrażona jako niezmienna o skojarzeniach między zamówieniami, menu i elementami w modelu klasy wymagań.

 Niezmienna reguła tego rodzaju reguluje nie tylko przypadki użycia, które są obecnie zdefiniowane, ale również inne przypadki użycia, które zostaną zdefiniowane później. Z tego względu przydatne jest zapisanie go niezależnie od dowolnego przypadku użycia i przetestowanie go niezależnie od przypadków użycia.

## <a name="deriving-subsystem-tests-from-models"></a>Wyprowadzanie testów podsystemu z modeli
 W projekcie wysokiego poziomu dużego systemu można zidentyfikować składniki lub podsystemy. Reprezentują one części, które mogą być oddzielnie zaprojektowane lub znajdują się na różnych komputerach, lub są modułami wielokrotnego użytku, które można połączyć na wiele sposobów.

 Do każdego głównego składnika można zastosować te same zasady, które są stosowane do całego systemu. W dużym projekcie każdy składnik może mieć własny model wymagań. W mniejszych projektach można utworzyć model architektoniczny lub projekt wysokiego poziomu, aby pokazać główne składniki i ich interakcje. Aby uzyskać więcej informacji, zobacz [modelowanie architektury aplikacji](../modeling/model-your-app-s-architecture.md).

 W obu przypadkach można ustanowić relację między elementami modelu i testami podsystemu w taki sam sposób, jak między modelem wymagań i testami systemowymi.

### <a name="isolate-components-with-provided-and-required-interfaces"></a>Izoluj składniki z udostępnionymi i wymaganymi interfejsami
 Przydatne jest zidentyfikowanie wszystkich zależności, które składnik ma w innych częściach systemu lub usług zewnętrznych, a także do reprezentowania ich jako wymaganych interfejsów. To ćwiczenie zwykle prowadzi do niektórych reprojektów, które powodują, że składnik jest znacznie bardziej oddzielony i łatwo można go oddzielić od reszty Twojego projektu.

 Zaletą tego oddzielenia jest to, że składnik może być wykonywany do testowania przez zastępowanie z obiektami makiety, których zazwyczaj używa usługi. Są to składniki, które są skonfigurowane do celów testowych. Składnik makiety udostępnia interfejs wymagany przez składnik, który odpowiada na zapytania z symulowanymi danymi. Składniki makiety stanowią część kompletnego zespołu testowego, który można połączyć ze wszystkimi interfejsami składnika.

 Zaletą testowania makietów jest możliwość tworzenia składnika, gdy inne składniki, których będą używać usługi, są nadal w fazie projektowania.

## <a name="maintain-the-relationships-between-tests-and-model"></a>Obsługuj relacje między testami a modelem
 W typowym projekcie, który wykonuje iterację co kilka tygodni, przegląd wymagań jest przechowywany blisko początku każdej iteracji. Na spotkaniu omówiono funkcje, które zostaną dostarczone w następnej iteracji. Model wymagań może służyć do omówienia koncepcji, scenariuszy i sekwencji akcji, które zostaną opracowane. Zainteresowane strony biznesowe ustalają priorytety, deweloperzy dokonują oszacowania i sprawdzają, czy oczekiwane zachowanie poszczególnych funkcji jest przechwytywane poprawnie.

 Zapisywanie testów jest najbardziej skutecznym sposobem definiowania wymagania i jest również skutecznym sposobem zapewnienia, że osoba ma jasno zrozumiałe informacje o tym, co jest wymagane. Jednak podczas tworzenia testów trwa zbyt długo, aby podczas warsztatów dotyczących specyfikacji tworzenie modeli było znacznie szybsze.

 Z punktu widzenia testowania model wymagań może być traktowany jako skrót dla testów. W związku z tym ważne jest, aby zachować relacje między testami i modelem w całym projekcie.

## <a name="Attaching"></a>Dołączanie przypadków testowych do elementów modelu
 Jeśli projekt używa [!INCLUDE[TCMlong](../modeling/includes/tcmlong_md.md)], można połączyć testy z elementami w modelu. Dzięki temu można szybko znaleźć testy, których dotyczy zmiana w wymaganiach, i pomóc w śledzeniu zakresu, w jakim zostały zrealizowane wymagania.

 Można połączyć testy z wszystkimi rodzajami elementów. Oto kilka przykładów:

- Połącz przypadek użycia z testami, które go wykonują.

- Napisz klauzule błąd warunku końcowego przypadku użycia lub cel do komentarzy, które są połączone z przypadkiem użycia, a następnie połącz testy z każdym komentarzem.

- Zapisuj niezmienne reguły w komentarzach na diagramach klas lub diagramach aktywności i łącz je z testami.

- Połącz testy z diagramem aktywności lub z poszczególnymi działaniami.

- Połącz zestaw testów ze składnikiem lub podsystemem, który go testuje.

#### <a name="to-link-tests-to-a-model-element-or-relationship"></a>Aby połączyć testy z elementem modelu lub relacją

1. W [!INCLUDE[TCMlong](../modeling/includes/tcmlong_md.md)]Utwórz wymaganie i podstawowy zestaw testów.

    To wymaganie tworzone jest elementem roboczym w [!INCLUDE[vstsTfsShort](../modeling/includes/vststfsshort_md.md)]. Może to być scenariusz użytkownika, wymaganie lub element roboczy przypadku użycia, w zależności od szablonu procesu używanego przez projekt z programem Team Foundation. Aby uzyskać więcej informacji, zobacz [Informacje o narzędziach Agile i zarządzaniu projektami Agile](/azure/devops/boards/backlogs/backlogs-overview?view=vsts).

2. Połącz element roboczy wymaganie z co najmniej jednym elementem w modelu.

    Na diagramie modelowania kliknij prawym przyciskiem myszy element, komentarz lub relację, a następnie kliknij pozycję **Połącz z elementem roboczym**.

3. Dodaj do zestawu testów, przypadków testowych, które weryfikują wymóg wyrażony w elemencie modelu.

## <a name="see-also"></a>Zobacz także

- [Tworzenie modeli aplikacji](../modeling/create-models-for-your-app.md)
- [Wymagania modelu użytkownika](../modeling/model-user-requirements.md)
- [Modelowanie architektury aplikacji](../modeling/model-your-app-s-architecture.md)
- [Analizowanie i modelowanie architektury](../modeling/analyze-and-model-your-architecture.md)
