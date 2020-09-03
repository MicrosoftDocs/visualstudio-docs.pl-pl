---
title: Animowanie obiektów w projektant XAML | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-designers
ms.topic: conceptual
ms.assetid: fb88fa26-e835-47f5-9771-2f279441c83c
caps.latest.revision: 11
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: ea2fdf1f47385a9be26fa65a93b9104b2d864079
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "72658022"
---
# <a name="animate-objects-in-xaml-designer"></a>Animowanie obiektów w projektancie XAML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Można tworzyć krótkie animacje, które przesuwają obiekty lub rozjaśniają je w i na zewnątrz.

 Aby rozpocząć, Utwórz *scenorys*. Scenorys zawiera jedną lub więcej *osi czasu*. Ustaw *klatki kluczowe* na osi czasu, aby oznaczyć zmiany właściwości. Następnie po uruchomieniu animacji program Blend interpoluje zmiany właściwości w wydanym okresie czasu. Wynikiem jest płynne przejście. Można animować każdą właściwość, która należy do obiektu, nawet niewizualną właściwości.

 Na poniższej ilustracji przedstawiono scenorys o nazwie **górę**. Oś czasu zawiera ramki kluczowe, które oznaczają położenie X i Y prostokąta. Po uruchomieniu tej animacji prostokąt jest przenoszony z jednej pozycji do innej.

 ![](../designers/media/982f031a-74a3-414a-abc2-a0f41a741075.png "982f031a-74a3-414a-abc2-a0f41a741075")

 Dowiedz się, jak tworzyć animacje, obserwując te wideo.

|Obejrzyj krótkie wideo:|Instrukcje:|
|--------------------------|-------------------|
|![Konfigurowanie zainstalowanych funkcji](../designers/media/bldadminconsoleinitialconfigicon.PNG "BldAdminConsoleInitialConfigIcon") [Tworzenie osi czasu](http://www.popscreen.com/v/6A4eF/Microsoft-Expression-Blend-Creating-Timelines)|Utwórz oś czasu i pracuj z obiektami na osi czasu.|
|![Konfigurowanie zainstalowanych funkcji](../designers/media/bldadminconsoleinitialconfigicon.PNG "BldAdminConsoleInitialConfigIcon") [Dodaj klatki kluczowe i powtórz animację](http://www.popscreen.com/v/6A4fi/Microsoft-Expression-Blend-Adding-Keyframes-and-Repeating-an-Animation)|Dodaj klatki kluczowe i ustaw właściwości w każdej klatce kluczowej. Następnie Uruchom animację i obserwuj obiekty płynnie przechodzą między nimi.|
|![Konfigurowanie zainstalowanych funkcji](../designers/media/bldadminconsoleinitialconfigicon.PNG "BldAdminConsoleInitialConfigIcon") [Dodaj wyzwalacze zdarzeń dla funkcji interaktywny](http://www.popscreen.com/v/6A4e4/Microsoft-Expression-Blend-Adding-Event-Triggers-for-Interactivity)|Rozpocznij animację w przypadku wystąpienia zdarzenia. Na przykład uruchom je po załadowaniu okna.|
|![Konfigurowanie zainstalowanych funkcji](../designers/media/bldadminconsoleinitialconfigicon.PNG "BldAdminConsoleInitialConfigIcon") [Animuj kolory](http://www.popscreen.com/v/6A4gv/Microsoft-Expression-Blend-Animating-Colors)|Zmień kolor obiektu za pomocą animacji.|
|![Konfigurowanie zainstalowanych funkcji](../designers/media/bldadminconsoleinitialconfigicon.PNG "BldAdminConsoleInitialConfigIcon") [Tworzenie i modyfikowanie ścieżek ruchu](http://www.popscreen.com/v/6A4fX/Microsoft-Expression-Blend-Creating-and-Modifying-Motion-Paths)|Animuj obiekty wzdłuż ścieżki.|
|![Konfiguruj zainstalowane funkcje](../designers/media/bldadminconsoleinitialconfigicon.PNG "BldAdminConsoleInitialConfigIcon") [ułatwiają klatki kluczowe](http://www.popscreen.com/v/6A4dM/Microsoft-Expression-Blend-Easing-Keyframes)|Przyspiesz lub spowalniaj animację w sąsiedztwie początku (*Krzywa napięcia w programie*) lub blisko końca (*Krzywa napięcia*) animacji.|
|![Konfigurowanie zainstalowanych funkcji](../designers/media/bldadminconsoleinitialconfigicon.PNG "BldAdminConsoleInitialConfigIcon") [Animuj przycisk](http://www.popscreen.com/v/6A4fK/Microsoft-Expression-Blend-Animating-a-Button)|Twórz interesujące efekty, które pojawiają się na przycisku, gdy użytkownik wskaże go.|
|![Konfigurowanie zainstalowanych funkcji](../designers/media/bldadminconsoleinitialconfigicon.PNG "BldAdminConsoleInitialConfigIcon") [Tworzenie animacji i pracy z funkcją napięcia](https://www.youtube.com/watch?v=mAJXYrwxGYo)|Animowanie efektów, które pojawiają się, gdy użytkownik naciśnie przycisk w obrazie kalkulatora.|

## <a name="see-also"></a>Zobacz też
 [Tworzenie interfejsu użytkownika przy użyciu programu Blend for Visual Studio](../designers/creating-a-ui-by-using-blend-for-visual-studio.md)
