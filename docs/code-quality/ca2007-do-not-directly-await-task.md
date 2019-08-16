---
title: 'CA2007: Nie oczekuj bezpośrednio zadania'
ms.date: 03/08/2019
ms.topic: reference
f1_keywords:
- CA2007
- DoNotDirectlyAwaitATaskAnalyzer
helpviewer_keywords:
- CA2007
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
ms.openlocfilehash: 0d3ab899ad660c637492a4c3d229779481184e95
ms.sourcegitcommit: 209ed0fcbb8daa1685e8d6b9a97f3857a4ce1152
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/16/2019
ms.locfileid: "69547014"
---
# <a name="ca2007-do-not-directly-await-a-task"></a>CA2007: Nie oczekuj bezpośrednio zadania

|||
|-|-|
|TypeName|DoNotDirectlyAwaitATaskAnalyzer|
|CheckId|CA2007|
|Kategoria|Microsoft.Reliability|
|Zmiana kluczowa|Nieprzerwanie|

## <a name="cause"></a>Przyczyna

Metoda asynchroniczna [czeka](/dotnet/csharp/language-reference/keywords/await) <xref:System.Threading.Tasks.Task> bezpośrednio.

## <a name="rule-description"></a>Opis reguły

Gdy Metoda asynchroniczna czeka <xref:System.Threading.Tasks.Task> bezpośrednio, kontynuacja występuje w tym samym wątku, który utworzył zadanie. Takie zachowanie może być kosztowne pod względem wydajności i może spowodować zakleszczenie w wątku interfejsu użytkownika. Rozważ wywołanie <xref:System.Threading.Tasks.Task.ConfigureAwait(System.Boolean)?displayProperty=nameWithType> metody sygnalizującej zamiar kontynuacji.

Ta zasada została wprowadzona przy użyciu [analizatorów FxCop](install-fxcop-analyzers.md) i nie istnieje w starszej analizie FxCop.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia

Aby naprawić naruszenia, wywołaj <xref:System.Threading.Tasks.Task.ConfigureAwait%2A> <xref:System.Threading.Tasks.Task>oczekiwane. Można przekazać albo `true` `false` dla `continueOnCapturedContext` parametru.

- Wywołanie `ConfigureAwait(true)` dla zadania ma takie samo zachowanie, jak niejawnie wywoływanie <xref:System.Threading.Tasks.Task.ConfigureAwait%2A>. Jawne wywołanie tej metody polega na tym, że czytelnicy będą wiedzieli, że zamierzasz przeprowadzić kontynuację w oryginalnym kontekście synchronizacji.

- Wywołaj `ConfigureAwait(false)` zadanie, aby zaplanować kontynuacje puli wątków, unikając w ten sposób zakleszczenia w wątku interfejsu użytkownika. Przekazywanie `false` jest dobrym rozwiązaniem dla bibliotek niezależnych od aplikacji.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia

Możesz pominąć to ostrzeżenie, Jeśli wiesz, że klient nie jest aplikacją graficznego interfejsu użytkownika (GUI) lub jeśli użytkownik nie ma <xref:System.Threading.SynchronizationContext>.

## <a name="example"></a>Przykład

Poniższy fragment kodu generuje ostrzeżenie:

```csharp
public async Task Execute()
{
    Task task = null;
    await task;
}
```

Aby naprawić naruszenie, wywołaj <xref:System.Threading.Tasks.Task.ConfigureAwait%2A> <xref:System.Threading.Tasks.Task>oczekiwane:

```csharp
public async Task Execute()
{
    Task task = null;
    await task.ConfigureAwait(false);
}
```

## <a name="configurability"></a>Określając

Można skonfigurować, czy chcesz wykluczyć metody asynchroniczne, które nie zwracają wartości z tej reguły. Aby wykluczyć te rodzaje metod, Dodaj następującą parę klucz-wartość do pliku editorconfig w projekcie:

```ini
# Package version 2.9.0 and later
dotnet_code_quality.CA2007.exclude_async_void_methods = true

# Package version 2.6.3 and earlier
dotnet_code_quality.CA2007.skip_async_void_methods = true
```

Można także skonfigurować, do których rodzajów zestawów wyjściowych ma być stosowana ta reguła. Na przykład, aby zastosować tę regułę tylko do kodu generującego aplikację konsolową lub dynamicznie połączonej biblioteki (to nie jest aplikacja interfejsu użytkownika), Dodaj następującą parę klucz-wartość do pliku editorconfig w projekcie:

```ini
dotnet_code_quality.CA2007.output_kind = ConsoleApplication, DynamicallyLinkedLibrary
```

Aby uzyskać więcej informacji, zobacz [Konfigurowanie analizatorów FxCop](configure-fxcop-analyzers.md).

## <a name="see-also"></a>Zobacz także

- [Czy należy czekać na zadanie z ConfigureAwait (false)?](https://github.com/Microsoft/vs-threading/blob/master/doc/cookbook_vs.md#should-i-await-a-task-with-configureawaitfalse)
- [Zainstaluj analizatory FxCop w programie Visual Studio](install-fxcop-analyzers.md)