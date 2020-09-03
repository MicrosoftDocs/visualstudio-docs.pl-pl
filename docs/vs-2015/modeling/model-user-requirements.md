---
title: Wymagania dotyczące użytkownika modelu | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- requirements
- stories
- UML, modeling requirements
ms.assetid: 359900f8-6d69-493d-bfdf-2c9069c74a26
caps.latest.revision: 30
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: a94a4bd479c3ad48efe44d3a92e91dc3a050efcd
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "75918271"
---
# <a name="model-user-requirements"></a>Wymagania modelu użytkownika
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Program Visual Studio pomaga zrozumieć, omówić i komunikować się z potrzebami użytkowników, rysując diagramy związane z ich działaniami i część, która jest odtwarzana przez system w celu ułatwienia im osiągnięcia celów. Model wymagań to zbiór tych diagramów, z których każdy koncentruje się na różnych aspektach potrzeb użytkowników. Aby zapoznać się z prezentacją, zobacz: [modelowanie domeny biznesowej](https://channel9.msdn.com/blogs/clinted/uml-with-vs-2010-part-3-modeling-the-business-domain).

 Aby sprawdzić, które wersje programu Visual Studio obsługują każdy typ modelu, zobacz [Obsługa wersji dla narzędzi architektury i modelowania](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

 Model wymagań ułatwia:

- Skup się na zewnętrznym zachowaniu systemu, niezależnie od jego wewnętrznego projektu.

- Opisz potrzeby użytkowników i uczestników projektu o znacznie mniejszej niejednoznaczności niż w języku naturalnym.

- Zdefiniuj spójny słownik terminów, które mogą być używane przez użytkowników, deweloperów i testerów.

- Ogranicz luki i niespójności w wymaganiach.

- Zmniejsz ilość pracy wymaganej do reagowania na zmiany wymagań.

- Zaplanuj kolejność, w której będą rozwijane funkcje.

- Używaj modeli jako podstawy dla testów systemowych, co powoduje wyraźną relację między testami i wymaganiami. Po zmianie wymagań ta relacja pomaga zaktualizować testy prawidłowo. Pozwala to upewnić się, że system spełnia nowe wymagania.

  Model wymagań zapewnia największą korzyść, jeśli jest używany do koncentracji dyskusji z użytkownikami lub ich przedstawicielami, a następnie ponownie odwiedzany na początku każdej iteracji. Przed zapisaniem kodu nie jest konieczne jego szczegółowe zakończenie. Częściowo działająca aplikacja, nawet jeśli bardzo uproszczone, zazwyczaj stanowi najbardziej stymulowaną podstawę do omówienia wymagań dla użytkowników. Model jest efektywnym sposobem podsumowywania wyników dyskusji. Aby uzyskać więcej informacji, zobacz [Używanie modeli w procesie tworzenia oprogramowania](../modeling/use-models-in-your-development-process.md).

> [!NOTE]
> W tych tematach "system" oznacza system lub aplikację, którą tworzysz. Może to być duża kolekcja wielu składników oprogramowania i sprzętu. lub pojedynczej aplikacji; lub składnika oprogramowania w większym systemie. W każdym przypadku model wymagań opisuje zachowanie widoczne spoza systemu, niezależnie od tego, czy za pośrednictwem interfejsu użytkownika, czy interfejsu API.

## <a name="common-tasks"></a>Typowe zadania
 Można utworzyć kilka różnych widoków wymagań użytkowników.  Każdy widok zawiera informacje określonego typu.  Podczas tworzenia tych widoków najlepiej jest przebiegać często od jednego do drugiego. Możesz rozpocząć od dowolnego widoku.

|Diagram lub dokument|Co opisano w modelu wymagań|Sekcja|
|-------------------------|-----------------------------------------------|-------------|
|Diagramów przypadków użycia|Kto używa systemu i co robi z nim.|[Opis sposobu użycia systemu](#UseCases)|
|Diagram klasy koncepcyjnej|Słownik typów, które są używane do opisywania wymagań; typy widoczne w interfejsie systemu.|[Definiowanie terminów używanych do opisywania wymagań](#RequirementsClasses)|
|Diagramu aktywności|Przepływ pracy i informacje między działaniami wykonywanymi przez użytkowników i system lub jej części.|[Wyświetlanie przepływu pracy między użytkownikami i systemem](#Workflow)|
|Diagramów sekwencji|Sekwencja interakcji między użytkownikami i systemem lub jej częściami. Alternatywny widok diagramu aktywności.|[Wyświetlanie interakcji między użytkownikami i systemem](#Sequences)|
|Dodatkowe dokumenty lub elementy robocze|Kryteria wydajności, bezpieczeństwa, użyteczności i niezawodności.|[Opisywanie wymagań dotyczących jakości usług](#QoSRequirements)|
|Dodatkowe dokumenty lub elementy robocze|Ograniczenia i reguły niespecyficzne dla określonego przypadku użycia|[Wyświetlanie reguł firmy](#BusinessRules)|

 Należy zauważyć, że większość typów diagramów może być używana do innych celów. Aby zapoznać się z omówieniem typów diagramów, zobacz [Tworzenie modeli dla aplikacji](../modeling/create-models-for-your-app.md). Aby uzyskać podstawowe informacje o diagramach rysowania, zobacz [Edycja modeli UML i diagramów](../modeling/edit-uml-models-and-diagrams.md).

## <a name="describing-how-your-system-is-used"></a><a name="UseCases"></a> Opis sposobu użycia systemu
 Utwórz diagramy przypadków użycia, aby opisać, kto używa systemu i co z nich korzysta. Przypadek użycia reprezentuje cel użytkownika systemu i procedurę wykonywaną w celu osiągnięcia celu.

 Na przykład system sprzedaży posiłku w trybie online musi umożliwiać klientom wybór elementów z menu, a także Zezwalanie na aktualizowanie menu w usłudze Restauracje. Można podsumować ten element na diagramie przypadków użycia:

 ![Przypadki użycia dla klienta i restauracji](../modeling/media/uml-reqmuc1.png "UML_ReqmUC1")

 Możesz także pokazać, jak przypadek użycia składa się z mniejszych przypadków. Na przykład porządkowanie posiłku jest częścią zakupu posiłku, który obejmuje również płatność i dostarczanie:

 ![System uczestniczy w płatności, ale nie dostawy.](../modeling/media/uml-reqmuc2.png "UML_ReqmUC2")

 Można także pokazać, które przypadki użycia są zawarte w zakresie programowania. Na przykład system na ilustracji nie uczestniczy w przypadku użycia posiłku. Pozwala to na ustawienie kontekstu dla pracy programistycznej. (W diagramie przypadku użycia kontenery podsystemów mogą służyć do reprezentowania systemu lub jego składników).

 Pomaga również zespołowi omówić, co zostanie uwzględnione w kolejnych wersjach. Można na przykład omówić, czy w początkowej wersji systemu płatność za mączkę jest uporządkowana bezpośrednio między restauracji a klientem, zamiast przechodzić przez system. W takim przypadku można przenieść pozycję Płatność za posiłki na zewnątrz prostokąta systemowego do pierwszego obiadu w przypadku wersji początkowej.

 Diagram przypadków użycia zawiera tylko podsumowanie przypadków użycia. Aby uzyskać bardziej szczegółowe opisy, można połączyć przypadki użycia na diagramie, aby oddzielić dokumenty i inne diagramy. Aby dowiedzieć się, jak to zrobić, zobacz [łączenie przypadku użycia z dokumentami i diagramami](../modeling/link-a-use-case-to-documents-and-diagrams.md).

 Rysowanie diagramu przypadków użycia pomaga zespołowi:

- Należy skoncentrować się na tym, co użytkownicy oczekują w systemie, bez rozpraszania szczegółów implementacji.

- Omawianie zakresu systemu lub określonych wydań systemu.

  Dodatkowe informacje znajdują się w następujących tematach:

|Aby dowiedzieć się więcej o|Odczyt|
|--------------------|----------|
|Bardziej szczegółowe informacje na temat tworzenia przypadków użycia|[Diagramy przypadków użycia UML: wskazówki](../modeling/uml-use-case-diagrams-guidelines.md)|
|Elementy na diagramie przypadku użycia|[Diagramy przypadków użycia UML: Odwołanie](../modeling/uml-use-case-diagrams-reference.md)|
|Jak opracowywać kod z przypadków użycia|[Modelowanie architektury aplikacji](../modeling/model-your-app-s-architecture.md)|

## <a name="defining-terms-used-to-describe-requirements"></a><a name="RequirementsClasses"></a> Definiowanie terminów używanych do opisywania wymagań
 Diagramy klas UML ułatwiają tworzenie spójnego słownictwa koncepcji firmy używanych w następujących celach:

- Przez użytkowników w celu omówienia firmy, w której działa system.

- Aby opisać potrzeby użytkowników, na przykład opisy przypadków użycia, reguły biznesowe i historie użytkownika.

- Typy informacji wymienianych w interfejsie API systemu lub za pomocą interfejsu użytkownika.

- Opisy testów systemu lub akceptacji.

  Gdy są one używane do tego celu, zawartość diagramu klas UML jest nazywana diagramem klasy koncepcyjnej. (Jest on również nazywany modelem *domeny* lub *modelem klasy analizy*).

  Na diagramie klasy koncepcyjnej są wyświetlane tylko te klasy, które są potrzebne w opisie wymagań, bez pokazywania szczegółowych informacji o projekcie wewnętrznym systemu. Na diagramie nie są wyświetlane żadne szczegóły wewnętrznego projektu systemu. Zwykle nie są wyświetlane operacje ani interfejsy w klasach koncepcyjnych.

  Na przykład można narysować te klasy koncepcyjne na potrzeby systemu obiadu teraz:

  ![Menu klas, kolejność, element menu, element kolejności.](../modeling/media/uml-reqmcd1.png "UML_ReqMCD1")

  Diagram klasy koncepcyjnej zawiera słownictwo warunków, które są używane w całym modelu wymagań. Na przykład w szczegółowym opisie pozostałej części zamówienia przypadku użycia można napisać:

  Klient wybiera *menu* , z którego ma zostać utworzone *Zamówienie*, a następnie tworzy *elementy zamówienia* w *kolejności* , wybierając *pozycje menu* z *menu*.

  Zwróć uwagę na to, jak terminy używane w tym opisie są nazwami klas w modelu. Diagram usuwa niejasności z relacji między tymi klasami. Na przykład jasno pokazuje, że każde zamówienie jest skojarzone z tylko jednym menu.

  Niezrozumiałe informacje o wymaganiach użytkowników mogą być często śledzone w celu zapoznania się z szczegółowymi wyrazami. Na przykład większość restauracji będzie mieć wspólne zrozumienie menu warunki i kolejność, ale różnica między elementem w kolejności i elementem w menu jest mniej jasne. Gdy te wymagania są omawiane w zainteresowanych podmiotach, ważne jest, aby ujawnić te różnice. Diagram klas jest użytecznym narzędziem ułatwiającym wyjaśnienie warunków i ich relacji.

  Model klasy koncepcyjnej może stanowić podstawowe słownictwo, za pomocą którego można opisać system logiki biznesowej. Jednak klasy w oprogramowaniu zwykle są znacznie bardziej skomplikowane niż model koncepcyjny, ponieważ implementacja musi rozważyć problemy, takie jak wydajność, dystrybucja, elastyczność i inne czynniki. Kilka różnych implementacji klasy koncepcyjnej często można znaleźć w jednym systemie.

  Na przykład zamówienia mogą być reprezentowane w formacie XML, SQL, HTML i C# w różnych częściach systemu i w różnych interfejsach między częściami. Skojarzenie między kolejnością a menu może być reprezentowane na wiele różnych sposobów, takich jak odwołania w kodzie C#, relacje w bazie danych lub identyfikatory, do których istnieją odwołania w kodzie XML. Jednak pomimo tych różnic model koncepcyjny zawiera ważne informacje, które są prawdziwe w każdej części oprogramowania. Diagram klas w przykładzie informuje nas, że w każdej implementacji będzie tylko jedno menu skojarzone z każdym zamówieniem.

  Rysowanie diagramu klas wymagań ułatwia Twojemu zespołowi:

- Definiowanie i standaryzacja podstawowych terminów używanych w dyskusjach dotyczących potrzeb użytkowników.

- Wyjaśnij relacje między tymi postanowieniami.

  Dodatkowe informacje znajdują się w następujących tematach:

|Aby dowiedzieć się więcej o|Odczyt|
|--------------------|----------|
|Bardziej szczegółowe informacje na temat znajdowania klas wymagań|[Diagramy klas UML: wskazówki](../modeling/uml-class-diagrams-guidelines.md)|
|Elementy na diagramie klasy koncepcyjnej|[Diagramy klas UML: Odwołanie](../modeling/uml-class-diagrams-reference.md)|
|Jak opracowywać kod z klas koncepcyjnych|[Modelowanie architektury aplikacji](../modeling/model-your-app-s-architecture.md)|

 Na diagramie klasy koncepcyjnej zazwyczaj nie jest przydatne umieszczenie strzałek na skojarzeniach, aby reprezentować kierunek nawigacji. Dzieje się tak, ponieważ diagram nie reprezentuje implementacji. Skojarzenia reprezentują relacje między obiektami rzeczywistymi.

## <a name="showing-business-rules"></a><a name="BusinessRules"></a> Wyświetlanie reguł firmy
 Reguła biznesowa jest wymagana, która nie jest skojarzona z konkretnym przypadkiem użycia i powinna być zastosowana w całym systemie.

 Wiele reguł biznesowych to ograniczenia dotyczące relacji między klasami koncepcyjnymi. Te *statyczne reguły biznesowe* można napisać jako komentarze skojarzone z odpowiednimi klasami na diagramie klasy koncepcyjnej. Na przykład:

 ![Reguła w komentarzu dołączonym do klasy Order.](../modeling/media/uml-reqmcd2.png "UML_ReqmCD2")

 *Dynamiczne reguły biznesowe* ograniczają dozwolone sekwencje zdarzeń. Na przykład można użyć sekwencji lub diagramu aktywności, aby pokazać, że użytkownik musi się zalogować przed wykonaniem innych operacji w systemie.

 Jednak wiele reguł dynamicznych może być bardziej wydajnych i ogólnie określonych przez zastępowanie ich regułami statycznymi. Na przykład, można dodać atrybut Boolean "zalogowany" do klasy w modelu klasy koncepcyjnej. Należy dodać zalogowany jako błąd warunku końcowego w przypadku użycia i dodać go jako warunek wstępny większości innych przypadków użycia. Takie podejście pozwala uniknąć definiowania wszystkich możliwych kombinacji sekwencji zdarzeń. Jest to również bardziej elastyczne, gdy trzeba dodać do modelu nowe przypadki użycia.

 Należy zauważyć, że w tym miejscu opisano sposób definiowania wymagań oraz to, że jest on niezależny od sposobu implementacji wymagań w kodzie programu.

 Dodatkowe informacje znajdują się w następujących tematach:

|Aby dowiedzieć się więcej o|Odczyt|
|--------------------|----------|
|Bardziej szczegółowe informacje na temat znajdowania i rejestrowania statycznych reguł firmy|[Diagramy klas UML: wskazówki](../modeling/uml-class-diagrams-guidelines.md)|
|Elementy na diagramie klasy koncepcyjnej|[Diagramy klas UML: Odwołanie](../modeling/uml-class-diagrams-reference.md)|
|Jak opracowywać kod zgodny z regułami biznesowymi|[Modelowanie architektury aplikacji](../modeling/model-your-app-s-architecture.md)|

## <a name="describing-quality-of-service-requirements"></a><a name="QoSRequirements"></a> Opisywanie wymagań Quality of Service
 Istnieje kilka kategorii wymagań dotyczących jakości usług. Należą do nich następujące elementy:

- Wydajność

- Zabezpieczenia

- Łatwość obsługi

- Niezawodność

- Niezawodność

  Niektóre z tych wymagań można uwzględnić w opisach konkretnych przypadków użycia. Inne wymagania nie są specyficzne dla przypadków użycia i są najbardziej efektywnie zapisywane w osobnym dokumencie. Gdy jest to możliwe, warto przestrzegać słownictwa zdefiniowanego przez model wymagań. W poniższym przykładzie należy zauważyć, że główne wyrazy używane w wymaganiu są tytułami aktorów, przypadków użycia i klas na powyższych ilustracjach:

  Jeśli restauracji usunie element menu, gdy klient porządkuje posiłk, każdy element zamówienia, który odwołuje się do tego elementu menu będzie wyświetlany na czerwono.

  Dodatkowe informacje znajdują się w następujących tematach:

|Aby dowiedzieć się więcej o|Odczyt|
|--------------------|----------|
|Dołączanie dodatkowych dokumentów do przypadków użycia|[Łączenie przypadków użycia z dokumentami i diagramami](../modeling/link-a-use-case-to-documents-and-diagrams.md)|
|Jak opracowywać kod, który jest zgodny z wymaganiami dotyczącymi jakości usług|[Modelowanie architektury aplikacji](../modeling/model-your-app-s-architecture.md)|

## <a name="showing-work-flow-between-users-and-your-system"></a><a name="Workflow"></a> Wyświetlanie przepływu pracy między użytkownikami i systemem
 Możesz użyć diagramu aktywności, aby pokazać przepływ pracy między różnymi przypadkami użycia. Często warto rozpocząć model wymagań, rysując diagram aktywności pokazujący główne zadania wykonywane przez użytkowników — zarówno w systemie, jak i poza nim.

 Na przykład:

 ![Działanie z trzema akcjami i pętlą.](../modeling/media/uc-reqmwfact.png "UC_ReqmWFAct")

 Diagramy przypadków użycia i diagramy aktywności można rysować, aby wyświetlić różne widoki tych samych informacji.  Diagram przypadków użycia jest bardziej efektywny, pokazując zagnieżdżenie mniejszych akcji w ramach większego działania, ale nie pokazuje przepływu pracy. Na przykład:

 ![Przypadki użycia dla poprzednich akcji](../modeling/media/uml-reqmwfuc.png "UML_ReqmWFUC")

 Należy zauważyć, że można również użyć diagramów aktywności do przedstawiania algorytmów w oprogramowaniu, ale w przypadku używania diagramów dla procesu biznesowego należy skoncentrować się na działaniach, które są widoczne poza systemem.

 Dodatkowe informacje znajdują się w następujących tematach:

|Aby dowiedzieć się więcej o|Odczyt|
|--------------------|----------|
|Więcej informacji na temat definiowania przepływów pracy biznesowej|[Diagramy aktywności UML: wskazówki](../modeling/uml-activity-diagrams-guidelines.md)|
|Elementy na diagramie aktywności|[Diagramy aktywności UML: informacje](../modeling/uml-activity-diagrams-reference.md)|
|Jak opracowywać kod z diagramów aktywności|[Modelowanie architektury aplikacji](../modeling/model-your-app-s-architecture.md)|

## <a name="showing-interactions-between-users-and-your-system"></a><a name="Sequences"></a> Wyświetlanie interakcji między użytkownikami i systemem
 Możesz użyć diagramu sekwencji, aby pokazać wymianę komunikatów między systemem i aktorami zewnętrznymi lub między częściami systemu. Zapewnia to przegląd kroków w przypadku użycia, który pokazuje bardzo jasne sekwencje interakcji. Diagramy sekwencji są szczególnie przydatne w przypadku, gdy istnieje kilka stron współpracujących w przypadku użycia, a także w przypadku, gdy system ma interfejs API.

 Na przykład:

 ![Diagram sekwencji z systemem i aktorami.](../modeling/media/uml-reqmseq.png "UML_ReqmSeq")

 Jedną z zalet diagramów sekwencji jest łatwe sprawdzenie, jakie komunikaty są wykonywane w systemie, który tworzysz. Aby zaprojektować system, można zamienić pojedynczą linię życia systemu z osobną linią życia dla każdego z jej składników, a następnie pokazać interakcje między nimi w odpowiedzi na każdą wiadomość przychodzącą.

 Dodatkowe informacje znajdują się w następujących tematach:

|Aby dowiedzieć się więcej o|Odczyt|
|--------------------|----------|
|Więcej informacji na temat sposobu definiowania interakcji|[Diagramy sekwencji UML: wskazówki](../modeling/uml-sequence-diagrams-guidelines.md)|
|Elementy na diagramie sekwencji|[Diagramy sekwencji UML: informacje](../modeling/uml-sequence-diagrams-reference.md)|
|Jak opracowywać kod z diagramów sekwencji|[Modelowanie architektury aplikacji](../modeling/model-your-app-s-architecture.md)|

## <a name="using-a-model-to-reduce-inconsistencies"></a>Korzystanie z modelu w celu zmniejszenia niespójności
 Utworzenie modelu zwykle skutkuje znaczącym zmniejszeniem niespójności i niejasności w wymaganiach użytkowników. Różne osoby zainteresowane często mają różne zrozumienia świata firmy, w których działa system. W związku z tym pierwsze zadanie polega na rozwiązaniu tych różnic między klientami.

 Jeśli tworzysz model, wiele pytań dotyczących domeny biznesowej powstało w sposób naturalny. Umieszczenie tych pytań dla użytkowników spowoduje zmniejszenie potrzeb zmian w późniejszym etapie projektu. Poniżej przedstawiono kilka konkretnych pytań, na które można zadać swoją firmę, a następnie poproszenie zainteresowanych stron, jeśli odpowiedź jest niejasne:

- Dla każdej klasy w modelu wymagań należy zapytać "jakie przypadki użycia tworzą wystąpienia tej klasy?". Na przykład w usłudze zamawiania posiłków online można zażądać, "jakiego przypadku użycia tworzy wystąpienia klasy menu restauracji?". Może to prowadzić do omówienia sposobu rejestracji nowej restauracji w usłudze i współtworzenia menu. Możesz zadać podobne pytania dotyczące tworzenia lub zmieniania atrybutów i skojarzeń.

- Dla każdego przypadku użycia w modelu wymagań spróbuj opisać wynik lub błąd warunku końcowego każdego przypadku użycia w słowach dostarczonych przez diagramy klas. Często warto pokazać efekt przypadku użycia przez Szkicowanie wystąpień klas przed i po wystąpieniu przypadku użycia. Na przykład, jeśli przypadek użycia błąd warunku końcowego brzmi "element menu jest dodawany do zamówienia klienta", "szkic wystąpienia klasy Order i Item menu. Pokaż efekty przypadku użycia, takie jak nowy link lub nowy obiekt, w innym kolorze lub w nowym rysunku. Często prowadzi to do dyskusji na temat tego, jakie informacje są niezbędne w modelu. Mimo że klasy wymagań nie są bezpośrednio objęte implementacją, określają informacje, które system będzie musiał przechowywać i przesłać.

- Podawaj ograniczenia dotyczące atrybutów i skojarzeń, szczególnie ograniczeń obejmujących więcej niż jeden atrybut lub skojarzenie.

- Pytania dotyczące prawidłowych i nieprawidłowych sekwencji przypadków użycia, rysowania sekwencji lub diagramów aktywności w celu zilustrowania ich.

  Sprawdzając relacje między widokami, które udostępniają różne diagramy, możesz szybko zrozumieć główne koncepcje, z którymi pracują użytkownicy, i pomóc im zrozumieć, czego potrzebują z systemu. Możesz również lepiej zrozumieć, jakie wymagania uczestnicy projektu są na nich określone. Można zaplanować tworzenie tych funkcji, co najmniej w uproszczonej formie, na wczesnym etapie projektu, dzięki czemu użytkownicy mogą eksperymentować z nimi.

## <a name="see-also"></a>Zobacz też
 [Edytowanie modeli i diagramów UML](../modeling/edit-uml-models-and-diagrams.md) [Tworzenie testów z modelu](../modeling/develop-tests-from-a-model.md) [Używanie modeli w modelu procesów programistycznych](../modeling/use-models-in-your-development-process.md) film wideo dotyczący [architektury aplikacji](../modeling/model-your-app-s-architecture.md) [: Modelowanie domeny biznesowej](https://channel9.msdn.com/blogs/clinted/uml-with-vs-2010-part-3-modeling-the-business-domain)
