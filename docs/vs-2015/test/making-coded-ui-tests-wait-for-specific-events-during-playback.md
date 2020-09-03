---
title: Wykonywanie kodowanych testów interfejsu użytkownika Zaczekaj na określone zdarzenia podczas odtwarzania | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-test
ms.topic: conceptual
ms.assetid: 41981ad6-673e-492e-b739-9863b14157b1
caps.latest.revision: 26
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: dbc83731cfc1c04f33fc4de05f28ffd1a54f3e4d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "75851771"
---
# <a name="making-coded-ui-tests-wait-for-specific-events-during-playback"></a>Wstrzymywanie kodowanych testów użytkownika dla określonych zdarzeń podczas odtwarzania
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

W przypadku odtwarzania kodowanego testu interfejsu użytkownika można nakazać testowi zaczekać na wystąpienie niektórych zdarzeń, takich jak okno, które ma zostać wyświetlone, pasek postępu, który ma być znikany itd. W tym celu należy użyć odpowiedniej metody UITestControl. WaitForControlXXX (), zgodnie z opisem w poniższej tabeli. Przykład kodowanego testu interfejsu użytkownika, który czeka na włączenie formantu przy użyciu <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl.WaitForControlEnabled%2A> metody, zobacz [Przewodnik: Tworzenie, edytowanie i obsługa kodowanego testu interfejsu użytkownika](../test/walkthrough-creating-editing-and-maintaining-a-coded-ui-test.md).

 **Wymagania**

 Visual Studio Enterprise

> [!TIP]
> Możesz również dodać opóźnienia przed akcjami przy użyciu edytora kodowanego testu interfejsu użytkownika. Aby uzyskać więcej informacji, zobacz [jak: Wstawianie opóźnienia przed akcją interfejsu użytkownika przy użyciu edytora kodowanego testu interfejsu użytkownika](https://msdn.microsoft.com/library/509f8ef7-e105-4049-b11b-d64549e055b0).

 **Metody UITestControl. WaitForControlXXX ()**

 <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl.WaitForControlReady%2A>

 Czeka, aż kontrolka będzie gotowa do akceptacji danych wejściowych myszy i klawiatury. Aparat niejawnie wywołuje ten interfejs API w celu zaczekania, aż formant zostanie przygotowany przed wykonaniem jakiejkolwiek operacji. Jednak w pewnym scenariuszu Esoteric może być konieczne jawne wywołanie.

 <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl.WaitForControlEnabled%2A>

 Czeka, aż formant zostanie włączony, gdy Kreator przeprowadza pewne asynchroniczne sprawdzanie poprawności danych wejściowych przez wykonywanie wywołań do serwera. Na przykład możesz poczekać, aż zostanie włączony **Następny** przycisk kreatora (). Aby zapoznać się z przykładem tej metody, zobacz [Przewodnik: Tworzenie, edytowanie i obsługa kodowanego testu interfejsu użytkownika](../test/walkthrough-creating-editing-and-maintaining-a-coded-ui-test.md).

 <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl.WaitForControlExist%2A>

 Czeka, aż formant będzie widoczny w interfejsie użytkownika. Na przykład oczekuje się, że okno dialogowe błędu po zakończeniu sprawdzania poprawności parametrów przez aplikację. Czas potrzebny na weryfikację jest zmienny. Tej metody można użyć do oczekiwania na okno dialogowe błędu.

 <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl.WaitForControlNotExist%2A>

 Czeka, aż formant zniknie z interfejsu użytkownika. Na przykład możesz poczekać, aż pasek postępu zniknie.

 <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl.WaitForControlPropertyEqual%2A>

 Czeka, aż określona właściwość kontrolki ma daną wartość. Na przykład możesz poczekać, aż tekst stanu zostanie zmieniony na **gotowe**.

 <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl.WaitForControlPropertyNotEqual%2A>

 Czeka na określoną właściwość kontrolki, aby miała przeciwieństwo do określonej wartości. Na przykład Zaczekaj, aż pole edycji nie będzie tylko do odczytu, czyli edytowalne.

 <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl.WaitForControlCondition%2A>

 Czeka, aż określony predykat zwróci wartość `true` . Ta wartość może być używana dla złożonej operacji oczekiwania (na przykład lub warunków) dla danej kontrolki. Na przykład możesz poczekać, aż tekst stanu **zakończy się pomyślnie** lub **nie powiedzie się** , jak pokazano w poniższym kodzie:

```csharp

// Define the method to evaluate the condition
private static bool IsStatusDone(UITestControl control)
{
    WinText statusText = control as WinText;
    return statusText.DisplayText == "Succeeded" || statusText.DisplayText == "Failed";
}

// In test method, wait till the method evaluates to true
statusText.WaitForControlCondition(IsStatusDone);

```

 <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl.WaitForCondition%2A>

 Wszystkie poprzednie metody są metodami wystąpień UITestControl. Ta metoda jest metodą statyczną. Ta metoda czeka również, aż określony predykat jest, `true` ale może być używany dla złożonej operacji oczekiwania (np. lub warunków) dla wielu kontrolek. Na przykład możesz poczekać, aż tekst stanu **zakończy się pomyślnie** lub zostanie wyświetlony komunikat o błędzie, jak pokazano w poniższym kodzie:

```csharp

// Define the method to evaluate the condition
private static bool IsStatusDoneOrError(UITestControl[] controls)
{
    WinText statusText = controls[0] as WinText;
    WinWindow errorDialog = controls[1] as WinWindow;
    return statusText.DisplayText == "Succeeded" || errorDialog.Exists;
}

// In test method, wait till the method evaluates to true
UITestControl.WaitForCondition<UITestControl[]>(new UITestControl[] { statusText, errorDialog }, IsStatusDoneOrError);

```

 Wszystkie te metody mają następujące zachowanie:

 Metody zwracają wartość true, jeśli oczekiwanie zakończyło się pomyślnie i FAŁSZ, jeśli oczekiwanie nie powiodło się.

 Niejawny limit czasu dla operacji oczekiwania jest określony przez <xref:Microsoft.VisualStudio.TestTools.UITesting.PlaybackSettings.WaitForReadyTimeout%2A> Właściwość. Wartość domyślna tej właściwości to 60000 milisekund (jedna minuta).

 Metody mają Przeciążenie w milisekundach, aby uzyskać jawny limit czasu. Jednak gdy operacja oczekiwania powoduje niejawne wyszukiwanie formantu lub, gdy aplikacja jest zajęta, rzeczywisty czas oczekiwania może być większy niż określony limit czasu.

 Poprzednie funkcje są zaawansowane i elastyczne i powinny spełniać niemal wszystkie warunki. Jednak w przypadku, gdy te metody nie spełnią Twoich potrzeb i należy wykonać kod albo <xref:Microsoft.VisualStudio.TestTools.UITesting.Playback.Wait%2A> lub <xref:System.Threading.Thread.Sleep%2A> w kodzie, zaleca się używanie odtwarzania. czekaj () zamiast wątku. uśpienia (). Przyczyny tego są następujące:

 Możesz użyć właściwości,  <xref:Microsoft.VisualStudio.TestTools.UITesting.PlaybackSettings.ThinkTimeMultiplier%2A> Aby zmodyfikować czas trwania uśpienia. Domyślnie ta zmienna ma wartość 1, ale można ją zwiększyć lub zmniejszyć, aby zmienić czas oczekiwania na cały kod. Na przykład w przypadku testowania za pośrednictwem wolnej sieci lub innego przypadku niska wydajność można zmienić tę zmienną w jednym miejscu (lub nawet w pliku konfiguracji) na 1,5, aby dodać 50% dodatkowego oczekiwania we wszystkich miejscach.

 Odtwarzanie. czekaj () wewnętrznie wywołuje wątek. uśpienia () (po wyższym obliczaniu) w mniejszych fragmentach w pętli for podczas sprawdzania, czy operacja cancel\break użytkownika. Innymi słowy odtwarzanie. czekaj () umożliwia anulowanie odtwarzania przed końcem oczekiwania, gdy uśpienie może nie być lub zgłosić wyjątek.

> [!TIP]
> Edytor kodowanego testu interfejsu użytkownika pozwala łatwo modyfikować kodowane testy interfejsu użytkownika. Za pomocą edytora kodowanego testu interfejsu użytkownika można lokalizować, wyświetlać i edytować metody testowe. Możesz również edytować akcje interfejsu użytkownika i ich skojarzone kontrolki na mapie formantów interfejsu użytkownika. Aby uzyskać więcej informacji, zobacz [Edytowanie kodowanych testów interfejsu użytkownika za pomocą edytora kodowanego testu interfejsu użytkownika](../test/editing-coded-ui-tests-using-the-coded-ui-test-editor.md).

 **Wskazówki**

 Aby uzyskać dodatkowe informacje, zobacz [testowanie ciągłego dostarczania przy użyciu programu Visual Studio 2012 — Rozdział 5: Automatyzowanie testów systemowych](https://msdn.microsoft.com/library/jj159335.aspx)

## <a name="see-also"></a>Zobacz też
 [Korzystanie z automatyzacji interfejsu użytkownika do testowania kodu](../test/use-ui-automation-to-test-your-code.md) [Tworzenie KODOWANYCH testów interfejsu użytkownika](../test/use-ui-automation-to-test-your-code.md#VerifyingCodeUsingCUITCreate) [Przewodnik: Tworzenie, edytowanie i konserwowanie kodowanego testu interfejsu użytkownika](../test/walkthrough-creating-editing-and-maintaining-a-coded-ui-test.md) w przypadku kodowanych [testów interfejsu użytkownika](../test/anatomy-of-a-coded-ui-test.md) [obsługiwane konfiguracje i platformy dla kodowanych testów interfejsu użytkownika i nagrań akcji](../test/supported-configurations-and-platforms-for-coded-ui-tests-and-action-recordings.md) [: Wstawianie opóźnienia przed akcją interfejsu użytkownika przy użyciu edytora kodowanego testu](https://msdn.microsoft.com/library/509f8ef7-e105-4049-b11b-d64549e055b0)
