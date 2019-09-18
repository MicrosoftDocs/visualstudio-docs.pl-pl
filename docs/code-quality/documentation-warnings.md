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
ms.openlocfilehash: 00b42dc20b228e30a9b2632a0525a1ec8a9ddbb1
ms.sourcegitcommit: 541a0556958201ad6626bc8638406ad02640f764
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2019
ms.locfileid: "71079210"
---
# <a name="documentation-warnings"></a>Ostrzeżenia dotyczące dokumentacji

Ostrzeżenia dotyczące dokumentacji obsługują pisanie dobrze udokumentowanych bibliotek poprzez poprawne użycie [komentarzy dokumentacji XML](https://docs.microsoft.com/dotnet/csharp/codedoc) dla widocznych na zewnątrz interfejsów API.

## <a name="in-this-section"></a>W tej sekcji

| Reguła | Opis |
| - | - |
| [CA1200: Unikaj używania tagów cref z prefiksem](../code-quality/ca1200.md) | Atrybut [cref](https://docs.microsoft.com/dotnet/csharp/programming-guide/xmldoc/cref-attribute) w tagu dokumentacji XML oznacza "odwołanie do kodu". Określa, że wewnętrznym tekstem znacznika jest element kodu, taki jak typ, metoda lub właściwość. Należy unikać `cref` używania tagów z prefiksami, ponieważ uniemożliwia kompilatorowi Weryfikowanie odwołań. Uniemożliwia również znajdowanie i aktualizowanie tych odwołań do tych symboli podczas refaktoryzacji przez program Visual Studio Integrated Development Environment (IDE). |

## <a name="see-also"></a>Zobacz także

- [Ostrzeżenia analizy kodu](../code-quality/code-analysis-for-managed-code-warnings.md)
