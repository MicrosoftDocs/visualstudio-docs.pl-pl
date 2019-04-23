---
title: 'Instrukcje: Modyfikowanie punktu obrotu modelu 3D'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: c20b4ec8-29f5-4ca5-bc39-d4548ca6f573
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1b1baa6a42d0874cdefaa8cfb781f66e864d82b2
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "60055278"
---
# <a name="how-to-modify-the-pivot-point-of-a-3d-model"></a>Instrukcje: Modyfikowanie punktu obrotu modelu 3D

W tym artykule przedstawiono sposób używania edytora modelu do modyfikowania *punkt obrotu* modelu 3D. Punkt obrotu jest punktem w miejscu, definiująca środek matematyczne obiektu dla obrotu i skalowania.

## <a name="modify-the-pivot-point-of-a-3d-model"></a>Modyfikowanie punktu obrotu modelu 3D

Pochodzenie modelu 3D można zmienić, modyfikując jego punktu obrotu.

Upewnij się, że **właściwości** okna i **przybornika** są wyświetlane.

1. Zacznij od istniejącego modelu 3D, takiego jak opisany w [jak: Tworzenie podstawowego modelu 3D](../designers/how-to-create-a-basic-3-d-model.md).

2. Wprowadź tryb obrotu. Na **tryb edytora modelu** narzędzi, wybierz **tryb obrotu** przycisk, aby uaktywnić tryb obrotu. Zostanie wyświetlone okno z całym **tryb obrotu** przycisk, aby wskazać, że edytor modelu jest teraz tryb obrotu. W tryb obrotu operacji, takich jak tłumaczenia wpływają na punkt obrotu obiektu zamiast struktury obiektów w przestrzeni świata.

3. Modyfikowanie punktu obrotu obiektu. W **wybierz** tryb, wybierz obiekt, a następnie na **przeglądarka modelu** narzędzi, wybierz **Translate** narzędzia. Pole, który reprezentuje punkt obrotu jest wyświetlany na powierzchni projektowej. Przenieś pole, aby zmodyfikować punkt obrotu obiektu.

     Przenosząc pole, możesz przenieść punkt obrotu we wszystkich trzech wymiarach. Do translacji punktu obrotu wzdłuż osi, Przenieś strzałkę, która odnosi się do tej osi. Strzałki i pole Zmień kolor żółty, aby wskazać osi, który jest zależna od tłumaczenia.

     Można również określić przy użyciu punktu obrotu **Translacja punktu centralnego** właściwość **właściwości** okna.

    > [!TIP]
    > Aby wyświetlić efekt nowego punktu obrotu, obracanie obiektu. Aby obrócić go, należy użyć **Obróć** narzędzia lub zmodyfikować **obrotu** właściwości.

Oto modelu, który ma punkt obrotu zmodyfikowane:

![Model DOM, zawierający punkt obrotu zmodyfikowane](../designers/media/digit-modified-model.png)

## <a name="see-also"></a>Zobacz także

- [Instrukcje: Tworzenie podstawowego modelu 3D](../designers/how-to-create-a-basic-3-d-model.md)
- [Edytor modelu](../designers/model-editor.md)