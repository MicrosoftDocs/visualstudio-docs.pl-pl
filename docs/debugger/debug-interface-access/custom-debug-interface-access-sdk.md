---
title: Niestandardowy (zestaw SDK dostępu do interfejsu debugowania) | Microsoft Docs
description: Znajdź informacje referencyjne na temat niestandardowych typów symboli (identyfikowanych za pomocą tagu SymTagCustom) w zestawie SDK dostępu do interfejsu debugowania programu Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- Custom symbol
ms.assetid: a219fc83-d2a8-4bc5-b7e1-bfafeb247f16
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 322619bbfa759d97061aa3b62ddc65fde43db8e4
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99857385"
---
# <a name="custom-debug-interface-access-sdk"></a>Niestandardowe (Zestaw SDK dostępu do interfejsu debugowania)
Niektóre kompilatory wprowadzają symbole, które nie są identyfikowane przez żaden ze standardowych typów symboli leksykalnych. Te symbole są identyfikowane przez `SymTagCustom` tag.

## <a name="properties"></a>Właściwości
 W poniższej tabeli przedstawiono właściwości, które są prawidłowe dla tego typu symbolu.

|Właściwość|Typ danych|Opis|
|--------------|---------------|-----------------|
|[IDiaSymbol::get_dataBytes](../../debugger/debug-interface-access/idiasymbol-get-databytes.md)|`BYTE`|Tablica danych skojarzonych z symbolem.|
|[IDiaSymbol::get_symIndexId](../../debugger/debug-interface-access/idiasymbol-get-symindexid.md)|`DWORD`|Identyfikator indeksu symbolu.|
|[IDiaSymbol::get_symTag](../../debugger/debug-interface-access/idiasymbol-get-symtag.md)|`DWORD`|Zwraca `SymTagCustom` (jedną z wartości [wyliczenia SymTagEnum —](../../debugger/debug-interface-access/symtagenum.md) ).|

## <a name="see-also"></a>Zobacz też
- [Hierarchia leksykalna typów symboli](../../debugger/debug-interface-access/lexical-hierarchy-of-symbol-types.md)