---
title: Nie można zmienić wartości, okno dialogowe | Dokumentacja firmy Microsoft
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 5fd6b184b72acc2ecd08123160a512e5473e6611
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53966550"
---
# <a name="cannot-change-value-dialog-box"></a>Nie można zmienić wartości — okno dialogowe
## <a name="error"></a>Błąd  
 `The value of this variable cannot be changed` &#124;`The name` *nazwa* `does not exist in the current context` &#124; *różne inne komunikaty*  
  
 To okno komunikatu pojawia się podczas próby zmiany zawartości zmiennej na niedozwoloną wartość okna debugera (windows automatyczne, wyrażenie kontrolne lub lokalne) lub okna dialogowego QuickWatch. Na przykład Jeśli spróbujesz ustawić wartość zmiennej liczby całkowitej na ciąg znaków, pojawi się to okno komunikatu.  
  
## <a name="solution"></a>Rozwiązanie  
 Upewnij się, dane wejściowe, można wpisać w oknie debugera lub okno dialogowe QuickWatch reprezentuje dozwoloną wartością dla zmiennej, którą chcesz ustawić.  
  
## <a name="see-also"></a>Zobacz też  
 [Wyrażenia w debugerze](../debugger/expressions-in-the-debugger.md)