---
title: Opcje, edytor tekstu, C/C++, zaawansowane
description: Dowiedz się, jak użyć strony Zaawansowane w sekcji C/C++, aby zmienić zachowanie związane z technologią IntelliSense i bazą danych przeglądania.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.C\C++.Advanced
- VS.ToolsOptionsPages.Text_Editor.C%2FC%2B%2B.Advanced
- VS.ToolsOptionsPages.Text_Editor.C/C++.Advanced
helpviewer_keywords:
- Text Editor Options dialog box, advanced
ms.assetid: 67c82ae5-fddd-49df-baec-8e7498b156f3
author: corob-msft
ms.author: corob
manager: markl
ms.workload:
- cplusplus
ms.openlocfilehash: fe69471d231599c6e3eece0b56ff70fca5b6afab
ms.sourcegitcommit: 967c2f8c1b3f805cf42c0246389517689d971b53
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/25/2020
ms.locfileid: "96040345"
---
# <a name="options-text-editor-cc-advanced"></a>Opcje, edytor tekstu, C/C++, zaawansowane

Zmieniając te opcje, można zmienić zachowanie związane z technologią IntelliSense i bazą danych przeglądania podczas programowania w języku C lub C++.

Aby uzyskać dostęp do tej strony, w oknie dialogowym **Opcje** w okienku po lewej stronie rozwiń pozycję **Edytor tekstu**, rozwiń węzeł **C/C++**, a następnie wybierz pozycję **Zaawansowane**.

> [!NOTE]
> Na komputerze w poniższych instrukcjach mogą być wyświetlane inne nazwy i lokalizacje niektórych elementów interfejsu użytkownika programu Visual Studio. Te elementy są określane przez numer wersji Visual Studio oraz twoje ustawienia. Zobacz [personalizowanie środowiska IDE programu Visual Studio](../../ide/personalizing-the-visual-studio-ide.md).

## <a name="browsingnavigation"></a>Przeglądanie/Nawigacja

Nigdy nie należy wybierać tych opcji, z wyjątkiem rzadkich przypadków, w których rozwiązanie jest tak duże, że działanie bazy danych zużywa nieakceptowalną ilość zasobów systemowych.

**Wyłącz bazę danych**

Użycie bazy danych przeglądania kodu (SDF), wszystkie inne opcje przeglądania/nawigacji oraz wszystkie funkcje IntelliSense z wyjątkiem #include autouzupełniania są wyłączone.

**Wyłącz aktualizacje bazy danych**

Baza danych zostanie otwarta tylko do odczytu, a żadne aktualizacje nie będą wykonywane, gdy pliki są edytowane. Większość funkcji będzie nadal działała. Jednak po wprowadzeniu zmian dane staną się nieaktualne i otrzymasz nieprawidłowe wyniki.

**Wyłącz autoaktualizacje bazy danych**

Baza danych przeglądania kodu nie zostanie automatycznie zaktualizowana, gdy pliki źródłowe zostaną zmodyfikowane. Jeśli jednak otworzysz **Eksplorator rozwiązań**, otwórz menu skrótów dla projektu, a następnie wybierz polecenie **Skanuj ponownie rozwiązanie**, wszystkie nieaktualne pliki zostaną zaznaczone, a baza danych zostanie zaktualizowana.

**Wyłącz niejawne pliki**

Baza danych przeglądania kodu nie zbiera danych dla plików, które nie są określone w projekcie. Projekt zawiera pliki źródłowe i pliki nagłówkowe, które są jawnie określone. Pliki niejawne są zawarte w jawnych plikach (na przykład afxwin. h, Windows. h i atlbase. h). Zwykle system znajduje te pliki, a także indeksuje je pod kątem różnych funkcji przeglądania (w tym do przejścia do). W przypadku wybrania tej opcji te pliki nie są indeksowane, a niektóre funkcje nie są dla nich dostępne. W przypadku wybrania tej opcji "Wyłącz niejawne czyszczenie" i "Wyłącz zależności zewnętrzne" również są wybierane niejawnie.

**Wyłącz niejawne czyszczenie**

Baza danych przeglądania kodu nie czyści niejawnych plików, które nie są już przywoływane. Ta opcja uniemożliwia usuwanie niejawnych plików z bazy danych, gdy nie są one już używane. Na przykład, jeśli dodasz `#include` dyrektywę, która odwołuje się do interfejsu MAPI. h do jednego z plików źródłowych, zostanie znaleziony i zindeksowany MAPI. h. Jeśli następnie usuniesz #include i plik nie jest przywoływany w innym miejscu, informacje na jego temat zostaną ostatecznie usunięte, chyba że wybierzesz tę opcję. (Zobacz opcja **interwału ponownego skanowania** ). Ta opcja jest ignorowana, gdy użytkownik jawnie skanuje ponownie rozwiązanie.

**Wyłącz foldery zależności zewnętrznych**

Folder zależności zewnętrznych dla każdego projektu nie został utworzony ani zaktualizowany. W **Eksplorator rozwiązań** każdy projekt zawiera folder zależności zewnętrznych, który zawiera wszystkie niejawne pliki dla tego projektu. Jeśli wybierzesz tę opcję, ten folder nie zostanie wyświetlony.

**Utwórz ponownie bazę danych**

Utwórz ponownie bazę danych przeglądania kodu od momentu następnego ładowania rozwiązania. W przypadku wybrania tej opcji plik bazy danych SDF zostanie usunięty podczas następnego ładowania rozwiązania, co spowoduje ponowne utworzenie bazy danych i wszystkie pliki indeksowane.

**Przeskanuj ponownie interwał rozwiązania**

Zaplanowano zadanie "Skanuj ponownie rozwiązanie teraz" dla określonego interwału. Należy określić wartość z zakresu od 0 do 5000 minut. Wartość domyślna to 60 minut. Gdy rozwiązanie jest ponownie skanowane, sygnatury czasowe plików są sprawdzane w celu określenia, czy plik został zmieniony poza IDE. (Zmiany wprowadzone w środowisku IDE są automatycznie śledzone i pliki są aktualizowane). Niejawnie dołączone pliki są sprawdzane w celu ustalenia, czy są one nadal przywoływane.

## <a name="diagnostic-logging"></a>Rejestrowanie diagnostyczne

Te opcje są dostępne w przypadku, gdy firma Microsoft prosi o zebranie zaawansowanych informacji w celu zdiagnozowania problemu. Informacje o rejestrowaniu nie są przydatne dla użytkowników i zalecamy pozostawienie wyłączone.

**Włącz rejestrowanie**

Włącza rejestrowanie diagnostyczne do okna danych wyjściowych.

**Poziom rejestrowania**

Ustaw poziom szczegółowości dziennika, od 0 do 5.

**Filtr rejestrowania**

Filtruje wyświetlane typy zdarzeń przy użyciu maski bitowej.

Ustaw przy użyciu sumy spośród następujących opcji:

- 0 — brak

- 1 — ogólne

- 2 — bezczynne

- 4 — element roboczy

- 8 — IntelliSense

- 16 — ACPerf

- 32 – ClassView

## <a name="fallback-location"></a>Lokalizacja rezerwowa

Lokalizacja rezerwowa to miejsce, w którym pliki obsługi SDF i IntelliSense (na przykład iPCH) są umieszczane, gdy lokalizacja podstawowa (w tym samym katalogu jako rozwiązanie) nie jest używana. Taka sytuacja może wystąpić, jeśli użytkownik nie ma uprawnień do zapisu w katalogu rozwiązania lub katalog rozwiązania znajduje się na wolnym urządzeniu. Domyślna lokalizacja rezerwowa znajduje się w katalogu Temp użytkownika.

**Zawsze używaj lokalizacji rezerwowej**

Wskazuje, że pliki bazy danych przeglądania kodu i IntelliSense powinny być zawsze przechowywane w folderze określonym jako "Lokalizacja rezerwowa", a nie obok pliku. sln. IDE nigdy nie podejmie próby umieszczenia plików SDF lub iPCH obok katalogu rozwiązania i zawsze będzie używać lokalizacji rezerwowej.

**Nie Ostrzegaj, jeśli użyto lokalizacji rezerwowej**

Jeśli zostanie użyta opcja "Lokalizacja rezerwowa", nie masz informacji o tym, czy zostanie wyświetlony monit. Zwykle IDE będzie informować o tym, czy musiał używać lokalizacji rezerwowej. Ta opcja powoduje wyłączenie tego ostrzeżenia.

**Lokalizacja rezerwowa**

Ta wartość jest używana jako lokalizacja dodatkowa do przechowywania bazy danych przeglądania kodu lub plików IntelliSense. Domyślnie katalog tymczasowy jest lokalizacją rezerwową. IDE utworzy podkatalog w określonej ścieżce (lub katalogu Temp), który zawiera nazwę rozwiązania wraz z skrótem pełnej ścieżki do rozwiązania, co pozwala uniknąć problemów z identycznymi nazwami rozwiązań.

## <a name="intellisense"></a>IntelliSense

**Autoszybkie informacje**

Włącza etykietki narzędzi sekcji szybkich informacji po przesunięciu wskaźnika nad tekstem.

**Wyłącz funkcję IntelliSense**

Wyłącza wszystkie funkcje IntelliSense. IDE nie tworzy procesów VCPkgSrv.exe do obsługi żądań IntelliSense, a żadne funkcje IntelliSense nie będą działały (sekcji szybkich informacji, lista elementów członkowskich, funkcja autouzupełniania, Pomoc dotycząca parametrów). Kolorowanie semantyczne i wyróżnianie odwołań również jest wyłączone. Ta opcja nie powoduje wyłączenia funkcji przeglądania, które są zależne wyłącznie od bazy danych (w tym pasek nawigacyjny, ClassView i okno właściwości).

**Wyłącz autoaktualizowanie**

Aktualizacja IntelliSense jest opóźniona, dopóki nie zostanie wykonane rzeczywiste żądanie dotyczące technologii IntelliSense. To opóźnienie może skutkować dłuższym czasem wykonywania pierwszej operacji IntelliSense na pliku, ale może być przydatne, aby ustawić tę opcję na maszynach o bardzo niskiej lub ograniczonej ilości zasobów. W przypadku wybrania tej opcji można również niejawnie wybrać opcje "Wyłącz raportowanie błędów" i "Wyłącz zawijania".

**Wyłącz raportowanie błędów**

Wyłącza raportowanie błędów funkcji IntelliSense przez zygzaki i okno Lista błędów. Wyłącza również analizę w tle, która jest skojarzona z raportowaniem błędów. W przypadku wybrania tej opcji można również niejawnie wybrać opcję "Wyłącz Zawijanie".

**Wyłącz zygzaki**

Wyłącza opcję zygzaków błędów funkcji IntelliSense. Czerwony "zygzaks" nie jest wyświetlany w oknie edytora, ale błąd nadal pojawia się w oknie Lista błędów.

**Autodopasowanie Max Cached translation Units**

Maksymalna liczba jednostek translacji, które będą przechowywane w dowolnym momencie w przypadku żądań IntelliSense. Należy określić wartość z przedziału od 2 do 15. Ta liczba bezpośrednio odnosi się do maksymalnej liczby procesów VCPkgSrv.exe, które będą uruchamiane (dla danego wystąpienia programu Visual Studio). Wartość domyślna to 2, ale jeśli masz dostępną pamięć, możesz zwiększyć tę wartość i zapewnić nieco lepszą wydajność funkcji IntelliSense.

Aby uzyskać więcej informacji na temat jednostek translacji, zobacz [etapy tłumaczenia](/cpp/preprocessor/phases-of-translation).

**Wyłącz funkcję Autowypełniania #include**

Wyłącza Autouzupełnianie `#include` instrukcji.

**Użyj ukośnika do przodu w #include Autouzupełnianie**

Wyzwala Autouzupełnianie `#include` instrukcji, gdy jest używana wartość "/". Domyślny ogranicznik to ukośnik odwrotny \' . Kompilator może zaakceptować jedną z tych opcji, aby określić, do czego służy kod podstawowy.

**Wyłącz agresywną listę elementów członkowskich**

Lista elementów członkowskich nie jest wyświetlana podczas wpisywania nazwy typu lub zmiennej. Lista zostanie wyświetlona tylko po wpisaniu jednego z znaków zatwierdzenia, jak zdefiniowano w opcji **zatwierdzanie znaków listy składowych** .

**Wyłącz słowa kluczowe list elementów członkowskich**

Słowa kluczowe języka, takie jak `void` , `class` , `switch` nie są wyświetlane na listach elementów członkowskich.

**Wyłącz fragmenty kodu list składowych**

Fragmenty kodu nie są wyświetlane na listach elementów członkowskich.

**Tryb filtru listy elementów członkowskich**

Ustawia typ zgodnego algorytmu. **Rozmyte** Znajdowanie najbardziej możliwych dopasowań, ponieważ używa algorytmu podobnego do sprawdzania pisowni, aby znaleźć dopasowania, które są podobne, ale nie identyczne. **Inteligentne filtrowanie** dopasowuje podciągi, nawet jeśli nie znajdują się na początku wyrazu. **Prefiks** tylko pasuje do identycznych podciągów, które zaczynają się na początku wyrazu.

**Wyłącz kolorowanie semantyczne**

Wyłącza wszystkie kolorowanie kodu z wyjątkiem słów kluczowych, ciągów i komentarzy języka.

**Znaki zatwierdzania listy składowych**

Określa znaki, które powodują zatwierdzenie listy aktualnie wyróżnionych elementów członkowskich. Możesz dodawać lub usuwać znaki z tej listy.

**Zatwierdzenie listy elementów członkowskich Smart**

Dodaje wiersz po wybraniu klawisza Enter na końcu w pełni wpisanego wyrazu.

**Włącz listę elementów członkowskich z kropką na strzałkę**

Zastępuje znak "." elementem "->", jeśli jest to możliwe dla listy elementów członkowskich.

## <a name="references"></a>Odwołania

**Wyłącz Rozwiązywanie**

Ze względu na wydajność polecenie "Znajdź wszystkie odwołania" domyślnie wyświetla nieprzetworzone wyniki wyszukiwania tekstu, a nie za pomocą technologii IntelliSense, aby zweryfikować każdy kandydat. Możesz wyczyścić to pole wyboru, aby uzyskać dokładniejsze wyniki dla wszystkich operacji znajdowania. Aby odfiltrować według przeszukiwania, otwórz menu skrótów dla listy wyników, a następnie wybierz polecenie "Rozwiąż wyniki".

**Ukryj niepotwierdzone**

Ukryj niepotwierdzone elementy w wynikach "Znajdź wszystkie odwołania". W przypadku ustawienia opcji "Wyłącz rozpoznawanie" można użyć tej opcji do ukrycia niepotwierdzonych elementów w wynikach.

**Wyłącz podświetlanie odwołań**

Domyślnie po zaznaczeniu tekstu wszystkie wystąpienia tego samego tekstu są automatycznie wyróżniane w bieżącym dokumencie. Tę funkcję można wyłączyć, ustawiając **opcję Wyłącz podświetlanie odwołań** na **wartość true**.

## <a name="text-editor"></a>Edytor tekstu

**Włącz opcję Otocz za pomocą nawiasów klamrowych**

Jeśli ta funkcja jest włączona, można ująć zaznaczony tekst za pomocą nawiasów klamrowych, wpisując "{" w edytorze tekstu.

**Włącz funkcję Otocz za pomocą nawiasów**

Jeśli ta funkcja jest włączona, można ująć zaznaczony tekst za pomocą nawiasów, wpisując znak "(" w edytorze tekstu.

## <a name="see-also"></a>Zobacz też

- [Ustawianie opcji Edytora specyficznych dla języka](../../ide/reference/setting-language-specific-editor-options.md)
