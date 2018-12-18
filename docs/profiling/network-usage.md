---
title: Analizowanie użycia sieci w aplikacjach platformy UWP
ms.custom: seodec18
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 45fa397d-d7a1-4c4c-9c97-ede6c21643bd
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 06546e3d36e0568c27e4160342ad271a026b7b9e
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/07/2018
ms.locfileid: "53062247"
---
# <a name="analyze-network-usage-in-uwp-apps"></a>Analizowanie użycia sieci w aplikacjach platformy UWP
Visual Studio **sieci** narzędzie diagnostyczne zbiera dane dotyczące operacje sieciowe, wykonywane przy użyciu [Windows.Web.Http API](/uwp/api/windows.web.http). Analizowanie danych może pomóc rozwiązać problemy, takie jak problemy dostępu i uwierzytelniania, nieprawidłowe użycie pamięci podręcznej i wyświetlania jest niska i pobrać wydajności.  
  
 Narzędzie do sieci obsługuje tylko aplikacje platformy uniwersalnej systemu Windows. Inne platformy nie są obsługiwane w tej chwili.  
  
> [!NOTE]
>  Aby uzyskać bardziej szczegółowy opis narzędzie do sieci, zobacz [wprowadzenie do programu Visual Studio narzędzie sieci](https://blogs.msdn.microsoft.com/visualstudio/2015/05/04/introducing-visual-studios-network-tool/).  
  
## <a name="collect-network-tool-data"></a>Zbieranie danych narzędzie sieci  
 Należy uruchomić **sieci** narzędzie z otwartym projekcie programu Visual Studio na komputerze programu Visual Studio.  
  
1. Otwórz projekt w programie Visual Studio.  
  
2. W menu, kliknij polecenie **debugowanie / Profiler wydajności**. Wybierz **sieci**, a następnie wybierz **Start**.  
  
3. Narzędzie sieci rozpoczyna zbieranie ruch HTTP Twojej aplikacji.  
  
    Podczas uruchamiania aplikacji widok podsumowania w okienku po lewej stronie automatycznie wyświetla listę przechwyconych operacji HTTP. Wybierz element w widoku podsumowania, aby uzyskać więcej informacji, w okienku szczegółów w okienku po prawej stronie.  
  
4. Wybierz **zatrzymać** aby zamknąć aplikację.  
  
   Okno raportu powinna wyglądać mniej więcej tak:  
  
   ![Okno sieci](../profiling/media/network_fullwindow.png "NETWORK_FullWindow")  
  
## <a name="analyze-data"></a>Analizowanie danych  
 Można analizować przechwycone ruch HTTP, gdy Twoja aplikacja jest uruchomiona lub nawet w przypadku, po zamknięciu aplikacji, wybierając dowolną z operacji sieciowych wyświetlany w widoku podsumowania.  
  
 **Sieci** widok podsumowania pokazuje dane dla każdej operacji sieciowej podczas uruchomienia aplikacji. Wybierz nagłówek kolumny, aby posortować listę, lub wybierz typy zawartości do wyświetlenia w **Content Type** filtrowania widoku.  
  
 Wybierz **Zapisz jako plik HAR** do utworzenia pliku JSON, który może być używana przez narzędzia innych producentów, takie jak Fiddler.  
  
 **Sieci** widoków szczegółów zawiera więcej informacji na temat operacji sieciowej w widoku podsumowania.  
  
 ![Okienko szczegółów narzędzie sieci](../profiling/media/network_detailsviewpane.png "NETWORK_DetailsViewPane")  
  
|||  
|-|-|  
|**Nagłówki**|Informacje o nagłówku żądania zdarzenia.|  
|**Body**|Dane ładunku żądania i odpowiedzi.|  
|**Parametry**|Nazwy parametrów ciągu zapytania i wartości.|  
|**Plik cookie**|Dane pliku cookie odpowiedzi i żądania.|  
|**Chronometraż**|Wykres etapów w ramach pobieranie wybranych zasobów.|  
  
 Sieć **podsumowania** pasek pokazuje liczbę operacji sieciowych, które są wyświetlane na dowolnym etapie, ile danych zostało przeniesione, ile czasu zajęło Pobierz je oraz ile błędy (liczba żądań z odpowiedziami 4xx lub 5xx) widoczne.  
  
### <a name="analysis-tips"></a>Wskazówki dotyczące analizy  
 To narzędzie wyróżnione niektóre obszary, które mogą być przydatne podczas korzystania z analizy związanych z siecią:  
  
1.  Żądania, które są w pełni obsługiwane z pamięci podręcznej są wyświetlane jako **(z pamięci podręcznej)** w **odebrane** kolumny. To może pomóc w określeniu, czy używasz pamięci podręcznej skutecznie aby oszczędzić przepustowość użytkownika lub tego, czy buforowanie odpowiedzi przez pomyłkę i podając użytkowników końcowych w aplikacji za pomocą nieaktualne dane.  
  
2.  Odpowiedzi na błędy (4xx lub 5xx) są wyświetlane w **wyniki** kolumny z czerwonym oznaczeniem stanu kodu i są również wyróżnione na pasku podsumowania. Dzięki temu ułatwiają błędów między wiele potencjalnych żądań w swojej aplikacji.  
  
3.  Przycisk Drukowanie pretty odpowiedzi (wewnątrz karta Treść) może pomóc w przeanalizować za pomocą formatu JSON, XML, HTML, CSS, JavaScript i TypeScript ładunków odpowiedzi przez zwiększenie czytelności zawartości.  
  
## <a name="see-also"></a>Zobacz także  
 [Uruchamianie narzędzi profilowania z debugerem lub bez debugera](../profiling/running-profiling-tools-with-or-without-the-debugger.md)  
 [Blog dotyczący programu Visual Studio: Inspektor sieci wprowadzenie do programu Visual Studio](http://go.microsoft.com/fwlink/?LinkId=535022)   
 [Wideo Channel 9: Narzędzia diagnostyczne programu VS — nowy Profiler sieci](https://channel9.msdn.com/Series/ConnectOn-Demand/206)  
 [Profilowanie w programie Visual Studio](../profiling/index.md)  
 [Pierwsze spojrzenie na narzędziach profilowania](../profiling/profiling-feature-tour.md)
