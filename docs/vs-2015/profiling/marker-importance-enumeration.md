---
title: Wyliczenie marker_importance | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- cvmarkersobj/Concurrency::diagnostic::marker_importance
helpviewer_keywords:
- Concurrency::diagnostic::marker_importance enumeration
ms.assetid: d5524ea0-0227-4d8e-9122-332291042df5
caps.latest.revision: 8
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: a4451a7b222b66f0fe5bea2b0e5f2b8499c9033c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68198382"
---
# <a name="marker_importance-enumeration"></a>marker_importance — Wyliczenie
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Reprezentuje poziom ważności znacznika Concurrency Visualizer.  
  
## <a name="syntax"></a>Składnia  
  
```  
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
 **Nagłówek:** cvmarkersobj. h  
  
 **Przestrzeń nazw:** Współbieżność::d przesła  
  
## <a name="see-also"></a>Zobacz też  
 [Przestrzeń nazw diagnostyki](../profiling/diagnostic-namespace.md)
