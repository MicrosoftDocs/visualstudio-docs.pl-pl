---
title: 'CA1063: Poprawnie zaimplementuj interfejs IDisposable'
ms.date: 02/12/2018
ms.topic: reference
f1_keywords:
- ImplementIDisposableCorrectly
- CA1063
helpviewer_keywords:
- CA1063
- ImplementIDisposableCorrectly
ms.assetid: 12afb1ea-3a17-4a3f-a1f0-fcdb853e2359
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- multiple
ms.openlocfilehash: e4bc426162919f4112ffdfcc0fbeeb0fefd2f09e
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2019
ms.locfileid: "55945758"
---
# <a name="ca1063-implement-idisposable-correctly"></a>CA1063: Poprawnie zaimplementuj interfejs IDisposable

|||
|-|-|
|TypeName|ImplementIDisposableCorrectly|
|CheckId|CA1063|
|Kategoria|Microsoft.Design|
|Zmiana kluczowa|Bez podziału|

## <a name="cause"></a>Przyczyna

<xref:System.IDisposable?displayProperty=nameWithType> Interfejsu nie jest zaimplementowana poprawnie. Możliwe przyczyny są między innymi:

- <xref:System.IDisposable> jest reimplemented w klasie.

- Finalizowanie jest reoverridden.

- Metody Dispose() zostanie zastąpiona.

- Metoda Dispose() nie jest publiczna, [zapieczętowanego](/dotnet/csharp/language-reference/keywords/sealed), co najmniej o nazwie **Dispose**.

- Dispose(bool) nie jest chroniony, wirtualny lub niezapieczętowane.

- Niezapieczętowane typy metody Dispose() musi wywołać metody Dispose(true).

- W przypadku typów niezapieczętowanych implementacji Finalize niewywołujący jednego lub obu tych Dispose(bool) lub finalizator klasy bazowej.

Naruszenie któregokolwiek z tych wzorców wyzwala ostrzeżenie CA1063.

Każdy niezapieczętowany typ, który deklaruje i implementuje <xref:System.IDisposable> interfejsu należy podać swój własny chronionych void Dispose(bool) metodę wirtualną. Metody Dispose() powinny wywoływać Dipose(true) i finalizatory powinny wywoływać metody Dispose(false). Jeśli utworzysz niezamknięty typ, który deklaruje i implementuje <xref:System.IDisposable> interfejsu, należy zdefiniować Dispose(bool) i wywołać go. Aby uzyskać więcej informacji, zobacz [wyczyścić niezarządzane zasoby (.NET — przewodnik)](/dotnet/standard/garbage-collection/unmanaged) i [wzorzec usuwania](/dotnet/standard/design-guidelines/dispose-pattern).

## <a name="rule-description"></a>Opis reguły

Wszystkie <xref:System.IDisposable> typy powinny implementować [wzorzec usuwania](/dotnet/standard/design-guidelines/dispose-pattern) poprawnie.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia

Sprawdź kod i określić, które z następujących rozwiązań rozwiąże to naruszenie:

- Usuń <xref:System.IDisposable> z listy interfejsów, które są implementowane przez danego typu, a także Przesłoń implementację metody Dispose w klasie bazowej, zamiast tego.

- Usuń finalizator z typu, Przesłoń metodę Dispose (bool disposing) i umieść logikę finalizowania w ścieżce kodu, w którym "disposing" ma wartość false.

- Przesłoń metodę Dispose (bool disposing) i umieść logikę rozporządzania w ścieżce kodu, w którym "disposing" ma wartość true.

- Upewnij się, że metody Dispose() jest zadeklarowany jako publiczny i [zapieczętowanego](/dotnet/csharp/language-reference/keywords/sealed).

- Zmiana nazwy Twojego metodę dispose, aby **Dispose** i upewnij się, że jest on zadeklarowany jako publiczny i [zapieczętowanego](/dotnet/csharp/language-reference/keywords/sealed).

- Upewnij się, że Dispose(bool) został zadeklarowany jako chroniony, wirtualny i niezapieczętowany.

- Zmodyfikować Dispose() wywołuje metodę Dispose(true), następnie wywołuje <xref:System.GC.SuppressFinalize%2A> w bieżącym wystąpieniu obiektu (`this`, lub `Me` w języku Visual Basic), a następnie zwraca.

- Zmodyfikuj swoje finalizatora, tak, aby wywołuje metody Dispose(false), a następnie zwraca.

- Jeśli utworzysz niezamknięty typ, który deklaruje i implementuje <xref:System.IDisposable> interfejsu, upewnij się, że implementacja <xref:System.IDisposable> jest zgodna z wzorcem, opisanego wcześniej w tej sekcji.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia

Nie pomijaj ostrzeżeń dla tej reguły.

## <a name="pseudo-code-example"></a>Przykładowy pseudo-kod

Pseudo-poniższy kod stanowi przykład ogólne implementacji Dispose(bool) w klasie, która korzysta z zarządzanego i natywnego zasobów.

```csharp
public class Resource : IDisposable
{
    private IntPtr nativeResource = Marshal.AllocHGlobal(100);
    private AnotherResource managedResource = new AnotherResource();

    // Dispose() calls Dispose(true)
    public void Dispose()
    {
        Dispose(true);
        GC.SuppressFinalize(this);
    }

    // NOTE: Leave out the finalizer altogether if this class doesn't
    // own unmanaged resources, but leave the other methods
    // exactly as they are.
    ~Resource()
    {
        // Finalizer calls Dispose(false)
        Dispose(false);
    }

    // The bulk of the clean-up code is implemented in Dispose(bool)
    protected virtual void Dispose(bool disposing)
    {
        if (disposing)
        {
            // free managed resources
            if (managedResource != null)
            {
                managedResource.Dispose();
                managedResource = null;
            }
        }
        // free native resources if there are any.
        if (nativeResource != IntPtr.Zero)
        {
            Marshal.FreeHGlobal(nativeResource);
            nativeResource = IntPtr.Zero;
        }
    }
}
```

## <a name="see-also"></a>Zobacz także

- [Usuń wzorca (wytyczne dotyczące projektowania framework)](/dotnet/standard/design-guidelines/dispose-pattern)
- [Oczyszczanie zasobów niezarządzanych (Przewodnik platformy .NET)](/dotnet/standard/garbage-collection/unmanaged)