---
title: 'Diagramy aktywności UML: wytyczne | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- UML diagrams, activity
- diagrams - modeling, activity
- diagrams - modeling, UML activity
- activity diagrams
- UML, activity diagrams
ms.assetid: fe5dbe96-79ab-483a-b9bc-44d0d1d3efc2
caps.latest.revision: 50
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 692859008891439e4af3d751306bfd3ee6d351e8
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2019
ms.locfileid: "74298987"
---
# <a name="uml-activity-diagrams-guidelines"></a>Diagramy aktywności UML: Zalecenia
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

W programie Visual Studio możesz narysować diagram aktywności, aby opisać proces biznesowy lub algorytm oprogramowania jako przepływ pracy przez serię akcji. Te akcje mogą wykonać osoby, składniki oprogramowania lub urządzenia. Aby zapoznać się z pokazem wideo, zobacz: [przechwytywanie biznesowe przepływy pracy za pomocą diagramów aktywności](https://channel9.msdn.com/blogs/clinted/uml-with-vs-2010-part-4-capture-business-workflows).

 Aby sprawdzić, które wersje programu Visual Studio obsługują tę funkcję, zobacz [Obsługa wersji dla narzędzi architektury i modelowania](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

 Aby utworzyć diagram aktywności UML, w menu **Architektura** kliknij **Nowy UML lub diagram warstwowy**.

 Diagram aktywności można użyć w wielu celach:

- Aby opisać proces biznesowy lub przepływ pracy między użytkownikami i systemem. Aby uzyskać więcej informacji, zobacz [wymagania dotyczące modelu użytkownika](../modeling/model-user-requirements.md).

- Do opisywania kroków wykonywanych w przypadku użycia. Aby uzyskać więcej informacji, zobacz [diagramy przypadków użycia UML: wytyczne](../modeling/uml-use-case-diagrams-guidelines.md).

- Do opisywania metody, funkcji lub operacji w oprogramowaniu. Aby uzyskać więcej informacji, zobacz [modelowanie architektury aplikacji](../modeling/model-your-app-s-architecture.md).

  Rysowanie diagramu aktywności może pomóc w ulepszaniu procesu. Jeśli diagram istniejącego procesu jest bardzo skomplikowany, można rozważyć, jak można uprościć proces.

  Informacje referencyjne dotyczące elementów na diagramach aktywności można znaleźć w temacie [diagramy aktywności UML: odwołanie](../modeling/uml-activity-diagrams-reference.md).

## <a name="Relationships"></a>Relacje z innymi diagramami
 W przypadku rysowania diagramu aktywności do opisywania procesu biznesowego lub sposobu, w jaki użytkownicy korzystają z systemu, możesz narysować diagram przypadków użycia, aby pokazać inny widok tych samych informacji. Na diagramie przypadku użycia są rysowane akcje jako przypadki użycia. Nadaj przypadki użycia takie same nazwy jak odpowiadające im akcje. Zalety widoku przypadku użycia są następujące:

- Pokaż na jednym diagramie, jak większe działania/przypadki użycia składają się z mniejszych, przy użyciu relacji include.

- Połącz poszczególne akcje/przypadki użycia jawnie z użytkownikami lub systemami zewnętrznymi związanymi z jego wykonywaniem.

- Rysowanie granic wokół działań/przypadków użycia obsługiwanych przez system lub poszczególnych głównych składników.

  Możesz również narysować diagram aktywności, aby opisać szczegółowy projekt operacji oprogramowania.

  W diagramie aktywności można wyświetlić przepływ danych przesyłanych między akcjami. Zapoznaj się z sekcją [opisującą przepływ danych](#DataFlows). Jednak diagram aktywności nie opisuje struktury danych. W tym celu można narysować Diagram klas UML. Aby uzyskać informacje, zobacz [diagramy klas UML: wytyczne](../modeling/uml-class-diagrams-guidelines.md).

## <a name="BasicSteps"></a>Podstawowe kroki rysowania diagramów aktywności
 Szczegółowe instrukcje tworzenia dowolnego diagramu modelowania są opisane w sekcji [Edycja modeli UML i diagramów](../modeling/edit-uml-models-and-diagrams.md).

#### <a name="to-draw-an-activity-diagram"></a>Aby narysować diagram aktywności

1. W menu **Architektura** kliknij kolejno pozycje **Nowy UML lub diagram warstwowy**.

2. W obszarze **Szablony**kliknij pozycję **Diagram aktywności UML**.

3. Nadaj nazwę diagramowi.

4. W obszarze **Dodaj do projektu modelowania**wybierz istniejący projekt modelowania w rozwiązaniu lub **Utwórz nowy projekt modelowania**.

#### <a name="to-draw-elements-on-an-activity-diagram"></a>Aby narysować elementy na diagramie aktywności

1. Przeciągnij elementy z przybornika na diagram.

     Zacznij od umieszczenia głównych działań na diagramie, łącząc je, a następnie dodając do nich ostateczne elementy, takie jak początkowe i końcowe węzły.

    > [!NOTE]
    > Nie można przeciągać istniejących elementów na diagram z Eksploratora modelu UML.

2. Aby połączyć elementy, wykonaj następujące kroki:

    1. W przyborniku **Diagram aktywności** kliknij pozycję **Łącznik**.

    2. Na diagramie kliknij element źródłowy.

    3. Kliknij element docelowy.

        > [!NOTE]
        > Aby użyć narzędzia wiele razy, kliknij je dwukrotnie w przyborniku.

#### <a name="to-move-an-activity-to-another-package"></a>Aby przenieść działanie do innego pakietu

- W **Eksploratorze modelu UML**przeciągnij działanie do pakietu.

     \- lub-

- W **Eksploratorze modelu UML**, kliknij prawym przyciskiem myszy działanie, a następnie kliknij przycisk **Wytnij**. Następnie kliknij prawym przyciskiem myszy pakiet, a następnie kliknij przycisk **Wklej**.

    > [!NOTE]
    > Działanie będzie widoczne w Eksploratorze modelu UML tylko po dodaniu pierwszego elementu do diagramu.

## <a name="SimpleControlFlow"></a>Opisywanie przepływu sterowania
 Na diagramie aktywności opisano proces biznesowy lub algorytm oprogramowania w ramach szeregu akcji. Strzałki łączników pokazują, jak kontrolka jest przenoszona sekwencyjnie z jednej akcji do następnej. Zwykle akcja może zostać uruchomiona dopiero po zakończeniu poprzedniej akcji.

 Na poniższej ilustracji przedstawiono przykład sposobu wyświetlania sekwencji akcji zawierających akcje, łączniki, gałęzie i pętle. Każdy element jest wyjaśniony bardziej szczegółowo w poniższych sekcjach.

 ![Prosty diagram aktywności](../modeling/media/uml-actguidectrl.png "UML_ActGuideCtrl")

 Diagramy aktywności wykorzystują **Akcje** i **Łączniki** do opisywania systemu lub aplikacji jako szereg akcji z kontrolką przepływa sekwencyjnie od jednej akcji do następnego.

- Utwórz **akcję** (1) dla każdego zadania, które jest wykonywane przez użytkownika, system lub obie w obszarze współpraca.

  > [!NOTE]
  > Spróbuj opisać swój proces lub algorytm, korzystając z zaledwie kilku akcji. Możesz użyć **akcji zachowań wywołań** , aby zdefiniować poszczególne akcje bardziej szczegółowo na osobnym diagramie, zgodnie z opisem w artykule [opisywanie działań podrzędnych z akcjami zachowania wywoływania](#Subactivities).

- Upewnij się, że tytuł każdej akcji jasno wskazuje na to, co zazwyczaj osiąga.

- Połącz akcje w sekwencji z **łącznikami** (2).

- Każda akcja zakończy się przed rozpoczęciem następnej akcji w przepływie sterowania. Jeśli chcesz opisać akcje, które się nakładają, użyj **węzła rozwidlenia** , zgodnie z opisem w sekcji [współbieżne przepływy](#Concurrent).

  Mimo że diagram opisuje sekwencję akcji, nie opisuje sposobu wykonywania akcji lub sposobu przekazywania kontroli z jednej akcji do kolejnej. Jeśli diagram ma być używany do reprezentowania procesu biznesowego, może zostać przeniesiona kontrola, na przykład gdy jedna osoba wysyła wiadomość e-mail do innej osoby. W przypadku użycia diagramu do reprezentowania projektu oprogramowania kontrolka może zostać przeniesiona przez normalny przepływ wykonywania z jednej instrukcji do następnej.

### <a name="describing-decisions-and-loops"></a>Opisywanie decyzji i pętli

- Użyj **węzła decyzyjnego** (3) w celu wskazania punktu, w którym wynik decyzji wymusza następny krok. Możesz narysować dowolną liczbę ścieżek wychodzących.

- Jeśli używasz diagramu aktywności do definiowania części aplikacji, należy zdefiniować osłony (4) tak, aby były jasne, gdy każda ścieżka powinna zostać wykonana. Kliknij prawym przyciskiem myszy łącznik, kliknij pozycję **Właściwości**, a następnie w oknie **Właściwości** wpisz wartość pola **Guard** .

- Nie zawsze trzeba definiować osłony. Na przykład, jeśli używasz diagramu aktywności do opisywania procesu biznesowego lub protokołu interakcji, gałąź definiuje zakres opcji otwartych dla użytkownika lub interakcji ze składnikami.

- Użyj **węzła scalania** (5) do łączenia dwóch lub więcej alternatywnych przepływów, rozgałęzienia w **węźle decyzyjnym**.

    > [!NOTE]
    > Należy użyć **węzła scalania** do łączenia alternatywnych przepływów, zamiast przenosić przepływy w ramach akcji. W przykładzie nie będzie poprawna, aby połączyć się z węzła decyzyjnego bezpośrednio z powrotem do **Wybierz element menu**. Jest to spowodowane tym, że akcja nie zostanie uruchomiona, dopóki wątki kontroli nie dotarły do wszystkich łączników przychodzących. W związku z tym należy przenieść tylko współbieżne przepływy w ramach akcji. Aby uzyskać więcej informacji, zobacz [współbieżne przepływy](#Concurrent).

- Używaj gałęzi do opisywania pętli, jak pokazano w przykładzie.

    > [!NOTE]
    > Spróbuj zagnieżdżać pętle w dobrze uporządkowany sposób, jak w kodzie programu. W przypadku opisywania istniejącego procesu biznesowego może to ujawnić pewne możliwości w celu poprawienia go.

### <a name="starting-the-activity"></a>Uruchamianie działania
 Istnieją dwa sposoby wskazywania punktów wejścia do działania:

- **Węzeł początkowy**

     Utwórz jeden **węzeł początkowy** (6), aby wskazać pierwszą akcję działania.

     Ta metoda jest najbardziej przydatna w przypadku opisywania działania podrzędnego lub nie trzeba jawnie określać, co inicjuje działanie. Na przykład kolejność działań w ramach posiłku jasno rozpoczyna się, gdy klient uzyska zasobożernych.

- **Zaakceptuj węzeł zdarzenia**

     Utwórz **węzły zdarzeń Akceptuj**, zgodnie z opisem w sekcji [współbieżne przepływy](#Concurrent), aby wskazać początek wątku, który odpowiada na konkretne zdarzenie, takie jak dane wejściowe użytkownika. Nie dostarczaj przepływu przychodzącego do węzła. Pomijanie przepływu przychodzącego wskazuje, że wątek zostanie uruchomiony za każdym razem, gdy wystąpi zdarzenie.

     Ta metoda jest najbardziej przydatna podczas opisywania odpowiedzi na konkretne zdarzenie zewnętrzne.

### <a name="ending-the-activity"></a>Kończenie działania
 Użyj **końcowego węzła działania** (7), aby wskazać koniec działania.

- Gdy wątek kontrolki osiągnie **węzeł końcowy działania**, wszystkie akcje współbieżne i działania podrzędne działania są przerywane.

- Można użyć więcej niż jednego węzła końcowego działania, aby zmniejszyć liczbę dodatkowych łączników.

### <a name="interrupting-the-activity"></a>Przerywanie działania
 Aby opisać sposób przerwania zwykłego przepływu działania, na przykład jeśli użytkownik zdecyduje się anulować proces, można utworzyć węzeł zdarzenia akceptacji, który nasłuchuje dla tego zdarzenia. Aby uzyskać więcej informacji, zobacz sekcję [współbieżne przepływy](#Concurrent). Utwórz przepływ sterowania z tego elementu do ostatniego węzła działania (7).

### <a name="swimlanes"></a>Torów
 Czasami warto rozmieścić działania działań w obszarach odpowiadających różnym obiektom lub rolom biznesowym, które wykonują działania. Te obszary są uporządkowane w kolumnach i nazywane są *torami*.

- Użyj linii lub prostokątów z sekcji **proste kształty** w przyborniku, aby rysować ścieżki lub inne obszary.

- Aby oznaczyć każdy tor, Utwórz komentarz i ustaw jego właściwość **transparent** na **true**.

  Proste kształty nie są częścią modelu UML i nie są wyświetlane w Eksploratorze modelu UML.

## <a name="DataFlows"></a>Opisywanie przepływu danych
 Można opisać dane przekazywane i wychodzące z działania na jeden z dwóch sposobów:

- Użyj **węzła obiektu**. Jest to najprostsza metoda opisywania informacji przepływających między działaniami. Węzeł obiektu jest podobny do zmiennej w programie. Reprezentuje element, który przechowuje co najmniej jedną wartość, która przechodzi z jednej akcji do innej.

- Użyj **wyjściowego numeru PIN** i **wejściowego numeru PIN**. Ta metoda pozwala oddzielnie opisać dane wyjściowe z jednej akcji i dane wejściowe. Numery PIN są podobne do parametrów w programie. Numery PIN reprezentują porty, w których obiekty mogą wejść i opuszczają akcję.

    > [!NOTE]
    > Aby zapoznać się z omówieniem elementów użytych w tej sekcji, zobacz sekcję przepływy danych w temacie zobacz [diagramy aktywności UML: odwołanie](../modeling/uml-activity-diagrams-reference.md).

### <a name="describing-data-flow-with-object-nodes"></a>Opisywanie przepływu danych z węzłami obiektów
 Większość przepływów sterowania wykonuje dane. Na przykład przepływ danych wyjściowych z akcji "Klient zawiera szczegóły" przenosi odwołanie do adresu dostawy.

 Jeśli chcesz opisać te dane na diagramie, możesz zamienić łącznik na węzeł obiektu i dwa łączniki, jak pokazano na poniższej ilustracji.

 ![Węzły obiektów mogą wyświetlać dane przesyłane między akcjami](../modeling/media/uml-actguidedata.png "UML_ActGuideData")

 Zauważ, że prostokąty ze ściętymi wierzchołkami, takie jak towary wysyłki, reprezentują akcje, w których odbywa się przetwarzanie. Prostokąty kwadratowe, takie jak adres dostawy, reprezentują przepływ obiektów z jednej akcji do innej.

 Nadaj obiektowi nazwę, która odzwierciedla rolę węzła jako strumień lub bufor obiektów, które przepływają między akcjami.

 Można ustawić **Typ** węzła obiektu w okno właściwości. Typ może być typem pierwotnym, takim jak Integer, lub klasą, interfejsem lub wyliczeniem zdefiniowanym w diagramie klas. Na przykład można utworzyć adres dostawy klasy z atrybutami ulica, miasto i tak dalej, wraz z skojarzeniem z inną klasą o nazwie klient. Aby uzyskać więcej informacji, zobacz [diagramy klas UML: wytyczne](../modeling/uml-class-diagrams-guidelines.md).

> [!NOTE]
> Jeśli wpiszesz nazwę typu, który nie został jeszcze zdefiniowany, element zostanie dodany w obszarze **nieokreślone typy** w EKSPLORATORZE modelu UML. Jeśli następnie zdefiniujesz typ tej nazwy w diagramie klas, należy zresetować typ węzła obiektu, tak aby odnosił się do nowego typu.

#### <a name="buffering-data-in-object-nodes"></a>Buforowanie danych w węzłach obiektów
 Węzeł obiektu może działać jako bufor dla wielu obiektów. Na poniższej ilustracji przepływ sterowania pokazuje, że użytkownik może przekroczyć pętlę [Wybierz więcej] (1) wiele razy, podczas gdy wybrane elementy menu węzeł obiektu (2) gromadzi wybory użytkownika. Na koniec, gdy użytkownik zakończył swój wybór, sterowanie przechodzi do akcji Potwierdź zamówienie (3), która akceptuje pełną listę wyborów z wybranego buforu elementów menu.

 ![Buforowanie danych w węzłach obiektów](../modeling/media/uml-actguidebuffer.png "UML_ActGuideBuffer")

 Możesz określić, jak elementy w buforze są przechowywane przez ustawienie właściwości węzła obiektu:

- Ustaw właściwość **porządkowania** :

  - **Nieuporządkowany** , aby określić losową lub nieokreśloną kolejność. (Wartość domyślna).

  - **Uporządkowany** , aby określić zamówienie zgodnie z określonym kluczem.

  - **FIFO** , aby określić kolejność pierwszego w pierwszej kolejności.

  - **LIFO** , aby określić kolejność ostatniego, w pierwszej kolejności.

- Ustaw **górną granicę** właściwości, aby określić maksymalną liczbę obiektów, które mogą być zawarte w buforze. Wartość domyślna to *. Oznacza to, że nie ma żadnego limitu.

### <a name="describing-data-flow-with-input-and-output-pins"></a>Opisywanie przepływu danych za pomocą pinów wejściowych i wyjściowych
 Użyj **wyjściowego numeru PIN** i **wejściowego numeru PIN** , aby osobno opisać dane wyjściowe z jednej akcji i dane wejściowe.

 ![PIN wejściowe i wyjściowe są parametrami akcji](../modeling/media/uml-actguidepins.png "UML_ActGuidePins")

 Aby utworzyć kod PIN, kliknij pozycję **wejściowy numer PIN** lub **wyjściowy numer PIN** w przyborniku, a następnie kliknij akcję. Następnie można przenieść numer PIN wokół obwodu akcji i zmienić jego nazwę. Można tworzyć pinezki wejściowe i wyjściowe na dowolnym rodzaju akcji, w tym **Akcje wywoływania**, **Akcje operacji wywołania**, **Akcje wysyłania sygnałów**i **Akcje akceptowania zdarzeń**.

 Łącznik między dwoma pinezkami reprezentuje przepływ obiektu, tak jak przepływy do i z węzła obiektu.

 Nadaj każdemu numerowi PIN nazwę wskazującą rolę obiektów, które generuje lub akceptuje, takich jak nazwa parametru.

 Można ustawić typ obiektów transmitowanych we właściwości **Typ** . Musi to być typ utworzony na diagramie klas UML.

 Obiekty przepływające między połączonymi pinezkami muszą być zgodne w jakiś sposób. Może to być spowodowane faktem, że obiekty utworzone przez wyjściowy kod PIN należą do typu pochodnego wejściowego numeru PIN.

 Alternatywnie można określić, że przepływ obiektów obejmuje transformację, która konwertuje dane między typem wyjściowego numeru PIN a typem wejściowego numeru PIN. Najbardziej typowa transformacja tego rodzaju jedynie wyodrębnia odpowiednią część z większego typu. Przykład na rysunku oznacza istnienie transformacji, która wyodrębnia adres wysyłkowy z szczegółów zamówienia.

## <a name="Details"></a>Definiowanie akcji bardziej szczegółowo
 Oprócz używania nazwy akcji, aby wyczyścić wynik, który powinien być zwykle osiągnięty, poniżej przedstawiono kilka sposobów dodawania szczegółów do akcji:

- Napisz bardziej szczegółowy opis we właściwości **Body** . Można na przykład napisać fragment kodu programu lub pseudo kod lub pełen opis uzyskanych wyników.

- Zastąp akcję akcją zachowania wywołania i opisz jej szczegółowe zachowanie w ramach oddzielnego diagramu aktywności. Zobacz [Opis działań podrzędnych z akcjami zachowania wywoływania](#Subactivities).

- Ustaw właściwości **lokalnych warunki końcowe** i **lokalnych warunków** wstępnych akcji, aby opisać jej wynik bardziej szczegółowy. Aby uzyskać więcej informacji, zobacz [Definiowanie warunki końcowe i warunków wstępnych](#Postcondition).

### <a name="Subactivities"></a>Opisywanie działań podrzędnych z akcjami zachowania wywołania
 Można opisać szczegółowe zachowanie akcji przy użyciu oddzielnego diagramu aktywności. Zachowanie wywoływane to diagram aktywności, który jest reprezentowany na głównym diagramie aktywności przez akcję zachowania wywołania. Za pomocą akcji zachowanie wywołania można także opisać zachowanie, które jest współużytkowane przez różne działania, aby nie trzeba było wielokrotnie rysować działania podrzędne.

 Na poniższej ilustracji wykres 1 pokazuje działanie, które ma akcję zachowanie wywołania i diagram 2 przedstawia Diagram działania podrzędnego, który pokazuje wywoływane zachowanie.

 ![Oddzielny diagram aktywności przedstawia szczegółowe akcje](../modeling/media/uml-actguidedetail.png "UML_ActGuideDetail")

##### <a name="to-describe-a-sub-activity-with-a-call-behavior-action"></a>Aby opisać działanie podrzędne z akcją zachowania wywołania

1. Aby utworzyć diagram dla działania podrzędnego, w **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy projekt modelowania, wskaż polecenie **Dodaj**, a następnie kliknij pozycję **nowy element**.

2. W oknie dialogowym **Dodaj nowy element** w obszarze **Szablony** kliknij pozycję **Diagram aktywności** , a następnie w polu **Nazwa** wpisz nazwę, która ma zostać przystosowana do **akcji zachowania wywoływania**.

3. Narysuj szczegółowy przepływ pracy dla działania podrzędnego. Jest to wywołane zachowanie.

    - W przypadku wywoływanego diagramu poddziałania **początkowy węzeł** wskazuje, gdzie formant jest uruchamiany w momencie wywołania wywoływanego zachowania. **Końcowy węzeł działania** pokazuje, gdzie formant powinien powrócić do działania nadrzędnego.

4. Ustaw właściwość **Behavior** **akcji zachowanie wywołania** , aby odwoływać się do diagramu zachowań wywoływanych.

    > [!NOTE]
    > Diagram działania podrzędnego musi mieć pewne elementy lub diagram nie będzie dostępny na liście rozwijanej dla właściwości **zachowanie** . Ponadto ikona Trident nie będzie widoczna dla kształtu **akcji zachowanie wywołania** , dopóki nie ustawisz jego właściwości **Behavior** .

5. Ustaw właściwość **jest synchroniczna** akcji, aby wskazać, czy działanie czeka na zakończenie wywołanego działania.

    - Jeśli ustawisz wartość **synchroniczną** na false, wskazujesz, że przepływ może przejść do następnej akcji przed ukończeniem wywoływanego działania. Nie należy definiować pinów wyjściowych ani wychodzących przepływów danych z akcji.

### <a name="describing-data-flow-in-and-out-of-sub-activities"></a>Opisywanie przepływu danych w i poza działaniami podrzędnymi
 Można opisać dane przepływające do i z działań podrzędnych w taki sam sposób jak w przypadku używania parametrów w oprogramowaniu.

- Utwórz pinezki wejściowe i wyjściowe (1) dla wywoływanej akcji zachowań dla każdego elementu danych, który przechodzi do lub z akcji. Odpowiednio Nazwij każdy z nich.

- W diagramie działania podrzędnego Utwórz **węzeł parametru działania** (2) dla każdego wejściowego i wyjściowego numeru PIN w akcji wywołującej. Nadaj każdemu węzłowi taką samą nazwę jak odpowiedni kod PIN.

  > [!NOTE]
  > Węzeł parametru działania przypomina węzeł obiektu. Aby sprawdzić typ szukanego węzła, kliknij prawym przyciskiem myszy węzeł, a następnie kliknij polecenie **Właściwości**. Typ węzła jest wyświetlany w nagłówku okno Właściwości.

- W diagramie działania podrzędnego należy narysować łączniki pokazujące przepływ obiektów do lub z każdego węzła parametru działania.

  ![Pinezki na mapie zachowań wywołań do parametrów działania](../modeling/media/uml-actguidesub.png "UML_ActGuideSub")

### <a name="Postcondition"></a>Definiowanie warunki końcowe i warunków wstępnych
 Aby określić szczegółowo wynik akcji, można użyć **lokalnych właściwości warunki końcowe** i **lokalnych warunków** wstępnych. Te właściwości opisują efekt działania bez opisu sposobu osiągnięcia efektu.

 Aby ustawić te właściwości, kliknij prawym przyciskiem myszy akcję, a następnie kliknij pozycję **Właściwości**. Wpisz wartości we właściwościach w okno Właściwości.

#### <a name="local-postconditions"></a>Warunki końcowe lokalny
 Błąd warunku końcowego to warunek, który powinien zostać spełniony, zanim będzie można uznać akcję za ukończoną. W przykładowym potwierdzeniu akcji błąd warunku końcowego może być:

 Klient dostarczył pełne i ważne szczegóły, które są wymagane do przetworzenia karty kredytowej.

 Błąd warunku końcowego może wyrazić relację między Stanami przed i po wykonaniu akcji. Na przykład:

 Stawka odsetek jest podwójnie zawarto.

 Można napisać warunki końcowe w bardziej formalnym stylu, odwołując się do określonych atrybutów danych objętych działaniami. Na przykład:

 `InvoiceTotal == Sum(OrderItem.MenuItem.Price)`

#### <a name="local-preconditions"></a>Lokalne warunki wstępne
 Warunek wstępny to warunek, który powinien być prawdziwy, gdy akcja jest gotowa do rozpoczęcia. Na przykład akcja Potwierdź zamówienie może mieć warunek wstępny:

 Klient wybrał co najmniej jeden element z menu.

### <a name="describing-calls-to-operations"></a>Opisywanie wywołań operacji
 Ogólnie rzecz biorąc, Akcja opisuje prace wykonywane przez dowolną kombinację osób, oprogramowania lub maszyn. Można jednak użyć akcji operacji wywołania do opisania wywołania określonej metody lub funkcji oprogramowania.

- Ustaw nazwę akcji operacji wywołania, aby określić, jaka operacja jest wywoływana, oraz na jakie obiekty lub składniki.

- Dodaj numery PIN wejścia i wyjścia do akcji wywołania operacji, aby opisać parametry i wartości zwracane.

- Można ustawić właściwość **synchroniczną** akcji, aby wskazać, czy działanie czeka na ukończenie operacji.

  - Jeśli ustawisz opcję **synchroniczne** na false, wskazujesz, że przepływ może przejść do następnej akcji przed ukończeniem wywołanej operacji. Nie należy definiować pinów wyjściowych ani wychodzących przepływów danych z akcji.

## <a name="Concurrent"></a>Współbieżne przepływy
 Za pomocą **węzła rozwidlenia** i **węzła Join** można opisać dwa lub więcej wątków działań, które mogą być wykonywane w tym samym czasie.

 ![Węzły rozwidlenia i sprzęgania pokazują współbieżne przepływy](../modeling/media/uml-actguideconcurrent.png "UML_ActGuideConcurrent")

 Efekt **węzła rozwidlenia** (1) polega na podzieleniu wątku kontroli na dwa lub więcej wątków. Po zakończeniu poprzedniej akcji można uruchomić wszystkie akcje na stronie wyjście rozwidlenia.

 **Węzeł sprzężenia** (2) udostępnia współbieżne wątki. Akcja po **węźle sprzężenia** nie może się rozpocząć, dopóki nie zostaną zakończone wszystkie akcje prowadzące do **węzła Join** .

### <a name="describing-signals-and-events"></a>Opisywanie sygnałów i zdarzeń
 Możesz wyświetlić krok w procesie, który wysyła sygnał jako akcję wysłania sygnału w działaniu. Możesz wyświetlić krok czekający na konkretny sygnał lub zdarzenie, zanim krok będzie mógł kontynuować działanie jako akcję akceptowania zdarzenia.

 Można na przykład wyświetlić krok, który wysyła zamówienie, a następnie inny krok, który musi otrzymać zamówienie, przed jego przetworzeniem.

#### <a name="sending-a-signal"></a>Wysyłanie sygnału
 Użyj akcji wysyłania sygnału (3), aby wskazać, że sygnał lub komunikat pewnego rodzaju są wysyłane do innych działań lub procesów. Użyj nazwy akcji, aby określić rodzaj wysyłanego komunikatu.

- Kontrolka natychmiast przejdzie do następnej akcji w przepływie sterowania, jeśli istnieje.

- Nie można użyć akcji wysyłania sygnału, aby opisać, w jaki sposób proces reaguje na wszelkie zwrócone informacje. W tym celu należy użyć oddzielnej akcji Zaakceptuj zdarzenie.

- Możesz pokazać przepływ danych przychodzących do akcji wysyłania sygnału, aby wskazać, jakie dane mogą być wysyłane przy użyciu wiadomości wychodzącej. Aby uzyskać więcej informacji, zobacz [opisywanie przepływu danych](#DataFlows).

#### <a name="waiting-for-a-signal-or-event"></a>Oczekiwanie na sygnał lub zdarzenie
 Użyj akcji Akceptuj zdarzenie (4), aby wskazać, że to działanie oczekuje na niektóre zdarzenie zewnętrzne lub komunikat przychodzący. Użyj nazwy akcji, aby wskazać typ zdarzenia, które ma oczekiwać.

- Aby pokazać, że działanie czeka na zdarzenie zewnętrzne lub komunikat w określonym punkcie w przepływie, należy narysować akcję Akceptuj zdarzenie z przepływem przychodzącym w odpowiednim miejscu w działaniu.

- Aby pokazać, że działanie może reagować na zdarzenie zewnętrzne lub komunikat w dowolnym momencie, należy narysować akcję Zaakceptuj zdarzenie bez żadnego przepływu przychodzącego. Gdy wystąpi nazwane zdarzenie zewnętrzne, nowy wątek rozpocznie się w Twoim działaniu, rozpoczynając od akcji Zaakceptuj zdarzenie.

- Nie można użyć akcji akceptowania zdarzenia do opisywania wartości zwracanej do nadawcy sygnału. Użyj oddzielnej akcji wysyłania sygnału do tego celu.

- Można wyświetlić wychodzące przepływy danych z akcji, aby pokazać, jak działanie przetwarza dane odbierane w tym sygnale. Aby wyświetlić więcej niż jeden przepływ wyjściowy, należy ustawić właściwość **IsUnmarshall** akcji Akceptuj zdarzenie, która wskazuje, że akcja analizuje sygnał przychodzący w oddzielnych składnikach. Aby uzyskać więcej informacji, zobacz [opisywanie przepływu danych](#DataFlows).

### <a name="describing-multiple-data-flows"></a>Opisywanie wielu przepływów danych
 Można narysować więcej niż jeden przepływ sterowania lub przepływ obiektów, które wychodzą z akcji, aby wskazać, że po zakończeniu akcji zostanie przeprowadzone więcej niż jeden wątek. Efekt jest podobny do rozwidlenia, z tą różnicą, że można użyć kombinacji przepływów sterowania i obiektów.

 Poniższy przykład pokazuje wiele przepływów z i do akcji.

 ![Równoległe przepływy obiektów](../modeling/media/uml-actguidemulti.png "UML_ActGuideMulti")

 Gdy akcja "Klient zawiera szczegóły" zostanie ukończona, generowane są dwa obiekty: "adres wysyłkowy" i "szczegóły karty kredytowej". Dwa obiekty przechodzą do przodu w celu przetworzenia przez różne akcje.

 Ponieważ akcja wymaga, aby wszystkie dane wejściowe były dostępne przed rozpoczęciem, Ostatnia akcja nie zostanie uruchomiona, dopóki nie zostaną ukończone wszystkie akcje prowadzące do niej.

### <a name="streams"></a>Strumienie
 Możesz użyć diagramu aktywności, aby pomóc opisać potok lub serię akcji wykonywanych w tym samym czasie, i ciągle przekazywać dane z jednej akcji do innej.

 Zamierzenie w poniższym przykładzie polega na tym, że poszczególne akcje mogą generować obiekty i kontynuować pracę. Ponieważ nie ma przepływów sterowania, każda akcja może zacząć się zaraz po odebraniu jej pierwszych obiektów.

 Należy zauważyć, że łączniki w tym przykładzie są przepływami obiektów, ponieważ wszystkie mają co najmniej jeden koniec w węźle parametru działania, w węźle obiektu lub w numerze PIN danych wejściowych lub wyjściowych.

 ![Przepływ danych](../modeling/media/uml-actguidestream.png "UML_ActGuideStream")

 1. Przykład ma trzy węzły parametrów działania, które reprezentują dane wejściowe i wyjściowe.

 2. Węzły obiektów, numery PIN wejściowe i numery PIN wyjściowe mogą reprezentować bufory. Można ustawić górną granicę właściwości węzła obiektu, aby określić, ile obiektów może znajdować się w buforze w tym samym czasie.

 3. Można użyć węzłów decyzyjnych, aby pokazać, że strumień jest podzielony, wysyłając różne obiekty w dół w różnych gałęziach. Możesz użyć komentarzy lub tytułów węzłów, aby wyjaśnić, co to jest kryterium dzielenia.

 4. Można użyć węzłów rozwidlenia, aby pokazać, że co najmniej dwie kopie obiektów są wykonywane, wysyłając je do współbieżnego przetwarzania.

 5. Można użyć węzłów sprzężenia, aby pokazać, że dwa strumienie przetwarzania są scalane z powrotem w jeden.

### <a name="selection-and-transformation"></a>Wybór i transformacja
 Można określić, że obiekty w przepływie obiektów są przekształcane, wybierane lub oba. Przepływ obiektów jest przepływem do lub z kodu PIN lub z węzła obiektu.

- Przekształcenie opisuje sposób, w jaki obiekty wchodzące w przepływ są konwertowane na inny typ.

- Wybór opisuje, w jaki sposób tylko niektóre obiekty wchodzące w skład przepływu są przesyłane do akcji przejmującej.

  W przykładzie pokazano przekształcenie. Pierwsza akcja na diagramie 1 generuje kod pocztowy lub kod pocztowy w wyjściowym numerze PIN. Jest to połączenie z wejściowym numerem PIN dla drugiej akcji. Natomiast druga akcja oczekuje w pełni określonego adresu. Konwersja z jednego typu na inny jest określona w drugim działaniu, wyszukiwanie adresu. Jest to przywoływane z właściwości przekształcenia przepływu obiektów. Działanie wyszukiwania adresów zawiera jeden węzeł parametru działania dla przychodzącego kodu pocztowego oraz inny węzeł parametru działania dla wychodzącego pełnego adresu.

  ![Transformacja obiektu zdefiniowana w innym diagramie](../modeling/media/uml-actguidetransform.png "UML_ActGuideTransform")

  Można określić przekształcenie lub wybór na dwa sposoby:

- Dołącz komentarz do wejściowego lub wyjściowego numeru PIN.

  - Aby odróżnić ten opis od komentarza ogólnego, można rozpocząć dodawanie komentarza\<**transformacji**> > lub **<\<<** >.

- Określ szczegóły transformacji lub wyboru w oddzielnym diagramie aktywności.

  - Jeśli używasz tej metody, Dołącz komentarz również, aby był oczywisty dla czytelników, że transformacja została zdefiniowana.

##### <a name="to-specify-a-transformation-or-selection-in-a-separate-activity-diagram"></a>Aby określić przekształcenie lub zaznaczenie na osobnym diagramie aktywności

1. Utwórz nowy Diagram działania, w którym ma zostać opisany przepływ transformacji lub wyboru.

   - W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy projekt, wskaż polecenie **Dodaj**, kliknij pozycję **nowy element**, a następnie kliknij pozycję **Diagram aktywności**. Nadaj diagramowi odpowiednią nazwę dla przepływu transformacji lub zaznaczenia. Kliknij przycisk **Dodaj**.

2. Na nowym diagramie:

   1. Utwórz dwa węzły parametrów działania, jeden dla przepływu wejściowego i jeden dla danych wyjściowych.

   2. Twórz akcje połączone z przepływami obiektów. Pokazuje, jak działa transformacja lub zaznaczenie.

3. Na dowolnym diagramie, w którym chcesz użyć przekształcenia lub zaznaczenia:

   1. Utwórz przepływ obiektów, czyli łącznik do lub z Pinu wejściowego lub wyjściowego, węzeł obiektu lub węzeł parametru działania.

   2. Kliknij prawym przyciskiem myszy przepływ obiektów, a następnie kliknij polecenie **Właściwości**.

   3. We właściwości **przekształcanie** lub **wybór** Wybierz diagram, w którym został określony przepływ przekształcania lub zaznaczania.

   Można również zdefiniować wybór dla węzła obiektu i dla poszczególnych pinów wejściowych i wyjściowych. Zdefiniuj działanie wyboru jako w poprzedniej procedurze, a następnie ustaw właściwość **zaznaczania** węzła obiektu lub wejściowy lub wyjściowy numer PIN.

## <a name="see-also"></a>Zobacz też
 [Edycja modeli UML i diagramów](../modeling/edit-uml-models-and-diagrams.md) [diagramów sekwencji UML: referencyjne](../modeling/uml-sequence-diagrams-reference.md) [diagramy składników UML](../modeling/uml-component-diagrams-reference.md) : referencyjne diagramy [przypadków użycia UML](../modeling/uml-use-case-diagrams-reference.md) : referencyjne diagramy [klas UML: referencyjne](../modeling/uml-class-diagrams-reference.md) [diagramy składników UML](../modeling/uml-component-diagrams-reference.md) : [film wideo: Przechwytywanie biznesowe przepływy pracy za pomocą diagramów aktywności](https://channel9.msdn.com/blogs/clinted/uml-with-vs-2010-part-4-capture-business-workflows)
