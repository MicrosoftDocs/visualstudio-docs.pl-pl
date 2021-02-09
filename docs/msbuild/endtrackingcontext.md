---
title: EndTrackingContext | Microsoft Docs
description: Zapoznaj się z składnią, wartością zwracaną i wymaganiami, aby użyć programu MSBuild EndTrackingContext do zakończenia bieżącego kontekstu śledzenia.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
apiname:
- EndTrackingContext
apilocation:
- filetracker.dll
apitype: COM
helpviewer_keywords:
- EndTrackingContext
ms.assetid: c2c5d794-8dc8-4594-8717-70dc79a0e75d
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 90f4c8c4a83a496dba537e74dddfde4ae3f2f21a
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99877229"
---
# <a name="endtrackingcontext"></a>EndTrackingContext

Zakończ bieżący kontekst śledzenia.

## <a name="syntax"></a>Składnia

```cpp
HRESULT WINAPI EndTrackingContext();
```

## <a name="return-value"></a>Wartość zwracana

**Wynik HRESULT** z **pomyślnym** bitem ustawionym, jeśli kontekst śledzenia został zakończony.

## <a name="requirements"></a>Wymagania

**Nagłówek:** *FileTracker. h*

## <a name="see-also"></a>Zobacz też

- [StartTrackingContext](../msbuild/starttrackingcontext.md)
