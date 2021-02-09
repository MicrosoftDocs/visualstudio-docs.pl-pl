---
title: Nie można usunąć właściwości
description: Nie można usunąć właściwości. Wyświetl informacje o tym komunikacie Object Relational Designer programu Visual Studio (Projektant O/R).
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: error-reference
ms.assetid: 55873f74-7834-4ec1-8815-eeeb65618d87
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- data-storage
ms.openlocfilehash: 03d9fa4368251ec36dad8f791f033fdce1f71adb
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99858335"
---
# <a name="the-property-property-name-cannot-be-deleted"></a>Właściwości \<property name> nie można usunąć

\<property name>Nie można usunąć właściwości, ponieważ jest ona ustawiona jako **właściwość rozróżniacza** dla dziedziczenia między \<class name> i\<class name>

Wybrana właściwość jest ustawiana jako **właściwość rozróżniacza** dla dziedziczenia między klasami wskazanymi w komunikacie o błędzie. Nie można usunąć właściwości, jeśli uczestniczą w konfiguracji dziedziczenia między klasami danych.

Ustaw **Właściwość dyskryminatora** na inną właściwość klasy danych, aby umożliwić pomyślne usunięcie żądanej właściwości.

## <a name="to-correct-this-error"></a>Aby poprawić ten błąd

1. W **projektancie o/R** wybierz linię dziedziczenia, która łączy klasy danych wskazane w komunikacie o błędzie.

2. Ustaw właściwość **dyskryminatora** na inną właściwość.

3. Spróbuj ponownie usunąć właściwość.

## <a name="see-also"></a>Zobacz też

- [Narzędzia LINQ to SQL w programie Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)