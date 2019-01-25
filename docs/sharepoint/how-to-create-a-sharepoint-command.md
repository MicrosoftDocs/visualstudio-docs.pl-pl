---
title: 'Instrukcje: Tworzenie polecenia SharePoint | Dokumentacja firmy Microsoft'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint commands [SharePoint development in Visual Studio], creating
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: da1b31b7cc1436c90437a9e2b5ef66adfee825b1
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2019
ms.locfileid: "54867900"
---
# <a name="how-to-create-a-sharepoint-command"></a>Instrukcje: Tworzenie polecenia SharePoint
  Jeśli chcesz użyć modelu obiektów serwera w rozszerzenia narzędzi programu SharePoint, należy utworzyć niestandardowy *polecenia SharePoint* wywołać interfejs API. Polecenie programu SharePoint należy zdefiniować w zestawie, który można wywoływać bezpośrednio do modelu obiektów serwera.  
  
 Aby uzyskać więcej informacji o przeznaczeniu poleceń programu SharePoint, zobacz [wywoływanie modeli obiektów SharePoint](../sharepoint/calling-into-the-sharepoint-object-models.md).  
  
### <a name="to-create-a-sharepoint-command"></a>Aby utworzyć polecenie programu SharePoint  
  
1.  Utwórz projekt biblioteki klas, które ma następującą konfigurację:  
  
    -   Jest przeznaczony dla programu .NET Framework 3.5. Aby uzyskać więcej informacji o wybieraniu platformę docelową, zobacz [jak: Docelowa wersja systemu .NET Framework](../ide/how-to-target-a-version-of-the-dotnet-framework.md).  
  
    -   Jest przeznaczony dla AnyCPU lub x64 platformy. Domyślnie platforma docelowa projekty bibliotek klas to AnyCPU. Aby uzyskać więcej informacji o wybieraniu platformę docelową, zobacz [jak: Konfigurowanie projektów pod kątem platform docelowych](../ide/how-to-configure-projects-to-target-platforms.md).  
  
    > [!NOTE]  
    >  Nie można zaimplementować polecenia programu SharePoint w tym samym projekcie, który definiuje rozszerzenia narzędzi programu SharePoint, ponieważ poleceń programu SharePoint docelowych .NET Framework 3.5 i programu SharePoint narzędzia rozszerzeń element docelowy [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)]. Należy zdefiniować żadnych poleceń programu SharePoint, które są używane przez rozszerzenie w osobnym projekcie. Aby uzyskać więcej informacji, zobacz [wdrażanie rozszerzeń dla narzędzi SharePoint w programie Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).  
  
2.  Dodaj odwołania do następujących zestawów:  
  
    -   Microsoft.VisualStudio.SharePoint.Commands  
  
    -   Microsoft.SharePoint  
  
3.  Klasy w projekcie Utwórz metodę, która definiuje polecenie programu SharePoint. Metoda musi być zgodna z następującymi zasadami:  
  
    -   Może mieć jeden lub dwa parametry.  
  
         Pierwszy parametr musi być <xref:Microsoft.VisualStudio.SharePoint.Commands.ISharePointCommandContext> obiektu. Ten obiekt zawiera Microsoft.SharePoint.SPSite lub Microsoft.SharePoint.SPWeb wykonywania polecenia. Zapewnia także <xref:Microsoft.VisualStudio.SharePoint.Commands.ISharePointCommandLogger> obiekt, który może służyć do zapisywania komunikatów do **dane wyjściowe** okna lub **lista błędów** okna w programie Visual Studio.  
  
         Drugi parametr może być typem wybranego, ale ten parametr jest opcjonalny. Ten parametr można dodać do polecenia programu SharePoint, jeśli trzeba przekazać dane z rozszerzenia narzędzi programu SharePoint do polecenia.  
  
    -   Może mieć wartości zwracanej, ale jest to opcjonalne.  
  
    -   Drugi parametr i wartość zwracana musi być typem, który może być serializowany przez Windows Communication Foundation (WCF). Aby uzyskać więcej informacji, zobacz [typy obsługiwane przez serializator kontraktu danych](/dotnet/framework/wcf/feature-details/types-supported-by-the-data-contract-serializer) i [przy użyciu klasy XmlSerializer](/dotnet/framework/wcf/feature-details/using-the-xmlserializer-class).  
  
    -   Metoda może mieć żadnych widoczności (**publicznych**, **wewnętrzny**, lub **prywatnej**), i może być statyczne lub niestatycznej.  
  
4.  Zastosuj <xref:Microsoft.VisualStudio.SharePoint.Commands.SharePointCommandAttribute> do metody. Ten atrybut określa unikatowy identyfikator dla polecenia; Ten identyfikator nie musi być zgodna z nazwą metody.  
  
     Podczas wywoływania polecenia z rozszerzenia narzędzi programu SharePoint, należy określić ten sam Unikatowy identyfikator. Aby uzyskać więcej informacji, zobacz [jak: Wykonywanie polecenia SharePoint](../sharepoint/how-to-execute-a-sharepoint-command.md).  
  
## <a name="example"></a>Przykład  
 Poniższy przykład kodu demonstruje polecenia programu SharePoint, która ma identyfikator `Contoso.Commands.UpgradeSolution`. To polecenie używa interfejsów API w modelu obiektów serwera, aby uaktualnić do wdrożonym rozwiązaniem.  
  
 [!code-csharp[SPExtensibility.ProjectExtension.UpgradeDeploymentStep#5](../sharepoint/codesnippet/CSharp/UpgradeDeploymentStep/SharePointCommands/Commands.cs#5)]
 [!code-vb[SPExtensibility.ProjectExtension.UpgradeDeploymentStep#5](../sharepoint/codesnippet/VisualBasic/upgradedeploymentstep/sharepointcommands/commands.vb#5)]  
  
 Oprócz pierwszego niejawne <xref:Microsoft.VisualStudio.SharePoint.Commands.ISharePointCommandContext> parametr, to polecenie ma również parametr niestandardowy ciąg, który zawiera pełną ścieżkę pliku .wsp, który jest uaktualniany do witryny programu SharePoint. Aby wyświetlić ten kod w kontekście większego przykładu, zobacz [instruktażu: Tworzenie niestandardowego kroku wdrożenia dla projektów programu SharePoint](../sharepoint/walkthrough-creating-a-custom-deployment-step-for-sharepoint-projects.md).  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Ten przykład wymaga odwołania do następujących zestawów:  
  
-   Microsoft.VisualStudio.SharePoint.Commands  
  
-   Microsoft.SharePoint  
  
## <a name="deploying-the-command"></a>Wdrażanie polecenia  
 Aby wdrożyć polecenia, należy uwzględnić zestawu poleceń w tej samej [!include[vsprvs](../sharepoint/includes/vsprvs-md.md)] rozszerzenia (*vsix*) pakiet za pomocą zestawu rozszerzeń, która używa polecenia. Musisz również dodać wpis dla zestawu poleceń w pliku extension.vsixmanifest. Aby uzyskać więcej informacji, zobacz [wdrażanie rozszerzeń dla narzędzi SharePoint w programie Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).  
  
## <a name="see-also"></a>Zobacz także
 [Wywoływanie modeli obiektów SharePoint](../sharepoint/calling-into-the-sharepoint-object-models.md)   
 [Instrukcje: Wykonywanie polecenia SharePoint](../sharepoint/how-to-execute-a-sharepoint-command.md)   
 [Przewodnik: Rozszerzanie Eksploratora serwera na potrzeby wyświetlania składników web Part](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md)  
