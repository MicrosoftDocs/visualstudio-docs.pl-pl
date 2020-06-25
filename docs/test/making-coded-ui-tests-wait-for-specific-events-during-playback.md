---
title: Przekształć kodowane testy interfejsu użytkownika w celu zaczekania na określone zdarzenia
ms.date: 11/04/2016
ms.topic: how-to
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ea0bd0135ca90f96c2275248da7d116ecfd92e01
ms.sourcegitcommit: 1d4f6cc80ea343a667d16beec03220cfe1f43b8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/23/2020
ms.locfileid: "85286781"
---
# <a name="make-coded-ui-tests-wait-for-specific-events-during-playback"></a>Przekształć kodowane testy interfejsu użytkownika, aby oczekiwać na określone zdarzenia podczas odtwarzania

W przypadku odtwarzania kodowanego testu interfejsu użytkownika można nakazać testowi zaczekać na wystąpienie niektórych zdarzeń, takich jak okno, które ma zostać wyświetlone, pasek postępu, który ma być znikany itd. W tym celu należy użyć odpowiedniej metody UITestControl. WaitForControlXXX (), zgodnie z opisem w poniższej tabeli. Przykład kodowanego testu interfejsu użytkownika, który czeka na włączenie formantu przy użyciu <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl.WaitForControlEnabled%2A> metody, zobacz [Przewodnik: Tworzenie, edytowanie i obsługa kodowanego testu interfejsu użytkownika](../test/walkthrough-creating-editing-and-maintaining-a-coded-ui-test.md).

[!INCLUDE [coded-ui-test-deprecation](includes/coded-ui-test-deprecation.md)]

**Wymagania**

Visual Studio Enterprise

> [!TIP]
> Możesz również dodać opóźnienia przed akcjami przy użyciu edytora kodowanego testu interfejsu użytkownika. Aby uzyskać więcej informacji, zobacz [jak: Wstawianie opóźnienia przed akcją interfejsu użytkownika przy użyciu edytora kodowanego testu interfejsu użytkownika](editing-coded-ui-tests-using-the-coded-ui-test-editor.md#insert-a-delay-before-a-ui-action).

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

Możesz użyć właściwości, <xref:Microsoft.VisualStudio.TestTools.UITesting.PlaybackSettings.ThinkTimeMultiplier%2A> Aby zmodyfikować czas trwania uśpienia. Domyślnie ta zmienna ma wartość 1, ale można ją zwiększyć lub zmniejszyć, aby zmienić czas oczekiwania na cały kod. Na przykład w przypadku testowania za pośrednictwem wolnej sieci lub innego przypadku niska wydajność można zmienić tę zmienną w jednym miejscu (lub nawet w pliku konfiguracji) na 1,5, aby dodać 50% dodatkowego oczekiwania we wszystkich miejscach.

Odtwarzanie. czekaj () wewnętrznie wywołuje wątek. uśpienia () (po wyższym obliczaniu) w mniejszych fragmentach w pętli for podczas sprawdzania, czy operacja cancel\break użytkownika. Innymi słowy odtwarzanie. czekaj () umożliwia anulowanie odtwarzania przed końcem oczekiwania, gdy uśpienie może nie być lub zgłosić wyjątek.

> [!TIP]
> Edytor kodowanego testu interfejsu użytkownika pozwala łatwo modyfikować kodowane testy interfejsu użytkownika. Za pomocą edytora kodowanego testu interfejsu użytkownika można lokalizować, wyświetlać i edytować metody testowe. Możesz również edytować akcje interfejsu użytkownika i ich skojarzone kontrolki na mapie formantów interfejsu użytkownika. Aby uzyskać więcej informacji, zobacz [Edytowanie kodowanych testów interfejsu użytkownika za pomocą edytora kodowanego testu interfejsu użytkownika](../test/editing-coded-ui-tests-using-the-coded-ui-test-editor.md).

## <a name="see-also"></a>Zobacz też

- [Używanie automatyzacji interfejsu użytkownika do testowania kodu](../test/use-ui-automation-to-test-your-code.md)
- [Tworzenie kodowanych testów interfejsu użytkownika](../test/use-ui-automation-to-test-your-code.md)
- [Przewodnik: Tworzenie, edytowanie i obsługa kodowanego testu interfejsu użytkownika](../test/walkthrough-creating-editing-and-maintaining-a-coded-ui-test.md)
- [Anatomia kodowanego testu interfejsu użytkownika](../test/anatomy-of-a-coded-ui-test.md)
- [Obsługiwane konfiguracje i platformy dla kodowanych testów interfejsu użytkownika i nagrań akcji](../test/supported-configurations-and-platforms-for-coded-ui-tests-and-action-recordings.md)
- [Instrukcje: Wstawianie opóźnienia przed akcją interfejsu użytkownika przy użyciu edytora kodowanego testu interfejsu użytkownika](editing-coded-ui-tests-using-the-coded-ui-test-editor.md#insert-a-delay-before-a-ui-action)
