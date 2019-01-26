---
title: Wyliczenie marker_importance | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: 3d4049a3792fcc529352baef3e4649c6157aa7f0
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "54992155"
---
# <a name="markerimportance-enumeration"></a>marker_importance — wyliczenie
Reprezentuje poziom ważności znaczników narzędzia Concurrency Visualizer.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
enum marker_importance;  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="values"></a>Wartości  
  
|Nazwa|Opis|  
|----------|-----------------|  
|`critical_importance`|Określa, że znacznika ma krytyczne znaczenie.|  
|`high_importance`|Określa, że znacznika ma o wysokiej ważności.|  
|`low_importance`|Określa, że znacznika ma niską ważnością.|  
|`normal_importance`|Określa, że znacznika ma znaczenie normalny.|  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** *cvmarkersobj.h*  
  
 **Namespace:** CONCURRENCY::Diagnostic —  
  
## <a name="see-also"></a>Zobacz także  
 [Diagnostic — przestrzeń nazw](../profiling/diagnostic-namespace.md)