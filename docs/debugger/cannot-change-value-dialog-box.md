---
title: Nie można zmienić wartości — okno dialogowe | Microsoft Docs
description: Sprawdź okno dialogowe nie można zmienić wartości, które pojawia się w programie Visual Studio, jeśli spróbujesz zmienić zmienną na niedozwoloną wartość w oknie debugera lub QuickWatch.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 3dfedc12a1634e6f804c0cb3a9fceee9e9d43216
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99857893"
---
# <a name="cannot-change-value-dialog-box"></a>Nie można zmienić wartości — okno dialogowe
## <a name="error"></a>Błąd
 `The value of this variable cannot be changed``The name` *Nazwa* &#124; `does not exist in the current context` &#124; *różnych innych komunikatów*

 To okno komunikatu pojawia się, gdy użytkownik próbuje zmienić zawartość zmiennej do niedozwolonej wartości w oknie debugera (autostarty, czujka lub lokalnych oknach) lub w oknie dialogowym QuickWatch. Na przykład, jeśli spróbujesz ustawić wartość zmiennej liczb całkowitych na ciąg znaków, zostanie wyświetlone okno komunikatu.

## <a name="solution"></a>Rozwiązanie
 Upewnij się, że dane wejściowe wpisane do okna debugera lub okna dialogowego QuickWatch reprezentują wartość prawną dla zmiennej, którą próbujesz ustawić.

## <a name="see-also"></a>Zobacz też

- [Wyrażenia w debugerze](../debugger/expressions-in-the-debugger.md)