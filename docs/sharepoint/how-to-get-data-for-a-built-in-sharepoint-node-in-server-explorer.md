---
title: Pobierz dane dla wbudowanego węzła programu SharePoint w Eksplorator serwera
titleSuffix: ''
description: Pobierz dane dla podstawowego składnika programu SharePoint wbudowanego węzła programu SharePoint w oknie Eksplorator serwera programu Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint Connections [SharePoint development in Visual Studio], extending a node
- SharePoint development in Visual Studio, extending SharePoint Connections node in Server Explorer
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: c58de345400c7b724a755839cb8baa1afc3cfce2
ms.sourcegitcommit: 80fc9a72e9a1aba2d417dbfee997fab013fc36ac
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/02/2021
ms.locfileid: "106217193"
---
# <a name="how-to-get-data-for-a-built-in-sharepoint-node-in-server-explorer"></a>Instrukcje: pobieranie danych dla wbudowanego węzła programu SharePoint w Eksplorator serwera
  Dla każdego wbudowanego węzła programu SharePoint w **Eksplorator serwera** można uzyskać dane dla podstawowego składnika programu SharePoint reprezentowanego przez ten węzeł. Aby uzyskać więcej informacji, zobacz sekcję Rozpoznaj [węzeł połączenia SharePoint w Eksplorator serwera](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md).

## <a name="example"></a>Przykład
 Poniższy przykład kodu demonstruje, jak uzyskać dane dla podstawowej listy programu SharePoint reprezentowanej przez węzeł listy w **Eksplorator serwera**. Domyślnie węzły listy mają **Widok w** elemencie menu kontekstowego przeglądarki, który można kliknąć, aby otworzyć listy w przeglądarce sieci Web. Ten przykład rozszerza listę węzłów przez dodanie widoku w elemencie menu kontekstowego **programu Visual Studio** , który otwiera listy bezpośrednio w programie Visual Studio. Kod uzyskuje dostęp do danych listy dla węzła, aby uzyskać adres URL listy otwartej w programie Visual Studio.

 :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/projectsystemexamples/extension/serverexplorerextensionnodeinfo.vb" id="Snippet10":::
 :::code language="csharp" source="../sharepoint/codesnippet/CSharp/projectsystemexamples/extension/serverexplorerextensionnodeinfo.cs" id="Snippet10":::

 W tym przykładzie użyto usługi projektu programu SharePoint w celu uzyskania <xref:EnvDTE.DTE> obiektu, który jest używany do otwierania list w programie Visual Studio. Aby uzyskać więcej informacji na temat usługi projektu programu SharePoint, zobacz [Korzystanie z usługi projektu programu SharePoint](../sharepoint/using-the-sharepoint-project-service.md).

 Aby uzyskać więcej informacji na temat podstawowych zadań tworzenia rozszerzenia dla węzła programu SharePoint, zobacz [How to: rozszerzanie węzła programu SharePoint w Eksplorator serwera](../sharepoint/how-to-extend-a-sharepoint-node-in-server-explorer.md).

## <a name="compile-the-code"></a>Kompiluj kod
 Ten przykład wymaga odwołania do następujących zestawów:

- EnvDTE

- Microsoft. VisualStudio. SharePoint

- Microsoft. VisualStudio. SharePoint. Explorer. Extensions

- System. ComponentModel. kompozycji

## <a name="deploy-the-extension"></a>Wdróż rozszerzenie
 Aby wdrożyć rozszerzenie **Eksplorator serwera** , Utwórz [!include[vsprvs](../sharepoint/includes/vsprvs-md.md)] pakiet rozszerzenia (VSIX) dla zestawu i innych plików, które chcesz dystrybuować z rozszerzeniem. Aby uzyskać więcej informacji, zobacz [Wdrażanie rozszerzeń dla narzędzi programu SharePoint w programie Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).

## <a name="see-also"></a>Zobacz też
- [Rozwiń węzeł połączenia programu SharePoint w Eksplorator serwera](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md)
- [Instrukcje: zwiększanie węzła programu SharePoint w Eksplorator serwera](../sharepoint/how-to-extend-a-sharepoint-node-in-server-explorer.md)
- [Korzystanie z usługi projektu SharePoint](../sharepoint/using-the-sharepoint-project-service.md)
- [Wdróż rozszerzenia dla narzędzi programu SharePoint w programie Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md)
