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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: da1ef921106732a7787f68a979bc88f3ac012b6d
ms.sourcegitcommit: c4927ef8fe239005d7feff6c5a7707c594a7a05c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2020
ms.locfileid: "92436670"
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
