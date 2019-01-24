---
title: 'CA1063: Poprawnie zaimplementuj interfejs IDisposable | Dokumentacja firmy Microsoft'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- ImplementIDisposableCorrectly
- CA1063
helpviewer_keywords:
- CA1063
- ImplementIDisposableCorrectly
ms.assetid: 12afb1ea-3a17-4a3f-a1f0-fcdb853e2359
caps.latest.revision: 19
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 52e77762900a321cf547709d98d9856088580789
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54785470"
---
# <a name="ca1063-implement-idisposable-correctly"></a>CA1063: Poprawnie zaimplementuj interfejs IDisposable
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|ImplementIDisposableCorrectly|
|CheckId|CA1063|
|Kategoria|Microsoft.Design|
|Zmiana kluczowa|Bez podziału|

## <a name="cause"></a>Przyczyna
 `IDisposable` Nie zaimplementowano poprawnie. Poniżej przedstawiono niektóre przyczyny tego problemu:

- Interfejs IDisposable, jest ponownie zaimplementowane w klasie.

- Finalizowanie ponownie zostanie zastąpiona.

- Dispose zostanie zastąpiona.

- Metody Dispose() nie jest publiczna, zapieczętowany lub o nazwie metody Dispose.

- Dispose(bool) nie jest chroniony, wirtualny lub niezapieczętowane.

- Niezapieczętowane typy metody Dispose() musi wywołać metody Dispose(true).

- W przypadku typów niezapieczętowanych implementacji Finalize niewywołujący jednego lub obu tych Dispose(bool) lub finalizatory klasy wielkości liter.

  Naruszenie któregokolwiek z tych wzorców wyzwoli to ostrzeżenie.

  Co główny niezapieczętowany typ interfejsu IDisposable, musisz podać swój własny chronionych void Dispose(bool) metodę wirtualną. Metody Dispose() powinny wywoływać Dipose(true) i Finalize powinny wywoływać metody Dispose(false). W przypadku tworzenia głównego niezapieczętowanego typu IDisposable, należy zdefiniować Dispose(bool) i wywołać go. Aby uzyskać więcej informacji, zobacz [Cleaning Up Unmanaged Resources](http://msdn.microsoft.com/library/a17b0066-71c2-4ba4-9822-8e19332fc213) w [wytyczne dotyczące projektowania Framework](http://msdn.microsoft.com/library/5fbcaf4f-ea2a-4d20-b0d6-e61dee202b4b) części dokumentacji .NET Framework.

## <a name="rule-description"></a>Opis reguły
 Wszystkie typy IDisposable powinny poprawnie implementować wzorzec Dispose.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Sprawdź swój kod, aby określić, które z następujących rozwiązań rozwiąże to naruszenie.

-   Usuń interfejs IDisposable z listy interfejsów implementowanych przez {0} i Przesłoń implementację metody Dispose w klasie bazowej, zamiast tego.

-   Usuń finalizator z typu {0}, Przesłoń metodę Dispose (bool disposing) i umieść logikę finalizowania w ścieżce kodu, w którym "disposing" ma wartość false.

-   Usuń {0}, Przesłoń metodę Dispose (bool disposing) i umieść logikę rozporządzania w ścieżce kodu, w którym "disposing" ma wartość true.

-   Upewnij się, że {0} jest zadeklarowany jako publiczny i zapieczętowany.

-   Zmień nazwę {0} do "Usuwania" i upewnij się, że jest on zadeklarowany jako publiczny i zapieczętowany.

-   Upewnij się, że {0} jest zadeklarowany jako chroniony, wirtualny i niezapieczętowany.

-   Modyfikowanie {0} tak, aby Dispose(true), następnie wywołuje GC. SuppressFinalize w bieżącym wystąpieniu obiektu ("this" lub "Me" w [!INCLUDE[vbprvb](../includes/vbprvb-md.md)]), a następnie zwraca.

-   Modyfikowanie {0} tak, aby wywołuje metody Dispose(false), a następnie zwraca.

-   Jeśli piszesz klasę niezapieczętowany główny interfejs IDisposable, upewnij się, że implementacja interfejsu IDisposable jest zgodna z wzorcem, opisanego wcześniej w tej sekcji.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Nie pomijaj ostrzeżeń dla tej reguły.

## <a name="pseudo-code-example"></a>Przykładowy pseudo-kod
 Pseudo-poniższy kod stanowi przykład ogólne implementacji Dispose(bool) w klasie, która korzysta z zarządzanego i natywnego zasobów.

```
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
    // own unmanaged resources itself, but leave the other methods
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
