---
title: Zarządzanie wyjątkami za pomocą debugera | Dokumentacja firmy Microsoft
ms.custom: seodec18
ms.date: 10/09/2018
ms.topic: conceptual
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 408a21ef7794381d55c8ab416aee3ed104542aa6
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53968329"
---
# <a name="manage-exceptions-with-the-debugger-in-visual-studio"></a>Zarządzanie wyjątkami za pomocą debugera programu Visual Studio

Wyjątek jest wskazaniem stanu błędu, który występuje, gdy program jest wykonywane. Można polecić debugerowi, której wyjątki lub zestawy wyjątki, aby przerywał działanie w przypadku, a w tym momencie chcesz, aby debuger przerywa. Kiedy debuger przerywa, jego dowiesz się, gdy wyjątek został zgłoszony. Można również dodawać lub usuwać wyjątki. Za pomocą rozwiązania otwarte w programie Visual Studio, należy użyć **Debuguj > Windows > Ustawienia wyjątków** otworzyć **ustawienia wyjątków** okna.

Podaj obsługi reagujące na najważniejszych wyjątków. Poznasz również sposób konfigurowania debugera tak, aby zawsze przerwać wykonywanie dla niektórych wyjątków.

Gdy wystąpi wyjątek, debuger zapisuje komunikat o wyjątku do **dane wyjściowe** okna. Może je przerwać wykonywanie w następujących przypadkach, gdy:

- Jest zgłaszany wyjątek, który nie jest obsługiwany.
- Debuger jest skonfigurowany, aby przerwać wykonywanie, zanim wywoływana zostanie jakakolwiek Obsługa.
- Ustawiono [tylko mój kod](../debugger/just-my-code.md), Debuger jest skonfigurowany do przerwania dla każdego wyjątku, który nie jest obsługiwany w kodzie użytkownika.

> [!NOTE]
> Program ASP.NET ma program obsługi wyjątków najwyższego poziomu, pokazujący stron błędów, które w przeglądarce. Nie przerywa wykonywania, chyba że **tylko mój kod** jest włączona. Aby uzyskać przykład, zobacz [polecić debugerowi, aby kontynuować na wyjątkach nieobsługiwanych przez użytkownika](#BKMK_UserUnhandled) poniżej.

<!-- Two consecutive notes are intentional here...-->

> [!NOTE]
> W aplikacji Visual Basic debuger zarządza wszystkie błędy jako wyjątki, nawet jeśli jest używana w stylu błędu obsługi błędów.

## <a name="tell-the-debugger-to-break-when-an-exception-is-thrown"></a>Polecić debugerowi, aby Przerwij, gdy zostanie zgłoszony wyjątek

Debuger może przerwać wykonywanie w punkcie, gdzie jest zgłaszany wyjątek, dzięki czemu może zbadać wyjątku przed wywołaniem programu obsługi.

W **ustawienia wyjątków** okna (**Debuguj > Windows > Ustawienia wyjątków**), rozwiń węzeł kategorii wyjątków, takie jak **wyjątki środowiska uruchomieniowego języka wspólnego**. Następnie zaznacz pole wyboru dla określonego wyjątku w ramach tej kategorii, takich jak **System.AccessViolationException**. Możesz również wybrać całej kategorii wyjątków.

![Zaznaczone AccessViolationException](../debugger/media/exceptionsettingscheckaccess.png "ExceptionSettingsCheckAccess")

> [!TIP]
> Możesz znaleźć określone wyjątki za pomocą **wyszukiwania** okna **ustawienia wyjątków** paska narzędzi lub użyj Wyszukaj, aby filtrować dla określonych przestrzeni nazw (takich jak **System.IO**).

Jeśli wybierzesz wyjątek **ustawienia wyjątków** okna debugera wykonywanie zostanie przerwane wszędzie tam, gdzie jest zgłaszany wyjątek, niezależnie od tego, czy jest obsługiwany. Wyjątek jest teraz nazywana wyjątku pierwszej szansy. Na przykład poniżej przedstawiono kilka scenariuszy:

- W poniższym aplikacji konsolowej C#, metoda Main zgłasza **AccessViolationException** wewnątrz `try/catch` bloku.

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

  Jeśli masz **AccessViolationException** zaewidencjonowany **ustawienia wyjątków**, wykonywanie zostanie przerwane na `throw` wiersz po uruchomieniu tego kodu w debugerze. Następnie można kontynuować wykonywania. Obie linie powinien być wyświetlany w konsoli:

  ```cmd
  caught exception
  goodbye
  ```

  ale ona nie wyświetla `here` wiersza.

- Aplikacja konsolowa C# odwołuje się do biblioteki klas w języku klasę, która ma dwie metody. Jedna metoda zgłasza wyjątek i obsługuje go, podczas gdy druga metoda generuje ten sam wyjątek, ale nie obsługują jej.

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

  Poniżej przedstawiono metody Main() aplikacji konsoli:

  ```csharp
  static void Main(string[] args)
  {
      Class1 class1 = new Class1();
      class1.ThrowHandledException();
      class1.ThrowUnhandledException();
  }
  ```

  Jeśli masz **AccessViolationException** zaewidencjonowany **ustawienia wyjątków**, wykonywanie zostanie przerwane na `throw` wiersza w obu **ThrowHandledException()** i **ThrowUnhandledException()** po uruchomieniu tego kodu w debugerze.

Aby przywrócić ustawienia domyślne ustawienia wyjątków, wybierz **przywrócić ustawienia domyślne listy** przycisku:

![Przywróć ustawienia domyślne w ustawieniach wyjątek](../debugger/media/restoredefaultexceptions.png "RestoreDefaultExceptions")

## <a name="BKMK_UserUnhandled"></a>Polecić debugerowi, aby kontynuować na wyjątkach nieobsługiwanych przez użytkownika

Jeśli debugujesz kod .NET lub języka JavaScript za pomocą [tylko mój kod](../debugger/just-my-code.md), można polecić debugerowi, aby uniknąć podziału na wyjątki, które nie są obsługiwane w kodzie użytkownika, ale są obsługiwane w innym miejscu.

1. W **ustawienia wyjątków** , otwórz menu skrótów, klikając prawym przyciskiem myszy etykiety kolumn, a następnie wybierz pozycję **Pokaż kolumny > dodatkowe akcje**. (Jeśli zostały wyłączone **tylko mój kod**, nie zobaczysz tego polecenia.) Trzecia kolumna o nazwie **dodatkowe akcje** pojawia się.

   ![Dodatkową kolumnę akcji](../debugger/media/additionalactionscolumn.png "AdditionalActionsColumn")

   Wyjątku, który pokazuje **Kontynuuj w przypadku braku obsługi w kodzie użytkownika** w tej kolumnie, Debuger kontynuuje, jeśli ten wyjątek nie jest obsługiwany w kodzie użytkownika, ale jest obsługiwany zewnętrznie.

2. Aby zmienić to ustawienie dla określonego wyjątku, wybierz wyjątek, kliknij prawym przyciskiem myszy, aby wyświetlić menu skrótów i wybierz **kontynuować po nieobsługiwany w kodzie użytkownika**. Można również zmienić ustawienie dla całej kategorii wyjątków, takie jak całego wyjątki środowiska uruchomieniowego języka wspólnego).

   ![** Kontynuuj w przypadku braku obsługi w ustawienie kodu ** użytkownika](../debugger/media/continuewhenunhandledinusercodesetting.png "ContinueWhenUnhandledInUserCodeSetting")

Na przykład aplikacji sieci web ASP.NET obsługi wyjątków, konwertując je na kod stanu HTTP 500 ([obsługi wyjątków w ASP.NET Web API](http://www.asp.net/web-api/overview/error-handling/exception-handling)), który nie pomogą Ci określić źródło wyjątku. W poniższym przykładzie kod użytkownika wywołuje `String.Format()` która zgłasza <xref:System.FormatException>. Wykonanie przerywa w następujący sposób:

![Przerywa użytkownika&#45;nieobsłużony wyjątek](../debugger/media/exceptionunhandledbyuser.png "ExceptionUnhandledByUser")

## <a name="add-and-delete-exceptions"></a>Dodawanie i usuwanie wyjątków

Można dodawać i usuwać wyjątki. Aby usunąć typ wyjątku z kategorii, wybierz wyjątek, a następnie wybierz **Usuń wybrany wyjątek z listy** przycisku (znak minus) na **ustawienia wyjątków** paska narzędzi. Albo kliknij prawym przyciskiem myszy wyjątek i wybierz **Usuń** z menu skrótów. Usuwanie wyjątek działa tak samo jako posiadające wyjątek nie jest zaznaczone, czyli o tym, że debuger nie zostanie przerwane, gdy jest generowany.

Aby dodać wyjątek:

1. W **ustawienia wyjątków** okna, wybierz jedną z kategorii wyjątków (na przykład **środowiska uruchomieniowego języka wspólnego**).

2. Wybierz **Dodaj wyjątek do wybranej kategorii** przycisku (znak plus).

   ![** Dodać wyjątek do wybranej kategorii ** przycisku](../debugger/media/addanexceptiontotheselectedcategorybutton.png "AddAnExceptionToTheSelectedCategoryButton")

3. Wpisz nazwę wyjątku (na przykład **System.UriTemplateMatchException**).

   ![Wpisz nazwę wyjątek](../debugger/media/typetheexceptionname.png "TypeTheExceptionName")

   Wyjątek zostanie dodany do listy (w kolejności alfabetycznej) i automatycznie sprawdzane.

Aby dodać wyjątek wyjątki dostępu do pamięci procesora GPU, wyjątki środowiska uruchomieniowego JavaScript lub kategorii wyjątki Win32, zawierają kod błędu i opis.

> [!TIP]
> Sprawdź pisownię! **Ustawienia wyjątków** okna nie sprawdza istnienie dodano wyjątek. Tak, jeśli wpiszesz **Sytem.UriTemplateMatchException**, otrzymasz wpis dla tego wyjątku (a nie **System.UriTemplateMatchException**).

Ustawienia wyjątków są utrwalane w pliku .suo rozwiązania, dzięki czemu mają one zastosowanie do danego rozwiązania. Nie można ponownie użyć ustawienia określonego wyjątku w rozwiązań. Teraz są utrwalane tylko wyjątków dodanych; nie usunięto wyjątki. Możesz dodać wyjątek, zamknij i ponownie otwórz rozwiązanie, a wyjątek będą nadal dostępne. Ale jeśli usuniesz wyjątek, a Zamknij i otwórz ponownie rozwiązanie, pojawi się wyjątek.

**Ustawienia wyjątków** okna obsługuje typów wyjątków ogólnych w języku C#, ale nie w języku Visual Basic. Przerwanie przy wyjątkach, takich jak `MyNamespace.GenericException<T>`, należy dodać wyjątek jako **MyNamespace.GenericException'1**. Oznacza to jeśli został utworzony wyjątek podobnie do tego kodu:

```csharp
public class GenericException<T> : Exception
{
    public GenericException() : base("This is a generic exception.")
    {
    }
}
```

Możesz dodać wyjątek **ustawienia wyjątków** za pomocą poprzedniej procedury:

![Dodawanie wyjątek ogólny](../debugger/media/addgenericexception.png "AddGenericException")

## <a name="add-conditions-to-an-exception"></a>Dodawanie warunków do wyjątku

Użyj **ustawienia wyjątków** okna Ustawianie warunków wyjątków. Obecnie obsługiwane warunki obejmują nazwy modułu do dołączania lub wykluczania dla wyjątku. Przez ustawienie nazwy modułów, jako warunków, można wybrać przerwanie dla wyjątku tylko w przypadku niektórych modułów kodu. Można także uniknąć istotne dla konkretnego modułów.

> [!NOTE]
> Dodawanie warunków do wyjątku jest nowego w programie [!include[vs_dev15](../misc/includes/vs_dev15_md.md)].

Aby dodać wyjątki warunkowe:

1. Wybierz **Edytuj warunki** znajdujący się w oknie Ustawienia wyjątków lub kliknij prawym przyciskiem myszy wyjątek i wybierz pozycję **edytowanie warunków**.

   ![Warunki, dla wyjątku](../debugger/media/dbg-conditional-exception.png "DbgConditionalException")

2. Aby dodać dodatkowe wymagane warunki do wyjątku, zaznacz **Dodaj warunek** dla każdego nowego warunku. Zdefiniuj dodatkowy warunek wiersze są wyświetlane.

   ![Dodatkowe warunki, dla wyjątku](../debugger/media/extraconditionsforanexception.png "ExtraConditionsForAnException")

3. Dla każdego wiersza warunku wpisz nazwę modułu, a na liście operator porównania, aby zmienić **jest równa** lub **nie równa się**. Można określić symbole wieloznaczne (**\\***) w nazwie, aby określić więcej niż jeden moduł.

4. Jeśli musisz usunąć warunek, wybierz opcję **X** na końcu wiersza warunku.

## <a name="see-also"></a>Zobacz także

[Kontynuowanie wykonania po wystąpieniu wyjątku](../debugger/continuing-execution-after-an-exception.md)<br/>
[Instrukcje: Badanie kodu systemu po wystąpieniu wyjątku](../debugger/how-to-examine-system-code-after-an-exception.md)<br/>
[Instrukcje: Korzystanie z macierzystego sprawdzania w czasie wykonywania](../debugger/how-to-use-native-run-time-checks.md)<br/>
[Używanie sprawdzania w trakcie wykonywania bez biblioteki wykonawczej języka C](../debugger/using-run-time-checks-without-the-c-run-time-library.md)<br/>
[Pierwsze spojrzenie na debugera](../debugger/debugger-feature-tour.md)
