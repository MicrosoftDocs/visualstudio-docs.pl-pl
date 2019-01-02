---
title: 'CA1308: Normalizuj ciągi na wielkie litery | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology: vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- CA1308
- NormalizeStringsToUppercase
helpviewer_keywords:
- NormalizeStringsToUppercase
- CA1308
ms.assetid: 7e9a7457-3f93-4938-ac6f-1389fba8d9cc
caps.latest.revision: 13
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 6b2145b86da9cbc792b5baf16f19e94f24e148d5
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53913280"
---
# <a name="ca1308-normalize-strings-to-uppercase"></a>CA1308: Normalizuj ciągi na wielkie litery
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|NormalizeStringsToUppercase|
|CheckId|CA1308|
|Kategoria|Microsoft.Globalization|
|Zmiana kluczowa|Bez podziału|

## <a name="cause"></a>Przyczyna
 Operacja normalizuje ciąg na małe litery.

## <a name="rule-description"></a>Opis reguły
 Ciągi powinny być znormalizowane do użycia wielkich liter. Niewielkiej liczby znaków, gdy są konwertowane na małe litery, nie mogą wykonywać rund. Można wykonywać rund, sposób konwertowania znaków z ustawień regionalnych co do innej wersji regionalnej, który reprezentuje dane znakowe inaczej, a następnie do dokładnie pobierać oryginalne znaki z przekonwertowanego znaków.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Zmień operacje, które konwersji ciągów znaków na małe litery, tak aby ciągi są konwertowane na wielkie litery w zamian. Na przykład zmienić `String.ToLower(CultureInfo.InvariantCulture)` do `String.ToUpper(CultureInfo.InvariantCulture)`.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Jest to bezpieczne Pomiń komunikat ostrzegawczy, gdy nie wykonujesz decyzja dotycząca zabezpieczeń na podstawie wyniku (na przykład w przypadku wyświetlania go w interfejsie użytkownika).

## <a name="see-also"></a>Zobacz też
 [Ostrzeżenia dotyczące globalizacji](../code-quality/globalization-warnings.md)
