---
title: SuspendTracking | Dokumentacja firmy Microsoft
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
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a093b89264df43574acd3929d4370bb43162d829
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "54946753"
---
# <a name="suspendtracking"></a>SuspendTracking
Wstrzymuje śledzenia w bieżącym kontekście.  
  
## <a name="syntax"></a>Składnia  
  
```cpp 
HRESULT WINAPI SuspendTracking(void);  
```  
  
## <a name="return-value"></a>Wartość zwracana  
 **HRESULT** z **Powodzenie** bitu, jeśli śledzenie zostało wstrzymane.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** *FileTracker.h*  
  
## <a name="see-also"></a>Zobacz także  
 [ResumeTracking](../msbuild/resumetracking.md)