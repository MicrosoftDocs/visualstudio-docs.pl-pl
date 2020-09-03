---
title: Zarządzanie wyjątkami za pomocą debugera | Microsoft Docs
ms.custom: seodec18
ms.date: 10/09/2018
ms.topic: how-to
f1_keywords:
- vs.debug.exceptions
- vs.debug.exceptions.find
dev_langs:
- CSharp
- VB
- FSharp
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
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ff28944a36d338230a17cd533a4832452e42885b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "85348460"
---
# <a name="manage-exceptions-with-the-debugger-in-visual-studio"></a>Zarządzanie wyjątkami za pomocą debugera w programie Visual Studio

Wyjątek jest oznaczeniem stanu błędu, który występuje, gdy program jest wykonywany. Możesz powiedzieć debugerowi, w którym wyjątki lub zestawy wyjątków mają być przerywane, i w którym momencie chcesz, aby debuger został rozwierny (czyli wstrzymywać w debugerze). Gdy debuger przerwie, pokazuje, gdzie został zgłoszony wyjątek. Można również dodawać lub usuwać wyjątki. Aby otworzyć okno **Ustawienia wyjątku** w programie Visual Studio, należy użyć **ustawienia wyjątku debuguj > Windows >** .

Podaj programy obsługi reagujące na najważniejsze wyjątki. Aby dowiedzieć się, jak dodać procedury obsługi wyjątków, zobacz [Rozwiązywanie usterek poprzez pisanie lepszego kodu w języku C#](../debugger/write-better-code-with-visual-studio.md). Należy również dowiedzieć się, jak skonfigurować debuger, aby zawsze przerywał wykonywanie niektórych wyjątków.

Gdy wystąpi wyjątek, debuger zapisuje komunikat o wyjątku w oknie **danych wyjściowych** . Może przerwać wykonywanie w następujących przypadkach:

- Zgłaszany jest wyjątek, który nie jest obsługiwany.
- Debuger jest skonfigurowany do przerwania wykonywania przed wywołaniem jakiejkolwiek procedury obsługi.
- Ustawiono [tylko mój kod](../debugger/just-my-code.md), a debuger jest skonfigurowany do przerw w każdym wyjątku, który nie jest obsługiwany w kodzie użytkownika.

> [!NOTE]
> ASP.NET ma program obsługi wyjątków najwyższego poziomu, który pokazuje strony błędów w przeglądarce. Nie przerywa wykonywania, chyba że **tylko mój kod** jest włączona. Aby zapoznać się z przykładem, zobacz [Powiadom debugera, aby kontynuować Nieobsłużone wyjątki](#BKMK_UserUnhandled) poniżej.

<!-- Two consecutive notes are intentional here...-->

> [!NOTE]
> W aplikacji Visual Basic debuger zarządza wszystkimi błędami jako wyjątkami, nawet jeśli są używane w przypadku obsługi błędów w stylu błędu.

## <a name="tell-the-debugger-to-break-when-an-exception-is-thrown"></a>Poinformuj debugera o przerwaniu, gdy zostanie zgłoszony wyjątek

Debuger może przerwać wykonywanie w punkcie, w którym wystąpił wyjątek, więc możesz przejrzeć wyjątek przed wywołaniem programu obsługi.

W oknie **Ustawienia wyjątku** (**Debuguj > ustawienia wyjątku > systemu Windows**) rozwiń węzeł kategorii wyjątków, na przykład **wyjątki środowiska uruchomieniowego języka wspólnego**. Następnie zaznacz pole wyboru dla określonego wyjątku w tej kategorii, na przykład **System. AccessViolationException**. Można również wybrać całą kategorię wyjątków.

![Sprawdzone AccessViolationException](../debugger/media/exceptionsettingscheckaccess.png "ExceptionSettingsCheckAccess")

> [!TIP]
> Określone wyjątki można znaleźć za pomocą okna **wyszukiwania** na pasku narzędzi **Ustawienia wyjątku** lub użyć wyszukiwania do filtrowania określonych przestrzeni nazw (takich jak **System.IO**).

W przypadku wybrania wyjątku w oknie **Ustawienia wyjątku** , wykonanie debugera będzie przerywane wszędzie tam, gdzie wystąpił wyjątek, niezależnie od tego, czy jest on obsługiwany. Teraz wyjątek jest wywoływany jako wyjątek pierwszej szansy. Na przykład poniżej przedstawiono kilka scenariuszy:

- W poniższej aplikacji konsolowej C# Metoda Main zgłasza **AccessViolationException** wewnątrz `try/catch` bloku.

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

  Jeśli **AccessViolationException** zaznaczono **Ustawienia wyjątków**, wykonanie zostanie przerwane w `throw` wierszu po uruchomieniu tego kodu w debugerze. Następnie można kontynuować wykonywanie. W konsoli powinny być wyświetlane obie linie:

  ```cmd
  caught exception
  goodbye
  ```

  ale nie wyświetla `here` wiersza.

- Aplikacja konsolowa w języku C# odwołuje się do biblioteki klas z klasą, która ma dwie metody. Jedna metoda zgłasza wyjątek i obsługuje go, podczas gdy druga metoda zgłasza ten sam wyjątek, ale nie obsłuży go.

  ```csharp
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

  Jeśli **AccessViolationException** zaznaczono **Ustawienia wyjątku**, wykonanie spowoduje przerwanie w `throw` wierszu zarówno w **ThrowHandledException ()** , jak i w **ThrowUnhandledException ()** po uruchomieniu tego kodu w debugerze.

Aby przywrócić ustawienia wyjątków do ustawień domyślnych, wybierz przycisk **Przywróć ustawienia do ustawień domyślnych** :

![Przywróć wartości domyślne w ustawieniach wyjątku](../debugger/media/restoredefaultexceptions.png "RestoreDefaultExceptions")

## <a name="tell-the-debugger-to-continue-on-user-unhandled-exceptions"></a><a name="BKMK_UserUnhandled"></a>Poinformuj debugera, aby kontynuował pracę z nieobsługiwanymi wyjątkami użytkownika

Jeśli debugujesz kod .NET lub JavaScript przy użyciu [tylko mój kod](../debugger/just-my-code.md), możesz powiedzieć debuger, aby zapobiec przerywaniu wyjątków, które nie są obsługiwane w kodzie użytkownika, ale są obsługiwane w innym miejscu.

1. W oknie **Ustawienia wyjątku** Otwórz menu skrótów, klikając prawym przyciskiem myszy etykietę kolumny, a następnie wybierz polecenie **Pokaż kolumny > dodatkowe akcje**. (Jeśli wyłączono **tylko mój kod**, to polecenie nie zostanie wyświetlone). Zostanie wyświetlona trzecia kolumna o nazwie **dodatkowe akcje** .

   ![Kolumna dodatkowych akcji](../debugger/media/additionalactionscolumn.png "AdditionalActionsColumn")

   W przypadku wyjątku, który pokazuje **kontynuację w przypadku nieobsłużonego kodu użytkownika** w tej kolumnie, debuger kontynuuje działanie, jeśli ten wyjątek nie zostanie obsłużony w kodzie użytkownika, ale jest obsługiwany zewnętrznie.

2. Aby zmienić to ustawienie dla określonego wyjątku, zaznacz wyjątek, kliknij prawym przyciskiem myszy, aby wyświetlić menu skrótów, a następnie wybierz pozycję **Kontynuuj w przypadku nieobsługiwanych w kodzie użytkownika**. Można również zmienić ustawienie dla całej kategorii wyjątków, takie jak całe wyjątki środowiska uruchomieniowego języka wspólnego.

   ![* * Kontynuuj w przypadku nieobsłużonego kodu użytkownika * * ustawienie](../debugger/media/continuewhenunhandledinusercodesetting.png "ContinueWhenUnhandledInUserCodeSetting")

Na przykład ASP.NET aplikacje sieci Web obsługują wyjątki poprzez konwersję ich do kodu stanu HTTP 500 ([Obsługa wyjątków w interfejsie Web API ASP.NET](/aspnet/web-api/overview/error-handling/exception-handling)), co może nie pomóc w ustaleniu źródła wyjątku. W poniższym przykładzie kod użytkownika wywołuje metodę `String.Format()` , która zgłasza <xref:System.FormatException> . Przerwania wykonywania w następujący sposób:

![Przerwy w nieobsługiwanym wyjątku&#45;użytkownika](../debugger/media/exceptionunhandledbyuser.png "ExceptionUnhandledByUser")

## <a name="add-and-delete-exceptions"></a>Dodawanie i usuwanie wyjątków

Można dodawać i usuwać wyjątki. Aby usunąć typ wyjątku z kategorii, zaznacz wyjątek, a następnie wybierz przycisk **Usuń wybrany wyjątek z listy** (znak minus) na pasku narzędzi **Ustawienia wyjątku** . Możesz też kliknąć prawym przyciskiem myszy wyjątek, a następnie wybrać polecenie **Usuń** z menu skrótów. Usuwanie wyjątku ma ten sam skutek, co w przypadku niezaznaczania wyjątku, co oznacza, że debuger nie będzie przerywał działania po jego zgłoszeniu.

Aby dodać wyjątek:

1. W oknie **Ustawienia wyjątku** wybierz jedną z kategorii wyjątków (na przykład **środowisko uruchomieniowe języka wspólnego**).

2. Wybierz przycisk **Dodaj wyjątek do wybranej kategorii** (znak plus).

   ![* * Dodaj wyjątek do wybranej kategorii * * przycisk](../debugger/media/addanexceptiontotheselectedcategorybutton.png "AddAnExceptionToTheSelectedCategoryButton")

3. Wpisz nazwę wyjątku (na przykład **System. UriTemplateMatchException**).

   ![Wpisz nazwę wyjątku](../debugger/media/typetheexceptionname.png "TypeTheExceptionName")

   Wyjątek jest dodawany do listy (w kolejności alfabetycznej) i automatycznie zaznaczony.

Aby dodać wyjątek do wyjątków dostępu do pamięci procesora GPU, wyjątków środowiska uruchomieniowego języka JavaScript lub kategorii wyjątków Win32, należy uwzględnić kod błędu i opis.

> [!TIP]
> Sprawdź pisownię. Okno **Ustawienia wyjątku** nie sprawdza istnienia dodanego wyjątku. Dlatego jeśli wpiszesz system **. UriTemplateMatchException**, otrzymasz wpis dla tego wyjątku (a nie w przypadku **systemu. UriTemplateMatchException**).

Ustawienia wyjątków są utrwalane w pliku. suo rozwiązania, dlatego mają zastosowanie do określonego rozwiązania. Nie można ponownie użyć określonych ustawień wyjątków w różnych rozwiązaniach. Teraz tylko dodane wyjątki są utrwalane; usunięte wyjątki nie są. Możesz dodać wyjątek, zamknąć i ponownie otworzyć rozwiązanie, a mimo to nadal wystąpił wyjątek. Jednak po usunięciu wyjątku i zamknięciu/ponownym otwarciu rozwiązania zostanie wyświetlony wyjątek.

Okno **Ustawienia wyjątku** obsługuje typy wyjątków ogólnych w języku C#, ale nie w Visual Basic. Aby przerwać na wyjątkach `MyNamespace.GenericException<T>` , takich jak, należy dodać wyjątek jako **przestrzeń nazw. generycznexception ' 1**. Oznacza to, że jeśli utworzono wyjątek podobny do tego:

```csharp
public class GenericException<T> : Exception
{
    public GenericException() : base("This is a generic exception.")
    {
    }
}
```

Wyjątek można dodać do **ustawień wyjątków** przy użyciu poprzedniej procedury:

![Dodawanie wyjątku generycznego](../debugger/media/addgenericexception.png "Addgenericexception")

## <a name="add-conditions-to-an-exception"></a>Dodawanie warunków do wyjątku

Użyj okna **Ustawienia wyjątku** , aby ustawić warunki dotyczące wyjątków. Obecnie obsługiwane warunki obejmują nazwy modułów, które mają zostać dołączone lub wykluczone dla wyjątku. Ustawiając nazwy modułów jako warunki, można wybrać opcję przerwania dla wyjątku tylko dla niektórych modułów kodu. Możesz również wybrać, aby uniknąć przerywania określonych modułów.

> [!NOTE]
> Dodawanie warunków do wyjątku jest obsługiwane w programie [!include[vs_dev15](../misc/includes/vs_dev15_md.md)] .

Aby dodać wyjątki warunkowe:

1. Wybierz przycisk **Edytuj warunki** w oknie Ustawienia wyjątku lub kliknij prawym przyciskiem myszy wyjątek, a następnie wybierz polecenie **Edytuj warunki**.

   ![Warunki wyjątku](../debugger/media/dbg-conditional-exception.png "DbgConditionalException")

2. Aby dodać do wyjątku dodatkowe wymagane warunki, wybierz opcję **Dodaj warunek** dla każdego nowego warunku. Pojawią się dodatkowe wiersze warunków.

   ![Dodatkowe warunki dla wyjątku](../debugger/media/extraconditionsforanexception.png "ExtraConditionsForAnException")

3. Dla każdego wiersza warunku wpisz nazwę modułu i zmień listę operatorów porównania na **wartość Equals** lub **nie równa**się. W nazwie można określić symbole wieloznaczne ( **\\\*** ), aby określić więcej niż jeden moduł.

4. Jeśli musisz usunąć warunek, wybierz **znak X** na końcu wiersza warunku.

## <a name="see-also"></a>Zobacz też

- [Kontynuowanie wykonania po wystąpieniu wyjątku](../debugger/continuing-execution-after-an-exception.md)<br/>
- [Instrukcje: badanie kodu systemu po wystąpieniu wyjątku](../debugger/how-to-examine-system-code-after-an-exception.md)<br/>
- [Instrukcje: korzystanie z macierzystego sprawdzania w trakcie wykonywania](../debugger/how-to-use-native-run-time-checks.md)<br/>
- [Używanie sprawdzeń w czasie wykonywania bez biblioteki wykonawczej C](../debugger/using-run-time-checks-without-the-c-run-time-library.md)<br/>
- [Pierwsze spojrzenie na debugera](../debugger/debugger-feature-tour.md)
