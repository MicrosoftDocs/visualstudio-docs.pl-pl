---
title: 'Instrukcje: Stosowanie cieniowania do modelu 3D'
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: a3877bd6-abd8-4a9d-842c-6848b6c2f335
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1f1ae981704287a74bb4e37117190b8b6111d0a9
ms.sourcegitcommit: f27084e64c79e6428746a20dda92795df996fb31
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85769240"
---
# <a name="how-to-apply-a-shader-to-a-3d-model"></a>Instrukcje: stosowanie cieniowania do modelu 3D

W tym artykule pokazano, jak za pomocą edytora modelu zastosować moduł cieniowania ukierunkowanego języka programu Graph (DGSL) do modelu 3W.

## <a name="apply-a-shader-to-a-3d-model"></a>Stosowanie cieniowania do modelu 3D

Możesz zastosować efekt cieniowania do modelu 3D, aby nadać mu interesujący wygląd.

Przed rozpoczęciem upewnij się, że wyświetlane jest okno **Właściwości** .

1. Zacznij od sceny 3D, która zawiera co najmniej jeden model. Jeśli nie masz odpowiedniej sceny 3W, utwórz ją zgodnie z opisem w temacie [How to: Create a Basic model 3D](../designers/how-to-create-a-basic-3-d-model.md). Musisz również mieć moduł DGSL, który można zastosować do modelu. Jeśli nie masz odpowiedniego modułu cieniującego, utwórz go zgodnie z opisem w temacie [How to: Create a Basic Color Shader](../designers/how-to-create-a-basic-color-shader.md) i upewnij się, że Zapisano go w pliku przed kontynuowaniem.

2. W obszarze tryb **wyboru** wybierz model, do którego chcesz zastosować program do cieniowania, a następnie w oknie **Właściwości** , we właściwości **filename** grupy właściwości **efekt** Określ moduł DGSL, który ma zostać zastosowany do modelu.

Oto model, do którego zastosowano podstawowy efekt koloru:

![3&#45;D scena pokazująca podstawowy efekt koloru](../designers/media/digit-3d-model-effect.png)

Po zastosowaniu cieniowania do modelu można otworzyć go w projektancie programu do cieniowania, wybierając model, a następnie w oknie **Właściwości** , we właściwości **(Zaawansowane)** grupy właściwości **efekt** , wybierając przycisk wielokropka (**...**).

## <a name="see-also"></a>Zobacz także

- [Instrukcje: tworzenie podstawowego modelu 3D](../designers/how-to-create-a-basic-3-d-model.md)
- [Instrukcje: tworzenie cieniowania koloru podstawowego](../designers/how-to-create-a-basic-color-shader.md)
- [Edytor modelu](../designers/model-editor.md)
- [Projektant cieniowania](../designers/shader-designer.md)
