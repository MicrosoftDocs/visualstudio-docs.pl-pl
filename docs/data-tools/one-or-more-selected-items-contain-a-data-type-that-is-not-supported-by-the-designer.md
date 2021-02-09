---
title: Nieobsługiwany typ danych
description: Co najmniej jeden wybrany element zawiera typ danych, który nie jest obsługiwany przez projektanta. Wyświetl informacje o tym komunikacie projektanta programu Visual Studio O/R.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: error-reference
ms.assetid: 71dcd4f9-2946-42c5-9ce4-99c819ea2785
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- data-storage
ms.openlocfilehash: c50d47363217a87147275a406d5370cc8736c10b
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99866648"
---
# <a name="one-or-more-selected-items-contain-a-data-type-that-is-not-supported-by-the-designer"></a>Co najmniej jeden wybrany element zawiera typ danych nieobsługiwany przez projektanta

Jeden lub więcej elementów przeciąganych z **Eksplorator serwera** lub **Eksplorator bazy danych** do **projektanta o/r** zawiera typ danych, który nie jest obsługiwany przez **projektanta o/r**, na przykład [typy CLR zdefiniowane przez użytkownika](/dotnet/framework/data/adonet/sql/clr-user-defined-types).

## <a name="to-correct-this-error"></a>Aby poprawić ten błąd

1. Utwórz widok, który jest oparty na odpowiedniej tabeli i nie zawiera nieobsługiwanego typu danych.

2. Przeciągnij widok z **Eksplorator serwera** lub **Eksplorator bazy danych** do projektanta.

## <a name="see-also"></a>Zobacz też

- [Narzędzia LINQ to SQL w programie Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
