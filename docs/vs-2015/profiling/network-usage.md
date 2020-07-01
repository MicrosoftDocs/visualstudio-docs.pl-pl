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
ms.openlocfilehash: 20f7003bbcd319a6a8487d496697d3dcd0b7a18a
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/30/2020
ms.locfileid: "85548424"
---
# <a name="network-usage"></a>Użycie sieci
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Narzędzie Diagnostyka **sieci** programu Visual Studio zbiera dane dotyczące operacji sieciowych wykonywanych przy użyciu [interfejsu API Windows. Web. http](https://msdn.microsoft.com/library/windows/apps/windows.web.http.aspx). Analizowanie danych może pomóc w rozwiązywaniu problemów, takich jak problemy z dostępem i uwierzytelnianiem, niepoprawna pamięć podręczna oraz niska wydajność wyświetlania i pobierania.  
  
 Narzędzie sieciowe obsługuje tylko aplikacje platformy uniwersalnej systemu Windows. Inne platformy nie są w tej chwili obsługiwane.  
  
> [!NOTE]
> Aby zapoznać się z bardziej szczegółowym opisem narzędzia sieci, zobacz [wprowadzenie do narzędzia sieci programu Visual Studio](https://devblogs.microsoft.com/visualstudio/?m=20155).  
  
## <a name="collecting-network-tool-data"></a>Zbieranie danych narzędzia sieciowego  
 Należy uruchomić narzędzie **sieciowe** z otwartym projektem programu Visual Studio na komputerze z programem Visual Studio.  
  
1. Otwórz projekt w programie Visual Studio.  
  
2. W menu kliknij pozycję **Debuguj/Performance Profiler..**.. Wybierz pozycję **Sieć**, a następnie wybierz pozycję **Uruchom**.  
  
3. Narzędzie sieciowe rozpocznie zbieranie ruchu HTTP aplikacji.  
  
    Po uruchomieniu aplikacji Widok podsumowania w okienku po lewej stronie automatycznie wyświetla listę przechwyconych operacji HTTP. Wybierz element w widoku Podsumowanie, aby wyświetlić więcej informacji w panelu Szczegóły w okienku po prawej stronie.  
  
4. Wybierz pozycję **Zatrzymaj** , aby zamknąć aplikację.  
  
   Okno raportu powinno wyglądać następująco:  
  
   ![Okno sieci](../profiling/media/network-fullwindow.png "NETWORK_FullWindow")  
  
## <a name="analyzing-data"></a>Analizowanie danych  
 Przechwycony ruch HTTP można analizować, gdy aplikacja jest uruchomiona, a nawet po zamknięciu aplikacji, wybierając dowolną z operacji sieciowych wyświetlanych w widoku Podsumowanie.  
  
 Widok Podsumowanie **sieci** przedstawia dane dla każdej operacji sieciowej w uruchomieniu aplikacji. Wybierz nagłówek kolumny, aby posortować listę, lub wybierz typy zawartości, które mają być wyświetlane w widoku filtr **typu zawartości** .  
  
 Wybierz pozycję **Zapisz jako Har** , aby utworzyć plik JSON, który może być używany przez narzędzia innych firm, takie jak programu Fiddler.  
  
 Widoki szczegóły **sieci** wyświetlają więcej informacji o operacji sieciowej w widoku Podsumowanie.  
  
 ![Okienko szczegółów narzędzia sieciowego](../profiling/media/network-detailsviewpane.png "NETWORK_DetailsViewPane")  
  
|Nazwa|Opis|  
|-|-|  
|**Nagłówki**|Informacje o nagłówkach żądań zdarzenia.|  
|**Treść**|Dane ładunku żądania i odpowiedzi.|  
|**Parametry**|Nazwy i wartości parametrów ciągu zapytania.|  
|**Plik cookie**|Odpowiedź i żądanie danych plików cookie.|  
|**Chronometraż**|Wykres etapów pobierania wybranych zasobów.|  
  
 Na pasku **podsumowania** sieci jest wyświetlana liczba operacji w sieci, które są wyświetlane w danym momencie, ilość transferowanych danych, czas ich pobrania oraz liczba błędów (żądań z odpowiedziami 4xx lub 5xx).  
  
### <a name="analysis-tips"></a>Porady dotyczące analizy  
 To narzędzie wyróżnia pewne obszary, które mogą być przydatne w przypadku uruchamiania analizy związanej z siecią:  
  
1. Żądania, które są w pełni obsługiwane z pamięci podręcznej, są wyświetlane jako **(z pamięci podręcznej)** w kolumnie **odebrane** . Może to pomóc w ustaleniu, czy pamięć podręczna jest wydajnie używana do oszczędzania przepustowości użytkowników, czy też w przypadku buforowania odpowiedzi przez pomyłkę i dostarczenie użytkownikom końcowym aplikacji nieaktualnymi danymi.  
  
2. Odpowiedzi na błędy (4xx lub 5xx) są wyświetlane w kolumnie **wyniki** z czerwonym kodem stanu i są również wyróżnione na pasku podsumowania. Dzięki temu można łatwo wyróżnić błędy między wieloma potencjalnymi żądaniami w aplikacji.  
  
3. Przycisk "Łatwa drukowanie" odpowiedzi (na karcie Body) może pomóc w analizie danych w postaci JSON, XML, HTML, CSS, JavaScript i języka TypeScript, zwiększając czytelność zawartości.  
  
## <a name="see-also"></a>Zobacz też  
 [Uruchamianie narzędzi profilowania bez debugowania](https://msdn.microsoft.com/library/e97ce1a4-62d6-4b8e-a2f7-61576437ff01)   
 [Blog programu Visual Studio: wprowadzenie do Inspektora sieci programu Visual Studio](https://blogs.msdn.com/b/visualstudio/)   
 [Wideo Channel 9: narzędzia diagnostyczne VS — Nowy Profiler sieci](https://channel9.msdn.com/Series/ConnectOn-Demand/206)
