---
title: WriteContextTLogs | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
apiname:
- WriteContextTLogs
apilocation:
- filetracker.dll
apitype: COM
helpviewer_keywords:
- WriteContextTLogs
ms.assetid: ffc6c7be-3f22-4624-9ffc-0122fe72b6ec
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 026fb2dedbfb67aa64c1a8e074e8c4017f9e69aa
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "54955807"
---
# <a name="writecontexttlogs"></a>WriteContextTLogs
Zapisuje pliki dziennika dla bieżącego kontekstu.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT WINAPI WriteContextTLogs(LPCTSTR intermediateDirectory, LPCTSTR tlogRootName);  
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
 [WriteAllTLogs](../msbuild/writealltlogs.md)