---
title: Potwierdzenia w kodzie zarządzanym | Microsoft Docs
description: 'Dowiedz się więcej na temat potwierdzeń jako narzędzia debugowania dla kodu zarządzanego w języku C#, Visual Basic lub F # w programie Visual Studio.'
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging [Visual Studio], assertions in managed code
- Trace.Assert method
- debugging managed code, assertions
- Debug.Assert method
- Debug.Listeners property
- assertions, side effects
- Trace.Listeners property
- assertions, managed code
ms.assetid: 70ab2522-6486-4076-a1a9-e0f11cd0f3a1
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- dotnet
ms.openlocfilehash: 626f86c2a1d370a7f31e47f86d8adafc3f905672
ms.sourcegitcommit: 5654b7a57a9af111a6f29239212d76086bc745c9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/03/2021
ms.locfileid: "101684240"
---
# <a name="assertions-in-managed-code"></a>Potwierdzenia w zarządzanym kodzie
Potwierdzenie (lub instrukcja `Assert`) testuje warunek, który określasz jako argument instrukcji `Assert`. Jeśli warunek ma wartość „true” (prawda), nie są wykonywane żadne akcje. Jeśli warunek ma wartość „false” (fałsz), asercja kończy się niepowodzeniem. W przypadku uruchamiania programu z kompilacją debugowania program przechodzi do trybu przerwania.

## <a name="in-this-topic"></a><a name="BKMK_In_this_topic"></a> W tym temacie
 [Potwierdzenia w przestrzeni nazw System. Diagnostics](#BKMK_Asserts_in_the_System_Diagnostics_Namespace)

 [Debug. Assert — Metoda](#BKMK_The_Debug_Assert_method)

 [Efekty uboczne debugowania. Assert](#BKMK_Side_effects_of_Debug_Assert)

 [Wymagania dotyczące śledzenia i debugowania](#BKMK_Trace_and_Debug_Requirements)

 [Argumenty potwierdzenia](#BKMK_Assert_arguments)

 [Dostosowywanie zachowania potwierdzenia](#BKMK_Customizing_Assert_behavior)

 [Ustawianie potwierdzeń w plikach konfiguracji](#BKMK_Setting_assertions_in_configuration_files)

## <a name="asserts-in-the-systemdiagnostics-namespace"></a><a name="BKMK_Asserts_in_the_System_Diagnostics_Namespace"></a> Potwierdzenia w przestrzeni nazw System. Diagnostics
 W Visual Basic i Visual C#, można użyć `Assert` metody z <xref:System.Diagnostics.Debug> lub <xref:System.Diagnostics.Trace> , które znajdują się w <xref:System.Diagnostics> przestrzeni nazw. Metody klasy <xref:System.Diagnostics.Debug> nie są uwzględnione w wydanej wersji programu, więc nie zwiększają rozmiaru ani nie zmniejszają szybkości kodu wydania.

 Język C++ nie obsługuje <xref:System.Diagnostics.Debug> metod klasy. Ten sam efekt można osiągnąć przy użyciu <xref:System.Diagnostics.Trace> klasy z kompilacją warunkową, taką jak `#ifdef DEBUG` ... `#endif`

 [W tym temacie](#BKMK_In_this_topic)

## <a name="the-debugassert-method"></a><a name="BKMK_The_Debug_Assert_method"></a> Debug. Assert — Metoda
 Użyj <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=fullName> metody swobodnej, aby sprawdzić warunki, które powinny mieć wartość PRAWDA, jeśli kod jest poprawny. Załóżmy na przykład, że napisano funkcję dzielenia liczb całkowitych. Zgodnie z regułami matematycznymi dzielnik nigdy nie może być równy zero. Można to przetestować przy użyciu potwierdzenia:

```VB
Function IntegerDivide(ByVal dividend As Integer, ByVal divisor As Integer) As Integer
    Debug.Assert(divisor <> 0)
    Return CInt(dividend / divisor)
End Function
```

```csharp
int IntegerDivide ( int dividend , int divisor )
{
    Debug.Assert ( divisor != 0 );
    return ( dividend / divisor );
}
```

 Gdy uruchamiasz ten kod w debugerze, instrukcja asercji jest oceniana, ale w wersji wydanej nie zostanie wykonane porównanie, więc nie ma dodatkowych kosztów.

 Oto inny przykład. Masz klasę implementującą konto sprawdzania w następujący sposób:

```VB
Dim amount, balance As Double
balance = savingsAccount.balance
Debug.Assert(amount <= balance)
SavingsAccount.Withdraw(amount)
```

```csharp
float balance = savingsAccount.Balance;
Debug.Assert ( amount <= balance );
savingsAccount.Withdraw ( amount );
```

 Przed wycofaniem pieniędzy z konta należy upewnić się, że saldo konta jest wystarczające, aby pokryć kwotę przygotowywaną do wycofania. Możesz napisać potwierdzenie, aby sprawdzić saldo:

```VB
Dim amount, balance As Double
balance = savingsAccount.balance
Trace.Assert(amount <= balance)
SavingsAccount.Withdraw(amount)
```

```csharp
float balance = savingsAccount.Balance;
Trace.Assert ( amount <= balance );
savingsAccount.Withdraw ( amount );
```

 Należy pamiętać, że wywołania <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=fullName> metody znikają podczas tworzenia wydania wersji kodu. Oznacza to, że wywołanie sprawdzające saldo znika w wersji wydanej. Aby rozwiązać ten problem, należy zastąpić <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=fullName> <xref:System.Diagnostics.Trace.Assert%2A?displayProperty=fullName> poleceniem, które nie znika w wersji wydania:

 Wywołuje się <xref:System.Diagnostics.Trace.Assert%2A?displayProperty=fullName> , by dodać narzuty do wersji wydania, w przeciwieństwie do wywołań <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=fullName> .

 [W tym temacie](#BKMK_In_this_topic)

## <a name="side-effects-of-debugassert"></a><a name="BKMK_Side_effects_of_Debug_Assert"></a> Efekty uboczne debugowania. Assert
 Gdy używasz <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=fullName> , upewnij się, że żaden kod wewnątrz `Assert` nie zmienia wyników programu, jeśli `Assert` został usunięty. W przeciwnym razie można przypadkowo wprowadzić usterkę, która będzie wyświetlana tylko w wydanej wersji programu. Należy zwrócić szczególną uwagę na temat potwierdzeń, które zawierają wywołania funkcji lub procedur, takie jak Poniższy przykład:

```VB
' unsafe code
Debug.Assert (meas(i) <> 0 )
```

```csharp
// unsafe code
Debug.Assert (meas(i) != 0 );
```

 To użycie <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=fullName> może wydawać się w pierwszej kolejności, ale Załóżmy, że funkcja MEAS aktualizuje licznik przy każdym wywołaniu. Podczas kompilowania wersji wydania to wywołanie do MEAS jest eliminowane, więc licznik nie zostanie zaktualizowany. Jest to przykład funkcji z efektem ubocznym. Usunięcie wywołania funkcji, która ma efekty uboczne, może spowodować błąd, który pojawia się tylko w wersji Release. Aby uniknąć takich problemów, nie należy umieszczać wywołań funkcji w <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=fullName> instrukcji. Zamiast tego użyj zmiennej tymczasowej:

```VB
temp = meas( i )
Debug.Assert (temp <> 0)
```

```csharp
temp = meas( i );
Debug.Assert ( temp != 0 );
```

 Nawet w przypadku korzystania z programu <xref:System.Diagnostics.Trace.Assert%2A?displayProperty=fullName> można nadal unikać umieszczania wywołań funkcji wewnątrz `Assert` instrukcji. Takie wywołania powinny być bezpieczne, ponieważ <xref:System.Diagnostics.Trace.Assert%2A?displayProperty=fullName> instrukcje nie są eliminowane w kompilacji wydania. Jednakże w przypadku uniknięcia takich konstrukcji jako kwestii wykonywać, podczas korzystania z programu może wystąpić błąd <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=fullName> .

 [W tym temacie](#BKMK_In_this_topic)

## <a name="trace-and-debug-requirements"></a><a name="BKMK_Trace_and_Debug_Requirements"></a> Wymagania dotyczące śledzenia i debugowania
 Jeśli tworzysz projekt przy użyciu [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] kreatorów, symbol śledzenia jest definiowany domyślnie w konfiguracjach wersji i debugowania. Symbol debugowania jest definiowany domyślnie tylko w kompilacji debugowania.

 W przeciwnym razie, aby <xref:System.Diagnostics.Trace> metody działały, program musi mieć jedną z następujących wartości w górnej części pliku źródłowego:

- `#Const TRACE = True` w Visual Basic

- `#define TRACE` w językach Visual C# i C++

  Lub program musi być skompilowany przy użyciu opcji śledzenia:

- `/d:TRACE=True` w Visual Basic

- `/d:TRACE` w językach Visual C# i C++

  Jeśli musisz użyć metod debugowania w kompilacji w języku C# lub Visual Basic, musisz zdefiniować symbol debugowania w konfiguracji wydania.

  Język C++ nie obsługuje <xref:System.Diagnostics.Debug> metod klasy. Ten sam efekt można osiągnąć przy użyciu <xref:System.Diagnostics.Trace> klasy z kompilacją warunkową, taką jak `#ifdef DEBUG` ... `#endif` Można zdefiniować te symbole w oknie dialogowym **\<Project> strony właściwości** . Aby uzyskać więcej informacji, zobacz [Zmiana ustawień projektu dla konfiguracji debugowania Visual Basic](../debugger/project-settings-for-a-visual-basic-debug-configuration.md) lub [Zmiana ustawień projektu dla konfiguracji debugowania C lub C++](../debugger/project-settings-for-a-cpp-debug-configuration.md).

## <a name="assert-arguments"></a><a name="BKMK_Assert_arguments"></a> Argumenty potwierdzenia
 <xref:System.Diagnostics.Trace.Assert%2A?displayProperty=fullName> i <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=fullName> zapoznaj się z trzema argumentami. Pierwszy argument, który jest obowiązkowy, to warunek, który chcesz sprawdzić. W przypadku wywołania <xref:System.Diagnostics.Trace.Assert(System.Boolean)?displayProperty=fullName> lub <xref:System.Diagnostics.Debug.Assert(System.Boolean)?displayProperty=fullName> z tylko jednym argumentem `Assert` Metoda sprawdza warunek i, jeśli wynik ma wartość false, wyprowadza zawartość stosu wywołań do okna **danych wyjściowych** . Poniższy przykład przedstawia <xref:System.Diagnostics.Trace.Assert(System.Boolean)?displayProperty=fullName> i <xref:System.Diagnostics.Debug.Assert(System.Boolean)?displayProperty=fullName> :

```VB
Debug.Assert(stacksize > 0)
Trace.Assert(stacksize > 0)
```

```csharp
Debug.Assert ( stacksize > 0 );
Trace.Assert ( stacksize > 0 );
```

  Drugi i trzeci argument, jeśli istnieją, muszą być ciągami. W przypadku wywołania <xref:System.Diagnostics.Trace.Assert%2A?displayProperty=fullName> lub <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=fullName> z dwoma lub trzema argumentami, pierwszym argumentem jest warunek. Metoda sprawdza warunek i, jeśli wynik ma wartość false, wyprowadza drugi ciąg i trzecie ciągi. Poniższy przykład ilustruje <xref:System.Diagnostics.Debug.Assert(System.Boolean,System.String)?displayProperty=fullName> i jest <xref:System.Diagnostics.Trace.Assert(System.Boolean,System.String)?displayProperty=fullName> używany z dwoma argumentami:

```VB
Debug.Assert(stacksize > 0, "Out of stack space")
Trace.Assert(stacksize > 0, "Out of stack space")
```

```csharp
Debug.Assert ( stacksize > 0, "Out of stack space" );
Trace.Assert ( stacksize > 0, "Out of stack space" );
```

  Poniższy przykład pokazuje <xref:System.Diagnostics.Debug.Assert(System.Boolean,System.String,System.String)?displayProperty=fullName> i jest <xref:System.Diagnostics.Trace.Assert(System.Boolean,System.String,System.String)?displayProperty=fullName> używany z trzema argumentami:

```VB
Debug.Assert(stacksize > 0, "Out of stack space. Bytes left:" , Format(size, "G"))
Trace.Assert(stacksize > 0, "Out of stack space. Bytes left:" , Format(size, "G"))
Trace.Assert(stacksize > 0, "Out of stack space. Bytes left:", "inctemp failed on third call" )
```

```csharp
Debug.Assert ( stacksize > 100, "Out of stack space" , "Failed in inctemp" );
Trace.Assert ( stacksize > 0, "Out of stack space", "Failed in inctemp" );
```

 [W tym temacie](#BKMK_In_this_topic)

## <a name="customizing-assert-behavior"></a><a name="BKMK_Customizing_Assert_behavior"></a> Dostosowywanie zachowania potwierdzenia
 Jeśli uruchomisz aplikację w trybie interfejsu użytkownika, `Assert` Metoda wyświetli okno dialogowe **Niepowodzenie potwierdzenia** , gdy warunek się nie powiedzie. Akcje, które występują, gdy potwierdzenie nie powiedzie się, jest kontrolowane przez <xref:System.Diagnostics.Debug.Listeners%2A> <xref:System.Diagnostics.Trace.Listeners%2A> Właściwość or.

 Możesz dostosować zachowanie danych wyjściowych przez dodanie <xref:System.Diagnostics.TraceListener> obiektu do `Listeners` kolekcji, usuwając element <xref:System.Diagnostics.TraceListener> z `Listeners` kolekcji lub zastępując <xref:System.Diagnostics.TraceListener.Fail%2A?displayProperty=fullName> metodę istniejącej, `TraceListener` Aby zachowywać się inaczej.

 Można na przykład zastąpić <xref:System.Diagnostics.TraceListener.Fail%2A?displayProperty=fullName> metodę zapisu do dziennika zdarzeń zamiast wyświetlania okna dialogowego **potwierdzenie nie powiodło się** .

 Aby dostosować dane wyjściowe w ten sposób, program musi zawierać odbiornik i należy go dziedziczyć <xref:System.Diagnostics.TraceListener> i zastąpić jego <xref:System.Diagnostics.TraceListener.Fail%2A?displayProperty=fullName> metodę.

 Aby uzyskać więcej informacji, zobacz [detektory śledzenia](/dotnet/framework/debug-trace-profile/trace-listeners).

 [W tym temacie](#BKMK_In_this_topic)

## <a name="setting-assertions-in-configuration-files"></a><a name="BKMK_Setting_assertions_in_configuration_files"></a> Ustawianie potwierdzeń w plikach konfiguracji
 Można ustawić potwierdzenia w pliku konfiguracyjnym programu oraz w kodzie. Aby uzyskać więcej informacji, zobacz <xref:System.Diagnostics.Trace.Assert%2A?displayProperty=fullName> lub <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=fullName>.

## <a name="see-also"></a>Zobacz też

- <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=fullName>
- <xref:System.Diagnostics.Trace.Assert%2A?displayProperty=fullName>
- [Zabezpieczenia debugera](../debugger/debugger-security.md)
- [Śledzenie i instrumentowanie aplikacji](/dotnet/framework/debug-trace-profile/tracing-and-instrumenting-applications)
- [Instrukcje: Kompilowanie warunkowe ze śledzeniem i debugowaniem](/dotnet/framework/debug-trace-profile/how-to-compile-conditionally-with-trace-and-debug)
- [Typy projektów C#, F# i Visual Basic](../debugger/debugging-preparation-csharp-f-hash-and-visual-basic-project-types.md)
- [Debugowanie zarządzanego kodu](../debugger/debugging-managed-code.md)
