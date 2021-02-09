---
title: Stałe (zestaw SDK dostępu do interfejsu debugowania) | Microsoft Docs
description: Zobacz listę stałych ciągów, których można użyć do identyfikacji różnych sekcji pliku bazy danych debugowania programu (PDB) za pomocą zestawu SDK dostępu do interfejsu debugowania (DIA).
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- constants, DIA SDK
- DIA SDK, constants
ms.assetid: aca4ec77-bc08-4cdd-a6ce-8d4a28ea5ea3
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 89af4172a09631cfc63065cd5c49144c42d41a6d
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99865490"
---
# <a name="constants-debug-interface-access-sdk"></a>Stałe (Zestaw SDK dostępu do interfejsu debugowania)
Te stałe ciągów mogą służyć do identyfikowania różnych sekcji pliku bazy danych debugowania programu (PDB) za pomocą DIA SDK.

## <a name="constants"></a>Stałe
Poniższe elementy są zadeklarowane jako makra C/C++.

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

## <a name="see-also"></a>Zobacz też
- [Odwołanie](../../debugger/debug-interface-access/debug-interface-access-sdk-reference.md)
- [Wyliczenia i struktury](../../debugger/debug-interface-access/enumerations-and-structures.md)
- [Interfejsy (Zestaw SDK dostępu do interfejsu debugowania)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)
- [IDiaEnumTables::Item](../../debugger/debug-interface-access/idiaenumtables-item.md)
