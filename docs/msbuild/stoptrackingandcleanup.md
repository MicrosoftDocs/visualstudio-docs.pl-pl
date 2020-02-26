---
title: StopTrackingAndCleanup | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
apiname:
- StopTrackingAndCleanup
apilocation:
- filetracker.dll
apitype: COM
helpviewer_keywords:
- StopTrackingAndCleanup
ms.assetid: 9f8c5994-2dfc-43c3-a5fb-89b2f8990429
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4a80fcde7aeab601791c033bd21effce175b2cb9
ms.sourcegitcommit: 2ae2436dc3484b9dfa10e0483afba1e5a02a52eb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/25/2020
ms.locfileid: "77579560"
---
# <a name="stoptrackingandcleanup"></a>StopTrackingAndCleanup
Powoduje zatrzymanie śledzenia i zwolnienie dowolnej pamięci używanej przez sesję śledzenia.

## <a name="syntax"></a>Składnia

```cpp
HRESULT WINAPI StopTrackingAndCleanup(void);
```

## <a name="return-value"></a>Wartość zwracana
 Zwraca wartość **HRESULT** z **pomyślnie** ustawionym bitem, jeśli śledzenie zostało zatrzymane.

## <a name="requirements"></a>Wymagania
 **Nagłówek:** *FileTracker. h*

## <a name="see-also"></a>Zobacz też
- [StartTrackingContext](../msbuild/starttrackingcontext.md)