---
title: Korzystanie z kontrolek HTML5 w kodowanych testów interfejsu użytkownika | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-test
ms.topic: conceptual
ms.assetid: 2000b214-ae92-4334-b549-aa0eb4f45fe1
caps.latest.revision: 19
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 8b08853937be3f11913f88293633b02f3636898c
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "63439725"
---
# <a name="using-html5-controls-in-coded-ui-tests"></a>Korzystanie z formantów HTML5 w kodowanych testach interfejsu użytkownika
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Kodowane testy interfejsu użytkownika obsługują niektóre formanty języka HTML5, które są dołączone do programu Internet Explorer 9 i Internet Explorer 10.  
  
 **Wymagania**  
  
- Visual Studio Enterprise  
  
> [!WARNING]
> W wersjach wcześniejszych niż Internet Explorer 10 było możliwe do uruchomienia kodowanych testów interfejsu użytkownika w porównaniu do programu proces programu Internet Explorer wyższym poziomie uprawnień. Podczas uruchamiania kodowanych testów interfejsu użytkownika w programie Internet Explorer 10, proces programu Internet Explorer i kodowany test interfejsu użytkownika musi być na tym samym poziomie uprawnień. Jest to ze względu na bardziej bezpieczne funkcje kontenera aplikacji w programie Internet Explorer 10.  
  
> [!WARNING]
> Jeśli tworzysz kodowane testy interfejsu użytkownika w programie Internet Explorer 10, może nie zostać uruchomiony za pomocą programu Internet Explorer 9 i Internet Explorer 8. Jest to spowodowane programu Internet Explorer 10 zawiera formanty HTML5, takie jak Audio, wideo, pasek postępu i suwak. Te formanty HTML5 nie są rozpoznawane przez Internet Explorer 9 i Internet Explorer 8. Podobnie test interfejsu użytkownika kodowany za pomocą Internet Explorer 9 może zawierać niektóre formanty języka HTML5, które również nie zostaną rozpoznane przez Internet Explorer 8.  
  
## <a name="supported-html5-controls"></a>Formanty HTML5 obsługiwane  
 Kodowane testy interfejsu użytkownika obsługują rekordu, odtwarzanie i sposób sprawdzania poprawności formantów HTML5, następujące:  
  
- [Audio Control](#audio-control)  
  
- [Kontrolki wideo](#video-control)  
  
- [Slider](#slider)  
  
- [ProgressBar](#progressbar)  
  
### <a name="audio-control"></a>Kontrolki dźwięku  
 **Kontrolki dźwięku:** Akcje w kontrolce dźwięk HTML5 poprawnie są rejestrowane i odtwarzać.  
  
 ![Dźwięk HTML5 kontroli](../test/media/codedui-html5-audio.png)  
  
|Akcja|Rejestrowanie|Wygenerowany kod|  
|------------|---------------|--------------------|  
|**Odtwórz dźwięk**<br /><br /> Bezpośrednio z kontroli lub z menu kontekstowego kontrolki.|Odtwórz \<name > Audio z zakresu od 00:00:00|HtmlAudio.Play(TimeSpan)|  
|**Starać się w określonym czasie które usłyszysz**|Wyszukiwanie \<name > Audio do 00:01:48|HtmlAudio.Seek(TimeSpan)|  
|**Wstrzymaj audio**<br /><br /> Bezpośrednio z kontroli lub z menu kontekstowego kontrolki.|Wstrzymaj \<name > Audio na 00:01:53|HtmlAudio.Pause(TimeSpan)|  
|**Wycisz audio**<br /><br /> Bezpośrednio z kontroli lub z menu kontekstowego kontrolki.|Wycisz \<name > Audio|HtmlAudio.Mute()|  
|**Wyłącz Wyciszenie audio**<br /><br /> Bezpośrednio z kontroli lub z menu kontekstowego kontrolki.|Wyłącz wyciszenie \<name > Audio|HtmlAudio.Unmute()|  
|**Zmień głośność dźwięku**|Ustaw głośność \<name > Audio do 79%|HtmlAudio.SetVolume(float)|  
  
 Następujące właściwości są dostępne dla HtmlAudio i można dodać potwierdzenia na wszystkich z nich:  
  
```  
string AutoPlay  
string Controls  
string CurrentSrc  
string CurrentTime  
string CurrentTimeAsString  
string Duration  
string DurationAsString  
string Ended  
string Loop  
string Muted  
string Paused  
string PlaybackRate  
string ReadyState  
string Seeking  
string Src  
string Volume  
```  
  
 **Właściwości wyszukiwania:** Właściwości wyszukiwania `HtmlAudio` są `Id`, `Name` i `Title`.  
  
 **Właściwości filtru:** Właściwości filtru dla `HtmlAudio` są `Src`, `Class`, `ControlDefinition` i `TagInstance`.  
  
> [!NOTE]
> Ilość czasu, która umożliwia wyszukiwanie i wstrzymywanie działania mogą być znaczące. Podczas odtwarzania kodowanego testu interfejsu użytkownika będzie czekać aż do określonej w `(TimeSpan)` przed wstrzymaniem audio. Jeśli przez kilka specjalnych okoliczności określonego czasu minęło przed osiągnięcia polecenie wstrzymania, zostanie zgłoszony wyjątek.  
  
### <a name="video-control"></a>Kontrolki wideo  
 **Kontrolki wideo:** Poprawnie zarejestrowane i odtwarzać akcji dla kontrolki wideo HTML5.  
  
 ![Kontrolki wideo HTML5](../test/media/codedui-html5-video.png)  
  
|Akcja|Rejestrowanie|Wygenerowany kod|  
|------------|---------------|--------------------|  
|**Odtwórz wideo**<br /><br /> Bezpośrednio z kontroli lub z menu kontekstowego kontrolki.|Odtwórz \<name > wideo z zakresu od 00:00:00|HtmlVideo.Play(TimeSpan)|  
|**Starać się w określonym czasie, w trakcie filmu wideo**|Wyszukiwanie \<name > film, aby 00:01:48|HtmlVideo.Seek(TimeSpan)|  
|**Wstrzymaj wideo**<br /><br /> Bezpośrednio z kontroli lub z menu kontekstowego kontrolki.|Wstrzymaj \<name > wideo o 00:01:53|HtmlVideo.Pause(TimeSpan)|  
|**Wycisz wideo**<br /><br /> Bezpośrednio z kontroli lub z menu kontekstowego kontrolki.|Wycisz \<name > wideo|HtmlVideo.Mute()|  
|**Wyłącz Wyciszenie wideo**<br /><br /> Bezpośrednio z kontroli lub z menu kontekstowego kontrolki.|Wyłącz wyciszenie \<name > wideo|HtmlVideo.Unmute()|  
|**Zmień ilość wideo**|Ustaw głośność \<name > wideo do 79%||  
  
 Wszystkie właściwości HtmlAudio są dostępne dla HtmlVideo. Ponadto następujące trzy właściwości również są dostępne. Można dodać potwierdzenia na wszystkich z nich.  
  
```  
string Poster  
string VideoHeight  
string VideoWidth  
  
```  
  
 **Właściwości wyszukiwania:** Właściwości wyszukiwania `HtmlVideo` są `Id`, `Name` i `Title`.  
  
 **Właściwości filtru:** Właściwości filtru dla `HtmlVideo` są `Src`, `Poster`, `Class`, `ControlDefinition` i `TagInstance`.  
  
> [!NOTE]
> Jeśli przewinąć do tyłu lub szybkie przewijanie do przodu wideo przy użyciu etykiet-30s lub +30s, to zostaną zagregowane się w odpowiednim czasie.  
  
### <a name="slider"></a>Suwak  
 **Kontrolka suwaka:** Akcje w kontrolce suwaka HTML5 poprawnie są rejestrowane i odtwarzać.  
  
 ![Kontrolka suwaka HTML5](../test/media/codedui-html5-slider.png)  
  
|Akcja|Rejestrowanie|Wygenerowany kod|  
|------------|---------------|--------------------|  
|**Ustaw położenie na suwaku**|Ustaw położenie \<x > w \<name > suwaka|HtmlSlider.ValueAsNumber=\<x>|  
  
 Następujące właściwości są dostępne dla HtmlSlider i można dodać potwierdzenia na wszystkich z nich:  
  
```  
string Disabled  
string Max  
string Min  
string Required  
string Step  
string ValueAsNumber  
```  
  
### <a name="progressbar"></a>ProgressBar  
 **ProgressBar — formant:** ProgressBar jest-interactable kontroli. Można dodać asercje `Value` i `Max` właściwości tej kontrolki.  
  
 ![HTML5 ProgressBar, kontrolka](../test/media/codedui-html5-progressbar.png)  
  
## <a name="see-also"></a>Zobacz także

- [Elementy HTML](https://www.w3schools.com/HTML/html_elements.asp)   
- [Używanie automatyzacji interfejsu użytkownika do testowania kodu](../test/use-ui-automation-to-test-your-code.md)   
- [Tworzenie kodowanych testów interfejsu użytkownika](../test/use-ui-automation-to-test-your-code.md#VerifyingCodeUsingCUITCreate)   
- [Dostosowywanie kodowanego testu interfejsu użytkownika](../test/use-ui-automation-to-test-your-code.md#VerifyingCodeCUITModify)   
- [Obsługiwane konfiguracje oraz platformy zakodowanych testów interfejsu użytkownika i rejestrowania akcji](../test/supported-configurations-and-platforms-for-coded-ui-tests-and-action-recordings.md)
