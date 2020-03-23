---
title: WstrzymanieTracking | Dokumenty firmy Microsoft
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
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 950c6a07a46f7f4b970912e576257a577021367e
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "77632017"
---
# <a name="suspendtracking"></a>SuspendTracking

Zawiesza śledzenie w bieżącym kontekście.

## <a name="syntax"></a>Składnia

```cpp
HRESULT WINAPI SuspendTracking(void);
```

## <a name="return-value"></a>Wartość zwracana

 **HRESULT** z **bitem SUCCEEDED** ustawiony, jeśli śledzenie zostało zawieszone.

## <a name="requirements"></a>Wymagania

 **Nagłówek:** *FileTracker.h*

## <a name="see-also"></a>Zobacz też

- [ResumeTracking](../msbuild/resumetracking.md)