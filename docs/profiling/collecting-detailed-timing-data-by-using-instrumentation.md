---
title: Zbieranie szczegółowych danych o chronometrażu przy użyciu instrumentacji | Microsoft Docs
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
ms.sourcegitcommit: 00b71889bd72b6a566586885bdb982cfe807cf54
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2019
ms.locfileid: "74779626"
---
# <a name="collect-detailed-timing-data-by-using-instrumentation"></a>Zbieranie szczegółowych danych o chronometrażu przy użyciu instrumentacji
Metoda [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] narzędzia profilowania Instrumentation wprowadza kod profilowania do kopii modułu. Kod rejestruje każde wejście, wyjście i wywołanie funkcji funkcji w module podczas przebiegu profilowania. Metoda Instrumentacji jest przydatna do gromadzenia szczegółowych informacji o chronometrażu w sekcji kodu oraz do poznania wpływu operacji wejścia i wyjścia na wydajność aplikacji.

 Metodę Instrumentacji można określić za pomocą jednej z następujących procedur:

- Na pierwszej stronie kreatora profilowania wybierz pozycję **Instrumentacja**.

- Na **Eksplorator wydajności** pasku narzędzi na liście **Metoda** kliknij pozycję **Instrumentacja**.

- Na stronie **Ogólne** okna dialogowego właściwości dla sesji wydajności Wybierz pozycję **Instrumentacja**.

## <a name="common-tasks"></a>Wspólne zadania
 Dodatkowe opcje można określić w oknie dialogowym**strony właściwości** sesji wydajności. Aby otworzyć to okno dialogowe:

- W **Eksplorator wydajności**kliknij prawym przyciskiem myszy nazwę sesji wydajności, a następnie kliknij polecenie **Właściwości**.

  Zadania w poniższej tabeli zawierają opis opcji, które można określić w oknie dialogowym**strony właściwości** _sesji wydajności_podczas profilowania przy użyciu metody instrumentacji.

|Zadanie|Powiązana zawartość|
|----------|---------------------|
|Na stronie **Ogólne** Dodaj dane alokacji pamięci .NET i okresu istnienia, a następnie określ szczegóły nazewnictwa wygenerowanego pliku danych profilowania (. vsp).|-   [Zbieraj dane alokacji pamięci .NET i okresu istnienia](../profiling/collecting-dotnet-memory-allocation-and-lifetime-data.md)<br />-   [: Ustawianie opcji nazwy pliku danych wydajności](../profiling/how-to-set-performance-data-file-name-options.md)|
|Na stronie **Uruchamianie** , jeśli w rozwiązaniu masz wiele projektów. exe. Określ aplikację do uruchomienia i ich kolejność uruchamiania.|-   [jak określić plik binarny do uruchomienia](../profiling/how-to-specify-the-binary-to-start.md)|
|Na stronie **pliki binarne** Określ lokalizację przynoszącą instrumentację kopii modułów. Domyślnie oryginalne pliki binarne są przenoszone do folderu kopii zapasowej.|-   [How to: zmiana położenia plików binarnych z instrumentacją](../profiling/how-to-relocate-instrumented-binaries.md)|
|Na stronie **interakcja warstwy** Dodaj dane wywołania ADO.NET do przebiegu profilowania.|-   [Zbieraj dane interakcji warstwy](../profiling/collecting-tier-interaction-data.md)|
|Na stronie **Instrumentacja** Wyklucz małe funkcje z profilowania, aby zmniejszyć obciążenie profilowania, kod JavaScript profilu w ASP.NET stronach sieci Web i określić polecenia do uruchomienia w wierszu polecenia przed i po procesie Instrumentacji.|-   [instrukcje: wykluczanie lub uwzględnianie krótkich funkcji z Instrumentacji](../profiling/how-to-exclude-or-include-short-functions-from-instrumentation.md)<br />-   [: profilowanie kodu JavaScript na stronach sieci Web](../profiling/how-to-profile-javascript-code-in-web-pages.md)<br />-   [: Określanie poleceń przed i po Instrumentacji](../profiling/how-to-specify-pre-and-post-instrument-commands.md)|
|Na stronie **liczniki procesora** Określ co najmniej jeden licznik wydajności procesora, który ma zostać dodany do danych profilowania.|-   [jak zbierać dane licznika procesora CPU](../profiling/how-to-collect-cpu-counter-data.md)|
|Na stronie **zdarzenia systemu Windows** wybierz jedno lub więcej zdarzeń śledzenia zdarzeń systemu Windows (ETW), które mają być zbierane z danymi próbkowania.|-   [jak zbierać dane śledzenia zdarzeń systemu Windows (ETW)](../profiling/how-to-collect-event-tracing-for-windows-etw-data.md)|
|Na stronie **liczniki systemu Windows** Określ co najmniej jeden licznik wydajności systemu operacyjnego, który ma zostać dodany do danych profilowania jako znaczniki.|-   [jak zbierać dane liczników systemu Windows](../profiling/how-to-collect-windows-counter-data.md)|
|Na stronie **Zaawansowane** określ wszelkie dodatkowe opcje, które chcesz przekazać do programu Instrumentacji VSInstr, takie jak opcje dołączania lub wykluczania określonych funkcji.|-   [: Określanie dodatkowych opcji instrumentacji](../profiling/how-to-specify-additional-instrumentation-options.md)<br />-   [instrukcje: ograniczanie instrumentacji do określonych funkcji](../profiling/how-to-limit-instrumentation-to-specific-functions.md)<br />-   [VSInstr](../profiling/vsinstr.md)|
