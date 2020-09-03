---
title: 'Instrukcje: obsługa konfliktów wdrożenia | Microsoft Docs'
ms.date: 02/02/2017
ms.topic: how-to
helpviewer_keywords:
- SharePoint development in Visual Studio, extending deployment
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 5df9677fd349825983cc33c5a8ed2648f34b8c9e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "86015309"
---
# <a name="how-to-handle-deployment-conflicts"></a>Instrukcje: obsługa konfliktów wdrożenia
  Możesz podać własny kod do obsługi konfliktów wdrożenia dla elementu projektu programu SharePoint. Można na przykład określić, czy wszystkie pliki w bieżącym elemencie projektu istnieją już w lokalizacji wdrożenia, a następnie usunąć wdrożone pliki przed wdrożeniem bieżącego elementu projektu. Aby uzyskać więcej informacji na temat konfliktów wdrożenia, zobacz [rozszerzanie pakietów i wdrażanie programu SharePoint](../sharepoint/extending-sharepoint-packaging-and-deployment.md).

### <a name="to-handle-a-deployment-conflict"></a>Aby obsłużyć konflikt wdrożenia

1. Utwórz rozszerzenie elementu projektu, rozszerzenie projektu lub definicję nowego typu elementu projektu. Aby uzyskać więcej informacji, zobacz następujące tematy:

    - [Instrukcje: Tworzenie rozszerzenia elementu projektu SharePoint](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md)

    - [Instrukcje: Tworzenie rozszerzenia projektu SharePoint](../sharepoint/how-to-create-a-sharepoint-project-extension.md)

    - [Instrukcje: Definiowanie typu elementu projektu SharePoint](../sharepoint/how-to-define-a-sharepoint-project-item-type.md)

2. W rozszerzeniu Obsługuj <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.DeploymentStepStarted> zdarzenie <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemType> obiektu (w rozszerzeniu elementu projektu lub rozszerzeniu projektu) lub <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeDefinition> obiekt (w definicji nowego typu elementu projektu).

3. W programie obsługi zdarzeń Ustal, czy występuje konflikt między wdrażanym elementem projektu a wdrożonym rozwiązaniem w witrynie programu SharePoint na podstawie kryteriów, które są stosowane do danego scenariusza. Można użyć <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemEventArgs.ProjectItem%2A> Właściwości parametru argumenty zdarzenia do analizy elementu projektu, który jest wdrażany, i można analizować pliki w lokalizacji wdrożenia, wywołując polecenie SharePoint zdefiniowane do tego celu.

     W przypadku wielu typów konfliktów można najpierw określić, który krok wdrożenia ma być wykonywany. Można to zrobić przy użyciu <xref:Microsoft.VisualStudio.SharePoint.DeploymentStepStartedEventArgs.DeploymentStepInfo%2A> Właściwości parametru argumenty zdarzenia. Chociaż zwykle warto wykryć konflikty podczas wbudowanego <xref:Microsoft.VisualStudio.SharePoint.Deployment.DeploymentStepIds.AddSolution> kroku wdrożenia, można wyszukać konflikty podczas dowolnego kroku wdrożenia.

4. Jeśli istnieje konflikt, użyj <xref:Microsoft.VisualStudio.SharePoint.Deployment.IDeploymentConflictCollection.Add%2A> metody <xref:Microsoft.VisualStudio.SharePoint.DeploymentStepStartedEventArgs.Conflicts%2A> Właściwości argumentów zdarzenia, aby utworzyć nowy <xref:Microsoft.VisualStudio.SharePoint.Deployment.IDeploymentConflict> obiekt. Ten obiekt reprezentuje konflikt wdrożenia. W wywołaniu <xref:Microsoft.VisualStudio.SharePoint.Deployment.IDeploymentConflictCollection.Add%2A> metody, należy również określić metodę, która jest wywoływana w celu rozwiązania konfliktu.

## <a name="example"></a>Przykład
 Poniższy przykład kodu demonstruje podstawowy proces obsługi konfliktu wdrożenia w rozszerzeniu elementu projektu dla elementów projektu definicji listy. Aby obsłużyć konflikt wdrożenia dla innego typu elementu projektu, Przekaż inny ciąg do <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemTypeAttribute> . Aby uzyskać więcej informacji, zobacz sekcję [rozszerzając elementy projektu programu SharePoint](../sharepoint/extending-sharepoint-project-items.md).

 Dla uproszczenia <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.DeploymentStepStarted> w programie obsługi zdarzeń w tym przykładzie przyjęto założenie, że istnieje konflikt wdrożenia (oznacza to, że zawsze dodaje nowy <xref:Microsoft.VisualStudio.SharePoint.Deployment.IDeploymentConflict> obiekt), a `Resolve` Metoda po prostu zwraca **wartość true** , aby wskazać, że konflikt został rozwiązany. W rzeczywistym scenariuszu <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.DeploymentStepStarted> program obsługi zdarzeń najpierw określi, czy istnieje konflikt między plikiem w bieżącym elemencie projektu i plikiem w lokalizacji wdrożenia, a następnie Dodaj <xref:Microsoft.VisualStudio.SharePoint.Deployment.IDeploymentConflict> obiekt tylko wtedy, gdy istnieje konflikt. Na przykład można użyć `e.ProjectItem.Files` właściwości w programie obsługi zdarzeń do przeanalizowania plików w elemencie projektu i można wywołać polecenie programu SharePoint w celu przeanalizowania plików w lokalizacji wdrożenia. Podobnie w rzeczywistym scenariuszu `Resolve` Metoda może wywołać polecenie programu SharePoint w celu rozwiązania konfliktu w witrynie programu SharePoint. Aby uzyskać więcej informacji na temat tworzenia poleceń programu SharePoint, zobacz [How to: Create a SharePoint Command](../sharepoint/how-to-create-a-sharepoint-command.md).

 [!code-vb[SPExtensibility.ProjectItemExtension.DeploymentConflict#1](../sharepoint/codesnippet/VisualBasic/deploymentconflict/extension/deploymentconflictextension.vb#1)]
 [!code-csharp[SPExtensibility.ProjectItemExtension.DeploymentConflict#1](../sharepoint/codesnippet/CSharp/deploymentconflict/extension/deploymentconflictextension.cs#1)]

## <a name="compile-the-code"></a>Kompiluj kod
 Ten przykład wymaga odwołania do następujących zestawów:

- Microsoft. VisualStudio. SharePoint

- System. ComponentModel. kompozycji

## <a name="deploy-the-extension"></a>Wdróż rozszerzenie
 Aby wdrożyć rozszerzenie, Utwórz [!include[vsprvs](../sharepoint/includes/vsprvs-md.md)] pakiet rozszerzenia (VSIX) dla zestawu i wszystkie inne pliki, które chcesz dystrybuować z rozszerzeniem. Aby uzyskać więcej informacji, zobacz [Wdrażanie rozszerzeń dla narzędzi programu SharePoint w programie Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).

## <a name="see-also"></a>Zobacz też
- [Rozszerzona pakowanie i wdrażanie programu SharePoint](../sharepoint/extending-sharepoint-packaging-and-deployment.md)
- [Zwiększ elementy projektu SharePoint](../sharepoint/extending-sharepoint-project-items.md)
- [Instrukcje: uruchamianie kodu po wykonaniu kroków wdrożenia](../sharepoint/how-to-run-code-when-deployment-steps-are-executed.md)
- [Instrukcje: Tworzenie polecenia SharePoint](../sharepoint/how-to-create-a-sharepoint-command.md)
