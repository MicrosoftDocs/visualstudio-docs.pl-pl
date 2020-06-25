---
title: Jak w górę lub w dół w pamięci | Microsoft Docs
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- debugger, paging up or down in memory
- memory, paging up or down
- Disassembly window, viewing memory space
- Memory window, paging up or down in memory
ms.assetid: 50b30a68-66f6-43f8-a48b-59ce12c95471
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 79216ba29047101c9b9d2c6618cae013640542b8
ms.sourcegitcommit: c076fe12e459f0dbe2cd508e1294af14cb53119f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/25/2020
ms.locfileid: "85349422"
---
# <a name="how-to-page-up-or-down-in-memory"></a>Porady: stronicowanie w górę lub w dół w pamięci

Podczas wyświetlania zawartości pamięci w oknie **pamięci** lub w oknie **demontażu** można użyć pionowego paska przewijania, aby przenieść w górę lub w dół w obszarze pamięci.

### <a name="to-page-up-or-down-in-memory"></a>Na stronę w górę lub w dół w pamięci

1. Na stronę w dół (przejdź do wyższego adresu pamięci) kliknij pionowy pasek przewijania poniżej pola przewijania.

2. Aby Page Up (przenieść na niższy adres pamięci), kliknij pionowy pasek przewijania powyżej przycisku przewijania.

   Zauważ również, że pionowy pasek przewijania działa w sposób niestandardowym. Przestrzeń adresowa nowoczesnego komputera jest bardzo duża i będzie można ją łatwo stracić, pobierając kciuk paska przewijania i przeciągając go do lokalizacji losowej. Z tego powodu kciuk jest "springloaded" i zawsze pozostaje w środku paska przewijania. W aplikacjach kodu natywnego można wyłączać się w górę lub w dół, ale nie można przewijać w dowolny sposób.

   W aplikacjach zarządzanych rozzbiór jest ograniczony do jednej funkcji i można go przewinąć w normalny sposób.

   Zobaczysz, że wyższe adresy są wyświetlane u dołu okna. Aby wyświetlić wyższy adres, należy przenieść w dół, a nie w górę.

#### <a name="to-move-up-or-down-one-instruction"></a>Aby przenieść jedną instrukcję w górę lub w dół

- Kliknij strzałkę u góry lub u dołu pionowego paska przewijania.

## <a name="see-also"></a>Zobacz też
- [Okno pamięci](../debugger/memory-windows.md)
- [Porady: korzystanie z okna dezasemblacji](../debugger/how-to-use-the-disassembly-window.md)
- [Wyświetlanie danych w debugerze](../debugger/viewing-data-in-the-debugger.md)