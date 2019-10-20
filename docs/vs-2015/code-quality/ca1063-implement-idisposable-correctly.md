---
title: 'CA1063: Zaimplementuj interfejs IDisposable poprawnie | Microsoft Docs'
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
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 1fe2982ab9e1b3951583b268eadb44c97c8e4805
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72663635"
---
# <a name="ca1063-implement-idisposable-correctly"></a>CA1063: Należy prawidłowo zaimplementować interfejs IDisposable
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|ImplementIDisposableCorrectly|
|CheckId|CA1063|
|Kategoria|Microsoft. Design|
|Zmiana kluczowa|Nieprzerwanie|

## <a name="cause"></a>Przyczyna
 `IDisposable` nie został poprawnie zaimplementowany. Niektóre przyczyny tego problemu są wymienione tutaj:

- Interfejs IDisposable jest zaimplementowany w klasie.

- Finalizacja została przesłonięta.

- Metoda Dispose została zastąpiona.

- Metoda Dispose () nie jest publiczna, zapieczętowana lub nazywana Dispose.

- Metoda Dispose (bool) nie jest chroniona, wirtualna lub niezapieczętowany.

- W niezapieczętowanych typach Metoda Dispose () musi wywoływać metodę Dispose (true).

- W przypadku typów niezapieczętowanych implementacja finalizowania nie wywołuje żadnej lub obu metod Dispose (bool) ani finalizatora klasy przypadku.

  Naruszenie jednego z tych wzorców spowoduje wyzwolenie tego ostrzeżenia.

  Każdy niezapieczętowany typ interfejsu IDisposable musi zapewniać własną, chronioną metodę "void" (bool). Metoda Dispose () powinna wywołać metodę Dispose (true) i Finalize powinna wywołać metodę Dispose (false). Jeśli tworzysz niezapieczętowany typ interfejsu IDisposable, musisz zdefiniować metodę Dispose (bool) i wywołać ją. Aby uzyskać więcej informacji, zobacz [Oczyszczanie zasobów niezarządzanych](https://msdn.microsoft.com/library/a17b0066-71c2-4ba4-9822-8e19332fc213) w sekcji [wskazówki dotyczące projektowania struktury](https://msdn.microsoft.com/library/5fbcaf4f-ea2a-4d20-b0d6-e61dee202b4b) w dokumentacji .NET Framework.

## <a name="rule-description"></a>Opis reguły
 Wszystkie typy IDisposable powinny poprawnie implementować wzorzec Dispose.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Sprawdź kod i ustal, które z poniższych rozwiązań spowodują rozwiązanie tego naruszenia.

- Usuń interfejs IDisposable z listy interfejsów, które są implementowane przez {0} i Zastąp zamiast niej implementację Dispose klasy podstawowej.

- Usuń finalizator z typu {0}, przesłonić metodę Dispose (usuwanie bool) i umieścić logikę finalizacji w ścieżce kodu, w której element "Dispose" ma wartość false.

- Usuń {0}, Zastąp metodę Dispose (likwidacja bool) i umieść logikę usuwania w ścieżce kodu, w której element "Dispose" ma wartość true.

- Upewnij się, że {0} jest zadeklarowany jako publiczny i zapieczętowany.

- Zmień nazwę {0} na "Dispose" i upewnij się, że jest on zadeklarowany jako publiczny i zapieczętowany.

- Upewnij się, że {0} jest zadeklarowany jako chroniony, wirtualny i niezapieczętowany.

- Zmodyfikuj {0} tak, aby wywoływał metodę Dispose (true), a następnie wywołuje metodę GC. SuppressFinalize dla bieżącego wystąpienia obiektu ("This" lub "Me" w [!INCLUDE[vbprvb](../includes/vbprvb-md.md)]), a następnie zwraca wartość.

- Zmodyfikuj {0} tak, aby wywołuje metodę Dispose (false), a następnie zwraca wartość.

- W przypadku pisania niezapieczętowanej klasy głównej IDisposable upewnij się, że implementacja interfejsu IDisposable jest zgodna ze wzorcem opisanym wcześniej w tej sekcji.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Nie pomijaj ostrzeżeń dla tej reguły.

## <a name="pseudo-code-example"></a>Przykład pseudo kodu
 Następujący pseudo kod zawiera ogólny przykład sposobu, w jaki Metoda Dispose (bool) powinna zostać zaimplementowana w klasie, która korzysta z zasobów zarządzanych i natywnych.

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
