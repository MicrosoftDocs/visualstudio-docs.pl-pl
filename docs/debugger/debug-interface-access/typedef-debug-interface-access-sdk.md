---
title: Typedef (zestaw SDK dostępu do interfejsu debugowania) | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- Typedef symbol [DIA SDK]
ms.assetid: 9ab441b9-cc72-47fa-83e2-87b3c2b891b4
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 09aa2cc4554fc877f94b7575a2d67e7b38ad4b5c
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2019
ms.locfileid: "72738485"
---
# <a name="typedef-debug-interface-access-sdk"></a>Typedef (Zestaw SDK dostępu do interfejsu debugowania)
Symbole ze znacznikami `SymTagTypedef` wprowadzają nazwy dla innych typów.

## <a name="properties"></a>Właściwości
 W poniższej tabeli przedstawiono dodatkowe prawidłowe właściwości dla tego typu symbolu.

|Właściwość|Typ danych|Opis|
|--------------|---------------|-----------------|
|[IDiaSymbol::get_baseType](../../debugger/debug-interface-access/idiasymbol-get-basetype.md)|`DWORD`|Jedna z wartości [wyliczenia podstawowa](../../debugger/debug-interface-access/basictype.md) .|
|[IDiaSymbol::get_classParent](../../debugger/debug-interface-access/idiasymbol-get-classparent.md)|`IDiaSymbol*`|Klasa nadrzędna tego elementu Typedef (jeśli istnieje).|
|[IDiaSymbol::get_classParentId](../../debugger/debug-interface-access/idiasymbol-get-classparentid.md)|`DWORD`|Identyfikator symbolu nadrzędnego klasy.|
|[IDiaSymbol::get_constructor](../../debugger/debug-interface-access/idiasymbol-get-constructor.md)|`BOOL`|`TRUE`, jeśli ten element typedef ma konstruktora.|
|[IDiaSymbol::get_constType](../../debugger/debug-interface-access/idiasymbol-get-consttype.md)|`BOOL`|`TRUE`, jeśli ten element typedef jest oznaczony jako stała.|
|[IDiaSymbol::get_hasAssignmentOperator](../../debugger/debug-interface-access/idiasymbol-get-hasassignmentoperator.md)|`BOOL`|`TRUE`, jeśli ten element typedef ma operator przypisania.|
|[IDiaSymbol::get_hasCastOperator](../../debugger/debug-interface-access/idiasymbol-get-hascastoperator.md)|`BOOL`|`TRUE`, jeśli ten element typedef ma operator Cast.|
|[IDiaSymbol::get_hasNestedTypes](../../debugger/debug-interface-access/idiasymbol-get-hasnestedtypes.md)|`BOOL`|`TRUE`, jeśli ten element typedef ma typy zagnieżdżone.|
|[IDiaSymbol::get_length](../../debugger/debug-interface-access/idiasymbol-get-length.md)|`ULONGLONG`|Długość tego elementu typedef w bajtach.|
|[IDiaSymbol::get_lexicalParent](../../debugger/debug-interface-access/idiasymbol-get-lexicalparent.md)|`IDiaSymbol*`|Symbol otaczającej jednostka kompilacji.|
|[IDiaSymbol::get_lexicalParentId](../../debugger/debug-interface-access/idiasymbol-get-lexicalparentid.md)|`DWORD`|Identyfikator leksykalnego symbolicznego symbolu.|
|[IDiaSymbol::get_name](../../debugger/debug-interface-access/idiasymbol-get-name.md)|`BSTR`|Nazwa elementu typedef.|
|[IDiaSymbol::get_nested](../../debugger/debug-interface-access/idiasymbol-get-nested.md)|`BOOL`|`TRUE`, jeśli ten element typedef jest zagnieżdżony w zakresie leksykalnym.|
|[IDiaSymbol::get_overloadedOperator](../../debugger/debug-interface-access/idiasymbol-get-overloadedoperator.md)|`BOOL`|`TRUE`, jeśli ten element typedef ma przeciążony operator.|
|[IDiaSymbol::get_packed](../../debugger/debug-interface-access/idiasymbol-get-packed.md)|`BOOL`|`TRUE`, jeśli ten element typedef jest spakowany.|
|[IDiaSymbol::get_reference](../../debugger/debug-interface-access/idiasymbol-get-reference.md)|`BOOL`|`TRUE`, jeśli ten element typedef jest odwołaniem.|
|[IDiaSymbol::get_scoped](../../debugger/debug-interface-access/idiasymbol-get-scoped.md)|`BOOL`|`TRUE`, jeśli ten element typedef znajduje się w nieglobalnym zakresie leksykalnym.|
|[IDiaSymbol::get_symIndexId](../../debugger/debug-interface-access/idiasymbol-get-symindexid.md)|`DWORD`|Identyfikator indeksu symbolu.|
|[IDiaSymbol::get_symTag](../../debugger/debug-interface-access/idiasymbol-get-symtag.md)|`DWORD`|Zwraca `SymTagTypedef` (jedną z wartości [wyliczenia SymTagEnum —](../../debugger/debug-interface-access/symtagenum.md) ).|
|[IDiaSymbol::get_type](../../debugger/debug-interface-access/idiasymbol-get-type.md)|`IDiaSymbol*`|Symbol dla typu podstawowego.|
|[IDiaSymbol::get_typeId](../../debugger/debug-interface-access/idiasymbol-get-typeid.md)|`DWORD`|Identyfikator symbolu typu.|
|[IDiaSymbol::get_udtKind](../../debugger/debug-interface-access/idiasymbol-get-udtkind.md)|`DWORD`|Jedna z wartości [wyliczenia udtkind —](../../debugger/debug-interface-access/udtkind.md) .|
|[IDiaSymbol::get_unalignedType](../../debugger/debug-interface-access/idiasymbol-get-unalignedtype.md)|`BOOL`|`TRUE`, jeśli ten element typedef nie jest wyrównany.|
|[IDiaSymbol::get_virtualTableShape](../../debugger/debug-interface-access/idiasymbol-get-virtualtableshape.md)|`IDiaSymbol*`|Symbol opisujący kształt tabeli wirtualnej.|
|[IDiaSymbol::get_virtualTableShapeId](../../debugger/debug-interface-access/idiasymbol-get-virtualtableshapeid.md)|`DWORD`|Identyfikator symbolu kształtu tabeli wirtualnej.|
|[IDiaSymbol::get_volatileType](../../debugger/debug-interface-access/idiasymbol-get-volatiletype.md)|`BOOL`|`TRUE`, jeśli ten element typedef jest oznaczony jako nietrwały.|

## <a name="remarks"></a>Uwagi
 Ponieważ element typedef może reprezentować klasę, wskaźnik lub typ zdefiniowany przez użytkownika (UDT), symbol dla elementu typedef ma takie same właściwości jak jeden z tych typów symboli.

## <a name="see-also"></a>Zobacz także
- [Hierarchia klas typów symboli](../../debugger/debug-interface-access/class-hierarchy-of-symbol-types.md)