---
title: Tworzenie funkcji walidacji pakietu dla rozwiązań SharePoint
titleSuffix: ''
description: Utwórz niestandardowe reguły walidacji, aby zweryfikować pakiet rozwiązania wygenerowany przez program Visual Studio lub aby sprawdzić całą funkcję.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, extending deployment
- SharePoint development in Visual Studio, validation rules
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: ee6b27b92f1c79bfda95ba3d6dce7dbdce4a6fac
ms.sourcegitcommit: 80fc9a72e9a1aba2d417dbfee997fab013fc36ac
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/02/2021
ms.locfileid: "106216569"
---
# <a name="create-feature-and-package-validations-for-sharepoint-solutions"></a>Tworzenie funkcji walidacji pakietu dla rozwiązań SharePoint

  Można utworzyć niestandardowe reguły walidacji w celu zweryfikowania pakietu rozwiązania wygenerowanego przez program Visual Studio. Można przeprowadzić pełną weryfikację całej funkcji lub pakietu, wybierając pozycję **Weryfikuj** z menu kontekstowego pakietu lub funkcji w **PackagingExplorer**. Częściowe sprawdzanie poprawności jest wykonywane po dodaniu nowych elementów projektu programu SharePoint lub funkcji do projektu w celu ustalenia, czy pakiet lub funkcja byłyby w prawidłowym stanie.

### <a name="to-create-a-custom-package-validation-rule"></a>Aby utworzyć niestandardową regułę walidacji pakietu

1. Utwórz projekt biblioteki klas.

2. Dodaj odwołania do następujących zestawów:

    - Microsoft. VisualStudio. SharePoint

    - System. ComponentModel. kompozycji

3. Utwórz klasę, która implementuje jeden z następujących interfejsów:

    - Aby utworzyć regułę walidacji pakietu, zaimplementuj <xref:Microsoft.VisualStudio.SharePoint.Validation.IPackageValidationRule> interfejs.

    - Aby utworzyć regułę walidacji funkcji, zaimplementuj <xref:Microsoft.VisualStudio.SharePoint.Validation.IFeatureValidationRule> interfejs.

4. Dodaj <xref:System.ComponentModel.Composition.ExportAttribute> do klasy. Ten atrybut umożliwia programowi Visual Studio odnajdywanie i ładowanie reguły walidacji. Przekaż <xref:Microsoft.VisualStudio.SharePoint.Validation.IPackageValidationRule> lub <xref:Microsoft.VisualStudio.SharePoint.Validation.IFeatureValidationRule> wpisz do konstruktora atrybutu.

## <a name="example"></a>Przykład
 Poniższy przykład kodu demonstruje sposób tworzenia niestandardowej reguły walidacji funkcji.

 :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/featurevalidation/extension/customvalidationrule.vb" id="Snippet1":::
 :::code language="csharp" source="../sharepoint/codesnippet/CSharp/featurevalidation/extension/customfeaturevalidationrule.cs" id="Snippet1":::

## <a name="compile-the-code"></a>Kompiluj kod
 Ten przykład wymaga odwołania do następujących zestawów:

- Microsoft. VisualStudio. SharePoint.

- System. ComponentModel. kompozycji.

## <a name="deploy-the-extension"></a>Wdróż rozszerzenie
 Aby wdrożyć rozszerzenie, Utwórz [!include[vsprvs](../sharepoint/includes/vsprvs-md.md)] pakiet rozszerzenia (VSIX) dla zestawu i wszystkie inne pliki, które chcesz dystrybuować z rozszerzeniem. Aby uzyskać więcej informacji, zobacz [Wdrażanie rozszerzeń dla narzędzi programu SharePoint w programie Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).

## <a name="see-also"></a>Zobacz też
- [Rozszerzona pakowanie i wdrażanie programu SharePoint](../sharepoint/extending-sharepoint-packaging-and-deployment.md)
