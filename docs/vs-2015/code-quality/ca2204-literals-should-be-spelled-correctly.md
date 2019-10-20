---
title: 'CA2204: literały powinny być poprawnie napisane | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- Literals should be spelled correctly
- CA2204
- LiteralsShouldBeSpelledCorrectly
helpviewer_keywords:
- CA2204
ms.assetid: b0bbcbb6-c92d-4c14-8ef7-9c8b38c791a6
caps.latest.revision: 21
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: d3e94f308936f898e555b1ad38e6a9d50051a276
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72659541"
---
# <a name="ca2204-literals-should-be-spelled-correctly"></a>CA2204: Literały powinny być napisane poprawnie
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|LiteralsShouldBeSpelledCorrectly|
|CheckId|CA2204|
|Kategoria|Microsoft. Usage|
|Zmiana kluczowa|Bez przerywania|

## <a name="cause"></a>Przyczyna
 Metoda przekazuje ciąg literału do, który jest używany w parametrze lub właściwości, która wymaga zlokalizowanego ciągu, a ciąg literału zawiera jeden lub więcej wyrazów, które nie są rozpoznawane przez bibliotekę sprawdzania pisowni firmy Microsoft.

## <a name="rule-description"></a>Opis reguły
 Ta reguła sprawdza ciąg literału, który jest przesyłany jako wartość do parametru lub właściwości, gdy spełniony jest co najmniej jeden z następujących przypadków:

- Atrybut <xref:System.ComponentModel.LocalizableAttribute> parametru lub właściwości jest ustawiony na wartość true.

- Nazwa parametru lub właściwości zawiera tekst "text", "Message" lub "Caption".

- Nazwa parametru ciągu, który jest przesyłany do konsoli. Write lub Console. WriteLine ma wartość "value" lub "format".

  Ta reguła analizuje ciąg literału w słowach, tokenizowanie wyrazy złożone i sprawdza pisownię każdego wyrazu/tokenu. Aby uzyskać informacje na temat algorytmu analizy, zobacz [CA1704: Identyfikatory powinny być poprawnie napisane](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md).

  Domyślnie używana jest wersja angielskojęzyczna (EN) modułu sprawdzania pisowni.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Aby naprawić naruszenie tej zasady, Popraw pisownię wyrazu lub Dodaj słowo do słownika niestandardowego. Aby uzyskać informacje o sposobach używania słowników niestandardowych, zobacz [How to: Dostosowywanie słownika analizy kodu](../code-quality/how-to-customize-the-code-analysis-dictionary.md).

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Nie pomijaj ostrzeżeń dla tej reguły. Prawidłowo napisane wyrazy zmniejszają krzywą szkoleniową wymaganą dla nowych bibliotek oprogramowania.

## <a name="related-rules"></a>Powiązane reguły
 [CA1704: Identyfikatory powinny być zapisane poprawnie](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md)

 [CA1703: Ciągi zasobu powinny być zapisane poprawnie](../code-quality/ca1703-resource-strings-should-be-spelled-correctly.md)
