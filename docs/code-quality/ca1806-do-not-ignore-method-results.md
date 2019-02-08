---
title: 'CA1806: Nie ignoruj wyników metod'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA1806
- DoNotIgnoreMethodResults
helpviewer_keywords:
- CA1806
- DoNotIgnoreMethodResults
ms.assetid: fd805687-0817-481e-804e-b62cfb3b1076
author: gewarren
ms.author: gewarren
dev_langs:
- CPP
- CSharp
- VB
manager: jillfra
ms.openlocfilehash: d2a1dd9984601afa34e4aac7fa5ddc24061cf6ae
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2019
ms.locfileid: "55954507"
---
# <a name="ca1806-do-not-ignore-method-results"></a>CA1806: Nie ignoruj wyników metod

|||
|-|-|
|TypeName|DoNotIgnoreMethodResults|
|CheckId|CA1806|
|Kategoria|Microsoft.Usage|
|Zmiana kluczowa|Bez podziału|

## <a name="cause"></a>Przyczyna

Istnieje kilka możliwych przyczyn tego ostrzeżenia:

- Nowy obiekt jest utworzony, ale nigdy używane.

- Wywoływana jest metoda, która tworzy i zwraca nowy ciąg, a nowy ciąg nigdy nie jest używany.

- Metody COM lub P/Invoke, która zwraca wartość HRESULT lub kodu błędu, który nigdy nie jest używany. Opis reguły

Tworzenie obiektów niepotrzebne i skojarzonych elementów bezużytecznych nieużywane obiektu obniżyć wydajność.

Ciągów są niezmienne i metod, takich jak String.ToUpper zwraca nowe wystąpienie ciągu zamiast modyfikowania wystąpienie ciągu w przypadku wywołania metody.

Ignorowanie HRESULT lub kod błędu może prowadzić do nieoczekiwanego zachowania w warunkach błędu lub warunki zasobów.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Jeśli metoda tworzy nowe wystąpienie obiektu B, który nie jest nigdy używana, przekaż wystąpienie jako argument do innej metody lub Przypisz wystąpienie do zmiennej. Jeśli tworzenie obiektów nie jest konieczne, usuń go.- lub -

 Jeśli metoda wywołuje metodę B, ale nie używa nowego wystąpienia ciągu, które zwraca metoda B. Przekaż wystąpienie jako argument do innej metody, przypisz wystąpienie do zmiennej. Lub Usuń wywołanie funkcji, jeśli jest niepotrzebna.

 —lub—

 Jeśli metoda wywołuje metodę B, ale nie używa HRESULT lub kod błędu:, metoda zwraca. Użyj wyniku w instrukcji warunkowej, przypisz wynik do zmiennej lub przekaż go jako argument do innej metody.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Nie pomijaj ostrzeżeń dla tej reguły, chyba że pełni niektóre funkcje, akt tworzenia obiektu.

## <a name="example"></a>Przykład
 Poniższy przykład przedstawia klasę, która ignoruje wynik String.Trim wywoływania.

 [!code-csharp[FxCop.Usage.DoNotIgnoreMethodResults3#1](../code-quality/codesnippet/CSharp/ca1806-do-not-ignore-method-results_1.cs)]
 [!code-vb[FxCop.Usage.DoNotIgnoreMethodResults3#1](../code-quality/codesnippet/VisualBasic/ca1806-do-not-ignore-method-results_1.vb)]
 [!code-cpp[FxCop.Usage.DoNotIgnoreMethodResults3#1](../code-quality/codesnippet/CPP/ca1806-do-not-ignore-method-results_1.cpp)]

## <a name="example"></a>Przykład
 Poniższy przykład naprawia wcześniejszego naruszenia praw przez przypisywanie wynik String.Trim zmienną, która została wywołana na.

 [!code-csharp[FxCop.Usage.DoNotIgnoreMethodResults4#1](../code-quality/codesnippet/CSharp/ca1806-do-not-ignore-method-results_2.cs)]
 [!code-vb[FxCop.Usage.DoNotIgnoreMethodResults4#1](../code-quality/codesnippet/VisualBasic/ca1806-do-not-ignore-method-results_2.vb)]
 [!code-cpp[FxCop.Usage.DoNotIgnoreMethodResults4#1](../code-quality/codesnippet/CPP/ca1806-do-not-ignore-method-results_2.cpp)]

## <a name="example"></a>Przykład
 Poniższy przykład przedstawia metodę, która nie korzysta z obiektu, który tworzy.

> [!NOTE]
> Nie można odtworzyć to naruszenie w języku Visual Basic.

 [!code-cpp[FxCop.Usage.DoNotIgnoreMethodResults5#1](../code-quality/codesnippet/CPP/ca1806-do-not-ignore-method-results_3.cpp)]
 [!code-csharp[FxCop.Usage.DoNotIgnoreMethodResults5#1](../code-quality/codesnippet/CSharp/ca1806-do-not-ignore-method-results_3.cs)]

## <a name="example"></a>Przykład
 Poniższy przykład naprawia wcześniejszego naruszenia praw przez usunięcie niepotrzebnych tworzenia obiektu.

 [!code-csharp[FxCop.Usage.DoNotIgnoreMethodResults6#1](../code-quality/codesnippet/CSharp/ca1806-do-not-ignore-method-results_4.cs)]
 [!code-cpp[FxCop.Usage.DoNotIgnoreMethodResults6#1](../code-quality/codesnippet/CPP/ca1806-do-not-ignore-method-results_4.cpp)]

<!-- Examples don't exist for the below... -->
<!--
## Example
 The following example shows a method that ignores the error code that the native method GetShortPathName returns.

## Example
 The following example fixes the previous violation by checking the error code and throwing an exception when the call fails.
-->