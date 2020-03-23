---
title: ResumeTracking | Dokumenty firmy Microsoft
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
ms.openlocfilehash: 248bb5e5e01b8209f826478e90b2c60b70922987
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "77632501"
---
# <a name="resumetracking"></a>ResumeTracking

Wznawia śledzenie w bieżącym kontekście.

## <a name="syntax"></a>Składnia

```cpp
HRESULT WINAPI ResumeTracking();
```

## <a name="return-value"></a>Wartość zwracana

 **HRESULT** z **bitem SUCCEEDED** ustawiony, jeśli śledzenie zostało wznowione. **E_FAIL** jest zwracany, jeśli śledzenie nie można wznowić, ponieważ kontekst nie był dostępny.

## <a name="requirements"></a>Wymagania

 **Nagłówek:** *FileTracker.h*

## <a name="see-also"></a>Zobacz też

- [SuspendTracking](../msbuild/suspendtracking.md)