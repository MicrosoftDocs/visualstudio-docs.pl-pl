---
title: Options, Text Editor, C-C++, Advanced | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.C\C++.Advanced
- VS.ToolsOptionsPages.Text_Editor.C%2FC%2B%2B.Advanced
- VS.ToolsOptionsPages.Text_Editor.C/C++.Advanced
helpviewer_keywords:
- Text Editor Options dialog box, advanced
ms.assetid: 67c82ae5-fddd-49df-baec-8e7498b156f3
caps.latest.revision: 23
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 8c734e6bd41e91ba208a13e36c06f04111cac5ba
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54790100"
---
# <a name="options-text-editor-cc-advanced"></a>Opcje, edytor tekstu, C/C++, zaawansowane
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

  
Zmieniając tych opcji, możesz zmienić zachowanie związane z technologii IntelliSense i bazy danych przeglądania w przypadku programowania w języku C lub C++.  
  
 Dostępu do tej strony, w **opcje** rozwiń w lewym okienku w oknie dialogowym **edytora tekstów**, rozwiń węzeł **C/C++**, a następnie wybierz **zaawansowane**.  
  
> [!NOTE]
>  Na komputerze w poniższych instrukcjach mogą być wyświetlane inne nazwy i lokalizacje niektórych elementów interfejsu użytkownika programu Visual Studio. Te elementy są określane przez numer wersji Visual Studio oraz twoje ustawienia. Zobacz [Dostosowywanie ustawień środowiska deweloperskiego w programie Visual Studio](http://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
## <a name="browsingnavigation"></a>Przeglądanie nawigacji  
 Nigdy nie należy wybrać te opcje, z wyjątkiem w rzadkich przypadkach, gdy rozwiązanie jest tak duża, że działanie bazy danych wykorzystuje niedopuszczalne ilość zasobów systemowych.  
  
 **Wyłączanie bazy danych**  
 Wszystkie przypadki użycia przeglądania bazy danych (SDF), wszystkie inne opcje przeglądania/nawigacji i wszystkie funkcje IntelliSense, z wyjątkiem kodu # Autouzupełnianie include są wyłączone.  
  
 **Wyłącz aktualizacje bazy danych**  
 Baza danych zostanie otwarty tylko do odczytu, a będzie można wykonać żadnych aktualizacji, ponieważ edytowania plików. Większość funkcji będzie nadal działać. Jednak ponieważ zmiany zostaną wprowadzone, dane staną się nieaktualne i niepoprawne wyniki.  
  
 **Wyłącz automatyczne aktualizacje bazy danych**  
 Baza danych przeglądania kodu nie będzie aktualizowana automatycznie, gdy pliki źródłowe zostaną zmodyfikowane. Jednak jeśli otworzysz **Eksploratora rozwiązań**, otwórz menu skrótów dla projektu, a następnie wybierz **Skanuj ponownie rozwiązanie**, wszystkie nieaktualne pliki będą sprawdzane i bazy danych zostaną zaktualizowane.  
  
 **Wyłącz niejawne pliki**  
 Baza danych przeglądania kodu nie zbiera danych z plików, które nie są określone w projekcie. Projekt zawiera pliki źródłowe i pliki nagłówkowe, które są jawnie określone. Niejawne pliki dołączane przez jawne plików (na przykład afxwin.h windows.h i atlbase.h). Normalnie system znajdzie te pliki i również indeksuje je dla różnych funkcji przeglądania (w tym przejdź do). Jeśli ta opcja jest wybrana, pliki te nie są indeksowane, a niektóre funkcje nie są dostępne dla nich. Jeśli ta opcja "Wyłącz niejawne czyszczenie" i "Wyłącz zewnętrzne zależności" również niejawnie są wybierane.  
  
 **Wyłącz niejawne czyszczenie**  
 Baza danych przeglądania kodu nie wyczyścić Konfigurowanie niejawnych plików, które nie są już używane. Tej opcji uniemożliwia niejawne pliki usuwany z bazy danych, gdy są one już używane. Na przykład jeśli dodasz `#include` dyrektywy, który odwołuje się mapi.h do jednego z plików źródłowych, mapi.h zostanie znalezione i indeksowane. Jeśli następnie usuniesz #include i pliku nie jest odwoływać się gdzie indziej, informacje o nim zostaną usunięte po pewnym czasie, chyba że wybierzesz tę opcję. (Zobacz **interwał ponownego skanowania rozwiązania** opcję.) Ta opcja jest ignorowana, gdy jawnie Skanuj ponownie rozwiązanie.  
  
 **Wyłącz foldery zależności zewnętrznych**  
 Folder zewnętrznych zależności, dla każdego projektu nie jest tworzony lub aktualizowany. W **Eksploratora rozwiązań**, każdy projekt zawiera folder zewnętrznych zależności, który zawiera wszystkie niejawne pliki dla tego projektu. Jeśli ta opcja jest wybrana, nie jest wyświetlany ten folder.  
  
 **Ponowne utworzenie bazy danych**  
 Utwórz ponownie przeglądania przy następnym uruchomieniu ładuje rozwiązanie bazy danych skalują się od kodu. Jeśli ta opcja jest wybrana, plik bazy danych SDF zostanie usunięty podczas następnego ładowania rozwiązania, powodując w bazie danych do odtworzenia i indeksowane wszystkich plików.  
  
 **Interwał ponownego skanowania rozwiązania**  
 Zadanie "Przeskanuj teraz ponownie rozwiązanie" zaplanowano dla interwału, który określisz. Należy określić zakresu od 0 do 5000 minut. Wartość domyślna to 60 minut. Gdy rozwiązanie jest ponownie skanowana, sygnatury czasowe pliku jest sprawdzany w celu określenia, czy plik został zmieniony poza IDE. (Zmiany wprowadzone w środowisku IDE, są automatycznie śledzone, i pliki są aktualizowane). Niejawnie dołączone pliki są sprawdzane w celu określenia, czy są one wszystkie nadal istnieje odwołanie.  
  
## <a name="diagnostic-logging"></a>Rejestrowanie diagnostyczne  
 Te opcje są dostarczane w przypadku, gdy firma Microsoft prosi o zaawansowanych informacji w celu zdiagnozowania problemu. Rejestrowanie informacji nie jest przydatne w przypadku użytkowników, a firma Microsoft zaleca, aby pozostawić ją wyłączoną.  
  
 **Włączanie rejestrowania**  
 Umożliwia rejestrowanie diagnostyczne w oknie danych wyjściowych.  
  
 **Poziom rejestrowania**  
 Ustaw poziom szczegółowości dziennika, od 0 do 5.  
  
 **Filtr rejestrowania**  
 Filtry wyświetlane typy zdarzeń za pomocą maski bitów.  
  
 Ustaw za pomocą Suma dowolnych z następujących opcji:  
  
-   0 - Brak  
  
-   1 — Ogólne  
  
-   2 - bezczynności (%)  
  
-   4 — elementów roboczych  
  
-   8 - IntelliSense  
  
-   16 - ACPerf  
  
-   32 - ClassView  
  
## <a name="fallback-location"></a>Lokalizacja rezerwowa  
 Lokalizacji rezerwowej to, gdzie umieścić pliki obsługi SDF i funkcja IntelliSense (na przykład iPCH), gdy nie jest używana w lokalizacji głównej (tego samego katalogu jako rozwiązanie). Taka sytuacja może wystąpić, użytkownik nie ma uprawnień do zapisu do katalogu rozwiązania lub katalog rozwiązania jest powolne urządzenia. Domyślną lokalizację rezerwową znajduje się w katalogu temp użytkownika.  
  
 **Zawsze używaj lokalizacji rezerwowej**  
 Wskazuje, że kod bazy danych plików przeglądania i IntelliSense zawsze powinny być przechowywane w folderze wskazanym jako swojej "Lokalizacja rezerwowa", nie razem z plikiem .sln. IDE nigdy nie próbuje umieścić pliki SDF lub iPCH obok katalogu rozwiązania i będzie zawsze używać rezerwowej lokalizacji.  
  
 **Nie ostrzegaj o wykorzystaniu lokalizacji rezerwowej**  
 Nie ma informacji lub zostanie wyświetlony monit, jeśli jest używany "Lokalizacja rezerwowa". Normalnie IDE poinformuje, jeśli znajdował się na użycie rezerwowej lokalizacji. Ta opcja powoduje wyłączenie tego ostrzeżenia.  
  
 **Lokalizacja rezerwowa**  
 Ta wartość służy jako lokalizacja pomocnicza do przechowywania kodu, przeglądanie bazy danych lub pliki IntelliSense. Domyślnie katalog tymczasowy jest swojej lokalizacji rezerwowej. Spowoduje to utworzenie środowiska IDE podkatalogu w określonej ścieżki (lub katalogu temp), która zawiera nazwę rozwiązania oraz skrót pełnej ścieżki do rozwiązania, co pozwala uniknąć problemów z nazwy rozwiązania, które są identyczne.  
  
## <a name="intellisense"></a>IntelliSense  
 **Auto Quick Info**  
 Pozwala etykietek narzędzi Szybkieinfo, gdy przesuniesz wskaźnik myszy nad tekstem.  
  
 **Wyłącz IntelliSense**  
 Wyłącza wszystkie funkcje IntelliSense. IDE nie powoduje utworzenia VCPkgSrv.exe procesów do obsługi technologii IntelliSense żądań i żadne funkcje IntelliSense będzie działać (skrócone informacje, lista członków Autouzupełnianie, Param pomocy). Kolorowanie semantyczne i wyróżnianie odwołań są również wyłączone. Opcja ta nie wyłączenie funkcji przeglądania, które polegać wyłącznie na bazie danych (w tym oknie paska nawigacyjnego, ClassView i właściwości).  
  
 **Wyłącz automatyczne aktualizowanie**  
 Aktualizowanie IntelliSense jest opóźnione, dopóki rzeczywistego żądania dla technologii IntelliSense. To opóźnienie może spowodować dłuższy czas wykonania pierwszej operacji IntelliSense dla pliku, ale może być pomocne ustawić tę opcję na maszynach bardzo wolno lub ograniczonych zasobach. Jeśli ta opcja jest wybrana, dodatkowo niejawnie należy wybierać opcje "Wyłącz Error Reporting" i "Wyłącz zygzaki".  
  
 **Wyłączyć raportowanie błędów**  
 Wyłącza raportowanie błędów IntelliSense przez zygzaki i okno Lista błędów. Dodatkowo wyłącza analizowanie w tle skojarzone z raportowania błędów. Jeśli ta opcja jest wybrana, dodatkowo niejawnie należy wybrać opcję "Wyłącz zygzaki".  
  
 **Wyłącz zygzaki**  
 Wyłącza zygzaki sygnalizujące błędy IntelliSense. Czerwone "zygzaki" nie pokazuj w oknie edytora, ale błąd będzie nadal występować w oknie Lista błędów.  
  
 **Wyłącz # Autouzupełnianie include**  
 Wyłącza automatyczne uzupełnianie `#include` instrukcji.  
  
 **Użyj ukośnik w # Autouzupełnianie include**  
 Wyzwala automatyczne uzupełnianie `#include` instrukcji po "/" jest używany. Domyślnym ogranicznikiem jest odwrotny "\". Kompilator można zaakceptować albo, więc ta opcja umożliwia określenie używa bazy kodu.  
  
 **Maksymalna liczba buforowanych jednostek tłumaczenia**  
 Maksymalna liczba jednostek tłumaczenia, które będą znajdować się aktywne w dowolnym momencie dla żądań IntelliSense. Należy określić wartość z przedziału od 2 do 15. Ten numer bezpośrednio związana z oczekiwaną maksymalną liczbę procesów VCPkgSrv.exe, które będą uruchamiane (dla danego wystąpienia programu Visual Studio). Wartość domyślna to 2, ale jeśli masz dostępnej pamięci, można zwiększyć tę wartość i prawdopodobnie osiągnąć nieco większą wydajność w technologii IntelliSense.  
  
 Aby uzyskać więcej informacji na temat jednostek tłumaczenia, zobacz [etapy translacji](http://msdn.microsoft.com/library/a7f7a8c9-e8ba-4321-9e50-ebfbbdcce9db).  
  
 **Wyłącz agresywne listy**  
 Listę elementów członkowskich nie jest wyświetlany podczas wpisywania nazwy typu lub zmiennej. Lista jest wyświetlana tylko wtedy, gdy możesz wpisać znaki zatwierdzające zgodnie z definicją w **znaki zatwierdzania List składowych** opcji.  
  
 **Wyłącz słowa kluczowe List elementu członkowskiego**  
 Słowa kluczowe języka, takich jak `void`, `class`, `switch` nie pojawiają się w elementu członkowskiego listy sugestii.  
  
 **Wyłącz fragmenty kodu List składowych**  
 Fragmenty kodu nie są wyświetlane w elementu członkowskiego listy sugestii.  
  
 **Wyłącz kolorowanie semantyczne**  
 Wyłącza wszystkie kolorowania kodu, z wyjątkiem słów kluczowych języka, ciągi i komentarze.  
  
 **Zatwierdzanie List składowych inteligentne**  
 Dodaje wiersz po wybraniu klawisza Enter na końcu pełnego wpisanego wyrazu.  
  
 **Tryb filtrowania listy składowych**  
 Ustawia typ algorytm dopasowania. **Rozmyte** znajduje najbardziej możliwe jest zgodny, ponieważ używa ona algorytm, który jest podobny do sprawdzania pisowni, aby znaleźć dopasowania, które są podobne, ale nie są identyczne. **Inteligentne filtrowanie** odpowiada podciągów, nawet jeśli nie są one na początku wyrazu. **Prefiks** jest zgodny tylko na podciągi identyczne, rozpoczynające się od słowa.  
  
 **Znaki zatwierdzania List składowych**  
 Określa znaki, które powodują obecnie podświetlony sugestii listę elementów członkowskich do zatwierdzenia. Można dodać lub usunąć znaki z tej listy.  
  
## <a name="references"></a>Odwołania  
 **Wyłącz Rozwiązywanie**  
 Ze względu na wydajność "Znajdź wszystkie odwołania" wyświetli nieprzetworzone wyniki wyszukiwania tekstowego domyślnie zamiast wykorzystania IntelliSense do weryfikacji każdej możliwości. Można wyczyść to pole wyboru dla bardziej precyzyjne wyniki na wszystkich operacji wyszukiwania. Aby filtrować na podstawie na wyszukiwanie, otwórz menu skrótów dla listy wyników, a następnie wybierz "Resolve wyniki".  
  
 **Ukryj niepotwierdzone**  
 Ukryj niepotwierdzone elementów w wynikach "Znajdź wszystkie odwołania". Jeśli nie ustawiono "Wyłącz rozwiązywanie" opcji, należy umożliwia tę opcję, ukrywanie niepotwierdzone elementów w wynikach.  
  
 **Wyłącz podświetlanie odwołań**  
  
## <a name="see-also"></a>Zobacz też  
 [Ustawianie opcji edytora specyficznych dla języka](../../ide/reference/setting-language-specific-editor-options.md)
