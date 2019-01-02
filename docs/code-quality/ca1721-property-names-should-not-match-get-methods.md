---
title: 'CA1721: Nazwy właściwości nie powinny odpowiadać metody get'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- CA1721
- PropertyNamesShouldNotMatchGetMethods
helpviewer_keywords:
- CA1721
- PropertyNamesShouldNotMatchGetMethods
ms.assetid: 45a0e853-1f06-4688-af1b-cc634409e295
author: gewarren
ms.author: gewarren
manager: douge
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: e0b9c348fc9131ede355c58408b517d20ed2500b
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53920981"
---
# <a name="ca1721-property-names-should-not-match-get-methods"></a>CA1721: Nazwy właściwości nie powinny odpowiadać metody get

|||
|-|-|
|TypeName|PropertyNamesShouldNotMatchGetMethods|
|CheckId|CA1721|
|Kategoria|Microsoft.Naming|
|Zmiana kluczowa|Kluczowa|

## <a name="cause"></a>Przyczyna
 Nazwa publicznego lub chronionego elementu członkowskiego zaczyna się od "Get" i odpowiada nazwie właściwości publicznej lub chronionej. Na przykład typ, który zawiera metodę o nazwie "Getcolor —" i właściwość, która nosi nazwę "Color" narusza tę regułę.

## <a name="rule-description"></a>Opis reguły
 Metody GET i właściwości powinny mieć nazwy, które wyraźnie odróżniają ich funkcje.

 Konwencje nazewnictwa Obejmij wygląd wspólnych bibliotek obiektu docelowego środowiska uruchomieniowego języka wspólnego. Ten spójności skraca czas, są wymagane, aby dowiedzieć się nowa Biblioteka oprogramowania, która zwiększa poziom zaufania klientów, że biblioteka został opracowany przez osobę, która ma doświadczenie w tworzenie kodu zarządzanego.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Zmień nazwę, tak aby nazwę metody, która jest poprzedzony znakiem "Get" nie pasuje.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Nie pomijaj ostrzeżeń dla tej reguły.

> [!NOTE]
> To ostrzeżenie, mogą zostać wyłączone, jeśli metoda Get jest spowodowany przez zaimplementowanie interfejsu iextenderprovider —.

## <a name="example"></a>Przykład
 Poniższy przykład zawiera metody i właściwości, które spełniają tej reguły.

 [!code-csharp[FxCop.Naming.GetMethod#1](../code-quality/codesnippet/CSharp/ca1721-property-names-should-not-match-get-methods_1.cs)]
 [!code-vb[FxCop.Naming.GetMethod#1](../code-quality/codesnippet/VisualBasic/ca1721-property-names-should-not-match-get-methods_1.vb)]

## <a name="related-rules"></a>Powiązane reguły
 [CA1024: Korzystanie z właściwości, gdzie jest to odpowiednie](../code-quality/ca1024-use-properties-where-appropriate.md)