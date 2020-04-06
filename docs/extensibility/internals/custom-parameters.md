---
title: Parametry niestandardowe | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- wizards, custom parameters
- custom parameters
ms.assetid: ba5c364b-66e6-47ea-9760-a0b70de8f0a0
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: cd52a49daa7d57a21d8cb0896f7108efa09e32b2
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80708944"
---
# <a name="custom-parameters"></a>Parametry niestandardowe
Parametry niestandardowe sterują działaniem kreatora po uruchomieniu kreatora. Powiązany plik *vsz* zawiera tablicę parametrów zdefiniowanych przez użytkownika, które są pakowane przez zintegrowane środowisko programistyczne (IDE) i przekazywane do kreatora jako tablica ciągów po uruchomieniu kreatora. Następnie kreator analizuje tablicę ciągów i używa informacji do kontrolowania rzeczywistego działania kreatora. W ten sposób kreator może dostosować funkcjonalność w zależności od zawartości pliku *.vsz.*

 Parametry kontekstu, z drugiej strony, zdefiniować stan projektu po uruchomieniu kreatora. Aby uzyskać więcej informacji, zobacz [Parametry kontekstu](../../extensibility/internals/context-parameters.md).

 Oto przykład pliku *vsz,* który ma parametry niestandardowe:

```
VSWIZARD 8.0
Wizard=VsWizard.VsWizard_Engine
Param="WIZARD_NAME = Sample Wizard"
Param="WIZARD_UI = FALSE"
Param="RELATIVE_PATH = VSWizards\Classwiz\ATL"
Param="PREPROCESS_FUNCTION = CanAddATLSupport"
Param="PROJECT_TYPE = CSPROJ"
```

 Autor pliku *.vsz* dodaje wartości parametrów. Gdy użytkownik wybierze **nowy projekt** lub **Dodaj nowy element** w menu **Plik** lub klikając prawym przyciskiem myszy projekt w **Eksploratorze rozwiązań,** IDE zbiera te wartości w tablicy ciągów. IDE następnie wywołuje metodę <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.AddItem%2A> projektu z <xref:Microsoft.VisualStudio.Shell.Interop.VSADDITEMOPERATION> zestawem flag, a <xref:EnvDTE.IVsExtensibility.RunWizardFile%2A> projekt wywołuje metodę, która jest odpowiedzialna za uruchomienie kreatora i zwracanie wyniku.

 Kreator jest odpowiedzialny za analizowanie tablicy ciągów i odpowiednie działanie na ciągi. W ten sposób implementując parametry niestandardowe można utworzyć jeden kreator, który wykonuje różne funkcje. Innymi słowy, jeden kreator może mieć trzy różne pliki *.vsz.* Każdy plik przekazuje różne zestawy parametrów niestandardowych, aby kontrolować zachowanie kreatora w różnych sytuacjach.

 Aby uzyskać więcej informacji, zobacz [Plik kreatora (.vsz).](../../extensibility/internals/wizard-dot-vsz-file.md)

## <a name="see-also"></a>Zobacz też
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3>
- [Parametry kontekstu](../../extensibility/internals/context-parameters.md)
- [Kreatory](../../extensibility/internals/wizards.md)
- [Plik Kreatora (.vsz)](../../extensibility/internals/wizard-dot-vsz-file.md)
