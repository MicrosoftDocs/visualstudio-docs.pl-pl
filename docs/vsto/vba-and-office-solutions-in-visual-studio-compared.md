---
title: Język VBA i rozwiązania pakietu Office w programie Visual Studio
description: Dowiedz się więcej o różnicach między programem Microsoft Visual Basic for Applications (VBA) i rozwiązaniami Microsoft Office w programie Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- VBA code, managed code extensions
- managed code extensions [Office development in Visual Studio], VBA compared to
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: a07711fd854bd0dc035cab776f713701d5d85200
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99838116"
---
# <a name="vba-and-office-solutions-in-visual-studio-compared"></a>Język VBA i rozwiązania pakietu Office w programie Visual Studio
  Program Microsoft Visual Basic for Applications (VBA) korzysta z niezarządzanego kodu, który jest ściśle zintegrowany z aplikacjami pakietu Office. Projekty Microsoft Office utworzone za pomocą programu Visual Studio umożliwiają korzystanie z narzędzi do projektowania .NET Framework i programu Visual Studio.

 Aby uzyskać informacje na temat typów rozwiązań biurowych, które można utworzyć przy użyciu programu Visual Studio, zobacz [Omówienie tworzenia rozwiązań pakietu office &#40;narzędzi VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md).

## <a name="comparison"></a>Porównanie
 Poniższa tabela zawiera podstawowe porównanie rozwiązań w języku VBA i rozwiązań pakietu Office w programie Visual Studio.

|Rozwiązania VBA|Rozwiązania pakietu Office w programie Visual Studio|
|-------------------|---------------------------------------|
|Używa kodu, który jest połączony z określonym dokumentem i utrwalał go.|Używa kodu, który jest przechowywany niezależnie od dokumentu (dla dostosowań na poziomie dokumentu) lub w zestawie, który jest ładowany przez aplikację (dla dodatków VSTO).|
|Współpracuje z modelami obiektów pakietu Office i interfejsami API języka VBA.|Zapewnia dostęp zarówno do modeli obiektów pakietu Office, jak i [!INCLUDE[dnprdnshort](../sharepoint/includes/dnprdnshort-md.md)] interfejsów API.|
|Zaprojektowana na potrzeby rejestrowania makr i uproszczonego środowiska deweloperskiego.|Zaprojektowana pod kątem bezpieczeństwa, łatwiejszej konserwacji kodu i możliwości korzystania z pełnego zintegrowanego środowiska programistycznego (IDE) programu Visual Studio.|
|Dobrze sprawdza się w przypadku rozwiązań, które korzystają z ścisłej integracji z aplikacjami pakietu Office.|Dobrze sprawdza się w przypadku rozwiązań, które korzystają z pełnych zasobów programu Visual Studio i [!INCLUDE[dnprdnshort](../sharepoint/includes/dnprdnshort-md.md)] .|
|Ma ograniczenia dotyczące przedsiębiorstwa, szczególnie w zakresie zabezpieczeń i wdrażania.|Przeznaczone do użycia w przedsiębiorstwie.|

 Niektóre rzeczy są nadal łatwiejsze w użyciu języka VBA. W odniesieniu do programu można nadal używać języka VBA dla:

- Niestandardowe funkcje arkusza.

- Rejestrowanie makr.

## <a name="combine-vba-solutions-and-office-solutions-created-by-using-visual-studio"></a>Łączenie rozwiązań VBA i rozwiązań pakietu Office utworzonych przy użyciu programu Visual Studio
 Możesz wywołać kod VBA z rozwiązań pakietu Office utworzonych przy użyciu programu Visual Studio, a także wywołać kod w rozwiązaniach pakietu Office utworzonych przy użyciu programu Visual Studio z języka VBA. Konkretna technika różni się w zależności od tego, czy rozwiązanie pakietu Office jest dodatkiem narzędzia VSTO, czy też dostosowaniu na poziomie dokumentu. Aby uzyskać więcej informacji, zobacz [Wywoływanie kodu w dodatkach VSTO z innych rozwiązań pakietu Office](../vsto/calling-code-in-vsto-add-ins-from-other-office-solutions.md) i [łączenie języka VBA i dostosowań na poziomie dokumentu](../vsto/combining-vba-and-document-level-customizations.md).

## <a name="see-also"></a>Zobacz też
- [Omówienie programowania rozwiązań dla pakietu Office &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md)
- [Wywoływanie kodu w dodatkach VSTO z innych rozwiązań pakietu Office](../vsto/calling-code-in-vsto-add-ins-from-other-office-solutions.md)
- [Łączenie języka VBA i dostosowań na poziomie dokumentu](../vsto/combining-vba-and-document-level-customizations.md)
- [Architektura dostosowań na poziomie dokumentu](../vsto/architecture-of-document-level-customizations.md)
- [Architektura dodatków narzędzi VSTO](../vsto/architecture-of-vsto-add-ins.md)
- [Zabezpieczanie rozwiązań pakietu Office](../vsto/securing-office-solutions.md)
- [Wprowadzenie &#40;Programowanie Office w programie Visual Studio&#41;](../vsto/getting-started-office-development-in-visual-studio.md)
