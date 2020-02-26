---
title: ResumeTracking | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
apiname:
- ResumeTracking
apilocation:
- filetracker.dll
apitype: COM
helpviewer_keywords:
- ResumeTracking
ms.assetid: d637e019-7c50-4b0a-812e-bc822001e697
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 6bb4663013a73d88ed7c2118816007705834162c
ms.sourcegitcommit: 2ae2436dc3484b9dfa10e0483afba1e5a02a52eb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/25/2020
ms.locfileid: "77578449"
---
# <a name="resumetracking"></a>ResumeTracking
Wznawia śledzenie w bieżącym kontekście.

## <a name="syntax"></a>Składnia

```cpp
HRESULT WINAPI ResumeTracking();
```

## <a name="return-value"></a>Wartość zwracana
 **Wynik HRESULT** z **pomyślnie** ustawionym bitem, jeśli śledzenie zostało wznowione. **E_FAIL** jest zwracany, jeśli nie można wznowić śledzenia, ponieważ kontekst nie jest dostępny.

## <a name="requirements"></a>Wymagania
 **Nagłówek:** *FileTracker. h*

## <a name="see-also"></a>Zobacz też
- [SuspendTracking](../msbuild/suspendtracking.md)