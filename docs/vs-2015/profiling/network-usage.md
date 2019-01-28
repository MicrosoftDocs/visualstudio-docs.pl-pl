---
title: Użycie sieci | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 45fa397d-d7a1-4c4c-9c97-ede6c21643bd
caps.latest.revision: 12
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: b2a411a135330fbf36bde9b28f8015e96a4555c3
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54759912"
---
# <a name="network-usage"></a>Użycie sieci
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio **sieci** narzędzie diagnostyczne zbiera dane dotyczące operacje sieciowe, wykonywane przy użyciu [Windows.Web.Http API](https://msdn.microsoft.com/library/windows/apps/windows.web.http.aspx). Analizowanie danych może pomóc rozwiązać problemy, takie jak problemy dostępu i uwierzytelniania, nieprawidłowe użycie pamięci podręcznej i wyświetlania jest niska i pobrać wydajności.  
  
 Narzędzie do sieci obsługuje tylko platformy Universal Windows apps. Inne platformy nie są obsługiwane w tej chwili.  
  
> [!NOTE]
>  Aby uzyskać bardziej szczegółowy opis narzędzie do sieci, zobacz [wprowadzenie do programu Visual Studio narzędzie sieci](http://blogs.msdn.com/b/visualstudio/archive/2015/05/04/introducing-visual-studio-s-network-tool.aspx).  
  
## <a name="collecting-network-tool-data"></a>Zbieranie danych z narzędzia do sieci  
 Należy uruchomić **sieci** narzędzie z otwartym projekcie programu Visual Studio na komputerze programu Visual Studio.  
  
1. Otwórz projekt w programie Visual Studio.  
  
2. W menu, kliknij polecenie **debugowanie / Profiler wydajności...** . Wybierz **sieci**, a następnie wybierz **Start**.  
  
3. Narzędzie sieci rozpoczyna zbieranie ruch HTTP Twojej aplikacji.  
  
    Podczas uruchamiania aplikacji widok podsumowania w okienku po lewej stronie automatycznie wyświetla listę przechwyconych operacji HTTP. Wybierz element w widoku podsumowania, aby uzyskać więcej informacji, w okienku szczegółów w okienku po prawej stronie.  
  
4. Wybierz **zatrzymać** aby zamknąć aplikację.  
  
   W oknie Raport powinien wyglądać mniej więcej tak:  
  
   ![Okno sieci](../profiling/media/network-fullwindow.png "NETWORK_FullWindow")  
  
## <a name="analyzing-data"></a>Analizowanie danych  
 Można analizować przechwycone ruch HTTP, gdy Twoja aplikacja jest uruchomiona lub nawet w przypadku, po zamknięciu aplikacji, wybierając dowolną z operacji sieciowych wyświetlany w widoku podsumowania.  
  
 **Sieci** widok podsumowania pokazuje dane dla każdej operacji sieciowej podczas uruchomienia aplikacji. Wybierz nagłówek kolumny, aby posortować listę, lub wybierz typy zawartości do wyświetlenia w **Content Type** filtrowania widoku.  
  
 Wybierz **Zapisz jako plik HAR** do utworzenia pliku JSON, który może być używana przez narzędzia innych producentów, takie jak Fiddler.  
  
 **Sieci** widoków szczegółów zawiera więcej informacji na temat operacji sieciowej w widoku podsumowania.  
  
 ![Okienko szczegółów narzędzie sieci](../profiling/media/network-detailsviewpane.png "NETWORK_DetailsViewPane")  
  
|||  
|-|-|  
|**Nagłówki**|Informacje o nagłówku żądania zdarzenia.|  
|**Body**|Dane ładunku żądania i odpowiedzi.|  
|**Parametry**|Nazwy parametrów ciągu zapytania i wartości.|  
|**Plik cookie**|Dane pliku cookie odpowiedzi i żądania.|  
|**Chronometraż**|Wykres etapów w ramach pobieranie wybranych zasobów.|  
  
 Sieć **podsumowania** pasek pokazuje liczbę operacji sieciowych, które są wyświetlane na dowolnym etapie, ile danych zostało przeniesione, ile czasu zajęło Pobierz je oraz ile błędy (liczba żądań z odpowiedziami 4xx lub 5xx) widoczne.  
  
### <a name="analysis-tips"></a>Wskazówki dotyczące analizy  
 Najważniejsze funkcje to narzędzie, które niektóre obszary, które mogą być przydatne, gdy uruchamiasz sieci powiązane analizy:  
  
1.  Żądania, które są w pełni obsługiwane z pamięci podręcznej są wyświetlane jako **(z pamięci podręcznej)** w **odebrane** kolumny. To może pomóc w określeniu, czy używasz pamięci podręcznej skutecznie aby oszczędzić przepustowość użytkownika lub tego, czy buforowanie odpowiedzi przez pomyłkę i podając użytkowników końcowych w aplikacji za pomocą nieaktualne dane.  
  
2.  W odpowiedzi na błędy (4xx lub 5xx) są wyświetlane w **wyniki** kolumny z czerwonym oznaczeniem stanu kodu i są również wyróżnione na pasku podsumowania. Dzięki temu ułatwiają błędów między wiele potencjalnych żądań w swojej aplikacji.  
  
3.  Przycisk Drukowanie pretty odpowiedzi (wewnątrz karta Treść) może pomóc w przeanalizować za pomocą formatu JSON, XML, HTML, CSS, JavaScript i TypeScript ładunków odpowiedzi przez zwiększenie czytelności zawartości.  
  
## <a name="see-also"></a>Zobacz też  
 [Uruchamianie narzędzi profilowania bez debugowania](http://msdn.microsoft.com/library/e97ce1a4-62d6-4b8e-a2f7-61576437ff01)   
 [Visual Studio blog: Wprowadzenie do programu Visual Studio, inspektor sieci](http://go.microsoft.com/fwlink/?LinkId=535022)   
 [Wideo Channel 9: Narzędzia diagnostyczne VS — nowy Profiler sieci](http://channel9.msdn.com/Series/ConnectOn-Demand/206)
