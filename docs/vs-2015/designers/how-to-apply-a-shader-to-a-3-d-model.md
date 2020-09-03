---
title: 'Instrukcje: Stosowanie cieniowania do modelu 3-D | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-designers
ms.topic: conceptual
ms.assetid: a3877bd6-abd8-4a9d-842c-6848b6c2f335
caps.latest.revision: 17
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 15d88f52b3af3a3e4502c618280107a882761259
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "72664612"
---
# <a name="how-to-apply-a-shader-to-a-3-d-model"></a>Porady: stosowanie cieniowania do modelu 3-D
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

W tym dokumencie pokazano, jak za pomocą edytora modelu zastosować moduł cieniowania ukierunkowanego języka programu Graph (DGSL) do modelu 3-D.

 Ten dokument przedstawia następujące działania:

- Stosowanie cieniowania do modelu 3-D

## <a name="applying-a-shader-to-a-3-d-model"></a>Stosowanie cieniowania do modelu 3-D
 Możesz zastosować efekt cieniowania do modelu 3-D, aby nadać mu interesujący wygląd.

 Przed rozpoczęciem upewnij się, że wyświetlane jest okno **Właściwości** .

#### <a name="to-apply-a-shader-to-a-3-d-model"></a>Aby zastosować cieniowanie do modelu 3-D

1. Zacznij od sceny trójwymiarowej, która zawiera co najmniej jeden model. Jeśli nie masz odpowiedniej sceny trójwymiarowej, utwórz ją zgodnie z opisem w temacie [How to: Create a Basic model 3-D](../designers/how-to-create-a-basic-3-d-model.md). Trzeba również mieć moduł DGSL, który można zastosować do modelu. Jeśli nie masz odpowiedniego modułu cieniującego, utwórz go zgodnie z opisem w temacie [How to: Create a Basic Color Shader](../designers/how-to-create-a-basic-color-shader.md) i upewnij się, że Zapisano go w pliku przed kontynuowaniem.

2. W obszarze tryb **wyboru** wybierz model, do którego chcesz zastosować program do cieniowania, a następnie w oknie **Właściwości** , we właściwości **filename** grupy właściwości **efekt** Określ moduł DGSL, który ma zostać zastosowany do modelu.

   Oto model, do którego zastosowano podstawowy efekt koloru:

   ![3&#45;D scena pokazująca podstawowy efekt koloru](../designers/media/digit-3d-model-effect.png "Cyfra-3W — model — efekt")

   Po zastosowaniu cieniowania do modelu można otworzyć go w projektancie programu do cieniowania, wybierając model, a następnie w oknie **Właściwości** , we właściwości **(Zaawansowane)** grupy właściwości **efekt** , wybierając przycisk wielokropka (**...**).

## <a name="see-also"></a>Zobacz też
 [Instrukcje: Tworzenie podstawowego modelu 3-D](../designers/how-to-create-a-basic-3-d-model.md) [: Tworzenie podstawowego edytora kolorów programu do cieniowania —](../designers/how-to-create-a-basic-color-shader.md) [Model Editor](../designers/model-editor.md) [Projektant cieniowania](../designers/shader-designer.md)
