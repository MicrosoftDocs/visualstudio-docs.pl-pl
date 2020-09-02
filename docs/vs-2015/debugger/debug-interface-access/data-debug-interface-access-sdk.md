---
title: Dane (zestaw SDK dostępu do interfejsu debugowania) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- global variables [C++], as symbols
- local variables [C++], as symbols
- class members [C++], as symbols
- Data symbol
ms.assetid: 0f17e96a-2e06-42c9-a877-3e5e670ee0ef
caps.latest.revision: 20
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: a69e1cddec945cd797d91a92d28ba46221a20d10
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68197661"
---
# <a name="data-debug-interface-access-sdk"></a>Dane (Zestaw SDK dostępu do interfejsu debugowania)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Wszystkie zmienne, takie jak parametry, zmienne lokalne, zmienne globalne i składowe klas, są identyfikowane przez `SymTagData` symbole. Wartości stałe ( `LocIsConstant` ) są również identyfikowane za pomocą tego typu.  
  
## <a name="properties"></a>Właściwości  
 W poniższej tabeli przedstawiono właściwości, które są prawidłowe dla tego typu symbolu.  
  
|Właściwość|Typ danych|Opis|  
|--------------|---------------|-----------------|  
|[IDiaSymbol::get_access](../../debugger/debug-interface-access/idiasymbol-get-access.md)|`DWORD`|Jeśli pole, następnie jedną z wartości [wyliczenia CV_access_e](../../debugger/debug-interface-access/cv-access-e.md).|  
|[IDiaSymbol::get_addressOffset](../../debugger/debug-interface-access/idiasymbol-get-addressoffset.md)|`DWORD`|Przesunięta część lokalizacji; Aby uzyskać szczegółowe informacje, zobacz [Wyliczenie LocationType](../../debugger/debug-interface-access/locationtype.md).|  
|[IDiaSymbol::get_addressSection](../../debugger/debug-interface-access/idiasymbol-get-addresssection.md)|`DWORD`|Część lokalizacji; Aby uzyskać szczegółowe informacje, zobacz [Wyliczenie LocationType](../../debugger/debug-interface-access/locationtype.md).|  
|[IDiaSymbol::get_addressTaken](../../debugger/debug-interface-access/idiasymbol-get-addresstaken.md)|`BOOL`|`TRUE` Jeśli do tego adresu danych odwołuje się inny symbol.|  
|[IDiaSymbol::get_bitPosition](../../debugger/debug-interface-access/idiasymbol-get-bitposition.md)|`DWORD`|Pozycja bitu lokalizacji; Aby uzyskać szczegółowe informacje, zobacz [Wyliczenie LocationType](../../debugger/debug-interface-access/locationtype.md) (nieobsługiwane w DIA SDK v 8.0).|  
|[IDiaSymbol::get_classParent](../../debugger/debug-interface-access/idiasymbol-get-classparent.md)|`IDiaSymbol*`|Symbol klasy, jeśli jest to pole struktury, Unii lub klasy.|  
|[IDiaSymbol::get_classParentId](../../debugger/debug-interface-access/idiasymbol-get-classparentid.md)|`DWORD`|Identyfikator symbolu nadrzędnego klasy.|  
|[IDiaSymbol::get_compilerGenerated](../../debugger/debug-interface-access/idiasymbol-get-compilergenerated.md)|`BOOL`|`TRUE` Jeśli dane zostały wygenerowane przez kompilator.|  
|[IDiaSymbol::get_constType](../../debugger/debug-interface-access/idiasymbol-get-consttype.md)|`BOOL`|`TRUE` Jeśli dane są oznaczone jako stałe.|  
|[IDiaSymbol::get_dataKind](../../debugger/debug-interface-access/idiasymbol-get-datakind.md)|`DWORD`|Jedna z wartości [wyliczenia elementu datakind](../../debugger/debug-interface-access/datakind.md) .|  
|[IDiaSymbol::get_isAggregated](../../debugger/debug-interface-access/idiasymbol-get-isaggregated.md)|`BOOL`|`TRUE` Jeśli dane są częścią zagregowanego typu danych (tylko w DIA SDK v 8.0 i nowszych).|  
|[IDiaSymbol::get_isSplitted](../../debugger/debug-interface-access/idiasymbol-get-issplitted.md)|`BOOL`|`TRUE` Jeśli dane zostały podzielone na agregację wielu symboli (tylko w DIA SDK v 8.0 i nowszych).|  
|[IDiaSymbol::get_length](../../debugger/debug-interface-access/idiasymbol-get-length.md)|`ULONGLONG`|Długość pole bitowe; Aby uzyskać szczegółowe informacje, zobacz [Wyliczenie LocationType](../../debugger/debug-interface-access/locationtype.md).|  
|[IDiaSymbol::get_lexicalParent](../../debugger/debug-interface-access/idiasymbol-get-lexicalparent.md)|`IDiaSymbol*`|Symbol otaczającego jednostka kompilacji, funkcji lub bloku.|  
|[IDiaSymbol::get_lexicalParentId](../../debugger/debug-interface-access/idiasymbol-get-lexicalparentid.md)|`DWORD`|Identyfikator leksykalnego symbolicznego symbolu.|  
|[IDiaSymbol::get_locationType](../../debugger/debug-interface-access/idiasymbol-get-locationtype.md)|`DWORD`|Dowolna z dozwolonych typów lokalizacji; Aby uzyskać szczegółowe informacje, zobacz [lokalizacje symboli](../../debugger/debug-interface-access/symbol-locations.md)|  
|[IDiaSymbol::get_name](../../debugger/debug-interface-access/idiasymbol-get-name.md)|`BSTR`|Nazwa zmiennej.|  
|[IDiaSymbol::get_offset](../../debugger/debug-interface-access/idiasymbol-get-offset.md)|`LONG`|Przesunięcie z zawartości rejestru; Aby uzyskać szczegółowe informacje, zobacz [Wyliczenie LocationType](../../debugger/debug-interface-access/locationtype.md).|  
|[IDiaSymbol::get_registerId](../../debugger/debug-interface-access/idiasymbol-get-registerid.md)|`DWORD`|Zarejestruj oznaczenie lokalizacji; Aby uzyskać szczegółowe informacje, zobacz [Wyliczenie LocationType](../../debugger/debug-interface-access/locationtype.md).|  
|[IDiaSymbol::get_relativeVirtualAddress](../../debugger/debug-interface-access/idiasymbol-get-relativevirtualaddress.md)|`DWORD`|Względne położenie danych w jego bloku.|  
|[IDiaSymbol::get_slot](../../debugger/debug-interface-access/idiasymbol-get-slot.md)|`DWORD`|Pobiera numer gniazda danych.|  
|[IDiaSymbol::get_symIndexId](../../debugger/debug-interface-access/idiasymbol-get-symindexid.md)|`DWORD`|Identyfikator indeksu symbolu.|  
|[IDiaSymbol::get_symTag](../../debugger/debug-interface-access/idiasymbol-get-symtag.md)|`DWORD`|Zwraca `SymTagData` (jedną z wartości [wyliczenia SymTagEnum —](../../debugger/debug-interface-access/symtagenum.md) ).|  
|[IDiaSymbol::get_token](../../debugger/debug-interface-access/idiasymbol-get-token.md)|`DWORD`|Token metadanych reprezentujący dane.|  
|[IDiaSymbol::get_type](../../debugger/debug-interface-access/idiasymbol-get-type.md)|`IDiaSymbol*`|Symbol typu zmiennej.|  
|[IDiaSymbol::get_typeId](../../debugger/debug-interface-access/idiasymbol-get-typeid.md)|`DWORD`|Identyfikator symbolu typu zmiennej.|  
|[IDiaSymbol::get_unalignedType](../../debugger/debug-interface-access/idiasymbol-get-unalignedtype.md)|`BOOL`|`TRUE` Jeśli dane są niewyrównane.|  
|[IDiaSymbol::get_value](../../debugger/debug-interface-access/idiasymbol-get-value.md)|`VARIANT`|Wartość danych stałych.|  
|[IDiaSymbol::get_virtualAddress](../../debugger/debug-interface-access/idiasymbol-get-virtualaddress.md)|`ULONGLONG`|Pozycja danych w pliku wykonywalnym.|  
|[IDiaSymbol::get_volatileType](../../debugger/debug-interface-access/idiasymbol-get-volatiletype.md)|`BOOL`|`TRUE` Jeśli dane są oznaczone jako nietrwałe.|  
  
## <a name="see-also"></a>Zobacz też  
 [CV_access_e, Wyliczenie](../../debugger/debug-interface-access/cv-access-e.md)   
 [Wyliczenie typu datakind](../../debugger/debug-interface-access/datakind.md)   
 [Hierarchia leksykalna typów symboli](../../debugger/debug-interface-access/lexical-hierarchy-of-symbol-types.md)   
 [LocationType — Wyliczenie](../../debugger/debug-interface-access/locationtype.md)   
 [Lokalizacje symboli](../../debugger/debug-interface-access/symbol-locations.md)
