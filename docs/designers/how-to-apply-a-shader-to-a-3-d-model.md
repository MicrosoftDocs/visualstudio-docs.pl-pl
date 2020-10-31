---
title: 'Instrukcje: Stosowanie cieniowania do modelu 3D'
description: Dowiedz się, w jaki sposób używać edytora modelu, aby zastosować do modelu 3D trójwymiarowy program do cieniowania języka programu Graph w celu uzyskania interesującego wyglądu.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: a3877bd6-abd8-4a9d-842c-6848b6c2f335
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7b31e9002a97decf699ffbd589a1e0e656e3e403
ms.sourcegitcommit: a731a9454f1fa6bd9a18746d8d62fe2e85e5ddb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2020
ms.locfileid: "93134122"
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

Po zastosowaniu cieniowania do modelu można otworzyć go w projektancie programu do cieniowania, wybierając model, a następnie w oknie **Właściwości** , we właściwości **(Zaawansowane)** grupy właściwości **efekt** , wybierając przycisk wielokropka ( **...** ).

## <a name="see-also"></a>Zobacz też

- [Instrukcje: tworzenie podstawowego modelu 3D](../designers/how-to-create-a-basic-3-d-model.md)
- [Instrukcje: tworzenie cieniowania koloru podstawowego](../designers/how-to-create-a-basic-color-shader.md)
- [Edytor modelu](../designers/model-editor.md)
- [Projektant cieniowania](../designers/shader-designer.md)
