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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "75585590"
---
# <a name="using-html5-controls-in-coded-ui-tests"></a>Używanie formantów HTML5 w kodowanych testach interfejsu użytkownika

Kodowane testy interfejsu użytkownika obejmują obsługę niektórych formantów HTML5, które są zawarte w programach Internet Explorer 9 i Internet Explorer 10.

[!INCLUDE [coded-ui-test-deprecation](includes/coded-ui-test-deprecation.md)]

**Wymagania**

- Visual Studio Enterprise

> [!WARNING]
> W wersjach poprzedzających program Internet Explorer 10 można było uruchomić kodowane testy interfejsu użytkownika na wyższym poziomie uprawnień w porównaniu z procesem programu Internet Explorer. Podczas uruchamiania kodowanych testów interfejsu użytkownika w programie Internet Explorer 10 zarówno kodowany test interfejsu użytkownika, jak i proces programu Internet Explorer muszą znajdować się na tym samym poziomie uprawnień. Wynika to z bezpieczniejszych funkcji AppContainer w programie Internet Explorer 10.

> [!WARNING]
> Jeśli w programie Internet Explorer 10 zostanie utworzony kodowany test interfejsu użytkownika, może on nie zostać uruchomiony przy użyciu programu Internet Explorer 9 lub Internet Explorer 8. Dzieje się tak, ponieważ program Internet Explorer 10 zawiera formanty HTML5, takie jak audio, wideo, progressbar i slider. Te formanty HTML5 nie są rozpoznawane przez Internet Explorer 9 i Internet Explorer 8. Podobnie test interfejsu użytkownika kodowany za pomocą Internet Explorer 9 może zawierać niektóre formanty języka HTML5, które również nie zostaną rozpoznane przez Internet Explorer 8.

## <a name="audio-control"></a>Sterowanie dźwiękiem

**Sterowanie dźwiękiem:** Akcje na formancie HTML5 Audio są poprawnie rejestrowane i odtwarzane.

![Sterowanie dźwiękiem HTML5](../test/media/codedui_html5_audio.png)

|Akcja|Nagrywanie|Wygenerowany kod|
|-|---------------|-|
|**Odtwarzanie dźwięku**<br /><br /> Bezpośrednio z formantu lub z menu sterowania prawym przyciskiem myszy.|Nazwa \<odtwarzania> Audio od 00:00:00|HtmlAudio.Play(TimeSpan)|
|**Szukaj określonego czasu w dźwięku**|Szukaj \<nazwy> Audio do 00:01:48|HtmlAudio.Seek(TimeSpan)|
|**Wstrzymanie dźwięku**<br /><br /> Bezpośrednio z formantu lub z menu sterowania prawym przyciskiem myszy.|Nazwa \<pauzy> Audio o 00:01:53|HtmlAudio.pause(TimeSpan)|
|**Wyciszanie dźwięku**<br /><br /> Bezpośrednio z formantu lub z menu sterowania prawym przyciskiem myszy.|Nazwa \<wyciszenia> audio|HtmlAudio.Mute()|
|**Wyłączenie wyciszenia dźwięku**<br /><br /> Bezpośrednio z formantu lub z menu sterowania prawym przyciskiem myszy.|Co nie \<ma wyciszenia nazwy> audio|HtmlAudio.Unmute()|
|**Zmiana głośności dźwięku**|Ustawianie \<głośności nazwy> audio na 79%|HtmlAudio.SetVolume(float)|

Zobacz [HTMLAudioElement](https://developer.mozilla.org/docs/Web/API/HTMLAudioElement) listę właściwości, na których można dodać potwierdzenia.

**Właściwości wyszukiwania:** Właściwości wyszukiwania `HtmlAudio` to `Id`, `Name` `Title`i .

**Właściwości filtru:** Właściwości `HtmlAudio` filtru to `Src` `Class`, `ControlDefinition` `TagInstance`i .

> [!NOTE]
> Czas wyszukiwania i pauzy może być znaczący. Podczas odtwarzania kodowany test interfejsu użytkownika będzie czekać `(TimeSpan)` do określonego czasu przed wstrzymaniem dźwięku. Jeśli przez niektóre szczególne okoliczności, określony czas upłynął przed naciśnięciem Pause polecenia, wyjątek zostanie zgłoszony.

## <a name="video-control"></a>Sterowanie wideo
**Sterowanie wideo:** Akcje w formancie WIDEO HTML5 są poprawnie rejestrowane i odtwarzane.

![Sterowanie wideo HTML5](../test/media/codedui_html5_video.png)

|Akcja|Nagrywanie|Wygenerowany kod|
|-|---------------|-|
|**Odtwarzanie wideo**<br /><br /> Bezpośrednio z formantu lub z menu sterowania prawym przyciskiem myszy.|Nazwa \<odtwarzania> wideo od 00:00:00|HtmlVideo.Play(TimeSpan)|
|**Szukaj określonego czasu w filmie**|Szukaj \<nazwy> wideo do 00:01:48|HtmlVideo.Seek(TimeSpan)|
|**Wstrzymaj wideo**<br /><br /> Bezpośrednio z formantu lub z menu sterowania prawym przyciskiem myszy.|Wstrzymuj \<nazwę> Wideo o 00:01:53|HtmlVideo.Pause(TimeSpan)|
|**Wyciszanie wideo**<br /><br /> Bezpośrednio z formantu lub z menu sterowania prawym przyciskiem myszy.|Nazwa \<wyciszenia> wideo|HtmlVideo.Mute()|
|**Co nieprzemkotwóranie wyciszenia wideo**<br /><br /> Bezpośrednio z formantu lub z menu sterowania prawym przyciskiem myszy.|Co nie \<ma pracy,> wideo|HtmlVideo.Unmute()|
|**Zmienianie głośności wideo**|Ustaw głośność \<nazwy> Wideo na 79%||

Zobacz [HTMLVideoElement](https://developer.mozilla.org/docs/Web/HTML/Element/video) listę właściwości, na których można dodać potwierdzenia.

**Właściwości wyszukiwania:** Właściwości wyszukiwania `HtmlVideo` to `Id`, `Name` `Title`i .

**Właściwości filtru:** Właściwości filtru `HtmlVideo` to `Src` `Poster`, `Class` `ControlDefinition` , `TagInstance`i .

> [!NOTE]
> Jeśli przewiń do tyłu lub przewinąć do przodu wideo przy użyciu etykiet -30s lub +30s, zostanie to zagregowane w celu uzyskania odpowiedniego czasu.

## <a name="progressbar"></a>ProgressBar
**Kontrola ProgressBar:** ProgressBar jest formantem niewzdronia. Można dodać potwierdzenia na `Value` `Max` i właściwości tego formantu. Aby uzyskać więcej informacji, zobacz [HTMLProgressElement](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/progress).

![Kontrolka paska postępu HTML5](../test/media/codedui_html5_progressbar.png)

## <a name="see-also"></a>Zobacz też

- [Elementy HTML](https://developer.mozilla.org/docs/Web/HTML/Element)
- [Użyj automatyzacji interfejsu użytkownika, aby przetestować kod](../test/use-ui-automation-to-test-your-code.md)
- [Tworzenie kodowanych testów interfejsu użytkownika](../test/use-ui-automation-to-test-your-code.md)
- [Obsługiwane konfiguracje i platformy dla zakodowanych testów interfejsu użytkownika i nagrań akcji](../test/supported-configurations-and-platforms-for-coded-ui-tests-and-action-recordings.md)
