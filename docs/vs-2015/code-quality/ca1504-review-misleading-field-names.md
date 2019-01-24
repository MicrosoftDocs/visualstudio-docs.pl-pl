---
title: 'CA1504: Przejrzyj mylące nazwy pól | Dokumentacja firmy Microsoft'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- ReviewMisleadingFieldNames
- CA1504
helpviewer_keywords:
- CA1504
- ReviewMisleadingFieldNames
ms.assetid: 94136ff1-4aaf-4dc2-9170-48c171ab7499
caps.latest.revision: 17
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 2203e99974e5f232e8c90badef7c28921b971cdb
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54764460"
---
# <a name="ca1504-review-misleading-field-names"></a>CA1504: Sprawdź pod kątem mylących nazw pól
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|ReviewMisleadingFieldNames|
|CheckId|CA1504|
|Kategoria|Microsoft.Maintainability|
|Zmiana kluczowa|Bez podziału|

## <a name="cause"></a>Przyczyna
 Nazwa pola wystąpienia zaczyna się od "s_" lub nazwa `static` (`Shared` w [!INCLUDE[vbprvb](../includes/vbprvb-md.md)]) pola rozpoczyna się od "m_".

## <a name="rule-description"></a>Opis reguły
 Nazwy pól, rozpoczynających się od "s_" są skojarzone z danymi statycznymi przez wielu użytkowników. Podobnie pola, których nazwy rozpoczynają "m_" są skojarzone z dane wystąpienia (członek). Kod, aby łatwiej utrzymać nazwy powinien być zgodny z powszechnie używanych Konwencji.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Aby naprawić naruszenie tej zasady, należy zmienić nazwę pola używając odpowiedniego prefiksu. Alternatywnie, Przekształć pole zgadza się z bieżącym sufiks, dodając lub usuwając `static` modyfikator.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Nie pomijaj ostrzeżeń dla tej reguły.
