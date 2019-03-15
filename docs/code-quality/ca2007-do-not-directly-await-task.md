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
ms.openlocfilehash: bf3e13697f39f7d0f531549d4c018b9f42872596
ms.sourcegitcommit: f7c401a376ce410336846835332a693e6159c551
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2019
ms.locfileid: "57869292"
---
# <a name="ca2007-do-not-directly-await-a-task"></a>CA2007: Nie oczekuj bezpośrednio zadania

|||
|-|-|
|TypeName|DoNotDirectlyAwaitATaskAnalyzer|
|CheckId|CA2007|
|Kategoria|Microsoft.Reliability|
|Zmiana kluczowa|Bez podziału|

## <a name="cause"></a>Przyczyna

Metoda asynchroniczna [czeka](/dotnet/csharp/language-reference/keywords/await) <xref:System.Threading.Tasks.Task> bezpośrednio.

## <a name="rule-description"></a>Opis reguły

Gdy czeka na metodę asynchroniczną <xref:System.Threading.Tasks.Task> bezpośrednio, kontynuacja odbywa się w tym samym wątku, który utworzył zadanie. To zachowanie może być kosztowna pod względem wydajności i może spowodować zakleszczenie w wątku interfejsu użytkownika. Należy wziąć pod uwagę wywoływania <xref:System.Threading.Tasks.Task.ConfigureAwait(System.Boolean)?displayProperty=nameWithType> celu sygnalizowania, że masz zamiar dla kontynuacji.

Ta zasada została wprowadzona w systemach [analizatory FxCop analizujące kod](install-fxcop-analyzers.md) , a nie istnieje w "starszych" (statycznej analizy kodu) programu FxCop.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia

Aby naprawić naruszenia, należy wywołać <xref:System.Threading.Tasks.Task.ConfigureAwait%2A> na oczekiwane <xref:System.Threading.Tasks.Task>. Można przekazać `true` lub `false` dla `continueOnCapturedContext` parametru.

- Wywoływanie `ConfigureAwait(true)` zadania ma takie samo zachowanie jako nie zostały jawnie podczas wywoływania <xref:System.Threading.Tasks.Task.ConfigureAwait%2A>. Przez jawne wywołanie tej metody, zezwalania czytelników o tym, że chcesz celowo wykonywania kontynuację na oryginalnego kontekstu synchronizacji.

- Wywołaj `ConfigureAwait(false)` zadania można zaplanować kontynuacji w puli wątków, zapobiegając zakleszczenie w wątku interfejsu użytkownika. Przekazywanie `false` jest dobrym rozwiązaniem dla bibliotek niezależny od aplikacji.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia

Można pominąć to ostrzeżenie, jeśli wiesz, że użytkownik jest spoza aplikacji interfejsu graficznego lub jeśli użytkownik nie ma <xref:System.Threading.SynchronizationContext>.

## <a name="example"></a>Przykład

Poniższy fragment kodu generuje ostrzeżenie:

```csharp
public async Task Execute()
{
    Task task = null;
    await task;
}
```

Aby naprawić naruszenie, należy wywołać <xref:System.Threading.Tasks.Task.ConfigureAwait%2A> na oczekiwane <xref:System.Threading.Tasks.Task>:

```csharp
public async Task Execute()
{
    Task task = null;
    await task.ConfigureAwait(false);
}
```

## <a name="configurability"></a>Konfigurowalne

Możesz określić, czy chcesz wykluczyć metod asynchronicznych, które nie zwrócą wartość od tej reguły. Aby wykluczyć tych rodzajów metod, należy dodać następujące pary klucz wartość do pliku .editorconfig w projekcie:

```
# Package version 2.9.0 and later
dotnet_code_quality.CA2007.exclude_async_void_methods = true

# Package version 2.6.3 and earlier
dotnet_code_quality.CA2007.skip_async_void_methods = true
```

Można również skonfigurować, której dane wyjściowe rodzaju zestawu, aby zastosować tę regułę do. Na przykład tylko Zastosuj tę regułę do kodu, który tworzy aplikacji konsoli lub dynamicznie łączonych bibliotek (czyli nie aplikacja interfejsu użytkownika), Dodaj następujące pary klucz wartość w pliku .editorconfig w projekcie:

```
dotnet_code_quality.CA2007.output_kind = ConsoleApplication, DynamicallyLinkedLibrary
```

Aby uzyskać więcej informacji, zobacz [analizatory FxCop analizujące kod z skonfigurować](configure-fxcop-analyzers.md).

## <a name="see-also"></a>Zobacz także

- [Czy powinni oczekiwać zadania z ConfigureAwait(false)?](https://github.com/Microsoft/vs-threading/blob/master/doc/cookbook_vs.md#should-i-await-a-task-with-configureawaitfalse)
- [Zainstaluj analizatory FxCop analizujące kod w programie Visual Studio](install-fxcop-analyzers.md)