---
title: Idialoadcallback::restrictregistryaccess — | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaLoadCallback::RestrictRegistryAccess method
ms.assetid: de4760c3-a746-4bab-8065-1388fed31b67
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ab01afeec0539dbb6f7ccd4e41f265e3430eb923
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "54920048"
---
# <a name="idialoadcallbackrestrictregistryaccess"></a>IDiaLoadCallback::RestrictRegistryAccess
Określa, jeśli zapytania rejestru może służyć do zlokalizowania ścieżki wyszukiwania symboli.  
  
## <a name="syntax"></a>Składnia  
  
```C++  
HRESULT RestrictRegistryAccess();  
```  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.  
  
## <a name="remarks"></a>Uwagi  
 Dowolny kod powrotu innych niż `S_OK` zapobiega zapytanie w rejestrze dla ścieżki wyszukiwania symboli.  
  
## <a name="see-also"></a>Zobacz też  
 [IDiaLoadCallback2](../../debugger/debug-interface-access/idialoadcallback2.md)