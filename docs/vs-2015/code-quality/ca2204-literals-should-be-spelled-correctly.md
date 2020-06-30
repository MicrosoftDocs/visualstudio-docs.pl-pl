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
ms.openlocfilehash: ecf829251cbeab600cb95f8f0c0b0173cd7338d4
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/30/2020
ms.locfileid: "85546279"
---
# <a name="ca2204-literals-should-be-spelled-correctly"></a>CA2204: Pisownia literałów powinna być poprawna
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Element|Wartość|
|-|-|
|TypeName|LiteralsShouldBeSpelledCorrectly|
|CheckId|CA2204|
|Kategoria|Microsoft. Usage|
|Zmiana kluczowa|Bez przerywania|

## <a name="cause"></a>Przyczyna
 Metoda przekazuje ciąg literału do, który jest używany w parametrze lub właściwości, która wymaga zlokalizowanego ciągu, a ciąg literału zawiera jeden lub więcej wyrazów, które nie są rozpoznawane przez bibliotekę sprawdzania pisowni firmy Microsoft.

## <a name="rule-description"></a>Opis reguły
 Ta reguła sprawdza ciąg literału, który jest przesyłany jako wartość do parametru lub właściwości, gdy spełniony jest co najmniej jeden z następujących przypadków:

- <xref:System.ComponentModel.LocalizableAttribute>Atrybut parametru lub właściwości jest ustawiony na wartość true.

- Nazwa parametru lub właściwości zawiera tekst "text", "Message" lub "Caption".

- Nazwa parametru ciągu, który jest przesyłany do konsoli. Write lub Console. WriteLine ma wartość "value" lub "format".

  Ta reguła analizuje ciąg literału w słowach, tokenizowanie wyrazy złożone i sprawdza pisownię każdego wyrazu/tokenu. Aby uzyskać informacje na temat algorytmu analizy, zobacz [CA1704: Identyfikatory powinny być poprawnie napisane](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md).

  Domyślnie używana jest wersja angielskojęzyczna (EN) modułu sprawdzania pisowni.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Aby naprawić naruszenie tej zasady, Popraw pisownię wyrazu lub Dodaj słowo do słownika niestandardowego. Aby uzyskać informacje o sposobach używania słowników niestandardowych, zobacz [How to: Dostosowywanie słownika analizy kodu](../code-quality/how-to-customize-the-code-analysis-dictionary.md).

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Nie pomijaj ostrzeżeń dla tej reguły. Prawidłowo napisane wyrazy zmniejszają krzywą szkoleniową wymaganą dla nowych bibliotek oprogramowania.

## <a name="related-rules"></a>Powiązane reguły
 [CA1704: Pisownia identyfikatorów powinna być poprawna](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md)

 [CA1703: Pisownia ciągów zasobów powinna być poprawna](../code-quality/ca1703-resource-strings-should-be-spelled-correctly.md)
