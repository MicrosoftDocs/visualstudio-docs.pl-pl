---
title: C# IntelliSense
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- C#, IntelliSense
- IntelliSense [C#]
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 2ed5d86599fa99b9c1360b414b37ef95ab59082d
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "79303030"
---
# <a name="c-intellisense"></a>C# IntelliSense

C# IntelliSense jest dostępny podczas kodowania w edytorze i podczas debugowania w oknie polecenia [tryb natychmiastowy.](../ide/reference/immediate-window.md)

## <a name="completion-lists"></a>Listy uzupełnień

Listy ukończenia IntelliSense w języku C# zawierają tokeny z listy członków, kompletne słowo i inne. Zapewnia szybki dostęp do:

- Elementy członkowskie typu lub obszaru nazw

- Zmienne, polecenia i nazwy funkcji

- Fragmenty kodu

- Słowa kluczowe języka

- Metody rozszerzenia

Lista uzupełnień w języku C# jest również wystarczająco inteligentny, aby odfiltrować nietrafne tokeny i wstępnie wybrać token na podstawie kontekstu. Aby uzyskać więcej informacji, zobacz [filtrowane listy uzupełnień](#filtered-completion-lists).

### <a name="code-snippets-in-completion-lists"></a>Fragmenty kodu na listach uzupełnień

W języku C# lista uzupełnień zawiera fragmenty kodu, które ułatwiają wstawianie wstępnie zdefiniowanych treści kodu do programu. Fragmenty kodu są wyświetlane na liście uzupełnień jako [tekst skrótu](../ide/code-snippets-schema-reference.md#shortcut-element)fragmentu kodu . Aby uzyskać więcej informacji na temat fragmentów kodu, które są domyślnie dostępne w języku C#, zobacz [fragmenty kodu języka C#.](../ide/visual-csharp-code-snippets.md)

### <a name="language-keywords-in-completion-lists"></a>Słowa kluczowe języka na listach uzupełnień

W języku C# lista uzupełnień zawiera również słowa kluczowe języka. Aby uzyskać więcej informacji na temat słów kluczowych języka C#, zobacz [Słowa kluczowe języka C#](/dotnet/csharp/language-reference/keywords/index).

### <a name="extension-methods-in-completion-lists"></a>Metody rozszerzenia na listach uzupełniania

W języku C#lista uzupełniania zawiera metody rozszerzenia, które są w zakresie.

> [!NOTE]
> Na liście uzupełnień nie są <xref:System.String> wyświetlane wszystkie metody rozszerzenia dla obiektów.

Metody rozszerzenia używają innej ikony niż metody wystąpienia. Aby zapoznać się z przewodnikiem po ikonach listy, zobacz [Ikony widoku klasy i przeglądarki obiektów](../ide/class-view-and-object-browser-icons.md). Gdy metoda wystąpienia i metoda rozszerzenia o tej samej nazwie są zarówno w zakresie, lista zakończenia wyświetla ikonę metody rozszerzenia.

### <a name="filtered-completion-lists"></a>Filtrowane listy uzupełnień

IntelliSense usuwa niepotrzebnych członków z listy ukończenia przy użyciu filtrów. C# filtruje listy uzupełnień, które pojawiają się dla tych elementów:

- **Interfejsy i klasy podstawowe:** IntelliSense automatycznie usuwa elementy z listy uzupełnień interfejsu i klasy podstawowej, zarówno na listach bazowych i list interfejsów deklaracji klasy, jak i na listach ograniczeń. Na przykład wyliczenia nie są wyświetlane na liście uzupełnień dla klas podstawowych, ponieważ wyliczenia nie mogą być używane dla klas podstawowych. Lista uzupełnień klas podstawowych zawiera tylko interfejsy i przestrzenie nazw. Jeśli wybierzesz element na liście, a następnie wpisz przecinek, IntelliSense usunie klasy podstawowe z listy ukończenia, ponieważ C# nie obsługuje wielu dziedziczenia. To samo zachowanie występuje również dla klauzul ograniczeń.

- **Atrybuty:** Po zastosowaniu atrybutu do typu lista uzupełnień jest filtrowana tak, aby lista zawierała tylko te <xref:System.Attribute>typy, które schodzą z obszarów nazw zawierających te typy, takie jak .

- **Klauzule połowowe**

- **Inicjatory obiektów:** Na liście uzupełnień pojawią się tylko elementy członkowskie, które można zainicjować.

- **nowe słowo kluczowe** `new` : Po wpisaniu, a następnie naciśnięciu **spacji**zostanie wyświetlona lista uzupełnień. Element jest automatycznie wybierany na liście, na podstawie kontekstu w kodzie. Na przykład elementy są automatycznie wybierane na liście uzupełniania dla deklaracji i instrukcji zwrotu w metodach.

- **słowo kluczowe wyliczenia:** Po naciśnięciu **spacji** po znaku równości dla przypisania wyliczenia pojawi się lista uzupełnień. Element jest automatycznie wybierany na liście, na podstawie kontekstu w kodzie. Na przykład elementy są automatycznie wybierane na liście uzupełniania po wpisaniu słowa kluczowego return i podczas składania deklaracji.

- **as i jest operatorami:** Filtrowana lista uzupełnień jest wyświetlana automatycznie po `as` `is` naciśnięciu **spacji** po wpisaniu słowa kluczowego lub słowa kluczowego.

- **Zdarzenia:** Po wpisaniu `event`słowa kluczowego lista uzupełnień zawiera tylko typy pełnomocników.

- **Pomoc parametrów** automatycznie sortuje do pierwszego przeciążenia metody, które pasuje do parametrów podczas ich wprowadzania. Jeśli dostępnych jest wiele przeciążeń metod, można użyć strzałek w górę i w dół, aby przejść do następnego możliwego przeciążenia na liście.

### <a name="most-recently-used-members"></a>Ostatnio używane elementy członkowskie

Program IntelliSense zapamiętuje ostatnio wybranych członków w polu [Lista](../ide/using-intellisense.md) członków listy wyskakujących okienkach dla automatycznego uzupełniania nazwy obiektu. Przy następnym użyciu **listy członków,** ostatnio używane elementy członkowskie są wyświetlane u góry. Historia ostatnio używanych elementów członkowskich jest czyszczona między każdą sesją programu Visual Studio.

### <a name="override"></a>override

Po wpisaniu [zastąpienia,](/dotnet/csharp/language-reference/keywords/override) a następnie naciśnięciu **klawisza Space**, Program IntelliSense wyświetla wszystkie prawidłowe elementy członkowskie klasy podstawowej, które można zastąpić w polu listy podręcznej. Wpisywanie typu zwracanego `override` metody po monitowaniu intellisense, aby pokazać tylko metody, które zwracają tego samego typu. Gdy IntelliSense nie może znaleźć żadnych dopasowań, wyświetla wszystkie elementy członkowskie klasy podstawowej.

### <a name="ai-enhanced-intellisense"></a>Technologia IntelliSense z ulepszoną łatką SI

[Visual Studio IntelliCode](/visualstudio/intellicode/intellicode-visual-studio) udostępnia listy uzupełnień IntelliSense wzbogacone o sztuczną inteligencję. IntelliCode przewiduje najbardziej prawdopodobne poprawne interfejsu API do użycia, a nie tylko prezentacji alfabetycznej listy członków. Używa bieżącego kontekstu kodu i wzorców, aby zapewnić listę dynamiczną.

## <a name="automatic-code-generation"></a>Automatyczne generowanie kodu

### <a name="add-using"></a>Dodawanie using

Operacja **Dodaj za pomocą** intellisense automatycznie `using` dodaje wymaganą dyrektywę do pliku kodu. Ta funkcja umożliwia utrzymanie fokusu na kod, który piszesz, a nie wymaga, aby przenieść fokus do innej części kodu.

Aby zainicjować operację **Dodaj za pomocą,** umieść kursor na odwołaniu do typu, którego nie można rozpoznać. Na przykład podczas tworzenia aplikacji konsoli, `XmlReader` a następnie `Main` dodać do treści metody, czerwony squiggle pojawia się w tym wierszu kodu, ponieważ odwołanie do typu nie można rozpoznać. Następnie można wywołać **Dodaj za pomocą** szybkich **akcji**. **Szybkie akcje** są widoczne tylko wtedy, gdy kursor jest umieszczony na typie niezwiązanym.

![Dodawanie za pomocą, szybkie działanie rozszerzony obraz](../ide/media/addusing-quickaction.png)

Kliknij ikonę żarówki błędu, a następnie wybierz **pozycję System.Xml;** aby automatycznie dodać używaną dyrektywę.

### <a name="remove-and-sort-usings"></a>Usuwanie i sortowanie za pomocą

Opcja **Usuń i sortuj usings** sortuje `using` i usuwa i `extern` deklaracje bez zmiany zachowania kodu źródłowego. Z biegiem czasu pliki źródłowe mogą stać się nadęte i trudne do odczytania z powodu niepotrzebnych i niezorganizowanych `using` dyrektyw. Opcja **Usuń i sortuj usings** kompakuje `using` kod źródłowy, usuwając nieużywane dyrektywy i poprawia czytelność, sortując je. W menu **Edycja** wybierz polecenie **IntelliSense**, a następnie wybierz polecenie **Organizuj usings**.

### <a name="implement-interface"></a>Implementowanie interfejsu

IntelliSense udostępnia opcję ułatwiające implementowanie [interfejsu](/dotnet/csharp/language-reference/keywords/interface) podczas pracy w edytorze kodu. Zwykle, aby poprawnie zaimplementować interfejs, należy utworzyć deklarację metody dla każdego elementu członkowskiego interfejsu w klasie. Za pomocą intellisense, po wpisaniu nazwy interfejsu w deklaracji klasy, **szybkie akcje** żarówki jest wyświetlany. Żarówka daje możliwość automatycznego zaimplementowania interfejsu, przy użyciu jawnego lub niejawnego nazewnictwa. W jawnym nazewnictwie deklaracje metody zawierają nazwę interfejsu. W obszarze niejawne nazewnictwa deklaracje metody nie wskazują interfejsu, do którego należą. Jawnie nazwana metoda interfejsu jest dostępna tylko za pośrednictwem wystąpienia interfejsu, a nie za pośrednictwem wystąpienia klasy. Aby uzyskać więcej informacji, zobacz [Jawna implementacja interfejsu](/dotnet/csharp/programming-guide/interfaces/explicit-interface-implementation).

Implement Interface generuje minimalną liczbę wycinków metody, która jest wymagana do spełnienia interfejsu. Jeśli klasa podstawowa implementuje części interfejsu, a następnie te wycinki nie są generowane ponownie.

### <a name="implement-abstract-base-class"></a>Implementowanie abstrakcyjnej klasy podstawowej

IntelliSense udostępnia opcję, która ułatwia automatyczne implementowanie elementów członkowskich abstrakcyjnej klasy podstawowej podczas pracy w edytorze kodu. Zwykle do zaimplementowania elementów członkowskich klasy podstawowej abstrakcyjne wymaga utworzenia nowej definicji metody dla każdej metody abstrakcyjnej klasy podstawowej w klasie pochodnej. Za pomocą IntelliSense, po wpisaniu nazwy abstrakcyjnej klasy podstawowej w deklaracji klasy, szybkie **akcje** żarówki jest wyświetlany. Żarówka daje możliwość automatycznego wdrożenia metod klasy podstawowej.

Wycinki metody, które są generowane przez **implementuj abstrakcyjną klasę podstawową,** są modelowane przez fragment kodu zdefiniowany w pliku *MethodStub.snippet*. Fragmenty kodu można modyfikować. Aby uzyskać więcej informacji, zobacz [Instruktaż: Tworzenie fragmentu kodu](../ide/walkthrough-creating-a-code-snippet.md).

### <a name="generate-from-usage"></a>Generowanie z użycia

Funkcja **Generuj z użycia** umożliwia używanie klas i elementów członkowskich przed ich zdefiniowaniem. Można wygenerować skrót dla dowolnej klasy, konstruktora, metody, właściwości, pola lub wyliczenia, które mają być używane, ale jeszcze nie zostały zdefiniowane. Można wygenerować nowe typy i elementy członkowskie bez opuszczania bieżącej lokalizacji w kodzie. Minimalizuje to przerwy w przepływie pracy.

Pod każdym niezdefiniowanym identyfikatorem pojawia się czerwone faliste podkreślenie. Po umieszczeniu wskaźnika myszy na identyfikatorze w etykietce narzędzia pojawi się komunikat o błędzie. Aby wyświetlić odpowiednie opcje, można użyć jednej z następujących procedur:

- Kliknij niezdefiniowany identyfikator. Pod identyfikatorem pojawi się żarówka błędu **Szybkie akcje.** Kliknij żarówkę błędu.

- Kliknij niezdefiniowany identyfikator, a następnie naciśnij klawisz **Ctrl**+**.** **(Ctrl** + okres).

- Kliknij prawym przyciskiem myszy niezdefiniowany identyfikator, a następnie kliknij polecenie **Szybkie akcje i Refaktoryzowania**.

Wyświetlane opcje mogą być następujące:

- **Generowanie właściwości**

- **Generowanie pola**

- **Generowanie metody**

- **Generowanie klasy**

- **Generowanie nowego typu** (dla klasy, struktury, interfejsu lub wyliczenia)

## <a name="generate-event-handlers"></a>Generowanie programów obsługi zdarzeń

W edytorze kodu IntelliSense może pomóc w podłączeniu metod (programy obsługi zdarzeń) do pól zdarzeń.

Po wpisaniu `+=` operatora po polu zdarzenia w pliku *cs,* intelliSense monituje o naciśnięcie **klawisza Tab.** Spowoduje to wstawienie nowego wystąpienia delegata, który wskazuje na metodę obsługi zdarzenia.

![Przycisk Auto Podłączyć](../ide/media/vxautohookup.gif)

Jeśli naciśniesz **klawisz Tab,** program IntelliSense automatycznie zakończy instrukcję i wyświetli odwołanie do programu obsługi zdarzeń jako zaznaczony tekst w edytorze kodu. Aby zakończyć automatyczne podłączanie zdarzeń, IntelliSense monituje o ponowne **naciśnięcie klawisza Tab,** aby utworzyć pusty skrót dla programu obsługi zdarzeń.

![Generowanie obsługi zdarzeń](../ide/media/vxgenerateeventhandler.gif)

> [!NOTE]
> Jeśli nowy pełnomocnik, który jest tworzony przez IntelliSense odwołuje się do istniejącego programu obsługi zdarzeń, IntelliSense przekazuje te informacje w etykietce narzędzia. Następnie można zmodyfikować to odwołanie; tekst jest już zaznaczony w edytorze kodu. W przeciwnym razie automatyczne podłączanie zdarzeń zostanie zakończone w tym momencie.

Jeśli naciśniesz **tab**, IntelliSense wycinki obecnie metodę z poprawnym podpisem i umieszcza kursor w treści programu obsługi zdarzeń.

> [!NOTE]
> Użyj polecenia **Nawiguj wstecz** w menu **Widok** **(Ctrl),**+**-** aby powrócić do instrukcji podłączania zdarzeń.

## <a name="see-also"></a>Zobacz też

- [Korzystanie z funkcji IntelliSense](../ide/using-intellisense.md)
- [Visual Studio IDE](../get-started/visual-studio-ide.md)
