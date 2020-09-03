---
title: Dokument dziennika grafiki | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.graphics.vsglog.error
- vs.graphics.experiment
- vs.graphics.vsglog
ms.assetid: 6ccb1269-d55f-49c4-920d-baedf7de2888
caps.latest.revision: 34
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 430c321c14226228b46bfb0e43f372851fb2a232
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68161237"
---
# <a name="graphics-log-document"></a>Dokument dziennika grafiki
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Dokument dziennika grafiki to rekord zdarzeń graficznych, które wystąpiły, gdy aplikacja była uruchomiona w ramach sesji diagnostyki grafiki. Po zarejestrowaniu można przejrzeć dziennik w analizator grafiki programu Visual Studio, aby zdiagnozować problemy z renderowaniem i wydajnością.  
  
 Oto, jak wygląda dokument dziennika grafiki w analizatorze grafiki:  
  
 ![Dziennik grafiki zawierający dwie przechwycone ramki.](../debugger/media/gfx-diag-demo-graphics-log-orientation.png "gfx_diag_demo_graphics_log_orientation")  
  
## <a name="understanding-graphics-log-documents"></a>Informacje o dokumentach dzienników grafiki  
 Używając analizatora grafiki do badania dokumentu dziennika grafiki, można wizualizować efekty zdarzeń Direct3D w miejscu docelowym renderowania, które wystąpiło podczas przechwytywania. Możesz wskazać regiony elementu docelowego renderowania, który zawiera nieoczekiwane dane wyjściowe. Po wybraniu piksela w regionie, którego to dotyczy, można użyć Diagnostyka grafiki do sprawdzenia, jego programów do cieniowania, zdarzeń Direct3D, które to dotyczy, stosu wywołań aplikacji, który doprowadził do tych zdarzeń, oraz obiektów DirectX, które obsługują te zdarzenia. Te informacje służą do diagnozowania problemów z renderowaniem w grze lub aplikacji.  
  
 W górnej części okna (**eksperyment grafiki. vsglog**) są wyświetlane bieżące docelowe dane wyjściowe renderowania zaznaczonej ramki, a dolna część wyświetla **listę ramek** , która zawiera obrazy miniatur przechwyconej ramki.  
  
#### <a name="to-inspect-a-frame"></a>Aby przeprowadzić inspekcję ramki  
  
- Na **liście ramka**Wybierz ramkę, którą chcesz sprawdzić. Dane wyjściowe docelowej renderowania w górnej części dokumentu dziennika grafiki zostały zaktualizowane w celu wyświetlenia wybranej ramki.  
  
#### <a name="to-inspect-a-pixel"></a>Aby sprawdzić piksel  
  
- W górnej części dokumentu dziennika grafiki wybierz piksel, który ma się pojawić w docelowym wyjściu renderowania. Gdy piksel jest zaznaczony, można użyć okna **Historia pikseli grafiki** , aby wyświetlić szczegółowe informacje na temat wybranego piksela. Aby uzyskać więcej informacji, zobacz [Historia pikseli](../debugger/graphics-pixel-history.md).  
  
## <a name="playback-machine"></a>Maszyna odtwarzania  
 Również w prawym górnym rogu **listy ramek** znajduje się **maszyna odtwarzania**. Maszyna odtwarzania jest maszyną lub urządzeniem służącym do odtwarzania zdarzeń graficznych z pliku dziennika grafiki podczas późniejszej sesji diagnostyki grafiki. Przy użyciu innego urządzenia zamiast komputera deweloperskiego, aby odtwarzać przechwycone zdarzenia, można dokładniej odtworzyć środowisko wykonywania, w którym występuje problem — na przykład można użyć komputera z innym sprzętem lub sterownikiem graficznym niż te, które są używane przez maszynę deweloperskią, lub innych rodzajów urządzeń, takich jak tablet z systemem Windows RT lub Windows Phone.  
  
 Aby uzyskać informacje na temat sposobu określania komputera odtwarzającego, zobacz [How to: Change a Diagnostyka grafiki playback Machine](../debugger/how-to-change-the-graphics-diagnostics-playback-machine.md).  
  
## <a name="graphics-log-summary-information"></a>Informacje podsumowujące dzienników grafiki  
 Gdy plik dziennika grafiki jest aktywnym dokumentem, okno **Właściwości** wyświetla informacje o środowisku, w którym jest hostowana Diagnostyka grafiki sesji przechwytywania. Zostanie wyświetlona kilka kategorii informacji.  
  
 **Informacje o programie Direct3D**  
 Wyświetla informacje o funkcjach sprzętu i sterownika karty graficznej, która została użyta podczas sesji przechwytywania.  
  
|Właściwość|Opis|  
|--------------|-----------------|  
|**10-bitowy format XR High Color**|**Wartość true** , jeśli jest obsługiwany format 10-bitowy XR High-Color; w przeciwnym razie **false**.|  
|**DirectCompute CS 4. x**|**Prawda** , jeśli jest obsługiwany program obliczeniowy obliczeń 4,0; w przeciwnym razie **false**.|  
|**Programy do cieniowania podwójnej precyzji**|**Ma wartość true** , jeśli karta graficzna obsługuje wartości zmiennoprzecinkowe o podwójnej precyzji (64-bitowe); w przeciwnym razie **false**.|  
|**Listy poleceń sterowników**|**Ma wartość true** , jeśli sterownik obsługuje listy poleceń; w przeciwnym razie **false**.|  
|**Tworzenie współbieżne sterowników**|**Ma wartość true** , jeśli sterownik obsługuje współbieżne (asynchroniczne) Tworzenie; w przeciwnym razie **false**.|  
|**Formaty rozszerzone (BGRA itd.)**|**Ma wartość true** , jeśli obsługiwane są formaty rozszerzone, takie jak BGRA. w przeciwnym razie **false**.|  
|**Maksymalny poziom funkcjonalności SPRZĘTowej**|Wyświetla najwyższy poziom funkcji, który jest obsługiwany przez adapter wyświetlania.|  
  
 **Informacje o wyświetlaniu**  
 Wyświetla informacje o karcie graficznej, która została użyta podczas sesji przechwytywania.  
  
|Właściwość|Opis|  
|--------------|-----------------|  
|**Opis**|Ciąg opisu karty graficznej.|  
|**Wyświetl pamięć**|Ilość pamięci zainstalowanej na karcie graficznej.|  
|**Nazwisko kierowcy**|Nazwa sterownika karty graficznej.|  
|**Wersja sterownika**|Wersja sterownika karty graficznej.|  
|**Nazwa**|Nazwa karty graficznej.|  
  
 **Plik eksperymentu**  
 Wyświetla informacje o pliku eksperymentu skojarzonym z sesją przechwytywania.  
  
|Właściwość|Opis|  
|--------------|-----------------|  
|**Ścieżka**|Ścieżka pliku. vsglog. **Uwaga:**  W obszarze starszego przechwytywania ta właściwość nie jest używana.|  
  
 **Informacje o module**  
 Wyświetla nazwę i wersję bibliotek dołączanych dynamicznie (dll), które zostały załadowane przez aplikację podczas sesji przechwytywania.  
  
 **Informacje o systemie**  
 Wyświetla listę informacji o sprzęcie i systemie operacyjnym, które obsługują aplikację podczas sesji przechwytywania.  
  
|Właściwość|Opis|  
|--------------|-----------------|  
|**Pamięć**|Ilość pamięci zainstalowanej na komputerze.|  
|**Architektura systemu operacyjnego**|Docelowa architektura procesora systemu operacyjnego.|  
|**Wersja systemu operacyjnego**|wersja systemu operacyjnego.|  
|**Procesor**|Procesor, który jest zainstalowany na komputerze.|  
|**Architektura aplikacji docelowej**|Docelowa architektura procesora dla aplikacji. Może się to różnić od **architektury systemu operacyjnego**.|  
  
 **Aplikacja docelowa**  
 Wyświetla informacje o aplikacji, która jest podmiotem sesji przechwytywania.  
  
|Właściwość|Opis|  
|--------------|-----------------|  
|**Data/godzina ostatniej modyfikacji**|Data i godzina skompilowania aplikacji.|  
|**Ścieżka**|Ścieżka aplikacji.|  
|**Identyfikator procesu**|Identyfikator procesu, który został przekazany do aplikacji.|  
|**Wersja**|Wersja aplikacji.|  
  
 **Plik dziennika VSG**  
 Wyświetla informacje o dokumencie dziennika grafiki.  
  
|Właściwość|Opis|  
|--------------|-----------------|  
|**Utworzone przez**|Nazwa aplikacji, która utworzyła dokument dziennika grafiki. Na przykład jeśli sesja przechwytywania została zainicjowana z [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] (przechwytywanie ręczne), wartość tej właściwości to [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] .|  
|**Godzina rozpoczęcia sesji**|Data i godzina rozpoczęcia sesji przechwytywania.|  
|**Rozmiar**|Rozmiar dokumentu dziennika grafiki.|  
  
## <a name="see-also"></a>Zobacz też  
 [Przewodnik: brak obiektów ze względu na cieniowanie wierzchołków](../debugger/walkthrough-missing-objects-due-to-vertex-shading.md)   
 [Przewodnik: debugowanie błędów renderowania spowodowanych cieniowaniem](../debugger/walkthrough-debugging-rendering-errors-due-to-shading.md)
