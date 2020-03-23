---
title: Zbieranie szczegółowych danych dotyczących chronometrażu za pomocą oprzyrządowania | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Profiling Tools,instrumentation method
- instrumentation profiling method
ms.assetid: e9deb370-c459-45ac-84d3-14d646590d05
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: bfd22edc9bd672a8d82c94a705b523ce7d836169
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "74779626"
---
# <a name="collect-detailed-timing-data-by-using-instrumentation"></a>Zbieranie szczegółowych danych o chronometrażu przy użyciu instrumentacji
Metoda [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] instrumentacji narzędzi profilowania wstrzykuje kod profilowania do kopii modułu. Kod rejestruje każdy wpis, exit, i wywołania funkcji funkcji w module podczas wykonywania profilowania. Metoda instrumentacji jest przydatna do zbierania szczegółowych informacji o chronometrażu o sekcji kodu oraz do zrozumienia wpływu operacji wejściowych i wyjściowych na wydajność aplikacji.

 Metodę instrumentacji można określić przy użyciu jednej z następujących procedur:

- Na pierwszej stronie Kreatora profilowania wybierz pozycję **Instrumentacja**.

- Na **pasku narzędzi Eksploratora wydajności** na liście **Metoda** kliknij pozycję **Instrumentacja**.

- Na stronie **Ogólne** okna dialogowego właściwości sesji wydajności wybierz pozycję **Instrumentacja**.

## <a name="common-tasks"></a>Typowe zadania
 Dodatkowe opcje można określić w oknie dialogowym**Strony właściwości** _sesji_wydajności sesji wydajności. Aby otworzyć to okno dialogowe:

- W **Eksploratorze wydajności**kliknij prawym przyciskiem myszy nazwę sesji wydajności, a następnie kliknij polecenie **Właściwości**.

  Zadania w poniższej tabeli opisują opcje, które można określić w oknie dialogowym**Strony właściwości sesji** _wydajności_podczas profilowania przy użyciu metody instrumentacji.

|Zadanie|Powiązana zawartość|
|----------|---------------------|
|Na stronie **Ogólne** dodaj alokację pamięci .NET i dane okresu istnienia oraz określ szczegóły nazewnictwa wygenerowanego pliku danych profilowania (vsp).|-   [Zbieranie danych dotyczących alokacji pamięci i okresu istnienia .NET](../profiling/collecting-dotnet-memory-allocation-and-lifetime-data.md)<br />-   [Jak: Ustawianie opcji nazwy pliku danych wydajności](../profiling/how-to-set-performance-data-file-name-options.md)|
|Na **launch** strony, jeśli masz wiele projektów .exe w solution.specify aplikacji do uruchomienia i ich kolejności uruchamiania.|-   [Jak: Określ plik binarny, aby rozpocząć](../profiling/how-to-specify-the-binary-to-start.md)|
|Na stronie **Pliki binarne** określ lokalizację dla instrumentowanych kopii modułów. Domyślnie oryginalne pliki binarne są przenoszone do folderu kopii zapasowej.|-   [Jak: Przenoszenie instrumentowanych plików binarnych](../profiling/how-to-relocate-instrumented-binaries.md)|
|Na stronie **Interakcja warstwy** dodaj ADO.NET dane wywołania do uruchomienia profilowania.|-   [Zbieranie danych interakcji warstwy](../profiling/collecting-tier-interaction-data.md)|
|Na stronie **Instrumentacja** wyklucz małe funkcje z profilowania, aby zmniejszyć obciążenie związane z profilowania, kod JavaScript profilu na ASP.NET stron sieci Web i określić polecenia do uruchomienia w wierszu polecenia przed i po procesie instrumentacji.|-   [Jak: Wykluczyć lub uwzględnić krótkie funkcje z oprzyrządowania](../profiling/how-to-exclude-or-include-short-functions-from-instrumentation.md)<br />-   [Jak: Profil kodu JavaScript na stronach internetowych](../profiling/how-to-profile-javascript-code-in-web-pages.md)<br />-   [Jak: Określanie poleceń przed- i po instrumencie](../profiling/how-to-specify-pre-and-post-instrument-commands.md)|
|Na stronie **Liczniki procesora CPU** określ co najmniej jeden licznik wydajności procesora, który ma być dodawany do danych profilowania.|-   [Jak: zbieranie danych licznika procesora](../profiling/how-to-collect-cpu-counter-data.md)|
|Na stronie **Zdarzenia systemu Windows** wybierz jedno lub więcej zdarzeń śledzenia zdarzeń dla systemu Windows (ETW) do zbierania z danymi próbkowania.|-   [Jak: Zbieranie śledzenia zdarzeń dla danych systemu Windows (ETW)](../profiling/how-to-collect-event-tracing-for-windows-etw-data.md)|
|Na stronie **Liczniki systemu Windows** określ jeden lub więcej liczników wydajności systemu operacyjnego, które mają być dodawanye do danych profilowania jako znaczników.|-   [Jak: Zbieranie danych licznika systemu Windows](../profiling/how-to-collect-windows-counter-data.md)|
|Na stronie **Zaawansowane** określ wszelkie dodatkowe opcje, które mają zostać przełęczona do programu instrumentacji VSInstr, takie jak opcje dołączania lub wykluczania określonych funkcji.|-   [Jak: Określ dodatkowe opcje oprzyrządowania](../profiling/how-to-specify-additional-instrumentation-options.md)<br />-   [Jak: Ograniczenie oprzyrządowania do określonych funkcji](../profiling/how-to-limit-instrumentation-to-specific-functions.md)<br />-   [Vsinstr](../profiling/vsinstr.md)|
