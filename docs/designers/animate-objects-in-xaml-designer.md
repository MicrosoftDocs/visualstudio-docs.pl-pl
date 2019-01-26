---
title: Animowanie obiektów w projektancie XAML
ms.date: 04/11/2018
ms.prod: visual-studio-dev15
ms.topic: conceptual
ms.assetid: fb88fa26-e835-47f5-9771-2f279441c83c
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- uwp
ms.openlocfilehash: f6fbeceeb0c9943e561c5bd4e353551005be23a4
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "54960207"
---
# <a name="animate-objects-in-xaml-designer"></a>Animowanie obiektów w projektancie XAML

Tworzenie animacji w krótkim przenoszenie obiektów lub zanikanie je wewnątrz i na zewnątrz.

Aby rozpocząć, Utwórz *scenorysu*. Scenorysu zawiera jeden lub więcej *osi czasu*. Ustaw *klatki kluczowe* na osi czasu, aby oznaczyć zmiany właściwości. Następnie po uruchomieniu animacji, program Blend argumentu zmiany właściwości w wyznaczonym okresie. Wynikiem jest płynne przejście. Można animować dowolnej właściwości, która należy do obiektu, nawet właściwości niewizualnej.

Na poniższej ilustracji przedstawiono scenorysu o nazwie **MoveUp**. Oś czasu zawiera ramkami kluczowymi, który oznacza X i Y pozycja prostokąta. Po uruchomieniu ta animacja prostokąta bezproblemową z jednego miejsca do drugiego.

![MoveUp scenorysu w Projektancie XAML](../designers/media/982f031a-74a3-414a-abc2-a0f41a741075.png)

## <a name="see-also"></a>Zobacz także

- [Tworzenie interfejsu użytkownika przy użyciu programu Blend for Visual Studio](../designers/creating-a-ui-by-using-blend-for-visual-studio.md)