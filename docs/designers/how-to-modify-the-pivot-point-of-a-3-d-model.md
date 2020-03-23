---
title: 'Jak: Modyfikowanie punktu przestawnego modelu 3D'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: c20b4ec8-29f5-4ca5-bc39-d4548ca6f573
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 114beda700359eb5cdbfd4db12c18e442b8894f2
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "75589945"
---
# <a name="how-to-modify-the-pivot-point-of-a-3d-model"></a>Instrukcje: modyfikowanie punktu obrotu modelu 3D

W tym artykule pokazano, jak za pomocą Edytora modeli zmodyfikować *punkt przestawny* modelu 3D. Punkt obrotu jest punktem w przestrzeni, który definiuje matematyczny środek obiektu dla obrotu i skalowania.

## <a name="modify-the-pivot-point-of-a-3d-model"></a>Modyfikowanie punktu obrotu modelu 3D

Można ponownie zdefiniować początek modelu 3D, modyfikując jego punkt obrotu.

Upewnij się, że są wyświetlane okno **Właściwości** i **Przybornik.**

1. Zacznij od istniejącego modelu 3D, takiego jak opisany w [aplikacji Jak: Utwórz podstawowy model 3D](../designers/how-to-create-a-basic-3-d-model.md).

2. Wprowadź tryb obrotu. Na pasku narzędzi **Tryb edytora modelu** wybierz przycisk **Tryb przestawny,** aby włączyć tryb przestawny. Wokół przycisku **Tryb przestawny** pojawi się pole wskazujące, że Edytor modelu jest teraz w trybie przestawnym. W trybie przestawnym operacje takie jak tłumaczenie wpływają na punkt obrotu obiektu zamiast struktury obiektu w przestrzeni światowej.

3. Zmodyfikuj punkt obrotu obiektu. W trybie **wyboru** zaznacz obiekt, a następnie na pasku narzędzi **Podgląd modelu** wybierz narzędzie **Tłumacz.** Na powierzchni projektowej pojawi się pole reprezentujące punkt obrotu. Przesuń pole, aby zmodyfikować punkt obrotu obiektu.

     Przesuwając pole, można przesunąć punkt obrotu we wszystkich trzech wymiarach. Aby przetłumaczyć punkt obrotu wzdłuż jednej osi, przesuń strzałkę odpowiadającą tej osi. Pole i strzałki zmieniają kolor na żółty, aby wskazać oś, na którą ma wpływ tłumaczenie.

     Punkt przestawny można również określić za pomocą właściwości **Translacja przestawna** w oknie **Właściwości.**

    > [!TIP]
    > Efekt nowego punktu obrotu można wyświetlić, obracając obiekt. Aby go obrócić, użyj narzędzia **Obróć** lub zmodyfikuj właściwość **Obrót.**

Oto model, który ma zmodyfikowany punkt obrotu:

![Model domu, który ma zmodyfikowany punkt obrotu](../designers/media/digit-modified-model.png)

## <a name="see-also"></a>Zobacz też

- [Instrukcje: tworzenie podstawowego modelu 3D](../designers/how-to-create-a-basic-3-d-model.md)
- [Edytor modelu](../designers/model-editor.md)
