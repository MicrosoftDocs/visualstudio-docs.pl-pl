---
title: Pobieranie danych dla wbudowanego węzła SharePoint w Eksploratorze serwera
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint Connections [SharePoint development in Visual Studio], extending a node
- SharePoint development in Visual Studio, extending SharePoint Connections node in Server Explorer
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: b90582c9b8d352f95d3d5abb3bbb7fb69283b06b
ms.sourcegitcommit: 25570fb5fb197318a96d45160eaf7def60d49b2b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/30/2019
ms.locfileid: "66401419"
---
# <a name="how-to-get-data-for-a-built-in-sharepoint-node-in-server-explorer"></a>Instrukcje: Pobieranie danych dla wbudowanego węzła SharePoint w Eksploratorze serwera
  Dla każdego wbudowanego węzła SharePoint w **Eksploratora serwera**, możesz uzyskać dane podstawowego składnika programu SharePoint, który reprezentuje węzeł. Aby uzyskać więcej informacji, zobacz [rozszerzanie węzła połączeń SharePoint w Eksploratorze serwera](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md).

## <a name="example"></a>Przykład
 Poniższy przykład kodu demonstruje sposób uzyskiwania danych podstawowych listy programu SharePoint reprezentująca węzeł listy w **Eksploratora serwera**. Domyślnie lista węzły mają **Pokaż w przeglądarce** element menu kontekstowego, który można kliknąć, aby otworzyć listy w przeglądarce sieci Web. W tym przykładzie rozszerza listy węzłów, dodając **widok w programie Visual Studio** element menu kontekstowego, który spowoduje otwarcie listy bezpośrednio w programie Visual Studio. Kod uzyskuje dostęp do danych listy dla węzła uzyskać adres URL na liście, aby otworzyć w programie Visual Studio.

 [!code-vb[SPExtensibility.ProjectSystemExtension.General#10](../sharepoint/codesnippet/VisualBasic/projectsystemexamples/extension/serverexplorerextensionnodeinfo.vb#10)]
 [!code-csharp[SPExtensibility.ProjectSystemExtension.General#10](../sharepoint/codesnippet/CSharp/projectsystemexamples/extension/serverexplorerextensionnodeinfo.cs#10)]

 W tym przykładzie używa usługi projektu programu SharePoint do uzyskania <xref:EnvDTE.DTE> obiekt, który jest używany do otwierania listy w programie Visual Studio. Aby uzyskać więcej informacji na temat usługi projektu programu SharePoint, zobacz [korzystania z usługi projektu SharePoint](../sharepoint/using-the-sharepoint-project-service.md).

 Aby uzyskać więcej informacji na temat podstawowych zadań, aby utworzyć rozszerzenie dla węzła SharePoint, zobacz [jak: Rozszerzanie węzła SharePoint w Eksploratorze serwera](../sharepoint/how-to-extend-a-sharepoint-node-in-server-explorer.md).

## <a name="compile-the-code"></a>Skompilować kod
 Ten przykład wymaga odwołania do następujących zestawów:

- EnvDTE

- Microsoft.VisualStudio.SharePoint

- Microsoft.VisualStudio.SharePoint.Explorer.Extensions

- System.ComponentModel.Composition

## <a name="deploy-the-extension"></a>Wdrażanie rozszerzenia
 Aby wdrożyć **Eksploratora serwera** rozszerzenia, Utwórz [!include[vsprvs](../sharepoint/includes/vsprvs-md.md)] rozszerzenie (VSIX), pakiet dla zestawu i innych plików, które chcesz dystrybuować z rozszerzeniem. Aby uzyskać więcej informacji, zobacz [wdrażanie rozszerzeń dla narzędzi SharePoint w programie Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).

## <a name="see-also"></a>Zobacz także
- [Rozszerzanie węzła połączeń SharePoint w Eksploratorze serwera](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md)
- [Instrukcje: Rozszerzanie węzła SharePoint w Eksploratorze serwera](../sharepoint/how-to-extend-a-sharepoint-node-in-server-explorer.md)
- [Korzystanie z usługi projektu SharePoint](../sharepoint/using-the-sharepoint-project-service.md)
- [Wdrażanie rozszerzeń dla narzędzi SharePoint w programie Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md)
