---
title: 'CA1308: Normalizuj ciągi na wielkie litery | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1308
- NormalizeStringsToUppercase
helpviewer_keywords:
- NormalizeStringsToUppercase
- CA1308
ms.assetid: 7e9a7457-3f93-4938-ac6f-1389fba8d9cc
caps.latest.revision: 13
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: dfe8495184bf4daadb3bf8899ee2857a9743c842
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72661387"
---
# <a name="ca1308-normalize-strings-to-uppercase"></a>CA1308: Znormalizuj ciągi na wielkie litery
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|NormalizeStringsToUppercase|
|CheckId|CA1308|
|Kategoria|Microsoft. Globalizacja|
|Zmiana kluczowa|Nieprzerwanie|

## <a name="cause"></a>Przyczyna
 Operacja normalizuje ciąg do małych liter.

## <a name="rule-description"></a>Opis reguły
 Ciągi powinny być znormalizowane do użycia wielkich liter. Niewielka grupa znaków, gdy są konwertowane na małe litery, nie może przekonywać rundy. Aby przeznaczyć na rundę, można przekonwertować znaki z jednego ustawienia regionalnego na inne ustawienia regionalne, które reprezentują dane znakowe w różny sposób, a następnie w celu dokładnego pobrania oryginalnych znaków z konwertowanych znaków.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Zmień operacje, które konwertują ciągi na małe litery, aby ciągi były konwertowane na wielkie litery. Na przykład zmień `String.ToLower(CultureInfo.InvariantCulture)` na `String.ToUpper(CultureInfo.InvariantCulture)`.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Można bezpiecznie pominąć komunikat ostrzegawczy, gdy nie podejmowana jest decyzja o zabezpieczeniach na podstawie wyniku (na przykład gdy jest wyświetlany w interfejsie użytkownika).

## <a name="see-also"></a>Zobacz też
 [Ostrzeżenia dotyczące globalizacji](../code-quality/globalization-warnings.md)
