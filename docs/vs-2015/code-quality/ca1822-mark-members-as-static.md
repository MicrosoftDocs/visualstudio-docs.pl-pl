---
title: 'CA1822: Oznacz składowe jako statyczne | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- MarkMembersAsStatic
- CA1822
helpviewer_keywords:
- MarkMembersAsStatic
- CA1822
ms.assetid: 743f0af7-41d1-4852-8d97-af0688b31118
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 2416eb24c21ef0e61bdb6db3de66c892e1eb699f
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/30/2020
ms.locfileid: "85545343"
---
# <a name="ca1822-mark-members-as-static"></a>CA1822: Oznaczaj składowe jako statyczne
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Aby uzyskać najnowszą dokumentację programu Visual Studio, zobacz [CA1822: Mark Members as static](/visualstudio/code-quality/ca1822-mark-members-as-static).

|Element|Wartość|
|-|-|
|TypeName|MarkMembersAsStatic|
|CheckId|CA1822|
|Kategoria|Microsoft. Performance|
|Zmiana kluczowa|Rozdzielenie — Jeśli element członkowski nie jest widoczny poza zestawem, niezależnie od wprowadzonej zmiany.<br /><br /> Rozdzielenie — Jeśli po prostu zmienisz element członkowski na wystąpienie z `this` słowem kluczowym.<br /><br /> Przerywanie — Jeśli element członkowski zostanie zmieniony z elementu członkowskiego wystąpienia na statyczny element członkowski i będzie widoczny poza zestawem.|

## <a name="cause"></a>Przyczyna
 Członek, który nie ma dostępu do danych wystąpienia, nie jest oznaczony jako static (Shared in [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] ).

## <a name="rule-description"></a>Opis reguły
 Elementy członkowskie, które nie uzyskują dostępu do danych wystąpienia lub wywołania metody wystąpienia, mogą być oznaczone jako statyczne (udostępnione w [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] ). Po oznaczeniu metod jako statyczne kompilator wygeneruje niewirtualne wywołania do tych członków. Emitowanie niewirtualnych witryn wywołań uniemożliwi sprawdzenie w czasie wykonywania każdego wywołania, które sprawdza, czy bieżący wskaźnik obiektu jest inny niż null. Pozwala to osiągnąć wymierny wzrost wydajności dla kodu wrażliwego na wydajność. W niektórych przypadkach niepowodzenie dostępu do bieżącego wystąpienia obiektu reprezentuje problem z poprawnym.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Oznacz element członkowski jako statyczny (lub udostępniony [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] ) albo użyj "This"/"Me" w treści metody, jeśli jest to konieczne.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Można bezpiecznie pominąć ostrzeżenie z tej reguły dla wcześniej dostarczonego kodu, dla którego poprawka byłaby istotną zmianą.

## <a name="related-rules"></a>Powiązane reguły
 [CA1811: Unikaj niewywołanego kodu prywatnego](../code-quality/ca1811-avoid-uncalled-private-code.md)

 [CA1812: Unikaj klas wewnętrznych bez wystąpień](../code-quality/ca1812-avoid-uninstantiated-internal-classes.md)

 [CA1804: Usuwaj nieużywane zmienne lokalne](../code-quality/ca1804-remove-unused-locals.md)
