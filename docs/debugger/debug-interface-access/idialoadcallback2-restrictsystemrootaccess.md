---
title: IDiaLoadCallback2::RestrictSystemRootAccess | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaLoadCallback2::RestrictSystemRootAccess method
ms.assetid: 39f22db8-632a-4ef0-babc-23f758e6d937
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7b15d8cb68336de044e79484533124cbb8080348
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "55036085"
---
# <a name="idialoadcallback2restrictsystemrootaccess"></a>IDiaLoadCallback2::RestrictSystemRootAccess
Określa, jeśli wyszukiwanie plików .pdb jest dozwolona w katalogu głównym systemu.  
  
## <a name="syntax"></a>Składnia  
  
```C++  
HRESULT RestrictSystemRootAccess();  
```  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.  
  
## <a name="remarks"></a>Uwagi  
 Dowolny kod powrotu innych niż `S_OK` zapobiega wyszukiwanie katalog główny systemu plików .pdb.  
  
## <a name="see-also"></a>Zobacz też  
 [IDiaLoadCallback2](../../debugger/debug-interface-access/idialoadcallback2.md)