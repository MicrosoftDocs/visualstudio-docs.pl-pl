---
title: Rozwiązywanie problemów z metrykami kodu | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: troubleshooting
ms.assetid: f2fdb995-4888-4246-85dc-7bacadd45968
caps.latest.revision: 6
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: b4d374a2737e2ce8892304b615bebcf99d9c60ad
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72672453"
---
# <a name="troubleshooting-code-metrics-issues"></a>Rozwiązywanie problemów związanych z metrykami kodów
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Podczas zbierania metryk kodu mogą wystąpić następujące problemy:

- [Zmiany w obliczeniach złożoności kodu w programie Visual Studio 2010](#Changes_in_Visual_Studio_2010_code_complexity_calculations)

## <a name="Changes_in_Visual_Studio_2010_code_complexity_calculations"></a>Zmiany w obliczeniach złożoności kodu w programie Visual Studio 2010
 Dla tej samej funkcji Metryka złożoności kodu obliczana w [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)] może być różna od metryki obliczonej przez wcześniejsze wersje [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] w następujących sytuacjach:

- Funkcja zawiera jeden lub więcej bloków catch. W poprzednich wersjach [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] bloki catch nie zostały uwzględnione w obliczeniach. W [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)] złożoność każdego bloku catch jest dodawana do złożoności funkcji.

- Funkcja zawiera przełącznik (Wybieranie wielkości liter w języku VB). Różnice kompilatora między [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)] i wcześniejszymi wersjami mogą generować różne kody MSIL dla niektórych instrukcji switch, które zawierają przypadki przechodzenia między elementami.

## <a name="see-also"></a>Zobacz też
 [Mierzenie złożoności i poziomu łatwości konserwacji kodu zarządzanego](../code-quality/measuring-complexity-and-maintainability-of-managed-code.md)
