---
title: Ostrzeżenia dotyczące dokumentacji
ms.date: 09/16/2019
ms.topic: reference
f1_keywords:
- vs.codeanalysis.documentationrules
helpviewer_keywords:
- documentation warnings
- managed code analysis warnings, documentation warnings
- warnings, documentation
author: mavasani
ms.author: mavasani
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4946c69bbbe4bf1c240967ebd93ef58cfa79e333
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "72807101"
---
# <a name="documentation-warnings"></a>Ostrzeżenia dotyczące dokumentacji

Ostrzeżenia dotyczące dokumentacji obsługują pisanie dobrze udokumentowanych bibliotek poprzez poprawne użycie [komentarzy dokumentacji XML](/dotnet/csharp/codedoc) dla widocznych na zewnątrz interfejsów API.

## <a name="in-this-section"></a>W tej sekcji

| Reguła | Opis |
| - | - |
| [CA1200: Unikaj używania tagów cref z prefiksem](../code-quality/ca1200.md) | Atrybut [cref](/dotnet/csharp/programming-guide/xmldoc/cref-attribute) w tagu dokumentacji XML oznacza "odwołanie do kodu". Określa, że wewnętrznym tekstem znacznika jest element kodu, taki jak typ, metoda lub właściwość. Należy unikać używania `cref` tagów z prefiksami, ponieważ uniemożliwia kompilatorowi Weryfikowanie odwołań. Uniemożliwia również znajdowanie i aktualizowanie tych odwołań do tych symboli podczas refaktoryzacji przez program Visual Studio Integrated Development Environment (IDE). |

## <a name="see-also"></a>Zobacz też

- [Ostrzeżenia analizy kodu](../code-quality/code-analysis-for-managed-code-warnings.md)
