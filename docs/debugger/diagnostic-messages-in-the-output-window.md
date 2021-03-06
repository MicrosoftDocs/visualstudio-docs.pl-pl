---
title: Wyślij komunikaty do okna dane wyjściowe | Microsoft Docs
description: Zapisuj komunikaty czasu wykonywania w oknie danych wyjściowych w programie Visual Studio przy użyciu klasy Debug lub klasy Trace, która jest częścią biblioteki klas System. Diagnostics.
ms.custom: SEO-VS-2020
ms.date: 11/08/2018
ms.topic: how-to
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: b61d0c6bc89f8be2680930411e0b9109fdeec473
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99872058"
---
# <a name="send-messages-to-the-output-window"></a>Wysyłanie komunikatów do okna danych wyjściowych

Komunikaty czasu wykonywania można zapisywać do okna **danych wyjściowych** przy użyciu <xref:System.Diagnostics.Debug> klasy lub <xref:System.Diagnostics.Trace> klasy, która jest częścią <xref:System.Diagnostics> biblioteki klas. Użyj <xref:System.Diagnostics.Debug> klasy, jeśli chcesz, aby dane wyjściowe były tylko w *debugowanej* wersji programu. Użyj <xref:System.Diagnostics.Trace> klasy, jeśli chcesz, aby dane wyjściowe były w wersji *Debug* i *Release* .

## <a name="output-methods"></a>Metody wyjściowe
 <xref:System.Diagnostics.Trace>Klasy i <xref:System.Diagnostics.Debug> zapewniają następujące metody wyjściowe:

- Różne `Write` metody, które wyprowadzają informacje wyjściowe bez przerywania wykonywania. Te metody zastępują `Debug.Print` metodę używaną w poprzednich wersjach Visual Basic.

- <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=fullName> i <xref:System.Diagnostics.Trace.Assert%2A?displayProperty=fullName> metody, które przerywają wykonywanie i informacje wyjściowe, jeśli określony warunek zakończy się niepowodzeniem. Domyślnie `Assert` Metoda Wyświetla informacje w oknie dialogowym. Aby uzyskać więcej informacji, zobacz [potwierdzenia w kodzie zarządzanym](../debugger/assertions-in-managed-code.md).

- <xref:System.Diagnostics.Debug.Fail%2A?displayProperty=fullName>Metody i <xref:System.Diagnostics.Trace.Fail%2A?displayProperty=fullName> , które zawsze przerywają wykonywanie i informacje wyjściowe. Domyślnie `Fail` metody wyświetlają informacje w oknie dialogowym.

Okno **dane wyjściowe** może również zawierać informacje o:

- Moduły, które zostały załadowane lub zwolnione przez debuger.

- Wyjątki, które są generowane.

- Procesy, które zakończą działanie.

- Wątki, które wykończyły działanie.

## <a name="see-also"></a>Zobacz też
- [Zabezpieczenia debugera](../debugger/debugger-security.md)
- [Okno wyniku](../ide/reference/output-window.md)
- [Śledzenie i instrumentacja aplikacji](/dotnet/framework/debug-trace-profile/tracing-and-instrumenting-applications)
- [Typy projektów C#, F # i Visual Basic](../debugger/debugging-preparation-csharp-f-hash-and-visual-basic-project-types.md)
- [Debugowanie kodu zarządzanego](../debugger/debugging-managed-code.md)
