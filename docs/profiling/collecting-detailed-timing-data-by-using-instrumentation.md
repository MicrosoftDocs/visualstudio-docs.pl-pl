---
title: Zbieranie danych o chronometrażu przy użyciu Instrumentacji | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Profiling Tools,instrumentation method
- instrumentation profiling method
ms.assetid: e9deb370-c459-45ac-84d3-14d646590d05
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a58a5a1431dbb8ddbc9b23d93928f615e945b3b3
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62834310"
---
# <a name="collect-detailed-timing-data-by-using-instrumentation"></a>Zbieranie szczegółowych danych o chronometrażu przy użyciu instrumentacji
[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Profiling Tools metoda Instrumentacja wprowadza profilowania kodu do kopii modułu. Ten kod rejestruje każdego wpisu, zakończenia i wywołanie funkcji funkcji w module podczas uruchomienia profilowania. Metoda Instrumentacja jest przydatne do zbierania informacji chronometrażu o sekcji kodu i zrozumienie wpływu na operacje wejścia i wyjścia na wydajność aplikacji.

 Należy określić metody instrumentacji, przy użyciu jednej z następujących procedur:

- Na pierwszej stronie kreatora profilowania, wybierz **Instrumentacji**.

- Na **Eksplorator wydajności** narzędzi w **metoda** kliknij **Instrumentacji**.

- Na **ogólne** strony okna dialogowego właściwości sesji wydajności, wybierz opcję **Instrumentacji**.

## <a name="common-tasks"></a>Wspólne zadania
 Można określić dodatkowe opcje w _sesji wydajności_**stron właściwości** okna dialogowego sesji wydajności. Aby otworzyć to okno dialogowe:

- W **Eksplorator wydajności**, kliknij prawym przyciskiem myszy nazwę sesji wydajności, a następnie kliknij **właściwości**.

  Zadania przedstawione w poniższej tabeli opisano opcje, które można określić w _sesji wydajności_**stron właściwości** okno dialogowe podczas profilowania przy użyciu metody instrumentacji.

|Zadanie|Powiązana zawartość|
|----------|---------------------|
|Na **ogólne** strony, Dodaj alokacji pamięci .NET i danych o okresie istnienia, a następnie określ szczegóły nazewnictwa wygenerowany plik danych (Vsp) profilowania.|-   [Zbieranie danych alokacji i okresie istnienia pamięci platformy .NET](../profiling/collecting-dotnet-memory-allocation-and-lifetime-data.md)<br />-   [Jak: Ustawianie opcji nazwy pliku danych wydajności](../profiling/how-to-set-performance-data-file-name-options.md)|
|Na **Uruchom** strony, jeśli masz wiele projektów .exe w solution.specify Twojej aplikacji, aby uruchomić i ich kolejność uruchamiania.|-   [Jak: Określanie plików binarnych do uruchomienia](../profiling/how-to-specify-the-binary-to-start.md)|
|Na **pliki binarne** Określ lokalizację instrumentowanych kopie modułów. Domyślnie oryginalnych danych binarnych są przenoszone do folderu kopii zapasowej.|-   [Jak: Zmień lokalizację instrumentowanych danych binarnych](../profiling/how-to-relocate-instrumented-binaries.md)|
|Na **funkcję Tier Interaction** strony, należy dodać danych połączeń ADO.NET do uruchomienia profilowania.|-   [Zbieranie danych o interakcji między warstwami](../profiling/collecting-tier-interaction-data.md)|
|Na **Instrumentacji** strony, Wyklucz małe funkcje z profilowania, aby zmniejszyć profilowania obciążenie, Profiluj kod JavaScript na stronach sieci Web platformy ASP.NET, a także określić polecenie do uruchomienia w wierszu polecenia przed i po proces instrumentacji.|-   [Jak: Wykluczanie lub uwzględnianie krótkich funkcji z Instrumentacji](../profiling/how-to-exclude-or-include-short-functions-from-instrumentation.md)<br />-   [Jak: Profiluj kod JavaScript na stronach sieci web](../profiling/how-to-profile-javascript-code-in-web-pages.md)<br />-   [Jak: Określ polecenia przed i po Instrumentacji](../profiling/how-to-specify-pre-and-post-instrument-commands.md)|
|Na **liczniki CPU** stronie Określ co najmniej jeden licznik wydajności procesora do dodania do danych profilowania.|-   [Porady: zbieranie danych licznika procesora CPU](../profiling/how-to-collect-cpu-counter-data.md)|
|Na **zdarzeń Windows** wybierz jedno lub więcej zdarzeń śledzenie zdarzeń dla Windows (ETW) mają być zbierane dane z próbkowania.|-   [Jak: Zbieranie, śledzenie zdarzeń systemu Windows (ETW) danych](../profiling/how-to-collect-event-tracing-for-windows-etw-data.md)|
|Na **liczniki Windows** stronie Określ co najmniej jeden licznik wydajności systemu operacyjnego można dodać do danych profilowania jako znaki.|-   [Jak: Zbieranie danych licznika Windows](../profiling/how-to-collect-windows-counter-data.md)|
|Na **zaawansowane** Określ dodatkowe opcje, które mają być przekazane do programu Instrumentacji VSInstr, takich jak opcje do dołączania lub wykluczania określonych funkcji.|-   [Jak: Określanie dodatkowych opcji Instrumentacji](../profiling/how-to-specify-additional-instrumentation-options.md)<br />-   [Jak: Ograniczenie Instrumentacji do określonych funkcji](../profiling/how-to-limit-instrumentation-to-specific-functions.md)<br />-   [Narzędzie VSInstr](../profiling/vsinstr.md)|