---
title: Instrukcje zatrzymania w Visual Basic | Microsoft Docs
description: Przejrzyj instrukcję Visual Basic stop, która zapewnia programistyczną alternatywę do ustawiania punktu przerwania w programie Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- CSharp
- VB
helpviewer_keywords:
- End statements
- breakpoints, Stop statements
- debugging managed code, Stop statements vs breakpoints
- Stop statements, about Stop statements
- debugging [Visual Basic], Stop statements vs. breakpoints
ms.assetid: 4ad3fe5c-3dfb-4913-b2eb-a0b635751c18
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 4a17aafd508acd9272e8058ea7ca3ff585a8c0c8
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99904933"
---
# <a name="stop-statements-in-visual-basic"></a>Instrukcje „Stop” w języku Visual Basic

Instrukcja Visual Basic Stop zawiera programistyczną alternatywę do ustawiania punktu przerwania. Gdy debuger napotka instrukcję stop, przerywa wykonywanie programu (przejdzie do trybu przerwania). Programiści języka C# mogą osiągać ten sam efekt przy użyciu wywołania do <xref:System.Diagnostics.Debugger.Break%2A?displayProperty=nameWithType> .

Możesz ustawić lub usunąć instrukcję zatrzymania, edytując kod źródłowy. Nie można ustawiać lub czyścić instrukcji zatrzymania przy użyciu poleceń debugera, tak jak w przypadku punktu przerwania.

W przeciwieństwie do instrukcji End, instrukcja Stop nie resetuje zmiennych ani nie zwraca do trybu projektowania. Aby kontynuować działanie aplikacji, możesz wybrać pozycję Kontynuuj z menu Debuguj.

Po uruchomieniu aplikacji Visual Basic poza debugerem instrukcja Stop uruchamia debuger, jeśli jest włączone debugowanie just in Time. Jeśli debugowanie just in Time nie jest włączone, instrukcja stop zachowuje się tak, jakby była instrukcją End i kończy wykonywanie. Nie wystąpi zdarzenie QueryUnload ani Unload, dlatego należy usunąć wszystkie instrukcje zatrzymania z wersji aplikacji Visual Basic. Aby uzyskać więcej informacji, zobacz [debugowanie just in Time](just-in-time-debugging-in-visual-studio.md).

 Aby uniknąć konieczności usuwania instrukcji zatrzymania, można użyć kompilacji warunkowej:

```vb
#If DEBUG Then
   Stop
#Else
   ' Don't stop
#End If
```

Kolejną alternatywą jest użycie <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType> instrukcji zamiast instrukcji Stop. <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType>Instrukcja przerywa wykonywanie tylko wtedy, gdy określony warunek nie jest spełniony. <xref:System.Diagnostics.Debug.Assert%2A> instrukcje są usuwane automatycznie podczas tworzenia wersji wydania. Aby uzyskać więcej informacji, zobacz [potwierdzenia w kodzie zarządzanym](assertions-in-managed-code.md). Jeśli chcesz <xref:System.Diagnostics.Debug.Assert%2A> , aby instrukcja, która zawsze przerywa wykonywanie w wersji Debug, można wykonać następujące czynności:

```csharp
Debug.Assert(false);
```

```vb
Debug.Assert(False)
```

Inna alternatywą jest użycie <xref:System.Diagnostics.Debug.Fail%2A?displayProperty=nameWithType> metody:

```csharp
Debug.Fail("a clever output string goes here");
```

```vb
Debug.Fail("a clever output string goes here")
```

## <a name="see-also"></a>Zobacz też

- [Zabezpieczenia debugera](debugger-security.md)
- [Typy projektów C#, F# i Visual Basic](debugging-preparation-csharp-f-hash-and-visual-basic-project-types.md)
- [Debugowanie zarządzanego kodu](debugging-managed-code.md)
