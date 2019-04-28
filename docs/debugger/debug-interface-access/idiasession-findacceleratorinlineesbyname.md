---
title: IDiaSession::findAcceleratorInlineesByName | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: e203e5c2-6563-43fa-be56-3063955043ab
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: fb3caa5574605864a0dd16b59b6f451530b8e631
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62827789"
---
# <a name="idiasessionfindacceleratorinlineesbyname"></a>IDiaSession::findAcceleratorInlineesByName
Zwraca wyliczenie symboli dla ramki wbudowane odpowiadającej nazwie funkcji określone w jednej linii.

## <a name="syntax"></a>Składnia

```C++
HRESULT findAcceleratorInlineeLinesByName ( 
   LPCOLESTR             name,
   DWORD                 option,
   IDiaEnumSymbols**     ppResult
);
```

#### <a name="parameters"></a>Parametry
 `name`

[in] Nazwa funkcji przed wstawianiem do treści do wyszukania.

 `option`

[in] Opcje wyszukiwania nazw ma być używany podczas wyszukiwania wbudowanego w ramkach, które odpowiadają `name`. Aby uzyskać więcej informacji, zobacz [namesearchoptions — wyliczenie](../../debugger/debug-interface-access/namesearchoptions.md).

 `ppResult`

[out] Wskaźnik do `IDiaEnumSymbols` wskaźnik interfejsu, który jest inicjowany z wynikiem.

## <a name="return-value"></a>Wartość zwracana
 Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Ta funkcja wyszukuje wersji śródwierszowych tylko w ramach funkcji klasy zastępczej akceleratora. Ignoruje natywnego języka C++ procedury rekordów.

## <a name="see-also"></a>Zobacz też
- [IDiaSession](../../debugger/debug-interface-access/idiasession.md)
- [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)