---
title: 'IDiaSourceFile:: get_compilands | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSourceFile::get_compilands method
ms.assetid: 57deb50a-9c22-43ea-a80c-eab205997bc4
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 339097280cc3ddf88082f7c18c65693fd8e30702
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99854984"
---
# <a name="idiasourcefileget_compilands"></a>IDiaSourceFile::get_compilands
Pobiera moduł wyliczający compilands, który ma numery wierszy odwołujące się do tego pliku.

## <a name="syntax"></a>Składnia

```C++
HRESULT get_compilands ( 
   IDiaEnumSymbols** ppRetVal
);
```

#### <a name="parameters"></a>Parametry
 `ppRetVal`

określoną Zwraca obiekt [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md) , który zawiera listę wszystkich compilands zawierających numery wierszy odwołujące się do tego pliku.

## <a name="return-value"></a>Wartość zwracana
 Jeśli powiedzie się, zwraca `S_OK` ; w przeciwnym razie zwraca kod błędu.

## <a name="see-also"></a>Zobacz też
- [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md)
- [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)