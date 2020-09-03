---
title: 'Debugowanie F # | Microsoft Docs'
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "72738266"
---
# <a name="debugging-f"></a>Debugowanie F\#
Debugowanie F # jest podobne do debugowania dowolnego zarządzanego języka z kilkoma wyjątkami:

- W oknie **samochody** nie są wyświetlane zmienne F #.

- Edytuj i Kontynuuj nie jest obsługiwane dla języka F #. Edytowanie kodu F # podczas sesji debugowania jest możliwe, ale należy je unikać. Ponieważ zmiany kodu nie są stosowane podczas sesji debugowania, edytowanie kodu F # podczas debugowania spowoduje niezgodność między kodem źródłowym i debugowanym kodem.

- Debuger nie rozpoznaje wyrażeń języka F #. Aby wprowadzić wyrażenie w oknie debugera lub w oknie dialogowym podczas debugowania F #, należy przetłumaczyć wyrażenie na składnię języka C#. W przypadku tłumaczenia wyrażenia języka F # do języka C# Pamiętaj, aby pamiętać, że C# używa = = jako operatora porównania dla równości i że F # używa jednego =.

## <a name="see-also"></a>Zobacz też
- [Debugowanie zarządzanego kodu](../debugger/debugging-managed-code.md)
