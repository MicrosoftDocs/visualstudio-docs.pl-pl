---
title: Marker_importance Wyliczenie | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- cvmarkersobj/Concurrency::diagnostic::marker_importance
helpviewer_keywords:
- Concurrency::diagnostic::marker_importance enumeration
ms.assetid: d5524ea0-0227-4d8e-9122-332291042df5
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b3f5cfb583ec4fceb9fb7428b08c00f6ca8e26b6
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "62999960"
---
# <a name="marker_importance-enumeration"></a>marker_importance wyliczenie
Reprezentuje poziom ważności znacznika wizualizatora współbieżności.

## <a name="syntax"></a>Składnia

```cpp
enum marker_importance;
```

## <a name="members"></a>Elementy członkowskie

### <a name="values"></a>Wartości

|Nazwa|Opis|
|----------|-----------------|
|`critical_importance`|Określa, że znacznik ma kluczowe znaczenie.|
|`high_importance`|Określa, że znacznik ma duże znaczenie.|
|`low_importance`|Określa, że znacznik ma niskie znaczenie.|
|`normal_importance`|Określa, że znacznik ma normalne znaczenie.|

## <a name="requirements"></a>Wymagania
 **Nagłówek:** *cvmarkersobj.h*

 **Obszar nazw:** Współbieżność::dignostyk

## <a name="see-also"></a>Zobacz też
- [diagnostyczna przestrzeń nazw](../profiling/diagnostic-namespace.md)