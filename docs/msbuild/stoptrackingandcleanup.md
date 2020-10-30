---
title: StopTrackingAndCleanup | Microsoft Docs
description: Dowiedz się, w jaki sposób program MSBuild korzysta z StopTrackingAndCleanup, aby zatrzymać wszystkie śledzenie i zwolnić każdą pamięć używaną przez sesję śledzenia.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: 05aec8bc85ac392670469da8073da02888b2f063
ms.sourcegitcommit: 1a36533f385e50c05f661f440380fda6386ed3c1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2020
ms.locfileid: "93048097"
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