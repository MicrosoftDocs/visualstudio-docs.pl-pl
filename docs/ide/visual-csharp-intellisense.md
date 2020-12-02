---
title: C# IntelliSense
description: Dowiedz się więcej na temat funkcji IntelliSense, których można użyć podczas kodowania projektu C#.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: e725a06a2bc90c91cff11b05ad32b20a0db8e4fc
ms.sourcegitcommit: df6ba39a62eae387e29f89388be9e3ee5ceff69c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2020
ms.locfileid: "96479787"
---
# <a name="c-intellisense"></a>C# IntelliSense

Funkcja IntelliSense języka C# jest dostępna podczas kodowania w edytorze oraz podczas debugowania w oknie poleceń [trybu natychmiastowego](../ide/reference/immediate-window.md) .

## <a name="completion-lists"></a>Listy uzupełniania

Listy uzupełniania IntelliSense w języku C# zawierają tokeny z listy członków, kompletnych wyrazów i innych. Zapewnia szybki dostęp do:

- Elementy członkowskie typu lub przestrzeni nazw

- Zmienne, polecenia i nazwy funkcji

- Fragmenty kodu

- Słowa kluczowe języka

- Metody rozszerzeń

Lista uzupełniania w języku C# jest również odpowiednio inteligentna, aby odfiltrować nieistotne tokeny i wstępnie wybierać token oparty na kontekście. Aby uzyskać więcej informacji, zobacz [filtrowane listy uzupełniania](#filtered-completion-lists).

### <a name="code-snippets-in-completion-lists"></a>Fragmenty kodu na listach uzupełniania

W języku C# lista uzupełniania zawiera fragmenty kodu, które ułatwiają łatwe Wstawianie wstępnie zdefiniowanych treści kodu do programu. Fragmenty kodu są wyświetlane na liście uzupełniania jako [tekst skrótu](../ide/code-snippets-schema-reference.md#shortcut-element)wstawki. Aby uzyskać więcej informacji na temat fragmentów kodu, które są domyślnie dostępne w języku C#, zobacz [fragmenty kodu w języku c#](../ide/visual-csharp-code-snippets.md).

### <a name="language-keywords-in-completion-lists"></a>Słowa kluczowe języka na listach uzupełniania

W języku C# lista uzupełniania zawiera również słowa kluczowe języka. Aby uzyskać więcej informacji na temat słów kluczowych języka C#, zobacz [słowa kluczowe](/dotnet/csharp/language-reference/keywords/index)w języku c#.

### <a name="extension-methods-in-completion-lists"></a>Metody rozszerzające na listach uzupełniania

W języku C# lista uzupełniania zawiera metody rozszerzające, które znajdują się w zakresie.

> [!NOTE]
> Na liście uzupełniania nie są wyświetlane wszystkie metody rozszerzające dla <xref:System.String> obiektów.

Metody rozszerzające używają innej ikony niż metody instancji. Aby uzyskać informacje na temat ikony listy, zobacz [Widok klasy i Przeglądarka obiektów ikon](../ide/class-view-and-object-browser-icons.md). Gdy metoda wystąpienia i Metoda rozszerzająca o tej samej nazwie znajdują się zarówno w zakresie, na liście uzupełniania jest wyświetlana ikona metody rozszerzenia.

### <a name="filtered-completion-lists"></a>Filtrowane listy uzupełniania

Technologia IntelliSense usuwa zbędnych członków z listy uzupełniania, używając filtrów. Język C# filtruje listy uzupełniania, które są wyświetlane dla następujących elementów:

- **Interfejsy i klasy bazowe**: Funkcja IntelliSense automatycznie usuwa elementy z list interfejsów i uzupełniania klas bazowych, zarówno na liście podstawowej deklaracji klasy, jak i na listach ograniczeń. Na przykład wyliczenia nie są wyświetlane na liście uzupełniania dla klas bazowych, ponieważ wyliczenia nie mogą być używane dla klas bazowych. Lista uzupełniania klas bazowych zawiera tylko interfejsy i przestrzenie nazw. Jeśli wybierzesz element na liście, a następnie wpisz przecinek, IntelliSense usunie klasy bazowe z listy uzupełniania, ponieważ język C# nie obsługuje wielokrotnego dziedziczenia. Takie samo zachowanie występuje w przypadku klauzul ograniczenia.

- **Atrybuty**: w przypadku zastosowania atrybutu do typu Lista uzupełniania jest filtrowana, tak aby lista zawierała tylko te typy, które są podrzędne od przestrzeni nazw, które zawierają te typy, takich jak <xref:System.Attribute> .

- **Klauzule catch**

- **Inicjatory obiektów**: na liście uzupełniania będą wyświetlane tylko elementy członkowskie, które mogą zostać zainicjowane.

- **New — słowo kluczowe**: gdy wpiszesz, `new` a następnie naciśniesz **spację**, zostanie wyświetlona lista uzupełniania. Element jest automatycznie wybierany na liście na podstawie kontekstu w kodzie. Na przykład elementy są automatycznie wybierane na liście uzupełniania dla deklaracji i instrukcji return w metodach.

- **enum — słowo kluczowe**: po naciśnięciu **miejsca** po znaku równości dla przypisania wyliczenia zostanie wyświetlona lista uzupełniania. Element jest automatycznie wybierany na liście na podstawie kontekstu w kodzie. Na przykład elementy są automatycznie wybierane na liście uzupełniania po wpisaniu słowa kluczowego Return i po wprowadzeniu deklaracji.

- **Operatory AS i is**: filtrowana lista uzupełniania jest wyświetlana automatycznie po naciśnięciu **miejsca** po wpisaniu `as` `is` słowa kluczowego or.

- **Zdarzenia**: po wpisaniu słowa kluczowego `event` Lista uzupełniania zawiera tylko typy delegatów.

- **Pomoc parametru** automatycznie sortuje do pierwszego przeciążenia metody, które jest zgodne z parametrami wprowadzonymi przez użytkownika. Jeśli dostępne są wiele przeciążeń metod, można użyć strzałek w górę i w dół, aby przejść do następnego możliwego przeciążenia na liście.

### <a name="most-recently-used-members"></a>Ostatnio używane elementy członkowskie

Technologia IntelliSense zapamiętuje członków, którzy zostali ostatnio wybrani w polu [Członkowie listy](../ide/using-intellisense.md) podręcznej, aby automatycznie uzupełniać nazwy obiektów. Przy następnym użyciu **listy składowych**, ostatnio używane elementy członkowskie są wyświetlane u góry. Historia ostatnio używanych elementów członkowskich jest czyszczona między poszczególnymi sesjami programu Visual Studio.

### <a name="override"></a>override

Po wpisaniu [przesłonięcia](/dotnet/csharp/language-reference/keywords/override) , a **następnie naciśnięciu** klawisza, IntelliSense wyświetla wszystkie prawidłowe elementy członkowskie klasy bazowej, które można przesłonić w oknie listy rozwijanej. Wpisanie zwracanego typu metody po `override` wyświetleniu przez funkcję IntelliSense tylko metod, które zwracają ten sam typ. Gdy technologia IntelliSense nie może znaleźć dopasowań, wyświetla wszystkie elementy członkowskie klasy bazowej.

### <a name="ai-enhanced-intellisense"></a>Ulepszona funkcja IntelliSense

[Program Visual Studio rozszerzenia intellicode](/visualstudio/intellicode/intellicode-visual-studio) zapewnia sztuczne, ulepszone listy uzupełniania technologii IntelliSense. Rozszerzenia intellicode przewiduje najbardziej właściwy interfejs API do użycia, a nie tylko prezentowanie alfabetycznej listy członków. Używa bieżącego kontekstu kodu i wzorców w celu udostępnienia listy dynamicznej.

## <a name="automatic-code-generation"></a>Automatyczne generowanie kodu

### <a name="add-using"></a>Dodawanie using

Operacja **Dodaj przy użyciu funkcji** IntelliSense automatycznie dodaje dyrektywę wymaganą `using` do pliku kodu. Ta funkcja umożliwia utrzymywanie fokusu w kodzie, który jest pisany, a nie wymaga przesunięcia fokusu do innej części kodu.

Aby zainicjować operację **Dodaj przy użyciu** , umieść kursor w odniesieniu do typu, którego nie można rozpoznać. Na przykład podczas tworzenia aplikacji konsolowej, a następnie dodawania `XmlReader` do treści `Main` metody, w tym wierszu kodu pojawia się czerwona zygzakowata, ponieważ nie można rozpoznać odwołania do typu. Następnie można wywołać **Dodawanie przy użyciu** przez **szybkie akcje**. **Szybkie akcje** są widoczne tylko wtedy, gdy kursor jest ustawiony na niezwiązanym typie.

![Dodawanie przy użyciu, szybka akcja rozwinięta obraz](../ide/media/addusing-quickaction.png)

Kliknij ikonę żarówki błędów, a następnie wybierz pozycję **użyj System.Xml;** , aby automatycznie dodać dyrektywę using.

### <a name="remove-and-sort-usings"></a>Usuń i Sortuj użycia

Opcja **Usuń i Sortuj używa** sortuje i usuwa `using` `extern` deklaracje bez zmiany zachowania kodu źródłowego. W miarę upływu czasu pliki źródłowe mogą stać się bloated i trudne do odczytania ze względu na niepotrzebne i niezorganizowane `using` dyrektywy. Opcja **Usuń i Sortuj używa** kompaktuje kod źródłowy przez usunięcie nieużywanych `using` dyrektyw i zwiększa czytelność poprzez ich sortowanie. W menu **Edycja** wybierz pozycję **IntelliSense**, a następnie wybierz pozycję **Organizuj przy użyciu**.

### <a name="implement-interface"></a>Implementowanie interfejsu

Funkcja IntelliSense udostępnia opcję ułatwiającą implementowanie [interfejsu](/dotnet/csharp/language-reference/keywords/interface) podczas pracy w edytorze kodu. Zwykle aby poprawnie zaimplementować interfejs, należy utworzyć deklarację metody dla każdego elementu członkowskiego interfejsu w klasie. Przy użyciu funkcji IntelliSense po wpisaniu nazwy interfejsu w deklaracji klasy zostanie wyświetlona żarówka **Quick Actions** . Żarówka daje możliwość automatycznego zaimplementowania interfejsu przy użyciu jawnego lub niejawnego nazewnictwa. W przypadku jawnego nazewnictwa deklaracje metody zawierają nazwę interfejsu. W przypadku niejawnego nazewnictwa deklaracje metody nie wskazują interfejsu, do którego należą. Dostęp do metody jawnie nazwanego interfejsu można uzyskać tylko za pomocą wystąpienia interfejsu, a nie za pomocą wystąpienia klasy. Aby uzyskać więcej informacji, zobacz [jawną implementację interfejsu](/dotnet/csharp/programming-guide/interfaces/explicit-interface-implementation).

Implementacja interfejsu generuje minimalną liczbę elementów zastępczych metod, które są wymagane do zaspokojenia interfejsu. Jeśli klasa bazowa implementuje części interfejsu, nie są one ponownie generowane.

### <a name="implement-abstract-base-class"></a>Zaimplementuj abstrakcyjną klasę bazową

Funkcja IntelliSense udostępnia opcję ułatwiającą automatyczne implementowanie elementów członkowskich abstrakcyjnej klasy bazowej podczas pracy w edytorze kodu. Zwykle w celu zaimplementowania elementów członkowskich abstrakcyjnej klasy bazowej wymagane jest utworzenie nowej definicji metody dla każdej metody abstrakcyjnej klasy podstawowej w klasie pochodnej. Przy użyciu funkcji IntelliSense po wpisaniu nazwy abstrakcyjnej klasy podstawowej w deklaracji klasy zostanie wyświetlona żarówka **Quick Actions** . Żarówka daje możliwość automatycznego implementowania metod klasy bazowej.

Fragmenty metod, które są generowane przez **zaimplementowaną abstrakcyjną klasę bazową** , są modelowane przez fragment kodu zdefiniowany w pliku *MethodStub. fragment*. Fragmenty kodu są modyfikowane. Aby uzyskać więcej informacji, zobacz [Przewodnik: Tworzenie fragmentu kodu](../ide/walkthrough-creating-a-code-snippet.md).

### <a name="generate-from-usage"></a>Generuj na podstawie użycia

Funkcja **generowania z użycia** umożliwia korzystanie z klas i elementów członkowskich przed ich zdefiniowaniem. Można wygenerować element zastępczy dla dowolnej klasy, konstruktora, metody, właściwości, pola lub wyliczenia, które mają być użyte, ale nie zostały jeszcze zdefiniowane. Można generować nowe typy i składowe bez opuszczania bieżącej lokalizacji w kodzie. Pozwala to zminimalizować przerwy w przepływie pracy.

Czerwone faliste podkreślenie pojawia się pod każdym niezdefiniowanym identyfikatorem. Po umieszczeniu wskaźnika myszy na identyfikatorze w etykietce narzędzia zostanie wyświetlony komunikat o błędzie. Aby wyświetlić odpowiednie opcje, można użyć jednej z następujących procedur:

- Kliknij Niezdefiniowany identyfikator. W obszarze identyfikatora zostanie wyświetlona żarówka o błędzie **Quick Actions** . Kliknij żarówkę błędów.

- Kliknij Niezdefiniowany identyfikator, a następnie naciśnij klawisz **Ctrl** + **.** (**Ctrl** + kropka).

- Kliknij prawym przyciskiem myszy Niezdefiniowany identyfikator, a następnie kliknij pozycję **szybkie akcje i refaktoryzacje**.

Dostępne opcje mogą obejmować następujące elementy:

- **Generuj Właściwość**

- **Generuj pole**

- **Generowanie metody**

- **Generuj klasę**

- **Generuj nowy typ** (dla klasy, struktury, interfejsu lub wyliczenia)

## <a name="generate-event-handlers"></a>Generuj programy obsługi zdarzeń

W edytorze kodu technologia IntelliSense może pomóc w podłączaniu metod (obsługi zdarzeń) do pól zdarzeń.

Po wpisaniu `+=` operatora po polu zdarzenia w pliku *CS* funkcja IntelliSense poprosi o wybranie klawisza **Tab** . Spowoduje to wstawienie nowego wystąpienia delegata wskazującego metodę obsługi zdarzenia.

![Autohak przycisku](../ide/media/vxautohookup.gif)

Po naciśnięciu klawisza **Tab** funkcja IntelliSense automatycznie kończy instrukcję dla Ciebie i wyświetla odwołanie programu obsługi zdarzeń jako zaznaczony tekst w edytorze kodu. Aby ukończyć automatyczne podłączenie zdarzeń, IntelliSense poprosi o ponowne naciśnięcie klawisza **Tab** , aby utworzyć pustą procedurę dla programu obsługi zdarzeń.

![Generuj procedurę obsługi zdarzeń](../ide/media/vxgenerateeventhandler.gif)

> [!NOTE]
> Jeśli nowy delegat tworzony przez funkcję IntelliSense odwołuje się do istniejącej procedury obsługi zdarzeń, technologia IntelliSense komunikuje te informacje w etykietce narzędzia. Następnie można zmodyfikować to odwołanie; tekst jest już zaznaczony w edytorze kodu. W przeciwnym razie na tym etapie zostanie ukończone automatyczne podłączenie zdarzeń.

Po naciśnięciu klawisza **Tab** funkcja IntelliSense odtworzy metodę o poprawnym podpisie i umieści kursor w treści programu obsługi zdarzeń.

> [!NOTE]
> Użyj polecenia **Nawiguj wstecz** w menu **Widok** (**Ctrl** + **-** ), aby wrócić do instrukcji Event podłączenie.

## <a name="see-also"></a>Zobacz też

- [Korzystanie z funkcji IntelliSense](../ide/using-intellisense.md)
- [Visual Studio IDE](../get-started/visual-studio-ide.md)
