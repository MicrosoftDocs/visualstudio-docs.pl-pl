---
title: 'CA1721: nazwy właściwości nie powinny odpowiadać metodom Get | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1721
- PropertyNamesShouldNotMatchGetMethods
helpviewer_keywords:
- CA1721
- PropertyNamesShouldNotMatchGetMethods
ms.assetid: 45a0e853-1f06-4688-af1b-cc634409e295
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 366932c83328c6810e0103308db1c73a3e3076cb
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72671607"
---
# <a name="ca1721-property-names-should-not-match-get-methods"></a>CA1721: Nazwy właściwości nie powinny odpowiadać metodom Get
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|PropertyNamesShouldNotMatchGetMethods|
|CheckId|CA1721|
|Kategoria|Microsoft. nazewnictwo|
|Zmiana kluczowa|Kluczowa|

## <a name="cause"></a>Przyczyna
 Nazwa publicznego lub chronionego elementu członkowskiego rozpoczyna się od "Get", w przeciwnym razie jest zgodna z nazwą właściwości publicznej lub chronionej. Na przykład typ, który zawiera metodę o nazwie "GetColor" i właściwość o nazwie "Color" narusza tę regułę.

## <a name="rule-description"></a>Opis reguły
 Metody get i Properties powinny mieć nazwy, które wyraźnie odróżniają funkcję.

 Konwencje nazewnictwa zapewniają typowy wygląd bibliotek przeznaczonych dla środowiska uruchomieniowego języka wspólnego. Pozwala to skrócić czas wymagany do nauczenia się nowej biblioteki oprogramowania i zwiększyć zaufanie klienta, że biblioteka została opracowana przez kogoś, kto ma doświadczenie w tworzeniu kodu zarządzanego.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Zmień nazwę tak, aby nie odpowiadała nazwie metody poprzedzonej prefiksem "Get".

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Nie pomijaj ostrzeżeń dla tej reguły.

> [!NOTE]
> To ostrzeżenie może zostać wykluczone, jeśli metoda get jest spowodowana przez implementację interfejsu interfejsu IExtenderProvider.

## <a name="example"></a>Przykład
 Poniższy przykład zawiera metodę i właściwość, która narusza tę regułę.

 [!code-csharp[FxCop.Naming.GetMethod#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Naming.GetMethod/cs/FxCop.Naming.GetMethod.cs#1)]
 [!code-vb[FxCop.Naming.GetMethod#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Naming.GetMethod/vb/FxCop.Naming.GetMethod.vb#1)]

## <a name="related-rules"></a>Powiązane reguły
 [CA1024: Używaj właściwości wszędzie tam, gdzie jest to odpowiednie](../code-quality/ca1024-use-properties-where-appropriate.md)
