---
title: Interfejs kreatora (IDTWizard) | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- IDTWizard interface
- wizards, interface
ms.assetid: 09618d9d-d115-45b6-bccc-de328994b39c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: bb1c8d728a76097321e4e1f16640cab97599d6ba
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80703277"
---
# <a name="wizard-interface-idtwizard"></a>Interfejs kreatora (IDTWizard)
Zintegrowane środowisko programistyczne (IDE) używa interfejsu do komunikowania <xref:EnvDTE.IDTWizard> się z kreatorami. Kreatorzy muszą zaimplementować ten interfejs, aby można było zainstalować go w ide.

 Metoda <xref:EnvDTE.IDTWizard.Execute%2A> jest jedyną metodą <xref:EnvDTE.IDTWizard> skojarzoną z interfejsem. Kreatorzy implementują tę metodę, a IDE wywołuje metodę w interfejsie. W poniższym przykładzie przedstawiono podpis metody.

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

 Mechanizm uruchamiania jest podobny zarówno dla kreatorów **Nowego projektu, jak** i **Dodaj nowy element.** Aby rozpocząć, należy wywołać <xref:EnvDTE.IDTWizard> interfejs zdefiniowany w Dteinternal.h. Jedyną różnicą jest zestaw parametrów kontekstu i niestandardowych, które są przekazywane do interfejsu, gdy interfejs jest wywoływany.

 Poniżej opisano <xref:EnvDTE.IDTWizard> interfejs, który kreatorzy muszą [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] zaimplementować do pracy w IDE. IDE wywołuje <xref:EnvDTE.IDTWizard.Execute%2A> metodę na kreatorze, przekazując ją poniżej:

- Obiekt DTE

     Obiekt DTE jest katalogiem głównym modelu automatyzacji.

- Uchwyt okna dialogowego, jak pokazano w `hwndOwner ([in] long)`segmencie kodu, .

     Kreator używa tego `hwndOwner` jako nadrzędnego okna dialogowego kreatora.

- Parametry kontekstu przekazywane do interfejsu jako wariant safearray, `[in] SAFEARRAY (VARIANT)* ContextParams`jak pokazano w segmencie kodu, .

     Parametry kontekstu zawierają tablicę wartości, które są specyficzne dla rodzaju kreatora jest uruchamiany i bieżącego stanu projektu. IDE przekazuje parametry kontekstu do kreatora. Aby uzyskać więcej informacji, zobacz [Parametry kontekstu](../../extensibility/internals/context-parameters.md).

- Parametry niestandardowe przekazywane do interfejsu jako wariant safearray, `[in] SAFEARRAY (VARIANT)* CustomParams`jak pokazano w segmencie kodu, .

     Parametry niestandardowe zawierają tablicę parametrów zdefiniowanych przez użytkownika. Plik .vsz przekazuje parametry niestandardowe do IDE. Wartości są określane `Param=` przez instrukcje. Aby uzyskać więcej informacji, zobacz [Parametry niestandardowe](../../extensibility/internals/custom-parameters.md).

- Wartości zwracane dla interfejsu są

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
