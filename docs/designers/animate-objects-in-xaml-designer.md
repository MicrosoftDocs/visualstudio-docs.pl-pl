---
title: Animowanie obiektów w projektancie XAML
ms.date: 04/11/2018
ms.prod: visual-studio-dev15
ms.topic: conceptual
ms.assetid: fb88fa26-e835-47f5-9771-2f279441c83c
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- uwp
ms.openlocfilehash: 312721cb47858d3c5462fcbee99289dbad526180
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53941495"
---
# <a name="animate-objects-in-xaml-designer"></a>Animowanie obiektów w projektancie XAML

Tworzenie animacji w krótkim przenoszenie obiektów lub zanikanie je wewnątrz i na zewnątrz.

Aby rozpocząć, Utwórz *scenorysu*. Scenorysu zawiera jeden lub więcej *osi czasu*. Ustaw *klatki kluczowe* na osi czasu, aby oznaczyć zmiany właściwości. Następnie po uruchomieniu animacji, program Blend argumentu zmiany właściwości w wyznaczonym okresie. Wynikiem jest płynne przejście. Można animować dowolnej właściwości, która należy do obiektu, nawet właściwości niewizualnej.

Na poniższej ilustracji przedstawiono scenorysu o nazwie **MoveUp**. Oś czasu zawiera ramkami kluczowymi, który oznacza X i Y pozycja prostokąta. Po uruchomieniu ta animacja prostokąta bezproblemową z jednego miejsca do drugiego.

![MoveUp scenorysu w Projektancie XAML](../designers/media/982f031a-74a3-414a-abc2-a0f41a741075.png)

## <a name="see-also"></a>Zobacz także

- [Tworzenie interfejsu użytkownika przy użyciu programu Blend for Visual Studio](../designers/creating-a-ui-by-using-blend-for-visual-studio.md)