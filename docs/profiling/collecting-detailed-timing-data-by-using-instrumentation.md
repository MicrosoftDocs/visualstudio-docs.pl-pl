---
title: Zbieranie szczegółowych danych o chronometrażu przy użyciu instrumentacji
description: Użyj metody instrumentacji narzędzia profilowania, aby uzyskać szczegółowe informacje o chronometrażu w sekcji kodu i zrozumieć wpływ operacji we/wy.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- Profiling Tools,instrumentation method
- instrumentation profiling method
ms.assetid: e9deb370-c459-45ac-84d3-14d646590d05
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: ecdbc5c3b94e83f0b8d38cec161f94a65e64fdf4
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99868310"
---
# <a name="collect-detailed-timing-data-by-using-instrumentation"></a>Zbieranie szczegółowych danych o chronometrażu przy użyciu instrumentacji
[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]Metoda narzędzia profilowania Instrumentation wprowadza kod profilowania do kopii modułu. Kod rejestruje każde wejście, wyjście i wywołanie funkcji funkcji w module podczas przebiegu profilowania. Metoda Instrumentacji jest przydatna do gromadzenia szczegółowych informacji o chronometrażu w sekcji kodu oraz do poznania wpływu operacji wejścia i wyjścia na wydajność aplikacji.

 Metodę Instrumentacji można określić za pomocą jednej z następujących procedur:

- Na pierwszej stronie kreatora profilowania wybierz pozycję **Instrumentacja**.

- Na **Eksplorator wydajności** pasku narzędzi na liście **Metoda** kliknij pozycję **Instrumentacja**.

- Na stronie **Ogólne** okna dialogowego właściwości dla sesji wydajności Wybierz pozycję **Instrumentacja**.

## <a name="common-tasks"></a>Typowe zadania
 Dodatkowe opcje można określić w oknie dialogowym **strony właściwości** sesji wydajności. Aby otworzyć to okno dialogowe:

- W **Eksplorator wydajności** kliknij prawym przyciskiem myszy nazwę sesji wydajności, a następnie kliknij polecenie **Właściwości**.

  Zadania w poniższej tabeli zawierają opis opcji, które można określić w oknie dialogowym **strony właściwości** _sesji wydajności_ podczas profilowania przy użyciu metody instrumentacji.

|Zadanie|Powiązana zawartość|
|----------|---------------------|
|Na stronie **Ogólne** Dodaj dane alokacji pamięci .NET i okresu istnienia, a następnie określ szczegóły nazewnictwa wygenerowanego pliku danych profilowania (. vsp).|-   [Zbierz dane alokacji pamięci .NET i okresu istnienia](../profiling/collecting-dotnet-memory-allocation-and-lifetime-data.md)<br />-   [Instrukcje: Ustawianie opcji nazwy pliku danych wydajności](../profiling/how-to-set-performance-data-file-name-options.md)|
|Na stronie **Uruchamianie** , jeśli w rozwiązaniu masz wiele projektów. exe. Określ aplikację do uruchomienia i ich kolejność uruchamiania.|-   [Instrukcje: Określanie pliku binarnego do uruchomienia](../profiling/how-to-specify-the-binary-to-start.md)|
|Na stronie **pliki binarne** Określ lokalizację przynoszącą instrumentację kopii modułów. Domyślnie oryginalne pliki binarne są przenoszone do folderu kopii zapasowej.|-   [Instrukcje: Zmienianie położenia plików binarnych z instrumentacją](../profiling/how-to-relocate-instrumented-binaries.md)|
|Na stronie **interakcja warstwy** Dodaj dane wywołania ADO.NET do przebiegu profilowania.|-   [Zbierz dane interakcji warstwy](../profiling/collecting-tier-interaction-data.md)|
|Na stronie **Instrumentacja** Wyklucz małe funkcje z profilowania, aby zmniejszyć obciążenie profilowania, kod JavaScript profilu w ASP.NET stronach sieci Web i określić polecenia do uruchomienia w wierszu polecenia przed i po procesie Instrumentacji.|-   [Instrukcje: wykluczanie lub uwzględnianie krótkich funkcji z Instrumentacji](../profiling/how-to-exclude-or-include-short-functions-from-instrumentation.md)<br />-   [Instrukcje: profilowanie kodu JavaScript na stronach sieci Web](../profiling/how-to-profile-javascript-code-in-web-pages.md)<br />-   [Instrukcje: Określanie poleceń przed i po Instrumentacji](../profiling/how-to-specify-pre-and-post-instrument-commands.md)|
|Na stronie **liczniki procesora** Określ co najmniej jeden licznik wydajności procesora, który ma zostać dodany do danych profilowania.|-   [Instrukcje: zbieranie danych licznika procesora CPU](../profiling/how-to-collect-cpu-counter-data.md)|
|Na stronie **zdarzenia systemu Windows** wybierz jedno lub więcej zdarzeń śledzenia zdarzeń systemu Windows (ETW), które mają być zbierane z danymi próbkowania.|-   [Instrukcje: zbieranie danych śledzenia zdarzeń dla systemu Windows (ETW)](../profiling/how-to-collect-event-tracing-for-windows-etw-data.md)|
|Na stronie **liczniki systemu Windows** Określ co najmniej jeden licznik wydajności systemu operacyjnego, który ma zostać dodany do danych profilowania jako znaczniki.|-   [Instrukcje: zbieranie danych licznika systemu Windows](../profiling/how-to-collect-windows-counter-data.md)|
|Na stronie **Zaawansowane** określ wszelkie dodatkowe opcje, które chcesz przekazać do programu Instrumentacji VSInstr, takie jak opcje dołączania lub wykluczania określonych funkcji.|-   [Instrukcje: Określanie dodatkowych opcji instrumentacji](../profiling/how-to-specify-additional-instrumentation-options.md)<br />-   [Instrukcje: ograniczanie instrumentacji do określonych funkcji](../profiling/how-to-limit-instrumentation-to-specific-functions.md)<br />-   [VSInstr](../profiling/vsinstr.md)|
