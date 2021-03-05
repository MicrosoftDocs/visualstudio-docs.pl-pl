---
description: Informacje debugowania dotyczące skompilowanego programu są przechowywane w pliku bazy danych programu (. pdb) jako symbole, które są dostępne za pomocą interfejsów API zestawu dostęp do interfejsu debugowania (DIA).
title: Symbole i Tagi symboli | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- symbols [DIA SDK]
ms.assetid: 2ee3a262-cda6-48bf-b799-a37edde6c8b8
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 98631149e5a53c13bfc9b12b0d6de165c345e29a
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2021
ms.locfileid: "102155286"
---
# <a name="symbols-and-symbol-tags"></a>Symbole i znaczniki symboli
Informacje debugowania dotyczące skompilowanego programu są przechowywane w pliku bazy danych programu (. pdb) jako symbole, które są dostępne za pomocą interfejsów API zestawu dostęp do interfejsu debugowania (DIA). Wszystkie symbole mają właściwość [IDiaSymbol:: get_symTag](../../debugger/debug-interface-access/idiasymbol-get-symtag.md) i [IDiaSymbol:: get_symIndexId](../../debugger/debug-interface-access/idiasymbol-get-symindexid.md) . `symTag`Właściwość wskazuje rodzaj symbolu zdefiniowany przez Wyliczenie [wyliczenia SymTagEnum —](../../debugger/debug-interface-access/symtagenum.md) . `symIndexId`Właściwość jest `DWORD` wartością, która zawiera unikatowy identyfikator dla każdego wystąpienia symbolu.

 Symbole mają również właściwości, które mogą określać dodatkowe informacje o symbolu oraz odwołania do innych symboli, najczęściej [IDiaSymbol:: get_lexicalParent](../../debugger/debug-interface-access/idiasymbol-get-lexicalparent.md) lub [IDiaSymbol:: get_classParent](../../debugger/debug-interface-access/idiasymbol-get-classparent.md). Podczas wykonywania zapytania o właściwość, która zawiera odwołanie, odwołanie jest zwracane jako obiekt [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) . Takie właściwości są zawsze sparowane z inną właściwością o tej samej nazwie, ale z sufiksem "ID", na przykład [IDiaSymbol:: get_lexicalParentId](../../debugger/debug-interface-access/idiasymbol-get-lexicalparentid.md) i [IDiaSymbol:: get_classParentId](../../debugger/debug-interface-access/idiasymbol-get-classparentid.md). Tabele w [lokalizacjach symboli](../../debugger/debug-interface-access/symbol-locations.md), [Hierarchia leksykalna typów symboli](../../debugger/debug-interface-access/lexical-hierarchy-of-symbol-types.md)i [Hierarchia klas typów symboli](../../debugger/debug-interface-access/class-hierarchy-of-symbol-types.md) są Podkreśl właściwości dla każdego z różnych rodzajów symboli. Te właściwości mogą mieć istotne informacje lub odwołania do innych symboli. Ponieważ `*Id` właściwości są po prostu numeryczne identyfikatory porządkowe powiązanych właściwości, są pomijane z dalszych dyskusji. Są one określane tylko w przypadku, gdy jest to konieczne do wyjaśnienia parametrów.

 Podczas próby uzyskania dostępu do właściwości, jeśli nie wystąpi błąd i Właściwość symbol ma przypisaną wartość, zwraca metodę "Get" `S_OK` . Wartość zwracana przez `S_FALSE` wskazuje, że właściwość jest nieprawidłowa dla bieżącego symbolu.

## <a name="in-this-section"></a>W tej sekcji

[Lokalizacje symboli](../../debugger/debug-interface-access/symbol-locations.md)

Opisuje różne rodzaje lokalizacji, które mogą mieć symbole.

[Hierarchia leksykalna typów symboli](../../debugger/debug-interface-access/lexical-hierarchy-of-symbol-types.md)

Opisuje typy symboli, które tworzą hierarchie leksykalne, takie jak pliki, moduły i funkcje.

[Hierarchia klas typów symboli](../../debugger/debug-interface-access/class-hierarchy-of-symbol-types.md)

Opisuje typy symboli odpowiadające różnym elementom języka, takim jak klasy, tablice i zwracane typy funkcji.

## <a name="see-also"></a>Zobacz też

- [Zestaw SDK dostępu do interfejsu debugowania](../../debugger/debug-interface-access/debug-interface-access-sdk.md)
