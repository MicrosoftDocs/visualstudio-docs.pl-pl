---
title: 'IDiaSourceFile:: get_uniqueId | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSourceFile::get_uniqueId method
ms.assetid: e0b8dbc0-6061-4f31-bead-2cd72be44e41
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 3b562690569cfd5013ac44e0f091bc552874d8f6
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99854949"
---
# <a name="idiasourcefileget_uniqueid"></a>IDiaSourceFile::get_uniqueId
Pobiera prostą wartość klucza liczb całkowitych, która jest unikatowa dla tego obrazu.

## <a name="syntax"></a>Składnia

```C++
HRESULT get_uniqueId ( 
   DWORD* pRetVal
);
```

#### <a name="parameters"></a>Parametry
 `pRetVal`

określoną Zwraca prostą wartość klucza liczb całkowitych, która jest unikatowa dla tego obrazu.

## <a name="return-value"></a>Wartość zwracana
 Jeśli powiedzie się, zwraca `S_OK` ; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Porównanie kluczy zamiast ciągów może przyspieszyć przetwarzanie numerów wierszy.

## <a name="see-also"></a>Zobacz też
- [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md)