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
ms.openlocfilehash: b3fd18198811f6235c4e5d0627303e4243ad595b
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/22/2019
ms.locfileid: "56700266"
---
# <a name="fonts-and-colors-environment-options-dialog-box"></a>Czcionki i kolory, środowisko, opcje — Okno dialogowe

**Czcionki i kolory** strony **opcje** okno dialogowe umożliwia ustanawianie niestandardowy schemat czcionek i kolorów dla różnych elementów interfejsu użytkownika w zintegrowanym środowisku programistycznym (IDE). To okno dialogowe można skorzystać, klikając **narzędzia** > **opcje**, a następnie wybierając **środowiska** > **czcionek i Kolory**. Jeśli ta strona nie jest wyświetlana na liście, wybierz opcję **Pokaż wszystkie ustawienia** w **opcje** okno dialogowe.

Kolor schemat zmiany wprowadzone podczas sesji, w której należy. Możesz ocenić zmiany kolorów, otwierając innego wystąpienia programu Visual Studio i tworzenie warunków, w których oczekujesz, że zmiany do zastosowania.

**Pokaż ustawienia dla**

Wyświetla listę wszystkich elementów interfejsu użytkownika, dla których można zmienić czcionkę i kolor schematów. Po wybraniu elementu z tej listy można dostosować ustawienia kolorów dla elementu zaznaczonego w **wyświetlania elementów**.

-   **Edytor tekstu**

     Zmiany styl czcionki, rozmiaru i koloru ustawienia wyświetlania do edytora tekstów wpływają na wygląd tekstu w edytorze tekstu domyślnego. Te ustawienia nie wpłynie dokumentów otwartych w edytorze tekstów poza IDE.

-   **Drukarki**

     Zmiany styl czcionki, rozmiaru i wyświetlania kolorów dla drukarki na wygląd tekstu w dokumentach.

    > [!NOTE]
    > W razie potrzeby można wybrać czcionkę różne domyślne związane z drukowaniem niż ten używany do wyświetlania w edytorze tekstów. Może to być przydatne podczas drukowania kodu, który zawiera znaków jednobajtowych i dwubajtowych.

-   **Uzupełnianie instrukcji**

     Zmienia styl i rozmiar czcionki dla tekstu, który pojawia się w uzupełniania wyskakujących w edytorze.

-   **Etykietki narzędzi edytora**

     Zmienia styl i rozmiar czcionki dla tekstu wyświetlanego w etykietkach narzędzi jest wyświetlany w edytorze.

-   **Czcionka środowiska**

     Zmienia styl czcionki i rozmiar wszystkie elementy interfejsu użytkownika IDE, które nie mają już osobną opcją w **Pokaż ustawienia dla**.

     ::: moniker range="vs-2017"

     Na przykład, ta opcja ma zastosowanie do **strona startowa** , ale nie ma wpływu na **dane wyjściowe** okna.

     ::: moniker-end

-   **[Wszystkie tekstowe narzędzie Windows]**

     Zmiany styl czcionki, rozmiaru i koloru ustawienia wyświetlania na ten element wpływ wygląd tekstu w oknach narzędzi, których okienka danych wyjściowych w środowisku IDE. Na przykład okno danych wyjściowych, okno polecenia, okno bezpośrednie itp.

    > [!NOTE]
    > Zmiany w tekście z **[wszystkie tekstowe narzędzie Windows]** elementy zostaną wprowadzone podczas sesji, w której należy. Możesz ocenić takie zmiany, otwierając innego wystąpienia programu Visual Studio.

**Użyj wartości domyślnych**

Powoduje zresetowanie wartości czcionkę i kolor elementu listy, który wybrano w **Pokaż ustawienia dla**. **Użyj** przycisk jest wyświetlany, gdy do wyboru dostępne są inne systemy wyświetlania. Na przykład można wybierać spośród dwóch systemów dla drukarki.

**Czcionka (Pogrubienie oznacza czcionki o stałej szerokości)**

Wyświetla listę wszystkich czcionek, które są zainstalowane w systemie. Kiedy menu rozwijane po raz pierwszy występuje, bieżącą czcionkę dla elementu wybranego w **Pokaż ustawienia dla** pola zostanie wyróżniona. Naprawiono czcionki — które są łatwiejsze do wyrównania w edytorze — są wyświetlane pogrubioną czcionką.

**Rozmiar**

Listy dostępnych punktów rozmiarów wyróżnione czcionki. Zmiana rozmiaru czcionki wpływa na wszystkie **wyświetlania elementów** dla **Pokaż ustawienia dla** zaznaczenia.

**Wyświetl elementy**

Wyświetla listę elementów, dla których można zmodyfikować kolor pierwszego planu i tła.

> [!NOTE]
> **Zwykły tekst** elementu wyświetlana domyślna. W efekcie właściwości przypisane do **PlainText** zostaną zastąpione przez właściwości, przypisane do innych elementów wyświetlana. Na przykład, jeśli przypisujesz kolor niebieski na **PlainText** i kolor na zielony do **identyfikator**, wszystkie identyfikatory będą wyświetlane w kolorze zielonym. W tym przykładzie **identyfikator** zastąpienie właściwości **PlainText** właściwości.

Wyświetl elementy, należą:

|Element ekran|Opis|
|------------------|-----------------|
|**Zwykły tekst**|Tekst w edytorze.|
|**Zaznaczony tekst**|Tekst, który znajduje się w bieżącym zaznaczeniu, gdy Edytor ma fokus.|
|**Nieaktywny zaznaczony tekst**|Tekst, który znajduje się w bieżącym zaznaczeniu, gdy Edytor utraciła fokus.|
|**Margines wskaźnika**|Margines edytora kodu gdzie punkty przerwania i zakładki ikony są wyświetlane po lewej stronie.|
|**Numery wierszy**|Numery opcjonalne, które pojawiają się obok każdego wiersza kodu|
|**Pokazuj biały znak**|Miejsca do magazynowania, kart oraz zawijanie wierszy wskaźników|
|**Zakładka**|Wiersze, które mają zakładek. **Zakładki** jest widoczna tylko po margines wskaźnika jest wyłączona.|
|**Dopasowywanie nawiasów (Podświetl)**|Wyróżnianie, który jest zazwyczaj pogrubienie dla dopasowywanie nawiasów klamrowych.|
|**Dopasowywanie nawiasów (prostokąt)**|Wyróżnianie, który zazwyczaj jest szary prostokąt w tle.|
|**Punkt przerwania (wyłączony)**|Nie używany.|
|**Punkt przerwania (włączony)**|Określa kolor wyróżnienia instrukcji lub wiersze zawierające proste punktów przerwania. Ta opcja ma zastosowanie tylko wtedy, gdy poziom poufności punkty przerwania są aktywne lub **Podświetl cały wiersz źródła dla punktów przerwania lub bieżącą instrukcję** zaznaczona jest opcja [ogólne, debugowanie, okno dialogowe Opcje](../../debugger/general-debugging-options-dialog-box.md).|
|**Punkt przerwania (błąd)**|Określa kolor wyróżnienia instrukcji lub wiersze zawierające punkty przerwania, które znajdują się w stanie błędu. Dotyczy tylko wtedy, gdy poziom poufności punkty przerwania są aktywne lub **Podświetl cały wiersz źródła dla punktów przerwania lub bieżącą instrukcję** zaznaczona jest opcja [ogólne, debugowanie, okno dialogowe Opcje](../../debugger/general-debugging-options-dialog-box.md).|
|**Punkt przerwania (ostrzeżenie)**|Określa kolor wyróżnienia instrukcji lub wiersze zawierające punkty przerwania, które znajdują się w stanie ostrzeżenia. Dotyczy tylko wtedy, gdy poziom poufności punkty przerwania są aktywne lub **Podświetl cały wiersz źródła dla punktów przerwania lub bieżącą instrukcję** zaznaczona jest opcja [ogólne, debugowanie, okno dialogowe Opcje](../../debugger/general-debugging-options-dialog-box.md).|
|**Punkt przerwania — zaawansowany (wyłączony)**|Określa kolor wyróżnienia instrukcji lub wiersze zawierające wyłączony warunkowego najmniej liczone trafień punktu przerwania. Dotyczy tylko wtedy, gdy poziom poufności punkty przerwania są aktywne lub **Podświetl cały wiersz źródła dla punktów przerwania lub bieżącą instrukcję** zaznaczona jest opcja [ogólne, debugowanie, okno dialogowe Opcje](../../debugger/general-debugging-options-dialog-box.md).|
|**Punkt przerwania — zaawansowany (włączony)**|Określa kolor wyróżnienia instrukcji lub wiersze zawierające warunkowego najmniej liczone trafień punktu przerwania. Dotyczy tylko wtedy, gdy poziom poufności punkty przerwania są aktywne lub **Podświetl cały wiersz źródła dla punktów przerwania lub bieżącą instrukcję** zaznaczona jest opcja [ogólne, debugowanie, okno dialogowe Opcje](../../debugger/general-debugging-options-dialog-box.md).|
|**Punkt przerwania — zaawansowany (błąd)**|Określa kolor wyróżnienia instrukcji lub wiersze zawierające warunkowych lub liczone trafień punktów przerwania, które znajdują się w stanie błędu. Dotyczy tylko wtedy, gdy poziom poufności punkty przerwania są aktywne lub **Podświetl cały wiersz źródła dla punktów przerwania lub bieżącą instrukcję** zaznaczona jest opcja [ogólne, debugowanie, okno dialogowe Opcje](../../debugger/general-debugging-options-dialog-box.md).|
|**Punkt przerwania — zaawansowany (ostrzeżenie)**|Określa kolor wyróżnienia instrukcji lub wiersze zawierające warunkowych lub liczone trafień punktów przerwania, które są w stanie ostrzeżenia. Dotyczy tylko wtedy, gdy poziom poufności punkty przerwania są aktywne lub **Podświetl cały wiersz źródła dla punktów przerwania lub bieżącą instrukcję** zaznaczona jest opcja [ogólne, debugowanie, okno dialogowe Opcje](../../debugger/general-debugging-options-dialog-box.md).|
|**Punkt przerwania — zamapowany (wyłączony)**|Określa kolor wyróżnienia instrukcji lub wiersze zawierające wyłączone zamapowanego punktów przerwania. Odpowiednie dla stron ASP lub ASP.NET debugowania, jeśli poziom poufności punkty przerwania są aktywne lub **Podświetl cały wiersz źródła dla punktów przerwania lub bieżącą instrukcję** zaznaczona jest opcja [ogólne, debugowanie, okno dialogowe Opcje Pole](../../debugger/general-debugging-options-dialog-box.md).|
|**Punkt przerwania — zamapowany (włączony)**|Określa, że kolor wyróżnienia instrukcji lub wiersze zawierające mapowane punktów przerwania. Odpowiednie dla stron ASP lub ASP.NET debugowania, jeśli poziom poufności punkty przerwania są aktywne lub **Podświetl cały wiersz źródła dla punktów przerwania lub bieżącą instrukcję** zaznaczona jest opcja [ogólne, debugowanie, okno dialogowe Opcje Pole](../../debugger/general-debugging-options-dialog-box.md).|
|**Punkt przerwania — zamapowany (błąd)**|Określa, że kolor wyróżnienia instrukcji lub wiersze zawierające mapowane punktów przerwania w stanie błędu. Odpowiednie dla stron ASP lub ASP.NET debugowania, jeśli poziom poufności punkty przerwania są aktywne lub **Podświetl cały wiersz źródła dla punktów przerwania lub bieżącą instrukcję** zaznaczona jest opcja [ogólne, debugowanie, okno dialogowe Opcje Pole](../../debugger/general-debugging-options-dialog-box.md).|
|**Punkt przerwania — zamapowany (ostrzeżenie)**|Określa, że kolor wyróżnienia instrukcji lub wiersze zawierające mapowane punkty przerwania z ostrzeżeniami. Odpowiednie dla stron ASP lub ASP.NET debugowania, jeśli poziom poufności punkty przerwania są aktywne lub **Podświetl cały wiersz źródła dla punktów przerwania lub bieżącą instrukcję** zaznaczona jest opcja [ogólne, debugowanie, okno dialogowe Opcje Pole](../../debugger/general-debugging-options-dialog-box.md).|
|**Słowa kluczowe użytkownika języka C/C++**|Stała w pliku określonym kodem zdefiniowane przez `#define` dyrektywy.|
|**Powrót z wywołania**|Określa kolor wyróżnienia instrukcji źródła lub wiersze, które wskazują punkty zwracany wywołanie po przełączeniu kontekstu do ramki stosu-top podczas debugowania.|
|**Pole zależne od fragmentu kodu**|Pole, które zostaną zaktualizowane po zmodyfikowaniu bieżące pole można edytować.|
|**Pole fragmentu kodu**|Można edytować pole fragmentu kodu jest aktywny.|
|**Zwijane tekstu**|Blok tekstu lub kod, który może być przełączane z widoku w edytorze kodu.|
|**Komentarz**|Komentarze w kodzie.|
|**Błąd kompilatora**|Niebieski faliste linie w edytorze wskazujący błąd kompilatora.|
|**Obszar bez pokrycia**|Kod, który ma nie pasuje do żadnego testu jednostkowego.|
|**Obszar częściowo pokryty**|Kod, który ma zostać częściowo zasłonięte przez test jednostkowy.|
|**Obszar pokryty**|Kod, który ma zostać całkowicie omówione przez test jednostkowy.|
|**Komentarz w kodzie CSS**|Komentarz w kaskadowych arkuszy stylów. Na przykład:<br /><br /> / * komentarz \*/|
|**CSS — słowo kluczowe**|Słowa kluczowe w arkuszu stylów kaskadowych.|
|**Nazwa właściwości CSS**|Nazwa właściwości, na przykład tła.|
|**Wartość właściwości CSS**|Wartość przypisana do właściwości, takie jak blue.|
|**Selektor CSS**|Ciąg, który identyfikuje elementy dotyczy odpowiednią regułę. Selektor może być prosty selektor, takie "H1" lub kontekstowe selektora, takie jak "B H1", która składa się z kilku zastąpienia selektorów prostych.|
|**Wartość ciągu CSS**|Ciąg w kaskadowych arkuszy stylów.|
|**Bieżąca lokalizacja listy**|W oknie narzędzia listy, takich jak okno danych wyjściowych i windows Find Results przejście, bieżącego wiersza.|
|**Bieżąca instrukcja**|Określa kolor wyróżnienia źródła instrukcji lub wierszu, który wskazuje bieżącą pozycję w kroku podczas debugowania.|
|**Zmiany danych debugera**|Kolor tekstu używany do wyświetlania zmienionych danych wewnątrz **rejestruje** i **pamięci** systemu windows.|
|**Tło okna definicji**|Kolor tła **definicji kodu** okna.|
|**Bieżące dopasowanie okno definicji**|Bieżącej definicji w **definicji kodu** okna.|
|**Nazwa pliku dezasemblacji**|Kolor tekstu używany do wyświetlania pliku nazwa podziału wewnątrz **dezasemblacji** okna.|
|**Źródło dezasemblacji**|Kolor tekstu używany do wyświetlania źródła wierszy wewnątrz **dezasemblacji** okna.|
|**Symbol dezasemblacji**|Kolor tekstu używany do wyświetlania nazwy symboli wewnątrz **dezasemblacji** okna.|
|**Tekst dezasemblacji**|Kolor tekstu używany do wyświetlania op kod i dane wewnątrz **dezasemblacji** okna.|
|**Wykluczone kodu**|Kod, który jest nie mają być skompilowane, każdej warunkowego dyrektywy preprocesora takich jak `#if`.|
|**Identyfikator**|Identyfikatory w kodzie, takich jak nazwy klas, metod, nazwy i nazwy zmiennych.|
|**Keyword**|Słowa kluczowe dla danego języka, które są zastrzeżone. Na przykład: klasy i przestrzeni nazw.|
|**Adres pamięci**|Kolor tekstu używany do wyświetlania kolumny adres wewnątrz **pamięci** okna.|
|**Pamięć zmieniła się**|Kolor tekstu używany do wyświetlania zmienionych danych wewnątrz **pamięci** okna.|
|**Dane pamięci**|Kolor tekstu używany do wyświetlania danych wewnątrz **pamięci** okna.|
|**Pamięć niemożliwa do odczytu**|Kolor tekstu używany do wyświetlania obszary pamięci nie można go odczytać w ramach **pamięci** okna.|
|**Liczba**|Liczba w kodzie, który reprezentuje rzeczywisty wartość liczbową.|
|**Operator**|Operatory, takie jak +, -, i! =.|
|**Inny błąd**|Inne typy błędów nie pasuje do żadnego innymi zygzaki sygnalizujące błędy. Obecnie dotyczy to również prosta zmiany w Edytuj i Kontynuuj.|
|**Preprocesora — słowo kluczowe**|Słowa kluczowe używane przez preprocesor, takich jak #include.|
|**Region tylko do odczytu**|Kod, który nie może być edytowany. Na przykład kod wyświetlany w oknie widoku definicji kodu lub kod, który nie może być modyfikowany podczas operacji Edytuj i Kontynuuj.|
|**Refaktoryzowanie tła**|Kolor tła **podgląd zmian** okno dialogowe.|
|**Refaktoryzacja bieżącego pola**|Kolor bieżącego elementu refaktoryzacji w tła **podgląd zmian** okno dialogowe.|
|**Refaktoryzacja zależnych pól**|Kolor odwołania elementu, który ma być refaktoryzowany w **podgląd zmian** okno dialogowe.|
|**Dane rejestru**|Kolor tekstu używany do wyświetlania danych wewnątrz **rejestruje** okna.|
|**Zarejestruj NAT**|Kolor tekstu używany do wyświetlania Nierozpoznane dane i obiektów wewnątrz **rejestruje** okna.|
|**Tagi inteligentne**|Używany do określenia konspektu, gdy tagi inteligentne są wywoływane.|
|**Marker SQL DML**|Ma zastosowanie do edytora Transact-SQL. Domyślnie instrukcji DML, w tym edytorze są oznaczone obwiedni niebieski.|
|**Kod nieodświeżony**|Oczekiwanie na aktualizację zastąpioną kod. W niektórych przypadkach Edytuj i Kontynuuj nie można zastosować zmian w kodzie natychmiast, ale zastosuje je później w miarę dalszego debugowania. Dzieje się tak, jeśli edytujesz funkcja, która musi wywołać funkcję w trakcie wykonywania lub jeśli dodasz więcej niż 64 bajtów nowe zmienne do oczekiwania na stosie wywołań funkcji. W takim przypadku, debuger wyświetla okno dialogowe "Ostrzeżenie o kodzie Nieodświeżonym", a zastąpione kodu kontynuuje wykonywanie do momentu w danym funkcji zostanie zakończone i wywoływana jest ponownie. Edytuj i Kontynuuj ma zastosowanie zmian w kodzie, w tym czasie.|
|**Ciąg**|Literały ciągu.|
|**Ciąg (C# @ Verbatim)**|Literały języka C#, które są interpretowane dosłowne wyrażenie. Na przykład:<br /><br /> @"x"|
|**Błąd składni**|Błędy analizy.|
|**Skrót do listy zadań**|Jeśli **listy zadań** skrót zostanie dodany do wiersza i margines wskaźnika jest wyłączona, zostanie wyróżniony wiersz.|
|**Punkt śledzenia (wyłączony)**|Nie używany.|
|**Punkt śledzenia (włączony)**|Określa kolor wyróżnienia instrukcji lub wiersze zawierające proste punkty śledzenia. Ta opcja ma zastosowanie tylko wtedy, gdy poziom poufności punkty śledzenia są aktywne lub **Podświetl cały wiersz źródła dla punktów przerwania lub bieżącą instrukcję** zaznaczona jest opcja [ogólne, debugowanie, okno dialogowe Opcje](../../debugger/general-debugging-options-dialog-box.md).|
|**Punkt śledzenia (błąd)**|Określa kolor wyróżnienia instrukcji lub wiersze zawierające punkty śledzenia, które są w stanie błędu. Ta opcja ma zastosowanie tylko wtedy, gdy poziom poufności punkty śledzenia są aktywne lub **Podświetl cały wiersz źródła dla punktów przerwania lub bieżącą instrukcję** zaznaczona jest opcja [ogólne, debugowanie, okno dialogowe Opcje](../../debugger/general-debugging-options-dialog-box.md).|
|**Punkt śledzenia (ostrzeżenie)**|Określa kolor wyróżnienia instrukcji lub wiersze zawierające punkty śledzenia, które są w stanie ostrzeżenia. Ta opcja ma zastosowanie tylko wtedy, gdy poziom poufności punkty śledzenia są aktywne lub **Podświetl cały wiersz źródła dla punktów przerwania lub bieżącą instrukcję** zaznaczona jest opcja [ogólne, debugowanie, okno dialogowe Opcje](../../debugger/general-debugging-options-dialog-box.md).|
|**Punkt śledzenia — zaawansowany (wyłączony)**|Określa, że kolor wyróżnienia instrukcji lub wiersze zawierające wyłączone punkty śledzenia warunkowego lub liczone trafień. Ta opcja ma zastosowanie tylko wtedy, gdy poziom poufności punkty śledzenia są aktywne lub **Podświetl cały wiersz źródła dla punktów przerwania lub bieżącą instrukcję** zaznaczona jest opcja [ogólne, debugowanie, okno dialogowe Opcje](../../debugger/general-debugging-options-dialog-box.md).|
|**Punkt śledzenia — zaawansowany (włączony)**|Określa kolor wyróżnienia instrukcji lub wiersze zawierające punkty śledzenia warunkowego lub liczone trafień. Ta opcja ma zastosowanie tylko wtedy, gdy poziom poufności punkty śledzenia są aktywne lub **Podświetl cały wiersz źródła dla punktów przerwania lub bieżącą instrukcję** zaznaczona jest opcja [ogólne, debugowanie, okno dialogowe Opcje](../../debugger/general-debugging-options-dialog-box.md).|
|**Punkt śledzenia — zaawansowany (błąd)**|Określa kolor wyróżnienia instrukcji lub wiersze zawierające warunkowych lub liczone trafień punkty śledzenia, które są w stanie błędu. Ta opcja ma zastosowanie tylko wtedy, gdy poziom poufności punkty śledzenia są aktywne lub **Podświetl cały wiersz źródła dla punktów przerwania lub bieżącą instrukcję** zaznaczona jest opcja [ogólne, debugowanie, okno dialogowe Opcje](../../debugger/general-debugging-options-dialog-box.md).|
|**Punkt śledzenia — zaawansowany (ostrzeżenie)**|Określa kolor wyróżnienia instrukcji lub wiersze zawierające warunkowych lub liczone trafień punkty śledzenia, które są w stanie ostrzeżenia. Ta opcja ma zastosowanie tylko wtedy, gdy poziom poufności punkty śledzenia są aktywne lub **Podświetl cały wiersz źródła dla punktów przerwania lub bieżącą instrukcję** zaznaczona jest opcja [ogólne, debugowanie, okno dialogowe Opcje](../../debugger/general-debugging-options-dialog-box.md).|
|**Punkt śledzenia — zamapowany (wyłączony)**|Określa kolor wyróżnienia instrukcji lub wiersze zawierające wyłączone zamapowanego punkty śledzenia. Odpowiednie dla stron ASP lub ASP.NET debugowania, jeśli poziom poufności punkty przerwania są aktywne lub **Podświetl cały wiersz źródła dla punktów przerwania lub bieżącą instrukcję** zaznaczona jest opcja [ogólne, debugowanie, okno dialogowe Opcje Pole](../../debugger/general-debugging-options-dialog-box.md).|
|**Punkt śledzenia — zamapowany (włączony)**|Określa, że kolor wyróżnienia instrukcji lub wiersze zawierające mapowane punkty śledzenia. Odpowiednie dla stron ASP lub ASP.NET debugowania, jeśli poziom poufności punkty przerwania są aktywne lub **Podświetl cały wiersz źródła dla punktów przerwania lub bieżącą instrukcję** zaznaczona jest opcja [ogólne, debugowanie, okno dialogowe Opcje Pole](../../debugger/general-debugging-options-dialog-box.md).|
|**Punkt śledzenia — zamapowany (błąd)**|Określa, że kolor wyróżnienia instrukcji lub wiersze zawierające mapowany punkty śledzenia z błędami. Odpowiednie dla stron ASP lub ASP.NET debugowania, jeśli poziom poufności punkty przerwania są aktywne lub **Podświetl cały wiersz źródła dla punktów przerwania lub bieżącą instrukcję** zaznaczona jest opcja [ogólne, debugowanie, okno dialogowe Opcje Pole](../../debugger/general-debugging-options-dialog-box.md).|
|**Punkt śledzenia — zamapowany (ostrzeżenie)**|Określa, że kolor wyróżnienia instrukcji lub wiersze zawierające mapowany punkty śledzenia z ostrzeżeniami. Odpowiednie dla stron ASP lub ASP.NET debugowania, jeśli poziom poufności punkty przerwania są aktywne lub **Podświetl cały wiersz źródła dla punktów przerwania lub bieżącą instrukcję** zaznaczona jest opcja [ogólne, debugowanie, okno dialogowe Opcje Pole](../../debugger/general-debugging-options-dialog-box.md).|
|**Śledź zmiany po zapisaniu**|Wiersze kodu, które zostały zmodyfikowane, ponieważ plik został otwarty, ale nie są zapisywane na dysku.|
|**Śledź zmiany przed zapisaniem**|Wiersze kodu, które zostały zmodyfikowane, ponieważ plik został otwarty, ale nie są zapisywane na dysku.|
|**Typy użytkownika**|Typy definiowane przez użytkowników.|
|**Użytkownik wpisuje (delegatów)**|Typ koloru dla obiektów delegowanych.|
|**Użytkownik wpisuje (wyliczenia)**|Wpisz kolor używany dla typów wyliczeniowych.|
|**Użytkownik wpisuje (interfejsy)**|Typ koloru dla interfejsów.|
|**Użytkownik wpisuje (typy wartości)**|Typ koloru dla typów wartości, takie jak struktury w języku C#.|
|**Znacznik tylko odczyt języka Visual Basic**|Znacznik specyficzne dla języka Visual Basic, używany do wyznaczania EnC, takich jak regiony wyjątek, definicję metody i ramki wywołanie elementu członkowskiego typu liść.|
|**Ostrzeżenie**|Ostrzeżenia kompilatora.|
|**Ścieżka linii ostrzeżeń**|Używany linii ostrzeżeń analizy statycznej.|
|**Atrybut XML**|Nazwy atrybutów.|
|**Cudzysłowy atrybutu XML**|Znaki cudzysłowu dla atrybutów XML.|
|**Wartość atrybutu XML**|Zawartość atrybutów XML.|
|**Sekcja Cdata XML**|Zawartość \<![CDATA[...]]>.|
|**Komentarz XML**|Zawartość \<!---->.|
|**XML Delimiter**|Ograniczniki składni XML, w tym <, <?, <!, \<!-,-->,?\>, \<! [,]] > i [,].|
|**Atrybut dokumentu XML**|Wartość dokumentacji xml atrybutów, takich jak \<param name = "I" > gdzie "I" jest w trybie kolorowym.|
|**Komentarz dokumentu XML**|Komentarze, ujęte w komentarze dokumentacji xml.|
|**XML Doc Tag**|Komentarze tagów w dokumencie XML, takich jak<br /><br /> /// \<Podsumowanie >.|
|**Słowo kluczowe XML**|Słowa kluczowe DTD CDATA, IDREF i NDATA.|
|**Nazwa XML**|Nazwy elementów i nazwa docelowego instrukcje przetwarzania.|
|**Instrukcja przetwarzania XML**|Zawartość instrukcje przetwarzania nie zawiera nazwy docelowej.|
|**Tekst XML**|Zawartość elementu zwykłego tekstu.|
|**XSLT Keyword**|Nazwy elementów XSLT.|

**Pierwszy plan elementu**

Wyświetla listę dostępnych kolorów, można wybrać dla pierwszego planu elementu wybranego w **wyświetlania elementów**. Ponieważ niektóre elementy są ze sobą powiązane i w związku z tym należy zachować schemat spójne wyświetlanie, zmiana kolorem tekstu także zmianę wartości domyślne dla elementów, takich jak błąd kompilatora, słowo kluczowe lub Operator.

**Automatyczne**

Elementy może dziedziczyć kolor pierwszego planu innych wyświetle elementy takie jak **zwykły tekst**. Przy użyciu tej opcji, po zmianie koloru elementu dziedziczone wyświetlania, kolor elementów powiązanych wyświetlaną również zmienić automatycznie. Na przykład w przypadku wybrania **automatyczne** wartość **błąd kompilatora** i później zmienić kolor **zwykły tekst** czerwony, **błąd kompilatora**będzie również automatycznie dziedziczył kolor czerwony.

**Default**

Kolor, który pojawia się po raz pierwszy element programu Visual Studio. Klikając **Użyj ustawień domyślnych** przycisku powoduje przywrócenie tego koloru.

**Custom**

Wyświetla okno dialogowe kolorów do umożliwiają ustawianie koloru niestandardowego elementu wybranego na liście elementów ekranu.

> [!NOTE]
> Możliwość definiowanie kolorów niestandardowych, może być ograniczona przez ustawienia kolorów dla tego ekranu komputera. Na przykład, jeśli komputer jest równa 256 kolorów, a następnie wybierz kolor niestandardowy z **kolor** okno dialogowe IDE wartością domyślną jest najbardziej dostępna **kolor podstawowy** i wyświetla kolor czarny w **Kolor** okno podglądu.

**Tło elementu**

Udostępnia paletę kolorów, w którym można wybrać kolor tła dla elementu zaznaczonego w **wyświetlania elementów**. Ponieważ niektóre elementy są ze sobą powiązane i w związku z tym należy zachować schemat spójne wyświetlanie, zmiana koloru tła tekstu także zmianę wartości domyślne dla elementów, takich jak błąd kompilatora, słowo kluczowe lub Operator.

**Automatyczne**

Elementy może dziedziczyć kolor tła innych wyświetle elementy takie jak **zwykły tekst**. Przy użyciu tej opcji, po zmianie koloru elementu dziedziczone wyświetlania, kolor elementów powiązanych wyświetlaną również zmienić automatycznie. Na przykład w przypadku wybrania **automatyczne** wartość **błąd kompilatora** i później zmienić kolor **zwykły tekst** czerwony, **błąd kompilatora**będzie również automatycznie dziedziczył kolor czerwony.

**Default**

Kolor, który pojawia się po raz pierwszy element programu Visual Studio. Klikając **Użyj ustawień domyślnych** przycisku powoduje przywrócenie tego koloru.

**Custom**

Wyświetla okno dialogowe kolorów do umożliwiają ustawianie koloru niestandardowego elementu wybranego na liście elementów ekranu.

**Bold**

Wybierz tę opcję, aby wyświetlić tekst wybranego **wyświetlania elementów** pogrubioną czcionką. Tekst pogrubiony jest łatwiejszy do zidentyfikowania w edytorze.

**Próbki**

Wyświetla przykładowe styl czcionki, rozmiaru i schemat kolorów na potrzeby **Pokaż ustawienia dla** i **wyświetlania elementów** wybrane. Podgląd wyników, ponieważ możesz eksperymentować z różnych opcji formatowania, można użyć tego pola.

## <a name="see-also"></a>Zobacz także

- [Środowisko, Opcje — okno dialogowe](../../ide/reference/environment-options-dialog-box.md)
- [Opcje, okno dialogowe](../../ide/reference/options-dialog-box-visual-studio.md)
- [Instrukcje: Zmiana czcionek i kolorów](../../ide/how-to-change-fonts-and-colors-in-visual-studio.md)