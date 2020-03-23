---
title: 'Jak: Stosowanie modułu cieniującego do modelu 3D'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: a3877bd6-abd8-4a9d-842c-6848b6c2f335
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2ae04f4cc0afb1c24f391d140081040efe9db50e
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "76112755"
---
# <a name="how-to-apply-a-shader-to-a-3d-model"></a>Instrukcje: stosowanie cieniowania do modelu 3D

W tym artykule pokazano, jak za pomocą Edytora modeli zastosować program cieniujący directed Graph Shader Language (DGSL) do modelu 3D.

## <a name="apply-a-shader-to-a-3d-model"></a>Stosowanie cieniowania do modelu 3D

Efekt cieniowania można zastosować do modelu 3D, aby nadać mu interesujący wygląd.

Przed rozpoczęciem upewnij się, że jest wyświetlane okno **Właściwości.**

1. Zacznij od sceny 3D zawierającej jeden lub więcej modeli. Jeśli nie masz odpowiedniej sceny 3D, utwórz ją zgodnie z opisem w jak opisano w [obszarze Jak: Utwórz podstawowy model 3D](../designers/how-to-create-a-basic-3-d-model.md). Należy również mieć moduł cieniujący DGSL, który można zastosować do modelu. Jeśli nie masz odpowiedniego modułu cieniującego, utwórz go zgodnie z opisem w [obszarze Jak: Utwórz podstawowy moduł cieniujący kolorów](../designers/how-to-create-a-basic-color-shader.md) i upewnij się, że został zapisany w pliku przed kontynuowaniem.

2. W trybie **wyboru** wybierz model, do którego chcesz zastosować moduł cieniujący, a następnie w oknie **Właściwości** we właściwości **Nazwa pliku** grupy właściwości **Effect** określ moduł cieniujący DGSL, który ma zostać zastosowane do modelu.

Oto model, który ma podstawowy efekt koloru stosowane do niego:

![3&#45;scena D, która pokazuje podstawowy efekt koloru](../designers/media/digit-3d-model-effect.png)

Po zastosowaniu modułu cieniującego do modelu można go otworzyć w Projektancie **modułu** cieniującego, wybierając model, a następnie w oknie Właściwości we właściwości **(Zaawansowane)** grupy właściwości **Effect,** wybierając przycisk wielokropek (**...**).

## <a name="see-also"></a>Zobacz też

- [Instrukcje: tworzenie podstawowego modelu 3D](../designers/how-to-create-a-basic-3-d-model.md)
- [Instrukcje: tworzenie cieniowania koloru podstawowego](../designers/how-to-create-a-basic-color-shader.md)
- [Edytor modelu](../designers/model-editor.md)
- [Projektant cieniowania](../designers/shader-designer.md)
