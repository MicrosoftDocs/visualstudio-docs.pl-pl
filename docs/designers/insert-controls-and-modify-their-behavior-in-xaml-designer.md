---
title: Wstawianie kontrolek i modyfikowanie ich zachowania w programie Projektant XAML
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: conceptual
ms.assetid: a80fff74-bf01-41c9-ab85-ada7a873c3a9
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- uwp
ms.openlocfilehash: 28bc12cf483c9b988f4793aa03c6c6b0ced8e647
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "54979754"
---
# <a name="insert-controls-and-modify-their-behavior-in-xaml-designer"></a>Wstawianie kontrolek i modyfikowanie ich zachowania w programie Projektant XAML

Kontrolki umożliwiają użytkownikom na interakcję z aplikacją. Można użyć ich do zbierania informacji i wykonywanie działań takich jak animować obiekt lub zbadać źródło danych.

## <a name="add-controls-to-the-artboard"></a>Dodawanie formantów do obszaru kompozycji

Można przeciągać formantów z **zasoby** panelu na **obszaru kompozycji**, a następnie zmodyfikuj je w **właściwości** okna.

![Formanty karty zasobów programu Blend](../designers/media/blend_assetsflipview_xaml.png)

### <a name="make-a-control-out-of-an-image-shape-or-path"></a>Kontrolka poza obrazu, kształtu lub ścieżki

Można wprowadzić dowolny obiekt w kontrolce.

![Okno dialogowe przerób na kontrolkę w programie Blend](../designers/media/blend_makeintocontrol_xaml.png)

Na przykład Wyobraź sobie obraz telewizyjnych w środkowej części strony. Można utworzyć kontrolki poza małe obrazy, które wyglądają jak przyciski telewizyjnych w Twoim regionie. Następnie można kliknięciu tych przycisków, aby zmienić kanału.

Jest to możliwe, ponieważ przyciski są teraz kontrolki. Za pomocą kontrolek możesz odpowiedzieć na interakcję użytkownika; w tym przypadku, gdy użytkownik kliknie przycisk.

Aby utworzyć formant, zaznacz obiekt. Następnie na **narzędzia** menu, kliknij przycisk **wprowadzić formant**.

## <a name="make-controls-do-things"></a>Umożliwianie wykonywały formantów

Formanty może wykonywać akcje podczas interakcji z użytkownikiem. Na przykład one Rozpocznij animację, zaktualizować źródło danych lub odtworzyć wideo.

Użyj *wyzwalaczy*, *zachowania*, i *zdarzenia* aby wykonywały kontrolki.

### <a name="triggers"></a>Wyzwalacze

A *wyzwalacza* zmiany właściwości lub wykonuje zadanie w odpowiedzi na zdarzenie lub zmianę w innej właściwości. Na przykład możesz zmienić kolor przycisku po umieszczeniu nad nim.

![Panel wyzwalaczy](../designers/media/custom_button_blend_propertytriggerinfo.png)

### <a name="behaviors"></a>Zachowania

A *zachowanie* pakiet do ponownego wykorzystania kodu. Go może zrobić coś więcej niż zmiany właściwości. Może wykonywać akcje, takie jak zapytania usługi danych. Blend jest dostarczany z małych Kolekcja zachowań, ale można dodać więcej. Przeciągnij zachowanie na dowolnego obiektu w Twojego obszaru roboczego, a następnie dostosować zachowanie przez ustawienie właściwości.

![FluidMoveBehavior, w panelu Właściwości](../designers/media/b4_fluidmovebehaviorproperties_sample.png)

**Obejrzyj film wideo:** ![Odtwórz ikonę](../designers/media/bldadminconsoleinitialconfigicon.PNG) [Blend porad: Wprowadzenie do usługi za pomocą zachowań część 1](http://www.bing.com/videos/search?q=Expression%20blend%20behaviors&qs=n&form=QBVR&pq=expression%20blend%20behavior&sc=4-25&sp=-1&sk=#view=detail&mid=CF0DD797ED84DE740904CF0DD797ED84DE740904).

### <a name="events"></a>Zdarzenia

Ultimate elastyczność obsługi *zdarzeń*. Będziesz mieć do napisania kodu.