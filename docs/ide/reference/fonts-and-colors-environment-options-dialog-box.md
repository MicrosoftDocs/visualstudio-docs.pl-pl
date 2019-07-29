---
title: Czcionki i kolory, środowisko, opcje — Okno dialogowe
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.FontsAndColors
- VS.ToolsOptionsPages.Environment.Fonts_And_Colors
- VS.Environment.Fonts And Colors
helpviewer_keywords:
- colors, customizing IDE
- Query and View Designer, customizing
- fonts, editors
- menus, customizing
- Table Designer, customizing
- Database Designer, customizing environment
- default colors
- accessibility, options
- editors, customizing
- designers, customizing environment
- defaults, colors
- printers, customizing
ms.assetid: c767d302-51ed-47a8-a527-c07bce2aa485
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5b05d6651f865a300a0c065c5e0a275cb29fd309
ms.sourcegitcommit: ce1ab8a25c66a83e60eab80ed8e1596fe66dd85c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/29/2019
ms.locfileid: "68605418"
---
# <a name="fonts-and-colors-environment-options-dialog-box"></a>Czcionki i kolory, środowisko, opcje — Okno dialogowe

Na stronie **czcionki i kolory** okna dialogowego **Opcje** można utworzyć niestandardową czcionkę i schemat kolorów dla różnych elementów interfejsu użytkownika w zintegrowanym środowisku programistycznym (IDE). Możesz uzyskać dostęp do tego okna dialogowego, klikając**Opcje** **Narzędzia** > , a następnie wybierając**czcionki i kolory** **środowiska** > .

Zmiany schematu kolorów nie są stosowane podczas sesji, w której zostały wprowadzone. Zmiany kolorów można oszacować, otwierając inne wystąpienie programu Visual Studio i podając warunki, w których zmiany mają być stosowane.

**Pokaż ustawienia dla**

Wyświetla listę wszystkich elementów interfejsu użytkownika, dla których można zmienić czcionkę i schematy kolorów. Po wybraniu elementu z tej listy można dostosować ustawienia koloru dla elementu wybranego w **pozycji Wyświetl elementy**.

- **Edytor tekstu**

     Zmiany ustawień stylu, rozmiaru i koloru czcionki dla edytora tekstu wpływają na wygląd tekstu w domyślnym edytorze tekstu. Te ustawienia nie mają wpływ na dokumenty otwierane w edytorze tekstu poza środowiskiem IDE.

- **Urządzenie**

     Zmiany stylu, rozmiaru i koloru czcionki dla drukarki mają wpływ na wygląd tekstu w drukowanych dokumentach.

    > [!NOTE]
    > W razie potrzeby możesz wybrać inną domyślną czcionkę do drukowania niż ta, która została użyta do wyświetlania w edytorze tekstu. Może to być przydatne podczas drukowania kodu, który zawiera znaki jednobajtowe i dwubajtowe.

- **Uzupełnianie instrukcji**

     Zmienia styl i rozmiar czcionki dla tekstu wyświetlanego w wyskakującym zakończeniu wykonywania instrukcji w edytorze.

- **Etykietka narzędzia edytora**

     Zmienia styl i rozmiar czcionki dla tekstu wyświetlanego w etykietach narzędzi wyświetlanych w edytorze.

- **Czcionka środowiska**

     Zmienia styl i rozmiar czcionki dla wszystkich elementów interfejsu użytkownika IDE, które nie mają jeszcze oddzielnej opcji w obszarze **Pokaż ustawienia dla**.

     ::: moniker range="vs-2017"

     Na przykład ta opcja ma zastosowanie do **strony Start** , ale nie ma wpływu na okno **dane wyjściowe** .

     ::: moniker-end

- **[Wszystkie okna narzędzi tekstowych]**

     Zmiany ustawień stylu, rozmiaru i koloru czcionki dla tego elementu mają wpływ na wygląd tekstu w oknach narzędzi, które mają okienka danych wyjściowych w IDE. Na przykład okno dane wyjściowe, okno Polecenie, natychmiastowe okno itd.

    > [!NOTE]
    > Zmiany tekstu **[wszystkie narzędzia tekstowe narzędzi tekstowych]** nie są stosowane podczas sesji, w której zostały wprowadzone. Możesz oszacować takie zmiany, otwierając inne wystąpienie programu Visual Studio.

**Użyj domyślnych**

Resetuje czcionkę i wartości koloru elementu listy wybrane w obszarze **Pokaż ustawienia dla**. Przycisk **Użyj** pojawia się, gdy dostępne są inne schematy wyświetlania. Można na przykład wybrać spośród dwóch schematów dla drukarki.

**Czcionka (pogrubienie oznacza czcionkę o stałej szerokości)**

Wyświetla wszystkie czcionki zainstalowane w systemie. Po pierwszym wyświetleniu menu rozwijanego zostanie wyróżniona bieżąca czcionka elementu wybranego w polu **Pokaż ustawienia dla** pola. Stałe czcionki — które są łatwiejsze do dopasowania w edytorze — są wyświetlane pogrubione.

**Zmienia**

Wyświetla listę dostępnych rozmiarów punktów dla zaznaczonej czcionki. Zmiana rozmiaru czcionki ma wpływ na wszystkie **elementy wyświetlane** dla wybranych **ustawień** .

**Wyświetl elementy**

Wyświetla listę elementów, dla których można modyfikować kolor pierwszego planu i tła.

> [!NOTE]
> **Zwykły tekst** jest domyślnym elementem wyświetlanym. W związku z tym właściwości przypisane do **zwykłego tekstu** zostaną przesłonięte przez właściwości przypisane do innych elementów wyświetlania. Na przykład, Jeśli przypiszesz kolor niebieski do **zwykłego tekstu** i kolor zielony na **Identyfikator**, wszystkie identyfikatory będą wyświetlane w kolorze zielonym. W tym przykładzie właściwości **identyfikatora** zastępują właściwości w **postaci zwykłego tekstu** .

Do niektórych elementów wyświetlanych należą:

|Wyświetl element|Opis|
|------------------|-----------------|
|**Zwykły tekst**|Tekst w edytorze.|
|**Zaznaczony tekst**|Tekst, który jest zawarty w bieżącym zaznaczeniu, gdy Edytor ma fokus.|
|**Nieaktywny zaznaczony tekst**|Tekst, który jest zawarty w bieżącym zaznaczeniu po utracie fokusu przez Edytor.|
|**Margines wskaźnika**|Margines po lewej stronie edytora kodu, w którym są wyświetlane punkty przerwania i ikony zakładek.|
|**Numery wierszy**|Opcjonalne numery, które pojawiają się obok każdego wiersza kodu|
|**Widoczny biały znak**|Spacje, tabulatory i wskaźniki zawijania tekstu|
|**Zakładka**|Linie z zakładkami. **Zakładka** jest widoczna tylko wtedy, gdy margines wskaźnika jest wyłączony.|
|**Dopasowywanie nawiasów klamrowych (wyróżnianie)**|Wyróżnianie, które jest zwykle pogrubione dla pasujących nawiasów klamrowych.|
|**Dopasowywanie nawiasów klamrowych (prostokąt)**|Wyróżnianie zwykle szarego prostokąta w tle.|
|**Punkt przerwania (wyłączony)**|Nie używany.|
|**Punkt przerwania (włączony)**|Określa kolor wyróżniania dla instrukcji lub linii zawierających proste punkty przerwania. Ta opcja ma zastosowanie tylko wtedy, gdy punkty przerwania na poziomie instrukcji są aktywne lub opcja Wyróżnij **cały wiersz źródła dla punktów przerwania lub bieżącej instrukcji** jest zaznaczona w [oknie dialogowym ogólne, debugowanie, opcje](../../debugger/general-debugging-options-dialog-box.md).|
|**Punkt przerwania (błąd)**|Określa kolor wyróżnienia dla instrukcji lub wierszy zawierających punkty przerwania, które są w stanie błędu. Dotyczy tylko sytuacji, gdy punkty przerwania na poziomie instrukcji są aktywne lub opcja Wyróżnij **cały wiersz źródła dla punktów przerwania lub bieżącej instrukcji** jest zaznaczona w [oknie dialogowym ogólne, debugowanie, opcje](../../debugger/general-debugging-options-dialog-box.md).|
|**Punkt przerwania (ostrzeżenie)**|Określa kolor wyróżnienia dla instrukcji lub wierszy zawierających punkty przerwania, które są w stanie ostrzegawczym. Dotyczy tylko sytuacji, gdy punkty przerwania na poziomie instrukcji są aktywne lub opcja Wyróżnij **cały wiersz źródła dla punktów przerwania lub bieżącej instrukcji** jest zaznaczona w [oknie dialogowym ogólne, debugowanie, opcje](../../debugger/general-debugging-options-dialog-box.md).|
|**Punkt przerwania — zaawansowany (wyłączony)**|Określa kolor wyróżnienia dla instrukcji lub linii zawierających wyłączone punkty przerwania, które zostały obliczone warunkowo lub trafień. Dotyczy tylko sytuacji, gdy punkty przerwania na poziomie instrukcji są aktywne lub opcja Wyróżnij **cały wiersz źródła dla punktów przerwania lub bieżącej instrukcji** jest zaznaczona w [oknie dialogowym ogólne, debugowanie, opcje](../../debugger/general-debugging-options-dialog-box.md).|
|**Punkt przerwania — zaawansowany (włączony)**|Określa kolor wyróżnienia dla instrukcji lub linii zawierających punkty przerwania, które są zliczane lub trafień. Dotyczy tylko sytuacji, gdy punkty przerwania na poziomie instrukcji są aktywne lub opcja Wyróżnij **cały wiersz źródła dla punktów przerwania lub bieżącej instrukcji** jest zaznaczona w [oknie dialogowym ogólne, debugowanie, opcje](../../debugger/general-debugging-options-dialog-box.md).|
|**Punkt przerwania — zaawansowany (błąd)**|Określa kolor wyróżnienia instrukcji lub linii zawierających punkty przerwania, które znajdują się w stanie błędu. Dotyczy tylko sytuacji, gdy punkty przerwania na poziomie instrukcji są aktywne lub opcja Wyróżnij **cały wiersz źródła dla punktów przerwania lub bieżącej instrukcji** jest zaznaczona w [oknie dialogowym ogólne, debugowanie, opcje](../../debugger/general-debugging-options-dialog-box.md).|
|**Punkt przerwania — zaawansowany (ostrzeżenie)**|Określa kolor wyróżnienia dla instrukcji lub linii zawierających punkty przerwania, które są w stanie ostrzeżenia. Dotyczy tylko sytuacji, gdy punkty przerwania na poziomie instrukcji są aktywne lub opcja Wyróżnij **cały wiersz źródła dla punktów przerwania lub bieżącej instrukcji** jest zaznaczona w [oknie dialogowym ogólne, debugowanie, opcje](../../debugger/general-debugging-options-dialog-box.md).|
|**Punkt przerwania — zamapowany (wyłączony)**|Określa kolor wyróżnienia dla instrukcji lub wierszy zawierających wyłączone zmapowane punkty przerwania. Dotyczy debugowania ASP lub **ASP.NET, jeśli** są aktywne punkty przerwania na poziomie instrukcji lub w [oknie dialogowym ogólne, debugowanie, opcje](../../debugger/general-debugging-options-dialog-box.md).|
|**Punkt przerwania — zamapowany (włączony)**|Określa kolor wyróżnienia dla instrukcji lub linii zawierających zmapowane punkty przerwania. Dotyczy debugowania ASP lub **ASP.NET, jeśli** są aktywne punkty przerwania na poziomie instrukcji lub w [oknie dialogowym ogólne, debugowanie, opcje](../../debugger/general-debugging-options-dialog-box.md).|
|**Punkt przerwania — zamapowany (błąd)**|Określa kolor wyróżnienia dla instrukcji lub linii zawierających zamapowane punkty przerwania w stanie błędu. Dotyczy debugowania ASP lub **ASP.NET, jeśli** są aktywne punkty przerwania na poziomie instrukcji lub w [oknie dialogowym ogólne, debugowanie, opcje](../../debugger/general-debugging-options-dialog-box.md).|
|**Punkt przerwania — zamapowany (ostrzeżenie)**|Określa kolor wyróżnienia dla instrukcji lub linii zawierających zamapowane punkty przerwania w stanie ostrzegawczym. Dotyczy debugowania ASP lub **ASP.NET, jeśli** są aktywne punkty przerwania na poziomie instrukcji lub w [oknie dialogowym ogólne, debugowanie, opcje](../../debugger/general-debugging-options-dialog-box.md).|
|**Słowa kluczoweC++ języka C/User**|Stała w ramach określonego pliku kodu zdefiniowanego za pomocą `#define` dyrektywy.|
|**Wywołanie zwrotne**|Określa kolor wyróżnienia dla instrukcji lub wierszy źródła, które wskazują punkty powrotu wywołania, gdy kontekst jest przełączany do nienajwyższej ramki stosu podczas debugowania.|
|**Pole zależne od fragmentu kodu**|Pole, które zostanie zaktualizowane po zmodyfikowaniu bieżącego pola edytowalnego.|
|**Pole fragmentu kodu**|Pole można edytować, gdy fragment kodu jest aktywny.|
|**Tekst zwijany**|Blok tekstu lub kodu, który może być przełączany i wyświetlany w edytorze kodu.|
|**Komentarz**|Komentarze do kodu.|
|**Błąd kompilatora**|Niebieskie Zawijanie w edytorze wskazujące błąd kompilatora.|
|**Obszar nieobjęty pokryciem**|Kod, który nie został objęty testem jednostkowym.|
|**Obszar pokrycia częściowo naruszony**|Kod, który został częściowo objęty testem jednostkowym.|
|**Obszar objęty pokryciem**|Kod, który został całkowicie objęty testem jednostkowym.|
|**Komentarz CSS**|Komentarz w kaskadowe arkusze stylów. Na przykład:<br /><br /> /* komentarz\*/|
|**Słowo kluczowe CSS**|Słowa kluczowe w kaskadowym arkuszu stylów.|
|**Nazwa właściwości CSS**|Nazwa właściwości, na przykład tło.|
|**Wartość właściwości CSS**|Wartość przypisana do właściwości, takiej jak niebieska.|
|**Selektor CSS**|Ciąg, który identyfikuje elementy, do których odnosi się odpowiednia reguła. Selektor może być prostym selektorem, takim jak "H1" lub selektorem kontekstowym, takim jak "H1 B", który składa się z kilku prostych selektorów.|
|**Wartość ciągu CSS**|Ciąg w kaskadowe arkusze stylów.|
|**Bieżąca lokalizacja listy**|Bieżący wiersz z przechodzeniem do okna narzędzia listy, na przykład okno dane wyjściowe lub wyszukiwanie okien wyników.|
|**Current — instrukcja**|Określa kolor wyróżnienia źródłowej instrukcji lub linii, która wskazuje bieżącą pozycję kroku podczas debugowania.|
|**Zmieniono dane debugera**|Kolor tekstu służący do wyświetlania zmienionych danych w **rejestrach** i w oknach **pamięci** .|
|**Tło okna definicji**|Kolor tła okna **definicji kodu** .|
|**Bieżące dopasowanie okna definicji**|Bieżąca Definicja w oknie **definicji kodu** .|
|**Nazwa pliku rozasemblera**|Kolor tekstu służący do wyświetlania przerw w nazwie pliku w oknie **demontażu** .|
|**Źródło demontażu**|Kolor tekstu służący do wyświetlania linii źródłowych w oknie **demontażu** .|
|**Symbol demontażu**|Kolor tekstu służący do wyświetlania nazw symboli wewnątrz okna **demontażu** .|
|**Rozmontaż tekstu**|Kolor tekstu służący do wyświetlania wartości op-Code i danych w oknie **demontażu** .|
|**Wykluczony kod**|Kod, który nie jest kompilowany, na warunkową dyrektywę preprocesora, taką jak `#if`.|
|**Identyfikatora**|Identyfikatory w kodzie, takie jak nazwy klas, metody nazw i nazwy zmiennych.|
|**Keyword**|Słowa kluczowe dla danego języka, które są zarezerwowane. Na przykład: Klasa i przestrzeń nazw.|
|**Adres pamięci**|Kolor tekstu używanego do wyświetlania kolumny Address w oknie **pamięci** .|
|**Pamięć zmieniła się**|Kolor tekstu używanego do wyświetlania zmienionych danych w oknie **pamięci** .|
|**Dane pamięci**|Kolor tekstu używanego do wyświetlania danych w oknie **pamięci** .|
|**Pamięć nieczytelna**|Kolor tekstu służący do wyświetlania nieczytelnych obszarów pamięci w oknie **pamięci** .|
|**Liczba**|Liczba w kodzie, która reprezentuje rzeczywistą wartość liczbową.|
|**Operator**|Operatory, takie jak +,-i! =.|
|**Inny błąd**|Inne typy błędów, które nie są objęte innymi zygzakami błędów. Obecnie obejmuje to edycję prosta w obszarze Edytuj i Kontynuuj.|
|**Preprocesor — słowo kluczowe**|Słowa kluczowe używane przez preprocesor, takie jak #include.|
|**Region tylko do odczytu**|Kod, którego nie można edytować. Przykład kodu wyświetlanego w oknie widoku definicji kodu lub w kodzie, którego nie można modyfikować podczas Edytuj i Kontynuuj.|
|**Tło refaktoryzacji**|Kolor tła okna dialogowego **Podgląd zmian** .|
|**Refaktoryzacja bieżącego pola**|Kolor tła bieżącego elementu do refaktoryzacji w oknie dialogowym **Podgląd zmian** .|
|**Refaktoryzacja pola zależnego**|Kolor odwołań elementu do refaktoryzacji w oknie dialogowym **Podgląd zmian** .|
|**Rejestruj dane**|Kolor tekstu służący do wyświetlania danych w oknie **rejestrów** .|
|**Rejestrowanie translatora adresów sieciowych**|Kolor tekstu służący do wyświetlania nierozpoznanych danych i obiektów w oknie **rejestrów** .|
|**Tag inteligentny**|Służy do określenia konspektu, gdy Tagi inteligentne są wywoływane.|
|**Znacznik DML SQL**|Dotyczy edytora Transact-SQL. Instrukcje DML w tym edytorze są domyślnie oznaczone jako powiązane niebieskie pole.|
|**Nieodświeżony kod**|Zastąpiony kod oczekujący na aktualizację. W niektórych przypadkach polecenie Edytuj i Kontynuuj nie może natychmiast zastosować zmian w kodzie, ale zostaną one zastosowane później w przypadku kontynuowania debugowania. Dzieje się tak, Jeśli edytujesz funkcję, która musi wywołać obecnie wykonywaną funkcję, lub jeśli dodasz więcej niż 64 bajtów nowych zmiennych do funkcji oczekującej na stos wywołań. W takim przypadku debuger wyświetli okno dialogowe "nieodświeżone ostrzeżenie o kodzie", a zastąpiony kod będzie wykonywany do momentu zakończenia działania i zostanie wywołany ponownie. Edytuj i Kontynuuj stosuje zmiany kodu w tym czasie.|
|**Ciąg**|Literały ciągu.|
|**Ciąg (C# @ Verbatim)**|Literały ciągu w C# , które są interpretowane Verbatim. Na przykład:<br /><br /> @"x"|
|**Błąd składniowy**|Analizuj błędy.|
|**Skrót Lista zadań**|Jeśli do wiersza zostanie dodany skrót **Lista zadań** , a margines wskaźnika jest wyłączony, wiersz zostanie wyróżniony.|
|**Punkt śledzenia (wyłączone)**|Nie używany.|
|**Punkt śledzenia (włączone)**|Określa kolor wyróżnienia dla instrukcji lub linii zawierających prostą punkty śledzenia. Ta opcja ma zastosowanie tylko wtedy, gdy punkty śledzenia na poziomie instrukcji są aktywne lub opcja Wyróżnij **cały wiersz źródłowy dla punktów przerwania lub bieżącej instrukcji** jest zaznaczona w [oknie dialogowym ogólne, debugowanie, opcje](../../debugger/general-debugging-options-dialog-box.md).|
|**Punkt śledzenia (błąd)**|Określa kolor wyróżnienia dla instrukcji lub wierszy zawierających punkty śledzenia, które są w stanie błędu. Ta opcja ma zastosowanie tylko wtedy, gdy punkty śledzenia na poziomie instrukcji są aktywne lub opcja Wyróżnij **cały wiersz źródłowy dla punktów przerwania lub bieżącej instrukcji** jest zaznaczona w [oknie dialogowym ogólne, debugowanie, opcje](../../debugger/general-debugging-options-dialog-box.md).|
|**Punkt śledzenia (ostrzeżenie)**|Określa kolor wyróżnienia dla instrukcji lub wierszy zawierających punkty śledzenia, które są w stanie ostrzegawczym. Ta opcja ma zastosowanie tylko wtedy, gdy punkty śledzenia na poziomie instrukcji są aktywne lub opcja Wyróżnij **cały wiersz źródłowy dla punktów przerwania lub bieżącej instrukcji** jest zaznaczona w [oknie dialogowym ogólne, debugowanie, opcje](../../debugger/general-debugging-options-dialog-box.md).|
|**Punkt śledzenia — zaawansowany (wyłączony)**|Określa kolor wyróżnienia dla instrukcji lub linii zawierających wyłączoną punkty śledzenia warunkowe lub z trafieniem. Ta opcja ma zastosowanie tylko wtedy, gdy punkty śledzenia na poziomie instrukcji są aktywne lub opcja Wyróżnij **cały wiersz źródłowy dla punktów przerwania lub bieżącej instrukcji** jest zaznaczona w [oknie dialogowym ogólne, debugowanie, opcje](../../debugger/general-debugging-options-dialog-box.md).|
|**Punkt śledzenia — zaawansowany (włączony)**|Określa kolor wyróżnienia dla instrukcji lub linii zawierających punkty śledzenia lub zliczane jako trafień. Ta opcja ma zastosowanie tylko wtedy, gdy punkty śledzenia na poziomie instrukcji są aktywne lub opcja Wyróżnij **cały wiersz źródłowy dla punktów przerwania lub bieżącej instrukcji** jest zaznaczona w [oknie dialogowym ogólne, debugowanie, opcje](../../debugger/general-debugging-options-dialog-box.md).|
|**Punkt śledzenia — zaawansowany (błąd)**|Określa kolor wyróżnienia dla instrukcji lub wierszy zawierających punkty śledzenia lub zliczane jako trafień, które są w stanie błędu. Ta opcja ma zastosowanie tylko wtedy, gdy punkty śledzenia na poziomie instrukcji są aktywne lub opcja Wyróżnij **cały wiersz źródłowy dla punktów przerwania lub bieżącej instrukcji** jest zaznaczona w [oknie dialogowym ogólne, debugowanie, opcje](../../debugger/general-debugging-options-dialog-box.md).|
|**Punkt śledzenia — zaawansowany (ostrzeżenie)**|Określa kolor wyróżnienia dla instrukcji lub linii zawierających punkty śledzenia lub zliczane jako trafień, które są w stanie ostrzegawczym. Ta opcja ma zastosowanie tylko wtedy, gdy punkty śledzenia na poziomie instrukcji są aktywne lub opcja Wyróżnij **cały wiersz źródłowy dla punktów przerwania lub bieżącej instrukcji** jest zaznaczona w [oknie dialogowym ogólne, debugowanie, opcje](../../debugger/general-debugging-options-dialog-box.md).|
|**Punkt śledzenia — zamapowany (wyłączony)**|Określa kolor wyróżnienia dla instrukcji lub wierszy zawierających wyłączone mapowane punkty śledzenia. Dotyczy debugowania ASP lub **ASP.NET, jeśli** są aktywne punkty przerwania na poziomie instrukcji lub w [oknie dialogowym ogólne, debugowanie, opcje](../../debugger/general-debugging-options-dialog-box.md).|
|**Punkt śledzenia — zamapowany (włączony)**|Określa kolor wyróżnienia dla instrukcji lub linii zawierających zamapowane punkty śledzenia. Dotyczy debugowania ASP lub **ASP.NET, jeśli** są aktywne punkty przerwania na poziomie instrukcji lub w [oknie dialogowym ogólne, debugowanie, opcje](../../debugger/general-debugging-options-dialog-box.md).|
|**Punkt śledzenia — zamapowany (błąd)**|Określa kolor wyróżnienia dla instrukcji lub wierszy zawierających zamapowane punkty śledzenia w stanie błędu. Dotyczy debugowania ASP lub **ASP.NET, jeśli** są aktywne punkty przerwania na poziomie instrukcji lub w [oknie dialogowym ogólne, debugowanie, opcje](../../debugger/general-debugging-options-dialog-box.md).|
|**Punkt śledzenia — zamapowany (ostrzeżenie)**|Określa kolor wyróżnienia dla instrukcji lub wierszy zawierających zamapowane punkty śledzenia w stanie ostrzegawczym. Dotyczy debugowania ASP lub **ASP.NET, jeśli** są aktywne punkty przerwania na poziomie instrukcji lub w [oknie dialogowym ogólne, debugowanie, opcje](../../debugger/general-debugging-options-dialog-box.md).|
|**Śledź zmiany po zapisaniu**|Wiersze kodu, które zostały zmodyfikowane od czasu otwarcia pliku, ale zostały zapisane na dysku.|
|**Śledź zmiany przed zapisaniem**|Wiersze kodu, które zostały zmodyfikowane od czasu otwarcia pliku, ale nie zostały zapisane na dysku.|
|**Typy użytkowników**|Typy zdefiniowane przez użytkowników.|
|**Typy użytkowników (delegatów)**|Kolor typu dla delegatów.|
|**Typy użytkowników (wyliczenia)**|Kolor typu używany dla typów wyliczeniowych.|
|**Typy użytkowników (interfejsy)**|Kolor typu dla interfejsów.|
|**Typy użytkowników (typy wartości)**|Kolor typu dla typów wartości, takich jak struktury w C#.|
|**Visual Basic znacznik tylko do odczytu**|Znacznik charakterystyczny dla Visual Basic używany do wyznaczania elementu EnC, takiego jak regiony wyjątków, definicja metody i ramki wywołania innego niż liść.|
|**Ostrzeżenie**|Ostrzeżenia kompilatora.|
|**Ścieżka linii ostrzeżeń**|Używane dla linii ostrzeżeń analizy statycznej.|
|**Atrybut XML**|Nazwy atrybutów.|
|**Cudzysłowy atrybutu XML**|Znaki cudzysłowu dla atrybutów XML.|
|**Wartość atrybutu XML**|Zawartość atrybutów XML.|
|**Sekcja CDATA XML**|Zawartość \<![CDATA[...]]>.|
|**Komentarz XML**|Zawartość \<>!----.|
|**Ogranicznik XML**|Ograniczniki składni XML, w tym <, <?, <!, \<!--,-->,?\>, \<! [,]] > i [,].|
|**Atrybut XML doc**|Wartość atrybutu dokumentacji XML, taka jak \<param Name = "I" >, gdzie "i" jest kolorem.|
|**Komentarz dokumentacji XML**|Komentarze ujęte w komentarzach dokumentacji XML.|
|**Tag doc XML**|Tagi w komentarzach doc XML, takie jak<br /><br /> /// \<> podsumowania.|
|**Słowo kluczowe XML**|Słowa kluczowe DTD, takie jak CDATA, IDREF i nnazwa.|
|**Nazwa XML**|Nazwy elementów i instrukcje przetwarzania nazwy docelowej.|
|**Instrukcja przetwarzania XML**|Zawartość instrukcji przetwarzania, bez uwzględnienia nazwy docelowej.|
|**Tekst XML**|Zawartość elementu zwykłego tekstu.|
|**Słowo kluczowe XSLT**|Nazwy elementów XSLT.|

**Pierwszy plan elementu**

Wyświetla listę dostępnych kolorów, które można wybrać dla pierwszego planu elementu zaznaczonego w **pozycji Wyświetl elementy**. Ponieważ niektóre elementy są powiązane i dlatego powinny zachować spójny schemat wyświetlania, zmiana koloru pierwszego planu tekstu powoduje zmianę ustawień domyślnych dla elementów, takich jak błąd kompilatora, słowo kluczowe lub operator.

**Automatyczne**

Elementy mogą dziedziczyć kolor pierwszego planu z innych elementów wyświetlanych, takich jak **zwykły tekst**. Przy użyciu tej opcji, gdy zmienisz kolor dziedziczonego elementu wyświetlanego, kolor elementów wyświetlanych jest również zmieniany automatycznie. Na przykład jeśli wybrano wartość **Automatyczna** dla **błędu kompilatora** , a później zmieniono kolor **zwykłego tekstu** na czerwony, **błąd kompilatora** również automatycznie odziedziczy kolor czerwony.

**Default**

Kolor wyświetlany dla elementu przy pierwszym otwarciu programu Visual Studio. Kliknięcie przycisku **Użyj ustawień domyślnych** spowoduje zresetowanie do tego koloru.

**Custom**

Wyświetla okno dialogowe Kolor umożliwiające ustawienie niestandardowego koloru dla elementu zaznaczonego na liście elementy wyświetlania.

> [!NOTE]
> Możliwość definiowania niestandardowych kolorów może być ograniczona przez ustawienia koloru na ekranie. Na przykład, jeśli komputer jest ustawiony tak, aby wyświetlał 256 kolorów i wybierzesz kolor niestandardowy z okna dialogowego **kolor** , środowisko IDE domyślnie zostanie zbliżone do najbliższego dostępnego **koloru podstawowego** i wyświetla kolor czarny w polu Podgląd **koloru** .

**Tło elementu**

Udostępnia paletę kolorów, z której można wybrać kolor tła dla elementu wybranego w **pozycji elementy wyświetlania**. Ponieważ niektóre elementy są powiązane i dlatego powinny zachować spójny schemat wyświetlania, zmiana koloru tła tekstu powoduje zmianę ustawień domyślnych dla elementów, takich jak błąd kompilatora, słowo kluczowe lub operator.

**Automatyczne**

Elementy mogą dziedziczyć kolor tła z innych elementów wyświetlanych, takich jak **zwykły tekst**. Przy użyciu tej opcji, gdy zmienisz kolor dziedziczonego elementu wyświetlanego, kolor elementów wyświetlanych jest również zmieniany automatycznie. Na przykład jeśli wybrano wartość **Automatyczna** dla **błędu kompilatora** , a później zmieniono kolor **zwykłego tekstu** na czerwony, **błąd kompilatora** również automatycznie odziedziczy kolor czerwony.

**Default**

Kolor wyświetlany dla elementu przy pierwszym otwarciu programu Visual Studio. Kliknięcie przycisku **Użyj ustawień domyślnych** spowoduje zresetowanie do tego koloru.

**Custom**

Wyświetla okno dialogowe Kolor umożliwiające ustawienie niestandardowego koloru dla elementu zaznaczonego na liście elementy wyświetlania.

**Bold**

Zaznacz tę opcję, aby wyświetlić tekst wybranych **elementów wyświetlanych** w postaci pogrubionego tekstu. Tekst pogrubiony jest łatwiejszy do zidentyfikowania w edytorze.

**Northwind**

Wyświetla przykładowy styl czcionki, rozmiar i schemat kolorów dla wybranych elementów **Pokaż ustawienia dla** i **wyświetlania** . To pole służy do wyświetlania podglądu wyników podczas eksperymentu z różnymi opcjami formatowania.

## <a name="see-also"></a>Zobacz także

- [Opcje, okno dialogowe](../../ide/reference/options-dialog-box-visual-studio.md)
- [Instrukcje: Zmiana czcionek i kolorów](../../ide/how-to-change-fonts-and-colors-in-visual-studio.md)