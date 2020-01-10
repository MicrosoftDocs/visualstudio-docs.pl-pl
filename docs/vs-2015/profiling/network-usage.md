---
title: Użycie sieci | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 45fa397d-d7a1-4c4c-9c97-ede6c21643bd
caps.latest.revision: 12
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 6de07c705129aaef705d0c9651d53fdf35e6d0c0
ms.sourcegitcommit: c150d0be93b6f7ccbe9625b41a437541502560f5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/10/2020
ms.locfileid: "75850748"
---
# <a name="network-usage"></a>Użycie sieci
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio **sieci** narzędzie diagnostyczne zbiera dane dotyczące operacje sieciowe, wykonywane przy użyciu [Windows.Web.Http API](https://msdn.microsoft.com/library/windows/apps/windows.web.http.aspx). Analizowanie danych może pomóc rozwiązać problemy, takie jak problemy dostępu i uwierzytelniania, nieprawidłowe użycie pamięci podręcznej i wyświetlania jest niska i pobrać wydajności.  
  
 Narzędzie sieciowe obsługuje tylko aplikacje platformy uniwersalnej systemu Windows. Inne platformy nie są obsługiwane w tej chwili.  
  
> [!NOTE]
> Aby zapoznać się z bardziej szczegółowym opisem narzędzia sieci, zobacz [wprowadzenie do narzędzia sieci programu Visual Studio](https://devblogs.microsoft.com/visualstudio/?m=20155).  
  
## <a name="collecting-network-tool-data"></a>Zbieranie danych narzędzia sieciowego  
 Należy uruchomić **sieci** narzędzie z otwartym projekcie programu Visual Studio na komputerze programu Visual Studio.  
  
1. Otwórz projekt w programie Visual Studio.  
  
2. W menu kliknij pozycję **Debuguj/Performance Profiler..** .. Wybierz pozycję **Sieć**, a następnie wybierz pozycję **Uruchom**.  
  
3. Narzędzie sieciowe rozpocznie zbieranie ruchu HTTP aplikacji.  
  
    Podczas uruchamiania aplikacji widok podsumowania w okienku po lewej stronie automatycznie wyświetla listę przechwyconych operacji HTTP. Wybierz element w widoku podsumowania, aby uzyskać więcej informacji, w okienku szczegółów w okienku po prawej stronie.  
  
4. Wybierz **zatrzymać** aby zamknąć aplikację.  
  
   Okno raportu powinno wyglądać następująco:  
  
   ![Okno sieci](../profiling/media/network-fullwindow.png "NETWORK_FullWindow")  
  
## <a name="analyzing-data"></a>Analizowanie danych  
 Można analizować przechwycone ruch HTTP, gdy Twoja aplikacja jest uruchomiona lub nawet w przypadku, po zamknięciu aplikacji, wybierając dowolną z operacji sieciowych wyświetlany w widoku podsumowania.  
  
 **Sieci** widok podsumowania pokazuje dane dla każdej operacji sieciowej podczas uruchomienia aplikacji. Wybierz nagłówek kolumny, aby posortować listę, lub wybierz typy zawartości do wyświetlenia w **Content Type** filtrowania widoku.  
  
 Wybierz **Zapisz jako plik HAR** do utworzenia pliku JSON, który może być używana przez narzędzia innych producentów, takie jak Fiddler.  
  
 **Sieci** widoków szczegółów zawiera więcej informacji na temat operacji sieciowej w widoku podsumowania.  
  
 ![Okienko szczegółów narzędzia sieciowego](../profiling/media/network-detailsviewpane.png "NETWORK_DetailsViewPane")  
  
|||  
|-|-|  
|**Nagłówki**|Informacje o nagłówku żądania zdarzenia.|  
|**Body**|Dane ładunku żądania i odpowiedzi.|  
|**Parametry**|Nazwy parametrów ciągu zapytania i wartości.|  
|**Plik cookie**|Dane pliku cookie odpowiedzi i żądania.|  
|**Chronometraż**|Wykres etapów w ramach pobieranie wybranych zasobów.|  
  
 Sieć **podsumowania** pasek pokazuje liczbę operacji sieciowych, które są wyświetlane na dowolnym etapie, ile danych zostało przeniesione, ile czasu zajęło Pobierz je oraz ile błędy (liczba żądań z odpowiedziami 4xx lub 5xx) widoczne.  
  
### <a name="analysis-tips"></a>Wskazówki dotyczące analizy  
 To narzędzie wyróżnia pewne obszary, które mogą być przydatne w przypadku uruchamiania analizy związanej z siecią:  
  
1. Żądania, które są w pełni obsługiwane z pamięci podręcznej są wyświetlane jako **(z pamięci podręcznej)** w **odebrane** kolumny. To może pomóc w określeniu, czy używasz pamięci podręcznej skutecznie aby oszczędzić przepustowość użytkownika lub tego, czy buforowanie odpowiedzi przez pomyłkę i podając użytkowników końcowych w aplikacji za pomocą nieaktualne dane.  
  
2. Odpowiedzi na błędy (4xx lub 5xx) są wyświetlane w kolumnie **wyniki** z czerwonym kodem stanu i są również wyróżnione na pasku podsumowania. Dzięki temu ułatwiają błędów między wiele potencjalnych żądań w swojej aplikacji.  
  
3. Przycisk "Łatwa drukowanie" odpowiedzi (na karcie Body) może pomóc w analizie danych w postaci JSON, XML, HTML, CSS, JavaScript i języka TypeScript, zwiększając czytelność zawartości.  
  
## <a name="see-also"></a>Zobacz też  
 [Uruchom narzędzia profilowania bez debugowania](https://msdn.microsoft.com/library/e97ce1a4-62d6-4b8e-a2f7-61576437ff01)   
 [Blog programu Visual Studio: wprowadzenie do Inspektora sieci programu Visual studio](https://blogs.msdn.com/b/visualstudio/)   
 [Wideo Channel 9: narzędzia diagnostyczne VS — Nowy Profiler sieci](https://channel9.msdn.com/Series/ConnectOn-Demand/206)
