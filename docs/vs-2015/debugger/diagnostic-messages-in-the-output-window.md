---
title: Komunikaty diagnostyczne w Okno Dane wyjściowe | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.output
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- diagnostic messages [C#]
- System.Diagnostics.Debug class, Output window
- messages, diagnostic
- Debug.Print replacements
- diagnosis
- Output window, diagnostic messages
- System.Diagnostics.Trace class, Output window
- Trace class, diagnostic messages
- diagnostics
- debugger, Output window
- debugging [Visual Studio], diagnostic messages in Output window
- Debug class
ms.assetid: 386e9524-be17-4573-83fb-4f7c5cae0be0
caps.latest.revision: 19
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 60f8da2430e1c84af3c26be31c6de561291c8c6e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "65695296"
---
# <a name="diagnostic-messages-in-the-output-window"></a>Komunikaty diagnostyczne w oknie danych wyjściowych
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Komunikaty czasu wykonywania można zapisywać do okna danych wyjściowych przy użyciu klasy Debug lub klasy Trace, która jest częścią <xref:System.Diagnostics> biblioteki klas. Użyj klasy Debug, jeśli dane wyjściowe są tylko w debugowanej wersji programu. Użyj klasy Trace, jeśli chcesz, aby dane wyjściowe były w wersji Debug i Release.  
  
## <a name="output-methods"></a>Metody wyjściowe  
 <xref:System.Diagnostics.Trace>Klasy i <xref:System.Diagnostics.Debug> zapewniają następujące metody wyjściowe:  
  
- Różne `Write` metody, które wyprowadzają informacje wyjściowe bez przerywania wykonywania. Te metody zastępują `Debug.Print` metodę używaną w poprzednich wersjach Visual Basic.  
  
- <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=fullName> i <xref:System.Diagnostics.Trace.Assert%2A?displayProperty=fullName> metody, które przerywają wykonywanie i informacje wyjściowe w przypadku niepowodzenia określonego warunku. Domyślnie `Assert` Metoda Wyświetla informacje w oknie dialogowym. Aby uzyskać więcej informacji, zobacz [potwierdzenia w kodzie zarządzanym](../debugger/assertions-in-managed-code.md).  
  
- <xref:System.Diagnostics.Debug.Fail%2A?displayProperty=fullName>Metody i <xref:System.Diagnostics.Trace.Fail%2A?displayProperty=fullName> , które zawsze przerywają wykonywanie i informacje wyjściowe. Domyślnie `Fail` metody wyświetlają informacje w oknie dialogowym.  
  
  Oprócz programu z aplikacji okno **dane wyjściowe** może wyświetlić informacje o:  
  
- Moduły, które zostały załadowane lub zwolnione przez debuger.  
  
- Wyjątki, które są generowane.  
  
- Procesy, które zakończą działanie.  
  
- Wątki, które wykończyły działanie.  
  
## <a name="see-also"></a>Zobacz też  
 [Zabezpieczenia debugera](../debugger/debugger-security.md)   
 [Okno Dane wyjściowe](../ide/reference/output-window.md)   
 [Śledzenie i Instrumentacja aplikacji](https://msdn.microsoft.com/library/773b6fc4-9013-4322-b728-5dec7a72e743)   
 [Wprowadzenie do Instrumentacji i śledzenia](https://msdn.microsoft.com/e924e57c-33cf-4b0e-9e7f-a45d13e38f2c)   
 [Typy projektów C#, F # i Visual Basic](../debugger/debugging-preparation-csharp-f-hash-and-visual-basic-project-types.md)   
 [Debugowanie zarządzanego kodu](../debugger/debugging-managed-code.md)
