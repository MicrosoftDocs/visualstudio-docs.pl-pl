---
title: 'Instrukcje: Wykonywanie polecenia SharePoint | Dokumentacja firmy Microsoft'
ms.date: 02/02/2017
ms.topic: conceptual
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
ms.openlocfilehash: 6f5c285e71179c5dd59fad0357dbf71ee4b32f9d
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "60049191"
---
# <a name="how-to-execute-a-sharepoint-command"></a>Instrukcje: Wykonywanie polecenia SharePoint
  Jeśli chcesz użyć modelu obiektów serwera w rozszerzenia narzędzi programu SharePoint, należy utworzyć niestandardowy *polecenia SharePoint* wywołać interfejs API. Po zdefiniowaniu polecenia i wdrażania go przy użyciu rozszerzenia narzędzi programu SharePoint, rozszerzenia można wykonać polecenie do wywołania w modelu obiektów serwera SharePoint. Można wykonać polecenia, użyj jednej z metod ExecuteCommand <xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection> obiektu.

 Aby uzyskać więcej informacji o przeznaczeniu poleceń programu SharePoint, zobacz [wywoływanie modeli obiektów SharePoint](../sharepoint/calling-into-the-sharepoint-object-models.md).

### <a name="to-execute-a-sharepoint-command"></a>Wykonywanie polecenia SharePoint

1. Rozszerzenia narzędzi programu SharePoint, na uzyskanie <xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection> obiektu. Sposób uzyskasz <xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection> obiektu zależy od typu rozszerzenia tworzenia:

    - W rozszerzeniach systemu projektu programu SharePoint, należy użyć <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject.SharePointConnection%2A> właściwości.

         Aby uzyskać więcej informacji na temat rozszerzeń systemu projektu, zobacz [rozszerzanie systemu projektu SharePoint](../sharepoint/extending-the-sharepoint-project-system.md).

    - W rozszerzeniu **połączeń SharePoint** w węźle **Eksploratora serwera**, użyj <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeContext.SharePointConnection%2A> właściwości. Aby uzyskać <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeContext> obiektu, należy użyć <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNode.Context%2A> właściwości.

         Aby uzyskać więcej informacji na temat **Eksploratora serwera** rozszerzenia, zobacz [rozszerzanie węzła połączeń SharePoint w Eksploratorze serwera](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md).

    - W kodzie, który nie jest częścią rozszerzenia narzędzi programu SharePoint, takich jak Kreator szablonu projektu, należy użyć <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.SharePointConnection%2A> właściwości.

         Aby uzyskać więcej informacji na temat pobierania z usługi projektu, zobacz [korzystania z usługi projektu SharePoint](../sharepoint/using-the-sharepoint-project-service.md).

2. Wywołanie jednej z metod ExecuteCommand <xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection> obiektu. Przekaż nazwę polecenia, które chcesz wykonać, aby pierwszy argument metody ExecuteCommand. Jeśli polecenie ma parametru niestandardowego, przekaż ten parametru drugiego argumentu metody ExecuteCommand.

     Ma innego przeciążenia ExecuteCommand dla sygnatur obsługiwanych poleceń. W poniższej tabeli wymieniono obsługiwane podpisów i który przeciążenia do użycia dla każdego podpisu.

    |Polecenie podpisu|Parametr ExecuteCommand przeciążenia do użycia|
    |-----------------------|------------------------------------|
    |Polecenie ma tylko wartość domyślna <xref:Microsoft.VisualStudio.SharePoint.Commands.ISharePointCommandContext> parametr i zwraca żadnej wartości.|<xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection.ExecuteCommand%2A>|
    |Polecenie ma tylko wartość domyślna <xref:Microsoft.VisualStudio.SharePoint.Commands.ISharePointCommandContext> parametr i wartość zwracaną.|<xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection.ExecuteCommand%2A>|
    |Polecenie ma dwa parametry (wartość domyślna <xref:Microsoft.VisualStudio.SharePoint.Commands.ISharePointCommandContext> i niestandardowego parametru) i nie zwraca wartości.|<xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection.ExecuteCommand%2A>|
    |Polecenie ma dwa parametry i zwracane wartości.|<xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection.ExecuteCommand%2A>|

## <a name="example"></a>Przykład
 Poniższy przykład kodu demonstruje sposób używania <xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection.ExecuteCommand%2A> przeciążenia do wywołania `Contoso.Commands.UpgradeSolution` polecenia, które jest opisane w [jak: Tworzenie polecenia SharePoint](../sharepoint/how-to-create-a-sharepoint-command.md).

 [!code-csharp[SPExtensibility.ProjectExtension.UpgradeDeploymentStep#6](../sharepoint/codesnippet/CSharp/UpgradeDeploymentStep/deploymentstepextension/upgradestep.cs#6)]
 [!code-vb[SPExtensibility.ProjectExtension.UpgradeDeploymentStep#6](../sharepoint/codesnippet/VisualBasic/upgradedeploymentstep/deploymentstepextension/upgradestep.vb#6)]

 `Execute` Metod przedstawionych w tym przykładzie jest implementacją <xref:Microsoft.VisualStudio.SharePoint.Deployment.IDeploymentStep.Execute%2A> metody <xref:Microsoft.VisualStudio.SharePoint.Deployment.IDeploymentStep> interfejsu, niestandardowego kroku wdrożenia. Aby wyświetlić ten kod w kontekście większego przykładu, zobacz [instruktażu: Tworzenie niestandardowego kroku wdrożenia dla projektów programu SharePoint](../sharepoint/walkthrough-creating-a-custom-deployment-step-for-sharepoint-projects.md).

 Należy zauważyć następujące szczegółowe informacje o wywołaniu <xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection.ExecuteCommand%2A> metody:

- Pierwszy parametr określa polecenie, które ma zostać wywołana. Ten ciąg pasuje do wartości, który jest przekazywany do <xref:Microsoft.VisualStudio.SharePoint.Commands.SharePointCommandAttribute> w definicji polecenia.

- Drugi parametr jest wartością, który chcesz przekazać do parametru niestandardowego drugiego polecenia. W tym przypadku jest pełna ścieżka *.wsp* pliku, który jest uaktualniany do witryny programu SharePoint.

- Kod nie zostały spełnione niejawny <xref:Microsoft.VisualStudio.SharePoint.Commands.ISharePointCommandContext> do polecenia. Ten parametr jest przekazywany do polecenia automatycznie podczas wywoływania polecenia rozszerzenia systemu projektu programu SharePoint lub rozszerzenie **połączeń SharePoint** w węźle **Eksploratora serwera**. W przypadku innych typów rozwiązań, takich jak Kreator szablonu projektu, który implementuje <xref:Microsoft.VisualStudio.TemplateWizard.IWizard> interfejsu, ten parametr jest **null**.

## <a name="compile-the-code"></a>Skompilować kod
 W tym przykładzie wymaga to dodania odwołania do zestawu Microsoft.VisualStudio.SharePoint.

## <a name="see-also"></a>Zobacz także
- [Wywoływanie modeli obiektów SharePoint](../sharepoint/calling-into-the-sharepoint-object-models.md)
- [Instrukcje: Tworzenie polecenia SharePoint](../sharepoint/how-to-create-a-sharepoint-command.md)
- [Przewodnik: Rozszerzanie Eksploratora serwera na potrzeby wyświetlania składników web Part](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md)
