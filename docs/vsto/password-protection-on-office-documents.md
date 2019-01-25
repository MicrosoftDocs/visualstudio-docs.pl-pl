---
title: Ochrona za pomocą hasła w dokumentach pakietu Office
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- permissions [Office development in Visual Studio]
- workbooks [Office development in Visual Studio], restricted permissions
- passwords [Office development in Visual Studio], document protections
- documents [Office development in Visual Studio], restricted permissions
- Office documents [Office development in Visual Studio, restricted permissions
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 062196206d881ebb5a10f4bd7b14d892dbbbe0e9
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2019
ms.locfileid: "54872212"
---
# <a name="password-protection-on-office-documents"></a>Ochrona za pomocą hasła w dokumentach pakietu Office
  Istnieje możliwość ustawić hasło dla dokumentów pakietu Microsoft Office Word i skoroszytów programu Microsoft Office Excel, tak aby nie było otwierane przez osobę, która nie zna hasło. Ta opcja jest nazywany **hasło podczas otwierania**.  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
 Można tworzyć projektów na poziomie dokumentu przy użyciu istniejących dokumentów i skoroszyty, które mają **hasło podczas otwierania** włączone. Zachowanie w programie Visual Studio różni się dla dokumentów Word i Excel, które mają **hasło podczas otwierania** włączone.  
  
 Aby uzyskać informacje na temat włączania **hasło podczas otwierania**, należy zajrzeć do pomocy w programie Word lub Excel.  
  
## <a name="behavior-of-excel-and-word"></a>Działanie programów Excel i Word  
 Za każdym razem, gdy otwierania skoroszytu programu Excel w programie Visual Studio, który ma **hasło podczas otwierania** włączona, program Excel wyświetli monit o podanie hasła. Podczas kompilowania rozwiązania użytkownik jest monitowany o podanie hasła ponownie, ponieważ dokument jest otwarty podczas kompilacji.  
  
 Przy pierwszym otwarciu dokumentu programu Word w programie Visual Studio, który ma **hasło podczas otwierania** włączony, użytkownik jest monitowany o podanie hasła. Po wprowadzeniu hasła, **hasło podczas otwierania** zostanie usunięty z dokumentu i otwieranie dokumentu nie jest już konieczne będzie hasło. Jeśli dokument ma w swoim rozwiązaniu należy wymagać hasła przed otwarciem, należy włączyć **hasło podczas otwierania** po ostatnim kompilacji, a przed wdrożeniem rozwiązania.  
  
## <a name="see-also"></a>Zobacz także  
 [Ochrona dokumentów w rozwiązaniach na poziomie dokumentu](../vsto/document-protection-in-document-level-solutions.md)   
 [Zarządzanie prawami do informacji i przegląd rozszerzeń kodu zarządzanego](../vsto/information-rights-management-and-managed-code-extensions-overview.md)   
 [Instrukcje: Zezwalanie kodu do uruchamiania w tle dokumentów z ograniczonymi uprawnieniami](../vsto/how-to-permit-code-to-run-behind-documents-with-restricted-permissions.md)   
 [Projektowanie i tworzenie rozwiązań pakietu Office](../vsto/designing-and-creating-office-solutions.md)  
