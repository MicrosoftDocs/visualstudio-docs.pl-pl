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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 5e74e44289e4fd04acf82170584af8645767b63e
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99905237"
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