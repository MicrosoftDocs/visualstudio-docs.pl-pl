---
title: Dokument dziennika grafiki | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.graphics.vsglog.error
- vs.graphics.experiment
- vs.graphics.vsglog
ms.assetid: 6ccb1269-d55f-49c4-920d-baedf7de2888
caps.latest.revision: 34
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 097f431446ed2148e2a61c6f85266843fe7ada44
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51745170"
---
# <a name="graphics-log-document"></a>Dokument dziennika grafiki
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Dokument dziennika grafiki jest rekord zdarzenia grafiki, które wystąpiły, gdy aplikacja została uruchomiona w ramach sesji diagnostyki grafiki. Po rejestrowane, można sprawdzić dziennik w analizatora grafiki programu Visual Studio do diagnozowania problemów z renderowaniem i wydajności.  
  
 Jest to, jakie dokument dziennika grafiki wygląda w analizatorze grafiki domen:  
  
 ![Dziennik grafiki zawierający dwa przechwyconych klatek. ](../debugger/media/gfx-diag-demo-graphics-log-orientation.png "gfx_diag_demo_graphics_log_orientation")  
  
## <a name="understanding-graphics-log-documents"></a>Dokumenty dziennika grafiki opis  
 Za pomocą analizatora grafiki do zbadania dokument dziennika grafiki, można wizualizować skutków zdarzenia Direct3D dla obiektu docelowego renderowania, który wystąpił podczas przechwytywania. Można wyznaczyć regiony obiektu docelowego renderowania, które zawierają nieoczekiwane dane wyjściowe. Po wybraniu piksel w regionie, których to dotyczy, umożliwia Graphics Diagnostics sprawdź go, jego programów do cieniowania, zdarzenia Direct3D, które jej wpływ, stos wywołań aplikacji, które doprowadziło do tych zdarzeń i obiektów programu DirectX, które obsługują te zdarzenia. Te informacje można użyć do diagnozowania problemów z renderowaniem w grach i aplikacjach.  
  
 W górnej części okna (**Experiment.vsglog grafiki**) Wyświetla bieżącego dane wyjściowe docelowy renderowania zaznaczonej klatki i wyświetla część dolnej **lista ramek** zawierający obrazy miniatur przechwycone ramki.  
  
#### <a name="to-inspect-a-frame"></a>Aby sprawdzić ramkę  
  
-   W **lista ramek**, wybierz ramkę, która ma zostać sprawdzony. Dane wyjściowe docelowego renderowania w górnej części dokumentu dziennika grafiki jest zaktualizowany i będzie pokazywał zaznaczonej klatki.  
  
#### <a name="to-inspect-a-pixel"></a>Aby sprawdzić piksel  
  
-   W górnej części dokumentu dziennika grafiki wybierz piksel, który chcesz z danych wyjściowych docelowego renderowania. Po wybraniu pikseli, można użyć **Historia pikseli grafiki** okna, aby wyświetlić szczegółowe informacje na temat wybranego piksela. Aby uzyskać więcej informacji, zobacz [historii pikseli](../debugger/graphics-pixel-history.md).  
  
## <a name="playback-machine"></a>Maszyna odtwarzająca  
 Wyświetlany w prawym górnym rogu **lista ramek** jest **maszynę odtwarzającą**. Maszyna odtwarzania jest komputerem lub urządzeniem, który służy do odtwarzania zdarzenia grafiki z pliku dziennika grafiki podczas sesji diagnostyki grafiki nowsze. Za pomocą innego urządzenia zamiast komputera deweloperskiego do odtwarzania przechwytywanych zdarzeń, bardziej precyzyjne można odtworzyć środowiska wykonawczego, w której występuje problem — na przykład, można użyć maszyny, sprzęt graficzny różnych lub sterowniki niż te, które korzysta z komputera deweloperskiego lub inne rodzaje urządzeń, takich jak tablety przeznaczone dla komputerów z procesorem ARM z systemem Windows RT lub urządzenia Windows Phone.  
  
 Aby uzyskać informacje o sposobie określania maszyny odtwarzania, zobacz [porady: zmiana maszyny odtwarzania diagnostyki grafiki](../debugger/how-to-change-the-graphics-diagnostics-playback-machine.md).  
  
## <a name="graphics-log-summary-information"></a>Podsumowanie dziennika grafiki  
 Gdy plik dziennika grafiki jest aktywny dokument **właściwości** okna wyświetla informacje o środowisku, który hostuje sesji przechwytywania diagnostyki grafiki. Zostaną wyświetlone różne kategorie informacji.  
  
 **Informacje o programie Direct3D**  
 Wyświetla informacje na temat funkcji sprzętu i sterownik karty wideo, który został użyty podczas sesji przechwytywania.  
  
|Właściwość|Opis|  
|--------------|-----------------|  
|**Format 10-bitowy XR High Color**|**Wartość true,** Jeśli format trybie high-color XR 10-bitowy jest obsługiwana; w przeciwnym razie **False**.|  
|**DirectCompute CS 4.x**|**Wartość true,** Jeśli 4.0 programu do cieniowania obliczenia jest obsługiwana; w przeciwnym razie **False**.|  
|**Podwójne dokładności programów do cieniowania**|**Wartość true,** Jeśli karty graficznej obsługuje wartości zmiennoprzecinkowych (64-bitowy) podwójnej precyzji; w przeciwnym razie **False**.|  
|**Listy poleceń sterownika**|**Wartość true,** , gdy sterownik obsługuje listy poleceń; w przeciwnym razie **False**.|  
|**Tworzenie współbieżne sterownika**|**Wartość true,** Jeśli sterownik obsługuje równoczesne tworzenie (asynchroniczny); w przeciwnym razie **False**.|  
|**Formaty rozszerzone (BGRA itd.)**|**Wartość true,** Jeśli formaty rozszerzone, takich jak BGRA są obsługiwane; w przeciwnym razie **False**.|  
|**Maksymalny poziom funkcjonalności Sprzętowej**|Wyświetla najwyższy poziom funkcji, która jest obsługiwana przez kartę wideo.|  
  
 **Wyświetlanie informacji**  
 Wyświetla informacje dotyczące karty graficznej, który został użyty podczas sesji przechwytywania.  
  
|Właściwość|Opis|  
|--------------|-----------------|  
|**Opis**|Ciąg opisu karty wyświetlania.|  
|**Pamięć karty graficznej**|Ilość pamięci, która jest zainstalowana na karty graficznej.|  
|**Nazwa sterownika**|Nazwa sterownika karty graficznej.|  
|**Wersja sterownika**|Wersja sterownika karty graficznej.|  
|**Nazwa**|Nazwa karty graficznej.|  
  
 **Plik eksperymentalny**  
 Zawiera informacje o pliku eksperymentu, która jest skojarzona z sesji przechwytywania.  
  
|Właściwość|Opis|  
|--------------|-----------------|  
|**Path**|Ścieżka pliku .vsglog. **Uwaga:** w starszej wersji przechwytywania, ta właściwość jest używana.|  
  
 **Informacje o module**  
 Wyświetla nazwę i wersję biblioteki dołączanej dynamicznie (dll), które zostały załadowane przez aplikację podczas sesji przechwytywania.  
  
 **Informacje o systemie**  
 Wyświetla informacje dotyczące sprzętu i systemu operacyjnego, który obsługiwał aplikację podczas sesji przechwytywania.  
  
|Właściwość|Opis|  
|--------------|-----------------|  
|**Pamięć**|Ilość pamięci, który jest zainstalowany na komputerze.|  
|**Architektura systemu operacyjnego**|Obiekt docelowy architekturze Procesora systemu operacyjnego.|  
|**Wersja systemu operacyjnego**|Wersja systemu operacyjnego.|  
|**Procesor**|Procesor, który jest zainstalowany na komputerze.|  
|**Architektura aplikacji docelowej**|Obiekt docelowy architektury procesora CPU w aplikacji. Może to być inny niż **architektury systemu operacyjnego**.|  
  
 **Aplikacja docelowa**  
 Wyświetla informacje o aplikacji, które stanowią przedmiot sesji przechwytywania.  
  
|Właściwość|Opis|  
|--------------|-----------------|  
|**Data/godzina ostatniej modyfikacji**|Data i godzina, że aplikacja została skompilowana.|  
|**Path**|Ścieżka aplikacji.|  
|**Identyfikator procesu**|Identyfikator procesu, który został określony dla aplikacji.|  
|**Wersja**|Wersja aplikacji.|  
  
 **Plik dziennika VSG**  
 Wyświetla informacje o dokument dziennika grafiki.  
  
|Właściwość|Opis|  
|--------------|-----------------|  
|**Utworzone przez**|Nazwa aplikacji, utworzenia grafiki dziennika dokumentu. Załóżmy, że sesja przechwytywania zostało zainicjowane z [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] (Ręczne przechwytywanie) wartość tej właściwości jest [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].|  
|**Czas rozpoczęcia sesji**|Data i godzina rozpoczęcia sesji przechwytywania.|  
|**Rozmiar**|Rozmiar dokument dziennika grafiki.|  
  
## <a name="see-also"></a>Zobacz też  
 [Przewodnik: Brak obiektów spowodowany cieniowaniem wierzchołków](../debugger/walkthrough-missing-objects-due-to-vertex-shading.md)   
 [Przewodnik: debugowanie błędów renderowania spowodowanych cieniowaniem](../debugger/walkthrough-debugging-rendering-errors-due-to-shading.md)



