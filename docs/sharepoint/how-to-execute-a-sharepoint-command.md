---
title: 'Instrukcje: wykonywanie polecenia SharePoint | Microsoft Docs'
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint commands [SharePoint development in Visual Studio], executing
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 789b77f3161b5fe566ea033060e8cab16cbaecc7
ms.sourcegitcommit: f9e44f5ab6a1dfb56c945c9986730465e1adb6fc
ms.contentlocale: pl-PL
ms.lasthandoff: 07/06/2020
ms.locfileid: "86016993"
---
# <a name="how-to-execute-a-sharepoint-command"></a>Instrukcje: wykonywanie polecenia SharePoint
  Jeśli chcesz użyć modelu obiektów serwera w rozszerzeniu narzędzi programu SharePoint, musisz utworzyć niestandardowe *polecenie programu SharePoint* , aby wywołać interfejs API. Po zdefiniowaniu polecenia i wdrożeniu go przy użyciu rozszerzenia narzędzi programu SharePoint, rozszerzenie może wykonać polecenie, aby wywołać model obiektów programu SharePoint Server. Aby wykonać polecenie, użyj jednej z ExecuteCommand metod <xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection> obiektu.

 Aby uzyskać więcej informacji na temat przeznaczenia poleceń programu SharePoint, zobacz [Wywoływanie modeli obiektów programu SharePoint](../sharepoint/calling-into-the-sharepoint-object-models.md).

### <a name="to-execute-a-sharepoint-command"></a>Aby wykonać polecenie programu SharePoint

1. W rozszerzeniu narzędzi programu SharePoint Pobierz <xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection> obiekt. Sposób uzyskania <xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection> obiektu zależy od typu tworzonego rozszerzenia:

    - W rozszerzeniu systemu projektu programu SharePoint należy użyć <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject.SharePointConnection%2A> właściwości.

         Aby uzyskać więcej informacji o rozszerzeniach systemu projektu, zobacz [Rozszerzanie systemu projektu programu SharePoint](../sharepoint/extending-the-sharepoint-project-system.md).

    - W rozszerzeniu węzła **połączenia programu SharePoint** w **Eksplorator serwera**Użyj <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeContext.SharePointConnection%2A> właściwości. Aby uzyskać <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeContext> obiekt, użyj <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNode.Context%2A> właściwości.

         Aby uzyskać więcej informacji na temat rozszerzeń **Eksplorator serwera** , zobacz [rozszerzanie węzła połączeń SharePoint w Eksplorator serwera](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md).

    - W kodzie, który nie jest częścią rozszerzenia narzędzi programu SharePoint, takiego jak Kreator szablonu projektu, należy użyć <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.SharePointConnection%2A> właściwości.

         Aby uzyskać więcej informacji o pobieraniu usługi projektu, zobacz [Korzystanie z usługi projektu programu SharePoint](../sharepoint/using-the-sharepoint-project-service.md).

2. Wywołaj jedną z metod ExecuteCommand <xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection> obiektu. Przekaż nazwę polecenia, które chcesz wykonać do pierwszego argumentu metody ExecuteCommand. Jeśli polecenie ma parametr niestandardowy, Przekaż ten parametr do drugiego argumentu metody ExecuteCommand.

     Istnieje inne Przeciążenie ExecuteCommand dla każdej obsługiwanej sygnatury polecenia. W poniższej tabeli wymieniono obsługiwane podpisy oraz Przeciążenie, które mają być używane dla poszczególnych sygnatur.

    |Podpis polecenia|Przeciążenie ExecuteCommand do użycia|
    |-----------------------|------------------------------------|
    |Polecenie ma tylko <xref:Microsoft.VisualStudio.SharePoint.Commands.ISharePointCommandContext> parametr domyślny i nie zwraca wartości.|<xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection.ExecuteCommand%2A>|
    |Polecenie ma tylko <xref:Microsoft.VisualStudio.SharePoint.Commands.ISharePointCommandContext> parametr domyślny i wartość zwracaną.|<xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection.ExecuteCommand%2A>|
    |Polecenie ma dwa parametry ( <xref:Microsoft.VisualStudio.SharePoint.Commands.ISharePointCommandContext> parametr domyślny i parametr niestandardowy) i nie zwraca wartości.|<xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection.ExecuteCommand%2A>|
    |Polecenie ma dwa parametry i wartość zwracaną.|<xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection.ExecuteCommand%2A>|

## <a name="example"></a>Przykład
 Poniższy przykład kodu demonstruje, jak użyć przeciążenia, <xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection.ExecuteCommand%2A> Aby wywołać `Contoso.Commands.UpgradeSolution` polecenie, które zostało opisane w [instrukcje: Create a SharePoint Command](../sharepoint/how-to-create-a-sharepoint-command.md).

 [!code-csharp[SPExtensibility.ProjectExtension.UpgradeDeploymentStep#6](../sharepoint/codesnippet/CSharp/UpgradeDeploymentStep/deploymentstepextension/upgradestep.cs#6)]
 [!code-vb[SPExtensibility.ProjectExtension.UpgradeDeploymentStep#6](../sharepoint/codesnippet/VisualBasic/upgradedeploymentstep/deploymentstepextension/upgradestep.vb#6)]

 `Execute`Metoda pokazana w tym przykładzie jest implementacją <xref:Microsoft.VisualStudio.SharePoint.Deployment.IDeploymentStep.Execute%2A> metody <xref:Microsoft.VisualStudio.SharePoint.Deployment.IDeploymentStep> interfejsu w niestandardowym kroku wdrożenia. Aby wyświetlić ten kod w kontekście większego przykładu, zobacz [Przewodnik: Tworzenie niestandardowego kroku wdrożenia dla projektów programu SharePoint](../sharepoint/walkthrough-creating-a-custom-deployment-step-for-sharepoint-projects.md).

 Zwróć uwagę na następujące szczegóły wywołania <xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection.ExecuteCommand%2A> metody:

- Pierwszy parametr identyfikuje polecenie, które chcesz wywołać. Ten ciąg pasuje do wartości przekazanej <xref:Microsoft.VisualStudio.SharePoint.Commands.SharePointCommandAttribute> w definicji polecenia.

- Drugi parametr jest wartością, która ma zostać przekazana do niestandardowego drugiego parametru polecenia. W takim przypadku jest to pełna ścieżka pliku *. wsp* , który jest uaktualniany do witryny programu SharePoint.

- Kod nie przekazuje parametru niejawnego <xref:Microsoft.VisualStudio.SharePoint.Commands.ISharePointCommandContext> do polecenia. Ten parametr jest przesyłany do polecenia automatycznie po wywołaniu polecenia z rozszerzenia systemu projektu programu SharePoint lub rozszerzenia węzła **połączenia programu SharePoint** w **Eksplorator serwera**. W innych typach rozwiązań, takich jak w Kreatorze szablonu projektu, który implementuje <xref:Microsoft.VisualStudio.TemplateWizard.IWizard> interfejs, ten parametr ma **wartość null**.

## <a name="compile-the-code"></a>Kompiluj kod
 Ten przykład wymaga odwołania do zestawu Microsoft. VisualStudio. SharePoint.

## <a name="see-also"></a>Zobacz także
- [Wywoływanie modeli obiektów programu SharePoint](../sharepoint/calling-into-the-sharepoint-object-models.md)
- [Instrukcje: Tworzenie polecenia SharePoint](../sharepoint/how-to-create-a-sharepoint-command.md)
- [Przewodnik: rozszerzona Eksplorator serwera do wyświetlania składników Web Part](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md)
