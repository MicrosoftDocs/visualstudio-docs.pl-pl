---
title: Neutralny język zasobów do lokalizacji
ms.date: 11/04/2016
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c1a671eefae23fb369cd7398efb7589764ebb46f
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2019
ms.locfileid: "55912875"
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