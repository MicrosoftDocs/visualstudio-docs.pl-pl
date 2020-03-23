---
title: Zbieranie alokacji pamięci .NET i danych okresu istnienia | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- .NET memory profiling method
- Profiling Tools,.NET memory method
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- dotnet
ms.openlocfilehash: 6a8c5d431b7be54c4c5bc1a1c37619deb67de751
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "74779587"
---
# <a name="collect-net-memory-allocation-and-lifetime-data"></a>Zbieranie danych alokacji pamięci .NET i okresu istnienia

Narzędzia profilowania programu Visual Studio obsługują zbieranie danych alokacji pamięci i okresu istnienia obiektów.NET, co ułatwia wykrywanie problemów z wydajnością związanych z pamięcią w aplikacji.

- Dane dotyczące alokacji pamięci .NET obejmują rozmiar i liczbę obiektów pamięci programu .NET Framework, które zostały przydzielone.

- Dane okresu istnienia obiektu obejmują rozmiar i liczbę obiektów pamięci .NET Framework, które zostały odzyskane w trzech generacjach wyrzucania elementów bezużytecznych.

> [!NOTE]
> Ulepszone funkcje zabezpieczeń w systemach Windows 8 i Windows Server 2012 wymagały znaczących zmian w sposobie, w jaki profiler programu Visual Studio zbiera dane na tych platformach. Aplikacje platformy uniwersalnej systemu Windows wymagają również nowych technik zbierania. Zobacz [Narzędzia wydajności w aplikacjach dla systemów Windows 8 i Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).

Dane można zbierać przy użyciu metody pobierania próbek lub profilowania instrumentacji.

- Korzystając z metody próbkowania, profiler śledzi wszystkie alokacje pamięci .NET i obiekty, które są generowane przez proces, który został uruchomiony lub dołączony do.

- Korzystając z metody instrumentacji, profiler śledzi tylko te alokacje pamięci .NET i obiekty, które są generowane przez moduły instrumentowane.

> [!IMPORTANT]
> Podczas zbierania danych pamięci .NET (alokacje, okresy istnienia obiektów lub oba) przy użyciu metody próbkowania wszystkie zdarzenia próbkowania określone przez użytkownika są ignorowane, a odpowiednie zdarzenia alokacji pamięci są używane do zbierania danych.

Po włączeniu profilowania of.NET alokacji pamięci, należy również włączyć widok alokacji. Po włączeniu profilowania danych okresu istnienia platformy .NET należy również włączyć widok okresu istnienia obiektów. Aby uzyskać więcej informacji, zobacz [Widok alokacji](../profiling/dotnet-memory-allocations-view.md) i [Widok okresu istnienia obiektu](../profiling/object-lifetime-view.md).

Aby uzyskać informacje dotyczące sposobu zbierania danych pamięci platformy .NET przy użyciu narzędzi wiersza polecenia Narzędzia profilowania, zobacz Zbieranie metod alokacji pamięci za pomocą metod pamięci .NET i danych w przypadku [korzystania z metod profilowania z wiersza polecenia](../profiling/using-profiling-methods-to-collect-performance-data-from-the-command-line.md).

## <a name="to-collect-net-memory-data"></a>Aby zebrać dane pamięci .NET

1. W **Eksploratorze wydajności**kliknij prawym przyciskiem myszy sesję wydajności, a następnie kliknij polecenie **Właściwości**.

2. W oknie dialogowym **Strony właściwości sesji** *wydajności* kliknij kartę **Ogólne** i zaznacz pole wyboru Zbieranie informacji **o alokacji obiektów .NET.**

3. Aby zebrać dane okresu istnienia obiektu .NET, zaznacz pole wyboru **Również zbieraj informacje o okresie istnienia obiektu .NET.**

## <a name="common-tasks"></a>Typowe zadania

Dodatkowe opcje można określić w oknie dialogowym**Strony właściwości** _sesji_wydajności sesji wydajności. Aby otworzyć to okno dialogowe:

- W **Eksploratorze wydajności**kliknij prawym przyciskiem myszy nazwę sesji wydajności, a następnie kliknij polecenie **Właściwości**.

Zadania w poniższej tabeli opisują opcje, które można określić w oknie dialogowym**Strony właściwości sesji** _wydajności_podczas zbierania danych pamięci .NET.

|Zadanie|Powiązana zawartość|
|----------|---------------------|
|Na stronie **Ogólne** określ szczegóły nazewnictwa wygenerowanego pliku danych profilowania (vsp).|- [Zbieranie danych dotyczących alokacji pamięci i okresu istnienia .NET](../profiling/collecting-dotnet-memory-allocation-and-lifetime-data.md)<br />- [Jak: Ustawianie opcji nazwy pliku danych wydajności](../profiling/how-to-set-performance-data-file-name-options.md)|
|Na **launch** strony wybierz aplikację, aby uruchomić, jeśli masz wiele projektów .exe w rozwiązaniu kodu.|- [Zbieranie danych interakcji warstwy](../profiling/collecting-tier-interaction-data.md)|
|Na stronie **Interakcja warstwy** dodaj ADO.NET dane wywołania do uruchomienia profilowania.|- [Zbieranie danych interakcji warstwy](../profiling/collecting-tier-interaction-data.md)|
|Na stronie **Zdarzenia systemu Windows** określ co najmniej jedno zdarzenie śledzenia zdarzeń dla systemu Windows (ETW) do zbierania za pomocą danych próbkowania.|- [Jak: Zbieranie danych śledzenia zdarzeń dla systemu Windows (ETW)](../profiling/how-to-collect-event-tracing-for-windows-etw-data.md)|
|Na stronie **Liczniki systemu Windows** określ jeden lub więcej liczników wydajności systemu operacyjnego, które mają być dodawanye do danych profilowania jako znaczników.|- [Jak: Zbieranie danych licznika systemu Windows](../profiling/how-to-collect-windows-counter-data.md)|
|Na stronie **Zaawansowane** określ wersję środowiska uruchomieniowego programu .NET Framework do profilu, jeśli moduły aplikacji używają wielu wersji. Domyślnie pierwsza załadowana wersja jest profilowana.|- [Jak: Określ środowisko uruchomieniowe programu .NET Framework](../profiling/how-to-specify-the-dotnet-framework-runtime.md)|

## <a name="instrumentation-tasks"></a>Zadania oprzyrządowania

Zadania w poniższej tabeli są opcjami w oknie dialogowym **Strony właściwości,** które są specyficzne dla profilowania za pomocą metody instrumentacji.

|Zadanie|Powiązana zawartość|
|----------|---------------------|
|Na stronie **Pliki binarne** określ lokalizację dla instrumentowanych kopii modułów. Domyślnie oryginalne pliki binarne są przenoszone do folderu kopii zapasowej.|- [Jak: Przeniesienie instrumentowanych plików binarnych](../profiling/how-to-relocate-instrumented-binaries.md)|
|Na stronie **Instrumentacja** wyklucz małe funkcje z profilowania, aby zmniejszyć obciążenie związane z profilowania, kod JavaScript profilu na ASP.NET stron sieci Web i określić polecenia do uruchomienia w wierszu polecenia przed i po procesie instrumentacji.|- [Jak: Wykluczyć lub uwzględnić krótkie funkcje z oprzyrządowania](../profiling/how-to-exclude-or-include-short-functions-from-instrumentation.md)<br />- [Jak: Profil kodu JavaScript na stronach internetowych](../profiling/how-to-profile-javascript-code-in-web-pages.md)<br />- [Jak: Określanie poleceń wstępnych i poprzyrządowych](../profiling/how-to-specify-pre-and-post-instrument-commands.md)|
|Na stronie **Liczniki procesora CPU** określ co najmniej jeden licznik wydajności procesora, który ma być dodawany do danych profilowania.|- [Jak: Zbieranie danych licznika procesora](../profiling/how-to-collect-cpu-counter-data.md)|
|Na stronie **Zaawansowane** określ wszystkie dodatkowe opcje programu VSInstr.exe, takie jak opcje dołączania lub wykluczania określonych funkcji. Aby uzyskać więcej informacji na temat opcji VSInstr, zobacz [VSInstr](../profiling/vsinstr.md)|- [Jak: Określ dodatkowe opcje oprzyrządowania](../profiling/how-to-specify-additional-instrumentation-options.md)<br />- [Jak: Ograniczenie oprzyrządowania do określonych funkcji](../profiling/how-to-limit-instrumentation-to-specific-functions.md)|

## <a name="see-also"></a>Zobacz też

[Konfigurowanie sesji](../profiling/configuring-performance-sessions.md)
wydajności[Jak: Wybieranie metod](../profiling/how-to-choose-collection-methods.md)
zbierania[właściwości sesji wydajności](../profiling/performance-session-properties.md)
