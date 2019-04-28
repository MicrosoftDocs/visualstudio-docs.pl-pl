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
ms.openlocfilehash: 5ad74f92765ee449eab1e3089511a063e70d96a0
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62831936"
---
# <a name="idiastackwalker"></a>IDiaStackWalker
Udostępnia metody stosu szczegółowe, korzystając z informacji w pliku .pdb.

## <a name="syntax"></a>Składnia

```
IDiaStackWalker: IUnknown
```

## <a name="methods-in-vtable-order"></a>Metody w Vtable kolejności
W poniższej tabeli przedstawiono metody `IDiaStackWalker`.

|Metoda|Opis|
|------------|-----------------|
|[IDiaStackWalker::getEnumFrames](../../debugger/debug-interface-access/idiastackwalker-getenumframes.md)|Pobiera moduł wyliczający ramek stosu dla x86 platform.|
|[IDiaStackWalker::getEnumFrames2](../../debugger/debug-interface-access/idiastackwalker-getenumframes2.md)|Pobiera moduł wyliczający ramek stosu dla typu określonej platformy.|

## <a name="remarks"></a>Uwagi
Ten interfejs jest używany do uzyskiwania listy ramek stosu dla załadowanym module. Każdej z metod jest przekazywany [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md) obiektu (implementowane przez aplikację klienta), który dostarcza niezbędne informacje, aby utworzyć listę ramek stosu.

## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania
Ten interfejs jest można uzyskać przez wywołanie `CoCreateInstance` metody z identyfikatorem klasy `CLSID_DiaStackWalker` i identyfikator interfejsu `IID_IDiaStackWalker`. W przykładzie przedstawiono sposób uzyskiwania tego interfejsu.

## <a name="example"></a>Przykład
W tym przykładzie pokazano, jak uzyskać `IDiaStackWalker` interfejsu.

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
Nagłówek: Dia2.h

Biblioteka: diaguids.lib

DLL: msdia80.dll

## <a name="see-also"></a>Zobacz też
- [Interfejsy (Zestaw SDK dostępu do interfejsu debugowania)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)
- [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md)
