---
description: Zwraca początek obrazu pliku wykonywalnego w pamięci pod adresem wirtualnym znajdującym się w miejscu pliku wykonywalnego.
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 2459ed59f4b34befd893d25848de9482b39f9d70
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2021
ms.locfileid: "102156847"
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
