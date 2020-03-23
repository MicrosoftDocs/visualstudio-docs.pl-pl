---
title: Opcje, edytor tekstu, C/C++, zaawansowane
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
ms.openlocfilehash: 2e7e031836c9762d9666a5624e78ecc7c8cc7dd9
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "77275201"
---
# <a name="options-text-editor-cc-advanced"></a>Opcje, edytor tekstu, C/C++, zaawansowane

Zmieniając te opcje, można zmienić zachowanie związane z IntelliSense i przeglądania bazy danych podczas programowania w języku C lub C++.

Aby uzyskać dostęp do tej strony, w oknie dialogowym **Opcje** w lewym okienku rozwiń rozwiń pozycję **Edytor tekstu**, rozwiń węzeł **C/C++,** a następnie wybierz pozycję **Zaawansowane**.

> [!NOTE]
> Na komputerze w poniższych instrukcjach mogą być wyświetlane inne nazwy i lokalizacje niektórych elementów interfejsu użytkownika programu Visual Studio. Te elementy są określane przez numer wersji Visual Studio oraz twoje ustawienia. Zobacz [Personalizuj IDE programu Visual Studio](../../ide/personalizing-the-visual-studio-ide.md).

## <a name="browsingnavigation"></a>Przeglądanie/Nawigacja

Nigdy nie należy wybierać tych opcji, z wyjątkiem rzadkich przypadków, gdy rozwiązanie jest tak duże, że działanie bazy danych zużywa niedopuszczalną ilość zasobów systemowych.

**Wyłącz bazę danych**

Wszystkie korzystanie z bazy danych przeglądania kodu (SDF), wszystkie inne opcje przeglądania/nawigacji oraz wszystkie funkcje IntelliSense z wyjątkiem #include Auto Complete są wyłączone.

**Wyłączanie aktualizacji bazy danych**

Baza danych zostanie otwarta tylko do odczytu i żadne aktualizacje nie będą wykonywane podczas edytowania plików. Większość funkcji będzie nadal działać. Jednak w miarę wprowadzania zmian dane staną się przestarzałe, a otrzymasz nieprawidłowe wyniki.

**Wyłącz automatyczne aktualizacje bazy danych**

Baza danych przeglądania kodu nie zostanie automatycznie zaktualizowana po zmodyfikowaniu plików źródłowych. Jeśli jednak otworzysz **Eksploratora rozwiązań,** otwórz menu skrótów dla projektu, a następnie wybierz pozycję **Rescan Solution**, wszystkie nieaktualne pliki zostaną sprawdzone, a baza danych zostanie zaktualizowana.

**Wyłączanie plików niejawnych**

Baza danych przeglądania kodu nie zbiera danych dla plików, które nie są określone w projekcie. Projekt zawiera pliki źródłowe i pliki nagłówkowe, które są jawnie określone. Pliki niejawne są uwzględniane przez jawne pliki (na przykład afxwin.h, windows.h i atlbase.h). Zwykle system znajduje te pliki, a także indeksuje je dla różnych funkcji przeglądania (w tym Przejdź do). Jeśli wybierzesz tę opcję, te pliki nie są indeksowane, a niektóre funkcje nie są dla nich dostępne. Jeśli wybierzesz tę opcję, "Wyłącz oczyszczanie niejawne" i "Wyłącz zależności zewnętrzne" są również niejawnie wybrane.

**Wyłącz oczyszczanie niejawne**

Baza danych przeglądania kodu nie czyści niejawnych plików, do których nie ma już przywoływania. Ta opcja zapobiega niejawne pliki są usuwane z bazy danych, gdy nie są już używane. Na przykład jeśli dodasz dyrektywę, `#include` która odwołuje się do mapi.h do jednego z plików źródłowych, mapi.h zostanie znaleziony i zindeksowany. Jeśli następnie usuniesz #include, a plik nie będzie się odwoływał gdzie indziej, informacje o nim zostaną ostatecznie usunięte, chyba że wybierzesz tę opcję. (Zobacz opcję **Interwał ponownego sskanowania rozwiązania).** Ta opcja jest ignorowana podczas jawnego ponownego wyskanowania rozwiązania.

**Wyłączanie folderów zależności zewnętrznych**

Folder Zależności zewnętrzne dla każdego projektu nie jest tworzony ani aktualizowany. W **Eksploratorze rozwiązań**każdy projekt zawiera folder Zależności zewnętrznych, który zawiera wszystkie niejawne pliki dla tego projektu. Jeśli wybierzesz tę opcję, ten folder nie będzie wyświetlany.

**Odtworzenie bazy danych**

Ponownie utworzyć bazę danych przeglądania kodu z niczego następnym razem, gdy rozwiązanie jest ładowane. Jeśli wybierzesz tę opcję, plik bazy danych SDF zostanie usunięty przy następnym załadowaniu rozwiązania, co spowoduje odtworzenie bazy danych i zindeksowanie wszystkich plików.

**Interwał ponownego sskanowania rozwiązania**

Zadanie "Przeskanuj rozwiązanie teraz" jest zaplanowane dla określonego interwału. Należy określić od 0 do 5000 minut. Wartość domyślna to 60 minut. Podczas ponownego skanowania rozwiązania sygnatury czasowe pliku są sprawdzane w celu ustalenia, czy plik został zmieniony poza IDE. (Zmiany wprowadzone w IDE są automatycznie śledzone, a pliki są aktualizowane). Niejawnie dołączone pliki są sprawdzane, aby ustalić, czy wszystkie są nadal odwołuje.

## <a name="diagnostic-logging"></a>Rejestrowanie diagnostyczne

Te opcje są dostępne w przypadku, gdy firma Microsoft poprosi o zebranie zaawansowanych informacji w celu zdiagnozowania problemu. Informacje o rejestrowaniu nie są przydatne dla użytkowników i zaleca się pozostawienie ich wyłączonych.

**Włącz rejestrowanie**

Umożliwia rejestrowanie diagnostyczne do okna wyjściowego.

**Poziom rejestrowania**

Ustaw szczegółowość dziennika, od 0 do 5.

**Filtr rejestrowania**

Filtry wyświetlały typy zdarzeń przy użyciu maski bitowej.

Ustaw przy użyciu sumy dowolnej z następujących opcji:

- 0 - Brak

- 1 - Ogólne

- 2 - Bezczynny

- 4 - WorkItem

- 8 - IntelliSense

- 16 - ACPerf

- 32 - Widok na klasę

## <a name="fallback-location"></a>Lokalizacja rezerwy

Lokalizacja rezerwowa to miejsce, w którym pliki obsługi SDF i IntelliSense (na przykład iPCH) są umieszczane, gdy lokalizacja podstawowa (ten sam katalog jako rozwiązanie) nie jest używana. W takiej sytuacji może wystąpić użytkownik nie ma uprawnień do zapisu w katalogu rozwiązania lub katalog rozwiązania znajduje się na wolnym urządzeniu. Domyślna lokalizacja rezerwowa znajduje się w katalogu tymczasowym użytkownika.

**Zawsze używaj lokalizacji rezerwowej**

Wskazuje, że baza danych przeglądania kodu i pliki IntelliSense powinny być zawsze przechowywane w folderze określonym jako "Lokalizacja rezerwowa", a nie obok pliku .sln. IDE nigdy nie spróbuje umieścić pliki SDF lub iPCH obok katalogu rozwiązania i zawsze będzie używać lokalizacji rezerwowej.

**Nie ostrzegaj, jeśli używana jest lokalizacja rezerwa**

Nie zostaniesz poinformowany ani monitowany, jeśli używana jest "Lokalizacja rezerwowa". Zwykle IDE powie, czy trzeba było użyć lokalizacji rezerwowej. Ta opcja wyłącza to ostrzeżenie.

**Lokalizacja rezerwy**

Ta wartość jest używana jako lokalizacja pomocnicza do przechowywania bazy danych przeglądania kodu lub plików IntelliSense. Domyślnie katalog tymczasowy jest lokalizacją rezerwową. IDE utworzy podkatalog w ramach określonej ścieżki (lub katalogu tymczasowego), który zawiera nazwę rozwiązania wraz z skrótem pełnej ścieżki do rozwiązania, co pozwala uniknąć problemów z nazwami rozwiązań są identyczne.

## <a name="intellisense"></a>IntelliSense

**Automatyczne szybkie informacje**

Włącza etykietki narzędzi QuickInfo podczas przesuwania wskaźnika nad tekstem.

**Wyłącz intellisense**

Wyłącza wszystkie funkcje IntelliSense. IDE nie tworzy procesów VCPkgSrv.exe do obsługi żądań IntelliSense i żadne funkcje IntelliSense nie będą działać (QuickInfo, Member List, Auto Complete, Param Help). Koloryzacja semantyczna i wyróżnianie odniesienia są również wyłączone. Ta opcja nie wyłącza funkcji przeglądania, które opierają się wyłącznie na bazie danych (w tym na pasku nawigacyjnym, classview i oknie właściwości).

**Wyłącz automatyczne aktualizowanie**

Aktualizacja IntelliSense jest opóźniona do momentu złożenia rzeczywistego żądania intellisense. To opóźnienie może spowodować dłuższy czas wykonywania pierwszej operacji IntelliSense w pliku, ale może być przydatne ustawienie tej opcji na komputerach bardzo wolno lub z ograniczonymi zasobami. Jeśli wybierzesz tę opcję, możesz również niejawnie wybrać opcje "Wyłącz raportowanie błędów" i "Wyłącz squiggles".

**Wyłącz raportowanie błędów**

Wyłącza raportowanie błędów IntelliSense za pomocą squiggles i okna lista błędów. Wyłącza również analizowanie w tle, które jest skojarzone z raportowaniem błędów. Jeśli wybierzesz tę opcję, możesz również niejawnie wybrać opcję "Wyłącz squiggles".

**Wyłącz squiggles**

Wyłącza błędy IntelliSense squiggles. Czerwone "squiggles" nie są wyświetlane w oknie edytora, ale błąd nadal pojawi się w oknie Lista błędów.

**Automatyczne dostrajanie maksymalnych buforowanych jednostek tłumaczeniowych**

Maksymalna liczba jednostek tłumaczeniowych, które będą aktywne w dowolnym momencie dla żądań IntelliSense. Należy określić wartość z 2 do 15. Liczba ta bezpośrednio odnosi się do maksymalnej liczby procesów VCPkgSrv.exe, które zostaną uruchomione (dla danego wystąpienia programu Visual Studio). Wartość domyślna to 2, ale jeśli masz dostępną pamięć, możesz zwiększyć tę wartość i ewentualnie osiągnąć nieco lepszą wydajność na IntelliSense.

Aby uzyskać więcej informacji na temat jednostek tłumaczeniowych, zobacz [Fazy tłumaczenia](/cpp/preprocessor/phases-of-translation).

**Wyłącz #include autouzupełnianie**

Wyłącza automatyczne uzupełnianie `#include` instrukcji.

**Użyj ukośnika do przodu w #include Autouzupełnianie**

Wyzwala automatyczne uzupełnianie `#include` instrukcji, gdy używana jest "/". Domyślnym ogranicznikiem jest\'ukośnik odwrotny . Kompilator może zaakceptować albo, więc użyj tej opcji, aby określić, co używa bazy kodu.

**Wyłącz agresywną listę członków**

Lista członków nie jest wyświetlana podczas wpisywanie nazwy typu lub zmiennej. Lista pojawia się dopiero po wpisaniu jednego ze znaków zatwierdzenia, zgodnie z definicją w opcji **Zatwierdź znaki listy członków.**

**Wyłącz słowa kluczowe listy członków**

Słowa kluczowe języka, `class` `switch` takie jak `void`, nie pojawiają się w sugestiach listy członków.

**Wyłącz fragmenty kodu listy elementów członkowskich**

Fragmenty kodu nie są wyświetlane w sugestiach listy członków.

**Tryb filtru listy członków**

Ustawia typ algorytmu dopasowywania. **Fuzzy** znajduje najbardziej możliwe dopasowania, ponieważ używa algorytmu, który jest podobny do sprawdzania pisowni, aby znaleźć dopasowania, które są podobne, ale nie identyczne. **Inteligentne filtrowanie** dopasowuje podciągi, nawet jeśli nie są one na początku wyrazu. **Prefiks** pasuje tylko do identycznych podciągów, które zaczynają się na początku wyrazu.

**Wyłącz kolorowanie semantyczne**

Wyłącza wszystkie koloryzowanie kodu z wyjątkiem słów kluczowych, ciągów i komentarzy w języku.

**Znaki zatwierdzania listy członków**

Określa znaki, które powodują zatwierdzenie aktualnie wyróżnionej sugestii listy elementów członkowskich. Możesz dodać lub usunąć znaki z tej listy.

**Zatwierdzanie listy inteligentnych członków**

Dodaje wiersz po wybraniu klawisza Enter na końcu w pełni wpisanego wyrazu.

**Włącz listę członków Do-To-Arrow**

Zastępuje "." > w stosownych przypadkach dla listy członków.

## <a name="references"></a>Dokumentacja

**Wyłącz rozwiązywanie problemów**

Ze względu na wydajność "Znajdź wszystkie odwołania" domyślnie wyświetla surowe tekstowe wyniki wyszukiwania zamiast używać intellisense do weryfikacji każdego kandydata. To pole wyboru można wyczyścić, aby uzyskać dokładniejsze wyniki wszystkich operacji znajdowania. Aby filtrować według zasad wyszukiwania, otwórz menu skrótów dla listy wyników, a następnie wybierz opcję "Rozwiąż wyniki".

**Ukryj niepotwierdzone**

Ukryj niepotwierdzone elementy w wynikach "Znajdź wszystkie odwołania". Jeśli wyłączysz opcję "Wyłącz rozwiązywanie", możesz użyć tej opcji, aby ukryć niepotwierdzone elementy w wynikach.

**Wyłącz wyróżnianie odwołań**

Domyślnie po zaznaczeniu tekstu wszystkie wystąpienia tego samego tekstu są automatycznie wyróżniane w bieżącym dokumencie. Tę funkcję można wyłączyć, ustawiając **opcję Wyłącz wyróżnianie odniesienia** na wartość **True**.

## <a name="text-editor"></a>Edytor tekstu

**Włącz funkcję Surround za pomocą nawiasów klamrowych**

Jeśli ta opcja jest włączona, można otoczyć zaznaczony tekst nawiasami klamrowymi, wpisując "{" w edytorze tekstu.

**Włącz funkcję Surround za pomocą nawiasów**

Jeśli ta opcja jest włączona, można otoczyć zaznaczony tekst nawiasami, wpisując w edytorze tekstu "(" w edytorze tekstu.

## <a name="see-also"></a>Zobacz też

- [Ustawianie opcji Edytora specyficznych dla języka](../../ide/reference/setting-language-specific-editor-options.md)
