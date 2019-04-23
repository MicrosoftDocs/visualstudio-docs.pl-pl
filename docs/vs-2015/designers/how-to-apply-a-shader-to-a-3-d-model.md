---
title: 'Instrukcje: Stosowanie cieniowania do modelu 3-D | Dokumentacja firmy Microsoft'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-designers
ms.topic: conceptual
ms.assetid: a3877bd6-abd8-4a9d-842c-6848b6c2f335
caps.latest.revision: 17
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: a55c1e71242e59c04066c09efa2375c4bafc485b
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "60094780"
---
# <a name="how-to-apply-a-shader-to-a-3-d-model"></a>Instrukcje: Stosowanie cieniowania do modelu 3-D
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

W tym dokumencie przedstawiono sposób stosowanie cieniowania kierowane wykres modułu cieniującego języka (DGSL) do modelu 3D za pomocą edytora modelu.  
  
 W tym dokumencie przedstawiono to działanie:  
  
- Stosowanie cieniowania do modelu 3-D  
  
## <a name="applying-a-shader-to-a-3-d-model"></a>Stosowanie cieniowania do modelu 3-D  
 Efekt programu cieniującego można zastosować do modelu 3-D w celu nadania mu interesującym wyglądem.  
  
 Przed rozpoczęciem upewnij się, że **właściwości** zostanie wyświetlone okno.  
  
#### <a name="to-apply-a-shader-to-a-3-d-model"></a>Aby stosowanie cieniowania do modelu 3-D  
  
1. Rozpoczynają się od scenę 3-D, który zawiera co najmniej jednego modelu. Jeśli nie masz odpowiedniego scenę 3-D, utwórz ją zgodnie z opisem w [jak: Tworzenie podstawowego modelu 3-D](../designers/how-to-create-a-basic-3-d-model.md). Możesz również mieć modułu cieniującego DGSL, które można zastosować do modelu. Jeśli nie masz odpowiedniego programu do cieniowania, utwórz ją zgodnie z opisem w [jak: Tworzenie podstawowego cieniowania koloru](../designers/how-to-create-a-basic-color-shader.md) i upewnij się, że zapisane do pliku przed kontynuowaniem.  
  
2. W **wybierz** tryb, wybierz model, który chcesz zastosować programu do cieniowania, a następnie w **właściwości** okna w **Filename** właściwość **efektu**  właściwość konto należy do grupy określ modułu cieniującego DGSL, który chcesz zastosować do modelu.  
  
   Oto modelu, który ma zastosowano efekt kolor podstawowy:  
  
   ![3&#45;scen D, które przedstawiono efekt kolor podstawowy](../designers/media/digit-3d-model-effect.png "cyfrę 3D — Model-efektu")  
  
   Po zastosowaniu cieniowania do modelu, możesz go otworzyć w projektancie programu do cieniowania, wybierając modelu, a następnie w **właściwości** okna w **(zaawansowane)** właściwość **efekt**grupy właściwości, wybierając wielokropek (**...** ) przycisku.  
  
## <a name="see-also"></a>Zobacz też  
 [Instrukcje: Tworzenie podstawowego modelu 3-D](../designers/how-to-create-a-basic-3-d-model.md)   
 [Instrukcje: Tworzenie cieniowania koloru podstawowego](../designers/how-to-create-a-basic-color-shader.md)   
 [Edytor modelu](../designers/model-editor.md)   
 [Projektant cieniowania](../designers/shader-designer.md)
