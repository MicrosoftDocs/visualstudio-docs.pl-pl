---
title: Zbieranie statystyk wydajności przy użyciu próbkowania
description: Użyj metody próbkowania narzędzia profilowania, aby znaleźć problemy dotyczące użycia procesora. Jest to sugerowana metoda uruchamiania większości badań wydajności.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- Profiling Tools,sampling
- sampling profiling method
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: e5a58ec02fa6bff0dd06ce08b933a381bca37a80
ms.sourcegitcommit: 7a5c4f60667b5792f876953d55192b49a73f5fe9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/16/2021
ms.locfileid: "98533735"
---
# <a name="collect-performance-statistics-by-using-sampling"></a>Zbieranie statystyk wydajności za pomocą próbkowania

Domyślnie metoda próbkowania narzędzia profilowania programu Visual Studio zbiera informacje o profilach co 10 000 000 cykli procesora (około każdej jednej setnej sekundy na komputerze z 1 GHz). Metoda próbkowania jest przydatna do znajdowania problemów z użyciem procesora i jest sugerowaną metodą uruchamiania większości badań wydajności.

> [!NOTE]
> Ulepszone funkcje zabezpieczeń w systemach Windows 8 i Windows Server 2012 wymagały znaczących zmian w sposobie, w jaki program Visual Studio profiler zbiera dane na tych platformach. Aplikacje platformy UWP wymagają również nowych technik zbierania danych. Zobacz [Narzędzia do oceny wydajności w aplikacjach systemu Windows 8 i Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).

Metodę próbkowania można określić za pomocą jednej z następujących procedur:

- Na pierwszej stronie kreatora profilowania kliknij pozycję **próbkowanie procesora (zalecane)**.
- Na **Eksplorator wydajności** pasku narzędzi na liście **Metoda** kliknij pozycję **próbkowanie**.
- Na stronie **Ogólne** okna dialogowego właściwości sesji wydajności kliknij polecenie **próbkowanie**.

## <a name="common-tasks"></a>Typowe zadania

Dodatkowe opcje można określić w oknie dialogowym **strony właściwości** sesji wydajności. Aby otworzyć to okno dialogowe:

- W **Eksplorator wydajności** kliknij prawym przyciskiem myszy nazwę sesji wydajności, a następnie kliknij polecenie **Właściwości**.

  Zadania w poniższej tabeli opisują opcje, które można określić w oknie dialogowym **strony właściwości** _sesji wydajności_ podczas profilowania przy użyciu metody próbkowania.

|Zadanie|Powiązana zawartość|
|----------|---------------------|
|Na stronie **Ogólne** Dodaj przydział pamięci platformy .NET i zbieranie danych o okresie istnienia, a następnie określ szczegóły nazewnictwa dla wygenerowanego pliku danych profilowania (. vsp).|- [Zbieranie danych alokacji pamięci .NET i okresu istnienia](../profiling/collecting-dotnet-memory-allocation-and-lifetime-data.md)<br />- [Instrukcje: Ustawianie opcji nazwy pliku danych wydajności](../profiling/how-to-set-performance-data-file-name-options.md)|
|Na stronie **próbkowanie** Zmień częstotliwość próbkowania, Zmień zdarzenie próbkowania z cykli zegara procesora na inny licznik wydajności procesora lub Zmień oba te parametry.|- [Instrukcje: Wybieranie zdarzeń próbkowania](../profiling/how-to-choose-sampling-events.md)|
|Na stronie **Uruchamianie** Określ aplikację do uruchomienia i kolejność uruchamiania, jeśli masz wiele projektów. exe w rozwiązaniu kodu.|- [Zbieranie danych o interakcji między warstwami](../profiling/collecting-tier-interaction-data.md)|
|Na stronie **interakcja warstwy** Dodaj informacje o wywołaniu ADO.NET do danych zbieranych w ramach przebiegu profilowania.|- [Zbieranie danych o interakcji między warstwami](../profiling/collecting-tier-interaction-data.md)|
|Na stronie **zdarzenia systemu Windows** Określ jedno lub więcej zdarzeń śledzenia zdarzeń systemu Windows (ETW), które mają być zbierane z danymi próbkowania.|- [Instrukcje: zbieranie danych śledzenia zdarzeń dla systemu Windows (ETW)](../profiling/how-to-collect-event-tracing-for-windows-etw-data.md)|
|Na stronie **liczniki systemu Windows** Określ co najmniej jeden licznik wydajności systemu operacyjnego, który ma zostać dodany do danych profilowania jako znaczniki.|- [Instrukcje: zbieranie danych licznika systemu Windows](../profiling/how-to-collect-windows-counter-data.md)|
|Na stronie **Zaawansowane** Określ wersję środowiska uruchomieniowego .NET Framework, która ma być używana do profilowania, jeśli moduły aplikacji korzystają z wielu wersji. Domyślnie pierwsza ładowana wersja jest profilowana.|- [Instrukcje: Określanie środowiska uruchomieniowego .NET Framework](../profiling/how-to-specify-the-dotnet-framework-runtime.md)|
