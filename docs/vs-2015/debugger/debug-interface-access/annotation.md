---
title: Adnotacja | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- SymTabAnnotation symbol
- Annotation symbol
ms.assetid: eb9f759b-98a5-45fc-b085-91f1f2666e72
caps.latest.revision: 9
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: ce86a76e812618730a74151ee2b37fec90831f54
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68197696"
---
# <a name="annotation"></a>Adnotacja
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Kod programu lokalizacji może być oznaczony `SymTagAnnotation` symbolem.  
  
## <a name="properties"></a>Właściwości  
 W poniższej tabeli przedstawiono właściwości, które są prawidłowe dla tego typu symbolu.  
  
|Właściwość|Typ danych|Opis|  
|--------------|---------------|-----------------|  
|[IDiaSymbol::get_addressOffset](../../debugger/debug-interface-access/idiasymbol-get-addressoffset.md)|`DWORD`|Przesunięta część lokalizacji; Aby uzyskać szczegółowe informacje, zobacz [Wyliczenie LocationType](../../debugger/debug-interface-access/locationtype.md).|  
|[IDiaSymbol::get_addressSection](../../debugger/debug-interface-access/idiasymbol-get-addresssection.md)|`DWORD`|Część lokalizacji; Aby uzyskać szczegółowe informacje, zobacz [Wyliczenie LocationType](../../debugger/debug-interface-access/locationtype.md).|  
|[IDiaSymbol::get_dataKind](../../debugger/debug-interface-access/idiasymbol-get-datakind.md)|`DWORD`|Jedna z wartości [wyliczenia elementu datakind](../../debugger/debug-interface-access/datakind.md) .|  
|[IDiaSymbol::get_relativeVirtualAddress](../../debugger/debug-interface-access/idiasymbol-get-relativevirtualaddress.md)|`DWORD`|Względne położenie tej adnotacji w jej module.|  
|[IDiaSymbol::get_symIndexId](../../debugger/debug-interface-access/idiasymbol-get-symindexid.md)|`DWORD`|Identyfikator indeksu symbolu.|  
|[IDiaSymbol::get_symTag](../../debugger/debug-interface-access/idiasymbol-get-symtag.md)|`DWORD`|Zwraca `SymTagAnnotation` (jedną z wartości [wyliczenia SymTagEnum —](../../debugger/debug-interface-access/symtagenum.md) ).|  
|[IDiaSymbol::get_value](../../debugger/debug-interface-access/idiasymbol-get-value.md)|`VARIANT`|Wartość danych stałych.|  
|[IDiaSymbol::get_virtualAddress](../../debugger/debug-interface-access/idiasymbol-get-virtualaddress.md)|`ULONGLONG`|Pozycja tej adnotacji w obrazie wykonywalnym.|  
  
## <a name="see-also"></a>Zobacz też  
 [Hierarchia leksykalna typów symboli](../../debugger/debug-interface-access/lexical-hierarchy-of-symbol-types.md)   
 [LocationType — Wyliczenie](../../debugger/debug-interface-access/locationtype.md)   
 [Lokalizacje symboli](../../debugger/debug-interface-access/symbol-locations.md)
