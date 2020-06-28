---
title: 'IDiaStackWalkHelper:: imageForVA | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackWalkHelper::imageForVA method
ms.assetid: 8d4edabf-3c01-4fef-8b61-4779f3371067
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9f28af62a4e5eaa89e92db533bf461dbecaf039d
ms.sourcegitcommit: 66f31cc4ce1236e638ab58d2f70d3646206386fa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/27/2020
ms.locfileid: "85464717"
---
# <a name="idiastackwalkhelperimageforva"></a>IDiaStackWalkHelper::imageForVA
Zwraca początek obrazu pliku wykonywalnego w pamięci pod adresem wirtualnym znajdującym się w miejscu pliku wykonywalnego.

## <a name="syntax"></a>Składnia

```C++
HRESULT imageForVA(
   ULONGLONG  vaContext,
   ULONGLONG *pvaImageStart
);
```

#### <a name="parameters"></a>Parametry
 `vaContext`

podczas Adres wirtualny, który znajduje się w miejscu pliku wykonywalnego.

 `pvaImageStart`

określoną Zwraca początkowy adres wirtualny obrazu pliku wykonywalnego.

## <a name="return-value"></a>Wartość zwracana
 Jeśli powiedzie się, zwraca `S_OK` ; w przeciwnym razie zwraca kod błędu.

## <a name="see-also"></a>Zobacz też
- [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md)