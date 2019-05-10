---
title: Friend (dostępu do interfejsu debugowania zestawu SDK) | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- friend functions [DIA SDK]
- friend classes [DIA SDK]
- Friend symbol
ms.assetid: 5147a170-41ce-4727-8ace-c318e8d11647
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 118a6b6caf6a208898bba3894d532e5dc6e4a14a
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62554694"
---
# <a name="friend-debug-interface-access-sdk"></a>Przyjaciel (Zestaw SDK dostępu do interfejsu debugowania)
Klasy przyjazne i Friend — funkcje, które są identyfikowane przez `SymTagFriend` symboli. Ich elementy podrzędne elementu nadrzędnego typy zdefiniowane przez użytkownika (UDTs) i ma [idiasymbol::get_classparent —](../../debugger/debug-interface-access/idiasymbol-get-classparent.md) właściwości.

## <a name="properties"></a>Właściwości
 W poniższej tabeli przedstawiono dodatkowe prawidłowe właściwości dla tego typu symbolu.

|Właściwość|Typ danych|Opis|
|--------------|---------------|-----------------|
|[IDiaSymbol::get_classParent](../../debugger/debug-interface-access/idiasymbol-get-classparent.md)|`IDiaSymbol*`|Symbol nadrzędnego UDT.|
|[IDiaSymbol::get_classParentId](../../debugger/debug-interface-access/idiasymbol-get-classparentid.md)|`DWORD`|Identyfikator klasy nadrzędnej symbolu.|
|[IDiaSymbol::get_name](../../debugger/debug-interface-access/idiasymbol-get-name.md)|`BSTR`|Nazwa klasy lub funkcji.|
|[IDiaSymbol::get_symIndexId](../../debugger/debug-interface-access/idiasymbol-get-symindexid.md)|`DWORD`|Identyfikator indeksu: symbolu.|
|[IDiaSymbol::get_symTag](../../debugger/debug-interface-access/idiasymbol-get-symtag.md)|`DWORD`|Zwraca `SymTagFriend` (jeden z [symtagenum — wyliczenie](../../debugger/debug-interface-access/symtagenum.md) wartości).|
|[IDiaSymbol::get_type](../../debugger/debug-interface-access/idiasymbol-get-type.md)|`IDiaSymbol*`|Symbol dla klasy lub funkcji.|
|[IDiaSymbol::get_typeId](../../debugger/debug-interface-access/idiasymbol-get-typeid.md)|`DWORD`|Identyfikator typu symbolu.|

## <a name="see-also"></a>Zobacz też
- [Hierarchia klas typów symboli](../../debugger/debug-interface-access/class-hierarchy-of-symbol-types.md)