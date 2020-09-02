---
title: CompilandEnv | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- CompilandEnv symbol
ms.assetid: 808404bb-ece1-47f1-b9ea-c76d4d86ddd9
caps.latest.revision: 18
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 9dfa9f1efa266a95e0580717b06cee4b9d2a7725
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68164442"
---
# <a name="compilandenv"></a>CompilandEnv
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Kompilator może zawierać dodatkowe zmienne środowiskowe z symbolami. Istnieje jeden `SymTagCompilandEnv` symbol dla każdej z tych zmiennych.  
  
## <a name="properties"></a>Właściwości  
 W poniższej tabeli przedstawiono właściwości, które są prawidłowe dla tego typu symbolu.  
  
|Właściwość|Typ danych|Opis|  
|--------------|---------------|-----------------|  
|[IDiaSymbol::get_lexicalParent](../../debugger/debug-interface-access/idiasymbol-get-lexicalparent.md)|`IDiaSymbol*`|Symbol dla elementu nadrzędnego jednostka kompilacji.|  
|[IDiaSymbol::get_lexicalParentId](../../debugger/debug-interface-access/idiasymbol-get-lexicalparentid.md)|`DWORD`|Identyfikator leksykalnego symbolicznego symbolu.|  
|[IDiaSymbol::get_name](../../debugger/debug-interface-access/idiasymbol-get-name.md)|`BSTR`|Nazwa zmiennej.|  
|[IDiaSymbol::get_symIndexId](../../debugger/debug-interface-access/idiasymbol-get-symindexid.md)|`DWORD`|Identyfikator indeksu symbolu.|  
|[IDiaSymbol::get_symTag](../../debugger/debug-interface-access/idiasymbol-get-symtag.md)|`DWORD`|Zwraca `SymTagCompilandEnv` (jedną z wartości [wyliczenia SymTagEnum —](../../debugger/debug-interface-access/symtagenum.md) ).|  
|[IDiaSymbol::get_value](../../debugger/debug-interface-access/idiasymbol-get-value.md)|`VARIANT`|Zawartość z wartościami ciągu zmiennej ( `VT_BSTR` ).|  
  
## <a name="see-also"></a>Zobacz też  
 [Jednostka kompilacji](../../debugger/debug-interface-access/compiland.md)   
 [Hierarchia leksykalna typów symboli](../../debugger/debug-interface-access/lexical-hierarchy-of-symbol-types.md)
