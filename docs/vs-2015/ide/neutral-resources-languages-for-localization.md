---
title: Neutralne Języki zasobów dla lokalizacji | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- localization [Visual Studio], resources
- NeutralResourcesLanguageAttribute class
- globalization [Visual Studio], resources
- resources [Visual Studio], fallback system
- culture, locating resources
- neutral resources
ms.assetid: ef064995-3b84-4698-a708-9689b7723533
caps.latest.revision: 9
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 85e0be0172f27732f8efeb882cbcde5b9c6aef3d
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72670390"
---
# <a name="neutral-resources-languages-for-localization"></a>Neutralny język zasobów do lokalizacji
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Klasa <xref:System.Resources.NeutralResourcesLanguageAttribute> określa kulturę zasobów zawartych w zestawie głównym. Ten atrybut jest używany jako rozszerzenie wydajności, aby obiekt <xref:System.Resources.ResourceManager> nie przeszukał zasobów uwzględnionych w głównym zestawie.

 Poniższy kod przedstawia sposób ustawienia języka neutralnych zasobów. Kod można umieścić w skrypcie kompilacji lub w pliku AssemblyInfo. vb lub AssemblyInfo.cs.

```vb
' Set neutral resources language for assembly.
<Assembly: NeutralResourcesLanguageAttribute("en")>

```

```csharp
// Set neutral resources language for assembly.
[assembly: NeutralResourcesLanguageAttribute("en")]
```

## <a name="see-also"></a>Zobacz też
 <xref:System.Resources.ResourceManager> [wprowadzenie do aplikacji międzynarodowych opartych na .NET Framework](../ide/introduction-to-international-applications-based-on-the-dotnet-framework.md) [hierarchicznej organizacji zasobów dla lokalizacji](../ide/hierarchical-organization-of-resources-for-localization.md) [lokalizowania aplikacji](../ide/localizing-applications.md) [, które umożliwiają globalizację i lokalizowanie aplikacji](../ide/globalizing-and-localizing-applications.md)
