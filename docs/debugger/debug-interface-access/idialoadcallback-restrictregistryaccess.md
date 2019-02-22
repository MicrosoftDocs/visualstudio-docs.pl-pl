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
ms.openlocfilehash: 25e6397b65c717be65a9a707dd0a53fc70321acb
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/21/2019
ms.locfileid: "56615601"
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
- [IDiaLoadCallback2](../../debugger/debug-interface-access/idialoadcallback2.md)