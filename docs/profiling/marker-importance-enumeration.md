---
title: Wyliczenie marker_importance | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- cvmarkersobj/Concurrency, diagnostic::marker_importance
helpviewer_keywords:
- Concurrency, diagnostic::marker_importance enumeration
ms.assetid: d5524ea0-0227-4d8e-9122-332291042df5
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d67a1806034d55147379626b6eb4f868532e4d77
ms.sourcegitcommit: 57d96de120e0574e506dfd80bb7adfbac73f96be
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/24/2020
ms.locfileid: "85330741"
---
# <a name="marker_importance-enumeration"></a>marker_importance, Wyliczenie
Reprezentuje poziom ważności znacznika Concurrency Visualizer.

## <a name="syntax"></a>Składnia

```cpp
enum marker_importance;
```

## <a name="members"></a>Elementy członkowskie

### <a name="values"></a>Wartości

|Nazwa|Opis|
|----------|-----------------|
|`critical_importance`|Określa, że znacznik ma krytyczne znaczenie.|
|`high_importance`|Określa, że znacznik ma wysoką ważność.|
|`low_importance`|Określa, że znacznik ma niską ważność.|
|`normal_importance`|Określa, że znacznik ma normalne znaczenie.|

## <a name="requirements"></a>Wymagania
 **Nagłówek:** *cvmarkersobj. h*

 **Przestrzeń nazw:** Współbieżność::d przesła

## <a name="see-also"></a>Zobacz też
- [Przestrzeń nazw diagnostyki](../profiling/diagnostic-namespace.md)