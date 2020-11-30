---
title: Parametry niestandardowe | Microsoft Docs
description: Dowiedz się, jak utworzyć parametry niestandardowe kontrolujące działanie kreatora po rozpoczęciu pracy przez kreatora, modyfikując plik. vsz.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: f2fd2ba746f10094a79f1b37e57ba4ca90ff117b
ms.sourcegitcommit: 9ce13a961719afbb389fa033fbb1a93bea814aae
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/30/2020
ms.locfileid: "96328447"
---
# <a name="custom-parameters"></a>Parametry niestandardowe
Parametry niestandardowe kontrolują działanie kreatora po rozpoczęciu pracy przez kreatora. Powiązany plik *vsz* zawiera tablicę parametrów zdefiniowanych przez użytkownika, które są pakowane przez zintegrowane środowisko programistyczne (IDE) i przekazaną do kreatora jako tablicę ciągów, gdy Kreator został uruchomiony. Następnie Kreator analizuje tablicę ciągów i używa tych informacji do sterowania rzeczywistą operacją kreatora. W ten sposób Kreator może dostosować funkcje w zależności od zawartości pliku *. vsz* .

 Parametry kontekstu z drugiej strony definiują stan projektu po uruchomieniu kreatora. Aby uzyskać więcej informacji, zobacz [Parametry kontekstu](../../extensibility/internals/context-parameters.md).

 Poniżej znajduje się przykładowy plik *. vsz* , który ma parametry niestandardowe:

```
VSWIZARD 8.0
Wizard=VsWizard.VsWizard_Engine
Param="WIZARD_NAME = Sample Wizard"
Param="WIZARD_UI = FALSE"
Param="RELATIVE_PATH = VSWizards\Classwiz\ATL"
Param="PREPROCESS_FUNCTION = CanAddATLSupport"
Param="PROJECT_TYPE = CSPROJ"
```

 Autor pliku *. vsz* dodaje wartości parametrów. Gdy użytkownik wybierze **Nowy projekt** lub **Dodaj nowy element** w menu **plik** lub klikając prawym przyciskiem myszy projekt w **Eksplorator rozwiązań**, IDE zbiera te wartości w tablicy ciągów. IDE następnie wywołuje <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.AddItem%2A> metodę projektu z <xref:Microsoft.VisualStudio.Shell.Interop.VSADDITEMOPERATION> zestawem flag, a projekt wywołuje <xref:EnvDTE.IVsExtensibility.RunWizardFile%2A> metodę, która jest odpowiedzialna za uruchomienie kreatora i zwraca wynik.

 Kreator jest odpowiedzialny za analizę tablicy ciągów i odpowiednio działające na ciągach. W ten sposób przez zaimplementowanie parametrów niestandardowych można utworzyć jeden Kreator, który wykonuje różne funkcje. Innymi słowy, jeden Kreator może mieć trzy różne pliki *. vsz* . Każdy plik przekazuje różne zestawy niestandardowych parametrów, aby kontrolować zachowanie kreatora w różnych sytuacjach.

 Aby uzyskać więcej informacji, zobacz [plik kreatora (. vsz)](../../extensibility/internals/wizard-dot-vsz-file.md).

## <a name="see-also"></a>Zobacz też
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3>
- [Parametry kontekstu](../../extensibility/internals/context-parameters.md)
- [Kreatory](../../extensibility/internals/wizards.md)
- [Plik kreatora (. vsz)](../../extensibility/internals/wizard-dot-vsz-file.md)
