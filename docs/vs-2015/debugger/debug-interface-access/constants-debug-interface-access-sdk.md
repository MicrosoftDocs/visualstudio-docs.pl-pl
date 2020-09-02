---
title: Stałe (zestaw SDK dostępu do interfejsu debugowania) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- constants, DIA SDK
- DIA SDK, constants
ms.assetid: aca4ec77-bc08-4cdd-a6ce-8d4a28ea5ea3
caps.latest.revision: 10
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 931e1ab46793a5ff7e0434949330eaf4dbc820e8
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68164430"
---
# <a name="constants-debug-interface-access-sdk"></a>Stałe (Zestaw SDK dostępu do interfejsu debugowania)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

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
  
```cpp#  
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
 [Odwoła](../../debugger/debug-interface-access/debug-interface-access-sdk-reference.md)   
 [Wyliczenia i struktury](../../debugger/debug-interface-access/enumerations-and-structures.md)   
 [Interfejsy (zestaw SDK dostępu do interfejsu debugowania)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)   
 [IDiaEnumTables::Item](../../debugger/debug-interface-access/idiaenumtables-item.md)
