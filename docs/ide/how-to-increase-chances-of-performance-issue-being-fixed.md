---
title: Jak zwiększyć szanse na rozwiązywanie problemów z wydajnością
description: Dodatkowe informacje i najlepsze rozwiązania dotyczące przesyłania problemów z wydajnością w programie Visual Studio
author: seaniyer
ms.author: seiyer
ms.date: 11/19/2019
ms.topic: reference
ms.openlocfilehash: d61e7f47fde06c12b6b133ced76e5a8d72d220b0
ms.sourcegitcommit: b5cb0eb09369677514ee1f44d5d7050d34c7fbc1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/26/2019
ms.locfileid: "74528435"
---
# <a name="how-to-increase-the-chances-of-a-performance-issue-being-fixed"></a>Jak zwiększyć szanse na rozwiązywanie problemów z wydajnością

Narzędzie "[Zgłoś problem](https://aka.ms/vs-rap)" jest szeroko używane przez użytkowników programu Visual Studio do zgłaszania wielu problemów. Zespół programu Visual Studio plamuje trendy awarii i spowolnienia w zakresie opinii użytkowników i rozwiązuje problemy, które mają wpływ na rozległą Swath użytkowników. Im bardziej funkcjonalny jest konkretny bilet opinii, tym bardziej prawdopodobnie zostanie on zdiagnozowany i rozwiązany szybko przez zespół produktu. W tym dokumencie opisano najlepsze rozwiązania w zakresie zgłaszania problemów dotyczących awarii lub spowolnienia w celu zwiększenia możliwości podejmowania działań.

## <a name="general-best-practices"></a>Ogólne najlepsze rozwiązania

Program Visual Studio to duża, złożona platforma, która obsługuje wiele języków, typów projektów, platform i nie tylko. Sposób działania jest funkcją, w której składniki są instalowane i aktywne w sesji, zainstalowane rozszerzenia, ustawienia programu Visual Studio, Konfiguracja komputera i na końcu kształtu edytowanego kodu. Mając na względzie liczbę zmiennych, trudno jest stwierdzić, czy raport o problemach z jednego użytkownika ma ten sam problem jako raport o problemie od innego użytkownika, chociaż widoczny objaw jest taki sam. Z tego względu niektóre najlepsze rozwiązania mają na celu zagwarantowanie, że konkretny raport o problemie ma większe prawdopodobieństwo zdiagnozowania.

**Podaj jak określony tytuł**

Poszukaj unikatowych podpisów zgłaszanego problemu i Dołącz możliwie jak najwięcej w tytule. Jeśli tytuł jest opisowy, jest mniej dobry, że użytkownicy z niepowiązanymi problemami (ale ten sam objaw) będą głosować lub komentować bilet, co sprawia, że diagnozowanie *problemu jest* trudniejsze.

**W razie wątpliwości Zarejestruj nowy raport o problemie**

Wiele problemów może nie mieć żadnych odrębnych podpisów ani kroków do odtworzenia. W takich przypadkach nowy raport jest lepszy niż zagłosowanie lub komentarz dotyczący innego raportu, który zgłasza podobny *objaw*zewnętrzny. W zależności od typu raportu Dołącz do raportu dodatkowe pliki diagnostyczne zgodnie z opisem w dalszej części tego dokumentu.

**Najlepsze rozwiązania dotyczące problemów**

Poniżej opisano problemy, które trudno zdiagnozować bez prawidłowych plików diagnostycznych. Po zidentyfikowaniu przypadku, który najlepiej opisuje Twój problem, postępuj zgodnie z instrukcjami dotyczącymi opinii specyficznymi dla tego przypadku.

-   [Awarie:](#crashes) Awaria występuje, gdy proces (Visual Studio) kończy się nieoczekiwanie.

-   Brak [odpowiedzi:](#unresponsiveness) VS przestaje odpowiadać przez dłuższy czas.

-   [Problemy z spowolnieniem:](#slowness-and-high-cpu-issues) Każda określona akcja w programie VS jest wolniejsza niż wymagana

-   [Wysoki procesor CPU:](#slowness-and-high-cpu-issues) Rozszerzone okresy nieoczekiwanie wysokiego użycia procesora CPU

## <a name="crashes"></a>Stąp
Awaria występuje, gdy proces (Visual Studio) kończy się nieoczekiwanie.

**Bezpośrednie odtwarzalne awarie**

Bezpośrednie odtwarzalne awarie to przypadki, które mają wszystkie następujące cechy:

- Mogą być obserwowane przez następujący znany zestaw kroków

- Mogą być zaobserwowane na wielu komputerach (jeśli są dostępne)

- Może być odtwarzany w przykładowym kodzie lub w projekcie, który może być połączony lub udostępniony jako część opinii (Jeśli kroki obejmują Otwieranie projektu lub dokumentu)

Aby uzyskać te problemy, wykonaj kroki opisane w temacie "[Jak zgłosić problem](https://docs.microsoft.com/visualstudio/ide/how-to-report-a-problem-with-visual-studio-2017)" i pamiętaj, aby uwzględnić następujące informacje:

-   Kroki prowadzące do odtworzenia problemu

-   Autonomiczny projekt Odtwórz, zgodnie z powyższym opisem. Jeśli autonomiczna Odtwórz nie jest możliwa, należy dołączyć:

    -   Język otwartych projektów (C\#, C++itp.)

    -   Rodzaj projektu (Aplikacja konsolowa, ASP.NET itp.)


> [!NOTE]
> **Najbardziej cenna opinia:** W takim przypadku najbardziej cenną opinią jest zestaw kroków służących do odtworzenia problemu wraz z przykładowym kodem źródłowym.

**Nieznane awarie**

Jeśli nie masz pewności, co jest przyczyną awarii lub wydaje się losowo, możesz przechwycić zrzuty lokalnie za każdym razem, gdy program Visual Studio ulegnie awarii i dołączyć je do oddzielnych elementów opinii. Aby zaoszczędzić zrzuty lokalnie podczas awarii programu Visual Studio, uruchom następujące polecenia w oknie polecenia administratora:

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

Dostosuj liczbę zrzutów i folder zrzutów odpowiednio do potrzeb. Więcej informacji na temat tych ustawień znajduje się w [tym miejscu](https://docs.microsoft.com/windows/win32/wer/collecting-user-mode-dumps?redirectedfrom=MSDN).

> [!NOTE]
> Zrzuty przechwycone przy użyciu Menedżera zadań mogą mieć nieprawidłową liczbę bitów, co sprawia, że są one mniej użyteczne. Opisana powyżej procedura jest preferowanym sposobem przechwytywania zrzutu sterty. Jeśli chcesz użyć Menedżera zadań, Zamknij ten, który jest aktualnie uruchomiony, uruchom Menedżera zadań 32-bitowe (% windir%\\syswow64\\polecenia taskmgr. exe) i zbierz z niego zrzut sterty.

> [!NOTE] 
> Każdy plik zrzutu utworzony przez tę metodę będzie miał rozmiar do 4 GB. Upewnij się, że ustawisz DumpFolder do lokalizacji z odpowiednią ilością miejsca na dysku, lub odpowiednio Dostosuj DumpCount.

Za każdym razem, gdy program Visual Studio ulega awarii, utworzy plik zrzutu **devenv. exe. [ Number]. dmp** plik w skonfigurowanej lokalizacji.

Następnie użyj programu Visual Studio "Zgłoś problem..." ona. Umożliwi to dołączenie odpowiedniego zrzutu.

1.  Zlokalizuj plik zrzutu dla zgłaszanej awarii (Poszukaj pliku o poprawnym czasie tworzenia)

2.  Jeśli to możliwe, należy pliku zip (\*. zip), aby zmniejszyć jego rozmiar przed przesłaniem opinii

3.  Wykonaj kroki opisane w temacie "[Jak zgłosić problem](https://docs.microsoft.com/visualstudio/ide/how-to-report-a-problem-with-visual-studio-2017)" i Dołącz zrzut sterty do nowego elementu opinii.

> [!NOTE] 
> **Najbardziej cenna opinia:** W takim przypadku najbardziej cenną opinią jest zrzut sterty przechwytywany w chwili awarii.

## <a name="unresponsiveness"></a>Braku
VS przestaje odpowiadać przez dłuższy czas.

**Bezpośrednia odtwarzalność braku odpowiedzi**

Zgodnie z opisem w odpowiedniej sekcji dotyczącej awarii, w przypadku problemów, które można łatwo odtworzyć, były widoczne na wielu maszynach i mogą być prezentowane w małych przykładach, najbardziej cenne raporty dotyczące opinii to te, które obejmują kroki umożliwiające odtworzenie problemu i uwzględnienie przykładowy kod źródłowy, który pokazuje problem.

**Nieznana nieodpowiadający czas**

Jeśli manifesty nieodpowiadające są w sposób nieprzewidywalny, w następnym wystąpieniu Uruchom nowe wystąpienie programu Visual Studio i Zgłoś problem z tego wystąpienia.
Na [ekranie "rekord"](https://docs.microsoft.com/visualstudio/ide/how-to-report-a-problem-with-visual-studio?view=vs-2019#record-a-repro)Pamiętaj, aby wybrać sesję programu Visual Studio, która zawiesiła się.

Jeśli wystąpienie programu Visual Studio, które jest zawieszone, zostało uruchomione w trybie administratora, drugie wystąpienie należy również uruchomić w trybie administratora.

>[!NOTE] 
> **Najbardziej cenna opinia:** W takim przypadku najbardziej cenną opinią jest zrzut sterty przechwytywany w czasie braku odpowiedzi.

## <a name="slowness-and-high-cpu-issues"></a>Spowolnienie i wysokie problemy z procesorem CPU

Co sprawia, że zbyt niska lub wysokie wykorzystanie procesora CPU jest najbardziej funkcjonalny, jest to ślad wydajności przechwytywany, gdy trwa powolne działanie lub wysokie zdarzenie procesora CPU.

>[!NOTE] 
> Jeśli to możliwe, Izoluj każdy scenariusz w osobnym, konkretnym raporcie dotyczącym opinii.
Na przykład, jeśli wpisywanie i nawigacja jest niska, wykonaj poniższe czynności w przypadku każdego problemu. Ułatwia to zespołowi produktu odizolowanie przyczyny określonych problemów.

Aby uzyskać najlepsze wyniki przechwytywania wydajności, wykonaj następujące kroki:

1.  Jeśli jeszcze nie działa, należy otworzyć kopię programu Visual Studio, w której będzie można odtworzyć problem.

    -   Mam wszystko skonfigurowane w celu odtworzenia problemu. Na przykład jeśli potrzebujesz określonego projektu do załadowania z określonym plikiem otwartym, upewnij się, że oba te kroki zostały wykonane przed kontynuowaniem.

    -   Jeśli *nie* zgłaszasz problemu specyficznego dla ładowania rozwiązania, spróbuj odczekać 5-10 minut (lub więcej, w zależności od rozmiaru rozwiązania) po otwarciu rozwiązania przed zarejestrowaniem śladu wydajności. Proces ładowania rozwiązań tworzy dużą ilość danych, więc oczekiwanie na kilka minut pozwala nam skupić się na konkretnym wytworzonym problemie.

2.  Rozpocznij drugą kopię programu Visual Studio *bez otwartego rozwiązania*

3.  W nowej kopii programu Visual Studio Otwórz narzędzie **Zgłoś problem**

4.  Postępuj zgodnie z instrukcjami w temacie [Jak zgłosić problem](https://docs.microsoft.com/visualstudio/ide/how-to-report-a-problem-with-visual-studio-2017) do momentu osiągnięcia kroku "Podaj ślad i zrzut sterty (opcjonalnie)".

5.  Wybierz, aby zarejestrować pierwszą kopię programu Visual Studio (jeden napotkany problem z wydajnością) i Rozpocznij nagrywanie.

    -   Zostanie wyświetlona aplikacja rejestratora kroków i rozpocznie się nagrywanie.

    -   **Podczas nagrywania** wykonaj działanie problematyczne w pierwszej kopii programu Visual Studio. Trudno jest poprawić konkretne problemy z wydajnością, jeśli nie są one wyświetlane w zarejestrowanym czasie.

    -   Jeśli akcja jest krótsza niż 30 sekund i można ją łatwo powtórzyć, powtórz tę czynność, aby bardziej zademonstrować problem.

    -   W większości przypadków śledzenie 60 sekund jest wystarczające do zademonstrowania problemów, szczególnie jeśli problematyczna akcja zakończyła się (lub została powtórzona) przez więcej niż 30 sekund. Czas trwania można dostosować w miarę potrzeb, aby przechwytywać zachowanie, które chcesz naprawić.

6.  Kliknij pozycję "Zatrzymaj rekord" w rejestratorze kroków zaraz po zakończeniu operacji wolnej lub wysokiego procesora CPU, które chcesz zgłosić. Przetworzenie śledzenia wydajności może potrwać kilka minut.

7.  Po zakończeniu nastąpi kilka załączników do Twojej opinii. Dołącz wszelkie dodatkowe pliki, które mogą pomóc odtworzyć problem (przykładowy projekt, zrzuty ekranu, wideo itp.).

8.  Prześlij opinię.

Podczas rejestrowania śladu wydajności, jeśli zbyt niska operacja lub wysoki procesor CPU jest na końcu, natychmiast zatrzymać nagranie. W przypadku zebrania zbyt dużej ilości informacji najstarsze informacje są zastępowane. Jeśli śledzenie nie zostanie wkrótce zatrzymane (w ciągu kilku sekund) po interesującej operacji, przydatne dane śledzenia zostaną nadpisywane.

Nie dołączaj bezpośrednio śladów wydajności do istniejących elementów opinii w witrynie internetowej społeczności deweloperów. Żądanie/podanie dodatkowych informacji to obsługiwany przepływ pracy w wbudowanym raporcie programu Visual Studio — narzędzie problemu. Jeśli śledzenie wydajności jest wymagane, aby można było rozwiązać poprzedni element opinii, ustawimy stan elementu opinii na "potrzebne więcej informacji", co może być odpowiedziane w taki sam sposób jak Zgłaszanie nowego problemu. Aby uzyskać szczegółowe instrukcje, zapoznaj się z [sekcją "potrzebujesz więcej informacji"](https://docs.microsoft.com/visualstudio/ide/how-to-report-a-problem-with-visual-studio-2017?view=vs-2017#when-further-information-is-needed-need-more-info) w dokumencie Zgłoś narzędzie problemu.

> [!NOTE] 
> **Najbardziej cenna opinia:** W przypadku niemal wszystkich problemów z niską ilością zasobów procesora, najbardziej cenną opinią jest ogólny opis tego, co próbujesz zrobić, wraz z śladem wydajności (\*. etl. zip), który przechwytuje zachowanie w tym czasie.

**Zaawansowane dane śledzenia wydajności**

Możliwości zbierania danych śledzenia w przypadku większości scenariuszy są wystarczające w odniesieniu do narzędzia raport-a-problem. Ale istnieją przypadki, w których wymagana jest większa kontrola nad zbieraniem danych śledzenia (na przykład śledzenie o większym rozmiarze buforu), w którym to przypadku narzędzia PerfView jest doskonałym narzędziem do użycia. Procedurę ręcznego rejestrowania śledzenia wydajności za pomocą narzędzia Narzędzia PerfView można znaleźć na stronie [rejestrowanie śladów wydajności ze narzędzia PerfView](https://github.com/dotnet/roslyn/wiki/Recording-performance-traces-with-PerfView) .

## <a name="see-also"></a>Zobacz także

* [Opcje opinii programu Visual Studio](../ide/feedback-options.md)
* [Zgłoś problem z Visual Studio dla komputerów Mac](/visualstudio/mac/report-a-problem)
* [Zgłoś problem zC++](/cpp/how-to-report-a-problem-with-the-visual-cpp-toolset)
* [Społeczność deweloperów programu Visual Studio](https://developercommunity.visualstudio.com/)
* [Prywatność danych społeczności deweloperów](developer-community-privacy.md)