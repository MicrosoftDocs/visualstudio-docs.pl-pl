---
title: SuspendTracking | Microsoft Docs
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
ms.openlocfilehash: d48c29b9dcca477c5a5470c443be08d5060b413d
ms.sourcegitcommit: 2ae2436dc3484b9dfa10e0483afba1e5a02a52eb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/25/2020
ms.locfileid: "77578115"
---
# <a name="suspendtracking"></a>SuspendTracking
Wstrzymuje śledzenie w bieżącym kontekście.

## <a name="syntax"></a>Składnia

```cpp
HRESULT WINAPI SuspendTracking(void);
```

## <a name="return-value"></a>Wartość zwracana
 **Wynik HRESULT** z **pomyślnym** ustawieniem bitu, jeśli śledzenie zostało zawieszone.

## <a name="requirements"></a>Wymagania
 **Nagłówek:** *FileTracker. h*

## <a name="see-also"></a>Zobacz też
- [ResumeTracking](../msbuild/resumetracking.md)