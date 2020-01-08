---
title: Korzystanie z formantów HTML5 w kodowanych testach interfejsu użytkownika
ms.date: 11/04/2016
ms.topic: conceptual
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
author: mikejo5000
ms.openlocfilehash: 13f5da784a43df5146a66ca868bb6add9a702906
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/01/2020
ms.locfileid: "75585590"
---
# <a name="using-html5-controls-in-coded-ui-tests"></a>Korzystanie z kontrolek HTML5 w kodowanych testach interfejsu użytkownika

Kodowane testy interfejsu użytkownika obejmują obsługę niektórych formantów HTML5 zawartych w programie Internet Explorer 9 i Internet Explorer 10.

[!INCLUDE [coded-ui-test-deprecation](includes/coded-ui-test-deprecation.md)]

**Requirements**

- Visual Studio Enterprise

> [!WARNING]
> W wersjach programu starszych niż Internet Explorer 10 można było uruchomić kodowane testy interfejsu użytkownika na wyższym poziomie uprawnień w porównaniu z procesem programu Internet Explorer. Podczas uruchamiania kodowanych testów interfejsu użytkownika w programie Internet Explorer 10 zarówno kodowany test interfejsu użytkownika, jak i proces programu Internet Explorer, muszą być na tym samym poziomie uprawnień. Jest to spowodowane bardziej bezpiecznymi funkcjami kontenera aplikacji w programie Internet Explorer 10.

> [!WARNING]
> W przypadku utworzenia kodowanego testu interfejsu użytkownika w programie Internet Explorer 10 nie można uruchomić go za pomocą programu Internet Explorer 9 lub Internet Explorer 8. Jest to spowodowane tym, że program Internet Explorer 10 zawiera formanty HTML5, takie jak audio, wideo, ProgressBar i Slider. Te formanty HTML5 nie są rozpoznawane przez Internet Explorer 9 i Internet Explorer 8. Podobnie test interfejsu użytkownika kodowany za pomocą Internet Explorer 9 może zawierać niektóre formanty języka HTML5, które również nie zostaną rozpoznane przez Internet Explorer 8.

## <a name="audio-control"></a>Kontrolka audio

**Kontrolka audio:** Akcje w kontrolce audio HTML5 są poprawnie rejestrowane i odtwarzane.

![Formant audio HTML5](../test/media/codedui_html5_audio.png)

|Akcja|Nagrywanie|Wygenerowany kod|
|-|---------------|-|
|**Odtwórz dźwięk**<br /><br /> Bezpośrednio z kontrolki lub menu po kliknięciu prawym przyciskiem myszy.|Odtwórz nazwę \<> dźwięk z 00:00:00|HtmlAudio.Play(TimeSpan)|
|**Przeszukiwanie określonego czasu w dźwięku**|Wyszukaj nazwę \<> dźwięk do 00:01:48|HtmlAudio.Seek(TimeSpan)|
|**Wstrzymaj dźwięk**<br /><br /> Bezpośrednio z kontrolki lub menu po kliknięciu prawym przyciskiem myszy.|Wstrzymaj \<nazwę > audio w 00:01:53|HtmlAudio.Pause(TimeSpan)|
|**Wycisz dźwięk**<br /><br /> Bezpośrednio z kontrolki lub menu po kliknięciu prawym przyciskiem myszy.|Wycisz \<nazwę > audio|HtmlAudio.Mute()|
|**Wycisz dźwięk**<br /><br /> Bezpośrednio z kontrolki lub menu po kliknięciu prawym przyciskiem myszy.|Wyłącz wyciszenie nazwy \<> audio|HtmlAudio.Unmute()|
|**Zmień głośność dźwięku**|Ustaw wartość \<nazwy > audio na 79%|HtmlAudio.SetVolume(float)|

Zobacz [HTMLAudioElement](https://developer.mozilla.org/docs/Web/API/HTMLAudioElement) , aby uzyskać listę właściwości, na których można dodać potwierdzenie.

**Właściwości wyszukiwania:** Właściwości wyszukiwania dla `HtmlAudio` są `Id`, `Name` i `Title`.

**Właściwości filtru:** Właściwości filtru dla `HtmlAudio` są `Src`, `Class`, `ControlDefinition` i `TagInstance`.

> [!NOTE]
> Czas poszukiwania i wstrzymania może być istotny. Podczas odtwarzania kodowany test interfejsu użytkownika będzie czekać do określonego czasu w `(TimeSpan)` przed zawstrzymywaniem dźwięku. Jeśli w pewnych okolicznościach specjalnych określony czas został zakończony przed naciśnięciem polecenia Pause, zostanie zgłoszony wyjątek.

## <a name="video-control"></a>Kontrolka wideo
**Kontrolka wideo:** Akcje w kontrolce wideo HTML5 są poprawnie rejestrowane i odtwarzane.

![Formant wideo HTML5](../test/media/codedui_html5_video.png)

|Akcja|Nagrywanie|Wygenerowany kod|
|-|---------------|-|
|**Odtwórz wideo**<br /><br /> Bezpośrednio z kontrolki lub menu po kliknięciu prawym przyciskiem myszy.|Odtwórz nazwę \<> wideo z 00:00:00|HtmlVideo.Play(TimeSpan)|
|**Przeszukaj do określonego czasu w filmie wideo**|Wyszukaj nazwę \<> wideo do 00:01:48|HtmlVideo.Seek(TimeSpan)|
|**Wstrzymaj wideo**<br /><br /> Bezpośrednio z kontrolki lub menu po kliknięciu prawym przyciskiem myszy.|Wstrzymaj \<nazwę > wideo o godzinie 00:01:53|HtmlVideo.Pause(TimeSpan)|
|**Wycisz wideo**<br /><br /> Bezpośrednio z kontrolki lub menu po kliknięciu prawym przyciskiem myszy.|Wycisz \<nazwę > wideo|HtmlVideo.Mute()|
|**Odcisz wideo**<br /><br /> Bezpośrednio z kontrolki lub menu po kliknięciu prawym przyciskiem myszy.|Wycisz \<nazwę > wideo|HtmlVideo.Unmute()|
|**Zmień ilość wideo**|Ustaw wartość \<nazwy > wideo na 79%||

Zobacz [HTMLVideoElement](https://developer.mozilla.org/docs/Web/HTML/Element/video) , aby uzyskać listę właściwości, na których można dodać potwierdzenie.

**Właściwości wyszukiwania:** Właściwości wyszukiwania dla `HtmlVideo` są `Id`, `Name` i `Title`.

**Właściwości filtru:** Właściwości filtru dla `HtmlVideo` są `Src`, `Poster`, `Class`, `ControlDefinition` i `TagInstance`.

> [!NOTE]
> Jeśli przejdziesz do tyłu lub szybko przekażesz wideo przy użyciu etykiet-30 s lub + 30 s, zostanie ono zagregowane w celu przeszukania odpowiedniego czasu.

## <a name="progressbar"></a>ProgressBar
**Formant ProgressBar:** Element ProgressBar jest kontrolką niewspółpracującą. Możesz dodać potwierdzenia na `Value` i `Max` właściwości tej kontrolki. Aby uzyskać więcej informacji, zobacz [HTMLProgressElement](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/progress).

![Formant ProgressBar HTML5](../test/media/codedui_html5_progressbar.png)

## <a name="see-also"></a>Zobacz także

- [Elementy HTML](https://developer.mozilla.org/docs/Web/HTML/Element)
- [Używanie automatyzacji interfejsu użytkownika do testowania kodu](../test/use-ui-automation-to-test-your-code.md)
- [Tworzenie kodowanych testów interfejsu użytkownika](../test/use-ui-automation-to-test-your-code.md)
- [Obsługiwane konfiguracje oraz platformy zakodowanych testów interfejsu użytkownika i nagrywania akcji](../test/supported-configurations-and-platforms-for-coded-ui-tests-and-action-recordings.md)
