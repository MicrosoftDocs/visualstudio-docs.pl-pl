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
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 56f4fb82ab0e9792cadbeeea05499744e4c8ce46
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62939026"
---
# <a name="stoptrackingandcleanup"></a>StopTrackingAndCleanup
Zatrzymanie wszystkich funkcji śledzenia i zwalnia pamięć, wszystkie używane w sesji śledzenia.

## <a name="syntax"></a>Składnia

```cpp
HRESULT WINAPI StopTrackingAndCleanup(void);
```

## <a name="return-value"></a>Wartość zwracana
 Zwraca **HRESULT** z **Powodzenie** bitu, jeśli śledzenie została zatrzymana.

## <a name="requirements"></a>Wymagania
 **Nagłówek:** *FileTracker.h*

## <a name="see-also"></a>Zobacz także
- [StartTrackingContext](../msbuild/starttrackingcontext.md)