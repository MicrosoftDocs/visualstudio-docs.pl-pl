---
title: 'CA2213: Pola możliwe do likwidacji należy likwidować'
ms.date: 05/14/2019
ms.topic: reference
f1_keywords:
- DisposableFieldsShouldBeDisposed
- CA2213
helpviewer_keywords:
- CA2213
- DisposableFieldsShouldBeDisposed
ms.assetid: e99442c9-70e2-47f3-b61a-d8ac003bc6e5
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1838d7e57b841c932d95006d1ff33972dd7a1a1f
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/24/2019
ms.locfileid: "71231609"
---
# <a name="ca2213-disposable-fields-should-be-disposed"></a>CA2213: Pola możliwe do likwidacji należy likwidować

|||
|-|-|
|TypeName|DisposableFieldsShouldBeDisposed|
|CheckId|CA2213|
|Kategoria|Microsoft.Usage|
|Zmiana podziału|Nieprzerwanie|

## <a name="cause"></a>Przyczyna

Typ, który implementuje <xref:System.IDisposable?displayProperty=fullName> deklarowane pola, które są typu, które <xref:System.IDisposable>również implementują. Metoda pola nie jest wywoływana <xref:System.IDisposable.Dispose%2A> przez metodę typu deklarującego. <xref:System.IDisposable.Dispose%2A>

## <a name="rule-description"></a>Opis reguły

Typ jest odpowiedzialny za likwidację wszystkich niezarządzanych zasobów. Reguła CA2213 sprawdza, czy typ jednorazowy (to jest <xref:System.IDisposable>, który implementuje) `T` deklaruje pole `F` , które jest wystąpieniem typu `FT`jednorazowego. Dla każdego pola `F` , któremu przypisano lokalnie utworzony obiekt w metodach lub inicjatorach z typem `T`zawierającym, reguła próbuje zlokalizować wywołanie `FT.Dispose`. Reguła przeszukuje metody wywoływane przez `T.Dispose` i jeden poziom niższy (czyli metody wywoływane przez metody wywoływane przez `T.Dispose`).

> [!NOTE]
> Inaczej niż w [przypadku specjalnych przypadków](#special-cases), reguła CA2213 uruchamiana tylko dla pól, które mają przypisany lokalnie utworzony obiekt jednorazowy w metodach i inicjatorach zawartego typu. Jeśli obiekt jest tworzony lub przypisany poza typem `T`, reguła nie jest wyzwalana. Zmniejsza to hałas dla przypadków, gdy typ zawierający nie jest odpowiedzialny za usuwanie obiektu.

### <a name="special-cases"></a>Specjalne przypadki

Reguła CA2213 może również być wyzwalana dla pól następujących typów, nawet jeśli obiekt, do którego są przypisane nie jest tworzony lokalnie:

- <xref:System.IO.Stream?displayProperty=nameWithType>
- <xref:System.IO.TextReader?displayProperty=nameWithType>
- <xref:System.IO.TextWriter?displayProperty=nameWithType>
- <xref:System.Resources.IResourceReader?displayProperty=nameWithType>

Przekazanie obiektu jednego z tych typów do konstruktora, a następnie przypisanie go do pola wskazuje na *przeniesienie własności usuwania* do nowo skonstruowanego typu. Oznacza to, że nowo skonstruowany typ jest teraz odpowiedzialny za usuwanie obiektu. Jeśli obiekt nie zostanie usunięty, wystąpi naruszenie CA2213.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia

Aby naprawić naruszenie tej zasady, należy wywołać <xref:System.IDisposable.Dispose%2A> pola, które są typu, który implementuje. <xref:System.IDisposable>

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia

Można bezpiecznie pominąć ostrzeżenie z tej reguły, jeśli:

- Typ oflagowany nie jest odpowiedzialny za zwolnienie zasobu przechowywanego w polu (oznacza to, że typ nie ma *prawa własności do usuwania*)
- Wywołanie odbywa się <xref:System.IDisposable.Dispose%2A> na bardziej szczegółowym poziomie wywoływania niż sprawdzanie reguł

## <a name="example"></a>Przykład

Poniższy fragment kodu przedstawia typ `TypeA` , który implementuje. <xref:System.IDisposable>

[!code-csharp[FxCop.Usage.IDisposablePattern#1](../code-quality/codesnippet/CSharp/ca2213-disposable-fields-should-be-disposed_1.cs)]

Poniższy fragment `TypeB` kodu przedstawia typ, który narusza reguły CA2213 przez zadeklarowanie pola `aFieldOfADisposableType` jako typ jednorazowy (`TypeA`) i nie wywoływanie <xref:System.IDisposable.Dispose%2A> dla tego pola.

[!code-csharp[FxCop.Usage.IDisposableFields#1](../code-quality/codesnippet/CSharp/ca2213-disposable-fields-should-be-disposed_2.cs)]

Aby naprawić naruszenie, wywołaj `Dispose()` pole jednorazowe:

```csharp
protected virtual void Dispose(bool disposing)
{
   if (!disposed)
   {
      // Dispose of resources held by this instance.
      aFieldOfADisposableType.Dispose();

      disposed = true;

      // Suppress finalization of this disposed instance.
      if (disposing)
      {
          GC.SuppressFinalize(this);
      }
   }
}
```

## <a name="see-also"></a>Zobacz także

- <xref:System.IDisposable?displayProperty=fullName>
- [Usuń wzorzec](/dotnet/standard/design-guidelines/dispose-pattern)