---
description: Pobiera moduł wyliczający dla wszystkich tabel znajdujących się w magazynie symboli.
title: 'IDiaSession:: getEnumTables | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSession::getEnumTables method
ms.assetid: 66e0fba2-ca63-4e24-a46a-c99c7fb61dd1
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: d75ac2a4bca7051c6fe80f80b7a8063ef7ec6c86
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2021
ms.locfileid: "102157022"
---
# <a name="idiasessiongetenumtables"></a>IDiaSession::getEnumTables
Pobiera moduł wyliczający dla wszystkich tabel znajdujących się w magazynie symboli.

## <a name="syntax"></a>Składnia

```C++
HRESULT getEnumTables (
    IDiaEnumTables** ppEnumTables
);
```

#### <a name="parameters"></a>Parametry
`ppEnumTables`

określoną Zwraca obiekt [IDiaEnumTables](../../debugger/debug-interface-access/idiaenumtables.md) . Użyj tego interfejsu, aby wyliczyć tabele w magazynie symboli.

## <a name="return-value"></a>Wartość zwracana
Jeśli powiedzie się, zwraca `S_OK` ; w przeciwnym razie zwraca kod błędu.

## <a name="example"></a>Przykład
Ten przykład przedstawia ogólną funkcję, która używa `getEnumTables` metody do uzyskania określonego obiektu modułu wyliczającego. W przypadku znalezienia modułu wyliczającego funkcja zwraca wskaźnik, który można rzutować na żądany interfejs; w przeciwnym razie funkcja zwraca wartość `NULL` .

```C++
IUnknown *GetTable(IDiaSession *pSession, REFIID iid)
{
    IUnknown *pUnknown = NULL;
    if (pSession != NULL)
    {
        CComPtr<IDiaEnumTables> pEnumTables;
        if (pSession->getEnumTables(&pEnumTables) == S_OK)
        {
            CComPtr<IDiaTable> pTable;
            DWORD celt = 0;
            while(pEnumTables->Next(1,&pTable,&celt) == S_OK &&
                  celt == 1)
            {
                if (pTable->QueryInterface(iid, (void **)pUnknown) == S_OK)
                {
                    break;
                }
                pTable = NULL;
            }
        }
    }
    return(pUnknown);
}
```

## <a name="see-also"></a>Zobacz też
- [IDiaEnumTables](../../debugger/debug-interface-access/idiaenumtables.md)
- [IDiaSession](../../debugger/debug-interface-access/idiasession.md)
