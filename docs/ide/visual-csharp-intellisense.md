---
title: C# IntelliSense
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- C#, IntelliSense
- IntelliSense [C#]
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: ef4f8974f448ad9e2e81d4f1ba98aa02ed9da354
ms.sourcegitcommit: 4d9c54f689416bf1dc4ace058919592482d02e36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/19/2019
ms.locfileid: "58194607"
---
# <a name="c-intellisense"></a>C# IntelliSense

Funkcja IntelliSense języka C# jest dostępny podczas kodowania w edytorze i podczas debugowania w [tryb natychmiastowy](../ide/reference/immediate-window.md) okna poleceń.

## <a name="completion-lists"></a>Listy uzupełniania

Listy uzupełniania IntelliSense w języku C# zawiera tokenów z listy elementów członkowskich, Dokończ wyraz i innych. Zapewnia ona szybki dostęp do:

- Elementy członkowskie typu lub przestrzeni nazw

- Nazwy funkcji zmiennych i polecenia

- Fragmenty kodu

- Słowa kluczowe języka

- Metody rozszerzenia

Na liście uzupełniania w języku C# jest również inteligentnego odfiltrować tokenów nie ma znaczenia i wstępnie wybierz token na podstawie kontekstu. Aby uzyskać więcej informacji, zobacz [filtrowane listy uzupełniania](#filtered-completion-lists).

### <a name="code-snippets-in-completion-lists"></a>Fragmenty kodu w listach uzupełniania

W języku C# na liście uzupełniania zawiera fragmenty kodu, aby pomóc łatwo Wstawianie wstępnie zdefiniowanych jednostek kodu programu. Fragmenty kodu są wyświetlane na liście uzupełniania jako ten fragment kodu [tekst skrótu](../ide/code-snippets-schema-reference.md#shortcut-element). Aby uzyskać więcej informacji na temat fragmentów kodu, które domyślnie są dostępne w języku C#, zobacz [fragmenty kodu w języku C#](../ide/visual-csharp-code-snippets.md).

### <a name="language-keywords-in-completion-lists"></a>Słowa kluczowe języka w listach uzupełniania

W języku C# na liście uzupełniania zawiera słowa kluczowe języka. Aby uzyskać więcej informacji na temat słowa kluczowe języka C#, zobacz [słowa kluczowe języka C#](/dotnet/csharp/language-reference/keywords/index).

### <a name="extension-methods-in-completion-lists"></a>Metody rozszerzające w listach uzupełniania

W języku C# na liście uzupełniania zawiera metody rozszerzenia, które znajdują się w zakresie.

> [!NOTE]
> Na liście uzupełniania nie są wyświetlane wszystkie metody rozszerzenia dla <xref:System.String> obiektów.

Metody rozszerzające użyj ikony innego niż metody wystąpienia. Podręcznik informacyjny ikonę listy można zobaczyć [ikony w widoku klas i przeglądarki obiektów](../ide/class-view-and-object-browser-icons.md). Gdy metoda wystąpienia i metodę rozszerzenia o tej samej nazwie znajdują się zarówno w zakresie, na liście uzupełniania Wyświetla ikonę metody rozszerzenia.

### <a name="filtered-completion-lists"></a>Filtrowane listy uzupełniania

Funkcja IntelliSense usuwa zbędnych członków z listy uzupełniania przy użyciu filtrów. C# filtry listy uzupełniania, które są wyświetlane dla tych elementów:

- **Podstawowej klasy i interfejsy**: Funkcja IntelliSense automatycznie usuwa elementy z interfejsu i podstawowej klasy listy uzupełniania, w deklaracji klasy podstawowe i interfejs listy i listy ograniczeń. Na przykład wyliczenia nie są wyświetlane na liście uzupełniania dla klas bazowych, ponieważ nie można używać wyliczenia dla klas podstawowych. Na liście uzupełniania klas bazowych zawiera tylko interfejsów i przestrzeni nazw. Jeśli wybierz element na liście, a następnie wpisz przecinek, IntelliSense usuwa klas bazowych z listy uzupełniania, ponieważ C# nie obsługuje dziedziczenie wielokrotne. Takie samo zachowanie występuje także klauzule ograniczenia.

- **Atrybuty**: Po zastosowaniu atrybutu do typu, na liście uzupełniania jest filtrowana, tak aby lista zawiera tylko tych typów, które jest elementem podrzędnym elementu przestrzeni nazw, które zawierają te typy, takie jak <xref:System.Attribute>.

- **Klauzule catch**

- **Inicjatory obiektów**: Tylko elementy członkowskie, które mogą być inicjowane pojawi się na liście uzupełniania.

- **New — słowo kluczowe**: Podczas wpisywania `new` , a następnie naciśnij klawisz **miejsca**, zostanie wyświetlona lista uzupełniania. Automatycznie wybrano element na liście na podstawie kontekstu w kodzie. Na przykład automatycznie zaznaczono elementów na liście uzupełniania dla deklaracji i instrukcjach return w metodzie.

- **Enum — słowo kluczowe**: Po naciśnięciu klawisza **miejsca** po znaku równości przydziału wyliczenia, zostanie wyświetlona lista uzupełniania. Automatycznie wybrano element na liście na podstawie kontekstu w kodzie. Na przykład automatycznie zaznaczono elementów na liście uzupełniania po wpisaniu słowo kluczowe, które są zwracane, a po wprowadzeniu deklaracji.

- **jako operatorów i is**: Listy uzupełniania filtrowane jest wyświetlany automatycznie po naciśnięciu klawisza **miejsca** po wpisaniu `as` lub `is` — słowo kluczowe.

- **Zdarzenia**: Podczas wpisywania słowa kluczowego `event`, na liście uzupełniania zawiera tylko typy delegatów.

- **Parametr pomocy** automatycznie sortuje do pierwsze przeciążenie metody, zgodny z parametrami, podczas ich wprowadzania. Jeśli wiele przeciążeń metody są dostępne, możesz użyć pracy i naciśnij strzałkę, aby przejść do następnego przeciążenia możliwe na liście.

### <a name="most-recently-used-members"></a>Ostatnio używanych elementów członkowskich

Funkcja IntelliSense pamięta elementy członkowskie zaznaczone niedawno w oknie podręcznym [List Members](../ide/using-intellisense.md) pola obiektu automatyczne uzupełnianie nazw. Następnym użyciu **listę elementów członkowskich**, ostatnio używanych elementów członkowskich są wyświetlane u góry. Historia ostatnio używanych elementów członkowskich jest czyszczona między każdej sesji programu Visual Studio.

### <a name="override"></a>override

Podczas wpisywania [zastąpienia](/dotnet/csharp/language-reference/keywords/override) , a następnie naciśnij klawisz **miejsca**, IntelliSense wyświetla wszystkie elementy członkowskie prawidłową klasę podstawową, które można zastąpić w oknie podręcznym listy. Wpisywanie zwracany typ metody po `override` monity funkcji IntelliSense, aby wyświetlić tylko metody, które zwracają tego samego typu. Gdy IntelliSense nie może znaleźć dopasowań, wyświetla wszystkie elementy członkowskie klasy bazowej.

### <a name="ai-enhanced-intellisense"></a>Ulepszone sztucznej Inteligencji IntelliSense

Możesz zainstalować eksperymentalne [rozszerzenia IntelliCode](/visualstudio/intellicode/intellicode-visual-studio) dla programu Visual Studio, który zapewnia ulepszone sztucznej inteligencji na liście uzupełniania IntelliSense. To rozszerzenie przewiduje najprawdopodobniej poprawne interfejsu API do użycia zamiast po prostu prezentowanie alfabetyczną listę elementów członkowskich. Aby zapewnić dynamiczne listy używa Twojego bieżący kontekst kodu i wzorce.

## <a name="automatic-code-generation"></a>Automatyczne generowanie kodu

### <a name="add-using"></a>Dodawanie using

**Dodaj instrukcję using** operację funkcji IntelliSense automatycznie dodaje wymagane `using` dyrektywy do pliku kodu. Ta funkcja umożliwia zachowanie zespół nad kodem, użytkownik pisanie, a nie wymaga koncentruj się do innej części kodu.

Aby zainicjować **Dodaj instrukcję using** operacji położenia kursora w danym typie się odwołać do tego nie można rozpoznać. Na przykład podczas tworzenia aplikacji konsoli i przy dodawaniu `XmlReader` do treści `Main` metody czerwona fala pojawi się w danym wierszu kodu, ponieważ nie można rozpoznać odwołania do typu. Następnie należy wywołać **Dodaj instrukcję using** za pośrednictwem **szybkie akcje**. **Szybkie akcje** są widoczne tylko wtedy, gdy kursor znajduje się w typie niepowiązanej.

![Dodawanie przy użyciu szybkich akcji rozwiniętej obrazu](../ide/media/addusing-quickaction.png)

Kliknij ikonę żarówki błąd, a następnie wybierz **przy użyciu System.Xml;** automatyczne dodawanie za pomocą dyrektywy.

### <a name="remove-and-sort-usings"></a>Usuń i Sortuj wyrażenia Using

**Usuń i Sortuj wyrażenia Using** opcji sortuje i usuwa `using` i `extern` deklaracje bez zmiany zachowania kodu źródłowego. Wraz z upływem czasu, może stać się pliki źródłowe, w przeglądarek i trudne do odczytania ze względu na i niezorganizowane i niepotrzebne `using` dyrektywy. **Usuń i Sortuj wyrażenia Using** opcji kompaktuje kodu źródłowego, usuwając nieużywane `using` dyrektyw i zwiększa czytelność obrazu za pomocą sortowania. Na **Edytuj** menu wybierz **IntelliSense**, a następnie wybierz **organizowania deklaracje Using**.

### <a name="implement-interface"></a>Implementowanie interfejsu

Technologia IntelliSense zawiera opcję, aby pomóc w zaimplementowaniu [interfejsu](/dotnet/csharp/language-reference/keywords/interface) podczas pracy w edytorze kodu. Zwykle aby prawidłowo zaimplementować interfejs, należy utworzyć deklaracji metody dla każdego członka interfejsu w klasie. Za pomocą technologii IntelliSense po wpisaniu nazwy interfejsu w deklaracji klasy **szybkie akcje** jest wyświetlana ikona żarówki. Żarówki zapewnia możliwość automatycznie, implementują interfejs za pomocą jawnego lub niejawnego nazewnictwa. W obszarze nazw jawne deklaracje metody nosić nazwę interfejsu. W obszarze nazw niejawne deklaracje metody nie wskazują interfejsu, do którego należą. Metody interfejsu jawnie nazwane zostać oceniony jedynie przez wystąpienie interfejsu, a nie przy użyciu wystąpienia klasy. Aby uzyskać więcej informacji, zobacz [jawnej implementacji interfejsu](/dotnet/csharp/programming-guide/interfaces/explicit-interface-implementation).

Implementuj interfejs generuje minimalną liczbę wycinków — metoda, które są wymagane do spełnienia interfejsu. Jeśli klasa bazowa implementuje części interfejsu, te klasy zastępcze nie są generowane.

### <a name="implement-abstract-base-class"></a>Implementowanie abstrakcyjnych klas podstawowych

Technologia IntelliSense zawiera opcję, aby pomóc w zaimplementowaniu członkowie abstrakcyjną klasę bazową automatycznie podczas pracy w edytorze kodu. Zazwyczaj do zaimplementowania elementów członkowskich abstrakcyjną klasę bazową wymaga, tworząc nową definicję metody dla każdej metody abstrakcyjnej klasy bazowej w klasie pochodnej. Przy użyciu technologii IntelliSense po wpisaniu nazwę abstrakcyjną klasę bazową w deklaracji klasy, **szybkie akcje** jest wyświetlana ikona żarówki. Żarówki zapewnia możliwość implementacji metody klasy bazowej automatycznie.

Wycinki metody, które są generowane przez **abstrakcyjna klasa bazowa implementacji** funkcji są modelowane przez fragment kodu, zdefiniowane w pliku *MethodStub.snippet*. Fragmenty kodu pochodzą można modyfikować. Aby uzyskać więcej informacji, zobacz [instruktażu: Utwórz fragment kodu](../ide/walkthrough-creating-a-code-snippet.md).

### <a name="generate-from-usage"></a>Generowanie na podstawie użycia

**Generowanie z użycia** funkcja pozwala na użycie klas i składowych, przed zdefiniowaniem je. Można wygenerować klasy zastępczej dla dowolnej klasy, Konstruktor, metoda, właściwość, pole lub typu wyliczeniowego, którą chcesz używać, ale nie został jeszcze zdefiniowany. Możesz wygenerować nowe typy i elementy członkowskie bez opuszczania Twojej bieżącej lokalizacji w kodzie. Pozwala to zmniejszyć zakłócenia działania przepływu pracy.

Czerwone faliste podkreślenie pojawia się w obszarze każdej Niezdefiniowany identyfikator. Po umieszczeniu wskaźnika myszy na identyfikatorze w etykietce narzędzia pojawi się komunikat o błędzie. Aby wyświetlić odpowiednie opcje, można użyć jednej z następujących procedur:

- Kliknij przycisk Niezdefiniowany identyfikator. A **szybkie akcje** żarówki błąd pojawia się w obszarze identyfikator. Kliknij żarówkę błędu.

- Kliknij Niezdefiniowany identyfikator, a następnie naciśnij klawisz **Ctrl**+**.** (**Ctrl** + kropka).

- Kliknij prawym przyciskiem myszy Niezdefiniowany identyfikator, a następnie kliknij przycisk **szybkie akcje i Refaktoryzacje**.

Opcje, które pojawiają się mogą być następujące:

- **Generuj właściwość**

- **Generuj pole**

- **Generowanie metody**

- **Generuj klasę**

- **Generuj nowy typ** (dla klasy, struktury, interfejs lub wyliczenie)

## <a name="generate-event-handlers"></a>Generuj procedury obsługi zdarzeń

W edytorze kodu IntelliSense może pomóc podpinanie metody (procedury obsługi zdarzeń) do pola zdarzenia.

Podczas wpisywania `+=` operator po pole zdarzenia w *.cs* pliku, funkcja IntelliSense wyświetli monit o z opcją naciśnij **kartę** klucza. Spowoduje to wstawienie nowego wystąpienia delegata, który wskazuje na metodę obsługi zdarzenia.

![Przycisk Automatyczny Hook się](../ide/media/vxautohookup.gif)

Jeśli użytkownik naciśnie klawisz **kartę**, technologia IntelliSense automatycznie zakończy się wykonywanie instrukcji dla Ciebie i wyświetla dokumentacja programu obsługi zdarzeń jako zaznaczonego tekstu w edytorze kodu. Aby ukończyć zaczep zdarzenia automatycznego, funkcja IntelliSense wyświetli monit o naciśnij **kartę** klucz ponownie, aby utworzyć pusty klasy zastępczej dla programu obsługi zdarzeń.

![Generuj procedury obsługi zdarzeń](../ide/media/vxgenerateeventhandler.gif)

> [!NOTE]
> Jeśli nowy delegat, który jest tworzony przez funkcję IntelliSense odwołuje się do istniejącego programu obsługi zdarzeń, funkcja IntelliSense komunikuje się te informacje w etykietce narzędzia. Następnie można zmodyfikować tego odwołania; tekst jest zaznaczona w edytorze kodu. W przeciwnym razie zaczep zdarzenia automatycznego zakończeniu w tym momencie.

Jeśli użytkownik naciśnie klawisz **kartę**, zastępczych metodę o prawidłowej sygnaturze funkcji IntelliSense i umieszcza kursor w ciele obsługi zdarzenia.

> [!NOTE]
> Użyj **Nawiguj wstecz** polecenie **widoku** menu (**Ctrl**+**-**) aby wrócić do zdarzenia Obsługa instrukcji.

## <a name="see-also"></a>Zobacz także

- [Korzystanie z funkcji IntelliSense](../ide/using-intellisense.md)
- [Visual Studio IDE](../get-started/visual-studio-ide.md)