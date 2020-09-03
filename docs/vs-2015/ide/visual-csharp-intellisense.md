---
title: Visual C# IntelliSense | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- IntelliSense [J#]
- Visual C#, IntelliSense
- IntelliSense [C#]
ms.assetid: 79ca304d-dc1e-4dc9-a2a6-7808df2e588e
caps.latest.revision: 26
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 36803dfbba7ea6d6d2a869fb94c05105ed4af15d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "72643333"
---
# <a name="visual-c-intellisense"></a>Visual C# IntelliSense
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Funkcja IntelliSense języka Visual C# jest dostępna podczas kodowania w edytorze oraz podczas debugowania w oknie poleceń [trybu natychmiastowego](../ide/reference/immediate-window.md) .

## <a name="completion-lists"></a>Listy uzupełniania
 Listy uzupełniania IntelliSense w Visual C# zawierają tokeny z listy członków, kompletnych wyrazów i innych. Zapewnia szybki dostęp do:

- Elementy członkowskie typu lub przestrzeni nazw,

- Zmienne, polecenia i nazwy funkcji,

- [Fragmenty kodu](#CodeSnippets),

- [Słowa kluczowe języka](#Keywords),

- [Metody rozszerzania](#ExtensionMethods)

  Lista uzupełniania w języku C# jest również odpowiednio inteligentna, aby odfiltrować nieistotne tokeny i wstępnie wybierać token oparty na kontekście. Aby uzyskać więcej informacji, zobacz [filtrowane listy uzupełniania w c#](../misc/filtered-completion-lists-in-csharp.md) i [wstępnie wybranych elementach listy uzupełniania w języku c#](../misc/pre-selected-completion-list-items-in-csharp.md).

### <a name="code-snippets-in-completion-lists"></a><a name="CodeSnippets"></a> Fragmenty kodu na listach uzupełniania
 W języku Visual C# lista uzupełniania zawiera fragmenty kodu, które ułatwiają łatwe Wstawianie wstępnie zdefiniowanych treści kodu do programu. Fragmenty kodu są wyświetlane na liście uzupełniania jako [element skrótu fragmentu (fragmenty kodu IntelliSense)](https://msdn.microsoft.com/052cc97a-5c70-42f8-b398-4c3adf670cfa).  Aby uzyskać więcej informacji na temat fragmentów kodu, które są domyślnie dostępne w Visual C#, zobacz [fragmenty kodu Visual c#](../ide/visual-csharp-code-snippets.md).

### <a name="language-keywords-in-completion-lists"></a><a name="Keywords"></a> Słowa kluczowe języka na listach uzupełniania
 W języku Visual C# lista uzupełniania zawiera również słowa kluczowe języka. Aby uzyskać więcej informacji na temat słów kluczowych języka C#, zobacz [słowa kluczowe](https://msdn.microsoft.com/library/e929b0f2-4b92-4d37-8060-23d323b098ad)w języku c#.

### <a name="extension-methods-in-completion-lists"></a><a name="ExtensionMethods"></a> Metody rozszerzające na listach uzupełniania
 W języku Visual C# lista uzupełniania zawiera metody rozszerzające, które znajdują się w zakresie.

> [!NOTE]
> Na liście uzupełniania nie są wyświetlane wszystkie metody rozszerzające dla <xref:System.String> obiektów.

 Metody rozszerzające używają innej ikony niż metody instancji. Aby zapoznać się z listą ikon list, zobacz [Widok klasy i Przeglądarka obiektów ikon](../ide/class-view-and-object-browser-icons.md). Gdy metoda wystąpienia i Metoda rozszerzająca o tej samej nazwie znajdują się zarówno w zakresie, na liście uzupełniania jest wyświetlana ikona metody rozszerzenia.

### <a name="filtered-completion-lists"></a>Filtrowane listy uzupełniania
 Technologia IntelliSense usuwa zbędnych członków z listy uzupełniania, używając filtrów.

 Visual C# filtruje listy uzupełniania, które są wyświetlane dla następujących elementów:

- **Interfejsy i klasy bazowe.** Funkcja IntelliSense automatycznie usuwa elementy z list interfejsów i uzupełniania klas bazowych, zarówno na liście podstawowej deklaracji klasy, jak i na listach ograniczeń. Na przykład wyliczenia nie są wyświetlane na liście uzupełniania dla klas bazowych, ponieważ wyliczenia nie mogą być używane dla klas bazowych. Lista uzupełniania klas bazowych zawiera tylko interfejsy i przestrzenie nazw. Jeśli wybierzesz element na liście, a następnie wpisz przecinek, IntelliSense usunie klasy bazowe z listy uzupełniania, ponieważ Visual C# nie obsługuje dziedziczenia wielokrotnego. Takie samo zachowanie występuje w przypadku klauzul ograniczenia.

- **Atrybuty**: w przypadku zastosowania atrybutu do typu Lista uzupełniania jest filtrowana, tak aby lista zawierała tylko te typy, które są podrzędne od przestrzeni nazw, które zawierają te typy, takich jak <xref:System.Attribute> .

- `as``is`Operatory i.

- **Klauzule catch.**

- **Inicjatory obiektów:** Na liście uzupełniania będą wyświetlane tylko elementy członkowskie, które mogą zostać zainicjowane.

- **New — słowo kluczowe**: po wpisaniu `new` i naciśnięciu klawisza spacji zostanie wyświetlona lista uzupełniania. Element jest automatycznie wybierany na liście na podstawie kontekstu w kodzie. Na przykład elementy są automatycznie wybierane na liście uzupełniania dla deklaracji i instrukcji return w metodach.

- **Operatory AS i is:** Filtrowana lista uzupełniania jest wyświetlana automatycznie po naciśnięciu klawisza spacji po wpisaniu `as` `is` słowa kluczowego or.

- Zdarzenia: po wpisaniu słowa kluczowego `event` Lista uzupełniania zawiera tylko typy delegatów.

- Pomoc parametru automatycznie sortuje do pierwszego przeciążenia metody, które jest zgodne z parametrami wprowadzonymi przez użytkownika. Jeśli dostępne są wiele przeciążeń metod, można użyć strzałek w górę i w dół, aby przejść do następnego możliwego przeciążenia na liście.

## <a name="most-recently-used-members"></a>Ostatnio używane elementy członkowskie
 Technologia IntelliSense zapamiętuje członków, którzy zostali ostatnio wybrani w polu [Członkowie listy](../ide/using-intellisense.md) podręcznej, aby automatycznie uzupełniać nazwy obiektów. Przy następnym użyciu listy składowych, ostatnio używane elementy członkowskie są wyświetlane u góry. Historia ostatnio używanych elementów członkowskich jest czyszczona między poszczególnymi sesjami w IDE.

## <a name="override"></a>override
 Po wpisaniu [przesłonięcia](https://msdn.microsoft.com/library/dd1907a8-acf8-46d3-80b9-c2ca4febada8) , a następnie naciśnięciu klawisza spacji, IntelliSense wyświetla wszystkie prawidłowe elementy członkowskie klasy bazowej, które można przesłonić w oknie listy rozwijanej. Wpisanie zwracanego typu metody po wyświetleniu `override` monitu IntelliSense, aby wyświetlić tylko metody, które zwracają ten sam typ. Gdy technologia IntelliSense nie może znaleźć dopasowań, będzie wyświetlała wszystkie elementy członkowskie klasy bazowej.

## <a name="automatic-code-generation"></a>Automatyczne generowanie kodu

### <a name="add-using"></a>Dodawanie using
 Operacja Dodaj przy użyciu funkcji IntelliSense umożliwia utrzymywanie fokusu w kodzie, który jest pisany, a nie wymaga przesunięcia fokusu do innej części kodu.

 Aby zainicjować operację Dodaj przy użyciu, umieść kursor w odniesieniu do typu, którego nie można rozpoznać. Na przykład po utworzeniu aplikacji konsolowej, a następnie dodaniu jej `XmlTextReader` do treści `Main` metody, tag inteligentny pojawi się poniżej znaku po prawej stronie `XmlTextReader` , ponieważ pojawia się jako odwołanie do typu, którego nie można rozpoznać.

 ![Dodaj przy użyciu obrazu taga inteligentnego](../ide/media/addusesmart.gif "AddUseSmart")

 Następnie można wywołać Dodawanie przy użyciu, wybierając je z podmenu **Rozwiązywanie** w menu **IntelliSense** lub menu kontekstowym lub wywołując polecenie Dodaj przy użyciu za pośrednictwem tagu inteligentnego. Tag inteligentny jest widoczny tylko wtedy, gdy kursor jest umieszczony na lub sąsiadujący z typem niezwiązanym.

 ![Dodaj przy użyciu, rozwinięty obraz tagów inteligentnych](../ide/media/addusesmartexp.gif "AddUseSmartExp")

### <a name="organize-usings"></a>Organizuj użycia
 Opcje **Organizuj przy użyciu** sortują i usuwają `using` `extern` deklaracje bez zmiany zachowania kodu źródłowego. W miarę upływu czasu pliki źródłowe mogą stać się bloated i trudne do odczytania ze względu na niepotrzebne i niezorganizowane `using` dyrektywy. Opcje **Organizuj przy użyciu** kompaktowego kodu źródłowego przez usunięcie nieużywanych `using` dyrektyw i zwiększa czytelności przez ich sortowanie.

 Aby wyświetlić dostępne opcje w środowisku IDE programu Visual Studio, w menu **Edycja** wskaż polecenie **IntelliSense**, a następnie wskaż polecenie **Organizuj przy użyciu**. Środowisko IDE zapewnia następujące opcje organizowania i usuwania `usings` dyrektyw:

### <a name="implement-interface"></a>Implementowanie interfejsu
 Funkcja IntelliSense udostępnia opcję ułatwiającą implementowanie [interfejsu](https://msdn.microsoft.com/library/7da38e81-4f99-4bc5-b07d-c986b687eeba) podczas pracy w edytorze kodu. Zwykle w celu prawidłowego zaimplementowania interfejsu należy utworzyć deklarację metody dla każdego elementu członkowskiego interfejsu w klasie. Przy użyciu funkcji IntelliSense po wpisaniu nazwy interfejsu w deklaracji klasy zostanie wyświetlony tag inteligentny. Tag inteligentny umożliwia automatyczne zaimplementowanie interfejsu przy użyciu jawnego lub niejawnego nazewnictwa. W przypadku jawnego nazewnictwa deklaracje metody zawierają nazwę interfejsu; w przypadku niejawnego nazewnictwa deklaracje metody nie wskazują interfejsu, do którego należą. Dostęp do metody jawnie nazwanego interfejsu można uzyskać tylko za pomocą wystąpienia interfejsu, a nie za pomocą wystąpienia klasy. Aby uzyskać więcej informacji, zobacz [jawną implementację interfejsu](https://msdn.microsoft.com/library/181c901f-0d4c-4f29-97fc-895079617bf2).

 Implementacja interfejsu spowoduje wygenerowanie minimalnej liczby elementów pośredniczących metod, które są wymagane do zaspokojenia interfejsu. Jeśli klasa bazowa implementuje części interfejsu, nie są one ponownie generowane.

### <a name="implement-abstract-base-class"></a>Zaimplementuj abstrakcyjną klasę bazową
 Funkcja IntelliSense udostępnia opcję ułatwiającą automatyczne implementowanie elementów członkowskich abstrakcyjnej klasy bazowej podczas pracy w edytorze kodu. Zwykle w celu zaimplementowania elementów członkowskich abstrakcyjnej klasy bazowej wymagane jest utworzenie nowej definicji metody dla każdej metody abstrakcyjnej klasy podstawowej w klasie pochodnej. Przy użyciu funkcji IntelliSense po wpisaniu nazwy abstrakcyjnej klasy podstawowej w deklaracji klasy zostanie wyświetlony tag inteligentny. Tag inteligentny daje możliwość automatycznego implementowania metod klasy bazowej.

 Fragmenty metod, które są generowane przez zaimplementowaną abstrakcyjną klasę bazową, są modelowane przez fragment kodu zdefiniowany w pliku MethodStub. fragment. Fragmenty kodu są modyfikowane. Aby uzyskać więcej informacji, zobacz [Przewodnik: Tworzenie fragmentu kodu](../ide/walkthrough-creating-a-code-snippet.md).

### <a name="generate-from-usage"></a>Generuj na podstawie użycia
 Funkcja **generowania z użycia** umożliwia korzystanie z klas i elementów członkowskich przed ich zdefiniowaniem. Można wygenerować element zastępczy dla dowolnej klasy, konstruktora, metody, właściwości, pola lub wyliczenia, które mają być użyte, ale nie zostały jeszcze zdefiniowane. Można generować nowe typy i składowe bez opuszczania bieżącej lokalizacji w kodzie. Pozwala to zminimalizować przerwy w przepływie pracy.

 Podkreślenie faliste pojawia się pod każdym niezdefiniowanym identyfikatorem. Po umieszczeniu wskaźnika myszy na identyfikatorze w etykietce narzędzia zostanie wyświetlony komunikat o błędzie.

 Aby wyświetlić odpowiednie opcje, można użyć jednej z następujących procedur:

- Kliknij Niezdefiniowany identyfikator. W obszarze po lewej stronie pojawia się krótkie podkreolenie. Umieść wskaźnik myszy na krótkiej podkreolenie, a zostanie wyświetlony tag inteligentny (ikona). Kliknij tag inteligentny.

- Kliknij Niezdefiniowany identyfikator, a następnie naciśnij klawisze CTRL +. (kropka).

- Kliknij prawym przyciskiem myszy Niezdefiniowany identyfikator, a następnie kliknij przycisk **Generuj**.

  Dostępne opcje mogą obejmować następujące elementy:

- **Generuj procedurę tworzenia właściwości**

- **Generuj procedurę tworzenia pola**

- **Generuj procedurę pośredniczącą metody**

- **Generuj klasę**

- **Generuj nowy typ** (dla klasy, struktury, interfejsu lub wyliczenia)

## <a name="generate-event-handlers"></a>Generuj programy obsługi zdarzeń
 W edytorze kodu technologia IntelliSense może pomóc w podłączaniu metod (obsługi zdarzeń) do pól zdarzeń.

 Po wpisaniu `+=` operatora po polu zdarzenia w pliku CS funkcja IntelliSense poprosi o wybranie klawisza Tab. Spowoduje to wstawienie nowego wystąpienia delegata wskazującego metodę obsługi zdarzenia.

 ![Autohak przycisku](../ide/media/vxautohookup.gif "vxAutoHookUp")

 Po naciśnięciu klawisza TAB funkcja IntelliSense automatycznie kończy instrukcję dla Ciebie i wyświetla odwołanie programu obsługi zdarzeń jako zaznaczony tekst w edytorze kodu. Aby ukończyć automatyczne podłączenie zdarzeń, IntelliSense poprosi o ponowne naciśnięcie klawisza TAB, aby utworzyć pustą procedurę dla programu obsługi zdarzeń.

 ![Generuj procedurę obsługi zdarzeń](../ide/media/vxgenerateeventhandler.gif "vxGenerateEventHandler")

> [!NOTE]
> Jeśli nowy delegat tworzony przez funkcję IntelliSense odwołuje się do istniejącej procedury obsługi zdarzeń, technologia IntelliSense komunikuje te informacje w etykietce narzędzia. Następnie można zmodyfikować to odwołanie; tekst jest już zaznaczony w edytorze kodu. W przeciwnym razie na tym etapie zostanie ukończone automatyczne podłączenie zdarzeń.

 Po naciśnięciu klawisza TAB funkcja IntelliSense odtworzy metodę o poprawnym podpisie i umieści kursor w treści programu obsługi zdarzeń.

> [!NOTE]
> Użyj polecenia **Nawiguj wstecz** w menu **Widok** (Ctrl +-), aby wrócić do instrukcji Event podłączenie.

 Poniższe zadanie pokazuje, jak technologia IntelliSense automatycznie łączy procedurę obsługi zdarzeń o nazwie `button1_Click` do pola zdarzenia o nazwie `button1.Click` .

## <a name="see-also"></a>Zobacz też
 [Visual Studio IDE](../ide/visual-studio-ide.md)
