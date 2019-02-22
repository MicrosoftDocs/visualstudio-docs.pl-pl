---
title: Interfejs kreatora (IDTWizard) | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- IDTWizard interface
- wizards, interface
ms.assetid: 09618d9d-d115-45b6-bccc-de328994b39c
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: bd911c978e253b28827b5b4bb0551a2355164663
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/21/2019
ms.locfileid: "56645852"
---
# <a name="wizard-interface-idtwizard"></a>Interfejs kreatora (IDTWizard)
Używa zintegrowanego środowiska programistycznego (IDE) <xref:EnvDTE.IDTWizard> interfejs do komunikacji za pomocą kreatorów. Kreatorzy musi implementować ten interfejs, aby mogło zostać zainstalowane w środowisku IDE.

 <xref:EnvDTE.IDTWizard.Execute%2A> Metody jest jedyną metodą, które są skojarzone z <xref:EnvDTE.IDTWizard> interfejsu. Kreatorzy zaimplementować tę metodę i IDE wywołuje metodę w interfejsie. Poniższy przykład pokazuje podpis metody.

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

 Mechanizm rozpoczęcia jest podobny dla obu **nowy projekt** i **Dodaj nowy element** kreatorów. Aby rozpocząć, albo, należy wywołać <xref:EnvDTE.IDTWizard> interfejsem zdefiniowanym w Dteinternal.h. Jedyna różnica polega na zestaw kontekstu i parametry niestandardowe, które są przekazywane do interfejsu, po wywołaniu interfejsu.

 Poniższe informacje zawierają opis <xref:EnvDTE.IDTWizard> interfejs, który musi implementować kreatorów, aby pracować w [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE. Wywołania środowiska IDE <xref:EnvDTE.IDTWizard.Execute%2A> kreatora, podając mu następujące metody:

-   Obiekt DTE

     Obiekt DTE jest głównym modelu automatyzacji.

-   Dojście do pokazanego poniżej segment kodu, okno dialogowe `hwndOwner ([in] long)`.

     Kreator używa to `hwndOwner` jako element nadrzędny dla okna dialogowego kreatora.

-   Kontekst parametry przekazywane do interfejsu jako wariant dla SAFEARRAY zgodnie z informacjami w segmencie kodu `[in] SAFEARRAY (VARIANT)* ContextParams`.

     Parametry kontekstu zawierać tablicę wartości, które są specyficzne dla rodzaju uruchomieniu kreatora i bieżącego stanu projektu. IDE przekazuje parametrów kontekstu do kreatora. Aby uzyskać więcej informacji, zobacz [parametrów kontekstu](../../extensibility/internals/context-parameters.md).

-   Niestandardowe parametry przekazywane do interfejsu jako wariant dla SAFEARRAY zgodnie z informacjami w segmencie kodu `[in] SAFEARRAY (VARIANT)* CustomParams`.

     Parametry niestandardowe zawierać tablicę parametrów zdefiniowanych przez użytkownika. Plik .vsz przekazuje parametry niestandardowe do środowiska IDE. Wartości są określane przez `Param=` instrukcji. Aby uzyskać więcej informacji, zobacz [parametry niestandardowe](../../extensibility/internals/custom-parameters.md).

-   Są zwracane wartości dla interfejsu

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