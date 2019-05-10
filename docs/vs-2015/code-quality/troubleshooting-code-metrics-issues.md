---
title: Rozwiązywanie problemów z kodem metryki | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: troubleshooting
ms.assetid: f2fdb995-4888-4246-85dc-7bacadd45968
caps.latest.revision: 6
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 1567715a8f944eb10c2728caa9fc1edd43beda8e
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62580599"
---
# <a name="troubleshooting-code-metrics-issues"></a>Rozwiązywanie problemów związanych z metrykami kodów
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Niektóre następujące problemy mogą występować w przypadku zbierać metryki kodu:  
  
- [Zmiany w obliczeniach złożoności kodu programu Visual Studio 2010](#Changes_in_Visual_Studio_2010_code_complexity_calculations)  
  
## <a name="Changes_in_Visual_Studio_2010_code_complexity_calculations"></a> Zmiany w obliczeniach złożoności kodu programu Visual Studio 2010  
 Dla tej samej funkcji metryki złożoności kodu są obliczane w [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)] może różnić się od metryki obliczana na podstawie wcześniejszych wersjach [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] w następujących sytuacjach:  
  
- Funkcja zawiera jeden lub więcej bloki catch. W poprzednich wersjach [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)], catch bloki nie zostały uwzględnione w obliczeniach. W [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)], złożoność każdego bloku catch zostanie dodany do złożoność funkcji.  
  
- Funkcja zawiera instrukcję switch (Select Case w języku Visual Basic). Kompilator różnice między [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)] i wcześniejszych wersji może generować niektóre instrukcje switch, zawierające przypadków należą do różnych kod MSIL.  
  
## <a name="see-also"></a>Zobacz też  
 [Mierzenie złożoności i poziomu łatwości konserwacji kodu zarządzanego](../code-quality/measuring-complexity-and-maintainability-of-managed-code.md)
