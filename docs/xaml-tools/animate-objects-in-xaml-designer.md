---
title: Animowanie obiektów w projektancie XAML
titleSuffix: Blend for Visual Studio
ms.date: 07/31/2019
ms.topic: conceptual
ms.assetid: fb88fa26-e835-47f5-9771-2f279441c83c
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 23ddc7379e35fb060e34754f4188c04f91910ad0
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72649745"
---
# <a name="animate-objects-in-xaml-designer"></a>Animowanie obiektów w projektancie XAML

Blend for Visual Studio umożliwia łatwe tworzenie krótkich animacji, które przesuwają obiekty lub rozjaśniają je na przykład.

Aby utworzyć animację, potrzebujesz *scenorysu*. Scenorys zawiera jedną lub więcej *osi czasu*. Ustaw *klatki kluczowe* na osi czasu, aby oznaczyć zmiany właściwości. Następnie po uruchomieniu animacji Blend for Visual Studio interpoluje zmiany właściwości w wydanym okresie czasu. Wynikiem jest płynne przejście. Można animować każdą właściwość, która należy do obiektu, nawet niewizualną właściwości.

Poniższe obrazy przedstawiają scenorys o nazwie **Storyboard1**. Oś czasu zawiera ramki kluczowe, które oznaczają położenie X i Y prostokąta. Po uruchomieniu tej animacji prostokąt jest przenoszony z jednej pozycji do innej.

![Scenorys dla animacji w Blend for Visual Studio](media/storyboard-timeline.png)

## <a name="create-an-animation"></a>Tworzenie animacji

1. Aby utworzyć scenorys, wybierz przycisk **opcji scenorysu** w oknie **obiekty i oś czasu** , a następnie wybierz pozycję **Nowy**.

   ![Dodawanie scenorysu w Blend for Visual Studio](media/new-storyboard.png)

2. W oknie dialogowym **Tworzenie zasobu scenorysu** wprowadź nazwę scenorysu.

3. W panelu **składniki** w widok Projekt Dodaj prostokąt do lewej dolnej strony strony.

   ![Prostokąt w panelu elementy zawartości projektant XAML](media/add-rectangle.PNG)

4. W oknie **obiekty i oś czasu** Przenieś żółty wskaźnik czasu do **3** sekund.

   ![Wskaźnik czasu na osi czasu](media/timeline-indicator.PNG)

5. W widok Projekt na stronie przeciągnij prostokąt do prawej strony strony.

6. Naciśnij przycisk **Odtwórz** , aby obejrzeć prostokąt przeniesiony z lewej strony do prawej strony.

Odtwarzaj inne zmiany w prostokącie w różnych punktach w czasie. Na przykład możesz zmienić kolor wypełnienia lub przerzucić orientację w okno Właściwości.

## <a name="see-also"></a>Zobacz także

- [Tworzenie interfejsu użytkownika przy użyciu programu Blend for Visual Studio](../xaml-tools/creating-a-ui-by-using-blend-for-visual-studio.md)