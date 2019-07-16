---
title: 'CA2234: Przekazuj obiekty System.Uri zamiast ciągów | Dokumentacja firmy Microsoft'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- PassSystemUriObjectsInsteadOfStrings
- CA2234
helpviewer_keywords:
- CA2234
- PassSystemUriObjectsInsteadOfStrings
ms.assetid: 14616b37-74c4-4286-b051-115d00aceb5f
caps.latest.revision: 16
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: ce0ed8a2600d52d3a8f6649a528b6c809895f3fe
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "68142402"
---
# <a name="ca2234-pass-systemuri-objects-instead-of-strings"></a>CA2234: Przekazuj obiekty System.Uri zamiast ciągów
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|PassSystemUriObjectsInsteadOfStrings|
|CheckId|CA2234|
|Kategoria|Microsoft.Usage|
|Zmiana kluczowa|Bez podziału|

## <a name="cause"></a>Przyczyna
 Wykonano wywołanie do metody, która ma parametr typu ciąg, którego nazwa zawiera "uri", "Uri", "urn", "Urn", "url" lub "Url"; deklarujący typ metody zawiera odpowiadające przeciążenie metody, która ma <xref:System.Uri?displayProperty=fullName> parametru.

## <a name="rule-description"></a>Opis reguły
 Nazwa parametru jest podzielony na tokeny oparte na Konwencji camelcase, a następnie każdy token jest sprawdzane w celu sprawdzenia, czy jest ona równa "uri", "Uri", "urn", "Urn", "url" lub "Url". W przypadku dopasowania parametru zakłada, że do reprezentowania identyfikatora uniform resource identifier (URI). Reprezentacja ciągu identyfikatora URI jest podatna na analizowanie i kodowanie błędów i może prowadzić do powstawania luk w zabezpieczeniach. <xref:System.Uri> Klasa udostępnia te usługi w bezpieczny sposób. Gdy istnieje możliwość wyboru między dwa przeciążenia, które różnią się tylko do reprezentacji identyfikatora URI, użytkownik powinien wybrać przeciążenia, które przyjmuje <xref:System.Uri> argumentu.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Aby naprawić naruszenie tej zasady, należy wywołać przeciążenia, które przyjmuje <xref:System.Uri> argumentu.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Jest bezpieczne pominąć ostrzeżenie od tej reguły, jeśli parametr typu ciąg nie reprezentuje identyfikator URI.

## <a name="example"></a>Przykład
 W poniższym przykładzie pokazano metodę `ErrorProne`, który narusza regułę i metody `SaferWay`, który prawidłowo wywołuje <xref:System.Uri> przeciążenia.

 [!code-cpp[FxCop.Usage.PassUri#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Usage.PassUri/cpp/FxCop.Usage.PassUri.cpp#1)]
 [!code-csharp[FxCop.Usage.PassUri#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.PassUri/cs/FxCop.Usage.PassUri.cs#1)]
 [!code-vb[FxCop.Usage.PassUri#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.PassUri/vb/FxCop.Usage.PassUri.vb#1)]

## <a name="related-rules"></a>Powiązane reguły
 [CA1057: Przeciążenia identyfikatora URI ciągu wywołują przeciążenia System.Uri](../code-quality/ca1057-string-uri-overloads-call-system-uri-overloads.md)

 [CA1056: Właściwości identyfikatora URI nie powinny być ciągami](../code-quality/ca1056-uri-properties-should-not-be-strings.md)

 [CA1054: Parametry identyfikatora URI nie powinny być ciągami](../code-quality/ca1054-uri-parameters-should-not-be-strings.md)

 [CA1055: Identyfikator URI zwracanych wartości nie powinny być ciągami](../code-quality/ca1055-uri-return-values-should-not-be-strings.md)
