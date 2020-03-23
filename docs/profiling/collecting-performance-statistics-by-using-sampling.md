---
title: Zbieranie statystyk wydajności przy użyciu próbkowania | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Profiling Tools,sampling
- sampling profiling method
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: cbe03f52b31664c59cb7e59d448db7c6b96b6487
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "74772881"
---
# <a name="collect-performance-statistics-by-using-sampling"></a>Zbieranie statystyk wydajności za pomocą próbkowania

Domyślnie metoda próbkowania narzędzi profilowania programu Visual Studio zbiera informacje profilowania co 10 000 000 cykli procesora (mniej więcej co jedną setną sekundy na komputerze 1 GHz). Metoda próbkowania jest przydatna do znajdowania problemów z wykorzystaniem procesora i jest sugerowaną metodą uruchamiania większości badań wydajności.

> [!NOTE]
> Ulepszone funkcje zabezpieczeń w systemach Windows 8 i Windows Server 2012 wymagały znaczących zmian w sposobie, w jaki profiler programu Visual Studio zbiera dane na tych platformach. Aplikacje platformy uniwersalnej systemu Windows wymagają również nowych technik zbierania. Zobacz [Narzędzia wydajności w aplikacjach dla systemów Windows 8 i Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).

Metodę próbkowania można określić przy użyciu jednej z następujących procedur:

- Na pierwszej stronie Kreatora profilowania kliknij pozycję **Próbkowanie procesora (zalecane)**.
- Na pasku narzędzi **Eksploratora wydajności** na liście **Metoda** kliknij pozycję **Próbkowanie**.
- Na stronie **Ogólne** okna dialogowego właściwości sesji wydajności kliknij pozycję **Próbkowanie**.

## <a name="common-tasks"></a>Typowe zadania

Dodatkowe opcje można określić w oknie dialogowym**Strony właściwości** _sesji_wydajności sesji wydajności. Aby otworzyć to okno dialogowe:

- W **Eksploratorze wydajności**kliknij prawym przyciskiem myszy nazwę sesji wydajności, a następnie kliknij polecenie **Właściwości**.

  Zadania w poniższej tabeli opisują opcje, które można określić w oknie dialogowym**Strony właściwości sesji** _wydajności_podczas profilowania przy użyciu metody próbkowania.

|Zadanie|Powiązana zawartość|
|----------|---------------------|
|Na stronie **Ogólne** dodaj alokację pamięci .NET i zbieranie danych w okresie istnienia oraz określ szczegóły nazewnictwa wygenerowanego pliku danych profilowania (vsp).|- [Zbieranie alokacji pamięci platformy .NET i danych w okresie istnienia](../profiling/collecting-dotnet-memory-allocation-and-lifetime-data.md)<br />- [Jak: Ustawianie opcji nazwy pliku danych wydajności](../profiling/how-to-set-performance-data-file-name-options.md)|
|Na **próbkowanie** strony zmień częstotliwość próbkowania, zmień zdarzenie próbkowania z cykli zegara procesora na inny licznik wydajności procesora lub zmień oba..|- [Jak: Wybierz zdarzenia próbkowania](../profiling/how-to-choose-sampling-events.md)|
|Na **launch** strony określ aplikację do uruchomienia i kolejność rozpoczęcia, jeśli masz wiele projektów .exe w rozwiązaniu kodu.|- [Zbieranie danych interakcji warstwy](../profiling/collecting-tier-interaction-data.md)|
|Na stronie **Interakcja warstwy** dodaj informacje o ADO.NET wywołania do danych zebranych w przebieguprofilowania.|- [Zbieranie danych interakcji warstwy](../profiling/collecting-tier-interaction-data.md)|
|Na stronie **Zdarzenia systemu Windows** określ co najmniej jedno zdarzenie śledzenia zdarzeń dla systemu Windows (ETW) do zbierania za pomocą danych próbkowania.|- [Jak: Zbieranie danych śledzenia zdarzeń dla systemu Windows (ETW)](../profiling/how-to-collect-event-tracing-for-windows-etw-data.md)|
|Na stronie **Liczniki systemu Windows** określ jeden lub więcej liczników wydajności systemu operacyjnego, które mają być dodawanye do danych profilowania jako znaczników.|- [Jak: Zbieranie danych licznika systemu Windows](../profiling/how-to-collect-windows-counter-data.md)|
|Na stronie **Zaawansowane** określ wersję środowiska uruchomieniowego programu .NET Framework do profilu, jeśli moduły aplikacji używają wielu wersji. Domyślnie pierwsza załadowana wersja jest profilowana.|- [Jak: Określ środowisko uruchomieniowe programu .NET Framework](../profiling/how-to-specify-the-dotnet-framework-runtime.md)|
