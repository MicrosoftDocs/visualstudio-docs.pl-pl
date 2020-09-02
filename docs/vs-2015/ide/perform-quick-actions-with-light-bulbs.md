---
title: Wykonaj szybkie akcje z żarówkami | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
ms.assetid: 990ee487-cf9a-4b89-9784-e7b47c220e8c
caps.latest.revision: 9
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 78ac9b0aba4e56b2240ef65783231d31d77e5144
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "72670349"
---
# <a name="perform-quick-actions-with-light-bulbs"></a>Szybkie wykonywanie akcji dzięki żarówkom
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Żarówki są nową funkcją produktywności w programie Visual Studio 2015. Są to ikony, które pojawiają się w edytorze programu Visual Studio i można kliknąć, aby wykonać szybkie akcje, w tym refaktoryzację usuwania błędów. Żarówki umożliwiają naprawianie błędów i refaktoryzację pomocy w pojedynczym punkcie ogniskowym, często bezpośrednio w wierszu, w którym wpisujesz.

 ![Ikona małej żarówki](../ide/media/vs2015-lightbulbsmall.png "VS2015_LightBulbSmall")

 W języku C# i Visual Basic zobaczysz żarówkę, jeśli istnieje czerwona zygzakowata i program Visual Studio ma sugestię dotyczącą sposobu rozwiązania problemu. Jeśli na przykład wystąpi błąd wskazywany przez czerwony zygzak, zostanie wyświetlona Żarówka, gdy poprawki będą dostępne dla tego błędu. W języku C++, gdy dodasz nową funkcję do pliku nagłówkowego, zobaczysz żarówkę, która oferuje możliwość utworzenia wbudowanej implementacji tej funkcji. W przypadku dowolnego języka osoby trzecie mogą zapewnić niestandardową diagnostykę i sugestie, na przykład w ramach zestawu SDK, a żarówki programu Visual Studio na podstawie tych reguł.

## <a name="to-see-a-light-bulb"></a>Aby wyświetlić żarówkę

1. W wielu przypadkach żarówki są spontanicznie wyświetlane po umieszczeniu wskaźnika myszy w punkcie błędu lub na lewym marginesie edytora po przesunięciu karetki do wiersza, który zawiera błąd. Gdy zobaczysz czerwony zygzak, możesz go umieścić nad nim, aby wyświetlić żarówkę. Możesz również sprawić, aby żarówka była wyświetlana po użyciu myszy lub klawiatury, aby przejść do dowolnego miejsca w wierszu, w którym występuje problem.

2. Naciśnij **klawisze CTRL +.** w dowolnym miejscu w wierszu, aby wywołać żarówkę i przejść bezpośrednio do listy potencjalnych poprawek.

   ![Żarówka z przesuwaniem myszy](../ide/media/vs2015-lightbulb-hover.png "VS2015_LightBulb_Hover")

## <a name="to-see-potential-fixes"></a>Aby wyświetlić potencjalne poprawki
 Kliknij strzałkę w dół lub link Pokaż potencjalne poprawki, aby wyświetlić listę szybkich akcji, które można wykonać za pomocą żarówki.

 ![Rozwinięta żarówka](../ide/media/vs2015-lightbulb-hover-expanded.png "VS2015_LightBulb_hover_expanded")

## <a name="to-do-a-refactoring"></a>Aby wykonać refaktoryzację
 Można nadal wykonywać refaktoryzacje przez kliknięcie prawym przyciskiem myszy, aby wyświetlić menu kontekstowe, ale można również nacisnąć klawisze CTRL +. Aby wyświetlić opcje refaktoryzacji. Na poniższej ilustracji jest oferowana Refaktoryzacja metody wyodrębniania po naciśnięciu klawiszy CTRL +. gdzieś w wierszu, który zawiera `Math.Abs` wywołanie:

 ![Żarówka przedstawiająca opcje refaktoryzacji](../ide/media/vs2015-lightbulbs-refactor.png "VS2015_LightBulbs_refactor")
