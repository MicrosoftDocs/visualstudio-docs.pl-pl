---
title: 'Diagramy sekwencji UML: wskazówki | Microsoft Docs'
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
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: cdd853307bdea28c48762a6a3f0416e698b577ff
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "75850121"
---
# <a name="uml-sequence-diagrams-guidelines"></a>Diagramy sekwencyjne UML: Zalecenia
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

W programie Visual Studio możesz narysować *Diagram sekwencji* , aby wyświetlić interakcję. Interakcja to sekwencja komunikatów między typowymi wystąpieniami klas, składników, podsystemów lub aktorów.

 Diagramy sekwencji UML są częścią modelu UML i istnieją tylko w projektach modelowania UML. Aby utworzyć diagram sekwencji UML, w menu **Architektura** kliknij **Nowy UML lub diagram warstwowy**. Więcej informacji na temat [elementów diagramu sekwencji UML](../modeling/uml-sequence-diagrams-reference.md) lub [diagramów modelowania UML](../modeling/edit-uml-models-and-diagrams.md) znajduje się ogólnie. Aby zapoznać się z prezentacją, zobacz [Szkicowanie interakcji przy użyciu diagramów sekwencyjnych (2010)](https://channel9.msdn.com/Blogs/clinted/UML-with-VS-2010-Part-7-Sketching-Interactions-with-Sequence-Diagrams).

 Aby sprawdzić, które wersje programu Visual Studio obsługują tę funkcję, zobacz [Obsługa wersji dla narzędzi architektury i modelowania](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

## <a name="in-this-topic"></a>W tym temacie:
 [Korzystanie z diagramów sekwencji UML](#Using)

 [Podstawowe kroki dotyczące rysowania diagramów sekwencji](#BasicSteps)

 [Tworzenie i używanie prostych diagramów sekwencji](#Simple)

 [Klasy i linie życia](#ClassesAndLifelines)

 [Tworzenie sekwencji interakcji do wielokrotnego użytku](#Multiple)

 [Zwijanie grup linii życia](#Collapse)

 [Opisywanie struktur kontroli z fragmentami](#Fragments)

## <a name="using-uml-sequence-diagrams"></a><a name="Using"></a> Korzystanie z diagramów sekwencji UML
 Diagramy sekwencji można używać do różnych celów na różnych poziomach szczegółów programu. Typowe przypadki rysowania diagramu sekwencji są następujące:

- Jeśli masz diagram przypadków użycia, który podsumowuje użytkowników systemu i ich cele, możesz narysować diagramy sekwencji opisujące, jak główne składniki systemu współdziałają w celu spełnienia celu dla każdego przypadku użycia. Aby uzyskać więcej informacji, zobacz [diagramy przypadków użycia UML: wytyczne](../modeling/uml-use-case-diagrams-guidelines.md).

- Jeśli zidentyfikowano komunikaty docierające do interfejsu składnika, można narysować diagramy sekwencji opisujące, jak wewnętrzne części składnika współdziałają w celu osiągnięcia wyniku wymaganego dla każdego komunikatu przychodzącego. Aby uzyskać więcej informacji, zobacz [diagramy składników UML: wytyczne](../modeling/uml-component-diagrams-guidelines.md).

  Diagramy sekwencji rysowania mają kilka zalet:

- Możesz łatwo zobaczyć, jak zadania są dystrybuowane między składnikami.

- Można zidentyfikować wzorce interakcji, które utrudniają aktualizację oprogramowania.

## <a name="relationship-to-other-diagrams"></a>Relacje z innymi diagramami
 Diagramy sekwencji UML można używać razem z innymi diagramami na kilka sposobów.

#### <a name="lifelines-and-types"></a>Linie życia i typy
 Linie życia rysowane w diagramie sekwencji mogą reprezentować typowe wystąpienia składników lub klas w systemie. Można tworzyć linie życia z typów i typy z linii życia, a także wyświetlać typy na diagramach klas UML i diagramach składników UML. Aby uzyskać więcej informacji, zobacz [klasy i linie życia](#ClassesAndLifelines).

#### <a name="parameter-types"></a>Typy parametrów
 Można również opisać w diagramie klasy UML typy parametrów i zwracane wartości, które były używane w komunikatach przesyłanych między liniami życia.

#### <a name="use-case-details"></a>Szczegóły przypadku użycia
 Przypadek użycia reprezentuje cel użytkownika wraz z sekwencją kroków w celu osiągnięcia celu. Sekwencję kroków można opisać na kilka sposobów. Jedną z opcji jest narysowanie diagramu sekwencji, który pokazuje interakcje między użytkownikami i głównymi składnikami systemu. Aby uzyskać więcej informacji, zobacz [diagramy przypadków użycia UML: wytyczne](../modeling/uml-use-case-diagrams-guidelines.md).

## <a name="basic-steps-for-drawing-sequence-diagrams"></a><a name="BasicSteps"></a> Podstawowe kroki dotyczące rysowania diagramów sekwencji
 Aby uzyskać pełną listę elementów na diagramach sekwencji, zobacz [diagramy sekwencji UML: odwołanie](../modeling/uml-sequence-diagrams-reference.md).

> [!NOTE]
> Szczegółowe instrukcje dotyczące sposobu tworzenia dowolnego diagramu modelowania są opisane w sekcji [Edycja modeli UML i diagramów](../modeling/edit-uml-models-and-diagrams.md).

#### <a name="to-create-a-sequence-diagram"></a>Aby utworzyć diagram sekwencji

1. W menu **Architektura** kliknij kolejno pozycje **Nowy UML lub diagram warstwowy**.

2. W obszarze **Szablony**kliknij pozycję **Diagram sekwencji UML**.

3. Nadaj nazwę diagramowi.

4. W obszarze **Dodaj do projektu modelowania**wybierz istniejący projekt modelowania w rozwiązaniu lub **Utwórz nowy projekt modelowania**, a następnie kliknij przycisk **OK**.

    Zostanie wyświetlony nowy diagram sekwencji z przybornikiem **Diagram sekwencji** . Przybornik zawiera wymagane elementy i łączniki.

   ![Części diagramu sekwencji](../modeling/media/uml-sequence.png "UML_Sequence")

#### <a name="to-draw-a-sequence-diagram"></a>Aby narysować diagram sekwencji

1. Przeciągnij **linie życia** (1) z **przybornika** na diagram, aby reprezentować wystąpienia klas, składników, aktorów lub urządzeń.

    > [!NOTE]
    > Linię życia można także utworzyć, przeciągając istniejącą klasę, interfejs, aktor lub składnik z **Eksploratora modelu UML** na diagram. Spowoduje to utworzenie linii życia reprezentującej wystąpienie wybranego typu.

2. Rysuj wiadomości, aby pokazać, jak linie życia współpracują w celu osiągnięcia określonego celu.

     Aby utworzyć komunikat (3, 4, 6, 7), kliknij narzędzie wiadomości. Następnie kliknij pozycję linia życia, w której ma zostać uruchomiony komunikat, a następnie kliknij pozycję linia życia.

     Wystąpienie wykonywania (5) pojawia się po odebraniu linii życia. Wystąpienie wykonywania reprezentuje okres, w którym wystąpienie wykonuje metodę. Można utworzyć inne komunikaty, które zaczynają się od wystąpienia wykonania.

3. Aby wyświetlić komunikat pochodzący z nieznanego źródła zdarzeń (9) lub emisji do nieznanych odbiorców (10), narysuj komunikat asynchroniczny z lub do pustego miejsca na diagramie. Komunikaty te są nazywane *komunikatami znalezionymi* (9) i *utraconymi komunikatami* (10).

    > [!NOTE]
    > Aby przenieść grupę linii życia z utraconymi lub znalezionymi komunikatami, wykonaj następujące kroki, aby wybrać linie życia przed ich przeniesieniem: Narysuj prostokąt wokół tych linii życia lub naciśnij i przytrzymaj klawisz **Ctrl** podczas klikania każdej linii życia. Jeśli używasz **opcji Zaznacz wszystko** lub **Ctrl** + **A** , aby zaznaczyć wszystkie linie życia, a następnie przeniesiesz je, utracone lub znalezione komunikaty dołączone do tych linii życia nie będą przenoszone. Jeśli wystąpi taka sytuacja, te wiadomości można przenosić oddzielnie.

4. Rysuj diagramy sekwencji dla każdej istotnej wiadomości do tego samego składnika lub systemu.

#### <a name="to-change-the-order-of-messages"></a>Aby zmienić kolejność komunikatów

- Przeciągnij komunikat w górę lub w dół w jego linii życia. Można przeciągać je do innych komunikatów lub do lub z bloku wykonywania.

     \- oraz

- Kliknij komunikat i użyj klawiszy Strzałka w **górę** i **Strzałka w dół** , aby dostosować położenie wiadomości. Aby zmienić kolejność komunikatów, użyj **klawiszy Shift + Strzałka w górę** i **Shift + Strzałka w dół** .

#### <a name="to-move-or-copy-message-sequences-on-the-sequence-diagram"></a>Aby przenieść lub skopiować sekwencje komunikatów na diagramie sekwencji

1. Kliknij prawym przyciskiem myszy komunikat (3, 4), a następnie kliknij polecenie **Kopiuj**.

2. Kliknij prawym przyciskiem myszy wystąpienie wykonywania (5) lub linię życia (1), z której ma być wysyłany nowy komunikat, a następnie kliknij przycisk **Wklej**. Nowy nadawca może znajdować się na innym diagramie, jeśli chcesz.

     Kopia wiadomości i wszystkie jej komunikaty zależne są dodawane na końcu wystąpienia wykonywania lub na koniec linii życia.

    > [!NOTE]
    > Wklejony komunikat zawsze pojawia się na końcu wystąpienia lub linii życia wykonania. Po wklejeniu można go przeciągnąć do wcześniejszej pozycji.

#### <a name="to-display-and-edit-the-signature-text-for-a-message"></a>Aby wyświetlić i edytować tekst podpisu dla wiadomości

- Docelowa linia życia musi być powiązana lub zamapowana na typy, aby tekst podpisu był widoczny. Aby wykonać to zadanie, wykonaj jedną z następujących czynności:

  - Kliknij prawym przyciskiem myszy linię życia, a następnie wybierz polecenie **Utwórz klasę**.

     -lub-

  - Wybierz linię życia, naciśnij klawisz **F4**, a następnie w oknie **Właściwości** ustaw właściwość **Typ** na istniejący typ lub określ nazwę nowego typu. Kliknij prawym przyciskiem myszy etykietę komunikat, a następnie wybierz polecenie **Utwórz operację**.

    Tekst podpisu jest wyświetlany poniżej etykiety wiadomości. Teraz można edytować tekst podpisu. Aby uzyskać więcej informacji, zobacz [klasy i linie życia](#ClassesAndLifelines).

#### <a name="to-improve-the-layout-of-a-sequence-diagram"></a>Aby poprawić układ diagramu sekwencji

- Kliknij prawym przyciskiem myszy pustą część diagramu, a następnie kliknij polecenie **Zmień układ układu**.

- Aby cofnąć operację, kliknij przycisk **Edytuj**, a następnie kliknij przycisk **Cofnij**.

#### <a name="to-change-the-package-that-owns-the-interaction"></a>Aby zmienić pakiet, który jest właścicielem interakcji

1. W **Eksploratorze modelu UML**Znajdź interakcję, którą wyświetla diagram sekwencji.

    > [!NOTE]
    > Interakcja nie zostanie wyświetlona w **Eksploratorze modelu UML** do momentu dodania pierwszej linii życia do diagramu sekwencji.

2. Przeciągnij interakcję do pakietu.

     \- oraz

     Kliknij prawym przyciskiem myszy interakcję, a następnie kliknij pozycję **Wytnij**. Kliknij prawym przyciskiem myszy pakiet, a następnie kliknij przycisk **Wklej**.

## <a name="creating-and-using-simple-sequence-diagrams"></a><a name="Simple"></a> Tworzenie i używanie prostych diagramów sekwencji
 Najprostsza i najbardziej szeroko stosowana forma diagramu sekwencji zawiera tylko linie życia i wiadomości. Diagram tego rodzaju pozwala na jasne wyświetlanie typowej sekwencji interakcji między obiektami w projekcie lub między systemem a użytkownikami. Jest to często wystarczające, aby ułatwić omawianie i komunikowanie się z projektem.

 Oto kilka rzeczy, które należy wziąć pod uwagę podczas rysowania prostego diagramu sekwencji.

### <a name="types-of-message"></a>Typy komunikatów
 Istnieją trzy narzędzia, których można użyć do tworzenia komunikatów.

- Za pomocą narzędzia **synchronicznego** opisz interakcję, w której nadawca ma zwrócić odpowiedź (3).

     **<\<return>>** Na końcu wystąpienia wykonania zostanie wyświetlona strzałka. Oznacza to powrót kontroli do nadawcy.

- Narzędzie **asynchroniczne** służy do opisywania interakcji, w której nadawca może natychmiast kontynuować bez oczekiwania na odbiornik (4).

- Za pomocą narzędzia do **tworzenia** opisz interakcję, w której nadawca tworzy odbiornik (8).

     Komunikat o utworzeniu powinien być pierwszym komunikatem odbieranym przez odbiornik.

### <a name="annotating-the-interactions"></a>Dodawanie adnotacji do interakcji
 Aby bardziej szczegółowo opisać sekwencję, możesz umieścić **komentarz** w dowolnym miejscu na diagramie.

 Za pomocą **linków komentarzy**można połączyć komentarz z liniami życia, wykonaniami, użyciem interakcji i fragmentami.

> [!CAUTION]
> Jeśli chcesz dołączyć komentarz do określonego punktu w sekwencji, połącz go z wystąpieniem wykonywania, użyciem interakcji lub fragmentem. Nie należy łączyć jej z linią życia, ponieważ w takim przypadku nie pozostaje ona połączona w prawidłowym punkcie w sekwencji.

 Użyj komentarza, aby:

- Zwróć uwagę na to, co zostało osiągnięte w kluczowych punktach sekwencji. Dzięki temu czytelnicy mogą zobaczyć cele interakcji.

- Opisz ogólny cel całej sekwencji. Dołącz komentarz do początkowego wystąpienia wykonania lub pozostaw je niedołączone. Na przykład "klient wybrał elementy z menu i ma cenę".

- Opisz obowiązki każdej linii życia. Dołącz komentarz do linii życia. Na przykład "Menedżer porządkowania zbiera opcje menu klienta".

- Zwróć uwagę na wyjątki lub alternatywy, które mogą być wykonywane jako alternatywę dla typowej pokazanej sekwencji. Na przykład "klient może wybrać, aby pominąć resztę tej sekwencji".

  - Rozważ użycie fragmentów jako bardziej formalnej alternatywy dla tego rodzaju uwagi. Zobacz [Opis struktur kontroli z fragmentami](#Fragments)

## <a name="deciding-the-scope-of-the-diagram"></a>Decydowanie o zakresie diagramu
 Ważne jest, aby wyczyścić informacje o tym, co diagram ma być pokazywany.

#### <a name="initiating-event"></a>Inicjowanie zdarzenia
 Każdy diagram powinien zawierać sekwencję interakcji, które wynikają z jednego inicjującego zdarzenia. Może to być na przykład:

- Użytkownik inicjujący przypadek użycia, na przykład otwierając stronę sieci Web do kupowania posiłku.

- Komunikat z jednego składnika systemu do innego, na przykład badanie dostępności elementów, które klient chce kupić.

- Zdarzenie wyzwalane przez zmianę stanu, na przykład zapasy elementu wchodzące poniżej wartości progowej.

#### <a name="level-of-detail"></a>Poziom szczegółowości
 Diagramy sekwencji mogą wyświetlać różne poziomy szczegółowości. Poziom szczegółowości można określić w dwóch oddzielnych wymiarach niemal niezależnie:

 Linie życia mogą reprezentować jeden z następujących poziomów szczegółowości:

- Obiekty w kodzie programu, który istnieje lub jest opracowywany.

- Składniki lub ich podskładniki, zwykle pomijając fasad, proxy i inne mechanizmy łączące.

- System i aktory zewnętrzne

  Komunikaty mogą reprezentować jeden z następujących poziomów szczegółowości:

- Komunikaty o oprogramowaniu w kodzie programu, w interfejsie API lub interfejsie sieci Web.

- Transakcje lub transakcje podrzędne, na przykład między użytkownikami a systemem lub między kodem i bazą danych.

- Przypadki użycia — główne interakcje między użytkownikami a systemem.

  Niezależnie od tego, czy przeglądasz istniejący kod, czy opisywano nowy projekt, często przydatne jest rysowanie i dyskutowanie mniej szczegółowych widoków.

## <a name="describing-variations"></a>Opisywanie odmian
 Diagram przedstawia jedną, typową sekwencję zdarzeń. Jeśli chcesz pokazać alternatywne możliwości, takie jak scenariusze awarii, możesz użyć jednej z następujących opcji:

- Rysowanie oddzielnych diagramów sekwencji, aby opisać te scenariusze

- Użyj [opisu struktur kontroli z fragmentami](#Fragments) , aby pokazać pętle, alternatywy i tak dalej.

## <a name="assessing-the-design"></a>Ocenianie projektu
 Za pomocą diagramu można ocenić rozkład zadań między swoimi obiektami lub składnikami. Rozważ refaktoryzację, Jeśli zobaczysz następujące wzorce:

- Jedna linia życia wygląda na wszystko, wykonując wywołania do wszystkiego innego, podczas gdy inne linie życia reagują pasywnie.

- Wiele komunikatów między różnymi liniami życia. Każda linia życia powinna wysyłać komunikaty do kilku sąsiadów i nie powinna komunikować się z jej sąsiadami. Zwykle powinno być możliwe rozmieszczenie linii życia tak, aby istniały tylko kilka miejsc, w których komunikaty są krzyżowe. a tam, gdzie istnieją skrzyżowania, docelowa linia życia nie powinna również wymieniać komunikatów, które mają przecinające się linie życia.

- Niektóre linie życia wydają się obsługiwać więcej niż jeden rodzaj zadania. Należy łatwo znaleźć jedno zwięzłe zdanie, które opisuje obowiązki każdej linii życia, podsumowujące działania wykonywane w odpowiedzi na każdą odebraną wiadomość.

## <a name="classes-and-lifelines"></a><a name="ClassesAndLifelines"></a> Klasy i linie życia
 Linie życia w diagramach sekwencji pokazują wystąpienia klas lub interfejsów składników. Linię życia można nazwać na dwa sposoby:

|**W tym celu**|**Użyj tego formatu**|
|--------------------------|-------------------------|
|Anonimowe wystąpienie typu.<br /><br /> Użyj tego, jeśli masz tylko jedną linię życia dla każdego typu.|*Nazwa*|
|Nazwane wystąpienie typu.<br /><br /> Użyj tego, jeśli chcesz wyświetlić sekwencję obejmującą więcej niż jedno wystąpienie tego samego typu.|*ObjectName*:*TypeName*|

### <a name="creating-lifelines-from-types"></a>Tworzenie linii życia z typów
 Można tworzyć nowe linie życia na podstawie już zdefiniowanych klas, na przykład na diagramie klasy.

> [!NOTE]
> Przed wykonaniem tego zadania upewnij się, że masz istniejący diagram sekwencji.

##### <a name="to-create-a-lifeline-from-an-existing-type"></a>Aby utworzyć linię życia na podstawie istniejącego typu

- Przeciągnij klasę, składnik lub interfejs z Eksploratora modelu UML na diagram sekwencji.

   \- oraz

  1. Kliknij prawym przyciskiem myszy klasę, składnik lub interfejs na odpowiednim diagramie, a następnie kliknij polecenie **Utwórz linię życia**.

  2. W oknie dialogowym **Tworzenie linii życia** Wybierz diagram sekwencji, a następnie kliknij przycisk **OK**.

     Zostanie wyświetlona nowa linia życia o nazwanym wystąpieniu, której typ jest przeciągany.

  > [!NOTE]
  > Tę akcję można powtarzać dowolną liczbę razy. Spowoduje to utworzenie linii życia z różnymi nazwami wystąpień.

##### <a name="to-change-the-type-of-a-lifeline"></a>Aby zmienić typ linii życia

1. Kliknij prawym przyciskiem myszy linię życia, a następnie kliknij polecenie **Właściwości**.

2. W oknie **Właściwości** ustaw właściwość **Typ** . Możesz wybrać typ z menu rozwijanego lub wpisać nową nazwę.

### <a name="creating-classes-from-lifelines"></a>Tworzenie klas z linii życia
 Po utworzeniu co najmniej jednego diagramu sekwencji można podsumować linie życia przez utworzenie klas lub interfejsów z nich.

##### <a name="to-create-a-class-or-interface-from-a-lifeline"></a>Aby utworzyć klasę lub interfejs z linii życia

1. Kliknij prawym przyciskiem myszy linię życia, a następnie kliknij polecenie **Utwórz klasę** lub **Utwórz interfejs**.

     Nowa klasa lub interfejs pojawia się w Eksploratorze modelu UML.

2. Utwórz operacje w klasie lub interfejsie dla każdego komunikatu, który otrzymuje linia życia:

    1. Zaznacz wszystkie wiadomości, które chcesz dołączyć.

    2. Kliknij prawym przyciskiem myszy jeden z komunikatów, a następnie kliknij polecenie **Utwórz metodę**.

         Nowa klasa lub interfejs zawiera operacje dla każdego wybranego komunikatu.

         Nazwa operacji jest wyświetlana poniżej każdej strzałki komunikatu i we właściwości **operacji** komunikatu.

         Jeśli wiadomość zawiera parametry w postaci "(parametr: Type)", pojawią się na liście parametrów nowej operacji.

        > [!NOTE]
        > Ten krok należy powtórzyć w przypadku dodania nowych komunikatów do diagramu sekwencji.

3. Aby wyświetlić szczegółowe informacje o nowej klasie lub interfejsie, należy dodać ją do diagramu klasy lub składnika.

    1. Otwórz lub Utwórz klasę lub diagram składników.

    2. Przeciągnij nową klasę lub interfejs z **Eksploratora modelu UML** do diagramu klas.

         Klasa lub interfejs pojawia się na diagramie klas.

         \- oraz

    3. Przeciągnij nowy interfejs z **Eksploratora modelu UML** na składnik lub port na diagramie składników.

         Interfejs pojawia się na składniku jako lizak.

### <a name="creating-classes-for-parameters"></a>Tworzenie klas dla parametrów
 Można uwzględnić parametry w komunikatach na diagramie sekwencji. Można użyć diagramu klas UML do opisania typów parametrów.

## <a name="creating-reusable-interaction-sequences"></a><a name="Multiple"></a> Tworzenie sekwencji interakcji do wielokrotnego użytku
 Można użyć oddzielnego diagramu do opisywania sekwencji zawierającej szczegóły, które mają zostać rozdzielone lub które są wspólne dla kilku diagramów.

 Można utworzyć prostokąt używany do interakcji (12) na jednym diagramie, który wskazuje szczegóły na innym diagramie.

 Kliknij dwukrotnie pozycję interakcja, aby otworzyć powiązany z nią diagram sekwencji.

#### <a name="to-create-a-reusable-interaction-sequence-from-existing-lifelines"></a>Aby utworzyć sekwencję interakcji wielokrotnego użytku z istniejących linii życia

1. W **przyborniku**kliknij pozycję **użycie interakcji**.

2. Na diagramie sekwencji Trzymaj przycisk myszy w dół podczas przeciągania między liniami życia, które chcesz uwzględnić w sekwencji wielokrotnego użytku. Zacznij od pozycji w pionie, w której chcesz wstawić użycie interakcji.

     Użycie interakcji pojawia się w obrębie wybranych linii życia na diagramie sekwencji.

3. Kliknij dwukrotnie nazwę przy użyciu interakcji i zmień jej nazwę, aby opisać efekt sekwencji wielokrotnego użytku na tym diagramie.

     \- oraz

     Napisz nazwę, taką jak wywołanie funkcji, z parametrami.

4. Połącz użycie interakcji z innym diagramem sekwencji. Kliknij prawym przyciskiem myszy użycie interakcji, a następnie:

     Kliknij przycisk **Utwórz nową sekwencję** , aby utworzyć nowy diagram sekwencji

     \- oraz

     Kliknij pozycję **Połącz z sekwencją** , aby połączyć się z istniejącym diagramem.

     Program Visual Studio tworzy łącze między użyciem interakcji i nową sekwencją interakcji.

     W rozwiązaniu pojawi się nowy diagram sekwencji. Zawiera linie życia używane do tworzenia interakcji.

    > [!NOTE]
    > Zostaną uwzględnione tylko linie życia użyte podczas tworzenia interakcji. Nowy diagram nie obejmuje linii życia utworzonych po użyciu interakcji, nawet jeśli ta interakcja będzie teraz omawiana.

#### <a name="to-create-a-reusable-sequence-from-existing-messages"></a>Aby utworzyć sekwencję wielokrotnego użytku z istniejących komunikatów

- Kliknij prawym przyciskiem myszy komunikat, który chcesz przenieść, a następnie kliknij polecenie **Przenieś do diagramu**.

  Visual Studio:

  - Zastępuje interakcją z użyciem wybranej wiadomości i wszelkich komunikatów zależnych.

  - Przenosi zastąpione komunikaty do nowego diagramu sekwencji.

  - Tworzy łącze między użyciem interakcji a nowym diagramem sekwencji.

#### <a name="to-navigate-to-the-sequence-referenced-by-an-interaction-use"></a>Aby przejść do sekwencji, do której odwołuje się użycie interakcji

- Kliknij dwukrotnie użycie interakcji.

     \- oraz

     Kliknij prawym przyciskiem myszy użycie interakcji, a następnie kliknij pozycję **Przejdź do sekwencji**.

### <a name="creating-a-placeholder-with-an-interaction-use"></a>Tworzenie symbolu zastępczego z użyciem interakcji
 Można utworzyć interakcję bez powiązania jej z innym diagramem. Można go użyć jako symbolu zastępczego dla części sekwencji, której szczegóły jeszcze nie mają zostać wykonane. Użyj nazwy używanej interakcji, aby wskazać żądany wynik.

## <a name="collapsing-groups-of-lifelines"></a><a name="Collapse"></a> Zwijanie grup linii życia
 Zestaw linii życia można zwinąć ze sobą, aby grupa była wyświetlana jako jedna linia życia. Ułatwia to wizualizację grupy obiektów jako jednego składnika. Komunikaty i interakcje stosowane między liniami życia w zwiniętej grupie są ukryte. Wyświetlane są komunikaty i sekwencje interakcji, które obejmują inne linie życia.

#### <a name="to-collapse-a-group-of-lifelines-together"></a>Aby zwinąć grupę linii życia razem

1. Wybierz co najmniej dwie linie życia.

2. Kliknij prawym przyciskiem myszy jeden z nich, a następnie kliknij przycisk **Zwiń**.

     Osobne linie życia są zastępowane przez jedną linię życia.

     Komunikaty i interakcje są używane tylko w przypadku elementów członkowskich grupy.

3. Aby zmienić nazwę grupy, kliknij nazwę.

    > [!NOTE]
    > Nazwa grupy zostanie utracona po rozszerzeniu grupy.

#### <a name="to-expand-a-collapsed-group"></a>Aby rozwinąć zwiniętyą grupę

- Kliknij prawym przyciskiem myszy zwinięte linie życia, a następnie kliknij przycisk **Rozwiń**.

    > [!NOTE]
    > Nazwa grupy zostanie utracona wraz z dowolnymi łączami z grupy do komentarzy lub elementów roboczych.

## <a name="describing-control-structures-with-fragments"></a><a name="Fragments"></a> Opisywanie struktur kontroli z fragmentami
 Za pomocą połączonych fragmentów (13) można definiować pętle, gałęzie i współbieżne przetwarzanie w diagramie sekwencji. Zamiast tego Rozważ użycie diagramu aktywności. Diagram aktywności nie jest jak użyteczny podczas wyświetlania komunikatów między aktorami, ale w niektórych przypadkach lepiej jest wyświetlać pętle, gałęzie i współbieżność.

 Aby zapoznać się z pełną listą typów fragmentów, zobacz [opisywanie przepływu sterowania przy użyciu fragmentów w diagramach sekwencji UML](../modeling/describe-control-flow-with-fragments-on-uml-sequence-diagrams.md).

#### <a name="to-create-a-combined-fragment"></a>Aby utworzyć połączony fragment

1. Wybierz wiadomość lub sekwencję komunikatów, zaczynając od tego samego wystąpienia wykonywania lub linii życia.

    > [!NOTE]
    > Wybierz strzałki komunikatu, a nie wystąpienia wykonywania, do których wskazują komunikaty.

2. Kliknij prawym przyciskiem myszy jeden z komunikatów, wskaż polecenie **Otocz**, a następnie kliknij wymagany typ fragmentu.

     Zostanie wyświetlony nowy fragment. Zawiera wybrane komunikaty.

     Jeśli połączony typ fragmentu zezwala na wiele fragmentów, pojawi się również pusty fragment.

3. Aby ustawić ochronę fragmentu, kliknij prawym przyciskiem myszy obramowanie fragmentu, a następnie kliknij polecenie **Właściwości**. Ustaw właściwość **Guard** .

     Funkcja Guard służy do definiowania warunku dla gałęzi lub pętli.

4. Aby dodać nowy fragment do rodzaju, który zezwala na wiele fragmentów, kliknij prawym przyciskiem myszy granicę fragmentu i wskaż polecenie **Dodaj**. Kliknij wartość **argumentu operacji interakcji przed** lub z **argumentem operacji**.

5. Aby dodać nowe wiadomości do fragmentu, użyj narzędzi komunikatów lub skopiuj i wklej.

## <a name="see-also"></a>Zobacz też
 [Diagramy sekwencji UML: informacje referencyjne](../modeling/uml-sequence-diagrams-reference.md) [Edycja modeli UML i diagramy](../modeling/edit-uml-models-and-diagrams.md) diagramów [przypadków użycia UML: referencyjne](../modeling/uml-use-case-diagrams-reference.md) diagramy [klas UML:](../modeling/uml-class-diagrams-reference.md) referencyjne diagramy składników UML: [referencyjne](../modeling/uml-component-diagrams-reference.md) [diagramy składników UML](../modeling/uml-component-diagrams-reference.md) : [film wideo: Szkicowanie interakcji przy użyciu diagramów sekwencyjnych](https://channel9.msdn.com/posts/clinted/UML-with-VS-2010-Part-2-Organizing-Features-Into-Use-Cases)
