---
title: Rozwiązywanie problemów z metrykami kodu | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-test
ms.topic: troubleshooting
ms.assetid: f2fdb995-4888-4246-85dc-7bacadd45968
caps.latest.revision: 6
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 5a02dbc4840729d5004b0815175f626fc8760711
ms.sourcegitcommit: 59e5758036223ee866f3de5e3c0ab2b6dbae97b6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/23/2019
ms.locfileid: "68416967"
---
# <a name="troubleshooting-code-metrics-issues"></a>Rozwiązywanie problemów związanych z metrykami kodów
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Podczas zbierania metryk kodu mogą wystąpić następujące problemy:

- [Zmiany w obliczeniach złożoności kodu w programie Visual Studio 2010](#Changes_in_Visual_Studio_2010_code_complexity_calculations)

## <a name="Changes_in_Visual_Studio_2010_code_complexity_calculations"></a>Zmiany w obliczeniach złożoności kodu w programie Visual Studio 2010

Dla tej samej funkcji Metryka złożoności kodu obliczana w [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)] programie może różnić się od metryki obliczonej przez wcześniejsze [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] wersje programu w następujących sytuacjach:

- Funkcja zawiera jeden lub więcej bloków catch. W poprzednich wersjach programu [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)]bloki catch nie zostały uwzględnione w obliczeniach. W [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)]programie złożoność każdego bloku catch jest dodawana do złożoności funkcji.

- Funkcja zawiera przełącznik (Wybieranie wielkości liter w języku VB). Różnice kompilatora między [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)] programem i wcześniejszymi wersjami mogą generować różne kody MSIL dla niektórych instrukcji switch, które zawierają przypadki przechodzenia między elementami.

## <a name="see-also"></a>Zobacz także

- [Mierzenie złożoności i poziomu łatwości konserwacji kodu zarządzanego](../code-quality/measuring-complexity-and-maintainability-of-managed-code.md)
