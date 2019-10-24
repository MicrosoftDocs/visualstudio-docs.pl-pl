---
title: Debugowanie F# | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- Debugging [F#]
- F#, debugging
ms.assetid: 20bcd51c-2d06-4281-9a1e-ef2b91d1a779
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e7bc3934136f0966439bec2e4368488e52099602
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2019
ms.locfileid: "72738266"
---
# <a name="debugging-f"></a>Debugowanie F \#
Debugowanie F# jest podobne do debugowania dowolnego zarządzanego języka, z kilkoma wyjątkami:

- W oknie **samochody** nie są wyświetlane F# zmienne.

- Edytuj i Kontynuuj nie są obsługiwane w F#programie. Edytowanie F# kodu podczas sesji debugowania jest możliwe, ale należy je unikać. Ponieważ zmiany kodu nie są stosowane podczas sesji debugowania, edytowanie F# kodu podczas debugowania spowoduje niezgodność między kodem źródłowym i debugowanym kodem.

- Debuger nie rozpoznaje F# wyrażeń. Aby wprowadzić wyrażenie w oknie debugera lub w oknie dialogowym podczas F# debugowania, należy przetłumaczyć wyrażenie na C# składnię. F# W przypadku tłumaczenia wyrażenia C#na, pamiętaj, aby pamiętać, że C# użycie = = jako operatora porównania dla równości i F# używa jednego =.

## <a name="see-also"></a>Zobacz także
- [Debugowanie kodu zarządzanego](../debugger/debugging-managed-code.md)
