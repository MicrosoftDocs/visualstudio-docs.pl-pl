---
title: Korzystanie z kontrolek HTML5 w kodowanych testach interfejsu użytkownika | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-test
ms.topic: conceptual
ms.assetid: 2000b214-ae92-4334-b549-aa0eb4f45fe1
caps.latest.revision: 19
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 029b547102863f4798ad261deb678c4d98596916
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "72657201"
---
# <a name="using-html5-controls-in-coded-ui-tests"></a>Korzystanie z formantów HTML5 w kodowanych testach interfejsu użytkownika
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Kodowane testy interfejsu użytkownika obejmują obsługę niektórych formantów HTML5 zawartych w programie Internet Explorer 9 i Internet Explorer 10.

 **Wymagania**

- Visual Studio Enterprise

> [!WARNING]
> W wersjach programu starszych niż Internet Explorer 10 można było uruchomić kodowane testy interfejsu użytkownika na wyższym poziomie uprawnień w porównaniu z procesem programu Internet Explorer. Podczas uruchamiania kodowanych testów interfejsu użytkownika w programie Internet Explorer 10 zarówno kodowany test interfejsu użytkownika, jak i proces programu Internet Explorer, muszą być na tym samym poziomie uprawnień. Jest to spowodowane bardziej bezpiecznymi funkcjami kontenera aplikacji w programie Internet Explorer 10.

> [!WARNING]
> W przypadku utworzenia kodowanego testu interfejsu użytkownika w programie Internet Explorer 10 nie można uruchomić go za pomocą programu Internet Explorer 9 lub Internet Explorer 8. Jest to spowodowane tym, że program Internet Explorer 10 zawiera formanty HTML5, takie jak audio, wideo, ProgressBar i Slider. Te formanty HTML5 nie są rozpoznawane przez Internet Explorer 9 i Internet Explorer 8. Podobnie test interfejsu użytkownika kodowany za pomocą Internet Explorer 9 może zawierać niektóre formanty języka HTML5, które również nie zostaną rozpoznane przez Internet Explorer 8.

## <a name="supported-html5-controls"></a>Obsługiwane kontrolki HTML5
 Kodowane testy interfejsu użytkownika obejmują obsługę rejestrowania, odtwarzania i weryfikacji następujących formantów HTML5:

- [Kontrolka audio](#audio-control)

- [Kontrolka wideo](#video-control)

- [Slider](#slider)

- [ProgressBar](#progressbar)

### <a name="audio-control"></a>Kontrolka audio
 **Kontrolka audio:** Akcje w kontrolce audio HTML5 są poprawnie rejestrowane i odtwarzane.

 ![Formant audio HTML5](../test/media/codedui-html5-audio.png)

|Akcja|Nagrywanie|Wygenerowany kod|
|------------|---------------|--------------------|
|**Odtwórz dźwięk**<br /><br /> Bezpośrednio z kontrolki lub z menu kontekstowego kontrolek.|Odtwórz \<name> dźwięk z 00:00:00|HtmlAudio. Play (TimeSpan)|
|**Przeszukiwanie określonego czasu w dźwięku**|Wyszukaj \<name> dźwięk do 00:01:48|HtmlAudio. seek (TimeSpan)|
|**Wstrzymaj dźwięk**<br /><br /> Bezpośrednio z kontrolki lub z menu kontekstowego kontrolek.|Wstrzymaj \<name> audio o godzinie 00:01:53|HtmlAudio. Pause (TimeSpan)|
|**Wycisz dźwięk**<br /><br /> Bezpośrednio z kontrolki lub z menu kontekstowego kontrolek.|Wycisz \<name> dźwięk|HtmlAudio. Wycisz ()|
|**Wycisz dźwięk**<br /><br /> Bezpośrednio z kontrolki lub z menu kontekstowego kontrolek.|Wycisz \<name> dźwięk|HtmlAudio. unwyciszony ()|
|**Zmień głośność dźwięku**|Ustaw głośność \<name> dźwięku na 79%|HtmlAudio. SetVolume (float)|

 Następujące właściwości są dostępne dla HtmlAudio i można dodać potwierdzenie dla wszystkich z nich:

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

 **Właściwości wyszukiwania:** Właściwości wyszukiwania dla `HtmlAudio` są `Id` `Name` i `Title` .

 **Właściwości filtru:** Właściwości filtru dla `HtmlAudio` są `Src` , `Class` , `ControlDefinition` i `TagInstance` .

> [!NOTE]
> Czas poszukiwania i wstrzymania może być istotny. Podczas odtwarzania kodowany test interfejsu użytkownika będzie czekał do określonego czasu `(TimeSpan)` przed wstrzymaniem dźwięku. Jeśli w pewnych okolicznościach specjalnych określony czas został zakończony przed naciśnięciem polecenia Pause, zostanie zgłoszony wyjątek.

### <a name="video-control"></a>Kontrolka wideo
 **Kontrolka wideo:** Akcje w kontrolce wideo HTML5 są poprawnie rejestrowane i odtwarzane.

 ![Formant wideo HTML5](../test/media/codedui-html5-video.png)

|Akcja|Nagrywanie|Wygenerowany kod|
|------------|---------------|--------------------|
|**Odtwórz wideo**<br /><br /> Bezpośrednio z kontrolki lub z menu kontekstowego kontrolek.|Odtwórz \<name> wideo z 00:00:00|HtmlVideo. Play (TimeSpan)|
|**Przeszukaj do określonego czasu w filmie wideo**|Szukaj \<name> wideo na 00:01:48|HtmlVideo. seek (TimeSpan)|
|**Wstrzymaj wideo**<br /><br /> Bezpośrednio z kontrolki lub z menu kontekstowego kontrolek.|Wstrzymaj \<name> wideo o godzinie 00:01:53|HtmlVideo. Pause (TimeSpan)|
|**Wycisz wideo**<br /><br /> Bezpośrednio z kontrolki lub z menu kontekstowego kontrolek.|Wycisz \<name> wideo|HtmlVideo. Wycisz ()|
|**Odcisz wideo**<br /><br /> Bezpośrednio z kontrolki lub z menu kontekstowego kontrolek.|Odcisz \<name> wideo|HtmlVideo. unwyciszony ()|
|**Zmień ilość wideo**|Ustaw głośność \<name> wideo na 79%||

 Wszystkie właściwości HtmlAudio są dostępne dla HtmlVideo. Ponadto dostępne są również następujące trzy właściwości. Potwierdzenie można dodać do wszystkich z nich.

```
string Poster
string VideoHeight
string VideoWidth

```

 **Właściwości wyszukiwania:** Właściwości wyszukiwania dla `HtmlVideo` są `Id` `Name` i `Title` .

 **Właściwości filtru:** Właściwości filtru dla `HtmlVideo` są `Src` , `Poster` , `Class` , `ControlDefinition` i `TagInstance` .

> [!NOTE]
> Jeśli przejdziesz do tyłu lub szybko przekażesz wideo przy użyciu etykiet-30 s lub + 30 s, zostanie ono zagregowane w celu przeszukania odpowiedniego czasu.

### <a name="slider"></a>Slider
 **Kontrolka suwaka:** Akcje w kontrolce suwaka HTML5 są poprawnie rejestrowane i odtwarzane.

 ![Formant Slider HTML5](../test/media/codedui-html5-slider.png)

|Akcja|Nagrywanie|Wygenerowany kod|
|------------|---------------|--------------------|
|**Ustaw położenie na suwaku**|Ustaw pozycję na \<x> \<name> suwaka|HtmlSlider. ValueAsNumber =\<x>|

 Następujące właściwości są dostępne dla HtmlSlider i potwierdzenie można dodać na wszystkich z nich:

```
string Disabled
string Max
string Min
string Required
string Step
string ValueAsNumber
```

### <a name="progressbar"></a>ProgressBar
 **Formant ProgressBar:** Element ProgressBar jest kontrolką niewspółpracującą. Możesz dodać potwierdzenia do `Value` `Max` właściwości i tej kontrolki.

 ![Formant ProgressBar HTML5](../test/media/codedui-html5-progressbar.png)

## <a name="see-also"></a>Zobacz też

- [Elementy HTML](https://www.w3schools.com/HTML/html_elements.asp)
- [Używanie automatyzacji interfejsu użytkownika do testowania kodu](../test/use-ui-automation-to-test-your-code.md)
- [Tworzenie kodowanych testów interfejsu użytkownika](../test/use-ui-automation-to-test-your-code.md#VerifyingCodeUsingCUITCreate)
- [Dostosowywanie kodowanego testu interfejsu użytkownika](../test/use-ui-automation-to-test-your-code.md#VerifyingCodeCUITModify)
- [Obsługiwane konfiguracje oraz platformy zakodowanych testów interfejsu użytkownika i nagrywania akcji](../test/supported-configurations-and-platforms-for-coded-ui-tests-and-action-recordings.md)
