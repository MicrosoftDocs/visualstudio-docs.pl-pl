---
title: 'Diagramy sekwencji UML: Wytyczne dotyczące | Dokumentacja firmy Microsoft'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
f1_keywords:
- vs.teamarch.sequencediagram.linktosequencediagram
- vs.teamarch.logicalclassdiagram.createlifeline
- vs.teamarch.componentdiagram.createlifeline
helpviewer_keywords:
- diagrams - modeling, sequence
- sequence diagrams
- UML diagrams, sequence
- interactions, UML
- diagrams - modeling, UML sequence
- UML interactions
- UML, sequence diagrams
- UML sequence diagrams
- behaviors, UML
ms.assetid: 5990ef7c-ba60-4e20-a36d-e29c1fa6c8bb
caps.latest.revision: 55
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: a38d9b354de528797d0044f7b631bd2287c34fb4
ms.sourcegitcommit: 75807551ea14c5a37aa07dd93a170b02fc67bc8c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/11/2019
ms.locfileid: "67823563"
---
# <a name="uml-sequence-diagrams-guidelines"></a>Diagramy sekwencji UML: Wytyczne dotyczące
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

W programie Visual Studio, można narysować *diagram sekwencji* do przedstawiania interakcji. Interakcja to sekwencję wiadomości między wystąpieniami typowych klas, składników, podsystemów lub podmiotów.  
  
 Diagramy sekwencji UML są częścią modelu UML i istnieją tylko w projektach modelowania UML. Aby utworzyć diagram sekwencji UML, na **architektury** menu, kliknij przycisk **nowe UML lub diagramu warstwowego**. Dowiedz się więcej o [elementów diagramu sekwencji UML](../modeling/uml-sequence-diagrams-reference.md) lub [diagramów modelowania UML](../modeling/edit-uml-models-and-diagrams.md) ogólnie rzecz biorąc. Aby obejrzeć wideo demonstracyjne, zobacz [powstawać interakcje za pomocą diagramów sekwencji (2010)](http://channel9.msdn.com/Blogs/clinted/UML-with-VS-2010-Part-7-Sketching-Interactions-with-Sequence-Diagrams).  
  
 Aby zobaczyć, które wersje programu Visual Studio obsługuje tę funkcję, zobacz [obsługiwana wersja dla narzędzia architektury i modelowania](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).  
  
## <a name="in-this-topic"></a>W tym temacie:  
 [Za pomocą diagramów sekwencji UML](#Using)  
  
 [Podstawowe kroki rysowania diagramów sekwencji](#BasicSteps)  
  
 [Tworzenie i używanie prostych diagramy sekwencji](#Simple)  
  
 [Klasy i linii życia](#ClassesAndLifelines)  
  
 [Tworzenie sekwencji interakcji wielokrotnego użytku](#Multiple)  
  
 [Zwijanie grup linii życia](#Collapse)  
  
 [Opisujące struktury sterujące przy użyciu fragmentów](#Fragments)  
  
## <a name="Using"></a> Za pomocą diagramów sekwencji UML  
 Możesz użyć diagramów sekwencji do różnych celów, na różnych poziomach szczegółowości program. Typowe sytuacje rysowania diagramu sekwencji, są następujące:  
  
- Jeśli masz diagram przypadków użycia, która zawiera podsumowanie systemu, użytkowników i ich celów, możesz narysować diagramy sekwencji do opisywania sposobu interakcji główne składniki systemu do zrealizowania celu każdego przypadku użycia. Aby uzyskać więcej informacji, zobacz [diagramy przypadków użycia UML: Wytyczne dotyczące](../modeling/uml-use-case-diagrams-guidelines.md).  
  
- Po zidentyfikowaniu komunikatów przychodzących inny interfejs składnika można narysować diagramy sekwencji do opisywania sposobu interakcji wewnętrznych części składnika, aby uzyskać ten efekt, wymagany dla każdego komunikatu przychodzącego. Aby uzyskać więcej informacji, zobacz [diagramy składników UML: Wytyczne dotyczące](../modeling/uml-component-diagrams-guidelines.md).  
  
  Rysowanie diagramów sekwencji ma kilka zalet:  
  
- Można łatwo zobaczyć, jak zadania są dystrybuowane między składnikami.  
  
- Można zidentyfikować wzorce interakcji, które utrudniają aktualizacji oprogramowania.  
  
## <a name="relationship-to-other-diagrams"></a>Relacja z innymi diagramami  
 Można użyć diagramów sekwencji UML wraz z innymi diagramami na kilka sposobów.  
  
#### <a name="lifelines-and-types"></a>Linie życia i typów  
 Linie życia, rysowane na diagramie sekwencji może reprezentować typowe wystąpień składnikami lub klasami w Twoim systemie. Tworzenie linii życia na podstawie typów i typów z linii życia i Pokaż typów w diagramach przypadków UML i diagramy składników UML. Aby uzyskać więcej informacji, zobacz [klasy i linie życia](#ClassesAndLifelines).  
  
#### <a name="parameter-types"></a>Typy parametrów  
 Można również opisać w diagramie klas UML typy parametrów i zwracane wartości, które były używane w wiadomościach przesyłanych między liniami życia.  
  
#### <a name="use-case-details"></a>Szczegóły przypadku użycia  
 Przypadek użycia przedstawia cel użytkownika, wraz z sekwencji kroków do osiągnięcia celu. Sekwencja kroków można przedstawić na kilka sposobów. Jedną z opcji jest, aby narysować diagram sekwencji, który pokazuje interakcje występujące między użytkownikami a główne składniki systemu. Aby uzyskać więcej informacji, zobacz [diagramy przypadków użycia UML: Wytyczne dotyczące](../modeling/uml-use-case-diagrams-guidelines.md).  
  
## <a name="BasicSteps"></a> Podstawowe kroki rysowania diagramów sekwencji  
 Aby uzyskać pełną listę elementów na diagramach sekwencji, zobacz [UML Sequence Diagrams: Odwołanie](../modeling/uml-sequence-diagrams-reference.md).  
  
> [!NOTE]
> Szczegółowe informacje na temat sposobu tworzenia dowolnego diagramu modelowania zawiera są opisane w [modeli i diagramów UML Edytuj](../modeling/edit-uml-models-and-diagrams.md).  
  
#### <a name="to-create-a-sequence-diagram"></a>Aby utworzyć diagram sekwencji  
  
1. Na **architektury** menu, kliknij przycisk **nowe UML lub diagramu warstwowego**.  
  
2. W obszarze **szablony**, kliknij przycisk **Diagram sekwencji UML**.  
  
3. Nadaj nazwę diagramowi.  
  
4. W **Dodaj do projektu modelowania**, wybierz istniejący projekt modelowania w rozwiązaniu, lub **Utwórz nowy projekt modelowania**, a następnie kliknij przycisk **OK**.  
  
    Pojawi się nowy diagram sekwencji **Diagram sekwencji** przybornika. Przybornik zawiera wymagane elementy i łączniki.  
  
   ![Części diagramu sekwencji](../modeling/media/uml-sequence.png "UML_Sequence")  
  
#### <a name="to-draw-a-sequence-diagram"></a>Aby narysować diagram sekwencji  
  
1. Przeciągnij **linii życia** (1) z **przybornika** na niego przeciągnięte do reprezentowania wystąpień klas, składników, aktorów lub urządzeń.  
  
    > [!NOTE]
    > Możesz również utworzyć linię życia, przeciągając istniejącej klasy, interfejsu aktora lub składnika z **Eksploratora modelu UML** na diagram. Spowoduje to utworzenie linii życia, reprezentujący wystąpienie wybranego typu.  
  
2. Narysuj wiadomości, aby pokazać, jak linie życia współpracują w celu osiągnięcia określonego celu.  
  
     Aby utworzyć komunikat, (3, 4, 6, 7), kliknij narzędzie komunikatu. Następnie kliknij przycisk wysyłania linii życia w punkcie, w którym komunikat, aby rozpocząć, a następnie kliknij odbieranie linii życia.  
  
     Wystąpienie wykonania (5) pojawia się na odbieranie linii życia. Wystąpienie wykonania reprezentuje okres, podczas którego wystąpienie jest wykonywanie metody. Możesz utworzyć inne komunikaty, rozpoczynające się od wystąpienia wykonywania.  
  
3. Aby wyświetlić komunikat, który pochodzi z nieznanego źródła zdarzenia (9) lub emituje do nieznanego odbiorcy (10), narysuj komunikatów asynchronicznych z lub do pustego obszaru na diagramie. Komunikaty te są nazywane *znalezione wiadomości* (9) i *utracone wiadomości* (10).  
  
    > [!NOTE]
    > Aby przenieść grupę linii życia zawierającą utracone lub znalezione wiadomość, wykonaj następujące kroki, aby wybrać linie życia, przed przeniesieniem ich: Narysuj prostokąt wokół tych linii życia, lub naciśnij i przytrzymaj klawisz **CTRL** klucza podczas klikania każda linia życia. Jeśli używasz **Zaznacz wszystko** lub **CTRL**+**A** do zaznaczenia wszystkich linii życia, a następnie przenieś je, wszystkie utracone i znalezione wiadomości dołączone do tych linii życia, nie zostaną przeniesione. Jeśli wystąpi taka sytuacja, te wiadomości można przenosić oddzielnie.  
  
4. Narysuj diagramy sekwencji dla każdego komunikatu głównych do tego samego składnika lub systemu.  
  
#### <a name="to-change-the-order-of-messages"></a>Aby zmienić kolejność komunikatów  
  
- Przeciągnij wiadomość w górę lub w dół w jego życia. Można przeciągnąć go za pośrednictwem innych wiadomości, lub na lub poza blokiem wykonywania.  
  
     \- lub —  
  
- Kliknij komunikat, a następnie użyć **Strzałka w górę** i **strzałkę w dół** klucze, aby dostosować położenie wiadomości. Użyj **SHIFT + Strzałka w górę** i **SHIFT + Strzałka w dół** Aby zmienić kolejność komunikatów.  
  
#### <a name="to-move-or-copy-message-sequences-on-the-sequence-diagram"></a>Do przeniesienia lub skopiowania sekwencjami wiadomości na diagramie sekwencji  
  
1. Kliknij prawym przyciskiem myszy komunikat (3, 4), a następnie kliknij przycisk **kopiowania**.  
  
2. Kliknij prawym przyciskiem myszy wystąpienie wykonywania (5) lub linii życia (1), z którego chcesz się nowa wiadomość do wysłania, a następnie kliknij przycisk **Wklej**. Nowy nadawca może być na innym diagramie, jeśli chcesz.  
  
     Kopię wiadomości i jego uzupełniające wiadomości zostanie dodany na końcu wystąpienie wykonywania lub na końcu linii życia.  
  
    > [!NOTE]
    > Wklejony zawsze pojawi się na końcu wystąpienie wykonywania lub linii życia. Po wklejeniu go przeciągnąć go do wcześniej pozycji.  
  
#### <a name="to-display-and-edit-the-signature-text-for-a-message"></a>Aby wyświetlić i edytować tekst podpisu dla wiadomości  
  
- Docelowe linie życia musi być powiązany lub mapowane na typy tekst podpisu była widoczna. Aby wykonać to zadanie, wykonaj jedną z następujących czynności:  
  
  - Kliknij prawym przyciskiem myszy linii życia, a następnie wybierz **Utwórz klasę**.  
  
     —lub—  
  
  - Wybierz linii życia, naciśnij klawisz **F4**, a następnie w polu **właściwości** oknie **typu** właściwości do istniejącego typu, lub określ nazwę dla nowego typu. Kliknij prawym przyciskiem myszy Etykieta wiadomości, a następnie wybierz **operacji tworzenia**.  
  
    Tekst podpisu pojawia się poniżej etykiety wiadomości. Teraz możesz edytować tekst podpisu. Aby uzyskać więcej informacji, zobacz [klasy i linie życia](#ClassesAndLifelines).  
  
#### <a name="to-improve-the-layout-of-a-sequence-diagram"></a>Aby poprawić układ diagramu sekwencji  
  
- Kliknij prawym przyciskiem myszy pustą część diagramu, a następnie kliknij przycisk **Zmień rozmieszczanie układu**.  
  
- Aby cofnąć operację, kliknij przycisk **Edytuj**, a następnie kliknij przycisk **Cofnij**.  
  
#### <a name="to-change-the-package-that-owns-the-interaction"></a>Aby zmienić pakiet, który jest właścicielem interakcji  
  
1. W **Eksploratora modelu UML**, Znajdź interakcji, które są wyświetlane na diagramie sekwencji.  
  
    > [!NOTE]
    > Interakcja nie będą widoczne w **Eksploratora modelu UML** do momentu dodania pierwszej linii życia do diagramu sekwencji.  
  
2. Przeciągnij interakcję do pakietu.  
  
     \- lub —  
  
     Kliknij prawym przyciskiem myszy interakcji, a następnie kliknij przycisk **Wytnij**. Kliknij prawym przyciskiem myszy pakiet, a następnie kliknij przycisk **Wklej**.  
  
## <a name="Simple"></a> Tworzenie i używanie prostych diagramy sekwencji  
 Najprostszy i najbardziej powszechnie używany postaci diagramu sekwencji zawiera tylko linii życia i wiadomości. Diagram tego rodzaju umożliwia wyraźnego pokazania typowe sekwencja interakcji między obiektami w projekcie lub między systemem i jej użytkownikach. Często jest wystarczająco, aby pomóc w omawianiu i komunikowaniu projektu.  
  
 Oto kilka rzeczy, które należy uwzględnić podczas rysowania od prostego diagramu sekwencji.  
  
### <a name="types-of-message"></a>Typy komunikatu  
 Istnieją trzy narzędzia, których można użyć do utworzenia wiadomości.  
  
- Użyj **synchroniczną** narzędzie, opisujący interakcji, w którym nadawcy czeka na odbiorcy, do zwracania odpowiedzi (3).  
  
     A  **< \<zwracają >>** strzałki będą wyświetlane na końcu wystąpienie wykonywania. Oznacza to, powrót sterowania do nadawcy.  
  
- Użyj **asynchroniczne** narzędzie, opisujący interakcji, w którym nadawca może natychmiast kontynuować bez oczekiwania na odbiorcy (4).  
  
- Użyj **Utwórz** narzędzie, opisujący interakcji, w którym nadawca tworzy odbiorcy (8).  
  
     Komunikat utworzenia powinien być pierwszy komunikat, który odbiera odbiornika.  
  
### <a name="annotating-the-interactions"></a>Dodawanie adnotacji do interakcji  
 Aby opisać więcej szczegółów o kolejności, można umieścić **komentarz** dowolnym miejscu na diagramie.  
  
 Za pomocą **łącza do komentarzy**, możesz połączyć komentarz z linii życia, liczba wykonań, zastosowania interakcji i fragmenty.  
  
> [!CAUTION]
> Jeśli chcesz dołączyć komentarz do określonego punktu w sekwencji, połączyć wystąpienie wykonywania wykorzystanie interakcji lub fragmentu. Nie odsyłaj go do linii życia, ponieważ w takim przypadku on być dołączone w momencie poprawne w sekwencji.  
  
 Użyj komentarz:  
  
- Należy pamiętać, zdobyła w kluczowych punktach w sekwencji. Dzięki temu odbiorcy, aby zobaczyć, z uwzględnieniem określonych celów interakcji.  
  
- Opisz ogólnym celem całej sekwencji. Dołącz komentarz do wystąpienia wykonywania początkowej lub pozostaw to pole odłączone. Na przykład "Customer wybrał elementów menu i podano ceny".  
  
- Opisano obowiązki poszczególnych linii życia. Dołącz komentarz do linii życia. Na przykład "kolejność Manager gromadzi informacje o opcje menu klienta."  
  
- Należy pamiętać, wyjątki lub rozwiązań alternatywnych, wykonanych jako alternatywę dla typowej sekwencji wyświetlane. Na przykład "klienta można pominąć resztę tej sekwencji."  
  
  - Należy rozważyć użycie fragmentów bardziej formalne alternatywę do tego rodzaju Uwaga. Zobacz [opisujące struktury sterujące przy użyciu fragmentów](#Fragments)  
  
## <a name="deciding-the-scope-of-the-diagram"></a>Przy wyborze rozwiązania zakres diagramu  
 Należy być niejasne, o jaki diagram jest przeznaczony do wyświetlenia.  
  
#### <a name="initiating-event"></a>Zdarzenie inicjujące  
 Każdy diagram powinny pokazywać sekwencja interakcji, która wynika z jednego zdarzenia inicjujący. Może to być na przykład:  
  
- Użytkownika, na przykład inicjowanie przypadek użycia, Otwieranie strony sieci Web kupowania posiłek.  
  
- Komunikat ze składnika jednego systemu do innego, na przykład podczas badania dostępności elementów, które odbiorca chce kupić.  
  
- Zdarzenie wyzwalany przez zmianę stanu, na przykład zasobów elementu objętego poniżej wartości progowej.  
  
#### <a name="level-of-detail"></a>Poziom szczegółowości  
 Diagramy sekwencji można wyświetlić różne poziomy szczegółowości. Możesz zdecydować, poziomu szczegółowości w dwóch wymiarach oddzielne prawie niezależnie:  
  
 Linie życia może reprezentować jedną z tych poziomów szczegółowości:  
  
- Obiekty w kodzie programu, których istnieje lub jest tworzona.  
  
- Składniki lub ich podskładniki zwykle pominięcie fasad, serwery proxy i innych mechanizmów połączeń.  
  
- System i aktorów  
  
  Komunikaty mogą reprezentować jedną z tych poziomów szczegółowości:  
  
- Oprogramowanie wiadomości w kodzie programu, na interfejs API lub interfejsu sieci Web.  
  
- Transakcje i podrzędnych, na przykład między użytkownikami a system lub między kodem i bazy danych.  
  
- Użyj przypadków - główna interakcje między użytkownikami i systemu.  
  
  Ty analizujesz istniejącego kodu czy opisujące nowy projekt, jest często przydatny do rysowania i omawiania mniej szczegółowe widoki.  
  
## <a name="describing-variations"></a>Opisujące zmian  
 Na diagramie przedstawiono pojedynczy, typowe sekwencja zdarzeń. Jeśli chcesz wyświetlić alternatywne możliwości, takie jak scenariuszy awarii, możesz użyć jednej z tych opcji:  
  
- Narysować diagramy sekwencji oddzielnych do opisania tych scenariuszy  
  
- Użyj [opisujące struktury sterujące przy użyciu fragmentów](#Fragments) do wyświetlenia pętli, alternatywy i tak dalej.  
  
## <a name="assessing-the-design"></a>Ocena projektu  
 Diagram można użyć do oceny podział zadań między jej obiektów lub składniki. Jeśli widzisz te wzorce, należy rozważyć refaktoryzacji:  
  
- Do wszystkiego, wywołaniach wszystko inne, natomiast inne linie życia tylko odpowiadają pasywnie jest prawdopodobnie jedną linię życia.  
  
- Wiele komunikatów między liniami życia. Każda linia życia powinien wysyłać komunikaty do kilku sąsiadów i nie powinien komunikować się z jego sąsiadami sąsiadów. Zazwyczaj powinno być możliwe przeprowadzenie linie życia, tak aby były tylko kilku miejscach, w której wiadomości między liniami życia; a w przypadku przejazdów docelowej linii życia nie powinien również wymienić wiadomości, które mają przecinające linii życia.  
  
- Niektóre linie życia wydają się obsługiwać więcej niż jeden typ zadania. Proste należy znaleźć jedno zdanie zwięzły, które opisano obowiązki poszczególnych linii życia, podsumowanie pracę, którą robi w odpowiedzi na każdy komunikat, który odbiera.  
  
## <a name="ClassesAndLifelines"></a> Klasy i linii życia  
 Linie życia, diagramy sekwencji Pokaż wystąpień klas lub interfejsów składnika. Możesz nazwać linię życia na dwa sposoby:  
  
|**W tym celu**|**Użyj tego formatu**|  
|--------------------------|-------------------------|  
|Wystąpienie typu anonimowego.<br /><br /> Użyj tego, jeśli masz tylko jedną linię życia dla każdego typu.|*typeName*|  
|Nazwane wystąpienie typu.<br /><br /> Użyj, jeżeli chcesz pokazać sekwencji, która obejmuje więcej niż jedno wystąpienie tego samego typu.|*Nazwa obiektu*:*typeName*|  
  
### <a name="creating-lifelines-from-types"></a>Tworzenie linii życia z typami  
 Możesz utworzyć nowe linie życia z klas, które zostały już zdefiniowane, na przykład na diagramie klasy.  
  
> [!NOTE]
> Upewnij się, że masz istniejący diagram sekwencji, przed uruchomieniem tego zadania.  
  
##### <a name="to-create-a-lifeline-from-an-existing-type"></a>Aby utworzyć linię życia z istniejącego typu  
  
- Przeciągnij klasy, składnika lub interfejs z Eksploratora modelu UML na diagram sekwencji.  
  
   \- lub —  
  
  1. Kliknij prawym przyciskiem myszy klasę, składnika lub interfejsu na jego odpowiednich diagramu, a następnie kliknij przycisk **Utwórz linię życia**.  
  
  2. W **Utwórz linię życia** okno dialogowe, wybierz diagram sekwencji, a następnie kliknij przycisk **OK**.  
  
     Nowe wystąpienia o nazwie linii życia pojawi się, którego typem jest typ, który został przeciągnięty.  
  
  > [!NOTE]
  > Możesz powtórzyć tę akcję dowolną liczbę razy. Spowoduje to utworzenie linii życia przy użyciu innej nazwy.  
  
##### <a name="to-change-the-type-of-a-lifeline"></a>Aby zmienić typ linii życia  
  
1. Kliknij prawym przyciskiem myszy linię życia, a następnie kliknij przycisk **właściwości**.  
  
2. W **właściwości** oknie **typu** właściwości. Możesz wybrać typ z menu rozwijanego lub wpisz nową nazwę.  
  
### <a name="creating-classes-from-lifelines"></a>Tworzenie klas z linii życia  
 Po utworzeniu jeden lub więcej diagramów sekwencji można podsumować linie życia, tworząc z nich klas lub interfejsów.  
  
##### <a name="to-create-a-class-or-interface-from-a-lifeline"></a>Aby utworzyć klasę lub interfejs z linii życia  
  
1. Kliknij prawym przyciskiem myszy linii życia, a następnie kliknij przycisk **Utwórz klasę** lub **Utwórz interfejs**.  
  
     Nową klasę lub interfejs pojawi się w Eksploratorze modelu UML.  
  
2. Operacje tworzenia klasy lub interfejsu dla każdego komunikatu, który odbiera linii życia:  
  
    1. Zaznacz wszystkie komunikaty, które mają zostać uwzględnione.  
  
    2. Kliknij prawym przyciskiem myszy jeden z komunikatów, a następnie kliknij przycisk **tworzenie**.  
  
         Nową klasę lub interfejs ma operacji dla każdego wybranego komunikatu.  
  
         Nazwa operacji jest wyświetlana poniżej Strzałka każdego komunikatu, a następnie w **operacji** właściwość komunikatu.  
  
         Jeśli wiadomość zawiera parametry w formie "(parameter: type)", pojawią się one na liście parametrów nową operację.  
  
        > [!NOTE]
        > Ten krok należy powtórzyć po dodaniu nowych komunikatów w diagramie sekwencji.  
  
3. Aby wyświetlić szczegóły nowej klasy lub interfejsu, należy go dodać do diagramu klasy lub składnika.  
  
    1. Otwórz lub Utwórz diagram klasy lub składnika.  
  
    2. Przeciągnij nową klasę lub interfejs z **Eksploratora modelu UML** do diagramu klas.  
  
         Klasy lub interfejsu pojawia się na diagramie klasy.  
  
         \- lub —  
  
    3. Przeciągnij nowy interfejs z **Eksploratora modelu UML** na składnik lub port na diagramie składników.  
  
         Interfejs jako lizak pojawia się w składniku.  
  
### <a name="creating-classes-for-parameters"></a>Tworzenie klas dla parametrów  
 Parametry można uwzględnić w komunikatach na diagramie sekwencji. Można użyć diagramu klas UML do opisania typy parametrów.  
  
## <a name="Multiple"></a> Tworzenie sekwencji interakcji wielokrotnego użytku  
 Diagram oddzielnych służy do opisania sekwencji, który zawiera szczegóły przewidzianą do oddzielenia lub jest wspólne kilka diagramów.  
  
 Prostokąt wykorzystanie interakcji (12) można tworzyć na jednym diagramie, wskazujący na szczegóły na innym diagramie.  
  
 Kliknij dwukrotnie wykorzystanie interakcji, aby otworzyć diagram sekwencji, która jest połączona.  
  
#### <a name="to-create-a-reusable-interaction-sequence-from-existing-lifelines"></a>Aby utworzyć sekwencję wielokrotnego użytku interakcji z istniejącej linii życia  
  
1. W **przybornika**, kliknij przycisk **wykorzystanie interakcji**.  
  
2. Na diagramie sekwencji przytrzymując przycisk myszy przeciąganie linii życia, które mają zostać uwzględnione w sekwencji wielokrotnego użytku. Uruchom, w którym ma zostać wstawiony wykorzystanie interakcji położenie w pionie.  
  
     Wykorzystanie interakcji jest wyświetlana w wybranych linii życia w diagramie sekwencji.  
  
3. Kliknij dwukrotnie nazwę na wykorzystanie interakcji i zmień jej nazwę na opisano wpływ wielokrotnego użytku kolejność, w tym diagramie.  
  
     \- lub —  
  
     Wpisz nazwę, np. wywołanie funkcji z parametrami.  
  
4. Połącz wykorzystanie interakcji z innego diagramu sekwencji. Kliknij prawym przyciskiem myszy wykorzystanie interakcji, a następnie:  
  
     Kliknij przycisk **Utwórz nową sekwencję** Aby utworzyć nowy diagram sekwencji  
  
     \- lub —  
  
     Kliknij przycisk **łącze do sekwencji** połączyć istniejący diagram.  
  
     Program Visual Studio tworzy łącze między wykorzystanie interakcji i Nowa sekwencja interakcji.  
  
     W rozwiązaniu pojawia się nowy diagram sekwencji. Zawiera ona linie życia, które zostało użyte do utworzenia wykorzystanie interakcji.  
  
    > [!NOTE]
    > Tylko linii życia, który został użyty do utworzenia wykorzystanie interakcji zostaną dołączone. Nowy diagram nie obejmuje linii życia, które zostały utworzone po interakcji korzystać, nawet wtedy, gdy ich obejmuje teraz wykorzystanie interakcji.  
  
#### <a name="to-create-a-reusable-sequence-from-existing-messages"></a>Aby utworzyć sekwencję wielokrotnego użytku z istniejących wiadomości  
  
- Kliknij prawym przyciskiem myszy komunikat, który chcesz przenieść, a następnie kliknij przycisk **Przenieś do diagramu**.  
  
  Visual Studio:  

  - Zastępuje przy interakcji ze strony za pomocą wybranego komunikatu i wszelkie uzupełniające wiadomości.  

  - Przenosi wiadomości zamieniono nowy diagram sekwencji.  

  - Tworzy łącze między wykorzystanie interakcji i nowy diagram sekwencji.  
  
#### <a name="to-navigate-to-the-sequence-referenced-by-an-interaction-use"></a>Aby przejść do sekwencji odwołuje się wykorzystanie interakcji  
  
- Kliknij dwukrotnie wykorzystanie interakcji.  
  
     \- lub —  
  
     Kliknij prawym przyciskiem myszy wykorzystanie interakcji, a następnie kliknij przycisk **Przejdź kolejno do**.  
  
### <a name="creating-a-placeholder-with-an-interaction-use"></a>Tworzenie symbolu zastępczego z użyciem interakcji  
 Wykorzystanie interakcji można utworzyć bez powiązania go z innego diagramu. Umożliwia to jako symbolu zastępczego dla części sekwencji których szczegóły są jeszcze opracowaniem. Użyj nazwy wykorzystanie interakcji, aby wskazać wynik, który chcesz.  
  
## <a name="Collapse"></a> Zwijanie grup linii życia  
 Zestaw linii życia można zwinąć ze sobą tak, aby grupa pojawia się jako jedna linia życia. Dzięki temu można wizualizować grupy obiektów jako samodzielny składnik. Wiadomości i zastosowania interakcji między liniami życia zwinięte grupy są ukryte. Wiadomości i sekwencje interakcji, które obejmują innych linie życia są wyświetlane.  
  
#### <a name="to-collapse-a-group-of-lifelines-together"></a>Aby zwinąć grupę linii życia razem  
  
1. Wybierz dwa lub więcej linii życia.  
  
2. Kliknij prawym przyciskiem myszy jeden z nich, a następnie kliknij przycisk **Zwiń**.  
  
     Oddzielne linie życia są zastępowane przez pojedynczej linii życia.  
  
     Wiadomości i zastosowania interakcji, które obejmują tylko członkowie grupy są ukryte.  
  
3. Aby zmienić nazwę grupy, kliknij nazwę.  
  
    > [!NOTE]
    > Nazwa grupy zostaną utracone po rozwinięciu grupy.  
  
#### <a name="to-expand-a-collapsed-group"></a>Aby rozwinąć zwinięte grupy  
  
- Kliknij prawym przyciskiem myszy zwinięty linii życia, a następnie kliknij przycisk **rozwiń**.  
  
    > [!NOTE]
    > Nazwa grupy będą zostać utracone, oraz wszelkie linki z grupy na komentarze lub elementów roboczych.  
  
## <a name="Fragments"></a> Opisujące struktury sterujące przy użyciu fragmentów  
 Połączonego fragmentu (13) służy do definiowania pętle i gałęzie równoczesne przetwarzanie w diagramie sekwencji. Można również rozważyć użycie zamiast niego diagramie aktywności. Diagram aktywności jest bardzo przydatne w pokazujący wiadomości między uczestnikami, ale w niektórych przypadkach lepiej jest w pętli, gałęzie i współbieżności.  
  
 Aby uzyskać pełną listę typów fragmentu, zobacz [opis przepływu sterowania przy użyciu fragmentów w diagramach sekwencji UML](../modeling/describe-control-flow-with-fragments-on-uml-sequence-diagrams.md).  
  
#### <a name="to-create-a-combined-fragment"></a>Aby utworzyć połączony fragment  
  
1. Wybierz komunikat lub sekwencję wiadomości wszystko już na tym samym wystąpieniu wykonywania lub linii życia.  
  
    > [!NOTE]
    > Wybierz strzałki wiadomość, a nie wystąpienia wykonywania, które wskazują komunikaty.  
  
2. Kliknij prawym przyciskiem myszy jeden z komunikatów, wskaż opcję **Otocz**, a następnie kliknij typ fragmentu, która jest wymagana.  
  
     Pojawi się nowy fragment. Zawiera komunikaty, które zostały wybrane.  
  
     Jeśli typ połączonego fragmentu umożliwia wielu fragmentów, również pojawi się pusty fragment.  
  
3. Aby ustawić zabezpieczenia fragmentu, kliknij prawym przyciskiem myszy obramowania fragmentu, a następnie kliknij **właściwości**. Ustaw **Guard** właściwości.  
  
     Osłony jest używane do definiowania warunków dla gałęzi i pętli.  
  
4. Aby dodać nowy fragment do typu, który umożliwia wielu fragmentów, kliknij prawym przyciskiem myszy granic fragmentu, a następnie wskaż **Dodaj**. Kliknij opcję **argumentu interakcji przed** lub **Operand interakcji po**.  
  
5. Aby dodać nowe wiadomości do fragmentu, należy użyć narzędzia wiadomości lub skopiuj i Wklej.  
  
## <a name="see-also"></a>Zobacz też  
 [Diagramy sekwencji UML: Odwołanie](../modeling/uml-sequence-diagrams-reference.md)   
 [Edytowanie modeli i diagramów UML](../modeling/edit-uml-models-and-diagrams.md)   
 [Diagramy przypadków użycia UML: Odwołanie](../modeling/uml-use-case-diagrams-reference.md)   
 [Diagramy klas UML: Odwołanie](../modeling/uml-class-diagrams-reference.md)   
 [Diagramy składników UML: Odwołanie](../modeling/uml-component-diagrams-reference.md)   
 [Diagramy składników UML: Odwołanie](../modeling/uml-component-diagrams-reference.md)   
 [Wideo: Powstawać interakcje za pomocą diagramów sekwencji](http://go.microsoft.com/fwlink/?LinkId=201113)
