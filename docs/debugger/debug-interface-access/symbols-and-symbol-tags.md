---
title: Symbole i tagi symboli | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- symbols [DIA SDK]
ms.assetid: 2ee3a262-cda6-48bf-b799-a37edde6c8b8
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: b9d7c7d3710d7bca7fa76b30b7b2d0e97a0dfd50
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53843492"
---
# <a name="symbols-and-symbol-tags"></a>Symbole i tagi symboli
Informacje debugowania dotyczące skompilowany program znajduje się w pliku bazy danych (PDB) programu jako symbole, które są dostępne przy użyciu interfejsów API zestawu SDK debugowania interfejsu dostępu (DIA). Wszystkie symbole mają [idiasymbol::get_symtag —](../../debugger/debug-interface-access/idiasymbol-get-symtag.md) i [idiasymbol::get_symindexid —](../../debugger/debug-interface-access/idiasymbol-get-symindexid.md) właściwości. `symTag` Właściwość wskazuje rodzaj symbolu, zgodnie z definicją [symtagenum — wyliczenie](../../debugger/debug-interface-access/symtagenum.md) wyliczenia. `symIndexId` Właściwość `DWORD` wartość, która zawiera unikatowy identyfikator dla każdego wystąpienia symbolu.  
  
 Symbole również mieć właściwości, które można określić dodatkowe informacje na temat symboli, a także odwołania do innych symboli, w większości przypadków [idiasymbol::get_lexicalparent —](../../debugger/debug-interface-access/idiasymbol-get-lexicalparent.md) lub [idiasymbol::get_classparent —](../../debugger/debug-interface-access/idiasymbol-get-classparent.md). Kiedy wykonujesz zapytanie właściwość, która zawiera odwołanie, odwołanie, jest zwracana jako [idiasymbol —](../../debugger/debug-interface-access/idiasymbol.md) obiektu. Takie właściwości są zawsze skojarzone z innej właściwości o tej samej nazwie, ale sufiksami za pomocą "Id", na przykład [idiasymbol::get_lexicalparentid —](../../debugger/debug-interface-access/idiasymbol-get-lexicalparentid.md) i [idiasymbol::get_classparentid —](../../debugger/debug-interface-access/idiasymbol-get-classparentid.md). Tabele w [lokalizacje symboli](../../debugger/debug-interface-access/symbol-locations.md), [leksykalne hierarchii typów symboli](../../debugger/debug-interface-access/lexical-hierarchy-of-symbol-types.md), i [symboli typów klasy hierarchii](../../debugger/debug-interface-access/class-hierarchy-of-symbol-types.md) opisują właściwości dla każdego z różnego rodzaju programu symbole. Te właściwości mogą mieć istotne informacje dotyczące lub odwołania do innych symboli. Ponieważ `*Id` właściwości są po prostu liczbowych porządkowe identyfikatory ich powiązane właściwości, pominięto więcej dyskusji. Są one określone tylko wtedy, gdy jest to wymagane dla parametru wyjaśnienia.  
  
 Podczas dostępu do właściwości, jeśli żaden błąd nie wystąpi, a właściwość symbol zostanie przypisana wartość właściwości "get" Metoda zwraca `S_OK`. Zwracana wartość wynosząca `S_FALSE` wskazuje, że właściwość nie jest prawidłowy dla bieżący symbol.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Lokalizacje symboli](../../debugger/debug-interface-access/symbol-locations.md)  
 W tym artykule opisano różne rodzaje lokalizacje, które mogą mieć symbolu.  
  
 [Hierarchia leksykalna typów symboli](../../debugger/debug-interface-access/lexical-hierarchy-of-symbol-types.md)  
 W tym artykule opisano typy symboli, które tworzą leksykalne hierarchii, takie jak pliki, moduły i funkcje.  
  
 [Hierarchia klas typów symboli](../../debugger/debug-interface-access/class-hierarchy-of-symbol-types.md)  
 Opisuje typy symboli, odpowiadające elementom innego języka, takich jak klasy, tablic i funkcji zwracanych typów.  
  
## <a name="see-also"></a>Zobacz też  
 [Zestaw SDK dostępu do interfejsu debugowania](../../debugger/debug-interface-access/debug-interface-access-sdk.md)