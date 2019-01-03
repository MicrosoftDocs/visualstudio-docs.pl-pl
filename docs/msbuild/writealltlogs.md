---
title: WriteAllTLogs | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
apiname:
- WriteAllTLogs
apilocation:
- filetracker.dll
apitype: COM
helpviewer_keywords:
- WriteAllTLogs
ms.assetid: 1fa3e10b-263c-4960-a9ad-485c02a7a872
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 4ca5bfbdae319aff8d90686deb32a5c7348fa74e
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53985540"
---
# <a name="writealltlogs"></a>WriteAllTLogs
Zapisuje dzienniki śledzenia dla wszystkich wątków i kontekstów.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
HRESULT WINAPI WriteAllTLogs(LPCTSTR intermediateDirectory, LPCTSTR tlogRootName);  
```  
  
#### <a name="parameters"></a>Parametry  
 [in] `intermediateDirectory`  
 Katalog, w którym mają zostać zapisane w dzienniku śledzenia.  
  
 [in] `tlogRootName`  
 Nazwa głównej nazwy pliku dziennika.  
  
## <a name="return-value"></a>Wartość zwracana  
 **HRESULT** z **Powodzenie** bitu, jeśli kontekst śledzenia został utworzony.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** *FileTracker.h*  
  
## <a name="see-also"></a>Zobacz także  
 [WriteContextTLogs](../msbuild/writecontexttlogs.md)