---
title: 'CA1504: Sprawdź pod kątem mylących nazw pól'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
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
ms.openlocfilehash: da99bab4235028f75146be1807162e93759d3eb9
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "54926465"
---
# <a name="ca1504-review-misleading-field-names"></a>CA1504: Sprawdź pod kątem mylących nazw pól

|||
|-|-|
|TypeName|ReviewMisleadingFieldNames|
|CheckId|CA1504|
|Kategoria|Microsoft.Maintainability|
|Zmiana kluczowa|Bez podziału|

## <a name="cause"></a>Przyczyna
 Nazwa pola wystąpienia zaczyna się od "s_" lub nazwa `static` (`Shared` w [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]) pola rozpoczyna się od "m_".

## <a name="rule-description"></a>Opis reguły
 Nazwy pól, rozpoczynających się od "s_" są skojarzone z danymi statycznymi przez wielu użytkowników. Podobnie pola, których nazwy rozpoczynają "m_" są skojarzone z dane wystąpienia (członek). Kod, aby łatwiej utrzymać nazwy powinien być zgodny z powszechnie używanych Konwencji.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Aby naprawić naruszenie tej zasady, należy zmienić nazwę pola używając odpowiedniego prefiksu. Alternatywnie, Przekształć pole zgadza się z bieżącym sufiks, dodając lub usuwając `static` modyfikator.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Nie pomijaj ostrzeżeń dla tej reguły.