---
title: Potwierdzenia w zarządzanym kodzie | Dokumentacja firmy Microsoft
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
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: a2637e801ba0d317e4c0abec8bd12197656dc844
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "60067407"
---
# <a name="assertions-in-managed-code"></a>Potwierdzenia w zarządzanym kodzie
Na potwierdzenie lub `Assert` instrukcji sprawdza warunek, który jest określony jako argument do `Assert` instrukcji. Jeśli warunek jest spełniony, występuje żadna akcja. Gdy warunek jest spełniony, potwierdzenie nie powiedzie się. Jeśli korzystasz z kompilacji debugowania, programach przechodzi w tryb podziału.

## <a name="BKMK_In_this_topic"></a> W tym temacie
 [Potwierdzenia w Namespace System.Diagnostics](#BKMK_Asserts_in_the_System_Diagnostics_Namespace)

 [Debug.Assert — metoda](#BKMK_The_Debug_Assert_method)

 [Efekty uboczne Debug.Assert](#BKMK_Side_effects_of_Debug_Assert)

 [Wymagania debugowania i śledzenia](#BKMK_Trace_and_Debug_Requirements)

 [Asercja argumentów](#BKMK_Assert_arguments)

 [Dostosowywanie zachowania dotyczącego Assert](#BKMK_Customizing_Assert_behavior)

 [Ustawienie potwierdzenia w plikach konfiguracji](#BKMK_Setting_assertions_in_configuration_files)

## <a name="BKMK_Asserts_in_the_System_Diagnostics_Namespace"></a> Potwierdzenia w Namespace System.Diagnostics
 W języku Visual Basic i Visual C#, można użyć `Assert` z jednej metody <xref:System.Diagnostics.Debug> lub <xref:System.Diagnostics.Trace>, które znajdują się w <xref:System.Diagnostics> przestrzeni nazw. <xref:System.Diagnostics.Debug> metody klasy nie są uwzględnione w wersji programu, więc nie zwiększenie rozmiaru lub zmniejsz szybkość wersji kodu.

 Język C++ nie obsługuje <xref:System.Diagnostics.Debug> metody klasy. Ten sam efekt można osiągnąć za pomocą <xref:System.Diagnostics.Trace> klasy kompilacji warunkowej, takie jak `#ifdef DEBUG`... `#endif`.

 [W tym temacie](#BKMK_In_this_topic)

## <a name="BKMK_The_Debug_Assert_method"></a> Debug.Assert — metoda
 Użyj <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=fullName> metoda za darmo, aby przetestować warunki, które mają być przechowywane w wartość true, jeśli Twój kod jest poprawny. Na przykład załóżmy, że zostały napisane Funkcja dzielenia liczby całkowitej. Przez reguły matematyce dzielnik nigdy nie może być równy zero. Może to przetestować za pomocą potwierdzenia:

```VB
Function IntegerDivide(ByVal dividend As Integer, ByVal divisor As Integer) As Integer
    Debug.Assert(divisor <> 0)
    Return CInt(dividend / divisor)
End Function
```

```csharp
int IntegerDivide ( int dividend , int divisor )
    { Debug.Assert ( divisor != 0 );
        return ( dividend / divisor ); }
```

 Podczas uruchamiania tego kodu w debugerze, instrukcji asercji jest obliczane, ale w wersji, nie dokonywane jest porównanie, więc istnieje bez dodatkowych nakładów.

 Oto inny przykład. Masz klasę, która implementuje konta rozliczeniowego, w następujący sposób:

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

 Przed pieniądze wycofać się z konta, która ma być upewnij się, że saldo konta jest wystarczające, aby objąć kwotę, które są przygotowania do wycofania. Można napisać potwierdzenie, aby sprawdzić saldo:

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

 Należy zauważyć, że wywołania <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=fullName> metoda zniknąć po utworzeniu wersji kodu. Oznacza to, że wywołanie, które sprawdza, czy saldo znika w pełnej wersji. Aby rozwiązać ten problem, należy zastąpić <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=fullName> z <xref:System.Diagnostics.Trace.Assert%2A?displayProperty=fullName>, której nie znika w wersji:

 Wywołania <xref:System.Diagnostics.Trace.Assert%2A?displayProperty=fullName> obciążenie dodać do swojej wersji, w przeciwieństwie do wywołania <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=fullName>.

 [W tym temacie](#BKMK_In_this_topic)

## <a name="BKMK_Side_effects_of_Debug_Assert"></a> Efekty uboczne Debug.Assert
 Kiedy używasz <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=fullName>, upewnij się, że dowolny kod `Assert` nie zmienia wyniki program, jeśli `Assert` zostanie usunięty. W przeciwnym razie może przypadkowo wprowadzone usterki, które są wyświetlane tylko w wersji programu. Należy zachować szczególną ostrożność około potwierdza, które zawierają funkcji lub procedury wywołań, takich jak na poniższym przykładzie:

```VB
' unsafe code
Debug.Assert (meas(i) <> 0 )
```

```csharp
// unsafe code
Debug.Assert (meas(i) != 0 );
```

 Użycie tego <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=fullName> mogą być wyświetlane na pierwszy rzut oka bezpieczne, ale Załóżmy, że meas funkcji aktualizacji licznika każdym razem jest wywoływana. Podczas tworzenia wersji to wywołanie meas została pominięta, więc ten licznik nie zostaje zaktualizowana. Jest to przykład funkcji z atrybutem efekt uboczny. Wywołanie funkcji, która ma efekty uboczne, eliminując może spowodować usterkę, która jest wyświetlana tylko w pełnej wersji. Aby uniknąć tych problemów, nie należy umieszczać wywołania funkcji w <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=fullName> instrukcji. Zamiast tego użyj zmienna tymczasowa:

```VB
temp = meas( i )
Debug.Assert (temp <> 0)
```

```csharp
temp = meas( i );
Debug.Assert ( temp != 0 );
```

 Nawet jeśli używasz <xref:System.Diagnostics.Trace.Assert%2A?displayProperty=fullName>, może nadal chcesz uniknąć umieszczenie wywołania funkcji wewnątrz `Assert` instrukcji. Takie połączenia powinny być bezpieczne, ponieważ <xref:System.Diagnostics.Trace.Assert%2A?displayProperty=fullName> instrukcje nie są eliminowane kompilację wydania. Jednak jeśli uniknąć takich konstrukcji ewentualnemu przyzwyczajenia prawdopodobnie mniej popełnienia błędu w przypadku, gdy używasz <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=fullName>.

 [W tym temacie](#BKMK_In_this_topic)

## <a name="BKMK_Trace_and_Debug_Requirements"></a> Wymagania debugowania i śledzenia
 Jeśli tworzysz projekt przy użyciu [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] kreatorów, symbol śledzenia jest zdefiniowana w konfiguracji wydania i debugowania. Symbol debugowania jest definiowany przez domyślne tylko w kompilacji debugowania.

 W przeciwnym razie dla <xref:System.Diagnostics.Trace> metody do pracy, program musi mieć jedną z następujących czynności w górnej części pliku źródłowego:

- `#Const TRACE = True` W języku Visual Basic

- `#define TRACE` w środowisku Visual C# i C++

  Lub program muszą zostać skompilowane przy użyciu opcji śledzenia:

- `/d:TRACE=True` W języku Visual Basic

- `/d:TRACE` w środowisku Visual C# i C++

  W przypadku należy użyć metody debugowania w języku C# lub Visual Basic wersji kompilacji, zdefiniuj symbol debugowania w konfiguracji wydania.

  Język C++ nie obsługuje <xref:System.Diagnostics.Debug> metody klasy. Ten sam efekt można osiągnąć za pomocą <xref:System.Diagnostics.Trace> klasy kompilacji warunkowej, takie jak `#ifdef DEBUG`... `#endif`. Można zdefiniować te symbole w  **\<Projekt > strony właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [Zmienianie ustawienia projektu dla konfiguracji debugowania języka Visual Basic](../debugger/project-settings-for-a-visual-basic-debug-configuration.md) lub [Zmienianie ustawienia projektu dla konfiguracji debugowania języka C++ lub C](../debugger/project-settings-for-a-cpp-debug-configuration.md).

## <a name="BKMK_Assert_arguments"></a> Asercja argumentów
 <xref:System.Diagnostics.Trace.Assert%2A?displayProperty=fullName> i <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=fullName> zająć maksymalnie trzy argumenty. Pierwszy argument, który jest wymagany, jest warunek, który chcesz sprawdzić. Jeśli wywołasz <xref:System.Diagnostics.Trace.Assert(System.Boolean)?displayProperty=fullName> lub <xref:System.Diagnostics.Debug.Assert(System.Boolean)?displayProperty=fullName> z tylko jednym argumentem, `Assert` metoda sprawdza warunek i, jeśli wynikiem jest wartość FAŁSZ, wyświetla zawartość stosu wywołań, aby **dane wyjściowe** okna. W poniższym przykładzie przedstawiono <xref:System.Diagnostics.Trace.Assert(System.Boolean)?displayProperty=fullName> i <xref:System.Diagnostics.Debug.Assert(System.Boolean)?displayProperty=fullName>:

```VB
Debug.Assert(stacksize > 0)
Trace.Assert(stacksize > 0)
```

```csharp
Debug.Assert ( stacksize > 0 );
Trace.Assert ( stacksize > 0 );
```

 Jeśli jest obecny, drugi i trzeci argument musi być ciągami. Jeśli wywołasz <xref:System.Diagnostics.Trace.Assert%2A?displayProperty=fullName> lub <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=fullName> przy użyciu dwóch lub trzech argumentów, pierwszy argument jest warunek. Metoda sprawdza warunek i, jeśli wynikiem jest wartość FAŁSZ, dane wyjściowe ciągu drugiego i trzeciego ciągi. W poniższym przykładzie przedstawiono <xref:System.Diagnostics.Debug.Assert(System.Boolean,System.String)?displayProperty=fullName> i <xref:System.Diagnostics.Trace.Assert(System.Boolean,System.String)?displayProperty=fullName> używane w przypadku dwóch argumentów:

```VB
Debug.Assert(stacksize > 0, "Out of stack space")
Trace.Assert(stacksize > 0, "Out of stack space")
```

```csharp
Debug.Assert ( stacksize > 0, "Out of stack space" );
Trace.Assert ( stacksize > 0, "Out of stack space" );
```

 W poniższym przykładzie przedstawiono <xref:System.Diagnostics.Debug.Assert%2A> i <xref:System.Diagnostics.Trace.Assert%2A>:

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

## <a name="BKMK_Customizing_Assert_behavior"></a> Dostosowywanie zachowania dotyczącego Assert
 Jeśli uruchomisz aplikację w trybie interfejsu użytkownika `Assert` metoda Wyświetla **potwierdzenie nie powiodło się** okno dialogowe, gdy warunek nie powiodło się. Akcje, które występują, gdy nie powiedzie się potwierdzenie są kontrolowane przez <xref:System.Diagnostics.Debug.Listeners%2A> lub <xref:System.Diagnostics.Trace.Listeners%2A> właściwości.

 Zachowanie danych wyjściowych można dostosować, dodając <xref:System.Diagnostics.TraceListener> obiekt `Listeners` kolekcji, usuwając <xref:System.Diagnostics.TraceListener> z `Listeners` kolekcji, lub poprzez zastąpienie <xref:System.Diagnostics.TraceListener.Fail%2A?displayProperty=fullName> metoda istniejącego `TraceListener` się to zachowują się inaczej.

 Na przykład, można zastąpić <xref:System.Diagnostics.TraceListener.Fail%2A?displayProperty=fullName> metodę do zapisu do dziennika zdarzeń, zamiast **potwierdzenie nie powiodło się** okno dialogowe.

 Aby dostosować dane wyjściowe w ten sposób, program musi zawierać odbiornik i musi dziedziczyć <xref:System.Diagnostics.TraceListener> i zastąpić jej <xref:System.Diagnostics.TraceListener.Fail%2A?displayProperty=fullName> metody.

 Aby uzyskać więcej informacji, zobacz [detektorów śledzenia](/dotnet/framework/debug-trace-profile/trace-listeners).

 [W tym temacie](#BKMK_In_this_topic)

## <a name="BKMK_Setting_assertions_in_configuration_files"></a> Ustawienie potwierdzenia w plikach konfiguracji
 Potwierdzenia można ustawić w pliku konfiguracyjnym programu także, jak w poniższym kodzie. Aby uzyskać więcej informacji, zobacz <xref:System.Diagnostics.Trace.Assert%2A?displayProperty=fullName> lub <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=fullName>.

## <a name="see-also"></a>Zobacz też

- <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=fullName>
- <xref:System.Diagnostics.Trace.Assert%2A?displayProperty=fullName>
- [Zabezpieczenia debugera](../debugger/debugger-security.md)
- [Śledzenie i instrumentacja aplikacji](/dotnet/framework/debug-trace-profile/tracing-and-instrumenting-applications)
- [Instrukcje: Kompilowanie warunkowe ze śledzeniem i debugowaniem](/dotnet/framework/debug-trace-profile/how-to-compile-conditionally-with-trace-and-debug)
- [Typy projektów C#, F# i Visual Basic](../debugger/debugging-preparation-csharp-f-hash-and-visual-basic-project-types.md)
- [Debugowanie kodu zarządzanego](../debugger/debugging-managed-code.md)