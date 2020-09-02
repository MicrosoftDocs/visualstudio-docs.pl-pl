---
title: Plan rozszerzający debuger | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], roadmap
- Debugging SDK, roadmap
ms.assetid: 1f4096a8-f7aa-4dfa-84e1-6d59263e70bb
caps.latest.revision: 17
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 89a07bc5a5c4c8b7a6054b53610325c654355bc8
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "65695957"
---
# <a name="roadmap-for-extending-the-debugger"></a>Plan rozwoju rozszerzania debugera
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Ta dokumentacja zawiera przewodnik i informacje referencyjne dotyczące rozszerzania [!INCLUDE[vs_current_short](../../includes/vs-current-short-md.md)] debugera za pomocą narzędzia [!INCLUDE[vsipsdk](../../includes/vsipsdk-md.md)] .  
  
 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Dokumentacja dotycząca debugowania obejmuje przykłady, kompleksowe odwołanie i kilka reprezentatywnych scenariuszy, które przedstawiają typowe sposoby dostosowywania debugera.  
  
 Kompilator i jego dane wyjściowe określają, co należy zrobić, aby zaimplementować debugowanie w produkcie. Jeśli kompilator:  
  
- Jest przeznaczony dla systemu operacyjnego Windows Native i zapisuje. Plik PDB, można debugować programy z aparatem debugowania kodu natywnego (DE), który jest zintegrowany z programem [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] . Nie trzeba implementować ewaluatora not ani expression. Ewaluatora wyrażeń jest zapisywana dla składni języka programowania C++.  
  
- Tworzy dane wyjściowe języka pośredniego firmy Microsoft (MSIL), można debugować programy z aparatem debugowania kodu zarządzanego DE, który również jest zintegrowany z [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] . W tym celu należy zaimplementować tylko ewaluatora wyrażeń. Zostanie udostępniona Przykładowa ewaluatora wyrażeń. Aby uzyskać więcej informacji, zobacz następujące tematy:  
  
     [Obliczanie wyrażeń](../../extensibility/debugger/expression-evaluation-visual-studio-debugging-sdk.md)  
  
     [Ocenianie wyrażeń](../../extensibility/debugger/evaluating-expressions.md)  
  
     [Kontekst oceny wyrażeń](../../extensibility/debugger/expression-evaluation-context.md)  
  
     [Ocena wyrażeń w trybie przerwania](../../extensibility/debugger/expression-evaluation-in-break-mode.md)  
  
     [Pisanie ewaluatora wyrażeń środowiska uruchomieniowego języka wspólnego](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)  
  
- Dotyczy zastrzeżonego systemu operacyjnego lub innego środowiska wykonawczego, należy napisać własne. Podano samouczek, który tworzy prostą i nieużywaną ATL COM. Aby uzyskać więcej informacji, zobacz następujące tematy:  
  
     [Tworzenie niestandardowego aparatu debugowania](../../extensibility/debugger/creating-a-custom-debug-engine.md)  
  
     [Samouczek: kompilowanie aparatu debugowania przy użyciu biblioteki ATL COM](https://msdn.microsoft.com/9097b71e-1fe7-48f7-bc00-009e25940c24)  
  
     [Implementowanie dostawcy portu](../../extensibility/debugger/implementing-a-port-supplier.md)  
  
     [Samples](../../extensibility/debugger/visual-studio-debugging-samples.md)  
  
## <a name="see-also"></a>Zobacz też  
 [Wprowadzenie](../../extensibility/debugger/getting-started-with-debugger-extensibility.md)
