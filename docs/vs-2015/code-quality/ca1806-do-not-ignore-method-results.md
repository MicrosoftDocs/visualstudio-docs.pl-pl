---
title: 'CA1806: nie Ignoruj wyników metody | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1806
- DoNotIgnoreMethodResults
helpviewer_keywords:
- CA1806
- DoNotIgnoreMethodResults
ms.assetid: fd805687-0817-481e-804e-b62cfb3b1076
caps.latest.revision: 27
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 726cde42eb08ee5508481887fae2e9d2b059256c
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/30/2020
ms.locfileid: "85543874"
---
# <a name="ca1806-do-not-ignore-method-results"></a>CA1806: Nie ignoruj wyników metod
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Element|Wartość|
|-|-|
|TypeName|DoNotIgnoreMethodResults|
|CheckId|CA1806|
|Kategoria|Microsoft. Usage|
|Zmiana kluczowa|Bez przerywania|

## <a name="cause"></a>Przyczyna
 Istnieje kilka możliwych przyczyn tego ostrzeżenia:

- Nowy obiekt jest tworzony, ale nigdy nie jest używany.

- Metoda, która tworzy i zwraca nowy ciąg, jest wywoływana i nowy ciąg nigdy nie jest używany.

- Metoda COM lub P/Invoke zwracająca wartość HRESULT lub kod błędu, który nigdy nie jest używany. Opis reguły

  Niepotrzebne utworzenie obiektu i powiązane wyrzucanie elementów bezużytecznych nieużywanego obiektu.

  Ciągi są niezmienne i metody, takie jak String. ToUpper zwraca nowe wystąpienie ciągu, zamiast modyfikować wystąpienie ciągu w metodzie wywołującej.

  Zignorowanie HRESULT lub kod błędu może prowadzić do nieoczekiwanego zachowania w warunkach błędów lub w warunkach niskiego zasobu.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Jeśli metoda A tworzy nowe wystąpienie obiektu B, które nigdy nie jest używane, Przekaż wystąpienie jako argument do innej metody lub Przypisz wystąpienie do zmiennej. Jeśli Tworzenie obiektu jest niepotrzebne, usuń go.-lub-

 Jeśli metoda A wywołuje metodę B, ale nie używa nowego wystąpienia ciągu zwracanego przez metodę B. Przekaż wystąpienie jako argument do innej metody, przypisz wystąpienie do zmiennej. Lub Usuń wywołanie, jeśli jest niepotrzebne.

 -lub-

 Jeśli metoda A wywołuje metodę B, ale nie korzysta z kodu HRESULT lub Error zwracanego przez metodę. Użyj wyniku w instrukcji warunkowej, przypisz wynik do zmiennej lub Przekaż go jako argument do innej metody.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Nie pomijaj ostrzeżenia z tej reguły, chyba że czynność tworzenia obiektu nie ma pewnego celu.

## <a name="example"></a>Przykład
 W poniższym przykładzie pokazano klasę, która ignoruje wynik wywołania metody String. Trim.

<!-- TODO: review snippet reference  [!CODE [FxCop.Usage.DoNotIgnoreMethodResults#1](FxCop.Usage.DoNotIgnoreMethodResults#1)]  -->

## <a name="example"></a>Przykład
 Poniższy przykład naprawia poprzednie naruszenie, przypisując wynik ciągu. Odwróć do zmiennej, w której został wywołany.

<!-- TODO: review snippet reference  [!CODE [FxCop.Usage.DoNotIgnoreMethodResults2#1](FxCop.Usage.DoNotIgnoreMethodResults2#1)]  -->

## <a name="example"></a>Przykład
 Poniższy przykład przedstawia metodę, która nie korzysta z tworzonego obiektu.

> [!NOTE]
> Nie można odtworzyć tego naruszenia w Visual Basic.

 [!code-cpp[FxCop.Usage.DoNotIgnoreMethodResults3#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Usage.DoNotIgnoreMethodResults3/cpp/FxCop.Usage.DoNotIgnoreMethodResults3.cpp#1)]
 [!code-csharp[FxCop.Usage.DoNotIgnoreMethodResults3#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.DoNotIgnoreMethodResults3/cs/FxCop.Usage.DoNotIgnoreMethodResults3.cs#1)]
 [!code-vb[FxCop.Usage.DoNotIgnoreMethodResults3#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.DoNotIgnoreMethodResults3/vb/FxCop.Usage.DoNotIgnoreMethodResults3.vb#1)]

## <a name="example"></a>Przykład
 Poniższy przykład naprawia poprzednie naruszenie przez usunięcie niepotrzebnego utworzenia obiektu.

 [!code-cpp[FxCop.Usage.DoNotIgnoreMethodResults4#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Usage.DoNotIgnoreMethodResults4/cpp/FxCop.Usage.DoNotIgnoreMethodResults4.cpp#1)]
 [!code-csharp[FxCop.Usage.DoNotIgnoreMethodResults4#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.DoNotIgnoreMethodResults4/cs/FxCop.Usage.DoNotIgnoreMethodResults4.cs#1)]
 [!code-vb[FxCop.Usage.DoNotIgnoreMethodResults4#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.DoNotIgnoreMethodResults4/vb/FxCop.Usage.DoNotIgnoreMethodResults4.vb#1)]

## <a name="example"></a>Przykład
 Poniższy przykład przedstawia metodę, która ignoruje kod błędu, który zwraca metoda natywna GetShortPathName.

 [!code-cpp[FxCop.Usage.DoNotIgnoreMethodResults5#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Usage.DoNotIgnoreMethodResults5/cpp/FxCop.Usage.DoNotIgnoreMethodResults5.cpp#1)]
 [!code-csharp[FxCop.Usage.DoNotIgnoreMethodResults5#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.DoNotIgnoreMethodResults5/cs/FxCop.Usage.DoNotIgnoreMethodResults5.cs#1)]

## <a name="example"></a>Przykład
 Poniższy przykład naprawia poprzednie naruszenie przez sprawdzenie kodu błędu i zgłaszanie wyjątku, gdy wywołanie nie powiedzie się.

 [!code-cpp[FxCop.Usage.DoNotIgnoreMethodResults6#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Usage.DoNotIgnoreMethodResults6/cpp/FxCop.Usage.DoNotIgnoreMethodResults6.cpp#1)]
 [!code-csharp[FxCop.Usage.DoNotIgnoreMethodResults6#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.DoNotIgnoreMethodResults6/cs/FxCop.Usage.DoNotIgnoreMethodResults6.cs#1)]