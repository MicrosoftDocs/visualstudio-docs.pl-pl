---
title: Wysyłanie komunikatów do okna danych wyjściowych | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/08/2018
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
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
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 02bdd2c6d83e13887a8051ab4101627ba14220fa
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51724485"
---
# <a name="send-messages-to-the-output-window"></a>Wysyłanie komunikatów do okna danych wyjściowych

Można napisać komunikaty czasu wykonywania, aby **dane wyjściowe** przy użyciu okna <xref:System.Diagnostics.Debug> klasy lub <xref:System.Diagnostics.Trace> klasy, które są dostępne w ramach programu <xref:System.Diagnostics> biblioteki klas. Użyj <xref:System.Diagnostics.Debug> klasy, jeśli chcesz tylko dane wyjściowe *debugowania* wersji programu. Użyj <xref:System.Diagnostics.Trace> klasy, jeśli chcesz, aby dane wyjściowe w obu *debugowania* i *wersji* wersji.  
  
## <a name="output-methods"></a>Metod wyjścia  
 <xref:System.Diagnostics.Trace> i <xref:System.Diagnostics.Debug> klasy zapewniają następujące metody dane wyjściowe:  
  
- Różne `Write` metody, które dane wyjściowe informacji bez przerywania wykonywania. Te metody zamieniają `Debug.Print` metody używane w poprzednich wersjach programu Visual Basic.  
  
- <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=fullName> i <xref:System.Diagnostics.Trace.Assert%2A?displayProperty=fullName> metody, które przerwanie wykonywania i danych wyjściowych informacji określony warunek zakończy się niepowodzeniem. Domyślnie `Assert` metoda Wyświetla informacje w oknie dialogowym. Aby uzyskać więcej informacji, zobacz [potwierdzenia w zarządzanym kodzie](../debugger/assertions-in-managed-code.md).  
  
- <xref:System.Diagnostics.Debug.Fail%2A?displayProperty=fullName> i <xref:System.Diagnostics.Trace.Fail%2A?displayProperty=fullName> metody, które zawsze przerwanie wykonywania i danych wyjściowych informacji. Domyślnie `Fail` metody powodują wyświetlenie informacji w oknie dialogowym.  
  
**Dane wyjściowe** okna można również wyświetlić informacje o:  
  
- Modułów debuger został załadowany lub zwolnione.  
  
- Wyjątki, które są zgłaszane.  
  
- Procesy, które wyjść.  
  
- Wątki, które wyjść.  
  
## <a name="see-also"></a>Zobacz także  
 [Zabezpieczenia debugera](../debugger/debugger-security.md)   
 [Okno danych wyjściowych](../ide/reference/output-window.md)   
 [Śledzenie i instrumentacji aplikacji](/dotnet/framework/debug-trace-profile/tracing-and-instrumenting-applications)  
 [C#, F#i typów projektów języka Visual Basic](../debugger/debugging-preparation-csharp-f-hash-and-visual-basic-project-types.md)   
 [Debugowanie zarządzanego kodu](../debugger/debugging-managed-code.md)
