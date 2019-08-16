---
title: 'CA1063: Poprawnie zaimplementuj interfejs IDisposable'
ms.date: 03/11/2019
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
ms.openlocfilehash: 837659ca24eb66995626668185500db7bc32bbd7
ms.sourcegitcommit: 209ed0fcbb8daa1685e8d6b9a97f3857a4ce1152
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/16/2019
ms.locfileid: "69547376"
---
# <a name="ca1063-implement-idisposable-correctly"></a>CA1063: Poprawnie zaimplementuj interfejs IDisposable

|||
|-|-|
|TypeName|ImplementIDisposableCorrectly|
|CheckId|CA1063|
|Kategoria|Microsoft.Design|
|Zmiana kluczowa|Nieprzerwanie|

## <a name="cause"></a>Przyczyna

<xref:System.IDisposable?displayProperty=nameWithType> Interfejs nie został poprawnie zaimplementowany. Możliwe przyczyny tego obejmują:

- <xref:System.IDisposable>jest zaimplementowana w klasie.

- `Finalize`zostanie ponownie zastąpiony.

- `Dispose()`jest zastępowany.

- Metoda nie jest publiczna, [zapieczętowana](/dotnet/csharp/language-reference/keywords/sealed)ani nazywana **Dispose.** `Dispose()`

- `Dispose(bool)`nie jest chroniony, wirtualny lub niezapieczętowany.

- W niezapieczętowanych typach, `Dispose()` należy wywołać `Dispose(true)`.

- W przypadku typów `Finalize` niezapieczętowanych implementacja nie wywołuje ani obu `Dispose(bool)` , ani ani do finalizatora klasy bazowej.

Naruszenie jednego z tych wzorców wyzwala ostrzeżenie CA1063.

Każdy niezapieczętowany typ, który deklaruje i implementuje <xref:System.IDisposable> interfejs, musi udostępniać własną `protected virtual void Dispose(bool)` metodę. `Dispose()`należy wywołać `Dispose(true)`metodę, a finalizator powinien wywołać. `Dispose(false)` W przypadku utworzenia niezapieczętowanego typu, który deklaruje i implementuje <xref:System.IDisposable> interfejs, należy go zdefiniować `Dispose(bool)` i wywołać. Aby uzyskać więcej informacji, zobacz [Oczyszczanie zasobów niezarządzanych (Przewodnik po platformie .NET)](/dotnet/standard/garbage-collection/unmanaged) i [wzorca usuwania](/dotnet/standard/design-guidelines/dispose-pattern).

Domyślnie ta reguła sprawdza tylko typy widoczne na zewnątrz, ale [można to skonfigurować](#configurability).

## <a name="rule-description"></a>Opis reguły

Wszystkie <xref:System.IDisposable> typy powinny poprawnie zaimplementować [wzorzec Dispose](/dotnet/standard/design-guidelines/dispose-pattern) .

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia

Sprawdź kod i ustal, które z następujących rozwiązań spowodują rozwiązanie tego naruszenia:

- Usuń <xref:System.IDisposable> z listy interfejsów, które są implementowane przez typ, i Przesłoń implementację metody Dispose klasy podstawowej.

- Usuń finalizator z typu, Przesłoń metodę Dispose (usuwanie bool) i umieść logikę finalizacji w ścieżce kodu, gdzie "Dispose" ma wartość false.

- Zastąp metodę Dispose (likwidacja bool) i umieść logikę usuwania w ścieżce kodu, w której wartość "Dispose" jest prawdziwa.

- Upewnij się, że metoda Dispose () jest zadeklarowana jako publiczna i [zapieczętowana](/dotnet/csharp/language-reference/keywords/sealed).

- Zmień nazwę metody Dispose na **Dispose** i upewnij się, że jest ona zadeklarowana jako publiczna i [zapieczętowana](/dotnet/csharp/language-reference/keywords/sealed).

- Upewnij się, że metoda Dispose (bool) jest zadeklarowana jako chroniona, wirtualna i niezapieczętowany.

- Zmodyfikuj metodę Dispose (), tak aby wywoła ona metodę Dispose (true) <xref:System.GC.SuppressFinalize%2A> , a następnie wywołuje w bieżącym`this`wystąpieniu obiektu `Me` (lub w Visual Basic), a następnie zwraca wartość.

- Zmodyfikuj finalizator, aby wywoływał metodę Dispose (false), a następnie zwraca wartość.

- W przypadku utworzenia niezapieczętowanego typu, który deklaruje i implementuje <xref:System.IDisposable> interfejs, upewnij się, że <xref:System.IDisposable> implementacja jest zgodna ze wzorcem opisanym wcześniej w tej sekcji.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia

Nie pomijaj ostrzeżeń dla tej reguły.

## <a name="configurability"></a>Określając

Jeśli uruchamiasz tę regułę z [analizatorów FxCop](install-fxcop-analyzers.md) (a nie ze starszą analizą), możesz skonfigurować, które części bazy kodu mają uruchamiać tę regułę, na podstawie ich dostępności. Na przykład aby określić, że reguła powinna być uruchamiana tylko względem powierzchni niepublicznego interfejsu API, Dodaj następującą parę klucz-wartość do pliku editorconfig w projekcie:

```ini
dotnet_code_quality.ca1063.api_surface = private, internal
```

Tę opcję można skonfigurować tylko dla tej reguły, dla wszystkich reguł lub dla wszystkich reguł w tej kategorii (projekt). Aby uzyskać więcej informacji, zobacz [Konfigurowanie analizatorów FxCop](configure-fxcop-analyzers.md).

## <a name="pseudo-code-example"></a>Przykład pseudo kodu

Następujący pseudo kod zawiera ogólny przykład sposobu, w jaki Metoda Dispose (bool) powinna zostać zaimplementowana w klasie, która korzysta z zasobów zarządzanych i natywnych.

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

- [Dispose — wzorzec (wskazówki dotyczące projektowania struktury)](/dotnet/standard/design-guidelines/dispose-pattern)
- [Wyczyść niezarządzane zasoby (Przewodnik .NET)](/dotnet/standard/garbage-collection/unmanaged)