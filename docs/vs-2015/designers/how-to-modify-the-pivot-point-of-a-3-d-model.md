---
title: 'Instrukcje: modyfikowanie punktu obrotu modelu 3-D | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-designers
ms.topic: conceptual
ms.assetid: c20b4ec8-29f5-4ca5-bc39-d4548ca6f573
caps.latest.revision: 16
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: baeae2af825edc6a0032445288de7311b1ab1ae1
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72664406"
---
# <a name="how-to-modify-the-pivot-point-of-a-3-d-model"></a>Porady: modyfikowanie punktu obrotu modelu 3-D
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

W tym dokumencie przedstawiono sposób użycia Edytora modelu do modyfikacji *punktu obrotu* modelu 3-D. Punkt obrotu jest punktem w miejscu, który definiuje środek matematyczny obiektu do obrotu i skalowania.

 Ten dokument przedstawia następujące działania:

- Modyfikowanie punktu obrotu obiektu

## <a name="modifying-the-pivot-point-of-a-3-d-model"></a>Modyfikowanie punktu obrotu modelu 3-D
 Możesz zmienić definicję pochodzenia modelu 3-D, modyfikując jego punkt obrotu.

 Upewnij się, że wyświetlane jest okno **Właściwości** i **Przybornik** .

#### <a name="to-modify-the-pivot-point-of-a-3-d-model"></a>Aby zmodyfikować punkt obrotu modelu 3-D

1. Zacznij od istniejącego modelu trójwymiarowego, takiego jak ten, który jest opisany w artykule [jak: Tworzenie podstawowego modelu 3-d](../designers/how-to-create-a-basic-3-d-model.md).

2. Przejdź do trybu Pivot. Na pasku narzędzi **Tryb edytora modelu** wybierz przycisk **tryb Pivot** , aby uaktywnić tryb Pivot. Zostanie wyświetlone okno z przyciskiem **tryb tabeli przestawnej** , aby wskazać, że Edytor modelu jest teraz w trybie Pivot. W trybie Pivot operacje, takie jak tłumaczenie, wpływają na punkt obrotu obiektu, a nie strukturę obiektu w przestrzeni kosmicznej.

3. Zmodyfikuj punkt obrotu obiektu. W obszarze tryb **wyboru** wybierz obiekt, a następnie na pasku narzędzi **Podgląd modelu** wybierz narzędzie **tłumaczenie** . Pole reprezentujące punkt obrotu pojawia się na powierzchni projektowej. Przenieś pole, aby zmodyfikować punkt obrotu obiektu.

    Przenosząc pole, można przenieść punkt obrotu we wszystkich trzech wymiarach. Aby przetłumaczyć punkt obrotu wzdłuż jednej osi, przesuń strzałkę odpowiadającą tej osi. Pole i strzałki zmienią kolor na żółty, aby wskazać oo, na którą ma wpływ tłumaczenie.

    Punkt obrotu można także określić przy użyciu właściwości **translacja przestawnego** w oknie **Właściwości** .

   > [!TIP]
   > Efekt nowego punktu przestawnego można wyświetlić, obracając obiekt. Aby go obrócić, użyj narzędzia **Obróć** lub zmodyfikuj Właściwość **Rotation** .

   Oto model, który ma zmodyfikowany punkt obrotu:

   ![Model domu, który ma zmodyfikowany punkt obrotu](../designers/media/digit-modified-model.png "Model, który został zmodyfikowany")

## <a name="see-also"></a>Zobacz też
 [Instrukcje: Tworzenie podstawowego](../designers/how-to-create-a-basic-3-d-model.md) [Edytora modelu](../designers/model-editor.md) 3-D
