---
title: 'Debugowanie F # | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- Debugging [F#]
- F#, debugging
ms.assetid: 20bcd51c-2d06-4281-9a1e-ef2b91d1a779
caps.latest.revision: 7
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 51a8e43268718421a90d051f0d4d9b6afa96980e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68156688"
---
# <a name="debugging-f"></a>Debugowanie F\#

[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Debugowanie F # jest podobne do debugowania dowolnego zarządzanego języka z kilkoma wyjątkami:

- W oknie **samochody** nie są wyświetlane zmienne F #.

- Edytuj i Kontynuuj nie jest obsługiwane dla języka F #. Edytowanie kodu F # podczas sesji debugowania jest możliwe, ale należy je unikać. Ponieważ zmiany kodu nie są stosowane podczas sesji debugowania, edytowanie kodu F # podczas debugowania spowoduje niezgodność między kodem źródłowym i debugowanym kodem.

- Debuger nie rozpoznaje wyrażeń języka F #. Aby wprowadzić wyrażenie w oknie debugera lub w oknie dialogowym podczas debugowania F #, należy przetłumaczyć wyrażenie na składnię języka C#. W przypadku tłumaczenia wyrażenia języka F # do języka C# Pamiętaj, aby pamiętać, że C# używa = = jako operatora porównania dla równości i że F # używa jednego =.

## <a name="see-also"></a>Zobacz też

- [Debugowanie zarządzanego kodu](../debugger/debugging-managed-code.md)
