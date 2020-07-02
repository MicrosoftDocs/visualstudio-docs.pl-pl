---
title: 'CA1059: elementy członkowskie nie powinny ujawniać niektórych typów konkretnych | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1059
- MembersShouldNotExposeCertainConcreteTypes
helpviewer_keywords:
- MembersShouldNotExposeCertainConcreteTypes
- CA1059
ms.assetid: 59f61f52-8d6c-49cb-aefb-191910523a3c
caps.latest.revision: 20
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 792426615dd78241ade1d38a24ec1f4d5702cede
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/30/2020
ms.locfileid: "85545382"
---
# <a name="ca1059-members-should-not-expose-certain-concrete-types"></a>CA1059: Składowe nie powinny ujawniać niektórych typów konkretnych
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Element|Wartość|
|-|-|
|TypeName|MembersShouldNotExposeCertainConcreteTypes|
|CheckId|CA1059|
|Kategoria|Microsoft. Design|
|Zmiana kluczowa|Kluczowa|

## <a name="cause"></a>Przyczyna
 Widoczny na zewnątrz element członkowski jest określonym konkretnym typem lub uwidacznia niektóre konkretne typy za pomocą jednego z jego parametrów lub zwracanych wartości. Obecnie ta reguła zgłasza narażenie następujących typów konkretnych:

- Typ pochodzący od <xref:System.Xml.XmlNode?displayProperty=fullName> .

## <a name="rule-description"></a>Opis reguły
 Konkretny typ jest typem posiadającym pełną implementację i dlatego może zostać utworzone jego wystąpienie. Aby umożliwić szerokie korzystanie z elementu członkowskiego, Zastąp konkretny typ proponowanym interfejsem. Dzięki temu członek może zaakceptować dowolny typ implementujący interfejs lub użyć, gdzie oczekiwany jest typ implementujący interfejs.

 Poniższa tabela zawiera listę konkretnych określonych typów i ich sugerowanych zamienników.

|Typ konkretny|Funkcja zastępująca|
|-------------------|-----------------|
|<xref:System.Xml.XPath.XPathDocument>|<xref:System.Xml.XPath.IXPathNavigable?displayProperty=fullName>.<br /><br /> Użycie interfejsu oddziela element członkowski od określonej implementacji źródła danych XML.|

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Aby naprawić naruszenie tej reguły, Zmień konkretny typ na sugerowany interfejs.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Można bezpiecznie pominąć komunikat z tej reguły, jeśli wymagane są określone funkcje dostarczone przez konkretny typ.

## <a name="related-rules"></a>Powiązane reguły
 [CA1011: Rozważ przekazywanie typów podstawowych jako parametrów](../code-quality/ca1011-consider-passing-base-types-as-parameters.md)
