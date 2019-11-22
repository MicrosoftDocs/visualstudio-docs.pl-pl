---
title: 'Diagramy przypadków użycia UML: wytyczne | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- diagrams - modeling, use case
- UML, use case diagrams
- diagrams - modeling, UML use case
- use case diagrams
- UML diagrams, use case
ms.assetid: b1ae8ed0-d00b-4f9b-8e23-733e09e81e9b
caps.latest.revision: 38
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 7c9ccd5285f9a2744704c0ee13094a1dac31c53b
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2019
ms.locfileid: "74302838"
---
# <a name="uml-use-case-diagrams-guidelines"></a>Diagramy przypadków użycia UML: Zalecenia
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

W programie Visual Studio możesz narysować *Diagram przypadków użycia* , aby podsumować, kto używa aplikacji lub systemu, i co można z nimi zrobić. Aby utworzyć diagram przypadków użycia UML, w menu **Architektura** kliknij **Nowy UML lub diagram warstwowy**.

 Aby zapoznać się z pokazem wideo, zobacz [organizowanie funkcji do przypadków użycia](https://channel9.msdn.com/blogs/clinted/uml-with-vs-2010-part-2-organizing-features-into-use-cases).

 Aby sprawdzić, które wersje programu Visual Studio obsługują tę funkcję, zobacz [Obsługa wersji dla narzędzi architektury i modelowania](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

 Za pomocą diagramu przypadków użycia można omawiać i komunikować:

- Scenariusze, w których system lub aplikacja współdziałają z osobami, organizacjami lub systemami zewnętrznymi.

- Cele, które ułatwiają tym uczestnikom.

- Zakres Twojego systemu.

  Diagram przypadków użycia nie pokazuje szczegółów przypadków użycia: podsumowuje tylko niektóre relacje między przypadkami użycia, aktorami i systemami. W szczególności diagram nie pokazuje kolejności wykonywania kroków w celu osiągnięcia celów każdego przypadku użycia. Można opisać te szczegóły w innych diagramach i dokumentach, które można połączyć z każdym przypadkiem użycia. Więcej informacji znajduje się [w sekcji opisywanie przypadków użycia szczegółowo](#Details) w tym temacie.

  Opisy wprowadzone w przypadku przypadków użycia będą używać kilku warunków związanych z domeną, w której działa system, takich jak sprzedaż, menu, klient i tak dalej. Ważne jest, aby zdefiniować te warunki i ich relacje jasno i można to zrobić za pomocą diagramu klas UML. Aby uzyskać więcej informacji, zobacz [diagramy klas UML: wytyczne](../modeling/uml-class-diagrams-guidelines.md).

  Przypadki użycia dotyczą tylko wymagań funkcjonalnych dla systemu. Inne wymagania, takie jak reguły biznesowe, wymagania dotyczące jakości usług i ograniczenia implementacji, muszą być reprezentowane osobno. Informacje o architekturze i wewnętrznych szczegółach muszą być również opisane osobno. Aby uzyskać więcej informacji na temat sposobu definiowania wymagań dotyczących użytkowników, zobacz [wymagania dotyczące modelu użytkownika](../modeling/model-user-requirements.md).

  Przykłady użyte w tym temacie dotyczą witryny sieci Web, w której klienci mogą zamawiać posiłki z lokalnych restauracji.

  ![Elementy na diagramie przypadków użycia](../modeling/media/uml-ucovactor.png "UML_UCOvActor")

- *Aktor* (1) to Klasa osoby, organizacji, urządzenia lub składnika oprogramowania zewnętrznego, który współdziała z systemem. Przykładowymi aktorami są **Klient**, **restauracji**, **czujnik temperatury**, **autoryzowanie autoryzacji karty kredytowej.**

- *Przypadek użycia* (2) reprezentuje akcje wykonywane przez co najmniej jedną aktora w celu osiągnięcia określonego celu. Przykładowe przypadki użycia to **posiłek z kolejnością**, **menu aktualizacji**, **proces płatności**.

   W przypadku diagramu przypadków użycia są skojarzone przypadki użycia (3) z aktorami, które je wykonują.

- Twój *System (4)* jest niezależnie od siebie. Może to być niewielki składnik oprogramowania, którego aktory są tylko innymi składnikami oprogramowania; może to być kompletna aplikacja. może to być duży rozproszony pakiet aplikacji wdrożony na wielu komputerach i urządzeniach. Przykładowe podsystemy to **Witryna sieci Web zamawiania posiłków**, **firma dostarczająca mączkę**, **wersja 2**.

   Diagram przypadków użycia może wskazywać, które przypadki użycia są obsługiwane przez system lub jego podsystemy.

## <a name="BasicSteps"></a>Podstawowe kroki rysowania diagramów przypadków użycia

> [!NOTE]
> Szczegółowe instrukcje tworzenia dowolnego diagramu modelowania są opisane w sekcji [Edycja modeli UML i diagramów](../modeling/edit-uml-models-and-diagrams.md).

#### <a name="to-create-a-new-use-case-diagram"></a>Aby utworzyć nowy diagram przypadków użycia

1. W menu **Architektura** kliknij kolejno pozycje **Nowy UML lub diagram warstwowy**.

2. W obszarze **Szablony**kliknij pozycję **Diagram przypadków UMLUse**.

3. Nadaj nazwę diagramowi.

4. W obszarze **Dodaj do projektu modelowania**wybierz istniejący projekt modelowania w rozwiązaniu lub **Utwórz nowy projekt modelowania**, a następnie kliknij przycisk **OK**.

#### <a name="to-draw-a-use-case-diagram"></a>Aby narysować diagram przypadków użycia

1. Przeciągnij granice **podsystemu** z przybornika na diagram, aby reprezentować cały system lub jego główne składniki.

    - Możesz narysować diagram przypadków użycia bez granic systemu, jeśli nie chcesz opisywać, które przypadki użycia są obsługiwane przez system lub jego składniki.

    - Przeciągnij róg systemu, aby go powiększyć, jeśli jest to konieczne.

    - Odpowiednio zmień nazwę.

2. Przeciągnij **aktory** z przybornika na diagram (umieszczając je poza granicami systemu).

    - Aktory reprezentują klasy użytkowników, organizacji i systemów zewnętrznych, które współpracują z systemem.

    - Zmień ich nazwy. Na przykład: **klient, restauracji, Agencja kart kredytowych.**

3. Przeciągnij **przypadki użycia** z przybornika do odpowiednich systemów.

    - Przypadki użycia reprezentują działania wykonywane przez aktorów z pomocą systemu.

    - Zmień ich nazwy, korzystając z tytułów, które są zrozumiałe dla aktorów. Nie używaj tytułów związanych z kodem. Na przykład: **posiłek na zamówienie, płatność za posiłki, dostarczenie posiłku**.

    - Zacznij od poważniejszych transakcji, takich jak **posiłek na zamówienie**, pozostawiając do późniejszej mniejszej liczby interakcji, np. **elementu menu wybierz**.

    - Umieść każdy przypadek użycia w systemie lub w głównym podsystemie, który go obsługuje (ignorowanie wszelkich elewacji lub składników, które są używane tylko w połączeniu z użytkownikiem).

    - Przypadek użycia można narysować poza granicą systemu, aby pokazać, że nie jest on obsługiwany przez system, być może w określonej wersji lub wersji.

4. Kliknij pozycję **skojarzenie** w przyborniku, a następnie przypadek użycia, a następnie aktora, który uczestniczy w przypadku użycia. Połącz poszczególne aktory ze swoimi przypadkami użycia w ten sposób.

5. Struktura przypadków użycia z relacjami **include**, **rozszerzając** i **generalize** . Aby utworzyć każde z tych linków, kliknij narzędzie, a następnie źródłowy przypadek użycia, a następnie element docelowy. Zapoznaj się z sekcją Tworzenie [struktury przypadków użycia](#Structuring).

6. Opisz przypadki użycia bardziej szczegółowo. Zapoznaj się z poniższą sekcją [opisywania przypadków użycia](#Details).

7. Rysowanie oddzielnych diagramów, aby skoncentrować się na różnych podsystemach lub różnych grupach powiązanych przypadków użycia. Wszystkie diagramy w jednym projekcie modelowania są widokami tego samego modelu.

## <a name="Actors"></a>Rysowanie aktorów i przypadków użycia
 Głównym celem diagramu przypadków użycia jest pokazanie osób, które współpracują z systemem, oraz głównych celów, z którymi się uzyskują.

- Twórz **aktory** reprezentujące klasy osób, organizacji, innych systemów, oprogramowania lub urządzeń, które współpracują z systemem lub podsystemem.

  - Aby dowiedzieć się, jak narysować aktory i inne elementy, zobacz [Edycja modeli UML i diagramów](../modeling/edit-uml-models-and-diagrams.md).

  - Dla każdego odrębnego zestawu celów Zidentyfikuj aktorów według ich typu lub roli, chociaż osoby fizyczne lub jednostki mogą być takie same. Na przykład restauracji i klient są oddzielnymi aktorami, chociaż pracownicy restauracji mogą czasami być klientami.

- Twórz **przypadki użycia** dla każdego z celów, które każdy aktor dąży do osiągnięcia w systemie.

  - Nazwij i opisz przypadki użycia w słowach, które będą zrozumieć aktora, a nie warunki implementacji.

- Łączenie aktorów z przypadkami użycia przy użyciu **skojarzeń** .

### <a name="inheritance-between-actors"></a>Dziedziczenie między aktorami
 ![Diagram przypadków użycia przedstawiający dziedziczenie](../modeling/media/uml-ucguideinherit.png "UML_UCGuideInherit")

 Możesz narysować łącze **generalizacji** między aktorami. Wyspecjalizowany aktor, taki jak klient klubu w przykładzie, dziedziczy przypadki użycia uogólnionego aktora, takiego jak klient. Grot powinien wskazywać na bardziej ogólny aktora, na przykład klient. Po utworzeniu linku najpierw wskaż bardziej wyspecjalizowany aktor.

 Wyspecjalizowany aktor może mieć własne dodatkowe przypadki użycia, które nie są dostępne dla innych aktorów.

> [!CAUTION]
> Nie należy tworzyć pętli relacji generalizacji, które powodują generalizację aktora. Pętle mogą generować błędy.

### <a name="alternative-actor-icons"></a>Alternatywne ikony aktora
 Możesz użyć niestandardowych ikon do reprezentowania aktora zamiast standardowej liczby nalepek. Można na przykład zmienić ją na podobną do urządzenia, restauracji, banku i tak dalej.

##### <a name="to-change-the-appearance-of-an-actor"></a>Aby zmienić wygląd aktora

1. Kliknij prawym przyciskiem myszy aktora, a następnie kliknij polecenie **Właściwości**.

     Zostanie wyświetlone okno **Właściwości** .

2. Ustaw właściwość **ścieżka obrazu** na lokalizację pliku obrazu.

    - Można użyć dowolnego z kilku formatów obrazu, takich jak GIF, jpg i BMP.

    - Użyj pliku, który znajduje się w rozwiązaniu lub kontroli źródła projektu, tak aby był dostępny, gdy rozwiązanie zostanie przeniesione lub skopiowane.

3. Aby replikować ten wygląd w innych diagramach przypadków użycia, skopiuj aktora i wklej go do innego diagramu.

    - Zmiana obrazu ma zastosowanie tylko do widoku na określonym diagramie. Nie dotyczy bazowego elementu modelu. Jeśli przeciągniesz aktora z Eksploratora modelu UML na inny diagram, pojawi się on jako standardowy rysunek nalepek.

### <a name="multiplicities-between-actors-and-use-cases"></a>Liczebność między aktorami i przypadkami użycia
 Skojarzenie między aktorem a przypadkiem użycia może pokazać *liczebność* na każdym końcu.

 ![Użyj przypadku jeden do jednego z aktorem](../modeling/media/uml-ucguidemulti1.png "UML_UCGuideMulti1")

> [!NOTE]
> Liczebność skojarzenia w diagramie przypadku użycia jest ukryta, jeśli oba te elementy są **1**.

 Domyślnie każda liczebność wynosi **1**. W ścisłej interpretacji modelu liczebność 1 oznacza, że na przykład tylko jeden klient jest związany z porządkowaniem każdego posiłku i że każdy klient zamówi w danym momencie tylko jedno posiłek.

 Można zmienić te liczebność.

 Na przykład:

 ![Przypadek użycia pokazujący wiele do wielu liczebności](../modeling/media/uml-ucguidemulti2.png "UML_UCGuideMulti2")

- Aby określić, że kilka aktorów tej samej klasy może brać udział w pojedynczym wystąpieniu przypadku użycia, ustaw liczebność na końcu aktora skojarzenia na **1..\*** .

   Na ilustracji co najmniej jedno Restauracje może wziąć udział w realizacji tej samej kolejności posiłków.

- Aby pokazać, że każdy aktor może uczestniczyć w tym samym czasie w kilku wystąpieniach przypadku użycia, ustaw liczebność na końcu przypadku użycia skojarzenia do **\*** .

   Na ilustracji każda restauracji może obsłużyć więcej niż jedno zamówienie jednocześnie.

##### <a name="to-set-multiplicities-on-an-association"></a>Aby ustawić Iloczyny dla skojarzenia

1. Kliknij prawym przyciskiem myszy skojarzenie, a następnie kliknij polecenie **Właściwości**.

2. Rozwiń węzeł **pierwsza rola** lub **druga rola**.

    *Rola* oznacza element na jednym końcu skojarzenia.

3. Ustaw właściwość liczebności, wybierając ją z listy:

   - **1** w celu oznaczania, że dokładnie jedno wystąpienie tej roli uczestniczy w każdym łączu.

   - **1..\*** , aby mieć możliwość, że co najmniej jedno wystąpienie tej roli uczestniczy w każdym łączu.

   - **0.. 1** , aby podać, że uczestnictwo jest opcjonalne.

   - **\*** , aby wyrównać, że zero lub więcej wystąpień tej roli uczestniczy w łączu.

> [!NOTE]
> Wiele zespołów nie umieszcza informacji o liczebności na diagramach przypadków użycia, pozostawiając liczebność przy wartości domyślnej 1. Zamiast tego dostarczają informacje w oddzielnych opisach przypadków użycia. W takim przypadku wszystkie liczebność na diagramach przypadków użycia zostaną ukryte.

### <a name="using-an-actor-or-use-case-on-multiple-diagrams"></a>Używanie aktora lub przypadku użycia na wielu diagramach
 Można wyświetlić te same aktory i przypadki użycia na kilku diagramach. Na przykład:

- W różnych diagramach można opisać różne przypadki użycia, w których bierze się jeden aktor.

- Można użyć jednego diagramu, aby pokazać aktory i podsystemy, z którymi jest skojarzony przypadek użycia, i użyć innego diagramu, aby pokazać, jak przypadek użycia jest podzielony na uwzględnione i rozszerzone przypadki użycia.

##### <a name="to-show-the-same-actor-or-use-case-on-different-diagrams"></a>Aby wyświetlić ten sam aktor lub przypadek użycia na różnych diagramach

1. Utwórz aktora lub przypadek użycia na jednym diagramie.

2. Utwórz inny diagram przypadków użycia.

3. Przeciągnij aktora lub wykorzystaj przypadek **Eksploratora modelu** na nowym diagramie.

    > [!NOTE]
    > Jeśli umieścisz na nowym diagramie aktora i przypadku użycia, które są już skojarzone, skojarzenie między nimi zostanie automatycznie wyświetlone na nowym diagramie.

## <a name="Details"></a>Szczegółowe opisywanie przypadków użycia
 Przypadek użycia reprezentuje:

- Cel aktora w korzystaniu z systemu, taki jak **zakup posiłku**; lub

- Co najmniej jeden *scenariusz*, czyli sekwencje kroków wykonywanych w celu osiągnięcia celu, na przykład: {**Order posiłk, Pay, Delivery**}. Oprócz scenariuszy zakończonych powodzeniem może istnieć kilka scenariuszy wyjątków lub niepowodzeń, takich jak **karta kredytowa odrzucona**.

  Przypadek użycia można opisać na różnych poziomach szczegółowości. Na wczesnym etapie projektowania wystarczy nazwa na diagramie przypadków użycia.  Później można napisać bardziej szczegółowe opisy scenariuszy.

  W Visual Studio Ultimate można opisać przypadek użycia na kilka sposobów, które mogą być używane osobno lub razem:

- Połącz przypadek użycia z innym diagramem lub diagramami w projekcie.

  - Diagram aktywności ułatwia wyjaśnienie bardziej złożonej procedury, w której istnieją pętle, gałęzie i równoległe wątki. Może również wyświetlać przepływ danych między częściami procesu. Aby uzyskać więcej informacji, zobacz [diagramy aktywności UML: wytyczne](../modeling/uml-activity-diagrams-guidelines.md).

  - Diagram sekwencji ułatwia wyjaśnienie złożonej serii interakcji między różnymi aktorami. Można go również użyć, aby zobaczyć, co się dzieje w systemie w odpowiedzi na poszczególne przypadki użycia. Aby uzyskać więcej informacji, zobacz [diagramy sekwencji UML: wytyczne](../modeling/uml-sequence-diagrams-guidelines.md).

- Połącz przypadek użycia z stroną, sekcją lub akapitem programu OneNote opisującym przypadek użycia.

- Połącz przypadek użycia z dokumentem programu Word, w którym używasz tekstu, zrzutów ekranu itd., aby opisać scenariusze przypadku użycia. Aby uzyskać więcej informacji, zobacz [wymagania dotyczące modelu użytkownika](../modeling/model-user-requirements.md).

#### <a name="to-link-a-use-case-to-a-diagram-or-file-in-the-same-solution"></a>Aby połączyć przypadek użycia z diagramem lub plikiem w tym samym rozwiązaniu

1. Narysuj diagram, taki jak diagram sekwencji lub diagram aktywności, aby zilustrować scenariusz przypadków użycia.

2. Wróć do diagramu przypadków użycia.

3. Przeciągnij diagram lub plik z Eksplorator rozwiązań na pustą część diagramu przypadków użycia.

4. Nawiąż połączenie z artefaktu z przypadkiem użycia przy użyciu **zależności**.

#### <a name="to-link-to-a-solution-file-such-as-a-word-document-or-powerpoint-presentation"></a>Aby utworzyć link do pliku rozwiązania, takiego jak dokument programu Word lub prezentacja programu PowerPoint

1. Napisz dokument, który używa tekstu, zrzutów ekranu i tak dalej, aby opisać scenariusz przypadków użycia.

2. Dodaj dokument do rozwiązania.

    1. Przenieś dokument programu Word do tego samego folderu systemu Windows, w którym znajduje się rozwiązanie.

    2. W Eksplorator rozwiązań kliknij prawym przyciskiem myszy rozwiązanie, wskaż polecenie **Dodaj**, a następnie kliknij pozycję **istniejący element**.

    3. Przejdź do dokumentu programu Word i kliknij przycisk **Dodaj**.

         Dokument programu Word zostanie wyświetlony w folderze rozwiązania w Eksplorator rozwiązań.

3. Przeciągnij dokument programu Word z Eksplorator rozwiązań na pustą część diagramu przypadków użycia.

     Zostanie wyświetlony nowy artefakt.

4. Nawiąż połączenie z artefaktu z przypadkiem użycia przy użyciu **zależności**.

#### <a name="to-link-to-a-shared-document-onenote-element-or-web-page"></a>Aby połączyć się z dokumentem udostępnionym, elementem programu OneNote lub stroną sieci Web

1. Uzyskaj adres URL elementu udostępnionego. Może to być na przykład ścieżką pliku sieciowego rozpoczynającą się "\\\\" lub stronę sieci Web lub adres URL programu SharePoint, zaczynając od "http://" lub link do sekcji programu OneNote, strony lub akapitu rozpoczynającego się "OneNote:".

2. W przyborniku kliknij pozycję **artefakt** , a następnie kliknij pozycję na diagramie przypadku użycia.

3. Po wybraniu nowego artefaktu wpisz lub wklej adres URL do właściwości **Hyperlink** .

> [!NOTE]
> Możesz kliknąć dwukrotnie artefakt, aby otworzyć diagram lub dokument, do którego się łączą.

### <a name="linking-use-cases-to-work-items"></a>Łączenie przypadków użycia z elementami roboczymi
 Jeśli projekt używa [!INCLUDE[vstsTfsRosarioLong](../includes/vststfsrosariolong-md.md)] i masz [!INCLUDE[esprtfc](../includes/esprtfc-md.md)], można połączyć każdy przypadek użycia z elementem roboczym w [!INCLUDE[esprfound](../includes/esprfound-md.md)]. Aby dowiedzieć się, jak utworzyć te linki, zobacz [łączenie elementów modelu i elementów roboczych](../modeling/link-model-elements-and-work-items.md).

 Dzięki temu można:

- Opisz przypadek użycia w połączonym elemencie roboczym. W szczególności, jeśli projekt używa formalnego szablonu procesu programu Visual Studio, można połączyć się z elementem roboczym przypadku użycia. Ten typ elementu pracy zawiera pola opisujące cele i scenariusze przypadku użycia.

- Połącz przypadki testowe z przypadkiem użycia, aby można było uzyskać raporty na temat tego, jak daleko opracowywany kod implementuje przypadek użycia.

- Połącz zadania z przypadkiem użycia, aby śledzić postęp prac programistycznych.

## <a name="Structuring"></a>Tworzenie struktury przypadków użycia
 Należy spróbować opisać zachowanie systemu, korzystając z zaledwie kilku najważniejszych przypadków użycia. Każdy duże przypadki użycia definiuje główny cel, który osiąga aktor, taki jak kupowanie produktu lub, od punktu widzenia dostawcy, dostarczając produkty do sprzedaży.

 Po wybraniu tych celów możesz przejść do bardziej szczegółowych informacji na temat sposobu osiągnięcia poszczególnych celów i różnic w podstawowych celach.

 Unikaj deredagowania przypadków użycia w zbyt dużej szczegółowości. Przypadki użycia dotyczą środowiska użytkownika systemu, a nie od jego wewnętrznych zadań roboczych. Ponadto ogólnie mówiąc, bardziej wydajniej będzie można tworzyć wczesne wersje kodu, a nie poświęcać ich na szczegółowe informacje.

 Można podsumować na diagramie przypadku użycia relacje między głównymi i bardziej szczegółowymi przypadkami użycia. W poniższych sekcjach opisano:

- [Wyświetlanie szczegółów dotyczących przypadku użycia z dołączeniem](#Include)

- [Cele udostępniania z generalizacją](#Inheritance)

- [Oddzielenie przypadków wariantów z rozszerzeniem](#Extend)

### <a name="Include"></a>Wyświetlanie szczegółów dotyczących przypadku użycia z dołączeniem
 Użyj relacji **include** , aby pokazać, że jeden przypadek użycia opisuje niektóre szczegóły innego. Na ilustracji **Porządkuj mączkę** obejmują **płatność**, **Wybierz menu**, a **następnie wybierz element menu**. Każdy z dołączanych, bardziej szczegółowych przypadków użycia jest krokiem, który aktor lub aktory mogą wykonać w celu osiągnięcia ogólnego celu, w tym przypadku użycia. Strzałka powinna wskazywać na bardziej szczegółowy, uwzględniony przypadek użycia.

> [!CAUTION]
> Nie należy tworzyć pętli z uwzględnieniem relacji, które powodują użycie przypadku użycia, w tym samego siebie. Pętle mogą generować błędy.

 Można udostępniać dołączone przypadki użycia. W przykładzie **zamówienie a posiłk** i **subskrybowanie do przeglądu** przypadków użycia obejmuje **płatność**.

 ![Przypadki użycia rozłożone z uwzględnieniem](../modeling/media/uml-ucguideinclude.png "UML_UCGuideInclude")

 Celem i scenariuszom dołączonego przypadku użycia powinno być niezależnie, aby można je było uwzględnić w przypadku użycia, które zostały zaprojektowane w późniejszym czasie.

 Oddzielenie przypadków użycia do dołączania i zawartych części jest przydatne do osiągnięcia następujących celów:

- Strukturę opisów przypadków użycia należy podzielić na różne warstwy szczegółów.

- Unikaj powtarzających się scenariuszy udostępnionych w różnych przypadkach użycia.

#### <a name="Steps"></a>Definiowanie kolejności szczegółowych czynności
 Diagram przypadków użycia nie zawiera żadnych informacji o kolejności, w której należy wykonać bardziej szczegółowe czynności, ani o tym, czy każdy z nich jest zawsze potrzebny.

 Aby kolejność kroków została wyczyszczona, można użyć **artefaktu** do dołączenia oddzielnego dokumentu do dołączania do niego przypadku użycia. W poniższym przykładzie diagram aktywności dołączony do zamówienia w przypadku użycia posiłku. Alternatywnie można użyć dokumentu tekstowego z listą kroków lub sekwencji zrzutów ekranu. Aby uzyskać więcej informacji, zobacz [szczegółowo opis przypadków użycia](#Details).

 Zwróć uwagę na te konwencje nazewnictwa w przypadku korzystania z diagramu aktywności:

- Nazwa całego działania jest taka sama jak w przypadku użycia.

- Akcje na diagramie aktywności mają takie same nazwy jak uwzględnione przypadki użycia.

  Aby uzyskać więcej informacji, zobacz [diagramy aktywności UML: wytyczne](../modeling/uml-activity-diagrams-guidelines.md).

  ![Kroki przypadków użycia pokazane w połączonym diagramie aktywności](../modeling/media/uml-ucguidesteps.png "UML_UCGuideSteps")

### <a name="Inheritance"></a>Cele udostępniania z generalizacją
 Użyj relacji generalizacji, aby pokazać, że *wyspecjalizowany* przypadek użycia jest szczególnym sposobem osiągnięcia celów wyrażonych przez inny *ogólny* przypadek użycia. Otwarta strzałka powinna wskazywać na bardziej ogólne przypadki użycia.

 ![Przypadki użycia pokazujące relację generalizacji](../modeling/media/uml-ucguidegeneral.png "UML_UCGuideGeneral")

 Na przykład **płatność** za generalizacje reguluje **płatność kartą kredytową** i **płatność gotówką**.

> [!CAUTION]
> Nie należy tworzyć pętli relacji generalizacji, co spowoduje generalizację aktora. Pętle mogą generować błędy.

 Wyspecjalizowane przypadki użycia mogą pomóc w pokazywania różnych sposobów osiągnięcia tego samego celu przez system.

 Wyspecjalizowane przypadki użycia są uważane za dziedziczenie celów i uczestników ogólnego przypadku użycia. Ogólny przypadek użycia nie musi mieć własnych scenariuszy; jego specjalizacje opisują różne sposoby osiągnięcia celów.

##### <a name="to-refactor-common-goals-from-two-or-more-use-cases"></a>Aby refaktoryzacji typowe cele z dwóch lub więcej przypadków użycia

1. Utwórz nowy ogólny przypadek użycia i nadaj mu nazwę.

2. Utwórz relację **generalizacji** z dużą strzałką wskazującą w nowym ogólnym przypadku użycia.

    1. Kliknij pozycję **Generalizacja** w przyborniku.

    2. Kliknij wyspecjalizowany przypadek użycia (**płatność według karty kredytowej** w przykładzie).

    3. Kliknij ogólny przypadek użycia (**płatność** w przykładzie).

3. Jeśli zostały opisane cele dla wyspecjalizowanych przypadków użycia, Przenieś wspólne części do opisu ogólnego przypadku użycia.

4. Aktory, które są współużytkowane przez wyspecjalizowane przypadki użycia, można przenieść do ogólnego przypadku użycia.

### <a name="Extend"></a>Oddzielanie przypadków wariantów z rozszerzeniem
 Użyj linku rozszerzonego, aby pokazać, że jeden przypadek użycia może dodawać funkcjonalność do innego przypadku użycia w pewnych okolicznościach. Strzałka powinna wskazywać na głównym, rozszerzonym przypadku użycia.

 ![Jeden przypadek użycia rozszerzający inny](../modeling/media/uml-ucguideextend.png "UML_UCGuideExtend")

> [!CAUTION]
> Nie należy tworzyć pętli dla relacji rozszerzających, co spowoduje generalizację aktora. Pętle mogą generować błędy.

 Na przykład przypadek użycia **logowania** typowej witryny sieci Web może obejmować **Rejestrowanie nowego użytkownika** , ale tylko wtedy, gdy użytkownik nie ma jeszcze konta.

##### <a name="to-separate-a-use-case-into-main-and-extending-parts"></a>Aby rozdzielić przypadek użycia na główne i rozszerzające części

1. Utwórz nowy przypadek użycia rozszerzenia i nadaj mu nazwę.

2. Utwórz relację **rozszerzania** za pomocą strzałki wskazującej rozszerzoną wielkość użycia.

   1. Kliknij przycisk **Rozciągnij** w przyborniku.

   2. Kliknij rozszerzanie przypadku użycia (w przykładzie**Zarejestruj nowego użytkownika** ).

   3. Kliknij rozszerzony przypadek użycia (**Logowanie** w przykładzie).

       > [!NOTE]
       > Unikaj tworzenia pętli rozszerzającej relacje na diagramie. Jeśli przypadek użycia ma być rozszerzeniem siebie, jest nieprawidłowy.

3. Jeśli utworzono już scenariusze dla rozszerzonego przypadku użycia, Przenieś odpowiednie kroki do scenariusza rozszerzenia.

4. Opis rozszerzenia (**Zarejestruj nowego użytkownika** w przykładzie) powinien zawierać szczegółowe informacje o tym, gdzie znajdują się w głównym scenariuszu przypadku użycia i w jakich okolicznościach. Należy je traktować jako modyfikując Opis głównej wielkości liter.

   Przypadek użycia rozszerzenia reprezentuje czynności scenariusza, które w przeciwnym razie byłyby częścią głównych scenariuszy przypadków użycia. Scenariusz i cel rozszerzenia zawsze będą odczytywane w kontekście głównego przypadku użycia, dlatego nie muszą być przydatne niezależnie.

   Oddzielenie rozszerzeń może być przydatne do opisywania następujących sytuacji:

- Istnieją dodatkowe podmioty, które są zaangażowane tylko w przypadku użycia rozszerzenia. Na przykład administrator musi zatwierdzić rejestrację klienta w witrynie sieci Web.

- Oddzielny podsystem rozwiąże się z przypadkiem użycia rozszerzenia.

- To rozszerzenie będzie dostępne tylko w określonych wersjach systemu. Każdą wersję można wyświetlić jako oddzielny podsystem na diagramie przypadków użycia.

## <a name="Subsystems"></a>Używanie granic podsystemu
 Użyj granicy podsystemu, aby zobaczyć, jakie przypadki użycia znajdują się w zakresie Twojego systemu.

#### <a name="to-draw-a-subsystem-boundary"></a>Aby narysować granicę podsystemu

1. W przyborniku kliknij pozycję **podsystem**, a następnie kliknij diagram.

    Podsystem pojawia się na diagramie.

2. Przeciągnij rogi podsystemu, aby dostosować jego rozmiar.

3. Przeciągnij istniejące przypadki użycia do podsystemu lub z niego, aby dostosować jego zawartość.

   \- lub —

   Aby utworzyć nowy przypadek użycia bezpośrednio w podsystemie, kliknij pozycję **przypadek użycia** w przyborniku, a następnie kliknij wewnątrz podsystemu.

> [!NOTE]
> Właściwość **podmiotu** przypadku użycia wskazuje, który podsystem jest zawarty w.

### <a name="use-cases-outside-the-system-scope"></a>Przypadki użycia poza zakresem systemowym
 Często warto uwzględnić w przypadku przypadków użycia diagramów, które są częścią firmy, ale nie są obsługiwane przez opracowywany system. Dzięki temu deweloperzy mogą zrozumieć kontekst swojej pracy. Na przykład dostarczenie posiłku może być pokazane jako przypadek użycia obejmujący uczestników restauracji i klienta, ale poza obowiązkiem witryny sieci Web zamawiania posiłków.

### <a name="multiple-subsystems"></a>Wiele podsystemów
 Można utworzyć kilka granic podsystemu, aby pokazać, jak różne przypadki użycia są rozpatrywane przez różne składniki systemu. Na przykład w przypadku witryny sieci Web dotyczącej forum mogą być rozpatrywane **dodatkowe oceny restauracji** . Należy pamiętać, że diagram przypadków użycia powinien dotyczyć elementów widocznych dla użytkownika. Jeśli chcesz opisać wewnętrzny podział pracy w systemie, rozważ użycie diagramu składników.

### <a name="system-versions"></a>Wersje systemu
 Aby zilustrować różne wersje systemu, można użyć różnych granic podsystemu. Na przykład przypadek użycia płatność może być uwzględniony w witrynie sieci Web w wersji 2, ale nie w wersji 1. oznacza to, że system pomaga klientom w realizacji zamówień. Jednak muszą oni bezpośrednio uiścić restauracji.

 Użyj relacji **zależności** , aby połączyć podsystemy reprezentujące różne wersje lub warianty.

 ![Podsystemy pokazują różne wersje systemu](../modeling/media/uml-ucguidesystem.png "UML_UCGuideSystem")

## <a name="see-also"></a>Zobacz też
 [Wymagania dotyczące modelu](../modeling/model-user-requirements.md) [UML diagramy sekwencji: wskazówki](../modeling/uml-sequence-diagrams-guidelines.md) [Edytowanie modeli UML i](../modeling/edit-uml-models-and-diagrams.md) diagramów [diagramów przypadków użycia UML: referencyjne](../modeling/uml-use-case-diagrams-reference.md) diagramy [klas UML: referencyjne](../modeling/uml-class-diagrams-reference.md) diagramy [składników UML:](../modeling/uml-component-diagrams-reference.md) referencyjne [diagramy działań UML: schematy](../modeling/uml-activity-diagrams-guidelines.md) [wideo: organizowanie funkcji w przypadku użycia](https://channel9.msdn.com/blogs/clinted/uml-with-vs-2010-part-2-organizing-features-into-use-cases)
