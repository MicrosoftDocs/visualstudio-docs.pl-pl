---
title: Kreator interfejsu (IDTWizard) | Microsoft Docs
description: Ide używa interfejsu IDTWizard do komunikowania się z kreatorami. Kreatorzy muszą zaimplementować ten interfejs, aby można go było zainstalować w idee.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDTWizard interface
- wizards, interface
ms.assetid: 09618d9d-d115-45b6-bccc-de328994b39c
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 930996de7fa5366463ec2d60f7cf96d941f6c243
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/25/2021
ms.locfileid: "112898620"
---
# <a name="wizard-interface-idtwizard"></a>Interfejs kreatora (IDTWizard)
Zintegrowane środowisko projektowe (IDE) używa <xref:EnvDTE.IDTWizard> interfejsu do komunikowania się z kreatorami. Kreatorzy muszą zaimplementować ten interfejs, aby można go było zainstalować w idee.

 Metoda <xref:EnvDTE.IDTWizard.Execute%2A> jest jedyną metodą skojarzoną z <xref:EnvDTE.IDTWizard> interfejsem. Kreatorzy implementują tę metodę, a ide wywołuje metodę w interfejsie. Poniższy przykład przedstawia podpis metody .

```
/* IDTWizard Method */
STDMETHOD(Execute)(THIS_
   /* [in] */ IDispatch *Application,
   /* [in] */ long hwndOwner,
   /* [in] */ SAFEARRAY * *ContextParams,
   /* [in] */ SAFEARRAY * *CustomParams,
   /* [out] [in] */ wizardResult *RetVal
   );
```

 Mechanizm uruchamiania jest podobny w przypadku **kreatorów Nowy projekt** i Dodaj **nowy** element. Aby rozpocząć, wywołaj <xref:EnvDTE.IDTWizard> interfejs zdefiniowany w pliku Dteinternal.h. Jedyną różnicą jest zestaw parametrów kontekstu i niestandardowych, które są przekazywane do interfejsu, gdy interfejs jest wywoływany.

 Poniższe informacje zawierają opis <xref:EnvDTE.IDTWizard> interfejsu, który kreatorzy muszą zaimplementować, aby pracować w [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] idee. Ide wywołuje metodę <xref:EnvDTE.IDTWizard.Execute%2A> w kreatorze, przekazując następujące informacje:

- Obiekt DTE

     Obiekt DTE jest katalogem głównym modelu automatyzacji.

- Dojście do okna dialogowego, jak pokazano w segmencie kodu , `hwndOwner ([in] long)` .

     Kreator używa tego `hwndOwner` elementu jako elementu nadrzędnego dla okna dialogowego kreatora.

- Parametry kontekstu przekazywane do interfejsu jako wariant dla safeARRAY, jak pokazano w segmencie kodu , `[in] SAFEARRAY (VARIANT)* ContextParams` .

     Parametry kontekstu zawierają tablicę wartości, które są specyficzne dla rodzaju kreatora, który jest uruchomiony, i bieżącego stanu projektu. Ide przekazuje parametry kontekstu do kreatora. Aby uzyskać więcej informacji, zobacz [Parametry kontekstu](../../extensibility/internals/context-parameters.md).

- Parametry niestandardowe przekazywane do interfejsu jako wariant dla safeARRAY, jak pokazano w segmencie kodu `[in] SAFEARRAY (VARIANT)* CustomParams` , .

     Parametry niestandardowe zawierają tablicę parametrów zdefiniowanych przez użytkownika. Plik vsz przekazuje parametry niestandardowe do środowiska IDE. Wartości są określane przez `Param=` instrukcje . Aby uzyskać więcej informacji, zobacz [Parametry niestandardowe](../../extensibility/internals/custom-parameters.md).

- Zwracane wartości interfejsu to

    ```
    wizardResultSuccess = -1,
    wizardResultFailure = 0
    wizardResultCancel = 1
    wizardResultBackout = 2
    ```

## <a name="see-also"></a>Zobacz też
- [Parametry kontekstu](../../extensibility/internals/context-parameters.md)
- [Parametry niestandardowe](../../extensibility/internals/custom-parameters.md)
- [Kreatory](../../extensibility/internals/wizards.md)
- [Kreator (plik Vsz)](../../extensibility/internals/wizard-dot-vsz-file.md)
