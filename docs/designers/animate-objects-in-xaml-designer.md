---
title: Animowanie obiektów w projektancie XAML
ms.date: 04/11/2018
ms.topic: conceptual
ms.assetid: fb88fa26-e835-47f5-9771-2f279441c83c
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- uwp
ms.openlocfilehash: a5bd9c24351201d066f9055554468939df02b33e
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62927036"
---
# <a name="animate-objects-in-xaml-designer"></a>Animowanie obiektów w projektancie XAML

Tworzenie animacji w krótkim przenoszenie obiektów lub zanikanie je wewnątrz i na zewnątrz.

Aby rozpocząć, Utwórz *scenorysu*. Scenorysu zawiera jeden lub więcej *osi czasu*. Ustaw *klatki kluczowe* na osi czasu, aby oznaczyć zmiany właściwości. Następnie po uruchomieniu animacji, program Blend argumentu zmiany właściwości w wyznaczonym okresie. Wynikiem jest płynne przejście. Można animować dowolnej właściwości, która należy do obiektu, nawet właściwości niewizualnej.

Na poniższej ilustracji przedstawiono scenorysu o nazwie **MoveUp**. Oś czasu zawiera ramkami kluczowymi, który oznacza X i Y pozycja prostokąta. Po uruchomieniu ta animacja prostokąta bezproblemową z jednego miejsca do drugiego.

![MoveUp scenorysu w Projektancie XAML](../designers/media/982f031a-74a3-414a-abc2-a0f41a741075.png)

## <a name="see-also"></a>Zobacz także

- [Tworzenie interfejsu użytkownika przy użyciu programu Blend for Visual Studio](../designers/creating-a-ui-by-using-blend-for-visual-studio.md)