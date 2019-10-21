---
title: Modelowanie architektury&#39;aplikacji | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- UML, modeling architecture
ms.assetid: aedce746-9df5-49e1-9662-67eb1b83d313
caps.latest.revision: 21
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 41dbb7b996c32af10010694935cbd3660b462f73
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72609637"
---
# <a name="model-your-app39s-architecture"></a>Modelowanie architektury&#39;aplikacji
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Aby zapewnić, że system oprogramowania lub aplikacja spełnia potrzeby użytkowników, możesz tworzyć modele w programie Visual Studio jako część opisu ogólnej struktury i zachowania systemu oprogramowania lub aplikacji. Korzystając z modeli, można również opisać wzorce, które są używane w całym projekcie. Te modele pomagają zrozumieć istniejącą architekturę, omawiać zmiany i informować o zamiarach jasno.

 Aby sprawdzić, które wersje programu Visual Studio obsługują tę funkcję, zobacz [Obsługa wersji dla narzędzi architektury i modelowania](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

 Celem modelu jest zredukowanie niejasnościych w opisach języka naturalnego i ułatwienie współpracownikom oraz wizualizacji projektu i omówienia alternatywnych projektów. Model powinien być używany razem z innymi dokumentami lub dyskusjami. Sam model nie reprezentuje kompletnej specyfikacji architektury.

> [!NOTE]
> W tym temacie "system" oznacza opracowywane oprogramowanie. Może to być duża kolekcja wielu składników oprogramowania i sprzętu albo jedna aplikacja lub część aplikacji.

 Architekturę systemu można podzielić na dwa obszary:

- [Projektowanie wysokiego poziomu](#Structure). Opisano w nim główne składniki i sposób współdziałania ze sobą, aby spełnić każde wymaganie. Jeśli system jest duży, każdy składnik może mieć własny projekt wysokiego poziomu, który pokazuje, jak składa się z mniejszych składników.

- [Wzorce projektowe](#Patterns) i konwencje używane w całym projekcie składników programu. Wzorzec opisuje konkretne podejście do osiągnięcia celów programistycznych. Korzystając z tych samych wzorców w całym projekcie, zespół może zmniejszyć koszty dokonywania zmian i tworzenia nowego oprogramowania.

## <a name="Structure"></a>Projektowanie wysokiego poziomu
 Projekt wysokiego poziomu opisuje główne składniki systemu i sposób współdziałania ze sobą, aby osiągnąć cele projektu. Działania na poniższej liście są związane z tworzeniem projektu wysokiego poziomu, chociaż niekoniecznie w określonej kolejności.

 Jeśli aktualizujesz istniejący kod, możesz zacząć od opisywania głównych składników. Upewnij się, że rozumiesz wszelkie zmiany wymagań użytkownika, a następnie Dodaj lub zmodyfikuj interakcje między składnikami. Jeśli tworzysz nowy system, Zacznij od poznania głównych funkcji potrzeb użytkowników. Następnie można zbadać sekwencje interakcji dla głównych przypadków użycia, a następnie skonsolidować sekwencje w projekcie składnika.

 W każdym przypadku warto opracować różne działania równolegle oraz opracować kod i testy na wczesnym etapie. Unikaj próby wykonania jednego z tych aspektów przed rozpoczęciem kolejnego. Zwykle wymagania i zrozumienie najlepszego sposobu projektowania systemu zmienią się podczas pisania i testowania kodu. W związku z tym należy zacząć od ustalenia i kodowania głównych funkcji wymagań i projektu. Wprowadź szczegóły w kolejnych iteracjach projektu.

- [Informacje o wymaganiach](#Requirements). Punktem początkowym dowolnego projektu jest jasne zrozumienie potrzeb użytkowników.

- [Wzorce architektury](#BigDecisions). Opcje dotyczące podstawowych technologii i elementów architektonicznych systemu.

- [Składniki i ich interfejsy](#Components). Możesz narysować diagramy składników, aby pokazać główne części systemu i pokazać interfejsy, za pomocą których współpracują ze sobą. Interfejsy każdego składnika obejmują wszystkie komunikaty, które zostały zidentyfikowane w diagramach sekwencji.

- [Interakcje między składnikami](#Interactions). Dla każdego przypadku użycia, zdarzenia lub wiadomości przychodzącej można narysować diagram sekwencji pokazujący, jak główne składniki systemu współdziałają w celu osiągnięcia wymaganej odpowiedzi.

- [Model danych składników i interfejsów](#Data). Można rysować diagramy klas, aby opisać informacje przesyłane między składnikami i przechowywane w składnikach.

## <a name="Requirements"></a>Informacje o wymaganiach
 Ogólny projekt kompletnej aplikacji jest najwydajniejszie opracowany z modelem wymagań lub innym opisem potrzeb użytkowników. Aby uzyskać więcej informacji na temat modeli wymagań, zobacz [wymagania dotyczące modelu użytkownika](../modeling/model-user-requirements.md).

 Jeśli opracowywany system jest składnikiem większego systemu, część lub wszystkie wymagania mogą być zawarte w interfejsach programistycznych.

 Model wymagań zawiera następujące podstawowe informacje:

- Udostępnione interfejsy. Udostępniony interfejs zawiera listę usług lub operacji, które system lub składnik musi dostarczyć swoim użytkownikom, niezależnie od tego, czy są one użytkownikami ludzkimi, czy innymi składnikami oprogramowania.

- Wymagane interfejsy. Wymagany interfejs zawiera listę usług lub operacji, które mogą być używane przez system lub składnik. W niektórych przypadkach będzie można zaprojektować wszystkie te usługi w ramach własnego systemu. W innych przypadkach, szczególnie w przypadku projektowania składnika, który można połączyć z innymi składnikami w wielu konfiguracjach, wymagany interfejs zostanie ustawiony przez zagadnienia zewnętrzne.

- Wymagania dotyczące jakości usług. Wydajność, bezpieczeństwo, niezawodność i inne cele oraz ograniczenia, które system musi spełnić.

  Model wymagań jest zapisywana z punktu widzenia użytkowników systemu, niezależnie od tego, czy są one osobami, czy innymi składnikami oprogramowania. Nie znają nic z wewnętrznych działań systemu. Z drugiej strony celem w modelu architektury jest opisywanie pracy wewnętrznej i pokazanie, jak spełnią się potrzeby użytkowników.

  Wymagania i różne modele architektoniczne są przydatne, ponieważ ułatwiają one przedyskutowanie wymagań z użytkownikami. Ułatwia również refaktoryzację projektu i rozważenie alternatywnych architektur przy zachowaniu niezmienionych wymagań.

  Wymagania i modele architektury można rozdzielić na dwa sposoby:

- Zachowaj je w tym samym rozwiązaniu, ale w różnych projektach. Będą one wyświetlane jako oddzielne modele w Eksploratorze modelu UML. Różne elementy członkowskie zespołu mogą równolegle współpracować z modelami. Można tworzyć ograniczone rodzaje śledzenia między modelami.

- Umieść je w tym samym modelu UML, ale w różnych pakietach. Ułatwia to Śledzenie zależności między modelami, ale uniemożliwia pracę nad modelem przez więcej niż jedną osobę. Ponadto bardzo duży model będzie dłużej ładowany do programu Visual Studio. W związku z tym takie podejście jest mniej odpowiednie dla dużych projektów.

  Ilość szczegółów, które należy umieścić w wymaganiach lub modelu architektury, zależy od skali projektu oraz wielkości i dystrybucji zespołu. Niewielki zespół w krótkim projekcie może nie przekroczyć szkicu diagramu klas koncepcji firmy i niektórych wzorców projektowych; duży projekt dystrybuowany przez więcej niż jeden region będzie wymagał znacznie większej szczegółowości.

## <a name="BigDecisions"></a>Wzorce architektury
 Na wczesnym etapie opracowywania należy wybrać główne technologie i elementy, od których zależy projekt. Obszary, w których należy dokonać wyboru, obejmują następujące elementy:

- Podstawowe opcje technologii, takie jak wybór między bazą danych i systemem plików oraz wybór między aplikacją sieciową a klientem internetowym itd.

- Opcje struktur, takie jak wybór między Windows Workflow Foundation lub ADO.NET Entity Framework.

- Wybór metody integracji, na przykład między usługą Service Bus lub kanałem punkt-punkt.

  Te opcje są często określane przez wymagania dotyczące jakości usług, takie jak skalowanie i elastyczność, i można je wprowadzić przed ustaleniem szczegółowych wymagań. W dużym systemie konfiguracja sprzętu i oprogramowania jest silnie powiązana.

  Wybrane opcje mają wpływ na sposób użycia i interpretacji modelu architektury. Na przykład w systemie, który korzysta z bazy danych, skojarzenia w diagramie klas mogą reprezentować relacje lub klucze obce w bazie danych, natomiast w systemie, który jest oparty na plikach XML, skojarzenia mogą wskazywać odwołania krzyżowe, które używają XPath. W systemie rozproszonym komunikaty w diagramie sekwencji mogą reprezentować komunikaty w sieci przewodowej. w aplikacji samodzielnej mogą one reprezentować wywołania funkcji.

## <a name="Components"></a>Składniki i ich interfejsy
 Główne zalecenia dotyczące tej sekcji są następujące:

- Utwórz diagramy składników, aby pokazać główne części systemu.

- Rysuj zależności między składnikami lub ich interfejsami, aby pokazać strukturę systemu.

- Użyj interfejsów na składnikach, aby wyświetlić usługi, które są dostarczane lub wymagane przez każdy składnik.

- W dużym projekcie można rysować oddzielne diagramy, aby rozłożyć poszczególne składniki na mniejsze części.

  Te punkty są rozbudowane w pozostałej części tej sekcji.

### <a name="components"></a>Składniki
 Centralnymi widokami modelu architektury są diagramy składników pokazujące główne części systemu i sposób, w jaki są one od siebie zależne. Aby uzyskać więcej informacji na temat diagramów składników, zobacz [diagramy składników UML: Reference](../modeling/uml-component-diagrams-reference.md).

 ![Diagram składnika UML pokazujący części](../modeling/media/uml-barecomponent.png "UML_BareComponent")

 Typowy diagram składników dla dużego systemu może obejmować następujące składniki:

- Prezentacj. Składnik, który zapewnia dostęp do użytkownika, zwykle działa w przeglądarce sieci Web.

- Składniki usługi sieci Web. Zapewnia połączenie między klientami a serwerami.

- Używanie kontrolerów przypadków. Przeprowadź użytkownika przez kroki każdego scenariusza.

- Rdzeń biznesowy. Zawiera klasy, które są oparte na klasach w modelu wymagań, implementuje najważniejsze operacje i nakładają ograniczenia biznesowe.

- Database. Przechowuje obiekty biznesowe.

- Rejestrowanie i obsługa błędów składników.

### <a name="dependencies-between-components"></a>Zależności między składnikami
 Oprócz samych składników można pokazać zależności między nimi. Strzałka zależność między dwoma składnikami pokazuje, że zmiany w projekcie jednego mogą wpłynąć na projekt drugiego. Zwykle dzieje się tak, ponieważ jeden składnik korzysta z usług lub funkcji udostępnianych przez inny składnik, bezpośrednio lub pośrednio.

 Dobrze skonstruowana architektura ma wyraźne rozmieszczenie zależności, w których są spełnione następujące warunki:

- Brak pętli na mapie kodu.

- Składniki można rozmieścić w warstwach, w których każda zależność przechodzi ze składnika w jednej warstwie do składnika w następnym. Wszystkie zależności między dwoma warstwami przechodzą w tym samym kierunku.

  Można pokazać zależności bezpośrednio między składnikami lub pokazać zależności między wymaganymi i udostępnionymi interfejsami, które są dołączone do składników programu. Korzystając z interfejsów, można definiować operacje, które są używane w poszczególnych zależnościach. Zazwyczaj zależności są wyświetlane między składnikami, gdy diagramy są rysowane po raz pierwszy, a następnie zastępowane przez zależności między interfejsami, gdy dodawane są więcej informacji. Obie wersje są prawidłowymi opisami oprogramowania, ale wersja z interfejsami zawiera więcej szczegółów niż wcześniejsza wersja.

  Zarządzanie zależnościami jest najważniejsze dla produkcji oprogramowania do utrzymania. Diagramy składników powinny odzwierciedlać wszystkie zależności w kodzie. Jeśli kod już istnieje, upewnij się, że wszystkie zależności są widoczne na diagramach. Jeśli kod jest opracowywany, upewnij się, że nie zawiera on zależności, które nie są planowane na diagramie składników. Aby ułatwić odnajdywanie zależności w kodzie, można generować diagramy warstwowe. Aby zapewnić spełnienie planowanych ograniczeń zależności, można sprawdzić poprawność kodu względem diagramów warstw. Aby uzyskać więcej informacji, zobacz [diagramy warstwowe: odwołanie](../modeling/layer-diagrams-reference.md).

### <a name="interfaces"></a>Interfejsy
 Umieszczając interfejsy w składnikach, można oddzielić główne grupy operacji, które są dostarczane przez poszczególne składniki, i ich nazwy. Na przykład składniki w systemie sprzedaży w sieci Web mogą mieć interfejs, za pośrednictwem którego klienci kupują towary, interfejs, za pośrednictwem którego dostawcy aktualizują wykazy, a trzecim interfejsem, za pośrednictwem którego system jest zarządzany.

 Składnik może mieć dowolną liczbę dostarczonych i wymaganych interfejsów. Podane interfejsy pokazują usługi udostępniane przez składnik innym składnikom do użycia. Interfejsy wymagane pokazują usługi, których składnik używa w innych składnikach.

 Jeśli zdefiniowano zarówno dostarczone, jak i wymagane interfejsy, to ułatwia oddzielenie składnika od reszty projektu, dzięki czemu można używać tych technik:

- Umieść składnik do zespołu testowego, w którym otaczające składniki są symulowane przez zespół testów.

- Opracowywanie składnika niezależnie od innych składników.

- Użyj ponownie składnika w innych kontekstach przez Sprzęganie jego interfejsów z różnymi składnikami.

  Aby zdefiniować listę operacji w interfejsie, można utworzyć inny widok interfejsu na diagramie klas UML. W tym celu Znajdź interfejs w Eksploratorze modelu UML i przeciągnij go na Diagram klas. Następnie można dodać operacje do interfejsu.

  Operacja w interfejsie UML może reprezentować dowolną metodę, w której można wywołać działanie składnika. Może reprezentować żądanie usługi sieci Web, sygnał lub interakcję innego rodzaju lub zwykłe wywołanie funkcji programu.

  Aby określić, jakie operacje dodać, Utwórz diagramy sekwencji, aby pokazać, jak składniki współdziałają ze sobą. Zobacz [interakcje między składnikami](#Interactions). Każdy z tych diagramów sekwencji pokazuje interakcje występujące w innym przypadku użycia. W ten sposób można stopniowo dodawać do listy operacji w interfejsie każdego składnika, podczas eksplorowania przypadków użycia.

### <a name="decomposing-a-component-into-parts"></a>Deredagowanie składnika do części
 Do każdego składnika można zastosować procedurę opisaną w poprzednich sekcjach.

 W ramach każdego składnika można pokazać jego składniki podrzędne jako części. Część jest efektywnie atrybutem jego składnika nadrzędnego, który jest rodzajem klasy. Każda część ma swój własny typ, który może być składnikiem. Można umieścić ten składnik na diagramie i wyświetlić jego części. Aby uzyskać więcej informacji, zobacz [diagramy składników UML: wytyczne](../modeling/uml-component-diagrams-guidelines.md).

 Warto zastosować tę technikę do całego systemu. Narysuj ją jako pojedynczy składnik i Pokaż jej główne składniki jako części. Dzięki temu możesz identyfikować jasno interfejsy systemu z zewnętrznym światem.

 Gdy projekt dla składnika używa innego składnika, często istnieje wybór, czy ma on być reprezentowany jako część, czy jako osobny składnik, do którego uzyskuje się dostęp za pośrednictwem wymaganego interfejsu.

 Użyj części w następujących sytuacjach:

- Projekt składnika nadrzędnego musi zawsze używać typu składnika części. W związku z tym konstrukcja części jest całką dla projektu składnika nadrzędnego.

- Składnik nadrzędny nie ma konkretnej istnienia. Na przykład może istnieć składnik koncepcyjny o nazwie warstwa prezentacji, która reprezentuje kolekcję rzeczywistych składników, które obsługują widoki i interakcje użytkowników.

  Użyj oddzielnych składników dostępnych w ramach wymaganych interfejsów w następujących sytuacjach:

- Składnik wymagający możliwości można połączyć za pomocą jego interfejsów, aby zapewnić różne składniki w czasie wykonywania.

- Projekt jest w taki sposób łatwy do zastępowania jednego dostawcy innym.

  Użycie wymaganych interfejsów jest zwykle preferowane w przypadku korzystania z części. Mimo że projekt może trwać dłużej, system, który jest bardziej elastyczny. Łatwiej jest również testować składniki osobno. Pozwala to na mniejsze sprzęganie w swoich planach programistycznych.

## <a name="Interactions"></a>Interakcje między składnikami
 Główne zalecenia dotyczące tej sekcji są następujące:

- Zidentyfikuj przypadki użycia systemu.

- Dla każdego przypadku użycia należy narysować jeden lub więcej diagramów, aby pokazać, jak składniki systemu osiągają wymagany wynik, współpracując ze sobą i z użytkownikami. Zazwyczaj są to diagramy sekwencji i diagramy aktywności.

- Użyj interfejsów, aby określić komunikaty odbierane przez poszczególne składniki.

- Opisz skutki operacji w interfejsach.

- Powtórz procedurę dla każdego składnika, pokazując, jak działa jego części.

  Na przykład w systemie sprzedaży opartym na sieci Web model wymagań może definiować zakup klienta jako przypadek użycia. Można utworzyć diagram sekwencji, aby pokazać interakcje, które klient ma ze składnikami warstwy prezentacji, oraz pokazać interakcje z nimi w hurtowni i składnikach księgowości.

### <a name="identifying-the-initiating-events"></a>Identyfikowanie zdarzeń inicjujących
 Pracy wykonywanej przez większość systemów oprogramowania można wygodnie podzielić na odpowiedzi na różne dane wejściowe lub zdarzenia. Zdarzenie inicjujące może być jednym z następujących zdarzeń:

- Pierwsza akcja w przypadku użycia. Może się pojawić w modelu wymagań jako krok w przypadku użycia lub Akcja w diagramie aktywności. Aby uzyskać więcej informacji, [diagramy przypadków użycia UML: wytyczne](../modeling/uml-use-case-diagrams-guidelines.md) i [diagramy aktywności UML: wytyczne](../modeling/uml-activity-diagrams-guidelines.md).

- Komunikat w interfejsie programistycznym. Jeśli opracowywany system jest składnikiem w większym systemie, powinien zostać opisany jako operacja w jednym z interfejsów składnika. Zobacz [składniki i ich interfejsy](#Components).

- Określony warunek, który jest monitorowany przez system lub regularnym zdarzeniem, takim jak dzień.

### <a name="describe-the-computations"></a>Opisz obliczenia
 Rysuj diagramy sekwencji, aby pokazać, jak składniki reagują na początkowe zdarzenie.

 Narysuj linię życia dla każdego wystąpienia składnika, które jest częścią typowej sekwencji. W niektórych przypadkach może istnieć więcej niż jedno wystąpienie każdego typu. Jeśli został opisany cały system jako pojedynczy składnik, dla każdej części, która zawiera, powinna istnieć jedna linia życia.

 Aby uzyskać więcej informacji, zobacz [diagramy sekwencji UML: wytyczne](../modeling/uml-sequence-diagrams-guidelines.md).

 Diagramy aktywności są również przydatne w niektórych przypadkach. Na przykład, jeśli składniki mają ciągły przepływ danych, można je opisać jako przepływ obiektów. Jeśli składnik ma złożony algorytm, można go opisać jako przepływ sterowania. Upewnij się, że wyczyścisz, który składnik wykonuje poszczególne akcje, na przykład przy użyciu komentarzy. Aby uzyskać więcej informacji, zobacz [diagramy aktywności UML: wytyczne](../modeling/uml-activity-diagrams-guidelines.md).

### <a name="specify-the-operations"></a>Określ operacje
 Diagramy pokazują operacje, które są wykonywane przez poszczególne składniki, reprezentowane jako wiadomości w diagramie sekwencji lub akcje na diagramie aktywności.

 Zbieraj te operacje razem dla każdego składnika. Utwórz udostępnione interfejsy w składniku i Dodaj operacje do interfejsów. Zazwyczaj dla każdego typu klienta jest używany osobny interfejs. Operacje są najłatwiej dodane do interfejsów w **Eksploratorze modelu UML**. W ten sam sposób Zbierz operacje, które każdy składnik używa z innych składników, i umieść je w wymaganych interfejsach dołączonych do składnika.

 Warto dodać komentarze do diagramów działań lub sekwencji, aby zauważyć, co zostało osiągnięte po każdej operacji. Możesz również napisać efekt każdej operacji we właściwości **lokalnej błąd warunku końcowego** .

### <a name="Data"></a>Model danych składników i interfejsów
 Zdefiniuj parametry i wartości zwracane dla każdej operacji w interfejsie składnika. Gdzie operacje reprezentują wywołania, takie jak żądania usługi sieci Web, parametry są te informacje, które są wysyłane w ramach żądania. Gdy kilka wartości jest zwracanych z operacji, można użyć parametrów z właściwością **Direction** ustawioną na wartość **out**.

 Każdy parametr i zwracana wartość ma typ. Te typy można definiować za pomocą diagramów klas UML. Nie ma potrzeby przedstawiania szczegółów implementacji w tych diagramach. Na przykład w przypadku opisywania danych, które są przesyłane jako XML, można użyć skojarzenia do reprezentowania dowolnego rodzaju odwołania między węzłami XML i używać klas do reprezentowania węzłów.

 Użyj komentarzy, aby opisać ograniczenia biznesowe dotyczące skojarzeń i atrybutów. Na przykład, jeśli wszystkie elementy w zamówieniu klienta muszą pochodzić od tego samego dostawcy, można je opisać przez odwołanie do skojarzeń między elementami zamówienia i elementami w katalogu produktów oraz między elementem katalogu i jego dostawcą.

## <a name="Patterns"></a>Wzorce projektowe
 Wzorzec projektowy to zarys sposobu projektowania określonego aspektu oprogramowania, szczególnie te, które odnoszą się do różnych części systemu. Przyjmując jednolite podejście w całym projekcie, można zmniejszyć koszt projektu, zapewnić spójność w interfejsie użytkownika, a także zmniejszyć koszt interpretacji i zmiany kodu.

 Niektóre ogólne wzorce projektowe, takie jak obserwator, są dobrze znane i szeroko stosowane. Ponadto istnieją wzorce, które mają zastosowanie tylko do projektu. Na przykład w systemie sprzedaży sieci Web będzie kilka operacji w kodzie, w którym zmiany są wprowadzane do zamówienia klienta. Aby upewnić się, że stan zamówienia jest dokładnie wyświetlany na każdym etapie, wszystkie te operacje muszą być zgodne z określonym protokołem w celu zaktualizowania bazy danych.

 Część pracy z architekturą oprogramowania polega na określeniu, jakie wzorce należy przyjąć w ramach projektu. Zwykle jest to bieżące zadanie, ponieważ nowe wzorce i ulepszenia istniejących wzorców zostaną odnalezione jako postęp projektu. Warto zorganizować plan rozwoju w taki sposób, aby wykonywał wszystkie główne wzorce projektowe na wczesnym etapie.

 Większość wzorców projektowych może być częściowo pomieścić w kodzie struktury. Część wzorca może zostać zredukowana, aby wymagać od programisty używania określonych klas lub składników, takich jak Warstwa dostępu do bazy danych, która gwarantuje, że baza danych jest prawidłowo obsługiwana.

 Wzorzec projektowy został opisany w dokumencie i zwykle zawiera te części:

- Nazwij.

- Opis kontekstu, w którym ma zastosowanie. Jakie kryteria należy wziąć pod uwagę w przypadku zastosowania tego wzorca przez dewelopera?

- Krótkie wyjaśnienie problemu, który rozwiązuje.

- Model głównych części i ich relacji. Mogą to być klasy lub składniki i interfejsy, ze skojarzeniami i zależnościami między nimi. Elementy zwykle należą do dwóch kategorii:

  - Elementy, które Deweloper musi replikować w każdej części kodu, w której używany jest wzorzec. Możesz użyć typów szablonów do opisywania tych. Aby uzyskać więcej informacji, zobacz [diagramy przypadków użycia UML: odwołanie](../modeling/uml-use-case-diagrams-reference.md).

  - Elementy opisujące klasy struktury, które powinny być używane przez dewelopera.

- Model interakcji między częściami, za pomocą diagramów sekwencji lub działań.

- Konwencje nazewnictwa.

- Opis sposobu, w jaki wzorzec rozwiązuje problem.

- Opis wariantów, które mogą być w stanie zastosować deweloperzy.

## <a name="see-also"></a>Zobacz też
 [Edytowanie modeli i diagramów UML](../modeling/edit-uml-models-and-diagrams.md) [Wizualizacja](../modeling/visualize-code.md) [wymagania użytkownika model](../modeling/model-user-requirements.md) kodu [projektowanie testów z modelu](../modeling/develop-tests-from-a-model.md) [Używanie modeli w procesie tworzenia](../modeling/use-models-in-your-development-process.md)
