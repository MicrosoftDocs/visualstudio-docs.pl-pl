---
title: SuspendTracking | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
apiname:
- SuspendTracking
apilocation:
- filetracker.dll
apitype: COM
helpviewer_keywords:
- SuspendTracking
ms.assetid: f5e06e5a-8083-444c-99c1-07ba834226b5
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: cc2a8b3dc2f5940c64be870df452b088dce7bc0e
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62939009"
---
# <a name="suspendtracking"></a>SuspendTracking
Wstrzymuje śledzenia w bieżącym kontekście.

## <a name="syntax"></a>Składnia

```cpp
HRESULT WINAPI SuspendTracking(void);
```

## <a name="return-value"></a>Wartość zwracana
 **HRESULT** z **Powodzenie** bitu, jeśli śledzenie zostało wstrzymane.

## <a name="requirements"></a>Wymagania
 **Nagłówek:** *FileTracker.h*

## <a name="see-also"></a>Zobacz także
- [ResumeTracking](../msbuild/resumetracking.md)