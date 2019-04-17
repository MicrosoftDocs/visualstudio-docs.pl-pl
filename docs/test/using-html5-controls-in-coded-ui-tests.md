---
title: Korzystanie z formantów HTML5 w kodowanych testach interfejsu użytkownika
ms.date: 11/04/2016
ms.topic: conceptual
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: 84c1a0a4f74c847da78920a638b37c0294717d02
ms.sourcegitcommit: 53aa5a413717a1b62ca56a5983b6a50f7f0663b3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/17/2019
ms.locfileid: "59649788"
---
# <a name="using-html5-controls-in-coded-ui-tests"></a>Korzystanie z kontrolek HTML5 w kodowanych testach interfejsu użytkownika

Kodowane testy interfejsu użytkownika obsługują niektóre formanty języka HTML5, które są dołączone do programu Internet Explorer 9 i Internet Explorer 10.

[!INCLUDE [coded-ui-test-deprecation](includes/coded-ui-test-deprecation.md)]

 **Wymagania**

-   Visual Studio Enterprise

> [!WARNING]
> W wersjach wcześniejszych niż Internet Explorer 10 było możliwe do uruchomienia kodowanych testów interfejsu użytkownika w porównaniu do programu proces programu Internet Explorer wyższym poziomie uprawnień. Podczas uruchamiania kodowanych testów interfejsu użytkownika w programie Internet Explorer 10, proces programu Internet Explorer i kodowany test interfejsu użytkownika musi być na tym samym poziomie uprawnień. Jest to ze względu na bardziej bezpieczne funkcje kontenera aplikacji w programie Internet Explorer 10.

> [!WARNING]
> Jeśli tworzysz kodowane testy interfejsu użytkownika w programie Internet Explorer 10, może nie zostać uruchomiony za pomocą programu Internet Explorer 9 i Internet Explorer 8. Jest to spowodowane programu Internet Explorer 10 zawiera formanty HTML5, takie jak Audio, wideo, pasek postępu i suwak. Te formanty HTML5 nie są rozpoznawane przez Internet Explorer 9 i Internet Explorer 8. Podobnie test interfejsu użytkownika kodowany za pomocą Internet Explorer 9 może zawierać niektóre formanty języka HTML5, które również nie zostaną rozpoznane przez Internet Explorer 8.

## <a name="audio-control"></a>Kontrolki dźwięku

**Kontrolki dźwięku:** Akcje w kontrolce dźwięk HTML5 poprawnie są rejestrowane i odtwarzać.

![Dźwięk HTML5 kontroli](../test/media/codedui_html5_audio.png)

|Akcja|Rejestrowanie|Wygenerowany kod|
|-|---------------|-|
|**Odtwórz dźwięk**<br /><br /> Bezpośrednio z kontrolki lub kontrolki prawym przyciskiem myszy.|Odtwórz \<name > Audio z zakresu od 00:00:00|HtmlAudio.Play(TimeSpan)|
|**Starać się w określonym czasie które usłyszysz**|Wyszukiwanie \<name > Audio do 00:01:48|HtmlAudio.Seek(TimeSpan)|
|**Wstrzymaj audio**<br /><br /> Bezpośrednio z kontrolki lub kontrolki prawym przyciskiem myszy.|Wstrzymaj \<name > Audio na 00:01:53|HtmlAudio.Pause(TimeSpan)|
|**Wycisz audio**<br /><br /> Bezpośrednio z kontrolki lub kontrolki prawym przyciskiem myszy.|Wycisz \<name > Audio|HtmlAudio.Mute()|
|**Wyłącz Wyciszenie audio**<br /><br /> Bezpośrednio z kontrolki lub kontrolki prawym przyciskiem myszy.|Wyłącz wyciszenie \<name > Audio|HtmlAudio.Unmute()|
|**Zmień głośność dźwięku**|Ustaw głośność \<name > Audio do 79%|HtmlAudio.SetVolume(float)|

Zobacz [HTMLAudioElement](https://developer.mozilla.org/docs/Web/API/HTMLAudioElement) listę właściwości, na których można dodać potwierdzenia.

 **Właściwości wyszukiwania:** Właściwości wyszukiwania `HtmlAudio` są `Id`, `Name` i `Title`.

 **Właściwości filtru:** Właściwości filtru dla `HtmlAudio` są `Src`, `Class`, `ControlDefinition` i `TagInstance`.

> [!NOTE]
> Ilość czasu, która umożliwia wyszukiwanie i wstrzymywanie działania mogą być znaczące. Podczas odtwarzania kodowanego testu interfejsu użytkownika będzie czekać aż do określonej w `(TimeSpan)` przed wstrzymaniem audio. Jeśli przez kilka specjalnych okoliczności określonego czasu minęło przed osiągnięcia polecenie wstrzymania, zostanie zgłoszony wyjątek.

## <a name="video-control"></a>Kontrolki wideo
 **Kontrolki wideo:** Poprawnie zarejestrowane i odtwarzać akcji dla kontrolki wideo HTML5.

 ![Kontrolki wideo HTML5](../test/media/codedui_html5_video.png)

|Akcja|Rejestrowanie|Wygenerowany kod|
|-|---------------|-|
|**Odtwórz wideo**<br /><br /> Bezpośrednio z kontrolki lub kontrolki prawym przyciskiem myszy.|Odtwórz \<name > wideo z zakresu od 00:00:00|HtmlVideo.Play(TimeSpan)|
|**Starać się w określonym czasie, w trakcie filmu wideo**|Wyszukiwanie \<name > film, aby 00:01:48|HtmlVideo.Seek(TimeSpan)|
|**Wstrzymaj wideo**<br /><br /> Bezpośrednio z kontrolki lub kontrolki prawym przyciskiem myszy.|Wstrzymaj \<name > wideo o 00:01:53|HtmlVideo.Pause(TimeSpan)|
|**Wycisz wideo**<br /><br /> Bezpośrednio z kontrolki lub kontrolki prawym przyciskiem myszy.|Wycisz \<name > wideo|HtmlVideo.Mute()|
|**Wyłącz Wyciszenie wideo**<br /><br /> Bezpośrednio z kontrolki lub kontrolki prawym przyciskiem myszy.|Wyłącz wyciszenie \<name > wideo|HtmlVideo.Unmute()|
|**Zmień ilość wideo**|Ustaw głośność \<name > wideo do 79%||

Zobacz [HTMLVideoElement](https://developer.mozilla.org/docs/Web/HTML/Element/video) listę właściwości, na których można dodać potwierdzenia.

 **Właściwości wyszukiwania:** Właściwości wyszukiwania `HtmlVideo` są `Id`, `Name` i `Title`.

 **Właściwości filtru:** Właściwości filtru dla `HtmlVideo` są `Src`, `Poster`, `Class`, `ControlDefinition` i `TagInstance`.

> [!NOTE]
> Jeśli przewinąć do tyłu lub szybkie przewijanie do przodu wideo przy użyciu etykiet-30s lub +30s, to zostaną zagregowane się w odpowiednim czasie.

## <a name="progressbar"></a>ProgressBar
 **ProgressBar — formant:** ProgressBar jest-interactable kontroli. Można dodać asercje `Value` i `Max` właściwości tej kontrolki. Aby uzyskać więcej informacji, zobacz [HTMLProgressElement](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/progress).

 ![HTML5 ProgressBar, kontrolka](../test/media/codedui_html5_progressbar.png)

## <a name="see-also"></a>Zobacz także

- [Elementy HTML](https://developer.mozilla.org/docs/Web/HTML/Element)
- [Używanie automatyzacji interfejsu użytkownika do testowania kodu](../test/use-ui-automation-to-test-your-code.md)
- [Tworzenie kodowanych testów interfejsu użytkownika](../test/use-ui-automation-to-test-your-code.md)
- [Obsługiwane konfiguracje oraz platformy zakodowanych testów interfejsu użytkownika i nagrywania akcji](../test/supported-configurations-and-platforms-for-coded-ui-tests-and-action-recordings.md)
