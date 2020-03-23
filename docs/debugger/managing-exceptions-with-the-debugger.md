---
title: Zarządzanie wyjątkami za pomocą debugera | Dokumenty firmy Microsoft
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 00ad5b41dd0a11661d281f24474b7673ea0a342c
ms.sourcegitcommit: 95f26af1da51d4c83ae78adcb7372b32364d8a2b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/13/2020
ms.locfileid: "79302155"
---
# <a name="manage-exceptions-with-the-debugger-in-visual-studio"></a>Zarządzanie wyjątkami za pomocą debugera w programie Visual Studio

Wyjątek jest wskazanie stanu błędu, który występuje podczas wykonywania programu. Debugera, które wyjątki lub zestawy wyjątków mają zostać przerwane i w którym momencie ma zostać przerwany debuger (czyli wstrzymanie w debugerze). Gdy debuger przerwy, pokazuje, gdzie został zgłoszony wyjątek. Można również dodawać lub usuwać wyjątki. Po otwarciu rozwiązania w programie Visual Studio należy użyć **debugowania > ustawienia wyjątków systemu Windows > wyjątków,** aby otworzyć okno **Ustawienia wyjątków.**

Podaj programy obsługi, które odpowiadają na najważniejsze wyjątki. Jeśli chcesz wiedzieć, jak dodać programy obsługi dla wyjątków, zobacz [Napraw błędy, pisząc lepszy kod C#.](../debugger/write-better-code-with-visual-studio.md) Ponadto dowiedz się, jak skonfigurować debugera, aby zawsze przerywać wykonywanie dla niektórych wyjątków.

W przypadku wystąpienia wyjątku debuger zapisuje komunikat o wyjątku w oknie **Dane wyjściowe.** Może przerwać wykonanie w następujących przypadkach, gdy:

- Wyjątek jest zgłaszany, który nie jest obsługiwany.
- Debuger jest skonfigurowany do przerwania wykonywania przed wywołaniem dowolnego programu obsługi.
- Ustawiono [just my code](../debugger/just-my-code.md), a debuger jest skonfigurowany do podziału na każdy wyjątek, który nie jest obsługiwany w kodzie użytkownika.

> [!NOTE]
> ASP.NET ma program obsługi wyjątków najwyższego poziomu, który pokazuje strony błędów w przeglądarce. Nie przerywa wykonywania, chyba że **tylko mój kod** jest włączony. Na przykład zobacz [Powiedz debugerowi, aby kontynuował wyjątki nieobsługiwalne](#BKMK_UserUnhandled) przez użytkownika poniżej.

<!-- Two consecutive notes are intentional here...-->

> [!NOTE]
> W aplikacji języka Visual Basic debuger zarządza wszystkimi błędami jako wyjątkami, nawet jeśli używasz programów obsługi błędów w stylu błędu.

## <a name="tell-the-debugger-to-break-when-an-exception-is-thrown"></a>Poinformuj debugera, aby przerwał, gdy zostanie zgłoszony wyjątek

Debuger może przerwać wykonanie w punkcie, w którym wyjątek jest generowany, więc można zbadać wyjątek przed wywołanie programu obsługi.

W oknie **Ustawienia wyjątków** **(Debug > Ustawienia wyjątków systemu Windows >**) rozwiń węzeł dla kategorii wyjątków, takich jak **wyjątki środowiska wykonawczego języka wspólnego**. Następnie zaznacz pole wyboru dla określonego wyjątku w tej kategorii, takiego jak **System.AccessViolationException**. Można również wybrać całą kategorię wyjątków.

![Sprawdzone AccessViolationException](../debugger/media/exceptionsettingscheckaccess.png "ExceptionSettingsCheckAccess")

> [!TIP]
> Określone wyjątki można znaleźć za pomocą okna **Wyszukiwania** na pasku **narzędzi Ustawienia wyjątków** lub użyć funkcji wyszukiwania do filtrowania określonych obszarów nazw (takich jak **System.IO**).

Jeśli wybierzesz wyjątek w oknie **Ustawienia wyjątku,** wykonanie debugera zostanie przerwane wszędzie tam, gdzie zostanie zgłoszony wyjątek, bez względu na to, czy jest obsługiwany. Teraz wyjątek jest nazywany wyjątkiem pierwszej szansy. Oto na przykład kilka scenariuszy:

- W następującej aplikacji konsoli Języka C# Main Metoda zgłasza **AccessViolationException** wewnątrz `try/catch` bloku.

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

  Jeśli masz **AccessViolationException** zaewidencjonowany w `throw` ustawienia **wyjątku,** wykonanie zostanie przerwane w wierszu po uruchomieniu tego kodu w debugerze. Następnie można kontynuować wykonywanie. Na konsoli powinny być wyświetlane obie linie:

  ```cmd
  caught exception
  goodbye
  ```

  ale nie wyświetla `here` linii.

- Aplikacja konsoli Języka C# odwołuje się do biblioteki klas z klasą, która ma dwie metody. Jedna metoda zgłasza wyjątek i obsługuje go, podczas gdy druga metoda zgłasza ten sam wyjątek, ale nie obsługuje go.

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

  Oto main() metoda aplikacji konsoli:

  ```csharp
  static void Main(string[] args)
  {
      Class1 class1 = new Class1();
      class1.ThrowHandledException();
      class1.ThrowUnhandledException();
  }
  ```

  Jeśli masz **AccessViolationException** zaewidencjonowany w `throw` ustawienia **wyjątku,** wykonanie zostanie przerwane w wierszu zarówno **ThrowHandledException()** i **ThrowUnhandledException()** po uruchomieniu tego kodu w debugerze.

Aby przywrócić ustawienia wyjątków do ustawień domyślnych, wybierz przycisk **Przywróć listę do ustawień domyślnych:**

![Przywracanie wartości domyślnych w ustawieniach wyjątków](../debugger/media/restoredefaultexceptions.png "Przywróćwywnienia")

## <a name="tell-the-debugger-to-continue-on-user-unhandled-exceptions"></a><a name="BKMK_UserUnhandled"></a>Poinformuj debuger, aby kontynuował wyjątki nieobsługiwalne przez użytkownika

Jeśli debugujesz kod .NET lub JavaScript za pomocą [tylko mój kod,](../debugger/just-my-code.md)możesz poinformować debuger, aby zapobiec łamaniu wyjątków, które nie są obsługiwane w kodzie użytkownika, ale są obsługiwane w innym miejscu.

1. W oknie **Ustawienia wyjątków** otwórz menu skrótów, klikając prawym przyciskiem myszy etykietę kolumny, a następnie wybierz polecenie **Pokaż kolumny > akcje dodatkowe**. (Jeśli wyłączyłeś **tylko mój kod,** nie zobaczysz tego polecenia). Pojawi się trzecia kolumna o nazwie **Akcje dodatkowe.**

   ![Kolumna Akcje dodatkowe](../debugger/media/additionalactionscolumn.png "Dodatkowe ActionsColumn")

   Dla wyjątku, który pokazuje **Kontynuuj, gdy nieobsługiwał w kodzie użytkownika** w tej kolumnie, debuger jest kontynuowany, jeśli ten wyjątek nie jest obsługiwany w kodzie użytkownika, ale jest obsługiwany zewnętrznie.

2. Aby zmienić to ustawienie dla określonego wyjątku, wybierz wyjątek, kliknij prawym przyciskiem myszy, aby wyświetlić menu skrótów, a następnie wybierz polecenie **Kontynuuj, gdy nie obsłużony w kodzie użytkownika**. Można również zmienić ustawienie dla całej kategorii wyjątków, takich jak całe wyjątki środowiska uruchomieniowego języka wspólnego).

   ![**Kontynuuj, gdy nieobsługiwał się kodem użytkownika**](../debugger/media/continuewhenunhandledinusercodesetting.png "ContinueWhenUnhandledInUserCodeSetting")

Na przykład ASP.NET aplikacje sieci web obsługują wyjątki, konwertując je na kod stanu HTTP 500[(Obsługa wyjątków w ASP.NET interfejsu API sieci Web),](/aspnet/web-api/overview/error-handling/exception-handling)co może nie pomóc w określeniu źródła wyjątku. W poniższym przykładzie kod użytkownika `String.Format()` wywołuje, że <xref:System.FormatException>zgłasza . Podziały wykonania w następujący sposób:

![Przerwy na wyjątek&#45;nieobsługiwał się nieobsługiwał](../debugger/media/exceptionunhandledbyuser.png "ExceptionUnhandledByUser")

## <a name="add-and-delete-exceptions"></a>Dodawanie i usuwanie wyjątków

Można dodawać i usuwać wyjątki. Aby usunąć typ wyjątku z kategorii, wybierz wyjątek i wybierz przycisk **Usuń wybrany wyjątek z** przycisku listy (znak minus) na pasku narzędzi Ustawienia **wyjątków.** Możesz też kliknąć wyjątek prawym przyciskiem myszy i wybrać polecenie **Usuń** z menu skrótów. Usunięcie wyjątku ma taki sam efekt jak wyjątek niezaznaczone, który jest, że debuger nie pęknie, gdy jest wyrzucany.

Aby dodać wyjątek:

1. W oknie **Ustawienia wyjątków** wybierz jedną z kategorii wyjątków (na przykład **Wspólny czas wykonywania języka).**

2. Wybierz przycisk **Dodaj wyjątek do wybranej kategorii** (znak plus).

   ![**Dodaj wyjątek do wybranej kategorii** przycisk](../debugger/media/addanexceptiontotheselectedcategorybutton.png "AddAnExceptionToTheSelectedCategoryButton AddAnExceptionToTheSelectedCategoryButton AddAnExceptionToTheSelectedCategoryButton AddAn")

3. Wpisz nazwę wyjątku (na przykład **System.UriTemplateMatChException**).

   ![Wpisz nazwę wyjątku](../debugger/media/typetheexceptionname.png "TypTheExceptionName")

   Wyjątek jest dodawany do listy (w kolejności alfabetycznej) i automatycznie sprawdzany.

Aby dodać wyjątek do wyjątków dostępu do pamięci GPU, wyjątków środowiska wykonawczego JavaScript lub kategorii wyjątków Win32, należy podać kod błędu i opis.

> [!TIP]
> Sprawdź pisownię! Okno **Ustawienia wyjątków** nie sprawdza istnienia dodatkowego wyjątku. Więc jeśli wpiszesz **Sytem.UriTemplateMatchException**, otrzymasz wpis dla tego wyjątku (a nie dla **System.UriTemplateMatchException**).

Ustawienia wyjątków są zachowywane w pliku .suo rozwiązania, więc mają zastosowanie do określonego rozwiązania. Nie można ponownie użyć określonych ustawień wyjątków w rozwiązaniach. Teraz tylko dodane wyjątki są zachowywane; usunięte wyjątki nie są. Możesz dodać wyjątek, zamknąć i ponownie otworzyć rozwiązanie, a wyjątek nadal będzie tam. Ale jeśli usuniesz wyjątek i zamkniesz/ponownie otworzysz rozwiązanie, wyjątek pojawi się ponownie.

Okno **Ustawienia wyjątków** obsługuje typy wyjątków ogólnych w języku C#, ale nie w języku Visual Basic. Aby przerwać wyjątki, takie jak `MyNamespace.GenericException<T>`, należy dodać wyjątek jako **MyNamespace.GenericException'1**. Oznacza to, że jeśli utworzono wyjątek, taki jak ten kod:

```csharp
public class GenericException<T> : Exception
{
    public GenericException() : base("This is a generic exception.")
    {
    }
}
```

Wyjątek można dodać do **ustawień wyjątków** przy użyciu poprzedniej procedury:

![dodawanie wyjątku ogólnego](../debugger/media/addgenericexception.png "AddGenericException")

## <a name="add-conditions-to-an-exception"></a>Dodawanie warunków do wyjątku

Okno **Ustawienia wyjątków** służy do ustawiania warunków wyjątków. Obecnie obsługiwane warunki obejmują nazwy modułów, które mają zawierać lub wykluczać dla wyjątku. Ustawiając nazwy modułów jako warunki, można podzielić dla wyjątku tylko na niektórych modułów kodu. Można również uniknąć zerwania na poszczególnych modułów.

> [!NOTE]
> Dodawanie warunków do wyjątku jest [!include[vs_dev15](../misc/includes/vs_dev15_md.md)]obsługiwane począwszy od .

Aby dodać wyjątki warunkowe:

1. Wybierz przycisk **Edytuj warunki** w oknie Ustawienia wyjątków lub kliknij prawym przyciskiem myszy wyjątek i wybierz polecenie **Edytuj warunki**.

   ![Warunki wyjątku](../debugger/media/dbg-conditional-exception.png "DbgConditionalException (Nierozliczeniewarzalne)")

2. Aby dodać dodatkowe wymagane warunki do wyjątku, wybierz **dodaj warunek** dla każdego nowego warunku. Pojawią się dodatkowe wiersze warunku.

   ![Dodatkowe warunki wyjątku](../debugger/media/extraconditionsforanexception.png "ExtraConditionsForAnException")

3. Dla każdego wiersza warunku wpisz nazwę modułu i zmień listę **operatorów** porównania na Równe lub **Nie równe**. Można określić symbole**\\**wieloznaczne ( ) w nazwie, aby określić więcej niż jeden moduł.

4. Jeśli chcesz usunąć warunek, wybierz **X** na końcu wiersza warunku.

## <a name="see-also"></a>Zobacz też

- [Kontynuowanie wykonania po wystąpieniu wyjątku](../debugger/continuing-execution-after-an-exception.md)<br/>
- [Instrukcje: badanie kodu systemu po wystąpieniu wyjątku](../debugger/how-to-examine-system-code-after-an-exception.md)<br/>
- [Instrukcje: korzystanie z macierzystego sprawdzania w trakcie wykonywania](../debugger/how-to-use-native-run-time-checks.md)<br/>
- [Używanie sprawdzania czasu wykonywania bez biblioteki czasu wykonywania języka C](../debugger/using-run-time-checks-without-the-c-run-time-library.md)<br/>
- [Pierwsze spojrzenie na debugera](../debugger/debugger-feature-tour.md)
