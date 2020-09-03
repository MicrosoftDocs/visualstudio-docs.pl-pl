---
title: Interfejs kreatora (IDTWizard) | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "80703277"
---
# <a name="wizard-interface-idtwizard"></a>Interfejs kreatora (IDTWizard)
Zintegrowane środowisko programistyczne (IDE) używa <xref:EnvDTE.IDTWizard> interfejsu do komunikowania się z kreatorami. Kreatory muszą zaimplementować ten interfejs, aby można go było zainstalować w środowisku IDE.

 <xref:EnvDTE.IDTWizard.Execute%2A>Metoda jest jedyną metodą skojarzoną z <xref:EnvDTE.IDTWizard> interfejsem. Kreatorzy implementują tę metodę, a IDE wywołuje metodę w interfejsie. Poniższy przykład przedstawia sygnaturę metody.

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

 Mechanizm uruchamiania jest podobny zarówno do kreatora **nowego projektu** , jak i **Dodaj nowy element** . Aby rozpocząć, należy wywołać <xref:EnvDTE.IDTWizard> interfejs zdefiniowany w Dteinternal. h. Jedyną różnicą jest zestaw parametrów kontekstowych i niestandardowych, które są przesyłane do interfejsu, gdy interfejs jest wywoływany.

 Poniższe informacje opisują <xref:EnvDTE.IDTWizard> interfejs, który Kreator musi zaimplementować do pracy w środowisku [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE. IDE wywołuje <xref:EnvDTE.IDTWizard.Execute%2A> metodę w kreatorze, przekazując ją w następujący sposób:

- Obiekt DTE

     Obiekt DTE jest głównym modelem automatyzacji.

- Uchwyt do okna dialogowego okno, jak pokazano w segmencie kodu `hwndOwner ([in] long)` .

     Kreator używa tego `hwndOwner` jako elementu nadrzędnego okna dialogowego Kreatora.

- Parametry kontekstu przekazano do interfejsu jako wariant dla elementu SAFEARRAY, jak pokazano w segmencie kodu `[in] SAFEARRAY (VARIANT)* ContextParams` .

     Parametry kontekstu zawierają tablicę wartości specyficznych dla rodzaju uruchamianego kreatora i bieżącego stanu projektu. IDE przekazuje parametry kontekstu do kreatora. Aby uzyskać więcej informacji, zobacz [Parametry kontekstu](../../extensibility/internals/context-parameters.md).

- Parametry niestandardowe przesłane do interfejsu jako wariant dla elementu SAFEARRAY, jak pokazano w segmencie kodu, `[in] SAFEARRAY (VARIANT)* CustomParams` .

     Parametry niestandardowe zawierają tablicę parametrów zdefiniowanych przez użytkownika. Plik. vsz przekazuje parametry niestandardowe do IDE. Wartości są określane przez `Param=` instrukcje. Aby uzyskać więcej informacji, zobacz [parametry niestandardowe](../../extensibility/internals/custom-parameters.md).

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
