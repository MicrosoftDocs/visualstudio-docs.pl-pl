---
title: C# IntelliSense
description: Dowiedz się więcej o niektórych funkcjach IntelliSense, których można używać podczas kodowania projektu C#.
ms.custom: SEO-VS-2020
ms.date: 06/01/2021
ms.topic: conceptual
helpviewer_keywords:
- C#, IntelliSense
- IntelliSense [C#]
author: mikadumont
ms.author: midumont
manager: jmartens
ms.workload:
- dotnet
ms.openlocfilehash: 3156b1236a130478d83fe82c8fa462a1144a8e6a
ms.sourcegitcommit: f50bbdb15c4f9fca0fa245ca765183c378960cc5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/03/2021
ms.locfileid: "111351958"
---
# <a name="c-intellisense"></a>C# IntelliSense

Funkcja IntelliSense w języku C# jest dostępna podczas kodowania w edytorze i podczas debugowania w oknie [poleceń trybu natychmiastowego.](../ide/reference/immediate-window.md)

## <a name="completion-lists"></a>Listy uzupełniania

Listy uzupełniania IntelliSense w języku C# zawierają tokeny z elementów członkowskich listy, uzupełniania wyrazów i nie tylko. Zapewnia szybki dostęp do:

- Elementy członkowskie typu lub przestrzeni nazw

- Nazwy zmiennych, poleceń i funkcji

- Fragmenty kodu

- Słowa kluczowe języka

- Metody rozszerzeń

Lista uzupełniania w języku C# jest również wystarczająco inteligentna, aby odfiltrować nieistotne tokeny i wstępnie wybrać token na podstawie kontekstu. Aby uzyskać więcej informacji, zobacz [Filtrowane listy uzupełniania](#filtered-completion-lists).

### <a name="code-snippets-in-completion-lists"></a>Fragmenty kodu na listach uzupełniania

W języku C# lista uzupełniania zawiera fragmenty kodu, które ułatwiają wstawianie wstępnie zdefiniowanych treści kodu do programu. Fragmenty kodu są wyświetlane na liście uzupełniania jako tekst skrótu [fragmentu kodu](../ide/code-snippets-schema-reference.md#shortcut-element). Aby uzyskać więcej informacji na temat fragmentów kodu, które są domyślnie dostępne w języku C#, zobacz Fragmenty kodu języka [C#.](../ide/visual-csharp-code-snippets.md)

### <a name="language-keywords-in-completion-lists"></a>Słowa kluczowe języka na listach uzupełniania

W języku C# lista uzupełniania zawiera również słowa kluczowe języka. Aby uzyskać więcej informacji na temat słów kluczowych języka C#, zobacz [Słowa kluczowe języka C#.](/dotnet/csharp/language-reference/keywords/index)

### <a name="extension-methods-in-completion-lists"></a>Metody rozszerzeń na listach uzupełniania

W języku C# lista uzupełniania zawiera metody rozszerzenia, które znajdują się w zakresie.

> [!NOTE]
> Lista uzupełniania nie zawiera wszystkich metod rozszerzenia dla <xref:System.String> obiektów.

Metody rozszerzeń używają innej ikony niż metody wystąpienia. Aby uzyskać przewodnik referencyjny dotyczący ikon listy, [zobacz Widok klasy i Przeglądarka obiektów](../ide/class-view-and-object-browser-icons.md). Gdy zarówno metoda wystąpienia, jak i metoda rozszerzenia o tej samej nazwie znajdują się w zakresie, na liście uzupełniania jest wyświetlana ikona metody rozszerzenia.

### <a name="filtered-completion-lists"></a>Filtrowane listy uzupełniania

Funkcja IntelliSense usuwa niepotrzebne elementy członkowskie z listy uzupełniania przy użyciu filtrów. Język C# filtruje listy uzupełniania wyświetlane dla tych elementów:

- **Interfejsy i klasy bazowe:** funkcja IntelliSense automatycznie usuwa elementy z interfejsu i list uzupełniania klas bazowych, zarówno na listach podstawowych deklaracji klas, jak i listach ograniczeń. Na przykład wylinia nie są wyświetlane na liście uzupełniania dla klas bazowych, ponieważ wyli nie mogą być używane dla klas bazowych. Lista uzupełniania klas bazowych zawiera tylko interfejsy i przestrzenie nazw. Jeśli wybierzesz element na liście, a następnie wpiszesz przecinek, funkcja IntelliSense usunie klasy bazowe z listy uzupełniania, ponieważ język C# nie obsługuje wielokrotnego dziedziczenia. To samo zachowanie występuje również w przypadku klauzul ograniczeń.

- **Atrybuty:** po zastosowaniu atrybutu do typu lista uzupełniania jest filtrowana tak, aby lista zawierała tylko te typy, które pochodzą z przestrzeni nazw zawierających te typy, takie jak <xref:System.Attribute> .

- **Klauzule Catch**

- **Inicjatory obiektów:** na liście uzupełniania będą wyświetlane tylko elementy członkowskie, które można zainicjować.

- **new —** słowo kluczowe: po wpisaniu `new` i naciśnięciu **klawisza Spacja** zostanie wyświetlona lista uzupełniania. Element jest automatycznie wybierany na liście na podstawie kontekstu w kodzie. Na przykład elementy są automatycznie wybierane na liście uzupełniania dla deklaracji i dla instrukcji return w metodach.

- **Słowo kluczowe enum:** po naciśnięciu klawisza **Spacja** po znaku równości w celu przypisania wyli zostanie wyświetlona lista uzupełniania. Element jest automatycznie wybierany na liście na podstawie kontekstu w kodzie. Na przykład elementy są automatycznie wybierane na liście uzupełniania po wpisaniu słowa kluczowego return i podczas deklaracji.

- **operatory as i is**: filtrowana lista uzupełniania jest wyświetlana automatycznie po naciśnięciu klawisza **Spacja** po wpisaniu słowa `as` kluczowego lub `is` .

- **Zdarzenia:** po wpisaniu słowa kluczowego `event` lista uzupełniania zawiera tylko typy delegatów.

- **Parametr pomaga** automatycznie sortować do pierwszego przeciążenia metody, które pasuje do parametrów podczas ich wprowadzania. Jeśli dostępnych jest wiele przeciążeń metod, możesz użyć strzałek w górę i w dół, aby przejść do następnego możliwego przeciążenia na liście.

### <a name="most-recently-used-members"></a>Ostatnio używane elementy członkowskie

Funkcja IntelliSense zapamiętuje ostatnio wybrane elementy członkowskie w oknie podręcznym [Elementy](../ide/using-intellisense.md) członkowskie listy w celu automatycznego uzupełniania nazw obiektów. Przy następnym użyciu listy **członków** u góry są wyświetlane ostatnio używane elementy członkowskie. Historia ostatnio używanych elementów członkowskich jest czyszona między poszczególnymi Visual Studio użytkownikami.

### <a name="override"></a>override

Po [wpisaniu przesłonięcia](/dotnet/csharp/language-reference/keywords/override) i naciśnięciu klawisza **Spacja** funkcja IntelliSense wyświetla wszystkie prawidłowe składowe klasy bazowej, które można zastąpić w wyskakującym polu listy. Wpisanie zwracanych typów metody po wyświetleniu monitu funkcji IntelliSense o pokazanie tylko tych metod, `override` które zwracają ten sam typ. Gdy funkcja IntelliSense nie może znaleźć żadnych dopasowania, wyświetla wszystkie składowe klasy bazowej.

### <a name="ai-enhanced-intellisense"></a>Funkcja IntelliSense rozszerzona o AI

[Visual Studio IntelliCode udostępnia](/visualstudio/intellicode/intellicode-visual-studio) listy uzupełniania intelliSense ulepszone ze sztucznej inteligencji. Funkcja IntelliCode przewiduje najbardziej prawdopodobny poprawny interfejs API do użycia, a nie tylko prezentowanie alfabetycznej listy elementów członkowskich. Używa ona bieżącego kontekstu kodu i wzorców w celu zapewnienia listy dynamicznej.

## <a name="automatic-code-generation"></a>Automatyczne generowanie kodu

### <a name="add-using"></a>Dodawanie using

Operacja **Dodaj przy użyciu** funkcji IntelliSense automatycznie dodaje wymaganą `using` dyrektywę do pliku kodu. Ta funkcja umożliwia skoncentrowanie się na pisanych kodach, a nie na konieczności zmiany fokusu na inną część kodu.

Aby zainicjować **operację Dodaj przy** użyciu, umieść kursor na odwołaniach do typu, których nie można rozpoznać. Na przykład podczas tworzenia aplikacji konsolowej, a następnie dodawania do treści metody, w tym wierszu kodu pojawia się czerwony zygniak, ponieważ nie można rozpoznać odwołania `XmlReader` `Main` do typu. Następnie możesz wywołać pozycję **Dodaj przy użyciu za** pomocą **szybkich akcji**. Szybkie **akcje są** widoczne tylko wtedy, gdy kursor jest umieszczony na typie niepowiązanych.

![Dodawanie obrazu rozwiniętego przy użyciu szybkiej akcji](../ide/media/addusing-quickaction.png)

Kliknij ikonę żarówki błędu, a następnie wybierz **pozycję using System.Xml;,** aby automatycznie dodać dyrektywę using.

### <a name="add-missing-using-directives-on-paste"></a>Dodawanie brakujących dyrektyw using przy wklejaniu

Funkcja IntelliSense może automatycznie dodawać brakujące `using` dyrektywy do kodu po wklejeniu typu do pliku kodu. Ta funkcja pozwala zaoszczędzić czas dzięki automatyzacji zadania dodawania brakujących dyrektyw using podczas wklejania typu do pliku. Włącz tę funkcję w **edytorze tekstów**  >  **Opcje**  >  **narzędzi**  >  **C#** lub Basic  >  **Advanced** i wybierz pozycję Dodaj brakujące dyrektywy using przy wklejeniu .

### <a name="remove-and-sort-usings"></a>Usuwanie i sortowanie using

Opcja **Usuń i sortuj deklaracje Usings** sortuje i usuwa deklaracje i bez zmiany `using` zachowania kodu `extern` źródłowego. Z czasem pliki źródłowe mogą stać się coraz bardziej utrudnione i trudne do odczytania z powodu niepotrzebnych i `using` niezorganizowanych dyrektyw. Opcja **Usuń i sortuj** using kompaktuje kod źródłowy przez usunięcie nieużywanych dyrektyw i zwiększa czytelność `using` dzięki posortowaniu ich. W menu **Edycja** wybierz pozycję **IntelliSense,** a następnie wybierz pozycję **Organizuj using.**

### <a name="implement-interface"></a>Implementowanie interfejsu

Funkcja IntelliSense udostępnia opcję, która pomaga zaimplementować [interfejs](/dotnet/csharp/language-reference/keywords/interface) podczas pracy w edytorze kodu. Zwykle, aby poprawnie zaimplementować interfejs, należy utworzyć deklarację metody dla każdego członka interfejsu w klasie. Przy użyciu funkcji IntelliSense po wpisaniu nazwy interfejsu  w deklaracji klasy jest wyświetlana żarówka Szybkie akcje. Żarówka zapewnia opcję automatycznego implementowania interfejsu przy użyciu jawnego lub niejawnego nazewnictwa. W przypadku jawnego nazewnictwa deklaracje metod noszą nazwę interfejsu. W obszarze niejawnego nazewnictwa deklaracje metod nie wskazują interfejsu, do którego należą. Jawnie nazwana metoda interfejsu jest dostępna tylko za pośrednictwem wystąpienia interfejsu, a nie wystąpienia klasy. Aby uzyskać więcej informacji, zobacz [Jawna implementacja interfejsu](/dotnet/csharp/programming-guide/interfaces/explicit-interface-implementation).

Implementacja interfejsu generuje minimalną liczbę wycinki metody, która jest wymagana do spełnienia interfejsu. Jeśli klasa bazowa implementuje części interfejsu, te wycinki nie są ponownie generowany.

### <a name="implement-abstract-base-class"></a>Implementowanie abstrakcyjnej klasy bazowej

Funkcja IntelliSense udostępnia opcję, która pomaga automatycznie implementować składowe abstrakcyjnej klasy bazowej podczas pracy w edytorze kodu. Zwykle implementowanie składowych abstrakcyjnej klasy bazowej wymaga utworzenia nowej definicji metody dla każdej metody abstrakcyjnej klasy bazowej w klasie pochodnej. Przy użyciu funkcji IntelliSense po wpisaniu nazwy abstrakcyjnej  klasy bazowej w deklaracji klasy jest wyświetlana żarówka Szybkich akcji. Żarówka zapewnia opcję automatycznego implementowania metod klasy bazowej.

Wycinki metody generowane przez funkcję  Implementuj abstrakcyjną klasę bazową są modelowane za pomocą fragmentu kodu zdefiniowanego w pliku *MethodStub.snippet*. Fragmenty kodu można modyfikować. Aby uzyskać więcej informacji, [zobacz Przewodnik: tworzenie fragmentu kodu](../ide/walkthrough-creating-a-code-snippet.md).

### <a name="generate-from-usage"></a>Generowanie na podstawie użycia

Funkcja **Generuj na** podstawie użycia umożliwia korzystanie z klas i składowych przed ich zdefiniowaniem. Można wygenerować wycinki dla dowolnej klasy, konstruktora, metody, właściwości, pola lub wyli możemy użyć, ale nie zostały jeszcze zdefiniowane. Możesz generować nowe typy i elementy członkowskie bez opuszczania bieżącej lokalizacji w kodzie. Pozwala to zminimalizować przerwy w przepływie pracy.

Pod każdym niezdefiniowym identyfikatorem jest wyświetlane czerwone podkreślenie faliste. Gdy na identyfikatorze znajduje się wskaźnik myszy, w etykietce narzędzia zostanie wyświetlony komunikat o błędzie. Aby wyświetlić odpowiednie opcje, można użyć jednej z następujących procedur:

- Kliknij niezdefiniowany identyfikator. Pod **identyfikatorem pojawi** się żarówka błędu Szybkie akcje. Kliknij żarówkę błędu.

- Kliknij niezdefiniowany identyfikator, a następnie naciśnij klawisz **Ctrl** + **.** **(Ctrl** + okres).

- Kliknij prawym przyciskiem myszy niezdefiniowany identyfikator, a następnie kliknij pozycję Szybkie **akcje i refaktoryzowanie.**

Wyświetlone opcje mogą obejmować następujące elementy:

- **Generowanie właściwości**

- **Generowanie pola**

- **Generowanie metody**

- **Generowanie klasy**

- **Generowanie nowego typu** (dla klasy, struktury, interfejsu lub wyliczania)

## <a name="generate-event-handlers"></a>Generowanie programów obsługi zdarzeń

W edytorze kodu funkcja IntelliSense może pomóc w podłączaniu metod (programów obsługi zdarzeń) do pól zdarzeń.

Po wpisaniu operatora po polu zdarzenia w pliku cs funkcja IntelliSense wyświetli monit z opcją `+=` naciśnięcia **klawisza Tab.**  Powoduje to wstawienie nowego wystąpienia delegata, który wskazuje na metodę obsługą zdarzenia.

![Automatyczne podłączanie przycisku](../ide/media/vxautohookup.gif)

Po naciśnięciu **klawisza Tab** funkcja IntelliSense automatycznie zakończy instrukcje i wyświetli odwołanie do obsługi zdarzeń jako zaznaczony tekst w edytorze kodu. Aby zakończyć automatyczne podłączanie zdarzeń, funkcja IntelliSense monituje o naciśnięcie klawisza **Tab** ponownie w celu utworzenia pustego wyciskania dla programu obsługi zdarzeń.

![Generuj program obsługi zdarzeń](../ide/media/vxgenerateeventhandler.gif)

> [!NOTE]
> Jeśli nowy delegat utworzony przez mechanizm IntelliSense odwołuje się do istniejącej procedury obsługi zdarzeń, funkcja IntelliSense przekazuje te informacje w etykietce narzędzia. Następnie można zmodyfikować to odwołanie. Tekst jest już zaznaczony w edytorze kodu. W przeciwnym razie w tym momencie zostanie ukończone automatyczne podłączanie zdarzeń.

Po naciśnięciu **klawisza Tab** funkcja IntelliSense wycięła metodę z poprawną sygnaturą i umieściła kursor w treści procedury obsługi zdarzeń.

> [!NOTE]
> Użyj polecenia **Przejdź do tyłu** w menu **Widok** **(Ctrl),** aby wrócić do instrukcji + **-** podłączania zdarzeń.

## <a name="see-also"></a>Zobacz też

- [Korzystanie z funkcji IntelliSense](../ide/using-intellisense.md)
- [Visual Studio IDE](../get-started/visual-studio-ide.md)
