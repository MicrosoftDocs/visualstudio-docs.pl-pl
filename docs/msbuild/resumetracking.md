---
title: ResumeTracking | Dokumentacja firmy Microsoft
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
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0e2ff32a4eb2218a8b3d09188c787156e484147f
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/21/2019
ms.locfileid: "56596402"
---
# <a name="resumetracking"></a>ResumeTracking
Wznawia śledzenia w bieżącym kontekście.

## <a name="syntax"></a>Składnia

```cpp
HRESULT WINAPI ResumeTracking();
```

## <a name="return-value"></a>Wartość zwracana
 **HRESULT** z **Powodzenie** bitu, jeśli śledzenie zostało wznowione. **E_FAIL** jest zwracany, jeśli nie można wznowić śledzenia, ponieważ kontekst nie jest dostępna.

## <a name="requirements"></a>Wymagania
 **Nagłówek:** *FileTracker.h*

## <a name="see-also"></a>Zobacz także
- [SuspendTracking](../msbuild/suspendtracking.md)