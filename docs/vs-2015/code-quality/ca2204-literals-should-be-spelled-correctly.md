---
title: 'CA2204: Literały powinny być zapisane poprawnie | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology: vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- Literals should be spelled correctly
- CA2204
- LiteralsShouldBeSpelledCorrectly
helpviewer_keywords:
- CA2204
ms.assetid: b0bbcbb6-c92d-4c14-8ef7-9c8b38c791a6
caps.latest.revision: 21
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 982fbb33e7b789944712dd334a1de1882d547ecd
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53939351"
---
# <a name="ca2204-literals-should-be-spelled-correctly"></a>CA2204: Literały powinny być zapisane poprawnie
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|LiteralsShouldBeSpelledCorrectly|
|CheckId|CA2204|
|Kategoria|Microsoft.Usage|
|Zmiana kluczowa|Bez podziału|

## <a name="cause"></a>Przyczyna
 Przebiegi metody, ciągiem literału, do którego jest używany w parametr lub właściwość, która wymaga zlokalizowany ciąg z ciągiem literału zawiera jeden lub więcej wyrazów, które nie są rozpoznawane przez bibliotekę sprawdzania pisowni Microsoft.

## <a name="rule-description"></a>Opis reguły
 Ta reguła sprawdza, czy ciąg literału, który jest przekazywany jako wartość parametru lub właściwości, gdy dla jednego lub więcej z następujących przypadków ma wartość true:

- <xref:System.ComponentModel.LocalizableAttribute> Atrybut parametru lub właściwość jest ustawiona na wartość true.

- Nazwa parametru lub właściwości zawiera "Text", "Message" lub "Podpis".

- Nazwa parametru ciągu, który jest przekazywany do metody Console.Write — lub elementu Console.WriteLine jest "value" lub "format".

  Ta reguła umożliwia przekształcanie ciągów literałów w wyrazy, tokenizowanie wyrazy złożone i sprawdza pisownię każdego wyrazu/tokenu. Aby uzyskać informacji na temat analizy algorytmu, zobacz [CA1704: Identyfikatory powinny być zapisane poprawnie](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md).

  Domyślnie używany jest język angielski (en) wersję modułu sprawdzania pisowni.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Aby naprawić naruszenie tej zasady, Popraw pisownię wyrazu, lub Dodaj ten wyraz do słownika niestandardowego. Aby uzyskać informacje o sposobie używania słowników niestandardowych, zobacz [jak: Dostosowywanie słownika analizy kodu](../code-quality/how-to-customize-the-code-analysis-dictionary.md).

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Nie pomijaj ostrzeżeń dla tej reguły. Poprawnie właściwej słów zmniejszyć nauki wymagany dla nowe biblioteki oprogramowania.

## <a name="related-rules"></a>Powiązane reguły
 [CA1704: Identyfikatory powinny być zapisane poprawnie](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md)

 [CA1703: Ciągi zasobów, które powinny być zapisane poprawnie](../code-quality/ca1703-resource-strings-should-be-spelled-correctly.md)
