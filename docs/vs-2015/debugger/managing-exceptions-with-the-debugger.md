---
title: Zarządzanie wyjątkami za pomocą debugera | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.exceptions
- vs.debug.exceptions.find
dev_langs:
- FSharp
- VB
- CSharp
- C++
- JScript
helpviewer_keywords:
- run-time errors
- exception handling, during debugging
- errors [debugger]
- debugger, runtime errors
- On Error-style error handlers
- exceptions, Win32
- run-time errors, debugging
- Win32, exceptions
- run time, exceptions
- error handling
- debugging [Visual Studio], exception handling
- common language runtime, exceptions
- native run-time checks
- exceptions, debugging
ms.assetid: 43a77fa8-37d0-4c98-a334-0134dbca4ece
caps.latest.revision: 40
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: be15b683a6e173d813ea13eaa0cc400a40e68206
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2019
ms.locfileid: "65690508"
---
# <a name="managing-exceptions-with-the-debugger"></a>Zarządzanie wyjątkami za pomocą debugera
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Wyjątek jest wskazaniem stanu błędu, który występuje, gdy program jest wykonywane. Może i powinno zapewniać obsługi reagujące na najważniejszych wyjątków, ale ważne jest, aby dowiedzieć się, jak skonfigurować debuger w celu przerwania do obsługi wyjątków, które mają być wyświetlane.  
  
 Gdy wystąpi wyjątek, debuger zapisuje komunikat o wyjątku w oknie danych wyjściowych. Może je przerwać wykonywanie w następujących przypadkach:  
  
- Gdy wyjątek jest wyrzucany i nie jest obsługiwany.  
  
- gdy debuger jest równa przerwać wykonywanie natychmiast, gdy wyjątek jest zgłaszany, zanim wywoływana zostanie jakakolwiek Obsługa.  
  
- Jeśli ustawiono [tylko mój kod](../debugger/just-my-code.md), a debuger jest ustawiona na przerwanie przy każdym wyjątku, który nie jest obsługiwany w kodzie użytkownika.  
  
> [!NOTE]
> Program ASP.NET ma program obsługi wyjątków najwyższego poziomu, pokazujący stron błędów, które w przeglądarce. Go nie Przerwij wykonywanie, chyba że **tylko mój kod** jest włączona. Aby uzyskać przykład, zobacz [ustawienia debugera, aby kontynuować na wyjątkach nieobsługiwanych przez użytkownika](../debugger/managing-exceptions-with-the-debugger.md#BKMK_UserUnhandled) poniżej.  
  
> [!NOTE]
> W aplikacji Visual Basic debuger zarządza wszystkie błędy jako wyjątki, nawet jeśli jest używana w stylu błędu obsługi błędów.  
  
## <a name="managing-exceptions-with-the-exception-settings-window"></a>Zarządzanie wyjątkami za pomocą okno ustawień wyjątków  
 Możesz użyć **ustawienia wyjątków** okna, aby określić wyjątki (lub zestawy wyjątki) spowoduje, że debuger przerywa, a w tym momencie chcesz przerwać. Dodawanie lub usuwanie wyjątków lub określić wyjątki, aby przerywał działanie w przypadku. Otwarcie tego okna, które rozwiązanie jest otwarte, klikając **debugowanie / Windows / Ustawienia wyjątków**.  
  
 Możesz znaleźć określone wyjątki za pomocą **wyszukiwania** okna **ustawienia wyjątków** paska narzędzi lub użyj Wyszukaj, aby filtrować dla określonych przestrzeni nazw (na przykład **System.IO**).  
  
### <a name="setting-the-debugger-to-break-when-an-exception-is-thrown"></a>Ustawienie debuger na przerwanie, gdy zostanie zgłoszony wyjątek  
 Debuger może przerwać wykonywanie w punkcie, gdzie jest zgłaszany wyjątek, dając Ci zbadać wyjątku przed wywołaniem programu obsługi.  
  
 W **ustawienia wyjątków** okna, rozwiń węzeł kategorii wyjątków (na przykład **wyjątki środowiska uruchomieniowego języka wspólnego**, co oznacza wyjątki platformy .NET), a następnie zaznacz pole wyboru dla określonego wyjątek w ramach tej kategorii (na przykład **System.AccessViolationException**). Możesz również wybrać całej kategorii wyjątków.  
  
 ![Zaznaczone AccessViolationException](../debugger/media/exceptionsettingscheckaccess.png "ExceptionSettingsCheckAccess")  
  
 Jeśli zaznaczysz dany wyjątek, wykonanie debuger przerywał działanie wszędzie tam, gdzie jest zgłaszany wyjątek, niezależnie od tego, czy jest obsługiwane i nieobsługiwane. W tym momencie wyjątek nosi nazwę wyjątku pierwszej szansy. Na przykład poniżej przedstawiono kilka scenariuszy:  
  
1. W poniższym aplikacji konsolowej C#, metoda Main zgłasza **AccessViolationException** wewnątrz `try/catch` bloku:  
  
   ```csharp  
   static void Main(string[] args)  
   {  
       try  
       {  
           throw new AccessViolationException();  
           Console.WriteLine("here");  
       }  
       catch (Exception e)  
       {  
           Console.WriteLine("caught exception");  
       }  
       Console.WriteLine("goodbye");  
   }  
   ```  
  
    Jeśli masz **AccessViolationException** zaewidencjonowany **ustawienia wyjątków**, po uruchomieniu tego kodu podczas wykonywania debuger przerywał działanie w `throw` wiersza. Następnie można kontynuować wykonywania. Obie linie powinien być wyświetlany w konsoli:  
  
   ```  
   caught exception  
   goodbye  
   ```  
  
    ale nie są wyświetlane `here` wiersza.  
  
2. Aplikacja konsolowa C# odwołuje się do biblioteki klas w języku klasę, która ma dwie metody, metoda zgłasza wyjątek, która obsługuje je i druga metoda, ten sam wyjątek, który nie obsługuje ona:  
  
   ```vb  
   public class Class1  
   {  
       public void ThrowHandledException()  
       {  
           try  
           {  
               throw new AccessViolationException();  
           }  
           catch (AccessViolationException ave)  
           {  
               Console.WriteLine("caught exception" + ave.Message);  
           }  
       }  
  
       public void ThrowUnhandledException()  
       {  
           throw new AccessViolationException();  
       }  
   }  
   ```  
  
    Poniżej przedstawiono metody Main() aplikacji konsoli:  
  
   ```csharp  
   static void Main(string[] args)  
   {  
       Class1 class1 = new Class1();  
       class1.ThrowHandledException();  
       class1.ThrowUnhandledException();  
   }  
   ```  
  
    Jeśli masz **AccessViolationException** zaewidencjonowany **ustawienia wyjątków**, po uruchomieniu tego kodu podczas wykonywania debuger przerywał działanie w `throw` wiersza w obu  **ThrowHandledException()** i **ThrowUnhandledException()**.  
  
   Jeśli chcesz przywrócić ustawienia domyślne ustawienia wyjątków, możesz kliknąć **przywrócić** przycisk na pasku narzędzi:  
  
   ![Przywróć ustawienia domyślne w ustawieniach wyjątek](../debugger/media/restoredefaultexceptions.png "RestoreDefaultExceptions")  
  
### <a name="BKMK_UserUnhandled"></a> Ustawienia debugera, aby kontynuować na wyjątkach nieobsługiwanych przez użytkownika  
 Jeśli debugujesz kod .NET lub języka JavaScript za pomocą [tylko mój kod](../debugger/just-my-code.md), można polecić debugerowi, które nie do przerwy na wyjątki, które nie są obsługiwane w kodzie użytkownika, ale są obsługiwane w innym miejscu.  
  
1. W **ustawienia wyjątków** okna, otwórz menu kontekstowe, klikając prawym przyciskiem myszy w oknie, a następnie wybierając **Pokaż kolumny**. (Jeśli wyłączysz **tylko mój kod**, nie zobaczysz tego polecenia.)  
  
2. Powinien zostać wyświetlony drugi kolumnę o nazwie **dodatkowe akcje**. Tej kolumnie jest wyświetlana **Kontynuuj w przypadku braku obsługi przez kod użytkownika** na określone wyjątki, co oznacza, że debuger nie przerwanie działania tego wyjątku nie jest obsługiwany w kodzie użytkownika, ale jest obsługiwany w kodzie zewnętrznych.  
  
3. Możesz zmienić to ustawienie, albo dla określonego wyjątku (wybierz wyjątek, kliknij prawym przyciskiem myszy i wybierz opcję/odznacz **Kontynuuj w przypadku braku obsługi w kodzie użytkownika**) lub dla całej kategorii wyjątków (na przykład wszystkie wspólne Wyjątki środowiska uruchomieniowego języka).  
  
   Na przykład aplikacji sieci web ASP.NET obsługi wyjątków, konwertując je na kod stanu HTTP 500 ([obsługi wyjątków w interfejsie ASP.NET API](http://www.asp.net/web-api/overview/error-handling/exception-handling)), który może nie pomocne podczas określania źródło wyjątku. W poniższym przykładzie kod użytkownika wywołuje `String.Format()` która zgłasza <xref:System.FormatException>. Wykonanie przerywa w następujący sposób:  
  
   ![przerywa użytkownika&#45;wyjątek unhanlded](../debugger/media/exceptionunhandledbyuser.png "ExceptionUnhandledByUser")  
  
### <a name="adding-and-deleting-exceptions"></a>Dodawanie i usuwanie wyjątków  
 Można dodawać i usuwać wyjątki. Możesz usunąć dowolny typ wyjątku z każdej kategorii, wybierając wyjątek i klikając **Usuń** przycisku (znak minus) na **ustawienia wyjątków** paska narzędzi lub klikając prawym przyciskiem myszy wyjątek i Wybieranie **Usuń** z menu kontekstowego. Usuwanie wyjątek działa tak samo jako posiadające wyjątek nie jest zaznaczone, który jest debugera nie będę powodować gdy jest generowany.  
  
 Aby dodać wyjątek: w **ustawienia wyjątków** okna, wybierz jedną z kategorii wyjątków (na przykład **środowiska uruchomieniowego języka wspólnego**) i kliknij przycisk **Dodaj** przycisku. Wpisz nazwę wyjątku (np.) **System.UriTemplateMatchException**). Wyjątek zostanie dodany do listy (w kolejności alfabetycznej) i zostanie automatycznie zaznaczone.  
  
 Jeśli chcesz dodać wyjątek wyjątki dostępu do pamięci procesora GPU, wyjątki środowiska uruchomieniowego JavaScript lub kategorii wyjątki Win32, konieczne jest uwzględnienie kodu błędu, a także opis.  
  
> [!TIP]
> Sprawdź pisownię! **Ustawienia wyjątków** okna nie sprawdza istnienie dodano wyjątek. Tak, jeśli wpiszesz **Sytem.UriTemplateMatchException**, otrzymasz wpis dla tego wyjątku (a nie **System.UriTemplateMatchException**).  
  
 Ustawienia wyjątków są utrwalane w pliku .suo rozwiązania, dzięki czemu mają one zastosowanie do danego rozwiązania. Nie można ponownie użyć ustawienia określonego wyjątku w rozwiązań. W tym momencie są utrwalane tylko wyjątków dodanych; Usunięto wyjątki nie są. Innymi słowy możesz dodać wyjątek, zamknij i ponownie otwórz rozwiązanie, a wyjątek będą nadal dostępne. Ale jeśli usuniesz wyjątek, a Zamknij i otwórz ponownie rozwiązanie, pojawi się wyjątek.  
  
 **Ustawienia wyjątków** okna obsługuje typów wyjątków ogólnych w języku C#, ale nie w języku Visual Basic. Przerwanie przy wyjątkach, takich jak `MyNamespace.GenericException<T>`, należy dodać wyjątek jako **MyNamespace.GenericException'1**. Oznacza to jeśli został utworzony wyjątek następująco:  
  
```csharp  
public class GenericException<T> : Exception  
{  
    public GenericException() : base("This is a generic exception.")  
    {  
    }  
}  
```  
  
 Możesz dodać wyjątek **ustawienia wyjątków** następująco:  
  
 ![Dodawanie wyjątek ogólny](../debugger/media/addgenericexception.png "AddGenericException")  
  
## <a name="see-also"></a>Zobacz też  
 [Kontynuowanie wykonania po wystąpieniu wyjątku](../debugger/continuing-execution-after-an-exception.md)   
 [Instrukcje: Badanie kodu systemu po wystąpieniu wyjątku](../debugger/how-to-examine-system-code-after-an-exception.md)   
 [Instrukcje: Korzystanie z macierzystego sprawdzania w czasie wykonywania](../debugger/how-to-use-native-run-time-checks.md)   
 [Za pomocą środowiska wykonawczego sprawdza, czy bez biblioteki wykonawczej języka C](../debugger/using-run-time-checks-without-the-c-run-time-library.md)   
 [Asystent wyjątków](https://msdn.microsoft.com/library/992892ac-9d52-44cc-bf09-b44bfc5befeb)   
 [Podstawowe informacje o debugerze](../debugger/debugger-basics.md)
