---
title: Parametry niestandardowe | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- wizards, custom parameters
- custom parameters
ms.assetid: ba5c364b-66e6-47ea-9760-a0b70de8f0a0
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: c8c243490a88010031bad91d6b45fe5645d21e6e
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53826364"
---
# <a name="custom-parameters"></a>Parametry niestandardowe
Parametry niestandardowe kontroli działania kreatora, po uruchomieniu kreatora. Powiązane *.vsz* plik zawiera tablicę parametrów zdefiniowanych przez użytkownika, które są opakowane przez zintegrowanego środowiska programistycznego (IDE) i przekazywana do kreatora jako tablicę ciągów, po uruchomieniu kreatora. Kreator następnie analizuje tablicę ciągów i używa tych informacji do kontroli rzeczywiste działania kreatora. W ten sposób kreatora można dostosować funkcjonalność w zależności od zawartości *.vsz* pliku.  
  
 Parametry kontekstu, z drugiej strony, Definiowanie stanu projektu, po uruchomieniu kreatora. Aby uzyskać więcej informacji, zobacz [parametrów kontekstu](../../extensibility/internals/context-parameters.md).  
  
 Poniżej przedstawiono przykład *.vsz* pliku, który ma parametry niestandardowe:  
  
```  
VSWIZARD 8.0  
Wizard=VsWizard.VsWizard_Engine  
Param="WIZARD_NAME = Sample Wizard"  
Param="WIZARD_UI = FALSE"  
Param="RELATIVE_PATH = VSWizards\Classwiz\ATL"  
Param="PREPROCESS_FUNCTION = CanAddATLSupport"  
Param="PROJECT_TYPE = CSPROJ"  
```  
  
 Autor *.vsz* plik dodaje wartości parametrów. Gdy użytkownik wybierze **nowy projekt** lub **Dodaj nowy element** na **pliku** menu lub klikając prawym przyciskiem myszy projekt w **Eksploratora rozwiązań**, IDE zbiera te wartości w tablicy ciągów. IDE następnie wywołuje projektu <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.AddItem%2A> metody z <xref:Microsoft.VisualStudio.Shell.Interop.VSADDITEMOPERATION> Flaga zestawu i wywoływanych w projekcie <xref:EnvDTE.IVsExtensibility.RunWizardFile%2A> metodę, która odpowiada za uruchamianie kreatora i zwrócenia wyniku.  
  
 Kreator jest odpowiedzialny za analizowanie tablicę ciągów i odpowiednio działają na ciągi. W ten sposób przez zaimplementowanie parametry niestandardowe można utworzyć jednego kreatora, który wykonuje różne funkcje. Innymi słowy, jednego kreatora może mieć trzy różne *.vsz* plików. Każdy plik przekazuje różnych zestawów niestandardowych parametrów do sterowania zachowaniem kreatora w różnych sytuacjach.  
  
 Aby uzyskać więcej informacji, zobacz [pliku kreatora (.vsz —)](../../extensibility/internals/wizard-dot-vsz-file.md).  
  
## <a name="see-also"></a>Zobacz także  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3>   
 [Parametry kontekstu](../../extensibility/internals/context-parameters.md)   
 [Kreatorzy](../../extensibility/internals/wizards.md)   
 [Plik kreatora (vsz)](../../extensibility/internals/wizard-dot-vsz-file.md)