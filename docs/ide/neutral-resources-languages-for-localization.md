---
title: Neutralny język zasobów do lokalizacji
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: conceptual
helpviewer_keywords:
- localization [Visual Studio], resources
- NeutralResourcesLanguageAttribute class
- globalization [Visual Studio], resources
- resources [Visual Studio], fallback system
- culture, locating resources
- neutral resources
ms.assetid: ef064995-3b84-4698-a708-9689b7723533
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: e246d31a3c3126f28cd6be383b368a1373118504
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53916812"
---
# <a name="neutral-resources-languages-for-localization"></a>Neutralny język zasobów do lokalizacji

<xref:System.Resources.NeutralResourcesLanguageAttribute> Klasa określa kulturę uwzględnione w głównym zestawie zasoby. Ten atrybut jest używany jako zwiększeniem wydajności, dzięki czemu <xref:System.Resources.ResourceManager> obiektu nie Szukaj zasobów, które znajdują się w głównym zestawie.

 Poniższy kod przedstawia sposób ustawiania języka neutralne zasoby. Kod można umieścić w skrypcie kompilacji lub w pliku AssemblyInfo.vb lub AssemblyInfo.cs.

```vb
' Set neutral resources language for assembly.
<Assembly: NeutralResourcesLanguageAttribute("en")>
```

```csharp
// Set neutral resources language for assembly.
[assembly: NeutralResourcesLanguageAttribute("en")]
```

## <a name="see-also"></a>Zobacz także

- <xref:System.Resources.ResourceManager>
- [Wprowadzenie do aplikacji międzynarodowych opartych na programie .NET Framework](../ide/introduction-to-international-applications-based-on-the-dotnet-framework.md)
- [Hierarchiczna organizacja zasobów do lokalizacji](../ide/hierarchical-organization-of-resources-for-localization.md)
- [Lokalizowanie aplikacji](../ide/localizing-applications.md)
- [Globalizowanie i lokalizowanie aplikacji](../ide/globalizing-and-localizing-applications.md)