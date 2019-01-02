---
title: ResumeTracking | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
apiname:
- ResumeTracking
apilocation:
- filetracker.dll
apitype: COM
helpviewer_keywords:
- ResumeTracking
ms.assetid: d637e019-7c50-4b0a-812e-bc822001e697
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 9608ca6237a44d48d4ee4c4d8daf057d88fc5b53
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53947835"
---
# <a name="resumetracking"></a>ResumeTracking
Wznawia śledzenia w bieżącym kontekście.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT WINAPI ResumeTracking();  
```  
  
## <a name="return-value"></a>Wartość zwracana  
 **HRESULT** z **Powodzenie** bitu, jeśli śledzenie zostało wznowione. **E_FAIL** jest zwracany, jeśli nie można wznowić śledzenia, ponieważ kontekst nie jest dostępna.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** *FileTracker.h*  
  
## <a name="see-also"></a>Zobacz także  
 [SuspendTracking](../msbuild/suspendtracking.md)