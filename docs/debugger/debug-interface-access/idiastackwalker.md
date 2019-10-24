---
title: IDiaStackWalker | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackWalker interface
ms.assetid: 4a61a22a-9cf8-4ea1-9e6e-b42f96872d40
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2366c933bf072c295b29d06ff5610bd3735c0077
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2019
ms.locfileid: "72741518"
---
# <a name="idiastackwalker"></a>IDiaStackWalker
Zapewnia metody do przeszukiwania stosu przy użyciu informacji w pliku. pdb.

## <a name="syntax"></a>Składnia

```
IDiaStackWalker: IUnknown
```

## <a name="methods-in-vtable-order"></a>Metody w kolejności tablic wirtualnych
W poniższej tabeli przedstawiono metody `IDiaStackWalker`.

|Metoda|Opis|
|------------|-----------------|
|[IDiaStackWalker::getEnumFrames](../../debugger/debug-interface-access/idiastackwalker-getenumframes.md)|Pobiera moduł wyliczający ramek stosu dla platform x86.|
|[IDiaStackWalker::getEnumFrames2](../../debugger/debug-interface-access/idiastackwalker-getenumframes2.md)|Pobiera moduł wyliczający ramek stosu dla określonego typu platformy.|

## <a name="remarks"></a>Uwagi
Ten interfejs służy do uzyskiwania listy ramek stosu dla załadowanego modułu. Każda z metod jest przenoszona obiekt [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md) (zaimplementowany przez aplikację kliencką), który zawiera informacje niezbędne do utworzenia listy ramek stosu.

## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania
Ten interfejs jest uzyskiwany przez wywołanie metody `CoCreateInstance` z identyfikatorem klasy `CLSID_DiaStackWalker` i IDENTYFIKATORem interfejsu `IID_IDiaStackWalker`. W przykładzie pokazano, jak zostanie uzyskany ten interfejs.

## <a name="example"></a>Przykład
Ten przykład pokazuje, jak uzyskać interfejs `IDiaStackWalker`.

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

DLL: msdia80. dll

## <a name="see-also"></a>Zobacz także
- [Interfejsy (Zestaw SDK dostępu do interfejsu debugowania)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)
- [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md)
