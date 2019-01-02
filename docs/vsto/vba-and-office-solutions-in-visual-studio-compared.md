---
title: Rozwiązania VBA i pakietu Office w Visual Studio
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- VBA code, managed code extensions
- managed code extensions [Office development in Visual Studio], VBA compared to
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 09c5fdeb37fa09595cdfda99aba06b9546c5f696
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53820086"
---
# <a name="vba-and-office-solutions-in-visual-studio-compared"></a>Rozwiązania VBA i pakietu Office w Visual Studio
  Microsoft Visual Basic for Applications (VBA) używa kod niezarządzany, który jest ściśle zintegrowany z aplikacjami pakietu Office. Projekty programu Microsoft Office utworzone przy użyciu programu Visual Studio umożliwiają korzystanie z zalet platformy .NET Framework i narzędzi projektowania programu Visual Studio.  
  
 Aby uzyskać informacji na temat typów rozwiązań dla pakietu Office, można utworzyć przy użyciu programu Visual Studio, zobacz [rozwój rozwiązań Office ― omówienie &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md).  
  
## <a name="comparison"></a>Porównanie  
 Poniższa tabela zawiera podstawowe porównanie rozwiązań VBA i rozwiązania pakietu Office w programie Visual Studio.  
  
|Rozwiązania VBA|Rozwiązań pakietu Office w Visual Studio|  
|-------------------|---------------------------------------|  
|Używa kodu, który jest połączony i utrwalane z określonym dokumentem.|Używa kodu, które były przechowywane osobno od dokumentu (dla dostosowania na poziomie dokumentu), lub w zestawie, który jest ładowany przez aplikację (dla dodatków narzędzi VSTO).|  
|Współdziałanie z usługami modele obiektów pakietu Office i interfejsy API języka VBA.|Zapewnia dostęp do obu modele obiektów pakietu Office i [!INCLUDE[dnprdnshort](../sharepoint/includes/dnprdnshort-md.md)] interfejsów API.|  
|Zaprojektowana na potrzeby rejestrowanie makra i środowiska deweloperów uproszczone.|Zaprojektowana na potrzeby zabezpieczeń, łatwiejsze utrzymanie kodu i możliwość używania pełnej programu Visual Studio zintegrowane środowisko programistyczne (IDE).|  
|Działa dobrze dla rozwiązania, które korzystają ze ścisłej integracji z aplikacjami pakietu Office.|Działa dobrze dla rozwiązania, które korzystają z zasobów stanowych programu Visual Studio i [!INCLUDE[dnprdnshort](../sharepoint/includes/dnprdnshort-md.md)].|  
|Ma ograniczenia w organizacji, szczególnie w zakresie zabezpieczeń i wdrażania.|Przeznaczony do użytku w przedsiębiorstwie.|  
  
 Niektóre elementy są nadal prostsze szybko za pomocą języka VBA. Ściślej mówiąc możesz chcieć kontynuować korzystanie z języka VBA do:  
  
-   Funkcje niestandardowe arkusza.  
  
-   Rejestrowanie makra.  
  
## <a name="combine-vba-solutions-and-office-solutions-created-by-using-visual-studio"></a>Łączenie VBA rozwiązań i rozwiązań pakietu Office utworzonych przy użyciu programu Visual Studio  
 Możesz wywołać kod VBA z rozwiązań pakietu Office utworzonych przy użyciu programu Visual Studio, a kod można również wywołać w rozwiązaniach pakietu Office utworzone przy użyciu programu Visual Studio z języka VBA. Technika określonych różnią się zależnie od tego, czy rozwiązania pakietu Office jest dodatku narzędzi VSTO dla programów lub dostosowywania poziomie dokumentu. Aby uzyskać więcej informacji, zobacz [wywoływanie kodu w dodatkach VSTO z innych rozwiązań pakietu Office](../vsto/calling-code-in-vsto-add-ins-from-other-office-solutions.md) i [łączenie VBA i dostosowywanie na poziomie dokumentu](../vsto/combining-vba-and-document-level-customizations.md).  
  
## <a name="see-also"></a>Zobacz także  
 [Rozwój rozwiązań Office ― omówienie &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md)   
 [Wywoływanie kodu w dodatkach VSTO z innych rozwiązań pakietu Office](../vsto/calling-code-in-vsto-add-ins-from-other-office-solutions.md)   
 [Łączenie VBA i dostosowywanie na poziomie dokumentu](../vsto/combining-vba-and-document-level-customizations.md)   
 [Architektura dostosowywania na poziomie dokumentu](../vsto/architecture-of-document-level-customizations.md)   
 [Architektura dodatków narzędzi VSTO](../vsto/architecture-of-vsto-add-ins.md)   
 [Zabezpieczanie rozwiązań pakietu Office](../vsto/securing-office-solutions.md)   
 [Rozpoczynanie pracy &#40;programowanie Office w Visual Studio&#41;](../vsto/getting-started-office-development-in-visual-studio.md)  
