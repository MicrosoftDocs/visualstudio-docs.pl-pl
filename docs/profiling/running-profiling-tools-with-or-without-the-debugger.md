---
title: Uruchamianie narzędzi profilowania z debugerem lub bez niego | Microsoft Docs
description: Dowiedz się więcej o różnicach między różnymi trybami dostępnymi dla narzędzi profilowania
ms.date: 5/26/2020
ms.topic: conceptual
ms.assetid: 3fcdccad-c1bd-4c67-bcec-bf33a8fb5d63
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0bd8f90c586366a298ba96009dfe5d87a042141b
ms.sourcegitcommit: 935e4d9a20928b733e573b6801a6eaff0d0b1b14
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/25/2020
ms.locfileid: "95970299"
---
# <a name="run-profiling-tools-with-or-without-the-debugger"></a>Uruchamianie narzędzi profilowania z debugerem lub bez debugera

Program Visual Studio oferuje wybór narzędzi do pomiaru wydajności i profilowania. Niektóre narzędzia, takie jak użycie procesora CPU i użycie pamięci, można uruchomić z debugerem lub bez niego, a także w konfiguracjach kompilacji wersji lub debugowania. Narzędzia, które pojawiają się w [oknie narzędzia diagnostyczne](../profiling/profiling-feature-tour.md#measure-performance-while-debugging) , są uruchamiane tylko podczas sesji debugowania. Narzędzia, które pojawiają się w [profilerze wydajności](../profiling/profiling-feature-tour.md#post_mortem) , są uruchamiane bez debugera i analizują wyniki po zaznaczeniu, aby zatrzymać i zbierać dane (na potrzeby analizy końcowej).

>[!NOTE]
>Możesz użyć narzędzi do oceny wydajności bez debugera w systemie Windows 7 i nowszych. Do uruchomienia narzędzi profilowania zintegrowanych ze debugerem wymagany jest system Windows 8 lub nowszy.

Profiler wydajności bez debugera i zintegrowany z debugerem narzędzia diagnostyczne udostępniają różne informacje i środowiska. Narzędzia zintegrowane z debugerem pokazują wartości zmiennych i umożliwiają używanie punktów przerwania. Narzędzia, które nie są debugerem, dają wyniki bliżej środowiska użytkownika końcowego.

Aby pomóc w wyborze narzędzi i wyników do użycia, należy wziąć pod uwagę następujące kwestie:

- Narzędzie zintegrowane z debugerem a narzędziem niebędącym debugerem
  - Zewnętrzne problemy z wydajnością, takie jak pliki we/wy lub problemy z odpowiedzią w sieci, nie wyglądają inaczej w debugerze lub narzędziach innych niż debuger.
  - Debuger zmienia czasy wydajności, ponieważ wymaga operacji debugera, takich jak przechwycenie zdarzeń ładowania wyjątków i modułów.
  - Numery wydajności kompilacji wydania w profilerze wydajności są najbardziej precyzyjne i dokładne. Narzędzia zintegrowane z debugerem są najbardziej przydatne do porównywania z innymi pomiarami związanymi z debugowaniem lub do korzystania z funkcji debugera.
  - Niektóre narzędzia, takie jak narzędzie do alokacji obiektów platformy .NET, są dostępne tylko dla scenariuszy innych niż debuger.
- Debugowanie a kompilacja wydania
  - W przypadku problemów spowodowanych przez wywołania intensywnie korzystające z procesora CPU mogą występować znaczne różnice wydajności między kompilacjami wydań i debugowania. Sprawdź, czy problem występuje w kompilacjach wydania.
  - Jeśli problem występuje tylko podczas kompilacji debugowania, prawdopodobnie nie trzeba uruchamiać narzędzi niebędących debugerem. W przypadku problemów z kompilacją wersji należy zdecydować, czy funkcje zapewniane przez narzędzia zintegrowane z debugerem pomogą zidentyfikować problem.
  - Kompilacje wydań zapewniają optymalizacje, takie jak wywołania funkcji defragmentowania i stałe, oczyszczanie nieużywanych ścieżek kodu i przechowywanie zmiennych w sposób, który nie może być używany przez debuger. Liczby wydajności w kompilacjach debugowania są mniej dokładne, ponieważ kompilacje debugowania nie mają tych optymalizacji.

## <a name="collect-profiling-data-while-debugging"></a><a name="BKMK_Quick_start__Collect_diagnostic_data"></a> Zbieraj dane profilowania podczas debugowania

Po rozpoczęciu debugowania w programie Visual Studio, wybierając **Debuguj**  >  **Rozpocznij debugowanie** lub naciskając klawisz **F5**, domyślnie zostanie wyświetlone okno **Narzędzia diagnostyczne** . Aby otworzyć go ręcznie, wybierz pozycję **Debuguj**  >  **okna**  >  **Pokaż narzędzia diagnostyczne**. Okno **Narzędzia diagnostyczne** zawiera informacje o zdarzeniach, pamięci procesu i użycia procesora CPU.

![Zrzut ekranu okna narzędzia diagnostyczne](../profiling/media/diagnostictoolswindow.png " Okno Narzędzia diagnostyczne")

- Użyj ikony **ustawień** na pasku narzędzi, aby określić, czy ma być wyświetlane **użycie pamięci**, **Analiza interfejsu użytkownika** i **użycie procesora CPU**.

- Wybierz pozycję **Ustawienia** na liście rozwijanej **Ustawienia** , aby otworzyć **Narzędzia diagnostyczne strony właściwości** z więcej opcji.

- Jeśli używasz Visual Studio Enterprise, możesz włączyć lub wyłączyć IntelliTrace, przechodząc do opcji **Narzędzia**  >  **Options**  >  **IntelliTrace**.

Sesja diagnostyczna zostanie zakończona po zatrzymaniu debugowania.

Aby uzyskać więcej informacji, zobacz:

- [Mierzenie wydajności aplikacji przez analizowanie użycia procesora CPU](../profiling/beginners-guide-to-performance-profiling.md)
- [Mierzenie użycia pamięci w programie Visual Studio](../profiling/memory-usage.md)

### <a name="the-events-tab"></a>Karta zdarzenia

Podczas sesji debugowania na karcie zdarzenia okna narzędzia diagnostyczne wyświetlane są zdarzenia diagnostyczne, które wystąpiły. Kategoria prefiksy *punktów przerwania*, *plik* i inne, umożliwia szybkie przeszukanie listy dla kategorii lub pominięcie kategorii, z którymi się nie interesują.

Lista rozwijana **Filtr** służy do filtrowania zdarzeń w i poza widok, wybierając lub czyszcząc określone kategorie zdarzeń.

![Zrzut ekranu filtru zdarzeń diagnostycznych](../profiling/media/diagnosticeventfilter.png "Filtr zdarzeń diagnostycznych")

Użyj pola wyszukiwania, aby znaleźć konkretny ciąg na liście zdarzeń. Poniżej przedstawiono wyniki wyszukiwania *nazwy* ciągu, która pasuje do czterech zdarzeń:

![Zrzut ekranu przedstawiający wyszukiwanie zdarzeń diagnostycznych](../profiling/media/diagnosticseventsearch.png "Wyszukiwanie zdarzeń diagnostycznych")

Aby uzyskać więcej informacji, zobacz [Wyszukiwanie i filtrowanie zdarzeń na karcie zdarzenia okna narzędzia diagnostyczne](https://devblogs.microsoft.com/devops/searching-and-filtering-the-events-tab-of-the-diagnostic-tools-window/).

## <a name="collect-profiling-data-without-debugging"></a>Zbieranie danych profilowania bez debugowania

Aby zbierać dane dotyczące wydajności bez debugowania, można uruchomić narzędzia profilera wydajności.

1. Po otwarciu projektu w programie Visual Studio Ustaw konfigurację rozwiązania na **Zwolnij**, a następnie wybierz pozycję **lokalny debuger systemu Windows** (lub **komputer lokalny**) jako cel wdrożenia.

1. Wybierz pozycję **Debuguj**  >  **wydajność Profiler** lub naciśnij klawisz **Alt** + **F2**.

1. Na stronie uruchamiania narzędzi diagnostycznych wybierz co najmniej jedno narzędzie do uruchomienia. Wyświetlane są tylko narzędzia, które mają zastosowanie do typu projektu, systemu operacyjnego i języka programowania. Wybierz pozycję **Pokaż wszystkie narzędzia** , aby wyświetlić także narzędzia, które są wyłączone dla tej sesji diagnostycznej.

   ![Zrzut ekranu narzędzi diagnostycznych](../profiling/media/diaghubsummarypage.png "DIAG_SelectTool")

1. Aby rozpocząć sesję diagnostyczną, wybierz pozycję **Uruchom**.

   Gdy sesja jest uruchomiona, niektóre narzędzia pokazują wykresy danych w czasie rzeczywistym na stronie narzędzia diagnostyczne, a także kontrolki do wstrzymywania i wznawiania zbierania danych.

    ![Zrzut ekranu przedstawiający zbieranie danych w profilerze wydajności](../profiling/media/diaghubcollectdata.png "Zbieranie danych przez centrum")

1. Aby zakończyć sesję diagnostyczną, wybierz pozycję **Zatrzymaj zbieranie**.

   Analizowane dane pojawiają się na stronie **raportu** .

Raporty można zapisać i otworzyć z listy **ostatnio otwierane sesje** na stronie uruchamiania narzędzia diagnostyczne.

![Zrzut narzędzia diagnostyczne ekranu przedstawiający listę ostatnio otwieranych sesji](../profiling/media/diaghubopenexistingdiagsession.png "PDHUB_OpenExistingDiagSession")

Aby uzyskać więcej informacji, zobacz:

- [Analizowanie użycia procesora CPU](../profiling/cpu-usage.md)
- [Analizowanie użycia pamięci dla kodu platformy .NET](../profiling/dotnet-alloc-tool.md)
- [Analizowanie użycia pamięci](../profiling/memory-usage-without-debugging2.md)
- [Analizowanie wydajności kodu asynchronicznego .NET](../profiling/analyze-async.md)
- [Analizowanie wydajności bazy danych](../profiling/analyze-database.md)
- [Analizowanie użycia procesora GPU](../profiling/gpu-usage.md)

## <a name="collect-profiling-data-from-the-command-line"></a>Zbieranie danych profilowania z wiersza polecenia

Aby zmierzyć dane dotyczące wydajności z wiersza polecenia, można użyć VSDiagnostics.exe, który jest dołączony do programu Visual Studio lub narzędzi zdalnych. Jest to przydatne w przypadku przechwytywania śladów wydajności w systemach, na których nie zainstalowano programu Visual Studio lub tworzenia skryptów kolekcji śladów wydajności. Aby uzyskać szczegółowe instrukcje, zobacz [mierzenie wydajności aplikacji z wiersza polecenia](../profiling/profile-apps-from-command-line.md).