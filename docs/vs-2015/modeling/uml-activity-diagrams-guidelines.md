---
title: 'Diagramy aktywności UML: Wytyczne dotyczące | Dokumentacja firmy Microsoft'
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
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 310e13e781997fd3a6431e4257918f8e61b9420d
ms.sourcegitcommit: 75807551ea14c5a37aa07dd93a170b02fc67bc8c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/11/2019
ms.locfileid: "67823577"
---
# <a name="uml-activity-diagrams-guidelines"></a>Diagramy aktywności UML: Wytyczne dotyczące
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

W programie Visual Studio można narysować diagram aktywności, aby opisują proces biznesowy lub algorytm oprogramowania jako przepływ pracy za pomocą szeregu akcji. Te akcje można wykonać osób, składniki oprogramowania lub urządzeń. Aby uzyskać demonstracyjne wideo – zobacz: [Przechwytywanie biznesowe przepływy pracy za pomocą diagramów aktywności](http://channel9.msdn.com/posts/clinted/UML-with-VS-2010-Part-4-Capture-Business-Workflows/).  
  
 Aby zobaczyć, które wersje programu Visual Studio obsługuje tę funkcję, zobacz [obsługiwana wersja dla narzędzia architektury i modelowania](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).  
  
 Aby utworzyć diagram aktywności UML na **architektury** menu, kliknij przycisk **nowe UML lub diagramu warstwowego**.  
  
 Diagram aktywności można użyć do wielu celów:  
  
- Opis procesu biznesowego przepływu pracy między użytkownikami a systemem. Aby uzyskać więcej informacji, zobacz [modelowanie wymagań użytkowników](../modeling/model-user-requirements.md).  
  
- Do opisania czynności wykonywanych w przypadku użycia. Aby uzyskać więcej informacji, zobacz [diagramy przypadków użycia UML: Wytyczne dotyczące](../modeling/uml-use-case-diagrams-guidelines.md).  
  
- Do opisania metody, funkcja lub operacja w oprogramowaniu. Aby uzyskać więcej informacji, zobacz [modelowanie architektury aplikacji](../modeling/model-your-app-s-architecture.md).  
  
  Rysowanie diagramu aktywności może pomóc ulepszyć proces. Diagram istniejący proces okaże się, że bardzo skomplikowane, można rozważyć, jak można uprościć proces.  
  
  Aby uzyskać informacje na temat elementów na diagramach aktywności, zobacz [diagramy aktywności UML: Odwołanie](../modeling/uml-activity-diagrams-reference.md).  
  
## <a name="Relationships"></a> Relacja z innymi diagramami  
 Możesz narysować diagram aktywności, aby opisać proces biznesowy oraz sposób, w którym użytkownicy korzystania z systemu, można narysować diagram przypadków użycia, aby wyświetlić inny widok tych samych informacji. Diagram przypadków użycia służy do rysowania akcje zgodnie z przypadkami użycia. Nadaj przypadków użycia takich samych nazwach jak odpowiednich akcji. Korzyści wynikające z widoku przypadków użycia są, możesz:  
  
- Pokaż w jednym diagramie jak większych akcji/zastosowań składają się z mniejszych, przy użyciu relacji obejmuje.  
  
- Każdy przypadek użycia akcji jawnie połączyć się z użytkowników lub systemów zewnętrznych, które są zaangażowane w jej wykonanie.  
  
- Rysuj granice wokół akcji/zastosowań obsługiwanych przez system lub każdego głównego składnika.  
  
  Możesz również narysować diagram aktywności, aby opisać projekt szczegółowe działania oprogramowania.  
  
  Na diagramie aktywności można pokazać przepływ danych przesyłanych między akcjami. Zobacz sekcję dotyczącą [opisujący przepływ danych](#DataFlows). Ale diagram aktywności nie opisano strukturę danych. W tym celu możesz narysować diagram klas UML. Aby uzyskać informacje, zobacz [diagramów klas UML: Wytyczne dotyczące](../modeling/uml-class-diagrams-guidelines.md).  
  
## <a name="BasicSteps"></a> Podstawowe kroki rysowania diagramów aktywności  
 Szczegółowe kroki tworzenia dowolnego diagramu modelowania zawiera są opisane w [modeli i diagramów UML Edytuj](../modeling/edit-uml-models-and-diagrams.md).  
  
#### <a name="to-draw-an-activity-diagram"></a>Aby narysować diagram aktywności  
  
1. Na **architektury** menu, kliknij przycisk **nowe UML lub diagramu warstwowego**.  
  
2. W obszarze **szablony**, kliknij przycisk **Diagram aktywności UML**.  
  
3. Nadaj nazwę diagramowi.  
  
4. W **Dodaj do projektu modelowania**, wybierz istniejący projekt modelowania w rozwiązaniu, lub **Utwórz nowy projekt modelowania**.  
  
#### <a name="to-draw-elements-on-an-activity-diagram"></a>Aby narysować elementy na diagramie aktywności  
  
1. Przeciągnij elementy z przybornika do diagramu.  
  
     Rozpocznij od wprowadzania główne czynności na diagramie, łącząc je, a następnie dodając wprowadzania ostatecznych poprawek, takich jak węzłów początkowych i końcowych.  
  
    > [!NOTE]
    > Nie można przeciągać istniejące elementy na diagram, z Eksploratora modelu UML.  
  
2. Aby połączyć elementy, wykonaj następujące kroki:  
  
    1. W **Diagram aktywności** przybornik, kliknij przycisk **łącznika**.  
  
    2. Na diagramie kliknij element źródła.  
  
    3. Kliknij element docelowy.  
  
        > [!NOTE]
        > Aby użyć narzędzia wielokrotnie, kliknij dwukrotnie narzędzie w przyborniku.  
  
#### <a name="to-move-an-activity-to-another-package"></a>Aby przenieść działanie do innego pakietu  
  
- W **Eksploratora modelu UML**, przeciągnij działanie w pakiecie.  
  
     \- lub —  
  
- W **Eksploratora modelu UML**, kliknij prawym przyciskiem myszy działanie i kliknij przycisk **Wytnij**. Następnie kliknij prawym przyciskiem myszy pakiet i kliknij przycisk **Wklej**.  
  
    > [!NOTE]
    > Działania będą wyświetlane w Eksploratorze modelu UML tylko po dodaniu pierwszego elementu na diagram.  
  
## <a name="SimpleControlFlow"></a> Opisywanie przepływu sterowania  
 Diagram aktywności opisuje algorytm procesu lub oprogramowania firmy jako szereg działań. Łącznik strzałki pokazują, jak kontrola jest przekazywana sekwencyjnie w ramach jednej akcji do następnego. Zazwyczaj akcji można uruchomić tylko po poprzedniej akcji.  
  
 Następujący rysunek jest przykładem przedstawiającym sposób możesz wyświetlić sekwencję akcji przy użyciu akcji, łączniki, gałęzie i pętle. Każdy element jest omówione bardziej szczegółowo w poniższych sekcjach.  
  
 ![Diagram prostego działania](../modeling/media/uml-actguidectrl.png "UML_ActGuideCtrl")  
  
 Działanie diagramy użycia **akcje** i **łączników** do opisania systemie lub w aplikacji jako szereg działań z kontrolką przepływają sekwencyjnie od jednej akcji do następnego.  
  
- Tworzenie **akcji** (1) dla każdego zadania główne, które jest wykonywane przez użytkownika i/lub system we współpracy.  
  
  > [!NOTE]
  > Spróbuj opis procesu algorytmu, gdy tylko kilka akcji. Możesz użyć **wywołać akcje zachowania** do definiowania każdej akcji w bardziej szczegółowo w oddzielnym diagramie, zgodnie z opisem w [opisujące działań podrzędnych za pomocą wywołania akcji zachowanie](#Subactivities).  
  
- Upewnij się, że tytuł każdej akcji jasno nie wskazuje, co powoduje to zazwyczaj osiągnięcie.  
  
- Łącze akcji w sekwencji **łączników** (2).  
  
- Każda akcja kończy się przed rozpoczęciem następnej akcji w przepływie sterowania. Jeśli użytkownik chce opisać akcje, które nakładają się na siebie, należy użyć **węzła rozwidlenia** zgodnie z opisem w sekcji [przepływy współbieżne](#Concurrent).  
  
  Mimo że na wykresie przedstawiono sekwencję akcji, nie opisano sposób wykonywania akcji lub jak sterowanie jest przekazywane z jedną akcję do następnego. Jeśli używasz diagramu do reprezentowania proces biznesowy kontroli mogą być przekazywane, na przykład, gdy jedna osoba wysyła wiadomość e-mail do innego. Jeśli używasz diagramu do reprezentowania projektu oprogramowania kontrolki mogą być przekazywane przy normalnym przepływem wykonania z jedną instrukcję do następnego.  
  
### <a name="describing-decisions-and-loops"></a>Opisujące decyzji i pętle  
  
- Użyj **węzła decyzji** (3), aby wskazać punkt, gdzie wynik decyzji decyduje o następnym krokiem. Możesz narysować dowolną liczbę ścieżek wychodzących.  
  
- Użycie diagram aktywności zdefiniować część aplikacji, należy zdefiniować osłony (4), aby było wiadomo, gdy są każdą ścieżkę należy podjąć. Kliknij prawym przyciskiem myszy łącznik, kliknij przycisk **właściwości**, a następnie w **właściwości** okna i wpisz wartość **Guard** pola.  
  
- Nie zawsze jest konieczne w celu zdefiniowania osłony. Na przykład w przypadku opisują proces biznesowy lub protokołu interakcji przy użyciu diagramu aktywności, gałąź definiuje zakres możliwości do użytkownika, lub ze składnikami interakcje.  
  
- Użyj **scalania węzła** (5), aby zebrać co najmniej dwóch alternatywnych przepływów, które rozgałęzione w **węzła decyzji**.  
  
    > [!NOTE]
    > Należy używać **scalania węzła** ze sobą alternatywnych przepływów, zamiast łączące przepływów w akcji. W tym przykładzie nie jest poprawna połączyć się z węzłem decyzji bezpośrednio z powrotem do **wybierz element Menu**. Jest to spowodowane akcji nie uruchamia się, dopóki wątków kontroli mogły przybyć wszystkich przychodzących łączników. W związku z tym można należy zebrać tylko przepływy współbieżne w akcji. Aby uzyskać więcej informacji, zobacz [przepływy współbieżne](#Concurrent).  
  
- Używanie gałęzi do opisania pętli, jak pokazano w przykładzie.  
  
    > [!NOTE]
    > Spróbuj zagnieździć pętli w sposób bezpieczny dobrze, jak w przypadku w kodzie programu. Jeśli są opisujące istniejący proces biznesowy, to może ujawnić niektóre możliwości poprawienia go.  
  
### <a name="starting-the-activity"></a>Uruchamianie działania  
 Istnieją dwa sposoby, aby wskazać punkty wejścia do działania:  
  
- **Węzeł początkowy**  
  
     Utwórz je **węzeł początkowy** (6), aby wskazać pierwszą akcję działania.  
  
     Ta metoda jest najbardziej użyteczne, są opisujących działania podrzędne lub w przypadku, gdy nie trzeba jawnie określać, jakie inicjuje działania. Na przykład działanie zamówienie posiłku wyraźnie rozpoczyna się, gdy klient pobiera hungry.  
  
- **Zaakceptuj węzła zdarzeń**  
  
     Tworzenie **zaakceptować węzłów zdarzeń**, zgodnie z opisem w sekcji [przepływy współbieżne](#Concurrent), aby wskazać uruchomienia wątku, który odpowiada na konkretne zdarzenie, takie jak dane wejściowe użytkownika. Nie wpisuj przychodzącego przepływu do węzła. Pominięcie przychodzącego przepływu wskazuje, czy wątek zostanie uruchomiony każdym wystąpieniu zdarzenia.  
  
     Ta metoda jest najbardziej przydatne, gdy opisują odpowiedzi na określone zdarzenie zewnętrzne.  
  
### <a name="ending-the-activity"></a>Kończenie działania  
 Użyj **działania ostatni węzeł** (7), aby wskazać koniec działania.  
  
- Gdy wątek kontroli osiągnie **działania ostatni węzeł**, zakończyć współbieżnych akcje i działania podrzędne wszystkich działań.  
  
- Więcej niż jeden węzeł końcowy działanie umożliwia zaśmiecać dodatkowe łączniki.  
  
### <a name="interrupting-the-activity"></a>Przerywania działania  
 Do opisywania, jak zwykłe przepływ działania może zostać przerwane, na przykład, jeśli użytkownik zdecyduje anulować proces, można utworzyć zaakceptować węzeł zdarzeń, który będzie nasłuchiwać pod kątem tego zdarzenia. Aby uzyskać więcej informacji, zobacz sekcję [przepływy współbieżne](#Concurrent). Utwórz przepływ sterowania od tego działania węzłem końcowym (7).  
  
### <a name="swimlanes"></a>Torów  
 Czasami jest to przydatne dla operacji działania do obszarów różnych obiektów lub ról biznesowych, wykonujące akcje. Te obszary tradycyjnie są rozmieszczone w kolumnach i są nazywane *torów*.  
  
- Użyj linie lub prostokąty z **kształty proste** sekcji przybornika Rysowanie ścieżek albo innych obszarów.  
  
- Aby dodać etykietę każdego toru, utworzyć komentarz i ustawić jej **przezroczysty** właściwości **True**.  
  
  Kształty proste nie stanowią części modelu UML i nie są wyświetlane w Eksploratorze modelu UML.  
  
## <a name="DataFlows"></a> Opisujący przepływ danych  
 Możesz opisać dane, przekazywanie i działania w jeden z dwóch sposobów:  
  
- Użyj **obiektu węzła**. Jest to najprostsza metoda opisujący dane przepływają między działaniami. Węzeł obiektu przypomina zmiennej w programie. Reprezentuje coś, co przechowuje jedną lub więcej wartości, które przechodzi do innego w ramach jednej akcji.  
  
- Użyj **Pin wyjściowy** i **wprowadzania numeru Pin**. Ta metoda umożliwia oddzielnie opisują dane wyjściowe z akcji i dane wejściowe do innego. Numery PIN są podobne parametry w programie. Numery PIN reprezentują porty, których obiekty można wprowadzać i pozostaw akcji.  
  
    > [!NOTE]
    > Omówienie elementy używane w tej sekcji, zobacz przepływu danych w sekcji tego tematu zobacz [diagramy aktywności UML: Odwołanie](../modeling/uml-activity-diagrams-reference.md).  
  
### <a name="describing-data-flow-with-object-nodes"></a>Opisujący przepływ danych za pomocą węzłów obiektowych  
 Większość przepływów sterowania przesyłania danych. Na przykład przepływ danych wyjściowych z akcji "Klienta zawiera szczegółowe informacje" zawiera odwołanie do adresu do wysyłki.  
  
 Do opisania tych danych na diagramie, możesz zastąpić łącznika z węzeł obiektu i dwa łączniki, jak pokazano na poniższej ilustracji.  
  
 ![Węzły obiektów można wyświetlić danych przesyłanych między akcjami](../modeling/media/uml-actguidedata.png "UML_ActGuideData")  
  
 Należy zauważyć, że prostokąty zaokrąglonymi narożnikami, takich jak towarów wysyłania reprezentują działań, gdzie występuje przetwarzanie. Prostokąty prostokątnych narożnikach, takie jak adres dostawy reprezentują przepływ obiektów z jedną akcję do innego.  
  
 Nazwij węzeł obiektu odzwierciedlającą rolę węzła kanał lub buforu obiektów, które przepływ między działaniami.  
  
 Możesz ustawić **typu** węzła obiektu, w oknie dialogowym właściwości. Typ może być typem pierwotnym, takie jak liczba całkowita, lub klasą, interfejsem lub wyliczenie, które zostały zdefiniowane na diagramie klasy. Na przykład można utworzyć klasy adres dostawy z atrybutami adres ulicy, miejscowości i tak dalej, wraz z skojarzenia z innej klasy, który nosi nazwę klienta. Aby uzyskać więcej informacji, zobacz [diagramów klas UML: Wytyczne dotyczące](../modeling/uml-class-diagrams-guidelines.md).  
  
> [!NOTE]
> Wpisz nazwę typu, który nie został jeszcze zdefiniowany element zostanie dodany w obszarze **nieokreślonym** w Eksploratorze modelu UML. Po zdefiniowaniu typu o takiej nazwie następnie na diagramie klasy, możesz zresetować typ węzła obiektu, dzięki czemu odwołuje się do nowego typu.  
  
#### <a name="buffering-data-in-object-nodes"></a>Buforowanie danych w węzłów obiektowych  
 Węzeł obiektu może działać jako bufor dla wielu obiektów. Na poniższej ilustracji, przepływ sterowania pokazuje, że użytkownik może go [Więcej opcji] pętli (1) wiele razy, podczas gdy elementy Menu wybrany węzeł obiektu (2) gromadzi wyborów użytkownika. Na koniec po ukończeniu jego wybór użytkownika kontrola przechodzi do akcji potwierdzenia zamówienia (3), która przyjmuje pełną listę wyboru z buforu wybrane elementy Menu.  
  
 ![Buforowanie danych w węzłach obiektów](../modeling/media/uml-actguidebuffer.png "UML_ActGuideBuffer")  
  
 Można określić, jak elementy w buforze są przechowywane przez ustawienie właściwości węzeł obiektu:  
  
- Ustaw **porządkowanie** właściwości:  

  - **Nieuporządkowana** do określania kolejności losowej lub nieokreślony. (Ustawienie domyślne)  

  - **Uporządkowane** można określić kolejność, zgodnie z określonym kluczem.  

  - **FIFO** do określania kolejności pierwszy w zasadzie.  

  - **LIFO** do określania kolejności ostatni na wejściu,.  

- Ustaw **górną granicę** właściwość, aby określić maksymalną liczbę obiektów, które mogą być zawarte w buforze. Wartość domyślna to *. Oznacza to, że nie ma żadnego limitu.  
  
### <a name="describing-data-flow-with-input-and-output-pins"></a>Opisujący przepływ danych z wejścia i wyjścia  
 Użyj **Pin wyjściowy** i **wprowadzania numeru Pin** oddzielnie opisujący dane wyjściowe z akcji i dane wejściowe do innego.  
  
 ![PinY wejściowe i wyjściowe są parametry akcji](../modeling/media/uml-actguidepins.png "UML_ActGuidePins")  
  
 Aby utworzyć numer pin, kliknij przycisk **wprowadzania numeru Pin** lub **Pin wyjściowy** w przyborniku a następnie kliknij akcję. Można następnie przenieść numeru pin na obwodzie akcji i zmień jego nazwę. Można tworzyć dane wejściowe i wyjściowe pinterest na dowolny rodzaj działania, w tym **wywołać akcje zachowania**, **wywołaj operację akcje**, **wysyłać sygnał akcje**, i  **Zaakceptuj akcje zdarzenia**.  
  
 Łącznik między dwa numery PIN reprezentuje przepływ obiektu, tak jak przepływy do i z węzeł obiektu.  
  
 Nadaj każdej numeru pin nazwę, która wskazuje rolę obiektów produkuje lub zaakceptuje, takie jak nazwa parametru.  
  
 Możesz ustawić typ obiektów przekazywane w **typu** właściwości. Musi to być typ, który został utworzony w diagramie klas UML.  
  
 Obiekty odbywającym się między połączonych numerów PIN musi być zgodny w jakiś sposób. Może to być, ponieważ obiekty produkowane przez danych wyjściowych numer pin należy do typu pochodnego typu wprowadzania numeru pin.  
  
 Alternatywnie można określić, że przepływ obiektu zawiera przekształcenia, które konwertuje dane między typ danych wyjściowych numer pin i typ wprowadzania numeru pin. Najbardziej typowe przekształcania tego rodzaju wyodrębnia tylko odpowiednie części z większych typu. Przykład pokazany na rysunku oznacza to istnienie transformacji, która wyodrębnia adresu wysyłkowego z szczegółów zamówienia.  
  
## <a name="Details"></a> Definiowanie akcji bardziej szczegółowo  
 Oprócz przy użyciu nazwy akcji, aby wyjaśnić, wynik, który zazwyczaj powinna osiągnąć, Oto kilka sposobów akcję można dodać więcej szczegółów:  
  
- Pisanie bardziej szczegółowy opis w **treści** właściwości. Na przykład można napisać fragment kodu programu lub pseudo kod lub pełny opis osiągnięte rezultaty.  
  
- Zamień akcji do wywołania akcji zachowanie i opisano jego szczegółowe zachowanie w diagramie aktywności na oddzielne. Zobacz [zawierająca opis działania podrzędne z akcjami zachowanie wywołania](#Subactivities).  
  
- Ustaw akcję **lokalnych warunków końcowych** i **lokalnego warunki wstępne** właściwości opisujących jej wynik szczegółowo bardziej szczegółowe. Aby uzyskać więcej informacji, zobacz [Definiowanie warunków końcowych i warunki wstępne](#Postcondition).  
  
### <a name="Subactivities"></a> Opisujący działania podrzędne z akcjami zachowanie wywołania  
 Możesz opisać szczegółowe zachowanie operacji za pomocą diagramu aktywności na oddzielne. O nazwie zachowanie jest przedstawione na diagramie głównego działania przez akcję zachowania wywołać diagram aktywności. Wywołanie zachowanie służy również do opisywania zachowanie współużytkowanych przez różne działania, aby nie masz do rysowania działania podrzędne wiele razy.  
  
 Na poniższym rysunku na diagramie 1 przedstawiono działanie, które zawiera akcję zachowanie wywołania i Diagram 2 przedstawia diagram aktywności podrzędną, która pokazuje zachowanie o nazwie.  
  
 ![Diagram oddzielnych działania pokazujący szczegółowe akcje](../modeling/media/uml-actguidedetail.png "UML_ActGuideDetail")  
  
##### <a name="to-describe-a-sub-activity-with-a-call-behavior-action"></a>Do opisania podrzędne działania przy użyciu akcji zachowanie wywołania  
  
1. Aby utworzyć diagram działania podrzędne w **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy projekt modelowania, wskaż **Dodaj**, a następnie kliknij przycisk **nowy element**.  
  
2. W **Dodaj nowy element** okno dialogowe, w obszarze **szablony** kliknij **Diagram aktywności** i **nazwa** wpisz nazwę, który chcesz nadać Twoje **wywołanie zachowanie**.  
  
3. Rysuj przepływ pracy szczegółowe dla działania podrzędne. Jest to zachowanie o nazwie.  
  
    - Na diagramie aktywności podrzędną o nazwie **węzeł początkowy** wskazuje, gdzie kontrola rozpoczyna się po wywołaniu o nazwie zachowanie. **Działania ostatni węzeł** pokazuje, gdzie kontrolka powinna zwrócić do działania nadrzędnego.  
  
4. Ustaw **zachowanie** właściwość **wywołanie zachowanie** do odwoływania się do diagramu o nazwie zachowanie.  
  
    > [!NOTE]
    > Diagram aktywności podrzędne muszą mieć niektóre elementy na nim lub diagram nie będą dostępne na liście rozwijanej **zachowanie** właściwości. Ponadto trident ikony nie będą wyświetlane na Twojej **wywołanie zachowanie** kształtu, dopóki nie zostanie ustawiony jego **zachowanie** właściwości.  
  
5. Ustaw **jest synchroniczne** właściwość akcji, aby wskazać, czy Twoje działanie ma oczekiwać na zakończenie działania o nazwie.  
  
    - Jeśli ustawisz **jest synchroniczne** na wartość false, wskazujesz, że przepływ może w dalszym następnej akcji przed zakończeniem działania o nazwie. Dane wyjściowe nie powinna definiować numerów PIN lub dane wychodzące przepływy z akcji.  
  
### <a name="describing-data-flow-in-and-out-of-sub-activities"></a>Opisujący przepływ danych i działania podrzędne  
 Możesz opisać dane przepływające pojęcie działania podrzędne w taki sam sposób, jak używać parametrów w oprogramowaniu.  
  
- Tworzenie wejściowych i wyjściowych kody PIN (1) w przypadku akcji o nazwie zachowanie, dla każdego z nich dane, które przechodzą do lub z akcji. Nazwa każdego z nich odpowiednio.  
  
- Na diagramie aktywności podrzędnych, należy utworzyć **węzła parametru działania** (2) dla każdego wejściowe i wyjściowe numeru pin w przypadku wywoływania akcji. Nadaj każdy węzeł taką samą nazwę jak odpowiedni numer pin.  
  
  > [!NOTE]
  > Węzeł parametru działania przypomina węzeł obiektu. Aby sprawdzić, jakiego rodzaju węzeł, który jest wyświetlany, kliknij prawym przyciskiem myszy węzeł, a następnie kliknij przycisk **właściwości**. Typ węzła jest wyświetlany w nagłówku w oknie właściwości.  
  
- Na diagramie aktywności podrzędnych narysuj łączników, które pokazują przepływ obiektów do i z każdego węzła parametru działania.  
  
  ![Przypina zachowanie wywołań na mapie w celu parametry działań](../modeling/media/uml-actguidesub.png "UML_ActGuideSub")  
  
### <a name="Postcondition"></a> Definiowanie warunków końcowych i warunków wstępnych  
 Możesz użyć **lokalnych warunków końcowych** i **lokalnego warunki wstępne** właściwości, aby określić szczegóły wyniku akcji. Te właściwości opisują efekt działania bez opisujące, jak to osiągnąć efekt.  
  
 Aby ustawić te właściwości, kliknij ją prawym przyciskiem myszy, a następnie kliknij przycisk **właściwości**. Wpisz wartości do właściwości w oknie dialogowym właściwości.  
  
#### <a name="local-postconditions"></a>Lokalne warunków końcowych  
 Postcondition jest warunek, który powinien być spełnione, zanim akcja jest uznawana za ukończone. Przykład akcji Potwierdź zamówienia może być postcondition:  
  
 Klient udostępnił kompletny i ważne szczegółowe informacje, które są wymagane do przetwarzania jej karty kredytowej.  
  
 Postcondition można wyrazić relację między stanami, przed i po przeprowadzeniu akcji. Na przykład:  
  
 Oprocentowanie jest double sprzed.  
  
 Styl formalnej, można napisać warunków końcowych odwołujące się do określonych atrybutów danych omówione w akcjach. Przykład:  
  
 `InvoiceTotal == Sum(OrderItem.MenuItem.Price)`  
  
#### <a name="local-preconditions"></a>Warunki wstępne lokalne  
 Warunkiem wstępnym jest warunek, który musi mieć wartość true, gdy akcja jest gotowy do rozpoczęcia. Na przykład akcja potwierdzenia zamówienia może mieć warunki wstępne:  
  
 Klient wybierze co najmniej jeden element menu.  
  
### <a name="describing-calls-to-operations"></a>Opisujące wywołania operacji  
 Ogólnie rzecz biorąc Akcja opis pracy wykonywanej przez dowolnej kombinacji osób, oprogramowania lub maszyn. Jednak można użyć do wywołania operacji akcji do opisania wywołanie metody określone oprogramowanie lub funkcji.  
  
- Ustaw nazwę akcji operacji wywołania do wskazania, jakie działania jest nazywany i jakie obiektu lub składnika.  
  
- Dodaj PinY wejściowe i wyjściowe do wywołania operacji akcji do opisywania parametry i zwracane wartości.  
  
- Możesz ustawić **jest synchroniczne** właściwość akcji, aby wskazać, czy Twoje działanie ma oczekiwać na zakończenie operacji.  
  
  - Jeśli ustawisz **jest synchroniczne** na wartość false, wskazujesz, że przepływ może w dalszym następnej akcji przed ukończeniem operacji o nazwie. Dane wyjściowe nie powinna definiować numerów PIN lub dane wychodzące przepływy z akcji.  
  
## <a name="Concurrent"></a> Przepływy współbieżne  
 Możesz użyć **węzła rozwidlenia** i **dołączyć węzła** do opisania dwa lub więcej wątków działań, które mogą być wykonywane w tym samym czasie.  
  
 ![Węzły rozwidlenia i sprzężenia Pokaż przepływy współbieżne](../modeling/media/uml-actguideconcurrent.png "UML_ActGuideConcurrent")  
  
 Efekt **węzła rozwidlenia** (1) jest podzielić wątku kontroli na dwa lub więcej wątków. Po zakończeniu poprzedniej akcji, można uruchomić wszystkie akcje po stronie dane wyjściowe rozwidlenia.  
  
 A **dołączyć węzła** (2) gromadzi współbieżnych wątków. Akcję po **dołączyć węzła** może rozpocząć się do wszystkich akcji, co prowadzi do **dołączyć węzła** są kompletne.  
  
### <a name="describing-signals-and-events"></a>Opisujące sygnały i zdarzenia  
 Możesz wyświetlić krok w procesie, który wysyła sygnał jako akcję wysyłania sygnału w działaniu. Możesz wyświetlić kroku, który oczekuje dla określonego sygnału lub zdarzeń, aby kontynuować ten krok jako Zaakceptuj akcję zdarzenia.  
  
 Na przykład możesz wyświetlać kroku, który wysyła zamówienia, a następnie kolejny krok, który musi odebrać kolejności, zanim przetworzy on tej kolejności.  
  
#### <a name="sending-a-signal"></a>Wysyła sygnał  
 Użyj Wyślij akcji sygnałów (3), aby wskazać, sygnału lub komunikat pewnego rodzaju są wysyłane do innych działań lub procesów. Nazwa akcji umożliwia wskazanie, jaki rodzaj komunikat o wysyła.  
  
- Kontrola przechodzi bezpośrednio do następnego działania w przepływie sterowania jeśli taka istnieje.  
  
- Wysyłać sygnał akcji nie można użyć do opisywania sposobu proces na wszystkie zwrócone informacje. Aby to zrobić, należy użyć oddzielnych Zaakceptuj akcję zdarzenia.  
  
- Możesz wyświetlić przychodzący przepływ danych do wysyłania sygnału akcji, aby wskazać, jakie dane mogą być wysyłane z komunikatu wychodzącego. Aby uzyskać więcej informacji, zobacz [opisujący przepływ danych](#DataFlows).  
  
#### <a name="waiting-for-a-signal-or-event"></a>Oczekuje na sygnał lub zdarzenie  
 Zaakceptuj akcję zdarzenia (4) umożliwia wskazanie, że to działanie czeka, aż niektóre zdarzenia zewnętrznego lub komunikatu przychodzącego. Użyj nazwy akcji, aby wskazać typ zdarzenia, które oczekuje na.  
  
- Aby pokazać, że działania czeka na zdarzenie zewnętrzne lub komunikatów w określonym punkcie w jego przepływu, narysuj Zaakceptuj akcję zdarzenia z przychodzący przepływ w odpowiednim miejscu w ramach działania.  
  
- Aby pokazać, że swoje działania mogą odpowiadać na zdarzenie zewnętrzne lub wiadomości w dowolnym momencie, narysuj Zaakceptuj akcję zdarzenia bez żadnych przepływów przychodzących. W przypadku nazwanych zewnętrznego zdarzenia nowy wątek rozpocznie się w swojej działalności, zaczynając od Zaakceptuj akcję zdarzenia.  
  
- Zaakceptuj akcję zdarzenia nie można użyć do opisania każda wartość zwracana przez nadawcę sygnału. Użyj osobnej akcji wysyłać sygnał do tego celu.  
  
- Możesz wyświetlić wychodzące przepływy danych od akcji, aby pokazać, w jaki sposób działania przetwarza dane odebrane w sygnale. Jeśli chcesz wyświetlić więcej niż jeden przepływ danych wyjściowych, należy ustawić **IsUnmarshall** właściwość Zaakceptuj akcję zdarzenia, co oznacza akcję analizowania przychodzących sygnałów na jego osobne składniki. Aby uzyskać więcej informacji, zobacz [opisujący przepływ danych](#DataFlows).  
  
### <a name="describing-multiple-data-flows"></a>Opisu danych wiele przepływów  
 Możesz narysować więcej niż jeden przepływ sterowania lub przepływ obiektu pochodzącemu z akcji, aby wskazać, że więcej niż jeden wątek wynika, po zakończeniu działania. Efekt jest podobny, rozwidlenia, z tą różnicą, że możesz użyć kombinacji przepływów sterowania i obiektu.  
  
 Poniższy przykład przedstawia wiele przepływów z i do działań.  
  
 ![Równoległe przepływy obiektów](../modeling/media/uml-actguidemulti.png "UML_ActGuideMulti")  
  
 Po ukończeniu akcji "Klienta zawiera szczegółowe informacje" tworzy dwa obiekty: "Wydanie address" i "Szczegóły karty kredytowej." Dwa obiekty przejść do przodu do przetworzenia przez różne akcje.  
  
 Ponieważ akcji wymaga wszystkie jego danych wejściowych była dostępna, zanim będzie można ją uruchamiać, ostatnia akcja nie można uruchomić dopiero po zakończeniu wszystkich akcji, które mogą prowadzić do niego.  
  
### <a name="streams"></a>Strumienie  
 Diagram aktywności można użyć opisu potoku lub szereg działań, które są wykonywane w tym samym czasie i stale przekazywania danych z jednej akcji do innego.  
  
 W poniższym przykładzie jest aby każda akcja generują obiektów i kontynuować pracę. Ponieważ nie zawiera żadnych przepływów sterowania, każdej akcji można uruchomić zaraz po odebraniu jej pierwszym obiektów.  
  
 Zauważ, że łączników w tym przykładzie są przepływach obiektu, ponieważ wszystkie one mają co najmniej jeden z punktów końcowych w węźle parametru działania, węzeł obiektu lub dla danych wejściowych lub numeru Pin w danych wyjściowych.  
  
 ![Przepływ danych](../modeling/media/uml-actguidestream.png "UML_ActGuideStream")  
  
 1. W przykładzie przedstawiono trzy węzły parametru działania, które reprezentują ich dane wejściowe i wyjściowe.  
  
 2. Węzły obiektów, pinów wejścia i wyjścia może reprezentować buforów. Możesz ustawić górną granicę właściwość węzeł obiektu do stanu obiektów ile może być w buforze, w tym samym czasie.  
  
 3. Węzły decyzji można użyć, aby pokazać, że dzieli strumienia, wysyłania różnych obiektów rozgałęzienia innej. Aby wyjaśnić, dzieląc kryterium jest, można użyć komentarze lub tytuły węzłów.  
  
 4. Można używać rozwidlenia węzłów, aby pokazać, czy dwie lub więcej kopii, obiekty zostaną wprowadzone, wysyłając na równoczesne przetwarzanie.  
  
 5. Można używać łączenia węzłów, aby pokazać, że dwa strumienie przetwarzania są scalane z powrotem jeden.  
  
### <a name="selection-and-transformation"></a>Wybór i przekształcenia  
 Można określić, że obiekty w przepływie obiektu są przekształcane, zaznaczone, lub obu. Przepływ obiektu jest przepływu z numeru pin lub węzeł obiektu.  
  
- Przekształcenia w tym artykule opisano sposób konwertowania obiektów, wprowadzając przepływ do innego typu.  
  
- Wybór w tym artykule opisano sposób tylko niektóre obiekty, wprowadzając przepływ są przekazywane do odbierania akcji.  
  
  W przykładzie pokazano przekształcenie. Pierwszą akcją w diagramie 1 generuje kod pocztowy lub kod pocztowy numeru pin w danych wyjściowych. To jest podłączony do wprowadzania numeru pin w drugiej akcji. A w przypadku drugiej akcji adresu pełni określona. Konwersja z jednego typu na inny jest określona w drugie działanie wyszukiwania na podstawie adresu. To jest wywoływany przez właściwość przekształcania przepływu obiektu. Działanie wyszukiwania na podstawie adresu zawiera jeden węzeł parametru aktywności dla przychodzących kodu pocztowego i wychodzących pełny adres innego węzła parametru działania.  
  
  ![Obiekt transformacji zdefiniowanych w innym diagramie](../modeling/media/uml-actguidetransform.png "UML_ActGuideTransform")  
  
  Przekształcenia lub wyboru można określić na dwa sposoby:  
  
- Dołącz komentarz do kodu pin wejściowych lub wyjściowych.  
  
  - Aby rozróżnić tego opisu, od ogólnego komentarza, można rozpocząć komentarz z <\<**przekształcania**>> lub <\<**wybór**>>.  
  
- Szczegółowo w diagramie aktywności na oddzielne, należy określić przekształcania lub zaznaczenia.  
  
  - Użycie tej metody, należy również dołączyć komentarz do ułatwiają Wyczyść, aby czytelnicy zdefiniowano transformacji.  
  
##### <a name="to-specify-a-transformation-or-selection-in-a-separate-activity-diagram"></a>Aby określić przekształcania lub zaznaczenia w diagramie aktywności na oddzielne  
  
1. Utwórz nowy Diagram aktywności, w którym opisuje przepływ przekształcenia lub zaznaczenia.  
  
   - W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy projekt, wskaż **Dodaj**, kliknij przycisk **nowy element**, a następnie kliknij przycisk **Diagram aktywności**. Nadaj diagramu odpowiednią nazwę przepływu przekształcania lub zaznaczenia. Kliknij przycisk **Dodaj**.  
  
2. Na nowym diagramie:  
  
   1. Utwórz dwa węzły parametru działania: jeden dla danych wejściowych przepływu i jeden dla danych wyjściowych.  
  
   2. Tworzenie akcji, połączone ze sobą przy użyciu obiektu przepływów. Pokazuje, jak działa transformacja lub zaznaczenia.  
  
3. W dowolny diagram, w której chcesz używać przekształcania lub zaznaczenie:  
  
   1. Utwórz przepływ obiektu, oznacza to, że łącznik do lub z danych wejściowych lub numeru pin w danych wyjściowych, węzeł obiektu lub węzłem parametru działania.  
  
   2. Kliknij prawym przyciskiem myszy obiekt przepływu, a następnie kliknij przycisk **właściwości**.  
  
   3. W **przekształcania** lub **wybór** właściwości, wybierz diagram, gdzie określone Przepływ przekształcenia lub zaznaczenia.  
  
   Można również zdefiniować wybór dla węzła obiektu, a także na poszczególne dane wejściowe i dane wyjściowe numerów PIN. Zdefiniuj działania zaznaczenia, tak jak w poprzedniej procedurze, a następnie ustaw **wybór** właściwość węzeł obiektu lub danych wejściowych lub wyjściowych numer pin.  
  
## <a name="see-also"></a>Zobacz też  
 [Edytowanie modeli i diagramów UML](../modeling/edit-uml-models-and-diagrams.md)   
 [Diagramy sekwencji UML: Odwołanie](../modeling/uml-sequence-diagrams-reference.md)   
 [Diagramy składników UML: Odwołanie](../modeling/uml-component-diagrams-reference.md)   
 [Diagramy przypadków użycia UML: Odwołanie](../modeling/uml-use-case-diagrams-reference.md)   
 [Diagramy klas UML: Odwołanie](../modeling/uml-class-diagrams-reference.md)   
 [Diagramy składników UML: Odwołanie](../modeling/uml-component-diagrams-reference.md)   
 [Wideo: Przechwytywanie biznesowe przepływy pracy za pomocą diagramów aktywności](http://channel9.msdn.com/posts/clinted/UML-with-VS-2010-Part-4-Capture-Business-Workflows/)
