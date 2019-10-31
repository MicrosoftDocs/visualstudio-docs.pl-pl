---
title: Analizowanie użycia sieci w aplikacjach platformy UWP
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
ms.sourcegitcommit: bdccab4c2dbd50ea8adaaf88c69c9ca32db88099
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73144701"
---
# <a name="analyze-network-usage-in-uwp-apps"></a>Analizowanie użycia sieci w aplikacjach platformy UWP
Narzędzie Diagnostyka **sieci** programu Visual Studio zbiera dane dotyczące operacji sieciowych wykonywanych przy użyciu [interfejsu API Windows. Web. http](/uwp/api/windows.web.http). Analizowanie danych może pomóc w rozwiązywaniu problemów, takich jak problemy z dostępem i uwierzytelnianiem, niepoprawna pamięć podręczna oraz niska wydajność wyświetlania i pobierania.

 Narzędzie sieciowe obsługuje tylko aplikacje platformy UWP. Inne platformy nie są w tej chwili obsługiwane.

> [!NOTE]
> Aby zapoznać się z bardziej szczegółowym opisem narzędzia sieci, zobacz [wprowadzenie do narzędzia sieci programu Visual Studio](https://devblogs.microsoft.com/visualstudio/introducing-visual-studios-network-tool/).

## <a name="collect-network-tool-data"></a>Zbieranie danych narzędzia sieciowego
 Należy uruchomić narzędzie **sieciowe** z otwartym projektem programu Visual Studio na komputerze z programem Visual Studio.

1. Otwórz projekt w programie Visual Studio.

2. W menu kliknij pozycję **Debuguj/Performance Profiler**. Wybierz pozycję **Sieć**, a następnie wybierz pozycję **Uruchom**.

3. Narzędzie sieciowe rozpocznie zbieranie ruchu HTTP aplikacji.

    Po uruchomieniu aplikacji Widok podsumowania w okienku po lewej stronie automatycznie wyświetla listę przechwyconych operacji HTTP. Wybierz element w widoku Podsumowanie, aby wyświetlić więcej informacji w panelu Szczegóły w okienku po prawej stronie.

4. Wybierz pozycję **Zatrzymaj** , aby zamknąć aplikację.

   Okno raportu powinno wyglądać następująco:

   ![Okno sieci](../profiling/media/network_fullwindow.png "NETWORK_FullWindow")

## <a name="analyze-data"></a>Analizowanie danych
 Przechwycony ruch HTTP można analizować, gdy aplikacja jest uruchomiona, a nawet po zamknięciu aplikacji, wybierając dowolną z operacji sieciowych wyświetlanych w widoku Podsumowanie.

 Widok Podsumowanie **sieci** przedstawia dane dla każdej operacji sieciowej w uruchomieniu aplikacji. Wybierz nagłówek kolumny, aby posortować listę, lub wybierz typy zawartości, które mają być wyświetlane w widoku filtr **typu zawartości** .

 Wybierz pozycję **Zapisz jako Har** , aby utworzyć plik JSON, który może być używany przez narzędzia innych firm, takie jak programu Fiddler.

 Widoki szczegóły **sieci** wyświetlają więcej informacji o operacji sieciowej w widoku Podsumowanie.

 ![Okienko szczegółów narzędzia sieciowego](../profiling/media/network_detailsviewpane.png "NETWORK_DetailsViewPane")

|||
|-|-|
|**Nagłówka**|Informacje o nagłówkach żądań zdarzenia.|
|**Jednostce**|Dane ładunku żądania i odpowiedzi.|
|**Parametry**|Nazwy i wartości parametrów ciągu zapytania.|
|**Plik cookie**|Odpowiedź i żądanie danych plików cookie.|
|**Chronometraż**|Wykres etapów pobierania wybranych zasobów.|

 Na pasku **podsumowania** sieci jest wyświetlana liczba operacji w sieci, które są wyświetlane w danym momencie, ilość transferowanych danych, czas ich pobrania oraz liczba błędów (żądań z odpowiedziami 4xx lub 5xx).

### <a name="analysis-tips"></a>Porady dotyczące analizy
 To narzędzie wyróżnia pewne obszary, które mogą być przydatne podczas przeprowadzania analizy związanej z siecią:

1. Żądania, które są w pełni obsługiwane z pamięci podręcznej, są wyświetlane jako **(z pamięci podręcznej)** w kolumnie **odebrane** . Może to pomóc w ustaleniu, czy pamięć podręczna jest wydajnie używana do oszczędzania przepustowości użytkowników, czy też w przypadku buforowania odpowiedzi przez pomyłkę i dostarczenie użytkownikom końcowym aplikacji nieaktualnymi danymi.

2. Odpowiedzi na błędy (4xx lub 5xx) są wyświetlane w kolumnie **wyniki** z czerwonym kodem stanu i są również wyróżnione na pasku podsumowania. Dzięki temu można łatwo wyróżnić błędy między wieloma potencjalnymi żądaniami w aplikacji.

3. Przycisk "Łatwa drukowanie" odpowiedzi (na karcie Body) może pomóc w analizie danych w postaci notacji JSON, XML, HTML, CSS, JavaScript i języka TypeScript przez zwiększenie czytelności zawartości.

## <a name="see-also"></a>Zobacz także

- [Uruchamianie narzędzi profilowania z debugerem lub bez debugera](../profiling/running-profiling-tools-with-or-without-the-debugger.md)
- [Blog programu Visual Studio: wprowadzenie do Inspektora sieci programu Visual Studio](https://devblogs.microsoft.com/visualstudio/)
- [Wideo Channel 9: narzędzia diagnostyczne VS — Nowy Profiler sieci](https://channel9.msdn.com/Series/ConnectOn-Demand/206)
- [Profilowanie w programie Visual Studio](../profiling/index.yml)
- [Pierwsze spojrzenie na narzędzia profilowania](../profiling/profiling-feature-tour.md)