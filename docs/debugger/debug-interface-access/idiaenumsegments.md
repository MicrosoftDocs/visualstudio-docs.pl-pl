---
title: Idiaenumsegments — | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumSegments interface
ms.assetid: 0c9edd5e-b9ce-43e1-a791-cd4c5d16d923
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 255c55dff0dab0c7b36f5029de9e688db949a1fe
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62833431"
---
# <a name="idiaenumsegments"></a>IDiaEnumSegments
Wylicza różnych segmentów znajdujących się w źródle danych.

## <a name="syntax"></a>Składnia

```
IDiaEnumSegments : IUnknown
```

## <a name="methods-in-vtable-order"></a>Metody w Vtable kolejności
W poniższej tabeli przedstawiono metody `IDiaEnumSegments`.

|Metoda|Opis|
|------------|-----------------|
|[IDiaEnumSegments::get__NewEnum](../../debugger/debug-interface-access/idiaenumsegments-get-newenum.md)|Pobiera [interfejsu interfejs IEnumVARIANT](/previous-versions/windows/desktop/api/oaidl/nn-oaidl-ienumvariant) wersję tego modułu wyliczającego.|
|[IDiaEnumSegments::get_Count](../../debugger/debug-interface-access/idiaenumsegments-get-count.md)|Pobiera liczbę segmentów.|
|[IDiaEnumSegments::Item](../../debugger/debug-interface-access/idiaenumsegments-item.md)|Pobiera segment za pomocą indeksu.|
|[IDiaEnumSegments::Next](../../debugger/debug-interface-access/idiaenumsegments-next.md)|Pobiera określoną liczbę segmentów w kolejności wyliczenia.|
|[IDiaEnumSegments::Skip](../../debugger/debug-interface-access/idiaenumsegments-skip.md)|Pomija określoną liczbę segmentów w kolejności wyliczenia.|
|[IDiaEnumSegments::Reset](../../debugger/debug-interface-access/idiaenumsegments-reset.md)|Resetuje sekwencji wyliczenia na początku.|
|[IDiaEnumSegments::Clone](../../debugger/debug-interface-access/idiaenumsegments-clone.md)|Tworzy moduł wyliczający, który zawiera ten sam stan wyliczenia jako bieżącego modułu wyliczającego.|

## <a name="remarks"></a>Uwagi

## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania
Uzyskanie tego interfejsu, wywołując `QueryInterface` metody [idiatable —](../../debugger/debug-interface-access/idiatable.md) obiektu. Zobacz przykład, aby uzyskać szczegółowe informacje.

## <a name="example"></a>Przykład
W tym przykładzie pokazano, jak uzyskać `IDiaEnumSections` interfejsu z tabeli. Aby uzyskać bardziej szczegółowy przykład użycia segmentów, zobacz [idiasegment —](../../debugger/debug-interface-access/idiasegment.md) interfejsu.

```C++
void ShowSegments(IDiaTable *pTable, IDiaSession *pSession)
{
    CComPtr<IDiaEnumSegments> pSegments;
    if ( SUCCEEDED( pTable->QueryInterface(
                                __uuidof( IDiaEnumSegments ),
                                (void**)&pSegments )
                  )
       )
    {
        // Do something with this enumeration
    }
}
```

## <a name="requirements"></a>Wymagania
Nagłówek: Dia2.h

Biblioteka: diaguids.lib

DLL: msdia80.dll

## <a name="see-also"></a>Zobacz też
- [Interfejsy (Zestaw SDK dostępu do interfejsu debugowania)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)
- [IDiaTable](../../debugger/debug-interface-access/idiatable.md)
- [IDiaSegment](../../debugger/debug-interface-access/idiasegment.md)
