---
title: Idiasymbol::get_type — | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_type method
ms.assetid: 1c6a4176-dd4e-4c22-8b8f-0e559fc078ba
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4fa57b1f289f9cc5e8c57c08b6d51bb1677c3db4
ms.sourcegitcommit: 75807551ea14c5a37aa07dd93a170b02fc67bc8c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/12/2019
ms.locfileid: "62835375"
---
# <a name="idiasymbolgettype"></a>IDiaSymbol::get_type
Pobiera symbol, który reprezentuje typ dla tego symbolu.

## <a name="syntax"></a>Składnia

```C++
HRESULT get_type (
    IDiaSymbol** pRetVal
);
```

#### <a name="parameters"></a>Parametry
`pRetVal`

[out] Zwraca [idiasymbol —](../../debugger/debug-interface-access/idiasymbol.md) obiekt, który reprezentuje typ tego symbolu.

## <a name="return-value"></a>Wartość zwracana
Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca `S_FALSE` albo kod błędu.

> [!NOTE]
> Zwracana wartość wynosząca `S_FALSE` oznacza, że właściwość nie jest dostępna dla symbolu.

## <a name="remarks"></a>Uwagi
Aby określić typ symbolu ma, należy wywołać tę metodę i sprawdź, wynikowy [idiasymbol —](../../debugger/debug-interface-access/idiasymbol.md) obiektu. Należy pamiętać, że możliwe jest nie mieć typ symbolu. Na przykład nazwę struktury nie ma typu, ale może mieć elementów podrzędnych symbole (Użyj [idiasymbol::findchildren —](../../debugger/debug-interface-access/idiasymbol-findchildren.md) metodę, aby zbadać te elementy podrzędne).

## <a name="example"></a>Przykład

```C++
IDiaSymbol*         pType;
CComPtr<IDiaSymbol> pBaseType;
if (SUCCEEDED(pType->get_type( &pBaseType ))) {
    BasicType btBaseType;
    if (SUCCEEDED(pBaseType->get_baseType((DWORD *)&btBaseType))) {
        // Do something with basic type.
    }
}
```

## <a name="see-also"></a>Zobacz też
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [IDiaSymbol::get_baseType](../../debugger/debug-interface-access/idiasymbol-get-basetype.md)
- [IDiaSymbol::findChildren](../../debugger/debug-interface-access/idiasymbol-findchildren.md)
