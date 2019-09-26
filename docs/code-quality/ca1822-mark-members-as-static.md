---
title: 'CA1822: Oznaczaj składowe jako statyczne'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- MarkMembersAsStatic
- CA1822
helpviewer_keywords:
- MarkMembersAsStatic
- CA1822
ms.assetid: 743f0af7-41d1-4852-8d97-af0688b31118
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7ebbbbe01f1dd23dfc560e019133dacd3517b388
ms.sourcegitcommit: e98db44f3a33529b0ba188d24390efd09e548191
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/25/2019
ms.locfileid: "71253451"
---
# <a name="ca1822-mark-members-as-static"></a>CA1822: Oznaczaj składowe jako statyczne

|||
|-|-|
|TypeName|MarkMembersAsStatic|
|CheckId|CA1822|
|Kategoria|Microsoft.Performance|
|Zmiana podziału|Rozdzielenie — Jeśli element członkowski nie jest widoczny poza zestawem, niezależnie od wprowadzonej zmiany. Rozdzielenie — Jeśli po prostu zmienisz element członkowski na wystąpienie z `this` słowem kluczowym.<br /><br /> Przerywanie — Jeśli element członkowski zostanie zmieniony z elementu członkowskiego wystąpienia na statyczny element członkowski i będzie widoczny poza zestawem.|

## <a name="cause"></a>Przyczyna
Członek, który nie ma dostępu do danych wystąpienia, nie jest oznaczony jako static ( [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]Shared in).

## <a name="rule-description"></a>Opis reguły
Elementy członkowskie, które nie uzyskuje dostępu do wystąpienia danych lub wywołanie metody wystąpienia mogą zostać oznaczone jako statyczne (współużytkowane w [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]). Po oznaczeniu metod jako statyczne kompilator wygeneruje niewirtualne wywołania do tych członków. Emitowanie niewirtualnych witryn wywołań uniemożliwi sprawdzenie w czasie wykonywania każdego wywołania, które sprawdza, czy bieżący wskaźnik obiektu jest inny niż null. Pozwala to osiągnąć wymierny wzrost wydajności dla kodu wrażliwego na wydajność. W niektórych przypadkach niepowodzenie dostępu do bieżącego wystąpienia obiektu reprezentuje problem z poprawnym.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
Oznacz element członkowski jako statyczny (lub udostępniony [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]) albo użyj "This"/"Me" w treści metody, jeśli jest to konieczne.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
Można bezpiecznie pominąć ostrzeżenie z tej reguły dla wcześniej dostarczonego kodu, dla którego poprawka byłaby istotną zmianą.

## <a name="related-rules"></a>Powiązane reguły
[CA1811: Unikaj niewywołanego kodu prywatnego](../code-quality/ca1811-avoid-uncalled-private-code.md)

[CA1812: Unikaj klas wewnętrznych bez wystąpień](../code-quality/ca1812-avoid-uninstantiated-internal-classes.md)

[CA1804: Usuń nieużywane elementy lokalne](../code-quality/ca1804-remove-unused-locals.md)