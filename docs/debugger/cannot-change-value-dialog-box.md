---
title: Nie można zmienić wartości — okno dialogowe | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.debug.variables.failededit
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- Cannot Change Value dialog box
- variables [debugger], editing
ms.assetid: 19e930c2-5fbf-4c83-aae8-a1dc3f8fcae8
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 97f057edefefd590c37b49d709ecf8a6e029b905
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "72745740"
---
# <a name="cannot-change-value-dialog-box"></a>Nie można zmienić wartości — okno dialogowe
## <a name="error"></a>Błąd
 `The value of this variable cannot be changed``The name` *Nazwa* &#124; `does not exist in the current context` &#124; *różnych innych komunikatów*

 To okno komunikatu pojawia się, gdy użytkownik próbuje zmienić zawartość zmiennej do niedozwolonej wartości w oknie debugera (autostarty, czujka lub lokalnych oknach) lub w oknie dialogowym QuickWatch. Na przykład, jeśli spróbujesz ustawić wartość zmiennej liczb całkowitych na ciąg znaków, zostanie wyświetlone okno komunikatu.

## <a name="solution"></a>Rozwiązanie
 Upewnij się, że dane wejściowe wpisane do okna debugera lub okna dialogowego QuickWatch reprezentują wartość prawną dla zmiennej, którą próbujesz ustawić.

## <a name="see-also"></a>Zobacz też

- [Wyrażenia w debugerze](../debugger/expressions-in-the-debugger.md)