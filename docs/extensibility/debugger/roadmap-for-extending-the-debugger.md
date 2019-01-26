---
title: Plan rozwoju rozszerzania debugera | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], roadmap
- Debugging SDK, roadmap
ms.assetid: 1f4096a8-f7aa-4dfa-84e1-6d59263e70bb
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 637452fe5b36860cd23385f4a041872ea9dfeb0f
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "55013473"
---
# <a name="roadmap-for-extending-the-debugger"></a>Plan rozwoju rozszerzania debugera
Ta dokumentacja zawiera przewodnik i informacje do rozszerzania [!INCLUDE[vs_current_short](../../code-quality/includes/vs_current_short_md.md)] debugera za pomocą [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)].  
  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] debugowanie dokumentacji zawiera przykłady, stanowią wyczerpujące Kompendium i kilka reprezentatywny scenariusze, które pokazują typowe sposoby dostosowywania debugera.  
  
 Kompilator i jego danych wyjściowych określają, co to są wymagane do skonfigurowania debugowania w programie. Jeśli kompilator:  
  
- Jest przeznaczony dla natywnego systemu operacyjnego Windows i zapisuje *. Plik PDB* pliku, można debugować programy przy użyciu aparatu debugowania kodu macierzystego (DE), która jest zintegrowana [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Nie trzeba implementować ewaluatora DE lub wyrażenie. Ewaluator wyrażeń jest przeznaczony dla składni języka programowania C++.  
  
- Tworzy Microsoft intermediate language (MSIL). dane wyjściowe, można debugować programy przy użyciu aparatu debugowania kodu zarządzanego DE, która jest również zintegrowana [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. W związku z tym należy zaimplementować tylko ewaluatora wyrażeń. Ewaluator wyrażeń próbki jest dostarczany. Więcej informacji znajduje się w następujących tematach:  
  
   [Szacowanie wyrażeń](../../extensibility/debugger/expression-evaluation-visual-studio-debugging-sdk.md)  
  
   [Ocenianie wyrażeń](../../extensibility/debugger/evaluating-expressions.md)  
  
   [Kontekst oceny wyrażeń](../../extensibility/debugger/expression-evaluation-context.md)  
  
   [Obliczanie wyrażenia w trybie przerwania](../../extensibility/debugger/expression-evaluation-in-break-mode.md)  
  
   [Pisanie ewaluatora wyrażeń środowiska uruchomieniowego wspólnego języka](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)  
  
- Obiekty docelowe w zastrzeżonej system operacyjny lub inne środowiska wykonawczego, należy napisać własne DE. Samouczek, w którym tworzy prostą DE, korzystając z modelu COM ATL jest dostępna. Więcej informacji znajduje się w następujących tematach:  
  
   [Tworzenie niestandardowego aparatu debugowania](../../extensibility/debugger/creating-a-custom-debug-engine.md)  
  
   [Samouczek: Tworzenie aparatu debugowania, korzystając z modelu COM ATL](https://msdn.microsoft.com/library/9097b71e-1fe7-48f7-bc00-009e25940c24)  
  
   [Implementowanie dostawcy portu](../../extensibility/debugger/implementing-a-port-supplier.md)  
  
   [Przykłady](../../extensibility/debugger/visual-studio-debugging-samples.md)  
  
## <a name="see-also"></a>Zobacz także  
 [Wprowadzenie](../../extensibility/debugger/getting-started-with-debugger-extensibility.md)