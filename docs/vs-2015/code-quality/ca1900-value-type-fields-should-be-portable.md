---
title: 'CA1900: pola typu wartości powinny być przenośne | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1900
- ValueTypeFieldsShouldBePortable
helpviewer_keywords:
- ValueTypeFieldsShouldBePortable
- CA1900
ms.assetid: 1787d371-389f-4d39-b305-12b53bc0dfb9
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 23b5705b7ee81e56945050fe63dd2f086894bd08
ms.sourcegitcommit: 939407118f978162a590379997cb33076c57a707
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/13/2020
ms.locfileid: "75917931"
---
# <a name="ca1900-value-type-fields-should-be-portable"></a>CA1900: Pola o typie wartości powinny być przenośne
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Aby uzyskać najnowszą dokumentację programu Visual Studio, zobacz [CA1900: pole typu wartości powinno być przenośne](/visualstudio/code-quality/ca1900-value-type-fields-should-be-portable).

|||
|-|-|
|TypeName|ValueTypeFieldsShouldBePortable|
|CheckId|CA1900|
|Kategoria|Microsoft. przenośność|
|Zmiana kluczowa|Przerywanie — Jeśli pole może być widoczne poza zestawem.<br /><br /> Bez przerywania — Jeśli pole nie jest widoczne poza zestawem.|

## <a name="cause"></a>Przyczyna
 Ta reguła sprawdza, czy struktury zadeklarowane za pomocą jawnego układu są wyrównane prawidłowo, gdy są przekazywane do kodu niezarządzanego w 64-bitowych systemach operacyjnych. IA-64 nie zezwala na niewyrównany dostęp do pamięci, a proces zostanie rozwiązany, jeśli to naruszenie nie zostanie naprawione.

## <a name="rule-description"></a>Opis reguły
 Struktury, które mają jawny układ, który zawiera niewyrównane pola, powodują awarie w 64-bitowych systemach operacyjnych.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Wszystkie pola, które są mniejsze niż 8 bajtów, muszą mieć przesunięcia, które są wielokrotnością rozmiaru, a pola, które mają 8 bajtów lub więcej, muszą mieć przesunięcia, które są wielokrotnością 8. Innym rozwiązaniem jest użycie `LayoutKind.Sequential` zamiast `LayoutKind.Explicit`, jeśli jest to uzasadnione.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 To ostrzeżenie powinno być pomijane tylko wtedy, gdy wystąpi błąd.
