---
title: Rozwiązywanie problemów z metrykami kodu | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-test
ms.topic: troubleshooting
ms.assetid: f2fdb995-4888-4246-85dc-7bacadd45968
caps.latest.revision: 6
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 3eda4127e046c7676525f1755f148663f58ec9b4
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "72672080"
---
# <a name="troubleshooting-code-metrics-issues"></a>Rozwiązywanie problemów związanych z metrykami kodów
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Podczas zbierania metryk kodu mogą wystąpić następujące problemy:

- [Zmiany w obliczeniach złożoności kodu w programie Visual Studio 2010](#Changes_in_Visual_Studio_2010_code_complexity_calculations)

## <a name="changes-in-visual-studio-2010-code-complexity-calculations"></a><a name="Changes_in_Visual_Studio_2010_code_complexity_calculations"></a> Zmiany w obliczeniach złożoności kodu w programie Visual Studio 2010

Dla tej samej funkcji Metryka złożoności kodu obliczana w programie [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)] może różnić się od metryki obliczonej przez wcześniejsze wersje programu [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] w następujących sytuacjach:

- Funkcja zawiera jeden lub więcej bloków catch. W poprzednich wersjach programu [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] bloki catch nie zostały uwzględnione w obliczeniach. W programie [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)] złożoność każdego bloku catch jest dodawana do złożoności funkcji.

- Funkcja zawiera przełącznik (Wybieranie wielkości liter w języku VB). Różnice kompilatora między programem [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)] i wcześniejszymi wersjami mogą generować różne kody MSIL dla niektórych instrukcji switch, które zawierają przypadki przechodzenia między elementami.

## <a name="see-also"></a>Zobacz też

- [Mierzenie złożoności i łatwości konserwacji zarządzanego kodu](../code-quality/measuring-complexity-and-maintainability-of-managed-code.md)
