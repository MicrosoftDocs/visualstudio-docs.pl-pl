---
title: W jaki sposób można zwiększyć szanse na naprawiony problem z wydajnością
description: Dodatkowe informacje i najlepsze rozwiązania dotyczące przesyłania problemów z wydajnością w programie Visual Studio
author: madskristensen
ms.author: madsk
ms.date: 11/19/2019
ms.topic: reference
ms.openlocfilehash: 1a83a9c16e915bde2958193c640c0981f5edc005
ms.sourcegitcommit: 22deb247ad951e4971f27fdab413b158415d0584
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81276458"
---
# <a name="how-to-increase-the-chances-of-a-performance-issue-being-fixed"></a>Jak zwiększyć szanse na naprawiony problem z wydajnością

Narzędzie["Zgłoś problem"](/visualstudio/ide/how-to-report-a-problem-with-visual-studio?view=vs-2019)jest szeroko używane przez użytkowników programu Visual Studio do zgłaszania szeregu problemów. Zespół programu Visual Studio dostrzega trendy awarii i spowolnienia w opiniach użytkowników i rozwiązuje problemy wpływające na szeroki pokos użytkowników. Im bardziej zasysanym jest konkretny bilet na opinię, tym większe prawdopodobieństwo, że zostanie on szybko zdiagnozowany i rozwiązany przez zespół produktu. W tym dokumencie opisano najlepsze rozwiązania podczas zgłaszania problemów z awarią lub spowolnieniem, aby uczynić je bardziej użytecznymi.

## <a name="general-best-practices"></a>Ogólne najlepsze praktyki

Visual Studio to duża, złożona platforma, która obsługuje wiele języków, typów projektów, platform i innych. Jak to działa jest funkcja, która składniki są zainstalowane i aktywne w sesji, rozszerzenia zainstalowane, ustawienia programu Visual Studio, konfiguracja komputera i wreszcie kształt kodu, który jest edytowany. Biorąc pod uwagę liczbę zmiennych, trudno jest stwierdzić, czy raport o problemie od jednego użytkownika ma ten sam podstawowy problem co raport o problemie od innego użytkownika, nawet jeśli widoczny objaw jest taki sam. Biorąc pod uwagę, że, oto kilka najlepszych praktyk, aby upewnić się, że konkretny raport problem ma większe prawdopodobieństwo zdiagnozowania.

**Podaj jak najbardziej konkretny tytuł**

Poszukaj różnych podpisów dla zgłaszanych problemów i uwzględnij w tytule jak najwięcej. Jeśli tytuł jest opisowy, jest mniej prawdopodobne, że użytkownicy z niepowiązanych problemów (ale ten sam powierzchowny objaw) będzie głosować lub komentować bilet, co utrudnia diagnozę *problemu.*

**W razie wątpliwości zarejestruj nowy raport o problemie**

Wiele problemów może nie mieć żadnych charakterystycznych podpisów lub kroków do odtworzenia. W takich przypadkach nowy raport jest lepszy niż głos lub komentarz do innego raportu, który zgłasza podobny *objaw*zewnętrzny . W zależności od typu raportu dołącz dodatkowe pliki diagnostyczne do raportu, zgodnie z opisem w dalszej części tego dokumentu.

**Najlepsze rozwiązania dotyczące problemów**

Opisane poniżej są problemy, które są trudne do zdiagnozowania bez dobrych plików diagnostycznych. Po zidentyfikowaniu sprawy, która najlepiej opisuje problem, wykonaj kroki opinii specyficzne dla tej sprawy.

-   [Awarie:](#crashes) Awaria występuje, gdy proces (Visual Studio) kończy się nieoczekiwanie.

-   [Brak reakcji:](#unresponsiveness) VS przestaje odpowiadać przez dłuższy czas.

-   [Problemy z powolnością:](#slowness-and-high-cpu-issues) Każda określona akcja w vs jest wolniejsza niż pożądana

-   [Wysoki procesor:](#slowness-and-high-cpu-issues) Wydłużone okresy nieoczekiwanie wysokiego zużycia procesora

-   [Problemy poza procesem:](#out-of-process-issues) Problem spowodowany procesem satelitarnym programu Visual Studio

## <a name="crashes"></a>Ulega awarii
Awaria występuje, gdy proces (Visual Studio) kończy się nieoczekiwanie.

**Bezpośrednio powtarzalne awarie**

Bezpośrednio powtarzalne awarie to przypadki, które mają wszystkie następujące cechy:

- Można zaobserwować, wykonując znany zestaw kroków

- Można zaobserwować na wielu komputerach (jeśli są dostępne)

- Może być powielana w przykładowym kodzie lub projekcie, który może być połączony lub dostarczony jako część opinii (jeśli kroki obejmują otwarcie projektu lub dokumentu)

W przypadku tych problemów wykonaj kroki opisane w["Jak zgłosić problem"](/visualstudio/ide/how-to-report-a-problem-with-visual-studio-2017)i pamiętaj o uwzględnienie:

-   Kroki, aby odtworzyć problem

-   Samodzielny projekt repro, jak opisano powyżej. Jeśli samodzielne repro nie jest możliwe, dołącz:

    -   Język otwartych projektów (C,\#C++, itp.)

    -   Rodzaj projektu (aplikacja konsoli, ASP.NET itp.)


> [!NOTE]
> **Najcenniejsze opinie:** W tym przypadku najbardziej cenne opinie jest zestaw kroków do odtworzenia problemu wraz z przykładowego kodu źródłowego.

**Nieznane awarie**

Jeśli nie masz pewności, co jest przyczyną awarii lub wydają się losowe, następnie można przechwycić zrzuty lokalnie za każdym razem, gdy program Visual Studio ulega awarii i dołączyć je do oddzielnych elementów opinii. Aby zapisać zrzuty lokalnie po awarii programu Visual Studio, uruchom następujące polecenia w oknie polecenia administratora:

```
reg add "HKEY_LOCAL_MACHINE\\SOFTWARE\\Microsoft\\Windows\\Windows Error
Reporting\\LocalDumps\\devenv.exe"

reg add "HKEY_LOCAL_MACHINE\\SOFTWARE\\Microsoft\\Windows\\Windows Error
Reporting\\LocalDumps\\devenv.exe" /v DumpType /t REG_DWORD /d 2

reg add "HKEY_LOCAL_MACHINE\\SOFTWARE\\Microsoft\\Windows\\Windows Error
Reporting\\LocalDumps\\devenv.exe" /v DumpCount /t REG_DWORD /d 2

reg add "HKEY_LOCAL_MACHINE\\SOFTWARE\\Microsoft\\Windows\\Windows Error
Reporting\\LocalDumps\\devenv.exe" /v DumpFolder /t REG_SZ /d "C:\\CrashDumps"
```

Dostosuj liczbę zrzutów i folder zrzutu, zgodnie z potrzebami. Więcej informacji na temat tych ustawień można [znaleźć tutaj](/windows/win32/wer/collecting-user-mode-dumps).

> [!NOTE]
> Zrzuty przechwycone za pomocą Menedżera zadań mogą być niewłaściwym bitness, co sprawia, że mniej użyteczne. Procedura opisana powyżej jest preferowanym sposobem przechwytywania zrzutu sterty. Jeśli chcesz użyć Menedżera zadań, zamknij ten, który jest aktualnie uruchomiony, uruchom 32-bitowego Menedżera zadań (%windir%\\syswow64\\taskmgr.exe) i zbierz stamtąd zrzut sterty.

> [!NOTE] 
> Każdy plik zrzutu wyprodukowany przez tę metodę będzie miał rozmiar do 4 GB. Upewnij się, aby ustawić DumpFolder do lokalizacji z odpowiednią przestrzeń dysku lub odpowiednio dostosować DumpCount.

Za każdym razem, gdy program Visual Studio ulega awarii, utworzy plik zrzutu **devenv.exe.[ w** skonfigurowanym pliku dmp w skonfigurowanym miejscu.

Następnie użyj programu Visual Studio "Zgłoś problem..." Funkcji. To pozwoli ci dołączyć odpowiedni zrzut.

1.  Znajdź plik zrzutu dla zgłaszanego awarii (poszukaj pliku z poprawnym czasem tworzenia)

2.  Jeśli to możliwe,\*skompresuj plik (.zip), aby zmniejszyć jego rozmiar przed przesłaniem opinii

3.  Wykonaj kroki opisane w "[Jak zgłosić problem](/visualstudio/ide/how-to-report-a-problem-with-visual-studio-2017)", i dołącz zrzut sterty do nowego elementu opinii.

> [!NOTE] 
> **Najcenniejsze opinie:** W tym przypadku najcenniejsze informacje zwrotne to zrzut sterty przechwycony w momencie awarii.

## <a name="unresponsiveness"></a>Brak reakcji
VS przestaje odpowiadać przez dłuższy czas.

**Bezpośrednio powtarzalna brak reakcji**

Jak opisano w odpowiedniej sekcji dotyczącej awarii, w przypadku problemów, które można łatwo odtworzyć, widoczne na wielu komputerach i można je zademonstrować w małej próbce, najbardziej wartościowe raporty opinii są te, które zawierają kroki w celu odtworzenia problemu i zawierają przykładowy kod źródłowy, który pokazuje problem.

**Nieznana niereaguje**

Jeśli brak odpowiedzi objawia się w nieprzewidywalny sposób, w następnym wystąpieniu uruchom nowe wystąpienie programu Visual Studio i zgłoś problem z tego wystąpienia.
Na [ekranie "Rekord"](/visualstudio/ide/how-to-report-a-problem-with-visual-studio?view=vs-2019#record-a-repro)należy wybrać sesję programu Visual Studio, która nie odpowiada.

Jeśli wystąpienie programu Visual Studio, które nie odpowiada został uruchomiony w trybie administratora, a następnie drugie wystąpienie również muszą zostać uruchomione w trybie administratora.

>[!NOTE] 
> **Najcenniejsze opinie:** W tym przypadku najcenniejsze informacje zwrotne to zrzut sterty przechwycony w czasie braku odpowiedzi.

## <a name="slowness-and-high-cpu-issues"></a>Powolność i wysokie problemy z procesorem

Co sprawia, że powolność lub wysoki problem użycia procesora CPU najbardziej zasłynialne jest śledzenie wydajności przechwycone podczas powolnej pracy lub zdarzenia procesora CPU jest w toku.

>[!NOTE] 
> Jeśli to możliwe, wyizolować każdy scenariusz w osobnym, szczegółowym raporcie opinii.
Na przykład jeśli wpisywanie i nawigacja są powolne, wykonaj poniższe kroki raz na problem. Pomaga to zespołowi produktu wyizolować przyczynę określonych problemów.

Aby uzyskać najlepsze wyniki w przechwytywaniu wydajności, wykonaj następujące kroki:

1.  Jeśli nie jest jeszcze uruchomiony, otwórz kopię programu Visual Studio, w której odtworzono problem

    -   Mieć wszystko skonfigurowane, aby odtworzyć problem. Na przykład jeśli potrzebujesz określonego projektu do załadowania z otwartym określonym plikiem, upewnij się, że oba te kroki zostały zakończone przed kontynuowaniem.

    -   Jeśli *nie* zgłaszasz problemu specyficznego dla ładowania rozwiązania, spróbuj odczekać 5-10 minut (lub więcej, w zależności od rozmiaru rozwiązania) po otwarciu rozwiązania przed nagraniem śledzenia wydajności. Proces ładowania rozwiązania generuje dużą ilość danych, więc odczekanie kilku minut pomaga nam skupić się na konkretnym problemie, który zgłaszasz.

2.  Uruchamianie drugiej kopii programu Visual Studio *bez otwierania rozwiązania*

3.  W nowej kopii programu Visual Studio otwórz narzędzie **Zgłoś problem**

4.  Wykonaj kroki opisane w [jak zgłosić problem,](/visualstudio/ide/how-to-report-a-problem-with-visual-studio-2017) aż do osiągnięcia kroku "Podaj zrzut śladu i sterty (opcjonalnie)".

5.  Wybierz, aby nagrać pierwszą kopię programu Visual Studio (ten, który napotyka problem z wydajnością) i rozpocząć nagrywanie.

    -   Pojawi się aplikacja Rejestrator kroków i rozpocznie nagrywanie.

    -   **Podczas nagrywania wykonaj** problematyczną akcję w pierwszej kopii programu Visual Studio. Trudno jest nam rozwiązać konkretne problemy z wydajnością, jeśli nie pojawią się one w zarejestrowanym czasie.

    -   Jeśli akcja jest krótsza niż 30 sekund i można ją łatwo powtórzyć, powtórz akcję, aby jeszcze bardziej zademonstrować problem.

    -   W większości przypadków ślad 60 sekund jest wystarczający, aby wykazać problemy, zwłaszcza jeśli problematyczne działanie trwało (lub zostało powtórzone) przez ponad 30 sekund. Czas trwania można dostosować w razie potrzeby, aby przechwycić zachowanie, które chcesz naprawić.

6.  Kliknij "Zatrzymaj rekord" w Rejestratorze kroków, gdy tylko powolna praca lub zdarzenie wysokiego procesora, które chcesz zgłosić, zostanie zakończone. Może upłynąć kilka minut, aby przetworzyć śledzenia wydajności.

7.  Po zakończeniu, będzie kilka załączników do opinii. Dołącz dodatkowe pliki, które mogą pomóc odtworzyć problem (przykładowy projekt, zrzuty ekranu, filmy itp.).

8.  Prześlij opinię.

Podczas rejestrowania śledzenia wydajności, jeśli powolna operacja lub wysoki procesor CPU, który zgłaszasz, dobiega końca, natychmiast zatrzymaj nagrywanie. Jeśli zbiera się zbyt dużo informacji, najstarsze informacje są zastępowane. Jeśli śledzenie nie zostanie zatrzymane wkrótce (w ciągu kilku sekund) po interesującej operacji, przydatne dane śledzenia zostaną zastąpione.

Nie należy bezpośrednio dołączać śladów wydajności do istniejących elementów opinii w witrynie społeczności deweloperów. Żądanie/podanie dodatkowych informacji jest obsługiwanym przepływem pracy we wbudowanym narzędziu Zgłoś problem w programie Visual Studio. Jeśli śledzenie wydajności jest wymagane w celu rozwiązania poprzedniego elementu opinii, ustawimy stan elementu opinii na "Potrzebujesz więcej informacji", na który można odpowiedzieć w taki sam sposób, jak zgłoszenie nowego problemu. Aby uzyskać szczegółowe instrukcje, zapoznaj się z [sekcją "Potrzebujesz więcej informacji"](/visualstudio/ide/how-to-report-a-problem-with-visual-studio-2017?view=vs-2017#when-further-information-is-needed-need-more-info) w dokumencie narzędzia Zgłoś problem.

> [!NOTE] 
> **Najcenniejsze opinie:** Dla prawie wszystkich problemów powolność / wysoki procesor, najcenniejsze opinie jest wysokiego poziomu opis tego,\*co starali się zrobić, wraz ze śledzeniem wydajności (.etl.zip), który przechwytuje zachowanie w tym czasie.

**Zaawansowane ślady wydajności**

Możliwości śledzenia kolekcji w narzędziu Report-a-problem są wystarczające dla większości scenariuszy. Ale są chwile, w których wymagana jest większa kontrola nad kolekcji śledzenia (na przykład śledzenia o większym rozmiarze buforu), w którym to przypadku PerfView jest doskonałym narzędziem do użycia. Kroki ręcznego rejestrowania śledzenia wydajności za pomocą narzędzia PerfView można znaleźć na [śledzenia wydajności nagrywania za pomocą PerfView](https://github.com/dotnet/roslyn/wiki/Recording-performance-traces-with-PerfView) strony.

## <a name="out-of-process-issues"></a>Problemy poza procesem

> [!NOTE]
> Począwszy od programu Visual Studio 2019 w wersji 16.3 dzienniki poza procesem są automatycznie dołączane do opinii przesłanych za pomocą narzędzia Zgłoś problem. Jeśli jednak problem jest bezpośrednio powtarzalny, wykonując poniższe kroki, nadal można dodać dodatkowe informacje, aby lepiej zdiagnozować problem.

Istnieje wiele procesów satelitarnych, które są uruchamiane równolegle do programu Visual Studio i zapewniają różne funkcje spoza głównego procesu programu Visual Studio. Jeśli wystąpi błąd w jednym z tych procesów satelitarnych jest zwykle postrzegane po stronie programu Visual Studio jako "StreamJsonRpc.RemoteInvocationException" lub "StreamJsonRpc.ConnectionLostException".

Co sprawia, że te typy problemów najbardziej zas uzywalne jest zapewnienie dodatkowych dzienników, które mogą być zbierane przez następujące kroki:

1.  Jeśli jest to problem bezpośrednio powtarzalny, należy rozpocząć od usunięcia folderu **%temp%/servicehub/logs.** Jeśli nie możesz odtworzyć tego problemu, zachowaj ten folder w stanie nienaruszonym i zignoruj następujące punktory:

    -   Ustaw globalną zmienną środowiskową **ServiceHubTraceLevel** na **Wszystkie**
    -   Odtwórz problem.

2.  Pobierz [tutaj](https://www.microsoft.com/download/details.aspx?id=12493)narzędzie microsoft visual studio i .NET Framework Log Collection Tool .
3.  Uruchom narzędzie. Powoduje to wyprowadzanie pliku zip do **%temp%/vslogs.zip**. Dołącz ten plik do swojej opinii.

## <a name="see-also"></a>Zobacz też

* [Opcje opinii programu Visual Studio](../ide/feedback-options.md)
* [Zgłaszanie problemu z programem Visual Studio dla komputerów Mac](/visualstudio/mac/report-a-problem)
* [Zgłoś problem z c++](/cpp/how-to-report-a-problem-with-the-visual-cpp-toolset)
* [Społeczność deweloperów programu Visual Studio](https://developercommunity.visualstudio.com/)
* [Prywatność danych w społeczności deweloperów](developer-community-privacy.md)
