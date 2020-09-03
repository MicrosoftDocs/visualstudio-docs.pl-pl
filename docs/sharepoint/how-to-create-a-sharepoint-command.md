---
title: 'Instrukcje: Tworzenie polecenia SharePoint | Microsoft Docs'
ms.date: 02/02/2017
ms.topic: how-to
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
ms.openlocfilehash: 15ea7ff86e90bf7a474f9d64c30a9803e3e20bf5
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "86016216"
---
# <a name="how-to-create-a-sharepoint-command"></a>Instrukcje: Tworzenie polecenia SharePoint
  Jeśli chcesz użyć modelu obiektów serwera w rozszerzeniu narzędzi programu SharePoint, musisz utworzyć niestandardowe *polecenie programu SharePoint* , aby wywołać interfejs API. Zdefiniuj polecenie programu SharePoint w zestawie, które może bezpośrednio wywołać model obiektów serwera.

 Aby uzyskać więcej informacji na temat przeznaczenia poleceń programu SharePoint, zobacz [Wywoływanie modeli obiektów programu SharePoint](../sharepoint/calling-into-the-sharepoint-object-models.md).

### <a name="to-create-a-sharepoint-command"></a>Aby utworzyć polecenie programu SharePoint

1. Utwórz projekt biblioteki klas, który ma następującą konfigurację:

    - Jest celem .NET Framework 3,5. Aby uzyskać więcej informacji na temat wybierania platformy docelowej, zobacz [How to: Target a Version of a .NET Framework](../ide/visual-studio-multi-targeting-overview.md).

    - Dotyczy platformy AnyCPU lub x64. Domyślnie platformą docelową dla projektów biblioteki klas jest AnyCPU. Aby uzyskać więcej informacji na temat wybierania platformy docelowej, zobacz [How to: Configure projects to target platforms](../ide/how-to-configure-projects-to-target-platforms.md).

    > [!NOTE]
    > Nie można zaimplementować polecenia programu SharePoint w tym samym projekcie, który definiuje rozszerzenie narzędzi programu SharePoint, ponieważ polecenia programu SharePoint są przeznaczone dla narzędzi .NET Framework 3,5 i SharePoint Tools Target [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] . Należy zdefiniować wszystkie polecenia programu SharePoint, które są używane przez rozszerzenie w oddzielnym projekcie. Aby uzyskać więcej informacji, zobacz [Wdrażanie rozszerzeń dla narzędzi programu SharePoint w programie Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).

2. Dodaj odwołania do następujących zestawów:

    - Microsoft. VisualStudio. SharePoint. Commands

    - Microsoft. SharePoint

3. W klasie w projekcie Utwórz metodę, która definiuje polecenie programu SharePoint. Metoda musi być zgodna z następującymi wskazówkami:

    - Może mieć jeden lub dwa parametry.

         Pierwszy parametr musi być <xref:Microsoft.VisualStudio.SharePoint.Commands.ISharePointCommandContext> obiektem. Ten obiekt zawiera Microsoft. SharePoint. SPSite lub Microsoft. SharePoint. SPWeb, w którym polecenie jest wykonywane. Udostępnia również <xref:Microsoft.VisualStudio.SharePoint.Commands.ISharePointCommandLogger> obiekt, którego można użyć do zapisu komunikatów w oknie **danych wyjściowych** lub oknie **Lista błędów** w programie Visual Studio.

         Drugi parametr może być wybranym typem, ale ten parametr jest opcjonalny. Możesz dodać ten parametr do polecenia programu SharePoint, jeśli chcesz przekazać dane z rozszerzenia narzędzi SharePoint Tools do polecenia.

    - Może mieć wartość zwracaną, ale jest to opcjonalne.

    - Drugi parametr i zwracana wartość muszą być typu, który może zostać Zserializowany przez Windows Communication Foundation (WCF). Aby uzyskać więcej informacji, zobacz [Typy obsługiwane przez serializator kontraktu danych](/dotnet/framework/wcf/feature-details/types-supported-by-the-data-contract-serializer) i [Używanie klasy XmlSerializer](/dotnet/framework/wcf/feature-details/using-the-xmlserializer-class).

    - Metoda może mieć widoczność (**publiczna**, **wewnętrzna**lub **prywatna**) i może być statyczna lub niestatyczna.

4. Zastosuj <xref:Microsoft.VisualStudio.SharePoint.Commands.SharePointCommandAttribute> do metody. Ten atrybut określa unikatowy identyfikator polecenia; Ten identyfikator nie musi być zgodny z nazwą metody.

     Należy określić ten sam unikatowy identyfikator, gdy wywołasz polecenie z rozszerzenia narzędzi programu SharePoint. Aby uzyskać więcej informacji, zobacz [How to: Execute a SharePoint Command](../sharepoint/how-to-execute-a-sharepoint-command.md).

## <a name="example"></a>Przykład
 Poniższy przykład kodu demonstruje polecenie programu SharePoint o identyfikatorze `Contoso.Commands.UpgradeSolution` . To polecenie używa interfejsów API w modelu obiektów serwera do uaktualnienia do wdrożonego rozwiązania.

 [!code-csharp[SPExtensibility.ProjectExtension.UpgradeDeploymentStep#5](../sharepoint/codesnippet/CSharp/UpgradeDeploymentStep/SharePointCommands/Commands.cs#5)]
 [!code-vb[SPExtensibility.ProjectExtension.UpgradeDeploymentStep#5](../sharepoint/codesnippet/VisualBasic/upgradedeploymentstep/sharepointcommands/commands.vb#5)]

 Oprócz niejawnego pierwszego <xref:Microsoft.VisualStudio.SharePoint.Commands.ISharePointCommandContext> parametru to polecenie ma także niestandardowy parametr ciągu, który zawiera pełną ścieżkę pliku. wsp, który jest uaktualniany do witryny programu SharePoint. Aby wyświetlić ten kod w kontekście większego przykładu, zobacz [Przewodnik: Tworzenie niestandardowego kroku wdrożenia dla projektów programu SharePoint](../sharepoint/walkthrough-creating-a-custom-deployment-step-for-sharepoint-projects.md).

## <a name="compiling-the-code"></a>Kompilowanie kodu
 Ten przykład wymaga odwołania do następujących zestawów:

- Microsoft. VisualStudio. SharePoint. Commands

- Microsoft. SharePoint

## <a name="deploying-the-command"></a>Wdrażanie polecenia
 Aby wdrożyć polecenie, należy uwzględnić zestaw poleceń w tym samym [!include[vsprvs](../sharepoint/includes/vsprvs-md.md)] pakiecie rozszerzenia (*VSIX*) z zestawem rozszerzeń, który używa polecenia. Należy również dodać wpis dla zestawu poleceń w pliku Extension. vsixmanifest. Aby uzyskać więcej informacji, zobacz [Wdrażanie rozszerzeń dla narzędzi programu SharePoint w programie Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).

## <a name="see-also"></a>Zobacz też
- [Wywoływanie modeli obiektów programu SharePoint](../sharepoint/calling-into-the-sharepoint-object-models.md)
- [Instrukcje: wykonywanie polecenia SharePoint](../sharepoint/how-to-execute-a-sharepoint-command.md)
- [Przewodnik: rozszerzona Eksplorator serwera do wyświetlania składników Web Part](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md)
