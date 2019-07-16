---
title: Parametry niestandardowe | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- wizards, custom parameters
- custom parameters
ms.assetid: ba5c364b-66e6-47ea-9760-a0b70de8f0a0
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 1a595861be835ec1aaa7079b3e3fe1962d5055e9
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "68154988"
---
# <a name="custom-parameters"></a>Parametry niestandardowe
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Parametry niestandardowe kontroli działania kreatora, po uruchomieniu kreatora. Plik .vsz powiązane zawiera tablicę parametrów zdefiniowanych przez użytkownika, które są opakowane przez zintegrowanego środowiska programistycznego (IDE) i przekazywana do kreatora jako tablicę ciągów, po uruchomieniu kreatora. Kreator następnie analizuje tablicę ciągów i używa tych informacji do kontroli rzeczywiste działania kreatora. W ten sposób kreatora można dostosować funkcjonalność w zależności od zawartości pliku .vsz.  
  
 Parametry kontekstu, z drugiej strony, Definiowanie stanu projektu, po uruchomieniu kreatora. Aby uzyskać więcej informacji, zobacz [parametrów kontekstu](../../extensibility/internals/context-parameters.md).  
  
 Poniżej znajduje się przykład pliku .vsz, który ma następujące parametry niestandardowe:  
  
```  
VSWIZARD 8.0  
Wizard=VsWizard.VsWizard_Engine  
Param="WIZARD_NAME = Sample Wizard"  
Param="WIZARD_UI = FALSE"  
Param="RELATIVE_PATH = VSWizards\Classwiz\ATL"  
Param="PREPROCESS_FUNCTION = CanAddATLSupport"  
Param="PROJECT_TYPE = CSPROJ"  
```  
  
 Tworzenie pliku .vsz dodaje wartości parametrów. Gdy użytkownik wybierze **nowy projekt** lub **Dodaj nowy element** menu Plik lub klikając prawym przyciskiem myszy projekt w **Eksploratora rozwiązań**, IDE zbiera te wartości do tablicy ciągi. IDE następnie wywołuje projektu <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.AddItem%2A> metody z <xref:Microsoft.VisualStudio.Shell.Interop.VSADDITEMOPERATION> Flaga zestawu i wywoływanych w projekcie <xref:EnvDTE.IVsExtensibility.RunWizardFile%2A> metodę, która odpowiada za uruchamianie kreatora i zwrócenia wyniku.  
  
 Kreator jest odpowiedzialny za analizowanie tablicę ciągów i odpowiednio działają na ciągi. W ten sposób przez zaimplementowanie parametry niestandardowe można utworzyć jednego kreatora, który wykonuje różne funkcje. Innymi słowy jednego kreatora może mieć trzy .vsz różne pliki. Każdy plik przekazuje różnych zestawów niestandardowych parametrów do sterowania zachowaniem kreatora w różnych sytuacjach.  
  
 Aby uzyskać więcej informacji, zobacz [kreatora (. Plik Vsz)](../../extensibility/internals/wizard-dot-vsz-file.md).  
  
## <a name="see-also"></a>Zobacz też  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3>   
 [Parametry kontekstu](../../extensibility/internals/context-parameters.md)   
 [Kreatorzy](../../extensibility/internals/wizards.md)   
 [Kreator (plik Vsz)](../../extensibility/internals/wizard-dot-vsz-file.md)
