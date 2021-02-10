---
title: 'Instrukcje: modyfikowanie punktu obrotu modelu 3W'
description: Dowiedz się, w jaki sposób używać edytora modelu do modyfikowania punktu obrotu modelu 3W, który jest punktem, który definiuje środek obiektu do obrotu i skalowania.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: c20b4ec8-29f5-4ca5-bc39-d4548ca6f573
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 4eaa3d671a8c9aeb3ed942e57278160af73dec19
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99930840"
---
# <a name="how-to-modify-the-pivot-point-of-a-3d-model"></a>Instrukcje: modyfikowanie punktu obrotu modelu 3D

W tym artykule pokazano, jak zmodyfikować *punkt obrotu* modelu 3D przy użyciu edytora modelu. Punkt obrotu jest punktem w miejscu, który definiuje środek matematyczny obiektu do obrotu i skalowania.

## <a name="modify-the-pivot-point-of-a-3d-model"></a>Modyfikowanie punktu obrotu modelu 3D

Możesz zmienić definicję pochodzenia modelu 3D, modyfikując jego punkt obrotu.

Upewnij się, że wyświetlane jest okno **Właściwości** i **Przybornik** .

1. Zacznij od istniejącego modelu 3D, takiego jak ten, który został opisany w artykule [jak: Tworzenie podstawowego modelu 3W](../designers/how-to-create-a-basic-3-d-model.md).

2. Przejdź do trybu Pivot. Na pasku narzędzi **Tryb edytora modelu** wybierz przycisk **tryb Pivot** , aby uaktywnić tryb Pivot. Zostanie wyświetlone okno z przyciskiem **tryb tabeli przestawnej** , aby wskazać, że Edytor modelu jest teraz w trybie Pivot. W trybie Pivot operacje, takie jak tłumaczenie, wpływają na punkt obrotu obiektu, a nie strukturę obiektu w przestrzeni kosmicznej.

3. Zmodyfikuj punkt obrotu obiektu. W obszarze tryb **wyboru** wybierz obiekt, a następnie na pasku narzędzi **Podgląd modelu** wybierz narzędzie **tłumaczenie** . Pole reprezentujące punkt obrotu pojawia się na powierzchni projektowej. Przenieś pole, aby zmodyfikować punkt obrotu obiektu.

     Przenosząc pole, można przenieść punkt obrotu we wszystkich trzech wymiarach. Aby przetłumaczyć punkt obrotu wzdłuż jednej osi, przesuń strzałkę odpowiadającą tej osi. Pole i strzałki zmienią kolor na żółty, aby wskazać oo, na którą ma wpływ tłumaczenie.

     Punkt obrotu można także określić przy użyciu właściwości **translacja przestawnego** w oknie **Właściwości** .

    > [!TIP]
    > Efekt nowego punktu przestawnego można wyświetlić, obracając obiekt. Aby go obrócić, użyj narzędzia **Obróć** lub zmodyfikuj Właściwość **Rotation** .

Oto model, który ma zmodyfikowany punkt obrotu:

![Model domu, który ma zmodyfikowany punkt obrotu](../designers/media/digit-modified-model.png)

## <a name="see-also"></a>Zobacz też

- [Instrukcje: tworzenie podstawowego modelu 3D](../designers/how-to-create-a-basic-3-d-model.md)
- [Edytor modelu](../designers/model-editor.md)
