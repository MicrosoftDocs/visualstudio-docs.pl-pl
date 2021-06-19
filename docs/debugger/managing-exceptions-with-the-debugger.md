---
title: Zarządzanie wyjątkami za pomocą debugera | Microsoft Docs
description: Dowiedz się, jak określić wyjątki, na których debuger przerywa pracy, w którym momencie debuger ma przerwać i jak są obsługiwane podziały.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 89795df3a4c6b87c6a878cd07a072027f880e660
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/19/2021
ms.locfileid: "112390427"
---
# <a name="manage-exceptions-with-the-debugger-in-visual-studio"></a>Zarządzanie wyjątkami za pomocą debugera w Visual Studio

Wyjątek jest wskazaniem stanu błędu, który występuje podczas wykonywania programu. Możesz określić debugerowi, które wyjątki lub zestawy wyjątków mają zostać przerwane, i w którym momencie debuger ma przerwać (czyli wstrzymać w debugerze). Gdy debuger przerywa, pokazuje, gdzie został zgłoszony wyjątek. Można również dodawać lub usuwać wyjątki. Po otwarciu rozwiązania w programie Visual Studio użyj ustawień **> debugowania systemu Windows > wyjątku,** aby otworzyć **okno Ustawienia wyjątku.**

Podaj programy obsługi, które reagują na najważniejsze wyjątki. Jeśli musisz wiedzieć, jak dodać procedury obsługi wyjątków, zobacz Naprawianie usterek przez [pisanie lepszego kodu C#.](../debugger/write-better-code-with-visual-studio.md) Dowiedz się również, jak skonfigurować debuger, aby zawsze przerwać wykonywanie niektórych wyjątków.

Gdy wystąpi wyjątek, debuger zapisuje komunikat o wyjątku w **oknie Dane** wyjściowe. Wykonanie może zostać przerwać w następujących przypadkach, gdy:

- Zgłaszany jest wyjątek, który nie jest obsługiwany.
- Debuger jest skonfigurowany tak, aby przerwać wykonywanie przed wywołaniem jakiegokolwiek programu obsługi.
- Ustawiono [Tylko mój kod](../debugger/just-my-code.md), a debuger jest skonfigurowany tak, aby przerwać każdy wyjątek, który nie jest obsługiwany w kodzie użytkownika.

> [!NOTE]
> ASP.NET ma program obsługi wyjątków najwyższego poziomu, który wyświetla strony błędów w przeglądarce. Wykonanie nie zostanie przerwać, **chyba że Tylko mój kod** jest włączona. Aby uzyskać przykład, zobacz [Temat Tell the debugger to continue on user-unhandled exceptions](#BKMK_UserUnhandled) (Poinformuj debuger, aby kontynuował pracę w przypadku nieobsługiwanych przez użytkownika wyjątków) poniżej.

<!-- Two consecutive notes are intentional here...-->

> [!NOTE]
> W aplikacji Visual Basic debuger zarządza wszystkimi błędami jako wyjątkami, nawet jeśli używasz obsługi błędów Wł.

## <a name="tell-the-debugger-to-break-when-an-exception-is-thrown"></a>Poinformuj debuger, aby przerwał w przypadku wygenerowania wyjątku

Debuger może przerwać wykonywanie w punkcie, w którym jest zgłaszany wyjątek, więc można zbadać wyjątek przed wywołaniem procedury obsługi.

W **oknie Ustawienia** wyjątku (Ustawienia >**środowiska uruchomieniowego** systemu Windows > ) rozwiń węzeł dla kategorii wyjątków, takich jak wyjątki środowiska **uruchomieniowego języka wspólnego.** Następnie zaznacz pole wyboru dla określonego wyjątku w tej kategorii, takiego jak **System.AccessViolationException.** Możesz również wybrać całą kategorię wyjątków.

![Sprawdzono accessViolationException](../debugger/media/exceptionsettingscheckaccess.png "ExceptionSettingsCheckAccess")

> [!TIP]
> Określone wyjątki można znaleźć  przy użyciu  okna Wyszukiwanie na pasku narzędzi Ustawienia wyjątków lub użyć funkcji wyszukiwania do filtrowania określonych przestrzeni nazw (takich **jak System.IO**).

Jeśli wybierzesz wyjątek  w oknie Ustawienia wyjątku, wykonanie debugera zostanie przerwać wszędzie tam, gdzie jest zgłaszany wyjątek, niezależnie od tego, czy jest obsługiwany. Teraz wyjątek jest nazywany wyjątkiem pierwszej szansy. Oto kilka scenariuszy:

- W poniższej aplikacji konsolowej języka C# metoda Main zgłasza wyjątek **AccessViolationException** wewnątrz `try/catch` bloku.

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

  Jeśli w ustawieniach wyjątku jest zaznaczona opcja **AccessViolationException,** wykonanie zostanie zerwane w wierszu po uruchomieniu tego kodu `throw` w debugerze. Następnie możesz kontynuować wykonywanie. W konsoli powinny być wyświetlane oba wiersze:

  ```cmd
  caught exception
  goodbye
  ```

  ale nie wyświetla `here` wiersza.

- Aplikacja konsolowa języka C# odwołuje się do biblioteki klas z klasą, która ma dwie metody. Jedna metoda zgłasza wyjątek i obsługuje go, a druga metoda zgłasza ten sam wyjątek, ale go nie obsługuje.

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

  Oto metoda Main() aplikacji konsolowej:

  ```csharp
  static void Main(string[] args)
  {
      Class1 class1 = new Class1();
      class1.ThrowHandledException();
      class1.ThrowUnhandledException();
  }
  ```

  Jeśli w ustawieniach wyjątków jest zaznaczona opcja **AccessViolationException,** wykonanie zostanie zerwane w wierszu w obu przypadkach: `throw` **ThrowHandledException()** i **ThrowUnhandledException()** podczas uruchamiania tego kodu w debugerze.

Aby przywrócić ustawienia wyjątku do wartości domyślnych, wybierz przycisk Przywróć **listę do ustawień domyślnych:**

![Przywróć wartości domyślne w ustawieniach wyjątku](../debugger/media/restoredefaultexceptions.png "RestoreDefaultExceptions")

## <a name="tell-the-debugger-to-continue-on-user-unhandled-exceptions"></a><a name="BKMK_UserUnhandled"></a>Poinformuj debuger, aby kontynuował pracę w przypadku nieobsługiwanych przez użytkownika wyjątków

W przypadku debugowania kodu .NET lub JavaScript za pomocą programu [Tylko mój kod](../debugger/just-my-code.md)można poinformować debuger, aby zapobiec przerywaniu wyjątków, które nie są obsługiwane w kodzie użytkownika, ale są obsługiwane w innym miejscu.

1. W **oknie Ustawienia wyjątku** otwórz menu skrótów, klikając prawym przyciskiem myszy etykietę kolumny, a następnie wybierz pozycję Pokaż kolumny **i > dodatkowe akcje.** (Jeśli wyłączysz **tę** Tylko mój kod , to polecenie nie będzie widać). Zostanie wyświetlona trzecia kolumna **o nazwie Dodatkowe** akcje.

   ![Kolumna Dodatkowe akcje](../debugger/media/additionalactionscolumn.png "AdditionalActionsColumn")

   W przypadku wyjątku, który pokazuje ciąg **Kontynuuj,** gdy nieobsłużony kod użytkownika w tej kolumnie jest nieobsługiwany, debuger kontynuuje pracę, jeśli ten wyjątek nie jest obsługiwany w kodzie użytkownika, ale jest obsługiwany zewnętrznie.

2. Aby zmienić to ustawienie dla określonego wyjątku, wybierz wyjątek, kliknij prawym przyciskiem myszy, aby wyświetlić menu skrótów, a następnie wybierz pozycję Kontynuuj po nieobsługiwanym **kodzie użytkownika.** Możesz również zmienić ustawienie dla całej kategorii wyjątków, takich jak wszystkie wyjątki środowiska uruchomieniowego języka wspólnego).

   ![Ustawienie **Kontynuuj, gdy nieobsłużone w kodzie użytkownika**](../debugger/media/continuewhenunhandledinusercodesetting.png "ContinueWhenUnhandledInUserCodeSetting")

Na przykład aplikacje internetowe ASP.NET obsługują wyjątki, konwertując je na kod stanu HTTP 500 (Obsługa wyjątków w internetowym interfejsie API usługi[ASP.NET),](/aspnet/web-api/overview/error-handling/exception-handling)co może nie pomóc w ustaleniu źródła wyjątku. W poniższym przykładzie kod użytkownika wykonuje wywołanie , które zgłasza `String.Format()` wyjątek <xref:System.FormatException> . Wykonywanie przerywa w następujący sposób:

![Przerwy w&#45;nieobsłużonych wyjątków](../debugger/media/exceptionunhandledbyuser.png "ExceptionUnhandledByUser")

## <a name="add-and-delete-exceptions"></a>Dodawanie i usuwanie wyjątków

Wyjątki można dodawać i usuwać. Aby usunąć typ wyjątku z kategorii, wybierz  wyjątek i wybierz przycisk Usuń wybrany wyjątek na liście (znak minus) na pasku **narzędzi Ustawienia wyjątku.** Możesz też kliknąć wyjątek prawym przyciskiem myszy i wybrać polecenie **Usuń** z menu skrótów. Usunięcie wyjątku ma taki sam efekt jak usunięcie wyjątku, co oznacza, że debuger nie przerwie działania po jego wyrzuceniu.

Aby dodać wyjątek:

1. W **oknie Ustawienia** wyjątku wybierz jedną z kategorii wyjątków (na przykład **Środowisko uruchomieniowe języka wspólnego).**

2. Wybierz przycisk **Dodaj wyjątek do wybranej kategorii** (znak plus).

   ![Przycisk **Dodaj wyjątek do wybranej kategorii**](../debugger/media/addanexceptiontotheselectedcategorybutton.png "AddAnExceptionToTheSelectedCategoryButton")

3. Wpisz nazwę wyjątku (na przykład **System.UriTemplateMatchException**).

   ![Wpisz nazwę wyjątku](../debugger/media/typetheexceptionname.png "TypeTheExceptionName")

   Wyjątek jest dodawany do listy (w kolejności alfabetycznej) i automatycznie sprawdzany.

Aby dodać wyjątek do kategorii Wyjątki dostępu do pamięci procesora GPU, Wyjątki środowiska uruchomieniowego JavaScript lub Wyjątki Win32, dołącz kod błędu i opis.

> [!TIP]
> Sprawdź pisownię! Okno **Ustawienia** wyjątku nie sprawdza istnienia dodanego wyjątku. Jeśli więc wpiszesz **Sytem.UriTemplateMatchException,** otrzymasz wpis dla tego wyjątku (a nie dla wyjątku **System.UriTemplateMatchException**).

Ustawienia wyjątków są utrwalane w pliku suo rozwiązania, więc mają zastosowanie do określonego rozwiązania. Nie można ponownie używać określonych ustawień wyjątków w różnych rozwiązaniach. Teraz utrwalane są tylko dodane wyjątki. usunięte wyjątki nie są. Możesz dodać wyjątek, zamknąć i ponownie otworzyć rozwiązanie, a wyjątek nadal będzie w tym miejscu. Jeśli jednak usuniesz wyjątek i zamkniesz/ponownie otworzysz rozwiązanie, ten wyjątek pojawi się ponownie.

Okno **Ustawienia wyjątków** obsługuje ogólne typy wyjątków w języku C#, ale nie w Visual Basic. Aby przerwać wyjątki, takie jak , należy dodać wyjątek `MyNamespace.GenericException<T>` jako **MyNamespace.GenericException'1**. Oznacza to, że jeśli utworzono wyjątek podobny do tego kodu:

```csharp
public class GenericException<T> : Exception
{
    public GenericException() : base("This is a generic exception.")
    {
    }
}
```

Wyjątek można dodać do ustawień **wyjątku przy** użyciu poprzedniej procedury:

![dodawanie wyjątku ogólnego](../debugger/media/addgenericexception.png "AddGenericException")

## <a name="add-conditions-to-an-exception"></a>Dodawanie warunków do wyjątku

Użyj okna **Ustawienia wyjątku,** aby ustawić warunki dla wyjątków. Obecnie obsługiwane warunki obejmują nazwy modułów, które mają być dołączane lub wykluczane dla wyjątku. Ustawiając nazwy modułów jako warunki, możesz przerwać wyjątek tylko w niektórych modułach kodu. Możesz również uniknąć łamania w określonych modułach.

> [!NOTE]
> Dodawanie warunków do wyjątku jest obsługiwane począwszy od [!include[vs_dev15](../misc/includes/vs_dev15_md.md)] .

Aby dodać wyjątki warunkowe:

1. Wybierz przycisk **Edytuj warunki** w oknie Ustawienia wyjątku lub kliknij prawym przyciskiem myszy wyjątek i wybierz polecenie **Edytuj warunki.**

   ![Warunki wyjątku](../debugger/media/dbg-conditional-exception.png "DbgConditionalException")

2. Aby dodać dodatkowe wymagane warunki do wyjątku, wybierz pozycję **Dodaj warunek** dla każdego nowego warunku. Zostaną wyświetlone dodatkowe wiersze warunku.

   ![Dodatkowe warunki dla wyjątku](../debugger/media/extraconditionsforanexception.png "ExtraConditionsForAnException")

3. Dla każdego wiersza warunku wpisz nazwę modułu i zmień listę operatorów porównania na **równa** się lub nie **równa się**. Możesz określić symbole wieloznaczne ( **\\\*** ) w nazwie, aby określić więcej niż jeden moduł.

4. Jeśli musisz usunąć warunek, wybierz **znak X** na końcu wiersza warunku.

## <a name="see-also"></a>Zobacz też

- [Kontynuowanie wykonania po wystąpieniu wyjątku](../debugger/continuing-execution-after-an-exception.md)<br/>
- [Instrukcje: badanie kodu systemu po wystąpieniu wyjątku](../debugger/how-to-examine-system-code-after-an-exception.md)<br/>
- [Instrukcje: korzystanie z macierzystego sprawdzania w trakcie wykonywania](../debugger/how-to-use-native-run-time-checks.md)<br/>
- [Pierwsze spojrzenie na debugera](../debugger/debugger-feature-tour.md)
