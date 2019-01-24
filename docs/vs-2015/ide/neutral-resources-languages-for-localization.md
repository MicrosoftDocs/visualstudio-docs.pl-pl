---
title: Neutralny język zasobów dla lokalizacji | Dokumentacja firmy Microsoft
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
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: da39ed9373daaa1dbef21ad36931ce97ea1f1e1b
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54764776"
---
# <a name="neutral-resources-languages-for-localization"></a>Neutralny język zasobów do lokalizacji
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

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
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Resources.ResourceManager>   
 [Wprowadzenie do aplikacji międzynarodowych opartych na programie .NET Framework](../ide/introduction-to-international-applications-based-on-the-dotnet-framework.md)   
 [Hierarchiczna organizacja zasobów do lokalizacji](../ide/hierarchical-organization-of-resources-for-localization.md)   
 [Lokalizowanie aplikacji](../ide/localizing-applications.md)   
 [Globalizowanie i lokalizowanie aplikacji](../ide/globalizing-and-localizing-applications.md)
