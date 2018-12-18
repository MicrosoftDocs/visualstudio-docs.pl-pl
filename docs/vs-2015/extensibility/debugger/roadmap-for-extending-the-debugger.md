---
title: Plan rozwoju rozszerzania debugera | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- debugging [Debugging SDK], roadmap
- Debugging SDK, roadmap
ms.assetid: 1f4096a8-f7aa-4dfa-84e1-6d59263e70bb
caps.latest.revision: 17
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 806a5ebb4bf27f4d46bbe5b81a5dba6b319ee02e
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51816687"
---
# <a name="roadmap-for-extending-the-debugger"></a>Plan rozwoju rozszerzania debugera
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Ta dokumentacja zawiera przewodnik i informacje do rozszerzania [!INCLUDE[vs_current_short](../../includes/vs-current-short-md.md)] debugera za pomocą [!INCLUDE[vsipsdk](../../includes/vsipsdk-md.md)].  
  
 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] debugowanie dokumentacji zawiera przykłady, stanowią wyczerpujące Kompendium i kilka reprezentatywny scenariusze, które pokazują typowe sposoby dostosowywania debugera.  
  
 Kompilator i jego danych wyjściowych określają, co jest potrzebne do zaimplementowania debugowania w programie. Jeśli kompilator:  
  
-   Jest przeznaczony dla natywnego systemu operacyjnego Windows i zapisuje je. Plik PDB można debugować programy przy użyciu aparatu debugowania kodu macierzystego (DE), która jest zintegrowana [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]. Nie trzeba do zaimplementowania ewaluatora DE lub wyrażenie. Ewaluator wyrażeń jest przeznaczony dla składni języka programowania C++.  
  
-   Tworzy Microsoft intermediate language (MSIL). dane wyjściowe, można debugować programy przy użyciu aparatu debugowania kodu zarządzanego DE, która jest również zintegrowana [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]. W związku z tym należy zaimplementować tylko ewaluatora wyrażeń. Ewaluator wyrażeń próbki jest dostarczany. Więcej informacji znajduje się w następujących tematach:  
  
     [Obliczanie wyrażeń](../../extensibility/debugger/expression-evaluation-visual-studio-debugging-sdk.md)  
  
     [Ocenianie wyrażeń](../../extensibility/debugger/evaluating-expressions.md)  
  
     [Kontekst oceny wyrażeń](../../extensibility/debugger/expression-evaluation-context.md)  
  
     [Ocena wyrażeń w trybie przerwania](../../extensibility/debugger/expression-evaluation-in-break-mode.md)  
  
     [Pisanie ewaluatora wyrażeń środowiska uruchomieniowego języka wspólnego](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)  
  
-   Obiekty docelowe w zastrzeżonej system operacyjny lub inne środowiska wykonawczego, należy napisać własne DE. Samouczek, w którym tworzy prostą DE, korzystając z modelu COM ATL jest dostępna. Więcej informacji znajduje się w następujących tematach:  
  
     [Tworzenie niestandardowego aparatu debugowania](../../extensibility/debugger/creating-a-custom-debug-engine.md)  
  
     [Samouczek: Tworzenie aparatu debugowania, korzystając z modelu COM ATL](http://msdn.microsoft.com/en-us/9097b71e-1fe7-48f7-bc00-009e25940c24)  
  
     [Implementowanie dostawcy portu](../../extensibility/debugger/implementing-a-port-supplier.md)  
  
     [Przykłady](../../extensibility/debugger/visual-studio-debugging-samples.md)  
  
## <a name="see-also"></a>Zobacz też  
 [Wprowadzenie](../../extensibility/debugger/getting-started-with-debugger-extensibility.md)

