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
ms.openlocfilehash: eed389a3847145a0f37eb3141526a38e4374d368
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2019
ms.locfileid: "74297908"
---
# <a name="network-usage"></a>Użycie sieci
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Narzędzie Diagnostyka **sieci** programu Visual Studio zbiera dane dotyczące operacji sieciowych wykonywanych przy użyciu [interfejsu API Windows. Web. http](https://msdn.microsoft.com/library/windows/apps/windows.web.http.aspx). Analizowanie danych może pomóc rozwiązać problemy, takie jak problemy dostępu i uwierzytelniania, nieprawidłowe użycie pamięci podręcznej i wyświetlania jest niska i pobrać wydajności.  
  
 Narzędzie sieciowe obsługuje tylko aplikacje platformy uniwersalnej systemu Windows. Inne platformy nie są obsługiwane w tej chwili.  
  
> [!NOTE]
> Aby zapoznać się z bardziej szczegółowym opisem narzędzia sieci, zobacz [wprowadzenie do narzędzia sieci programu Visual Studio](https://devblogs.microsoft.com/visualstudio/?m=20155).  
  
## <a name="collecting-network-tool-data"></a>Zbieranie danych narzędzia sieciowego  
 Należy uruchomić narzędzie **sieciowe** z otwartym projektem programu Visual Studio na komputerze z programem Visual Studio.  
  
1. Otwórz projekt w programie Visual Studio.  
  
2. W menu kliknij pozycję **Debuguj/Performance Profiler..** .. Wybierz pozycję **Sieć**, a następnie wybierz pozycję **Uruchom**.  
  
3. Narzędzie sieciowe rozpocznie zbieranie ruchu HTTP aplikacji.  
  
    Podczas uruchamiania aplikacji widok podsumowania w okienku po lewej stronie automatycznie wyświetla listę przechwyconych operacji HTTP. Wybierz element w widoku podsumowania, aby uzyskać więcej informacji, w okienku szczegółów w okienku po prawej stronie.  
  
4. Wybierz pozycję **Zatrzymaj** , aby zamknąć aplikację.  
  
   Okno raportu powinno wyglądać następująco:  
  
   ![Okno sieci](../profiling/media/network-fullwindow.png "NETWORK_FullWindow")  
  
## <a name="analyzing-data"></a>Analizowanie danych  
 Można analizować przechwycone ruch HTTP, gdy Twoja aplikacja jest uruchomiona lub nawet w przypadku, po zamknięciu aplikacji, wybierając dowolną z operacji sieciowych wyświetlany w widoku podsumowania.  
  
 Widok Podsumowanie **sieci** przedstawia dane dla każdej operacji sieciowej w uruchomieniu aplikacji. Wybierz nagłówek kolumny, aby posortować listę, lub wybierz typy zawartości, które mają być wyświetlane w widoku filtr **typu zawartości** .  
  
 Wybierz pozycję **Zapisz jako Har** , aby utworzyć plik JSON, który może być używany przez narzędzia innych firm, takie jak programu Fiddler.  
  
 Widoki szczegóły **sieci** wyświetlają więcej informacji o operacji sieciowej w widoku Podsumowanie.  
  
 ![Okienko szczegółów narzędzia sieciowego](../profiling/media/network-detailsviewpane.png "NETWORK_DetailsViewPane")  
  
|||  
|-|-|  
|**Nagłówka**|Informacje o nagłówku żądania zdarzenia.|  
|**Jednostce**|Dane ładunku żądania i odpowiedzi.|  
|**Parametry**|Nazwy parametrów ciągu zapytania i wartości.|  
|**Plik cookie**|Dane pliku cookie odpowiedzi i żądania.|  
|**Chronometraż**|Wykres etapów w ramach pobieranie wybranych zasobów.|  
  
 Na pasku **podsumowania** sieci jest wyświetlana liczba operacji w sieci, które są wyświetlane w danym momencie, ilość transferowanych danych, czas ich pobrania oraz liczba błędów (żądań z odpowiedziami 4xx lub 5xx).  
  
### <a name="analysis-tips"></a>Wskazówki dotyczące analizy  
 To narzędzie wyróżnia pewne obszary, które mogą być przydatne w przypadku uruchamiania analizy związanej z siecią:  
  
1. Żądania, które są w pełni obsługiwane z pamięci podręcznej, są wyświetlane jako **(z pamięci podręcznej)** w kolumnie **odebrane** . To może pomóc w określeniu, czy używasz pamięci podręcznej skutecznie aby oszczędzić przepustowość użytkownika lub tego, czy buforowanie odpowiedzi przez pomyłkę i podając użytkowników końcowych w aplikacji za pomocą nieaktualne dane.  
  
2. Odpowiedzi na błędy (4xx lub 5xx) są wyświetlane w kolumnie **wyniki** z czerwonym kodem stanu i są również wyróżnione na pasku podsumowania. Dzięki temu ułatwiają błędów między wiele potencjalnych żądań w swojej aplikacji.  
  
3. Przycisk "Łatwa drukowanie" odpowiedzi (na karcie Body) może pomóc w analizie danych w postaci JSON, XML, HTML, CSS, JavaScript i języka TypeScript, zwiększając czytelność zawartości.  
  
## <a name="see-also"></a>Zobacz też  
 [Uruchom narzędzia profilowania bez debugowania](https://msdn.microsoft.com/library/e97ce1a4-62d6-4b8e-a2f7-61576437ff01)   
 [Blog programu Visual Studio: wprowadzenie do Inspektora sieci programu Visual studio](https://go.microsoft.com/fwlink/?LinkId=535022)   
 [Wideo Channel 9: narzędzia diagnostyczne VS — Nowy Profiler sieci](https://channel9.msdn.com/Series/ConnectOn-Demand/206)
