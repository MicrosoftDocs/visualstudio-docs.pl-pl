---
title: 'CA1504: Sprawdź pod kątem mylących nazw pól'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- ReviewMisleadingFieldNames
- CA1504
helpviewer_keywords:
- CA1504
- ReviewMisleadingFieldNames
ms.assetid: 94136ff1-4aaf-4dc2-9170-48c171ab7499
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: df6ab704c2dfdbf8ebdf8eb42f56d8d64600736f
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/09/2019
ms.locfileid: "68921824"
---
# <a name="ca1504-review-misleading-field-names"></a>CA1504: Sprawdź pod kątem mylących nazw pól

|||
|-|-|
|TypeName|ReviewMisleadingFieldNames|
|CheckId|CA1504|
|Kategoria|Microsoft. łatwość obsługi|
|Zmiana kluczowa|Nieprzerwanie|

## <a name="cause"></a>Przyczyna
Nazwa pola wystąpienia rozpoczyna się od "s_" lub nazwa `static` pola (`Shared` w [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]) rozpoczyna się od "m_".

## <a name="rule-description"></a>Opis reguły
Nazwy pól, które zaczynają się od "s_", są skojarzone z danymi statycznymi przez wielu użytkowników. Podobnie nazwy pól, które zaczynają się od "m_", są skojarzone z danymi wystąpienia (elementu członkowskiego). Aby łatwiej utrzymywać kod, nazwy powinny być zgodne z ogólnie używanymi konwencjami.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
Aby naprawić naruszenie tej zasady, Zmień nazwę pola przy użyciu odpowiedniego prefiksu. Alternatywnie, należy wyrazić zgodę na bieżący sufiks, dodając lub usuwając `static` modyfikator.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
Nie pomijaj ostrzeżeń dla tej reguły.