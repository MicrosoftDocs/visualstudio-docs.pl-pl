---
title: Stronicowanie w górę lub w dół w pamięci | Microsoft Docs
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
ms.openlocfilehash: ee4e4e2037e39df7ce343143ff64235f1de0364f
ms.sourcegitcommit: 062615c058d2ff44751e8d0c704ccfa3c5543469
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/22/2020
ms.locfileid: "90852051"
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

## <a name="see-also"></a>Zobacz także
- [Okno pamięci](../debugger/memory-windows.md)
- [Porady: korzystanie z okna dezasemblacji](../debugger/how-to-use-the-disassembly-window.md)
- [Wyświetlanie danych w debugerze](../debugger/viewing-data-in-the-debugger.md)