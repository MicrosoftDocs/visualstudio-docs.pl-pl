---
title: Ustaw radix — polecenie | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- debug.setradix
helpviewer_keywords:
- Set Radix command
- Debug.SetRadix command
ms.assetid: 6ffd1554-7530-4da4-b5f5-e276a5034f3b
caps.latest.revision: 20
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: bee6368931dc47b78186ec870039ab292960fa77
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "68163322"
---
# <a name="set-radix-command"></a>Ustaw Radix — Polecenie
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Ustawia lub zwraca base numeryczne, używany do wyświetlania wartości całkowitych.  
  
## <a name="syntax"></a>Składnia  
  
```  
Debug.SetRadix [10 | 16 | hex | dec]  
```  
  
## <a name="arguments"></a>Argumenty  
 `10` lub `16` lub `hex` lub `dec`  
 Opcjonalny. Wskazuje dziesiętne (10 lub gru) lub liczba szesnastkowa (16 lub szesnastkowych). Jeśli argument jest pominięty, zwracany jest bieżąca wartość podstawy.  
  
## <a name="example"></a>Przykład  
 W tym przykładzie środowiska, aby wyświetlić wartości całkowite w formacie szesnastkowym.  
  
```  
>Debug.SetRadix hex  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Visual Studio Commands](../../ide/reference/visual-studio-commands.md)   
 [Okno polecenia](../../ide/reference/command-window.md)   
 [Znajdź/Command — pole](../../ide/find-command-box.md)   
 [Visual Studio — aliasy poleceń](../../ide/reference/visual-studio-command-aliases.md)
