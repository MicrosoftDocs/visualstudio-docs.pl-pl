---
title: Funkcja IntelliSense programu Visual C# | Dokumentacja firmy Microsoft
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
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 8de573e8d5f46988868f18114fdabb07f62690e0
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "63443167"
---
# <a name="visual-c-intellisense"></a>Visual C# IntelliSense
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual C# IntelliSense jest dostępna podczas kodowania w edytorze i podczas debugowania w [tryb natychmiastowy](../ide/reference/immediate-window.md) okna poleceń.  
  
## <a name="completion-lists"></a>Listy uzupełniania  
 Listy uzupełniania IntelliSense w języku Visual C# zawiera tokenów z listy elementów członkowskich, Dokończ wyraz i innych. Zapewnia ona szybki dostęp do:  
  
- Elementy członkowskie tego typu lub przestrzeni nazw  
  
- Nazwy funkcji, zmiennych i polecenia  
  
- [Fragmenty kodu](#CodeSnippets),  
  
- [Słowa kluczowe języka](#Keywords),  
  
- [Metody rozszerzeń](#ExtensionMethods)  
  
  Na liście uzupełniania w języku C# jest również inteligentnego odfiltrować tokenów nie ma znaczenia i wstępnie wybierz token na podstawie kontekstu. Aby uzyskać więcej informacji, zobacz [filtrowane listy uzupełniania w języku C#](../misc/filtered-completion-lists-in-csharp.md) i [Pre-selected listy uzupełniania w C#](../misc/pre-selected-completion-list-items-in-csharp.md).  
  
### <a name="CodeSnippets"></a> Fragmenty kodu w listach uzupełniania  
 W języku Visual C# na liście uzupełniania zawiera fragmenty kodu, aby pomóc łatwo Wstawianie wstępnie zdefiniowanych jednostek kodu programu. Fragmenty kodu są wyświetlane na liście uzupełniania jako ten fragment kodu [Shortcut — Element (fragmenty kodu Intellisense)](http://msdn.microsoft.com/052cc97a-5c70-42f8-b398-4c3adf670cfa).  Aby uzyskać więcej informacji na temat fragmentów kodu, które domyślnie są dostępne w Visual C#, zobacz [Visual C# — wstawki](../ide/visual-csharp-code-snippets.md).  
  
### <a name="Keywords"></a> Słowa kluczowe języka w listach uzupełniania  
 W języku Visual C# na liście uzupełniania także słowa kluczowe języka. Aby uzyskać więcej informacji na temat słowa kluczowe języka C#, zobacz [słowa kluczowe języka C#](http://msdn.microsoft.com/library/e929b0f2-4b92-4d37-8060-23d323b098ad).  
  
### <a name="ExtensionMethods"></a> Metody rozszerzające w listach uzupełniania  
 W języku Visual C# na liście uzupełniania zawiera metody rozszerzenia, które znajdują się w zakresie.  
  
> [!NOTE]
> Na liście uzupełniania nie są wyświetlane wszystkie metody rozszerzenia dla <xref:System.String> obiektów.  
  
 Metody rozszerzające użyj ikony innego niż metody wystąpienia. Aby uzyskać listę ikon na liście, zobacz [widoku klas i przeglądarka obiektów ― ikony](../ide/class-view-and-object-browser-icons.md). Gdy metoda wystąpienia i metodę rozszerzenia o tej samej nazwie znajdują się zarówno w zakresie, na liście uzupełniania Wyświetla ikonę metody rozszerzenia.  
  
### <a name="filtered-completion-lists"></a>Filtrowane listy uzupełniania  
 Funkcja IntelliSense usuwa zbędnych członków z listy uzupełniania przy użyciu filtrów.  
  
 Visual C# filtry listy uzupełniania, które są wyświetlane dla tych elementów:  
  
- **Interfejsy i klas bazowych.** Funkcja IntelliSense automatycznie usuwa elementy z interfejsu i podstawowej klasy listy uzupełniania, w deklaracji klasy podstawowe i interfejs listy i listy ograniczeń. Na przykład wyliczenia nie są wyświetlane na liście uzupełniania dla klas bazowych, ponieważ nie można używać wyliczenia dla klas podstawowych. Na liście uzupełniania klas bazowych zawiera tylko interfejsów i przestrzeni nazw. Jeśli wybierz element na liście, a następnie wpisz przecinek, IntelliSense usuwa klas bazowych z listy uzupełniania, ponieważ Visual C# nie obsługuje wielokrotne dziedziczenie. Takie samo zachowanie występuje także klauzule ograniczenia.  
  
- **Atrybuty**: Po zastosowaniu atrybutu do typu, na liście uzupełniania jest filtrowana, tak aby lista zawiera tylko tych typów, które jest elementem podrzędnym elementu przestrzeni nazw, które zawierają te typy, takie jak <xref:System.Attribute>.  
  
- `as` i `is` operatorów.  
  
- **CATCH klauzul.**  
  
- **Inicjatory obiektów:** Tylko elementy członkowskie, które mogą być inicjowane pojawi się na liście uzupełniania.  
  
- **New — słowo kluczowe**: Podczas wpisywania `new` i naciśnij klawisz spacji, zostanie wyświetlona lista uzupełniania. Automatycznie wybrano element na liście na podstawie kontekstu w kodzie. Na przykład automatycznie zaznaczono elementów na liście uzupełniania dla deklaracji i instrukcjach return w metodzie.  
  
- **jako operatorów i is:** Listy uzupełniania filtrowane jest wyświetlany automatycznie po naciśnięciu klawisza klawisz spacji po wpisaniu `as` lub `is` — słowo kluczowe.  
  
- Zdarzenia: Podczas wpisywania słowa kluczowego `event`, na liście uzupełniania zawiera tylko typy delegatów.  
  
- Parametr pomocy automatycznie sortuje do pierwsze przeciążenie metody, zgodny z parametrami, podczas ich wprowadzania. Jeśli wiele przeciążeń metody są dostępne, możesz użyć pracy i naciśnij strzałkę, aby przejść do następnego przeciążenia możliwe na liście.  
  
## <a name="most-recently-used-members"></a>Ostatnio używanych elementów członkowskich  
 Funkcja IntelliSense pamięta elementy członkowskie zaznaczone niedawno w oknie podręcznym [List Members](../ide/using-intellisense.md) pola obiektu automatyczne uzupełnianie nazw. Następnym razem, użyj listy członków ostatnio używanych elementów członkowskich są wyświetlane u góry. Historia ostatnio używanych elementów członkowskich jest czyszczona między każdej sesji w środowisku IDE.  
  
## <a name="override"></a>override  
 Podczas wpisywania [zastąpienia](http://msdn.microsoft.com/library/dd1907a8-acf8-46d3-80b9-c2ca4febada8) i następnie naciśnij klawisz spacji, IntelliSense wyświetla wszystkie elementy członkowskie prawidłową klasę podstawową, które można zastąpić w oknie podręcznym listy. Wpisywanie zwracany typ metody po `override` wyświetli monit o technologię IntelliSense, aby wyświetlić tylko metody, które zwracają tego samego typu. Gdy IntelliSense nie może znaleźć dopasowań, wyświetli wszystkie elementy członkowskie klasy bazowej.  
  
## <a name="automatic-code-generation"></a>Automatyczne generowanie kodu  
  
### <a name="add-using"></a>Dodawanie using  
 Dodaj przy użyciu operacji IntelliSense pozwala zachować zespół nad kodem, użytkownik pisanie, a nie wymaga koncentruj się do innej części kodu.  
  
 Aby zainicjować Dodaj przy użyciu operacji, umieść kursor na odwołanie do typu, którego nie można rozpoznać. Na przykład podczas tworzenia aplikacji konsoli i przy dodawaniu `XmlTextReader` do treści `Main` tagu inteligentnego metody będą wyświetlane po prawej stronie znaku `XmlTextReader`, ponieważ jest on wyświetlany jako odwołanie do typu, którego nie można rozpoznać.  
  
 ![Dodawanie przy użyciu obrazu tagu inteligentnego](../ide/media/addusesmart.gif "AddUseSmart")  
  
 Można następnie wywołać, Dodaj za pomocą, wybierając je z **rozwiązać** podmenu **IntelliSense** menu lub menu kontekstowego lub za pomocą wywołania Dodaj przy użyciu za pomocą tagu inteligentnego. Tag inteligentny jest widoczna tylko w przypadku, gdy kursor znajduje się rozmieszczanych na lub przylegające do typu niepowiązanego.  
  
 ![Dodaj instrukcję using, inteligentne tag obrazu rozwiniętej](../ide/media/addusesmartexp.gif "AddUseSmartExp")  
  
### <a name="organize-usings"></a>Organizuj użycia  
 **Organizowania deklaracje Using** opcje sortowania i Usuń `using` i `extern` deklaracje bez zmiany zachowania kodu źródłowego. Wraz z upływem czasu, może stać się pliki źródłowe, w przeglądarek i trudne do odczytania ze względu na i niezorganizowane i niepotrzebne `using` dyrektywy. **Organizowania deklaracje Using** opcje compact kodu źródłowego, usuwając nieużywane `using` dyrektyw i zwiększa czytelność obrazu za pomocą sortowania.  
  
 Aby wyświetlić opcje dostępne w programie Visual Studio IDE na **Edytuj** menu, wskaż **IntelliSense**, a następnie wskaż **organizowania deklaracje Using**. IDE udostępnia następujące opcje do organizowania i Usuń `usings` dyrektywy:  
  
### <a name="implement-interface"></a>Implementowanie interfejsu  
 Technologia IntelliSense zawiera opcję, aby pomóc w zaimplementowaniu [interfejsu](http://msdn.microsoft.com/library/7da38e81-4f99-4bc5-b07d-c986b687eeba) podczas pracy w edytorze kodu. Zwykle aby prawidłowo zaimplementować interfejs należy utworzyć deklaracji metody dla każdego członka interfejsu w klasie. Za pomocą technologii IntelliSense po wpisaniu nazwy interfejsu w deklaracji klasy, jest wyświetlany tagu inteligentnego. Tag inteligentny zapewnia możliwość automatycznie, implementować interfejs za pomocą jawnego lub niejawnego nazewnictwa. W obszarze nazw jawne deklaracje metody przenoszenia nazwę interfejsu; w obszarze nazw niejawne deklaracje metody nie wskazują interfejsu, do którego należą. Metody interfejsu jawnie nazwane zostać oceniony jedynie przez wystąpienie interfejsu, a nie przy użyciu wystąpienia klasy. Aby uzyskać więcej informacji, zobacz [jawnej implementacji interfejsu](http://msdn.microsoft.com/library/181c901f-0d4c-4f29-97fc-895079617bf2).  
  
 Implementuj interfejs wygeneruje minimalną liczbę wycinków — metoda, który jest wymagany do spełnienia interfejsu. Jeśli klasa bazowa implementuje części interfejsu, te klasy zastępcze nie są generowane.  
  
### <a name="implement-abstract-base-class"></a>Implementowanie abstrakcyjnych klas podstawowych  
 Technologia IntelliSense zawiera opcję, aby pomóc w zaimplementowaniu członkowie abstrakcyjną klasę bazową automatycznie podczas pracy w edytorze kodu. Zazwyczaj do zaimplementowania elementów członkowskich abstrakcyjną klasę bazową wymaga, tworząc nową definicję metody dla każdej metody abstrakcyjnej klasy bazowej w klasie pochodnej. Za pomocą technologii IntelliSense po wpisaniu nazwę abstrakcyjną klasę bazową w deklaracji klasy, jest wyświetlany tagu inteligentnego. Tag inteligentny zapewnia możliwość implementacji metody klasy bazowej automatycznie.  
  
 Wycinków metody, które są generowane przez funkcję implementacji klasy abstrakcyjnej bazy są modelowane przy zdefiniowane w pliku MethodStub.snippet fragmentu kodu. Fragmenty kodu pochodzą można modyfikować. Aby uzyskać więcej informacji, zobacz [instruktażu: Creating a Code Snippet](../ide/walkthrough-creating-a-code-snippet.md).  
  
### <a name="generate-from-usage"></a>Generowanie na podstawie użycia  
 **Generowanie z użycia** funkcja pozwala na użycie klas i składowych, przed zdefiniowaniem je. Można wygenerować klasy zastępczej dla dowolnej klasy, Konstruktor, metoda, właściwość, pole lub typu wyliczeniowego, którą chcesz używać, ale nie został jeszcze zdefiniowany. Możesz wygenerować nowe typy i elementy członkowskie bez opuszczania Twojej bieżącej lokalizacji w kodzie. Pozwala to zmniejszyć zakłócenia działania przepływu pracy.  
  
 Faliste podkreślenie pojawia się pod każdym Niezdefiniowany identyfikator. Po umieszczeniu wskaźnika myszy na identyfikatorze w etykietce narzędzia pojawi się komunikat o błędzie.  
  
 Aby wyświetlić odpowiednie opcje, można użyć jednej z następujących procedur:  
  
- Kliknij przycisk Niezdefiniowany identyfikator. Krótkie podkreślenie pojawia się w obszarze skrajnie po lewej stronie znaku. Umieść wskaźnik myszy na krótki podkreślenia i tagu inteligentnego (ikonę). Kliknij tag inteligentny.  
  
- Kliknij Niezdefiniowany identyfikator, a następnie naciśnij klawisze CTRL +. (okres).  
  
- Kliknij prawym przyciskiem myszy Niezdefiniowany identyfikator, a następnie kliknij przycisk **Generuj**.  
  
  Opcje, które pojawiają się mogą być następujące:  
  
- **Generowania szkieletu właściwości**  
  
- **Wygenerować klasy zastępczej pola**  
  
- **Generuj szkielet metody**  
  
- **Generuj klasę**  
  
- **Generuj nowy typ** (dla klasy, struktury, interfejs lub wyliczenie)  
  
## <a name="generate-event-handlers"></a>Generuj procedury obsługi zdarzeń  
 W edytorze kodu IntelliSense może pomóc podpinanie metody (procedury obsługi zdarzeń) do pola zdarzenia.  
  
 Podczas wpisywania `+=` operator po pole zdarzenia w pliku .cs, funkcja IntelliSense wyświetli monit z opcją naciskaj klawisz TAB. Spowoduje to wstawienie nowego wystąpienia delegata, który wskazuje na metodę obsługi zdarzenia.  
  
 ![Przycisk Automatyczny punktu zaczepienia się](../ide/media/vxautohookup.gif "vxAutoHookUp")  
  
 Jeśli użytkownik naciśnie klawisz TAB, IntelliSense zakończy się wykonywanie instrukcji dla Ciebie i automatycznie wyświetla dokumentacja programu obsługi zdarzeń jako zaznaczonego tekstu w edytorze kodu. Aby ukończyć zaczep zdarzenia automatycznego, funkcja IntelliSense wyświetli monit o naciskaj klawisz TAB, ponownie, aby utworzyć pusty klasy zastępczej dla programu obsługi zdarzeń.  
  
 ![Generuj procedury obsługi zdarzeń](../ide/media/vxgenerateeventhandler.gif "vxGenerateEventHandler")  
  
> [!NOTE]
> Jeśli nowy delegat, który jest tworzony przez funkcję IntelliSense odwołuje się do istniejącego programu obsługi zdarzeń, funkcja IntelliSense komunikuje się te informacje w etykietce narzędzia. Następnie można zmodyfikować tego odwołania; tekst jest zaznaczony w edytorze kodu. W przeciwnym razie zaczep zdarzenia automatycznego zakończeniu w tym momencie.  
  
 Jeśli użytkownik naciśnie klawisz TAB, IntelliSense zastępczych metodę o prawidłowej sygnaturze i umieszcza kursor w ciele obsługi zdarzenia.  
  
> [!NOTE]
> Użyj **Nawiguj wstecz** polecenie **widoku** menu (CTRL +-) aby wrócić do instrukcji obsługi zdarzeń.  
  
 Następujące zadanie pokazuje, jak technologia IntelliSense automatycznie przechwytuje się program obsługi zdarzeń o nazwie `button1_Click` z polem zdarzeń o nazwie `button1.Click`.  
  
## <a name="see-also"></a>Zobacz też  
 [Visual Studio IDE](../ide/visual-studio-ide.md)
