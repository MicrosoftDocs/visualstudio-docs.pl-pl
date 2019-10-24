---
title: Symbole i Tagi symboli | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- symbols [DIA SDK]
ms.assetid: 2ee3a262-cda6-48bf-b799-a37edde6c8b8
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5d2281a82926dabfde88b8d4bb9096f0e9624211
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2019
ms.locfileid: "72738530"
---
# <a name="symbols-and-symbol-tags"></a>Symbole i znaczniki symboli
Informacje debugowania dotyczące skompilowanego programu są przechowywane w pliku bazy danych programu (. pdb) jako symbole, które są dostępne za pomocą interfejsów API zestawu dostęp do interfejsu debugowania (DIA). Wszystkie symbole mają właściwość [IDiaSymbol:: get_symTag](../../debugger/debug-interface-access/idiasymbol-get-symtag.md) i [IDiaSymbol:: get_symIndexId](../../debugger/debug-interface-access/idiasymbol-get-symindexid.md) . Właściwość `symTag` wskazuje rodzaj symbolu zdefiniowany przez Wyliczenie [wyliczenia SymTagEnum —](../../debugger/debug-interface-access/symtagenum.md) . Właściwość `symIndexId` jest wartością `DWORD`, która zawiera unikatowy identyfikator dla każdego wystąpienia symbolu.

 Symbole mają również właściwości, które mogą określać dodatkowe informacje o symbolu oraz odwołania do innych symboli, najczęściej [IDiaSymbol:: get_lexicalParent](../../debugger/debug-interface-access/idiasymbol-get-lexicalparent.md) lub [IDiaSymbol:: get_classParent](../../debugger/debug-interface-access/idiasymbol-get-classparent.md). Podczas wykonywania zapytania o właściwość, która zawiera odwołanie, odwołanie jest zwracane jako obiekt [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) . Takie właściwości są zawsze sparowane z inną właściwością o tej samej nazwie, ale z sufiksem "ID", na przykład [IDiaSymbol:: get_lexicalParentId](../../debugger/debug-interface-access/idiasymbol-get-lexicalparentid.md) i [IDiaSymbol:: get_classParentId](../../debugger/debug-interface-access/idiasymbol-get-classparentid.md). Tabele w [lokalizacjach symboli](../../debugger/debug-interface-access/symbol-locations.md), [Hierarchia leksykalna typów symboli](../../debugger/debug-interface-access/lexical-hierarchy-of-symbol-types.md)i [Hierarchia klas typów symboli](../../debugger/debug-interface-access/class-hierarchy-of-symbol-types.md) są Podkreśl właściwości dla każdego z różnych rodzajów symboli. Te właściwości mogą mieć istotne informacje lub odwołania do innych symboli. Ponieważ właściwości `*Id` są po prostu numeryczne identyfikatory porządkowe powiązanych właściwości, są pomijane z dalszych dyskusji. Są one określane tylko w przypadku, gdy jest to konieczne do wyjaśnienia parametrów.

 W przypadku próby uzyskania dostępu do właściwości, jeśli nie wystąpi błąd i Właściwość symbol ma przypisaną wartość, Metoda "Get" właściwości zwraca `S_OK`. Wartość zwracana `S_FALSE` wskazuje, że właściwość jest nieprawidłowa dla bieżącego symbolu.

## <a name="in-this-section"></a>W tej sekcji

[Lokalizacje symboli](../../debugger/debug-interface-access/symbol-locations.md)

Opisuje różne rodzaje lokalizacji, które mogą mieć symbole.

[Hierarchia leksykalna typów symboli](../../debugger/debug-interface-access/lexical-hierarchy-of-symbol-types.md)

Opisuje typy symboli, które tworzą hierarchie leksykalne, takie jak pliki, moduły i funkcje.

[Hierarchia klas typów symboli](../../debugger/debug-interface-access/class-hierarchy-of-symbol-types.md)

Opisuje typy symboli odpowiadające różnym elementom języka, takim jak klasy, tablice i zwracane typy funkcji.

## <a name="see-also"></a>Zobacz także

- [Zestaw SDK dostępu do interfejsu debugowania](../../debugger/debug-interface-access/debug-interface-access-sdk.md)