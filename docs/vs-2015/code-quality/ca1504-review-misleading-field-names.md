---
title: 'CA1504: Przejrzyj mylące nazwy pól | Microsoft Docs'
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
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: c3f1cca5dd33047a4d19c78013dd535e0e9dd6f2
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72607752"
---
# <a name="ca1504-review-misleading-field-names"></a>CA1504: Przegląd mylących nazw pól
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|ReviewMisleadingFieldNames|
|CheckId|CA1504|
|Kategoria|Microsoft. łatwość obsługi|
|Zmiana kluczowa|Nieprzerwanie|

## <a name="cause"></a>Przyczyna
 Nazwa pola wystąpienia rozpoczyna się od "s_" lub nazwy `static` (`Shared` w [!INCLUDE[vbprvb](../includes/vbprvb-md.md)]) rozpoczyna się od "m_".

## <a name="rule-description"></a>Opis reguły
 Nazwy pól, które zaczynają się od "s_", są skojarzone z danymi statycznymi przez wielu użytkowników. Podobnie nazwy pól, które zaczynają się od "m_", są skojarzone z danymi wystąpienia (elementu członkowskiego). Aby łatwiej utrzymywać kod, nazwy powinny być zgodne z ogólnie używanymi konwencjami.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Aby naprawić naruszenie tej zasady, Zmień nazwę pola przy użyciu odpowiedniego prefiksu. Alternatywnie, należy wyrazić zgodę na bieżący sufiks poprzez dodanie lub usunięcie modyfikatora `static`.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Nie pomijaj ostrzeżeń dla tej reguły.
