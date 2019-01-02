---
title: 'CA1822: Oznaczaj składowe jako statyczne'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 7a566518d41a37e12ce20188bfe84c02a6cabcf9
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53890196"
---
# <a name="ca1822-mark-members-as-static"></a>CA1822: Oznaczaj składowe jako statyczne

|||
|-|-|
|TypeName|MarkMembersAsStatic|
|CheckId|CA1822|
|Kategoria|Microsoft.Performance|
|Zmiana kluczowa|Podziału non - Jeśli element członkowski nie jest widoczna spoza zestawu, niezależnie od tego, zmiany wprowadzone. Bez podziału — w przypadku tylko zmiany elementu członkowskiego do elementu członkowskiego wystąpienia z `this` — słowo kluczowe.<br /><br /> Przerywanie — Jeśli zmienisz element członkowski z elementu członkowskiego wystąpienia statyczną składową i jest on widoczny spoza zestawu.|

## <a name="cause"></a>Przyczyna
 Element członkowski, który nie uzyskać dostępu do danych wystąpienia nie jest oznaczony jako statyczne (współużytkowane w [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]).

## <a name="rule-description"></a>Opis reguły
 Elementy członkowskie, które nie uzyskuje dostępu do wystąpienia danych lub wywołanie metody wystąpienia mogą zostać oznaczone jako statyczne (współużytkowane w [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]). Po oznaczeniu metod jako statyczne kompilator wygeneruje niewirtualne wywołania do tych członków. Emitowanie niewirtualne wywołania uniemożliwi sprawdzanie w czasie wykonywania dla każdego wywołania, który sprawia, że bieżący wskaźnik do obiektu jest różna od null. Można to osiągnąć wymierny zysk wydajnościowy dla kodu wrażliwego na wydajność. W niektórych przypadkach błąd dostępu do bieżącego wystąpienia obiektu reprezentuje problem poprawności.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Oznacz składową jako statyczną (lub udostępniane w [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]) lub użyj "this" / "Me" w metodzie body, jeśli to stosowne.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Jest bezpieczne pominąć ostrzeżenie od tej reguły dla uprzednio wysłane kodu, dla których poprawki będą istotnej zmiany.

## <a name="related-rules"></a>Powiązane reguły
 [CA1811: Unikaj niewywołanego kodu prywatnego](../code-quality/ca1811-avoid-uncalled-private-code.md)

 [CA1812: Unikaj klas wewnętrznych bez wystąpień](../code-quality/ca1812-avoid-uninstantiated-internal-classes.md)

 [CA1804: Usuń nieużywane zmienne lokalne](../code-quality/ca1804-remove-unused-locals.md)