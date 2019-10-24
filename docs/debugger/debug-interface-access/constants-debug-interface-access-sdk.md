---
title: Stałe (zestaw SDK dostępu do interfejsu debugowania) | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- constants, DIA SDK
- DIA SDK, constants
ms.assetid: aca4ec77-bc08-4cdd-a6ce-8d4a28ea5ea3
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b10ab87f056bc153ec41c125b0e01ddefa139b80
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2019
ms.locfileid: "72745400"
---
# <a name="constants-debug-interface-access-sdk"></a>Stałe (Zestaw SDK dostępu do interfejsu debugowania)
Te stałe ciągów mogą służyć do identyfikowania różnych sekcji pliku bazy danych debugowania programu (PDB) za pomocą DIA SDK.

## <a name="constants"></a>Stałe
Poniższe elementy są zadeklarowane jako CC++ /MACROS.

|Makro|Wartość|
|-----------|-----------|
|`DiaTable_Symbols`|L "symbole"|
|`DiaTable_Sections`|L "sekcje"|
|`DiaTable_SrcFiles`|L "SourceFiles"|
|`DiaTable_LineNums`|L "Numerywierszy"|
|`DiaTable_SegMap`|L "SegmentMap"|
|`DiaTable_Dbg`|L "DBG"|
|`DiaTable_InjSrc`|L "InjectedSource"|
|`DiaTable_FrameData`|L "FrameData"|

## <a name="example"></a>Przykład
Oto przykład użycia jednego z następujących symboli:

```C++
HRESULT GetSymbolTable(IDiaEnumTables *pEnumTables, IDiaTable **pTable)
{
    HRESULT hr;
    VARIANT var;
    var.vt      = VT_BSTR;
    var.bstrVal = SysAllocString( DiaTable_Symbols );
    hr = pEnumTables->Item( var, pTable );
    return(hr);
}
```

## <a name="requirements"></a>Wymagania
Nagłówek: dia2. h

## <a name="see-also"></a>Zobacz także
- [Tematy pomocy](../../debugger/debug-interface-access/debug-interface-access-sdk-reference.md)
- [Wyliczenia i struktury](../../debugger/debug-interface-access/enumerations-and-structures.md)
- [Interfejsy (Zestaw SDK dostępu do interfejsu debugowania)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)
- [IDiaEnumTables::Item](../../debugger/debug-interface-access/idiaenumtables-item.md)
