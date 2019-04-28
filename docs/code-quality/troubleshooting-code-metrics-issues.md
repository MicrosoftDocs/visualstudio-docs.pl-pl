---
title: Rozwiązywanie problemów związanych z metrykami kodów
ms.date: 11/04/2016
ms.topic: troubleshooting
ms.assetid: f2fdb995-4888-4246-85dc-7bacadd45968
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 66655dd1e250ae16e48330eabc77610756fea367
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62820758"
---
# <a name="troubleshooting-code-metrics-issues"></a>Rozwiązywanie problemów związanych z metrykami kodów
Niektóre następujące problemy mogą występować w przypadku zbierać metryki kodu:

- [Zmiany w obliczeniach złożoności kodu programu Visual Studio 2010](#Changes_in_Visual_Studio_2010_code_complexity_calculations)

## <a name="Changes_in_Visual_Studio_2010_code_complexity_calculations"></a> Zmiany w obliczeniach złożoności kodu programu Visual Studio 2010
 Dla tej samej funkcji metryki złożoności kodu są obliczane w [!INCLUDE[vs_dev10_long](../code-quality/includes/vs_dev10_long_md.md)] może różnić się od metryki obliczana na podstawie wcześniejszych wersjach [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] w następujących sytuacjach:

- Funkcja zawiera jeden lub więcej bloki catch. W poprzednich wersjach [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)], catch bloki nie zostały uwzględnione w obliczeniach. W [!INCLUDE[vs_dev10_long](../code-quality/includes/vs_dev10_long_md.md)], złożoność każdego bloku catch zostanie dodany do złożoność funkcji.

- Funkcja zawiera instrukcję switch (Select Case w języku Visual Basic). Kompilator różnice między [!INCLUDE[vs_dev10_long](../code-quality/includes/vs_dev10_long_md.md)] i wcześniejszych wersji może generować niektóre instrukcje switch, zawierające przypadków należą do różnych kod MSIL.

## <a name="see-also"></a>Zobacz też
 [Mierzenie złożoności i poziomu łatwości konserwacji kodu zarządzanego](../code-quality/code-metrics-values.md)