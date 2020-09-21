---
title: Reguły dokumentacji
ms.date: 09/16/2019
ms.topic: reference
f1_keywords:
- vs.codeanalysis.documentationrules
helpviewer_keywords:
- documentation rules
- managed code analysis rules, documentation rules
- rules, documentation
author: mavasani
ms.author: mavasani
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5f4ec6a0dd154dae89145add26c60a8b1322a444
ms.sourcegitcommit: 566144d59c376474c09bbb55164c01d70f4b621c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2020
ms.locfileid: "90808655"
---
# <a name="documentation-rules"></a>Reguły dokumentacji

Reguły dokumentacji obsługują pisanie dobrze udokumentowanych bibliotek poprzez poprawne użycie [komentarzy dokumentacji XML](/dotnet/csharp/codedoc) dla widocznych na zewnątrz interfejsów API.

## <a name="in-this-section"></a>W tej sekcji

| Reguła | Opis |
| - | - |
| [CA1200: Unikaj używania tagów cref z prefiksem](../code-quality/ca1200.md) | Atrybut [cref](/dotnet/csharp/programming-guide/xmldoc/cref-attribute) w tagu dokumentacji XML oznacza "odwołanie do kodu". Określa, że wewnętrznym tekstem znacznika jest element kodu, taki jak typ, metoda lub właściwość. Należy unikać używania `cref` tagów z prefiksami, ponieważ uniemożliwia kompilatorowi Weryfikowanie odwołań. Uniemożliwia również znajdowanie i aktualizowanie tych odwołań do tych symboli podczas refaktoryzacji przez program Visual Studio Integrated Development Environment (IDE). |

## <a name="see-also"></a>Zobacz też

- [Reguły analizy kodu](../code-quality/code-analysis-for-managed-code-warnings.md)
