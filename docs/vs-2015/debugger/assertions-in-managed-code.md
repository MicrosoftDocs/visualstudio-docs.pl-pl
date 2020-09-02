---
title: Potwierdzenia w kodzie zarządzanym | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
- VB
- CSharp
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
caps.latest.revision: 32
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: ce0a416ef39165d38530c11aad0689811805b353
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "65702444"
---
# <a name="assertions-in-managed-code"></a>Potwierdzenia w zarządzanym kodzie
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Potwierdzenie lub `Assert` instrukcja, testuje warunek, który jest określany jako argument `Assert` instrukcji. Jeśli warunek ma wartość true, nie występuje żadna akcja. Jeśli warunek zwróci wartość false, potwierdzenie kończy się niepowodzeniem. W przypadku uruchamiania programu z kompilacją debugowania program wprowadza tryb przerwania.  
  
## <a name="in-this-topic"></a><a name="BKMK_In_this_topic"></a> W tym temacie  
 [Potwierdzenia w przestrzeni nazw System. Diagnostics](#BKMK_Asserts_in_the_System_Diagnostics_Namespace)  
  
 [Debug. Assert — Metoda](#BKMK_The_Debug_Assert_method)  
  
 [Efekty uboczne debugowania. Assert](#BKMK_Side_effects_of_Debug_Assert)  
  
 [Wymagania dotyczące śledzenia i debugowania](#BKMK_Trace_and_Debug_Requirements)  
  
 [Argumenty potwierdzenia](#BKMK_Assert_arguments)  
  
 [Dostosowywanie zachowania potwierdzenia](#BKMK_Customizing_Assert_behavior)  
  
 [Ustawianie potwierdzeń w plikach konfiguracji](#BKMK_Setting_assertions_in_configuration_files)  
  
## <a name="asserts-in-the-systemdiagnostics-namespace"></a><a name="BKMK_Asserts_in_the_System_Diagnostics_Namespace"></a> Potwierdzenia w przestrzeni nazw System. Diagnostics  
 W Visual Basic i Visual C#, można użyć `Assert` metody z <xref:System.Diagnostics.Debug> lub <xref:System.Diagnostics.Trace> , które znajdują się w <xref:System.Diagnostics> przestrzeni nazw. <xref:System.Diagnostics.Debug> metody klasy nie są uwzględnione w wydanej wersji programu, więc nie zwiększają rozmiaru ani nie zmniejszają szybkości kodu wydania.  
  
 Język C++ nie obsługuje <xref:System.Diagnostics.Debug> metod klasy. Ten sam efekt można osiągnąć przy użyciu <xref:System.Diagnostics.Trace> klasy z kompilacją warunkową, taką jak `#ifdef DEBUG` ... `#endif`  
  
 [W tym temacie](#BKMK_In_this_topic)  
  
## <a name="the-debugassert-method"></a><a name="BKMK_The_Debug_Assert_method"></a> Debug. Assert — Metoda  
 Użyj <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=fullName> metody swobodnej, aby sprawdzić warunki, które powinny mieć wartość PRAWDA, jeśli kod jest poprawny. Załóżmy na przykład, że Zapisano funkcję dzielenia liczb całkowitych. Według reguł matematycznych, dzielnik nie może być równy zero. Można to przetestować przy użyciu potwierdzenia:  
  
```vb  
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
  
 Gdy uruchamiasz ten kod w debugerze, zostanie oceniona instrukcja assertion, ale w wersji wydanej nie zostanie wykonane porównanie, więc nie ma dodatkowych kosztów.  
  
 Oto inny przykład. Masz klasę implementującą konto sprawdzania w następujący sposób:  
  
```vb  
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
  
```vb  
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
 Gdy używasz <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=fullName> , upewnij się, że żaden kod wewnątrz `Assert` nie zmienia wyników programu, jeśli `Assert` został usunięty. W przeciwnym razie można przypadkowo wprowadzić usterkę, która jest wyświetlana tylko w wydaniu wersji programu. Należy zwrócić szczególną uwagę na temat potwierdzeń, które zawierają wywołania funkcji lub procedur, takie jak Poniższy przykład:  
  
```vb  
' unsafe code  
Debug.Assert (meas(i) <> 0 )  
```  
  
```csharp  
// unsafe code  
Debug.Assert (meas(i) != 0 );  
```  
  
 To użycie <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=fullName> może wydawać się w pierwszej kolejności, ale Załóżmy, że funkcja MEAS aktualizuje licznik przy każdym wywołaniu. Podczas kompilowania wersji wydania to wywołanie do MEAS jest eliminowane, więc licznik nie zostanie zaktualizowany. Jest to przykład funkcji z efektem ubocznym. Usunięcie wywołania funkcji, która ma efekty uboczne, może spowodować błąd, który pojawia się tylko w wersji Release. Aby uniknąć takich problemów, nie należy umieszczać wywołań funkcji w <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=fullName> instrukcji. Zamiast tego użyj zmiennej tymczasowej:  
  
```vb  
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
 Jeśli tworzysz projekt przy użyciu [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] kreatorów, symbol śledzenia jest definiowany domyślnie w konfiguracjach wersji i debugowania. Symbol debugowania jest definiowany domyślnie tylko w kompilacji debugowania.  
  
 W przeciwnym razie, aby <xref:System.Diagnostics.Trace> metody działały, program musi mieć jedną z następujących wartości w górnej części pliku źródłowego:  
  
- `#Const TRACE = True` w Visual Basic  
  
- `#define TRACE` w językach Visual C# i C++  
  
  Lub program musi być skompilowany przy użyciu opcji śledzenia:  
  
- `/d:TRACE=True` w Visual Basic  
  
- `/d:TRACE` w językach Visual C# i C++  
  
  Jeśli musisz użyć metod debugowania w kompilacji w języku C# lub Visual Basic, musisz zdefiniować symbol debugowania w konfiguracji wydania.  
  
  Język C++ nie obsługuje <xref:System.Diagnostics.Debug> metod klasy. Ten sam efekt można osiągnąć przy użyciu <xref:System.Diagnostics.Trace> klasy z kompilacją warunkową, taką jak `#ifdef DEBUG` ... `#endif` Można zdefiniować te symbole w oknie dialogowym ** \<Project> strony właściwości** . Aby uzyskać więcej informacji, zobacz [Zmiana ustawień projektu dla konfiguracji debugowania Visual Basic](../debugger/project-settings-for-a-visual-basic-debug-configuration.md) lub [Zmiana ustawień projektu dla konfiguracji debugowania C lub C++](../debugger/project-settings-for-a-cpp-debug-configuration.md).  
  
## <a name="assert-arguments"></a><a name="BKMK_Assert_arguments"></a> Argumenty potwierdzenia  
 <xref:System.Diagnostics.Trace.Assert%2A?displayProperty=fullName> i <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=fullName> zapoznaj się z trzema argumentami. Pierwszy argument, który jest obowiązkowy, to warunek, który chcesz sprawdzić. W przypadku wywołania <xref:System.Diagnostics.Trace.Assert%28System.Boolean%29?displayProperty=fullName> lub <xref:System.Diagnostics.Debug.Assert%28System.Boolean%29?displayProperty=fullName> z tylko jednym argumentem `Assert` Metoda sprawdza warunek i, jeśli wynik ma wartość false, wyprowadza zawartość stosu wywołań do okna **danych wyjściowych** . Poniższy przykład przedstawia <xref:System.Diagnostics.Trace.Assert%28System.Boolean%29?displayProperty=fullName> i <xref:System.Diagnostics.Debug.Assert%28System.Boolean%29?displayProperty=fullName> :  
  
```vb  
Debug.Assert(stacksize > 0)  
Trace.Assert(stacksize > 0)  
```  
  
```csharp  
Debug.Assert ( stacksize > 0 );  
Trace.Assert ( stacksize > 0 );   
```  
  
 Drugi i trzeci argument, jeśli istnieją, muszą być ciągami. W przypadku wywołania <xref:System.Diagnostics.Trace.Assert%2A?displayProperty=fullName> lub <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=fullName> z dwoma lub trzema argumentami, pierwszym argumentem jest warunek. Metoda sprawdza warunek i, jeśli wynik ma wartość false, wyprowadza drugi ciąg i trzecie ciągi. Poniższy przykład ilustruje <xref:System.Diagnostics.Debug.Assert%28System.Boolean%2CSystem.String%29?displayProperty=fullName> i jest <xref:System.Diagnostics.Trace.Assert%28System.Boolean%2CSystem.String%29?displayProperty=fullName> używany z dwoma argumentami:  
  
```vb  
Debug.Assert(stacksize > 0, "Out of stack space")  
Trace.Assert(stacksize > 0, "Out of stack space")  
```  
  
```csharp  
Debug.Assert ( stacksize > 0, "Out of stack space" );  
Trace.Assert ( stacksize > 0, "Out of stack space" );  
```  
  
 Poniższy przykład przedstawia <xref:System.Diagnostics.Debug.Assert%2A> i <xref:System.Diagnostics.Trace.Assert%2A> :  
  
```vb  
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
  
 Aby uzyskać więcej informacji, zobacz [detektory śledzenia](https://msdn.microsoft.com/library/444b0d33-67ea-4c36-9e94-79c50f839025).  
  
 [W tym temacie](#BKMK_In_this_topic)  
  
## <a name="setting-assertions-in-configuration-files"></a><a name="BKMK_Setting_assertions_in_configuration_files"></a> Ustawianie potwierdzeń w plikach konfiguracji  
 Można ustawić potwierdzenia w pliku konfiguracyjnym programu oraz w kodzie. Aby uzyskać więcej informacji, zobacz <xref:System.Diagnostics.Trace.Assert%2A?displayProperty=fullName> lub <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=fullName>.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=fullName>   
 <xref:System.Diagnostics.Trace.Assert%2A?displayProperty=fullName>   
 [Zabezpieczenia debugera](../debugger/debugger-security.md)   
 [Śledzenie i Instrumentacja aplikacji](https://msdn.microsoft.com/library/773b6fc4-9013-4322-b728-5dec7a72e743)   
 [Instrukcje: kompilowanie warunkowe za pomocą śledzenia i debugowania](https://msdn.microsoft.com/library/56d051c3-012c-42c1-9a58-7270edc624aa)   
 [Typy projektów C#, F # i Visual Basic](../debugger/debugging-preparation-csharp-f-hash-and-visual-basic-project-types.md)   
 [Debugowanie zarządzanego kodu](../debugger/debugging-managed-code.md)
