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
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9d5c9edd47e3db43735d3c6e8f6a4ec1a881214e
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "75595621"
---
# <a name="fonts-and-colors-environment-options-dialog-box"></a>Czcionki i kolory, środowisko, opcje — Okno dialogowe

Strona **Czcionki i kolory** w oknie dialogowym **Opcje** umożliwia ustanowienie niestandardowego schematu czcionek i kolorów dla różnych elementów interfejsu użytkownika w zintegrowanym środowisku programistycznym (IDE). Dostęp do tego okna dialogowego można uzyskać, klikając pozycję**Opcje** **narzędzi** > , a następnie wybierając pozycję**Czcionki i kolory** **środowiska** > .

Zmiany schematu kolorów nie są zacieniane podczas sesji, w której je wykonujesz. Można ocenić zmiany kolorów, otwierając inne wystąpienie programu Visual Studio i tworząc warunki, w których oczekujesz, że zmiany zostaną zastosowane.

**Pokaż ustawienia dla**

Wyświetla listę wszystkich elementów interfejsu użytkownika, dla których można zmienić czcionki i schematy kolorów. Po wybraniu elementu z tej listy można dostosować ustawienia kolorów dla elementu wybranego w **obszarze Elementy wyświetlane**.

- **Edytor tekstu**

     Zmiany ustawień stylu, rozmiaru i koloru edytora tekstu mają wpływ na wygląd tekstu w domyślnym edytorze tekstu. Te ustawienia nie będą miały wpływu na dokumenty otwarte w edytorze tekstu poza IDE.

- **Drukarka**

     Zmiany ustawień stylu, rozmiaru i koloru czcionki dla drukarki wpływają na wygląd tekstu w drukowanych dokumentach.

    > [!NOTE]
    > W razie potrzeby można wybrać inną czcionkę domyślną do drukowania niż czcionka używana do wyświetlania w edytorze tekstu. Może to być przydatne podczas drukowania kodu zawierającego znaki jedno-i dwu bajtowe.

- **Dokańczanie instrukcji**

     Zmienia styl i rozmiar czcionki dla tekstu wyświetlanego w wyskakującym okienku uzupełniania instrukcji w edytorze.

- **Etykietka narzędzia edytora**

     Zmienia styl i rozmiar czcionki tekstu wyświetlanego w etykietkach narzędzi wyświetlanych w edytorze.

- **Czcionka środowiska**

     Zmienia styl i rozmiar czcionki dla wszystkich elementów interfejsu użytkownika IDE, które nie mają jeszcze osobnej opcji w **pokaż ustawienia dla**programu .

     ::: moniker range="vs-2017"

     Na przykład ta opcja ma zastosowanie do **strony początkowej,** ale nie ma wpływu na okno **Dane wyjściowe.**

     ::: moniker-end

- **[Wszystkie narzędzia tekstowe Windows]**

     Zmiany ustawień stylu, rozmiaru i koloru czcionki dla tego elementu wpływają na wygląd tekstu w oknach narzędzi, które mają okienka wyjściowe w IDE. Na przykład okno wyjście, okno polecenia, okno natychmiastowe itp.

    > [!NOTE]
    > Zmiany w tekście elementów **[Wszystkie narzędzia tekstowe systemu Windows]** nie są zacieniane podczas sesji, w której je tworzą. Takie zmiany można ocenić, otwierając inne wystąpienie programu Visual Studio.

**Użyj ustawień domyślnych**

Resetuje wartości czcionek i kolorów elementu listy wybranego w obszarze **Pokaż ustawienia dla**. Przycisk **Użyj** pojawia się, gdy inne schematy wyświetlania są dostępne do wyboru. Można na przykład wybrać jeden z dwóch schematów drukarki.

**Czcionka (pogrubienie oznacza czcionki o stałej szerokości)**

Wyświetla listę wszystkich czcionek zainstalowanych w systemie. Gdy menu rozwijane pojawia się po raz pierwszy, podświetlona jest bieżąca czcionka elementu wybranego w polu **Pokaż ustawienia dla.** Stałe czcionki — które są łatwiejsze do wyrównania w edytorze — są wyświetlane pogrubioną czcionką.

**Rozmiar**

Wyświetla listę dostępnych rozmiarów punktów dla wyróżnionej czcionki. Zmiana rozmiaru czcionki ma wpływ na wszystkie **elementy wyświetlane** dla ustawień **pokazu do** wyboru.

**Wyświetlanie elementów**

Wyświetla listę elementów, dla których można modyfikować kolor pierwszego planu i tła.

> [!NOTE]
> **Zwykły tekst** jest domyślnym elementem wyświetlanym. W związku z tym właściwości przypisane do **PlainText** zostaną zastąpione przez właściwości przypisane do innych elementów wyświetlanych. Na przykład, jeśli przypiszesz kolor niebieski do **zwykłego tekstu,** a kolor zielony do **identyfikatora,** wszystkie identyfikatory będą wyświetlane na zielono. W tym przykładzie właściwości **identyfikatora** zastępują właściwości **Zwykłego Tekstu.**

Niektóre elementy wyświetlania obejmują:

|Element wyświetlany|Opis|
|------------------|-----------------|
|**Zwykły tekst**|Tekst w edytorze.|
|**Zaznaczony tekst**|Tekst, który jest uwzględniony w bieżącym zaznaczeniu, gdy edytor ma fokus.|
|**Nieaktywny zaznaczony tekst**|Tekst, który jest uwzględniony w bieżącym zaznaczeniu, gdy edytor utracił fokus.|
|**Margines wskaźnika**|Margines po lewej stronie Edytora kodu, w którym są wyświetlane punkty przerwania i ikony zakładek.|
|**Numery wierszy**|Opcjonalne numery wyświetlane obok każdego wiersza kodu|
|**Widoczna biała przestrzeń**|Spacje, tabulatory i wskaźniki zawijania wyrazów|
|**Zakładka**|Wiersze, które mają zakładki. **Zakładka** jest widoczna tylko wtedy, gdy margines wskaźnika jest wyłączony.|
|**Dopasowywanie nawiasów klamrowych (podświetlenie)**|Wyróżnianie, które jest zazwyczaj pogrubione formatowanie do pasowania nawiasów klamrowych.|
|**Dopasowywanie nawiasów klamrowych (prostokąt)**|Wyróżnianie, które jest zazwyczaj szary prostokąt w tle.|
|**Punkt przerwania (wyłączony)**|Nie używany.|
|**Punkt przerwania (włączone)**|Określa kolor podświetlenia dla instrukcji lub linii zawierających proste punkty przerwania. Ta opcja ma zastosowanie tylko wtedy, gdy punkty przerwania na poziomie instrukcji są aktywne lub w [oknie dialogowym Ogólne, Debugowanie, Opcje](../../debugger/general-debugging-options-dialog-box.md)zaznaczono opcję **Wyróżnij całą linię źródłową dla punktów przerwania lub bieżącej instrukcji** .|
|**Punkt przerwania (błąd)**|Określa kolor podświetlenia dla instrukcji lub linii zawierających punkty przerwania, które są w stanie błędu. Ma zastosowanie tylko wtedy, gdy punkty przerwania na poziomie instrukcji są aktywne lub w oknie [dialogowym Ogólne, Debugowanie, Opcje](../../debugger/general-debugging-options-dialog-box.md)wybrano opcję **Wyróżnij całą linię źródłową dla punktów przerwania lub bieżącej instrukcji** .|
|**Punkt przerwania (ostrzeżenie)**|Określa kolor podświetlenia dla instrukcji lub linii zawierających punkty przerwania, które są w stanie ostrzegawczym. Ma zastosowanie tylko wtedy, gdy punkty przerwania na poziomie instrukcji są aktywne lub w oknie [dialogowym Ogólne, Debugowanie, Opcje](../../debugger/general-debugging-options-dialog-box.md)wybrano opcję **Wyróżnij całą linię źródłową dla punktów przerwania lub bieżącej instrukcji** .|
|**Punkt przerwania — zaawansowane (wyłączone)**|Określa kolor podświetlenia dla instrukcji lub linii zawierających wyłączone warunkowe lub zliczane punkty przerwania. Ma zastosowanie tylko wtedy, gdy punkty przerwania na poziomie instrukcji są aktywne lub w oknie [dialogowym Ogólne, Debugowanie, Opcje](../../debugger/general-debugging-options-dialog-box.md)wybrano opcję **Wyróżnij całą linię źródłową dla punktów przerwania lub bieżącej instrukcji** .|
|**Punkt przerwania — zaawansowane (włączone)**|Określa kolor podświetlenia dla instrukcji lub linii zawierających warunkowe lub zliczane przez trafienie punkty przerwania. Ma zastosowanie tylko wtedy, gdy punkty przerwania na poziomie instrukcji są aktywne lub w oknie [dialogowym Ogólne, Debugowanie, Opcje](../../debugger/general-debugging-options-dialog-box.md)wybrano opcję **Wyróżnij całą linię źródłową dla punktów przerwania lub bieżącej instrukcji** .|
|**Punkt przerwania — zaawansowane (błąd)**|Określa kolor podświetlenia dla instrukcji lub linii zawierających warunkowe lub zliczane przez trafienie punkty przerwania, które są w stanie błędu. Ma zastosowanie tylko wtedy, gdy punkty przerwania na poziomie instrukcji są aktywne lub w oknie [dialogowym Ogólne, Debugowanie, Opcje](../../debugger/general-debugging-options-dialog-box.md)wybrano opcję **Wyróżnij całą linię źródłową dla punktów przerwania lub bieżącej instrukcji** .|
|**Punkt przerwania — zaawansowane (ostrzeżenie)**|Określa kolor podświetlenia dla instrukcji lub linii zawierających warunkowe lub zliczane przez trafienie punkty przerwania, które są w stanie ostrzegawczym. Ma zastosowanie tylko wtedy, gdy punkty przerwania na poziomie instrukcji są aktywne lub w oknie [dialogowym Ogólne, Debugowanie, Opcje](../../debugger/general-debugging-options-dialog-box.md)wybrano opcję **Wyróżnij całą linię źródłową dla punktów przerwania lub bieżącej instrukcji** .|
|**Punkt przerwania — mapowane (wyłączone)**|Określa kolor podświetlenia dla instrukcji lub linii zawierających wyłączone mapowane punkty przerwania. Ma zastosowanie do asp lub ASP.NET debugowania, jeśli punkty przerwania na poziomie instrukcji są aktywne lub w [oknie dialogowym Ogólne, Debugowanie, Opcje](../../debugger/general-debugging-options-dialog-box.md)wybrano opcję **Wyróżnij całą linię źródłową dla punktów przerwania lub bieżącą instrukcję** .|
|**Punkt przerwania — mapowane (włączone)**|Określa kolor podświetlenia dla instrukcji lub linii zawierających mapowane punkty przerwania. Ma zastosowanie do asp lub ASP.NET debugowania, jeśli punkty przerwania na poziomie instrukcji są aktywne lub w [oknie dialogowym Ogólne, Debugowanie, Opcje](../../debugger/general-debugging-options-dialog-box.md)wybrano opcję **Wyróżnij całą linię źródłową dla punktów przerwania lub bieżącą instrukcję** .|
|**Punkt przerwania — mapowany (błąd)**|Określa kolor podświetlenia dla instrukcji lub linii zawierających mapowane punkty przerwania w stanie błędu. Ma zastosowanie do asp lub ASP.NET debugowania, jeśli punkty przerwania na poziomie instrukcji są aktywne lub w [oknie dialogowym Ogólne, Debugowanie, Opcje](../../debugger/general-debugging-options-dialog-box.md)wybrano opcję **Wyróżnij całą linię źródłową dla punktów przerwania lub bieżącą instrukcję** .|
|**Punkt przerwania — mapowane (ostrzeżenie)**|Określa kolor podświetlenia dla instrukcji lub linii zawierających mapowane punkty przerwania w stanie ostrzegawczym. Ma zastosowanie do asp lub ASP.NET debugowania, jeśli punkty przerwania na poziomie instrukcji są aktywne lub w [oknie dialogowym Ogólne, Debugowanie, Opcje](../../debugger/general-debugging-options-dialog-box.md)wybrano opcję **Wyróżnij całą linię źródłową dla punktów przerwania lub bieżącą instrukcję** .|
|**Słowa kluczowe użytkownika C/C++**|Stała w pliku określonego kodu zdefiniowanego `#define` za pomocą dyrektywy.|
|**Zadzwoń do returnu**|Określa kolor podświetlenia dla instrukcji źródłowych lub wierszy, które wskazują punkty powrotu wywołania, gdy kontekst jest przełączany na ramkę stosu innego niż szczyt podczas debugowania.|
|**Pole zależne fragmentu kodu**|Pole, które zostanie zaktualizowane po zmodyfikowaniu bieżącego pola edytowalnego.|
|**Pole fragmentu kodu**|Edytowalne pole, gdy fragment kodu jest aktywny.|
|**Zwijany tekst**|Blok tekstu lub kodu, który można włączyć i z widoku w Edytorze kodu.|
|**Komentarz**|Komentarze do kodu.|
|**Błąd kompilatora**|Niebieskie squiggles w edytorze wskazując błąd kompilatora.|
|**Zasięg nie dotknął obszaru**|Kod, który nie został objęty testem jednostkowym.|
|**Pokrycie częściowo dotknięty obszar**|Kod, który został częściowo objęty testem jednostkowym.|
|**Obszar dotknięty zasięgiem**|Kod, który został całkowicie objęty testem jednostkowym.|
|**Komentarz CSS**|Komentarz w kaskadowych arkuszach stylów. Przykład:<br /><br /> /* komentarz\*/|
|**Słowo kluczowe CSS**|Słowa kluczowe w kaskadowym arkuszu stylów.|
|**Nazwa właściwości CSS**|Nazwa właściwości, takich jak Tło.|
|**Wartość właściwości CSS**|Wartość przypisana do właściwości, takich jak niebieski.|
|**Selektor CSS**|Ciąg, który identyfikuje, jakie elementy stosuje się do odpowiedniej reguły. Selektor może być prostym selektorem, takim jak "H1", albo selektorem kontekstowym, takim jak "H1 B", który składa się z kilku prostych selektorów.|
|**Wartość ciągu CSS**|Ciąg w kaskadowych arkuszach stylów.|
|**Bieżąca lokalizacja listy**|Bieżąca linia przechodzi do okna narzędzia listy, takiego jak okno Dane wyjściowe lub Znajdź wyniki.|
|**Aktualne oświadczenie**|Określa kolor podświetlenia instrukcji źródłowej lub wiersza, który wskazuje bieżącą pozycję kroku podczas debugowania.|
|**Zmieniono dane debugera**|Kolor tekstu używanego do wyświetlania zmienionych danych w **oknach Rejestry** i **Pamięć.**|
|**Tło okna definicji**|Kolor tła okna **Definicja kodu.**|
|**Bieżące dopasowanie okna definicji**|Bieżąca definicja w oknie **Definicja kodu.**|
|**Nazwa pliku demontażu**|Kolor tekstu używanego do wyświetlania nazw plików przerwy wewnątrz **okna Demontaż.**|
|**Źródło demontażu**|Kolor tekstu używany do wyświetlania linii źródłowych wewnątrz okna **Demontaż.**|
|**Symbol demontażu**|Kolor tekstu używany do wyświetlania nazw symboli w oknie **Demontaż.**|
|**Demontaż tekstu**|Kolor tekstu używanego do wyświetlania kodu operacji i danych wewnątrz okna **Demontaż.**|
|**Wykluczony kod**|Kod, który nie ma być skompilowany, na warunkową `#if`dyrektywę preprocesora, taką jak .|
|**Identyfikator**|Identyfikatory w kodzie, takie jak nazwy klas, nazwy metod i nazwy zmiennych.|
|**Słowo kluczowe**|Słowa kluczowe dla danego języka, które są zarezerwowane. Na przykład: klasa i obszar nazw.|
|**Adres pamięci**|Kolor tekstu używany do wyświetlania kolumny adresu w oknie **Pamięć.**|
|**Zmieniono pamięć**|Kolor tekstu używanego do wyświetlania zmienionych danych w oknie **Pamięć.**|
|**Dane pamięci**|Kolor tekstu używany do wyświetlania danych w oknie **Pamięć.**|
|**Pamięć nieczytelna**|Kolor tekstu używany do wyświetlania nieczytelnych obszarów pamięci w oknie **Pamięć.**|
|**Numer**|Liczba w kodzie reprezentująca rzeczywistą wartość liczbową.|
|**Operator**|Operatory takie jak +, -, i !=.|
|**Inny błąd**|Inne typy błędów nie objęte innymi squiggles błędów. Obecnie obejmuje to niegrzeczne zmiany w edycji i kontynuuj.|
|**Słowo kluczowe preprocesora**|Słowa kluczowe używane przez preprocesora, takie jak #include.|
|**Region tylko do odczytu**|Kod, który nie może być edytowany. Na przykład kod wyświetlany w oknie widoku definicji kodu lub kod, który nie może być modyfikowany podczas edycji i kontynuowania.|
|**Refaktoryzowanie tła**|Kolor tła okna dialogowego **Zmiany podglądu.**|
|**Refaktoryzowanie bieżącego pola**|Kolor tła bieżącego elementu, który ma być refaktoryzowany w oknie dialogowym **Podgląd zmian.**|
|**Refaktoryzowanie pola zależnego**|Kolor odniesień do elementu, który ma być refaktoryzowany w oknie dialogowym **Podgląd zmian.**|
|**Zarejestruj dane**|Kolor tekstu używanego do wyświetlania danych w oknie **Rejestry.**|
|**Zarejestruj nat**|Kolor tekstu używanego do wyświetlania nierozpoznanych danych i obiektów wewnątrz okna **Rejestry.**|
|**Tag inteligentny**|Służy do oznaczania konturu podczas wywoływania tagów inteligentnych.|
|**Znacznik DML SQL**|Dotyczy edytora Transact-SQL. Instrukcje DML w tym edytorze są domyślnie oznaczone obwiednią niebieskiego pola.|
|**Nieświeży kod**|Zastąpiony kod oczekujący na aktualizację. W niektórych przypadkach edycja i kontynuuj nie można zastosować zmiany kodu natychmiast, ale zastosuje je później, jak kontynuować debugowanie. Dzieje się tak, jeśli edytujesz funkcję, która musi wywołać funkcję aktualnie wykonywane lub jeśli dodać więcej niż 64 bajtów nowych zmiennych do funkcji oczekujących na stosie wywołań. W takim przypadku debuger wyświetla okno dialogowe "Ostrzeżenie o nieaktualnym kodzie", a zastąpiony kod będzie nadal wykonywany do momentu zakończenia i wywołania tej funkcji. Edycja i kontynuuj stosuje zmiany kodu w tym czasie.|
|**Ciąg**|Literały.|
|**Ciąg (C# @ Verbatim)**|Literały ciągów w języku C#, które są interpretowane dosłownie. Przykład:<br /><br /> @"x"|
|**Błąd składni**|Błędy analizy.|
|**Skrót listy zadań**|Jeśli skrót **do listy zadań** zostanie dodany do wiersza, a margines wskaźnika zostanie wyłączony, wiersz zostanie wyróżniony.|
|**Punkt śledzenia (wyłączony)**|Nie używany.|
|**Punkt śledzenia (włączony)**|Określa kolor podświetlenia dla instrukcji lub linii zawierających proste punkty śledzenia. Ta opcja ma zastosowanie tylko wtedy, gdy punkty śledzenia na poziomie instrukcji są aktywne lub w [oknie dialogowym Ogólne, Debugowanie, Opcje](../../debugger/general-debugging-options-dialog-box.md)wybrano opcję **Wyróżnij całą linię źródłową dla punktów przerwania lub bieżącą instrukcję** .|
|**Punkt śledzenia (błąd)**|Określa kolor podświetlenia dla instrukcji lub linii zawierających punkty śledzenia, które są w stanie błędu. Ta opcja ma zastosowanie tylko wtedy, gdy punkty śledzenia na poziomie instrukcji są aktywne lub w [oknie dialogowym Ogólne, Debugowanie, Opcje](../../debugger/general-debugging-options-dialog-box.md)wybrano opcję **Wyróżnij całą linię źródłową dla punktów przerwania lub bieżącą instrukcję** .|
|**Punkt śledzenia (ostrzeżenie)**|Określa kolor podświetlenia dla instrukcji lub linii zawierających punkty śledzenia, które są w stanie ostrzegawczym. Ta opcja ma zastosowanie tylko wtedy, gdy punkty śledzenia na poziomie instrukcji są aktywne lub w [oknie dialogowym Ogólne, Debugowanie, Opcje](../../debugger/general-debugging-options-dialog-box.md)wybrano opcję **Wyróżnij całą linię źródłową dla punktów przerwania lub bieżącą instrukcję** .|
|**Tracepoint — zaawansowane (wyłączone)**|Określa kolor podświetlenia dla instrukcji lub linii zawierających wyłączone punkty śledzenia warunkowe lub zliczane przez trafienie. Ta opcja ma zastosowanie tylko wtedy, gdy punkty śledzenia na poziomie instrukcji są aktywne lub w [oknie dialogowym Ogólne, Debugowanie, Opcje](../../debugger/general-debugging-options-dialog-box.md)wybrano opcję **Wyróżnij całą linię źródłową dla punktów przerwania lub bieżącą instrukcję** .|
|**Tracepoint — zaawansowane (włączone)**|Określa kolor podświetlenia dla instrukcji lub linii zawierających punkty śledzenia warunkowe lub zliczane przez trafienie. Ta opcja ma zastosowanie tylko wtedy, gdy punkty śledzenia na poziomie instrukcji są aktywne lub w [oknie dialogowym Ogólne, Debugowanie, Opcje](../../debugger/general-debugging-options-dialog-box.md)wybrano opcję **Wyróżnij całą linię źródłową dla punktów przerwania lub bieżącą instrukcję** .|
|**Tracepoint — zaawansowane (błąd)**|Określa kolor podświetlenia dla instrukcji lub linii zawierających warunkowe lub zliczane przez trafienie punkty śledzenia, które są w stanie błędu. Ta opcja ma zastosowanie tylko wtedy, gdy punkty śledzenia na poziomie instrukcji są aktywne lub w [oknie dialogowym Ogólne, Debugowanie, Opcje](../../debugger/general-debugging-options-dialog-box.md)wybrano opcję **Wyróżnij całą linię źródłową dla punktów przerwania lub bieżącą instrukcję** .|
|**Tracepoint — zaawansowane (ostrzeżenie)**|Określa kolor podświetlenia dla instrukcji lub linii zawierających warunkowe lub zliczane przez trafienie punkty śledzenia, które znajdują się w stanie ostrzegawczym. Ta opcja ma zastosowanie tylko wtedy, gdy punkty śledzenia na poziomie instrukcji są aktywne lub w [oknie dialogowym Ogólne, Debugowanie, Opcje](../../debugger/general-debugging-options-dialog-box.md)wybrano opcję **Wyróżnij całą linię źródłową dla punktów przerwania lub bieżącą instrukcję** .|
|**Tracepoint — mapowane (wyłączone)**|Określa kolor podświetlenia dla instrukcji lub linii zawierających wyłączone mapowane punkty śledzenia. Ma zastosowanie do asp lub ASP.NET debugowania, jeśli punkty przerwania na poziomie instrukcji są aktywne lub w [oknie dialogowym Ogólne, Debugowanie, Opcje](../../debugger/general-debugging-options-dialog-box.md)wybrano opcję **Wyróżnij całą linię źródłową dla punktów przerwania lub bieżącą instrukcję** .|
|**Tracepoint — mapowane (włączone)**|Określa kolor podświetlenia dla instrukcji lub linii zawierających mapowane punkty śledzenia. Ma zastosowanie do asp lub ASP.NET debugowania, jeśli punkty przerwania na poziomie instrukcji są aktywne lub w [oknie dialogowym Ogólne, Debugowanie, Opcje](../../debugger/general-debugging-options-dialog-box.md)wybrano opcję **Wyróżnij całą linię źródłową dla punktów przerwania lub bieżącą instrukcję** .|
|**Tracepoint — mapowane (błąd)**|Określa kolor podświetlenia dla instrukcji lub linii zawierających mapowane punkty śledzenia w stanie błędu. Ma zastosowanie do asp lub ASP.NET debugowania, jeśli punkty przerwania na poziomie instrukcji są aktywne lub w [oknie dialogowym Ogólne, Debugowanie, Opcje](../../debugger/general-debugging-options-dialog-box.md)wybrano opcję **Wyróżnij całą linię źródłową dla punktów przerwania lub bieżącą instrukcję** .|
|**Tracepoint — mapowane (ostrzeżenie)**|Określa kolor podświetlenia dla instrukcji lub linii zawierających mapowane punkty śledzenia w stanie ostrzegawczym. Ma zastosowanie do asp lub ASP.NET debugowania, jeśli punkty przerwania na poziomie instrukcji są aktywne lub w [oknie dialogowym Ogólne, Debugowanie, Opcje](../../debugger/general-debugging-options-dialog-box.md)wybrano opcję **Wyróżnij całą linię źródłową dla punktów przerwania lub bieżącą instrukcję** .|
|**Śledzenie zmian po zapisaniu**|Wiersze kodu, które zostały zmodyfikowane od czasu otwarcia pliku, ale są zapisywane na dysku.|
|**Śledzenie zmian przed zapisaniem**|Wiersze kodu, które zostały zmodyfikowane od czasu otwarcia pliku, ale nie są zapisywane na dysku.|
|**Typy użytkowników**|Typy zdefiniowane przez użytkowników.|
|**Typy użytkowników (pełnomocnicy)**|Wpisz kolor delegatów.|
|**Typy użytkowników (wyliczenia)**|Kolor typu używany dla wyliczenia.|
|**Typy użytkowników (interfejsy)**|Wpisz kolor dla interfejsów.|
|**Typy użytkowników (typy wartości)**|Wpisz kolor dla typów wartości, takich jak struktury w języku C#.|
|**Znacznik tylko do odczytu w języku visual basic**|Znacznik specyficzny dla języka Visual Basic używany do wyznaczania EnC, takich jak regiony wyjątków, definicja metody i ramki wywołań innych niż liść.|
|**Ostrzeżenie**|Ostrzeżenia kompilatora.|
|**Ścieżka linii ostrzegawczych**|Używane w przypadku linii ostrzegawczych analizy statycznej.|
|**Atrybut XML**|Nazwy atrybutów.|
|**Cudzysłowy atrybutów XML**|Znaki cudzysłowu dla atrybutów XML.|
|**Wartość atrybutu XML**|Zawartość atrybutów XML.|
|**Sekcja XML Cdata**|Zawartość \<! [CDATA[...]] >.|
|**Komentarz XML**|Zawartość \<!-- -->.|
|**Ogranicznik XML**|Ograniczniki składni XML, w tym <, <?, <!, \<!--, -->, ? \>, \<! [, ]] > i [, ].|
|**Atrybut doc XML**|Wartość atrybutu dokumentacji xml, takiego \<jak param name="I" > gdzie jest pokolorowany "I".|
|**Komentarz do doc XML**|Komentarze zawarte w komentarzach do dokumentacji xml.|
|**XML Doc Tag**|Znaczniki w komentarzach doc XML, takie jak<br /><br /> /// \<> podsumowujących.|
|**Słowo kluczowe XML**|Słowa kluczowe DTD, takie jak CDATA, IDREF i NDATA.|
|**Nazwa XML**|Nazwy elementów i instrukcje przetwarzania nazwa docelowa.|
|**Instrukcja przetwarzania XML**|Zawartość instrukcji przetwarzania, z wyłączeniem nazwy docelowej.|
|**Tekst XML**|Zawartość elementu zwykłego tekstu.|
|**Słowo kluczowe XSLT**|Nazwy elementów XSLT.|

**Pierwszy plan elementu**

Wyświetla listę dostępnych kolorów, które można wybrać dla pierwszego planu elementu wybranego w **pozycji Wyświetl elementy**. Ponieważ niektóre elementy są powiązane i dlatego powinny zachować spójny schemat wyświetlania, zmiana koloru pierwszego planu tekstu zmienia również ustawienia domyślne dla elementów, takich jak błąd kompilatora, słowo kluczowe lub operator.

**Automatyczny**

Elementy mogą dziedziczyć kolor pierwszego planu z innych elementów wyświetlanych, takich jak **zwykły tekst**. Korzystając z tej opcji, po zmianie koloru dziedziczonego elementu wyświetlanego kolor powiązanych elementów wyświetlanych również zmienia się automatycznie. Na przykład, jeśli wybrano wartość **automatyczną** dla **błędu kompilatora,** a później zmieniono kolor **zwykłego tekstu** na czerwony, **błąd kompilatora** również automatycznie dziedziczy kolor Czerwony.

**Domyślny**

Kolor, który pojawia się dla elementu przy pierwszym otwarciu programu Visual Studio. Kliknięcie przycisku **Użyj ustawień domyślnych** powoduje zresetowanie do tego koloru.

**Niestandardowy**

Wyświetla okno dialogowe Kolor umożliwiający ustawienie niestandardowego koloru elementu wybranego na liście Elementy wyświetlane.

> [!NOTE]
> Możliwość definiowania kolorów niestandardowych może być ograniczona przez ustawienia kolorów wyświetlania komputera. Jeśli na przykład komputer ma wyświetlać 256 kolorów i w oknie dialogowym **Kolor** zostanie wybrany kolor niestandardowy, w polu podglądu **kolorów** jest domyślnie wyświetlany **kolor** podstawowy, który jest wyświetlany w kolorze czarnym.

**Tło elementu**

Zawiera paletę kolorów, z której można wybrać kolor tła dla elementu wybranego w **pozycji Wyświetl elementy**. Ponieważ niektóre elementy są powiązane i dlatego powinny zachować spójny schemat wyświetlania, zmiana koloru tła tekstu zmienia również wartości domyślne dla elementów, takich jak błąd kompilatora, słowo kluczowe lub operator.

**Automatyczny**

Elementy mogą dziedziczyć kolor tła z innych elementów wyświetlanych, takich jak **zwykły tekst**. Korzystając z tej opcji, po zmianie koloru dziedziczonego elementu wyświetlanego kolor powiązanych elementów wyświetlanych również zmienia się automatycznie. Na przykład, jeśli wybrano wartość **automatyczną** dla **błędu kompilatora,** a później zmieniono kolor **zwykłego tekstu** na czerwony, **błąd kompilatora** również automatycznie dziedziczy kolor Czerwony.

**Domyślny**

Kolor, który pojawia się dla elementu przy pierwszym otwarciu programu Visual Studio. Kliknięcie przycisku **Użyj ustawień domyślnych** powoduje zresetowanie do tego koloru.

**Niestandardowy**

Wyświetla okno dialogowe Kolor umożliwiający ustawienie niestandardowego koloru elementu wybranego na liście Elementy wyświetlane.

**Pogrubienie**

Wybierz tę opcję, aby wyświetlić tekst zaznaczonych **elementów wyświetlanych** pogrubioną czcionką. Pogrubiony tekst jest łatwiejszy do zidentyfikowania w edytorze.

**Przykładowe**

Wyświetla próbkę stylu czcionki, rozmiaru i schematu kolorów dla wybranych **ustawień pokaż** i **Wyświetl elementy.** To pole służy do wyświetlania podglądu wyników podczas eksperymentowania z różnymi opcjami formatowania.

## <a name="see-also"></a>Zobacz też

- [Opcje — Okno dialogowe](../../ide/reference/options-dialog-box-visual-studio.md)
- [Porady: Zmiana czcionek i kolorów](../../ide/how-to-change-fonts-and-colors-in-visual-studio.md)
