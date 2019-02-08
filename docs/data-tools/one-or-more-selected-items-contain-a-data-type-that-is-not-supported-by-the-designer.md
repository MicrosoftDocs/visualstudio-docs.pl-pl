---
title: Co najmniej jeden wybrany element zawiera typ danych nieobsługiwany przez projektanta
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 71dcd4f9-2946-42c5-9ce4-99c819ea2785
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 12ec2ed7dc2a12556fcb6eeeddbe2d0745ae7f72
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2019
ms.locfileid: "55928521"
---
# <a name="one-or-more-selected-items-contain-a-data-type-that-is-not-supported-by-the-designer"></a>Co najmniej jeden wybrany element zawiera typ danych nieobsługiwany przez projektanta

Co najmniej jeden z elementów przeciągnięte z **Eksploratora serwera** lub **Eksplorator bazy danych** na **O/R Designer** zawiera typ danych, która nie jest obsługiwana przez **O / R designer**, na przykład [typy CLR zdefiniowane przez użytkownika](/dotnet/framework/data/adonet/sql/clr-user-defined-types).

## <a name="to-correct-this-error"></a>Aby poprawić ten błąd

1. Utwórz widok, który jest oparty na odpowiednią tabelę i nie zawiera nieobsługiwany typ danych.

2. Przeciągnij widok z **Eksploratora serwera** lub **Eksplorator bazy danych** do projektanta.

## <a name="see-also"></a>Zobacz także

- [Komunikaty narzędzia Object Relational Designer](../data-tools/o-r-designer-messages.md)
- [Narzędzi LINQ to SQL w programie Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)