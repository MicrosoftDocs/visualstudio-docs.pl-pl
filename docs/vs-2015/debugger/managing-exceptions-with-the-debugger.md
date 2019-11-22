---
title: Zarządzanie wyjątkami za pomocą debugera | Microsoft Docs
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
ms.openlocfilehash: 5303a8003d84af5e2a059d9f509e560204afa528
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2019
ms.locfileid: "74301095"
---
# <a name="managing-exceptions-with-the-debugger"></a>Zarządzanie wyjątkami za pomocą debugera
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Wyjątek jest wskazaniem stanu błędu, który występuje, gdy program jest wykonywane. Można i zapewnić obsługę, która odpowiada na najważniejsze wyjątki, ale ważne jest, aby wiedzieć, jak skonfigurować debuger do przerwania dla wyjątków, które mają być wyświetlane.  
  
 Gdy wystąpi wyjątek, debuger zapisuje komunikat o wyjątku w oknie danych wyjściowych. Może przerwać wykonywanie w następujących przypadkach:  
  
- gdy wyjątek jest zgłaszany i nie jest obsługiwany.  
  
- gdy debuger jest ustawiony do przerwania wykonywania natychmiast po zgłoszeniu wyjątku, przed wywołaniem jakiejkolwiek procedury obsługi.  
  
- Jeśli ustawiono [tylko mój kod](../debugger/just-my-code.md), a debuger jest ustawiony na Break dla dowolnego wyjątku, który nie jest obsługiwany w kodzie użytkownika.  
  
> [!NOTE]
> Program ASP.NET ma program obsługi wyjątków najwyższego poziomu, pokazujący stron błędów, które w przeglądarce. Nie przerywa wykonywania, chyba że **tylko mój kod** jest włączona. Aby zapoznać się z przykładem, zobacz [Ustawianie debugera, aby kontynuować Nieobsłużone wyjątki](../debugger/managing-exceptions-with-the-debugger.md#BKMK_UserUnhandled) poniżej.  
  
> [!NOTE]
> W aplikacji Visual Basic debuger zarządza wszystkimi błędami jako wyjątkami, nawet jeśli jest używany w przypadku programów obsługi błędów w stylu błędu.  
  
## <a name="managing-exceptions-with-the-exception-settings-window"></a>Zarządzanie wyjątkami za pomocą okna Ustawienia wyjątku  
 Można użyć okna **Ustawienia wyjątku** , aby określić, które wyjątki (lub zestawy wyjątków) spowodują przerwanie działania debugera i w którym miejscu ma zostać przerwane. Możesz dodać lub usunąć wyjątki lub określić wyjątki, które mają zostać przerwane. Otwórz to okno, gdy rozwiązanie jest otwarte, klikając polecenie **Debuguj/ustawienia systemu Windows/wyjątków**.  
  
 Określone wyjątki można znaleźć za pomocą okna **wyszukiwania** na pasku narzędzi **Ustawienia wyjątku** lub użyć wyszukiwania do filtrowania określonych przestrzeni nazw (na przykład **System.IO**).  
  
### <a name="setting-the-debugger-to-break-when-an-exception-is-thrown"></a>Ustawienie debugera do przerwania w przypadku zgłoszenia wyjątku  
 Debuger może przerwać wykonywanie w punkcie, w którym wystąpił wyjątek, co daje możliwość sprawdzenia wyjątku przed wywołaniem programu obsługi.  
  
 W oknie **Ustawienia wyjątku** rozwiń węzeł kategorii wyjątków (na przykład **wyjątki środowiska uruchomieniowego języka wspólnego**, czyli wyjątki .NET), a następnie zaznacz pole wyboru dla określonego wyjątku w tej kategorii (na przykład **System. AccessViolationException**). Możesz również wybrać całej kategorii wyjątków.  
  
 ![Sprawdzone AccessViolationException](../debugger/media/exceptionsettingscheckaccess.png "ExceptionSettingsCheckAccess")  
  
 Jeśli sprawdzisz dany wyjątek, wykonanie debugera będzie przerywane wszędzie tam, gdzie wystąpi wyjątek, niezależnie od tego, czy jest on obsługiwany, czy nieobsługiwany. W tym momencie wyjątek jest wywoływany jako wyjątek pierwszej szansy. Na przykład poniżej przedstawiono kilka scenariuszy:  
  
1. W poniższej C# aplikacji konsolowej Metoda Main zgłasza **AccessViolationException** wewnątrz bloku `try/catch`:  
  
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
  
    Jeśli masz **AccessViolationException** zaznaczone **Ustawienia wyjątku**, po uruchomieniu tego kodu w ramach wykonywania debugera zostanie przerwane w wierszu `throw`. Następnie można kontynuować wykonywania. Obie linie powinien być wyświetlany w konsoli:  
  
   ```  
   caught exception  
   goodbye  
   ```  
  
    ale nie wyświetla `here` wiersza.  
  
2. Aplikacja C# konsolowa odwołuje się do biblioteki klas z klasą, która ma dwie metody, Metoda zwracająca wyjątek i obsługuje ją oraz drugą metodę, która zgłasza ten sam wyjątek i nie obsłuży:  
  
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
  
    Oto główna Metoda aplikacji konsolowej:  
  
   ```csharp  
   static void Main(string[] args)  
   {  
       Class1 class1 = new Class1();  
       class1.ThrowHandledException();  
       class1.ThrowUnhandledException();  
   }  
   ```  
  
    Jeśli **AccessViolationException** zaznaczono **Ustawienia wyjątków**, po uruchomieniu tego kodu w ramach wykonywania debugera program zacznie działać w wierszu `throw` w obu **ThrowHandledException ()** i **ThrowUnhandledException ()** .  
  
   Jeśli chcesz przywrócić ustawienia wyjątków do ustawień domyślnych, możesz kliknąć przycisk **Przywróć** na pasku narzędzi:  
  
   ![Przywróć wartości domyślne w ustawieniach wyjątku](../debugger/media/restoredefaultexceptions.png "RestoreDefaultExceptions")  
  
### <a name="BKMK_UserUnhandled"></a>Ustawianie debugera w celu kontynuowania wyjątków nieobsłużonych przez użytkownika  
 Jeśli debugujesz kod .NET lub JavaScript przy użyciu [tylko mój kod](../debugger/just-my-code.md), możesz poinstruować debuger, aby nie przerywał przerw w wyjątkach, które nie są obsługiwane w kodzie użytkownika, ale są obsługiwane w innym miejscu.  
  
1. W oknie **Ustawienia wyjątku** Otwórz menu kontekstowe, klikając prawym przyciskiem myszy w oknie, a następnie wybierając **Pokaż kolumny**. (Jeśli wyłączono **tylko mój kod**, to polecenie nie zostanie wyświetlone).  
  
2. Powinna zostać wyświetlona druga kolumna o nazwie **dodatkowe akcje**. Ta kolumna jest wyświetlana w **przypadku nieobsłużonych przez kod użytkownika** w określonych wyjątkach, co oznacza, że debuger nie przerywa działania, jeśli ten wyjątek nie jest obsługiwany w kodzie użytkownika, ale jest obsługiwany w kodzie zewnętrznym.  
  
3. To ustawienie można zmienić dla konkretnego wyjątku (wybierz wyjątek, kliknij prawym przyciskiem myszy, a następnie wybierz/Usuń zaznaczenie opcji **Kontynuuj w przypadku braku obsługi w kodzie użytkownika**) lub dla całej kategorii wyjątków (na przykład wszystkie wyjątki środowiska uruchomieniowego języka wspólnego).  
  
   Na przykład ASP.NET aplikacje sieci Web obsługują wyjątki poprzez konwersję ich do kodu stanu HTTP 500 ([Obsługa wyjątków w interfejsie API ASP.NET](https://docs.microsoft.com/aspnet/web-api/overview/error-handling/exception-handling)), co może nie pomóc w ustaleniu źródła wyjątku. W poniższym przykładzie kod użytkownika wywołuje `String.Format()` która zgłasza <xref:System.FormatException>. Wykonanie przerywa w następujący sposób:  
  
   ![przerwy w unhanlded&#45;użytkownika — wyjątek](../debugger/media/exceptionunhandledbyuser.png "ExceptionUnhandledByUser")  
  
### <a name="adding-and-deleting-exceptions"></a>Dodawanie i usuwanie wyjątków  
 Można dodawać i usuwać wyjątki. Każdy typ wyjątku można usunąć z dowolnej kategorii, wybierając wyjątek, a następnie klikając przycisk **Usuń** (znak minus) na pasku narzędzi **Ustawienia wyjątku** lub klikając prawym przyciskiem myszy wyjątek i wybierając polecenie **Usuń** z menu kontekstowego. Usuwanie wyjątku ma ten sam skutek, co w przypadku niezaznaczania wyjątku, co oznacza, że debuger nie będzie przerywany w momencie jego zgłoszenia.  
  
 Aby dodać wyjątek: w oknie **Ustawienia wyjątku** wybierz jedną z kategorii wyjątków (na przykład **środowisko uruchomieniowe języka wspólnego**), a następnie kliknij przycisk **Dodaj** . Wpisz nazwę wyjątku (na przykład. **System.UriTemplateMatchException**). Wyjątek jest dodawany do listy (w kolejności alfabetycznej) i jest automatycznie sprawdzany.  
  
 Jeśli chcesz dodać wyjątek do wyjątków dostępu do pamięci procesora GPU, wyjątków środowiska uruchomieniowego języka JavaScript lub kategorii wyjątków Win32, musisz dołączyć kod błędu, a także opis.  
  
> [!TIP]
> Sprawdź pisownię! Okno **Ustawienia wyjątku** nie sprawdza istnienia dodanego wyjątku. Dlatego jeśli wpiszesz system **. UriTemplateMatchException**, otrzymasz wpis dla tego wyjątku (a nie w przypadku **systemu. UriTemplateMatchException**).  
  
 Ustawienia wyjątków są utrwalane w pliku. suo rozwiązania, dlatego mają zastosowanie do określonego rozwiązania. Nie można ponownie użyć określonych ustawień wyjątków w różnych rozwiązaniach. W tym momencie tylko dodane wyjątki są utrwalane; usunięte wyjątki nie są. Innymi słowy, można dodać wyjątek, zamknąć i ponownie otworzyć rozwiązanie, a w dalszym ciągu będą nadal dostępne. Ale jeśli usuniesz wyjątek, a Zamknij i otwórz ponownie rozwiązanie, pojawi się wyjątek.  
  
 **Ustawienia wyjątków** okna obsługuje typów wyjątków ogólnych w języku C#, ale nie w języku Visual Basic. Przerwanie przy wyjątkach, takich jak `MyNamespace.GenericException<T>`, należy dodać wyjątek jako **MyNamespace.GenericException'1**. Oznacza to, że jeśli utworzono wyjątek podobny do tego:  
  
```csharp  
public class GenericException<T> : Exception  
{  
    public GenericException() : base("This is a generic exception.")  
    {  
    }  
}  
```  
  
 Wyjątek można dodać do **ustawień wyjątków** , takich jak:  
  
 ![Dodawanie wyjątku generycznego](../debugger/media/addgenericexception.png "Addgenericexception")  
  
## <a name="see-also"></a>Zobacz też  
 [Kontynuowanie wykonywania po  wyjątku](../debugger/continuing-execution-after-an-exception.md)  
 [Instrukcje: badanie kodu systemu po  wyjątku](../debugger/how-to-examine-system-code-after-an-exception.md)  
 [Instrukcje: korzystanie z natywnych sprawdzeń w czasie wykonywania](../debugger/how-to-use-native-run-time-checks.md)   
 [Używanie testów w czasie wykonywania bez biblioteki uruchomieniowej C](../debugger/using-run-time-checks-without-the-c-run-time-library.md)   
   [asystenta wyjątków](https://msdn.microsoft.com/library/992892ac-9d52-44cc-bf09-b44bfc5befeb)  
 [Podstawowe informacje o debugerze](../debugger/debugger-basics.md)
