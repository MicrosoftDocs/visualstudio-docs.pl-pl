---
title: 'Instrukcje: Tworzenie funkcji niestandardowej oraz zasady walidacji pakietu dla rozwiązań SharePoint | Dokumentacja firmy Microsoft'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, extending deployment
- SharePoint development in Visual Studio, validation rules
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 794974991216a521bf2ca4afb1e958716a3bf735
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2019
ms.locfileid: "54874084"
---
# <a name="how-to-create-custom-feature-and-package-validation-rules-for-sharepoint-solutions"></a>Instrukcje: Tworzenie funkcji niestandardowej oraz pakiet reguł sprawdzania poprawności dla rozwiązań SharePoint
  Możesz utworzyć niestandardowe reguły poprawności można zweryfikować pakietu rozwiązania generowane przez program Visual Studio. Można wykonać pełnej weryfikacji na całej funkcji lub pakiet, wybierając **weryfikacji** z menu kontekstowego pakietu lub funkcji w **PackagingExplorer**. Częściowej weryfikacji odbywa się po dodaniu nowych elementów projektu SharePonit lub funkcji do projektu, aby określić, czy pakiet lub funkcja może być w prawidłowym stanie.  
  
### <a name="to-create-a-custom-package-validation-rule"></a>Aby utworzyć regułę sprawdzania poprawności pakiecie niestandardowym  
  
1.  Utwórz projekt biblioteki klas.  
  
2.  Dodaj odwołania do następujących zestawów:  
  
    -   Microsoft.VisualStudio.SharePoint  
  
    -   System.ComponentModel.Composition  
  
3.  Utwórz klasę, która implementuje jedną z poniższych interfejsów:  
  
    -   Aby utworzyć regułę sprawdzania poprawności pakietu, należy zaimplementować <xref:Microsoft.VisualStudio.SharePoint.Validation.IPackageValidationRule> interfejsu.  
  
    -   Aby utworzyć regułę sprawdzania poprawności funkcji, należy zaimplementować <xref:Microsoft.VisualStudio.SharePoint.Validation.IFeatureValidationRule> interfejsu.  
  
4.  Dodaj <xref:System.ComponentModel.Composition.ExportAttribute> do klasy. Ten atrybut umożliwia środowisku Visual Studio wykrycie i załadowanie reguły sprawdzania poprawności. Przekaż <xref:Microsoft.VisualStudio.SharePoint.Validation.IPackageValidationRule> lub <xref:Microsoft.VisualStudio.SharePoint.Validation.IFeatureValidationRule> typu konstruktora atrybutu.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład kodu pokazuje, jak utworzyć niestandardową regułę sprawdzania poprawności funkcji.  
  
 [!code-vb[SPExtensibility.FeatureValidation#1](../sharepoint/codesnippet/VisualBasic/featurevalidation/extension/customvalidationrule.vb#1)]
 [!code-csharp[SPExtensibility.FeatureValidation#1](../sharepoint/codesnippet/CSharp/featurevalidation/extension/customfeaturevalidationrule.cs#1)]  
  
## <a name="compile-the-code"></a>Skompilować kod  
 Ten przykład wymaga odwołania do następujących zestawów:  
  
-   Microsoft.VisualStudio.SharePoint.  
  
-   System.ComponentModel.Composition.  
  
## <a name="deploy-the-extension"></a>Wdrażanie rozszerzenia  
 Aby wdrożyć rozszerzenie, należy utworzyć [!include[vsprvs](../sharepoint/includes/vsprvs-md.md)] rozszerzenie (VSIX), pakiet dla zestawu i innych plików, które chcesz dystrybuować z rozszerzeniem. Aby uzyskać więcej informacji, zobacz [wdrażanie rozszerzeń dla programu SharePoint narzędzia w programie Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).  
  
## <a name="see-also"></a>Zobacz także
 [Rozszerzanie pakowania i wdrażania SharePoint](../sharepoint/extending-sharepoint-packaging-and-deployment.md)  
