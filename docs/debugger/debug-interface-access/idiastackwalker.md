---
title: IDiaStackWalker | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackWalker interface
ms.assetid: 4a61a22a-9cf8-4ea1-9e6e-b42f96872d40
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: c9ec4267a0f5de93b32a4a56a61742a9148f2d9f
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99863859"
---
# <a name="idiastackwalker"></a>IDiaStackWalker
Zapewnia metody do przeszukiwania stosu przy użyciu informacji w pliku. pdb.

## <a name="syntax"></a>Składnia

```
IDiaStackWalker: IUnknown
```

## <a name="methods-in-vtable-order"></a>Metody w kolejności tablic wirtualnych
W poniższej tabeli przedstawiono metody `IDiaStackWalker` .

|Metoda|Opis|
|------------|-----------------|
|[IDiaStackWalker::getEnumFrames](../../debugger/debug-interface-access/idiastackwalker-getenumframes.md)|Pobiera moduł wyliczający ramek stosu dla platform x86.|
|[IDiaStackWalker::getEnumFrames2](../../debugger/debug-interface-access/idiastackwalker-getenumframes2.md)|Pobiera moduł wyliczający ramek stosu dla określonego typu platformy.|

## <a name="remarks"></a>Uwagi
Ten interfejs służy do uzyskiwania listy ramek stosu dla załadowanego modułu. Każda z metod jest przenoszona obiekt [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md) (zaimplementowany przez aplikację kliencką), który zawiera informacje niezbędne do utworzenia listy ramek stosu.

## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania
Ten interfejs jest uzyskiwany przez wywołanie `CoCreateInstance` metody z identyfikatorem klasy `CLSID_DiaStackWalker` i identyfikatorem interfejsu `IID_IDiaStackWalker` . W przykładzie pokazano, jak zostanie uzyskany ten interfejs.

## <a name="example"></a>Przykład
Ten przykład pokazuje, jak uzyskać `IDiaStackWalker` interfejs.

```C++

IDiaStackWalker* pStackWalker;
HRESULT hr = CoCreateInstance(CLSID_DiaStackWalker,
                              NULL,
                              CLSCTX_INPROC_SERVER,
                              IID_IDiaStackWalker,
                              (void**) &pStackWalker);
if (FAILED(hr))
{
    // Report error and exit
}
```

## <a name="requirements"></a>Wymagania
Nagłówek: dia2. h

Biblioteka: diaguids. lib

DLL: msdia80.dll

## <a name="see-also"></a>Zobacz też
- [Interfejsy (Zestaw SDK dostępu do interfejsu debugowania)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)
- [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md)
