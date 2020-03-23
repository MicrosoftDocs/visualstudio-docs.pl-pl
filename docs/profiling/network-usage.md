---
title: Analizowanie użycia sieci w aplikacjach platformy uniwersalnej systemu Windows
ms.custom: seodec18
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 45fa397d-d7a1-4c4c-9c97-ede6c21643bd
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
monikerRange: vs-2017
ms.openlocfilehash: 16c17c6f39980b115b34869fdc6b4912ca94ab0b
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "73144701"
---
# <a name="analyze-network-usage-in-uwp-apps"></a>Analizowanie użycia sieci w aplikacjach platformy uniwersalnej systemu Windows
Narzędzie diagnostyczne usługi Visual Studio **Network** zbiera dane dotyczące operacji sieciowych wykonywanych za pomocą [interfejsu API windows.web.http](/uwp/api/windows.web.http). Analizowanie danych może pomóc w rozwiązaniu problemów, takich jak problemy z dostępem i uwierzytelnianiem, nieprawidłowe użycie pamięci podręcznej oraz niska wydajność wyświetlania i pobierania.

 Narzędzie Sieć obsługuje tylko aplikacje platformy uniwersalnej systemu Windows. Inne platformy nie są obecnie obsługiwane.

> [!NOTE]
> Aby uzyskać pełniejszy opis narzędzia Sieć, zobacz [Wprowadzenie narzędzia sieciowego programu Visual Studio](https://devblogs.microsoft.com/visualstudio/introducing-visual-studios-network-tool/).

## <a name="collect-network-tool-data"></a>Zbieranie danych narzędzia sieciowego
 Należy uruchomić narzędzie **sieć** z otwartym projektem programu Visual Studio na komputerze z programem Visual Studio.

1. Otwórz projekt w programie Visual Studio.

2. W menu kliknij przycisk **Debug / Profiler wydajności**. Wybierz pozycję **Sieć**, a następnie wybierz pozycję **Start**.

3. Narzędzie sieciowe rozpoczyna zbieranie ruchu HTTP aplikacji.

    Podczas uruchamiania aplikacji widok podsumowania w lewym okienku automatycznie wyświetla listę przechwyconych operacji HTTP. Wybierz element w widoku podsumowania, aby wyświetlić więcej informacji w panelu szczegółów w prawym okienku.

4. Wybierz **pozycję Zatrzymaj,** aby zamknąć aplikację.

   Okno raportu powinno wyglądać mniej więcej tak:

   ![Okno Sieć](../profiling/media/network_fullwindow.png "NETWORK_FullWindow")

## <a name="analyze-data"></a>Analizowanie danych
 Możesz analizować przechwycony ruch HTTP, gdy aplikacja jest uruchomiona, a nawet po zamknięciu aplikacji, wybierając dowolną z operacji sieciowych wyświetlanych w widoku podsumowania.

 Widok podsumowania **sieci** zawiera dane dla każdej operacji sieciowej w uruchomieniu aplikacji. Wybierz nagłówek kolumny, aby posortować listę, lub wybierz typy zawartości do wyświetlenia w widoku filtru **Typ zawartości.**

 Wybierz **zapisz jako HAR,** aby utworzyć plik JSON, który może być zużywany przez narzędzia innych firm, takie jak Fiddler.

 W widokach **Szczegóły sieci** są wyświetlane więcej informacji o operacji sieciowej w widoku podsumowania.

 ![Okienko szczegółów narzędzia sieciowego](../profiling/media/network_detailsviewpane.png "NETWORK_DetailsViewPane")

|||
|-|-|
|**Nagłówki**|Informacje o nagłówkach żądań zdarzenia.|
|**Treść**|Dane ładunku żądania i odpowiedzi.|
|**Parametry**|Nazwy i wartości parametrów ciągu kwerendy.|
|**Plik cookie**|Odpowiedzi i żądania danych cookie.|
|**Chronometraż**|Wykres etapów pozyskiwania wybranych zasobów.|

 Pasek **podsumowania** sieci pokazuje liczbę operacji sieciowych wyświetlanych w danym momencie, ilość przesłanych danych, czas ich pobrania i liczbę błędów (żądania z odpowiedziami 4xx lub 5xx).

### <a name="analysis-tips"></a>Wskazówki dotyczące analizy
 To narzędzie wyróżnia niektóre obszary, które mogą być przydatne podczas analizy związanej z siecią:

1. Żądania, które są w pełni obsługiwane z pamięci podręcznej są wyświetlane jako **(z pamięci podręcznej)** w **Odebrane** kolumny. Może to pomóc w określeniu, czy pamięć podręczna jest skutecznie obsługiwana do zapisywania przepustowości użytkownika, czy też buforowanie odpowiedzi przez pomyłkę i dostarczanie użytkownikowi końcowemu aplikacji nieaktualnych danych.

2. Odpowiedzi na błędy (4xx lub 5xx) są wyświetlane w kolumnie **Wyniki** z czerwonym kodem stanu i są również wyróżnione na pasku podsumowania. Ułatwia to wykrywanie błędów wśród wielu potencjalnych żądań w aplikacji.

3. Przycisk drukowania (wewnątrz karty treści) może pomóc w analizacji ładunków odpowiedzi JSON, XML, HTML, CSS, JavaScript i TypeScript, zwiększając czytelność zawartości.

## <a name="see-also"></a>Zobacz też

- [Uruchamianie narzędzi profilowania z debugerem lub bez debugera](../profiling/running-profiling-tools-with-or-without-the-debugger.md)
- [Blog programu Visual Studio: Wprowadzenie inspektora sieci programu Visual Studio](https://devblogs.microsoft.com/visualstudio/)
- [Kanał 9 Wideo: Narzędzia diagnostyczne VS - nowy profiler sieciowy](https://channel9.msdn.com/Series/ConnectOn-Demand/206)
- [Profilowanie w programie Visual Studio](../profiling/index.yml)
- [Pierwsze spojrzenie na narzędzia profilowania](../profiling/profiling-feature-tour.md)