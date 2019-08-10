---
title: Przekształć kodowane testy interfejsu użytkownika w celu zaczekania na określone zdarzenia
ms.date: 11/04/2016
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 84a8ad1784ce33d30ce1023f0554feeb340b5703
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/09/2019
ms.locfileid: "68923651"
---
# <a name="make-coded-ui-tests-wait-for-specific-events-during-playback"></a>Przekształć kodowane testy interfejsu użytkownika, aby oczekiwać na określone zdarzenia podczas odtwarzania

W przypadku odtwarzania kodowanego testu interfejsu użytkownika można nakazać testowi zaczekać na wystąpienie niektórych zdarzeń, takich jak okno, które ma zostać wyświetlone, pasek postępu, który ma być znikany itd. W tym celu należy użyć odpowiedniej metody UITestControl. WaitForControlXXX (), zgodnie z opisem w poniższej tabeli. Aby zapoznać się z przykładem kodowanego testu interfejsu użytkownika, który czeka na włączenie formantu przy <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl.WaitForControlEnabled%2A> użyciu metody, [zobacz Przewodnik: Tworzenie, edytowanie i obsługa kodowanego testu](../test/walkthrough-creating-editing-and-maintaining-a-coded-ui-test.md)interfejsu użytkownika.

[!INCLUDE [coded-ui-test-deprecation](includes/coded-ui-test-deprecation.md)]

**Wymagania**

Visual Studio Enterprise

> [!TIP]
> Możesz również dodać opóźnienia przed akcjami przy użyciu edytora kodowanego testu interfejsu użytkownika. Aby uzyskać więcej informacji, zobacz [jak: Wstaw opóźnienie przed akcją interfejsu użytkownika przy użyciu edytora](editing-coded-ui-tests-using-the-coded-ui-test-editor.md#insert-a-delay-before-a-ui-action)KODOWANEGO testu interfejsu użytkownika.

**UITestControl.WaitForControlXXX() Methods**

<xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl.WaitForControlReady%2A>

Czeka, aż kontrolka będzie gotowa do akceptacji danych wejściowych myszy i klawiatury. Aparat niejawnie wywołuje ten interfejs API w celu zaczekania, aż formant zostanie przygotowany przed wykonaniem jakiejkolwiek operacji. Jednak w pewnym scenariuszu Esoteric może być konieczne jawne wywołanie.

<xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl.WaitForControlEnabled%2A>

Czeka, aż formant zostanie włączony, gdy Kreator przeprowadza pewne asynchroniczne sprawdzanie poprawności danych wejściowych przez wykonywanie wywołań do serwera. Na przykład możesz poczekać, aż zostanie włączony **Następny** przycisk kreatora (). Aby zapoznać się z przykładem tej metody [, zobacz Przewodnik: Tworzenie, edytowanie i obsługa kodowanego testu](../test/walkthrough-creating-editing-and-maintaining-a-coded-ui-test.md)interfejsu użytkownika.

<xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl.WaitForControlExist%2A>

Czeka, aż formant będzie widoczny w interfejsie użytkownika. Na przykład oczekuje się, że okno dialogowe błędu po zakończeniu sprawdzania poprawności parametrów przez aplikację. Czas potrzebny na weryfikację jest zmienny. Tej metody można użyć do oczekiwania na okno dialogowe błędu.

<xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl.WaitForControlNotExist%2A>

Czeka, aż formant zniknie z interfejsu użytkownika. Na przykład możesz poczekać, aż pasek postępu zniknie.

<xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl.WaitForControlPropertyEqual%2A>

Czeka, aż określona właściwość kontrolki ma daną wartość. Na przykład możesz poczekać, aż tekst stanu zostanie zmieniony na **gotowe**.

<xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl.WaitForControlPropertyNotEqual%2A>

Czeka na określoną właściwość kontrolki, aby miała przeciwieństwo do określonej wartości. Na przykład Zaczekaj, aż pole edycji nie będzie tylko do odczytu, czyli edytowalne.

<xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl.WaitForControlCondition%2A>

Czeka, aż określony predykat zwróci wartość `true`. Ta wartość może być używana dla złożonej operacji oczekiwania (na przykład lub warunków) dla danej kontrolki. Na przykład możesz poczekać, aż tekst stanu zakończy się **pomyślnie** lub **nie powiedzie się** , jak pokazano w poniższym kodzie:

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

Wszystkie poprzednie metody są metodami wystąpień UITestControl. Ta metoda jest metodą statyczną. Ta metoda czeka również, aż określony predykat jest `true` , ale może być używany dla złożonej operacji oczekiwania (np. lub warunków) dla wielu kontrolek. Na przykład możesz poczekać, aż tekst stanu zakończy się **pomyślnie** lub zostanie wyświetlony komunikat o błędzie, jak pokazano w poniższym kodzie:

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

Niejawny limit czasu dla operacji oczekiwania jest określony <xref:Microsoft.VisualStudio.TestTools.UITesting.PlaybackSettings.WaitForReadyTimeout%2A> przez właściwość. Wartość domyślna tej właściwości to 60000 milisekund (jedna minuta).

Metody mają Przeciążenie w milisekundach, aby uzyskać jawny limit czasu. Jednak gdy operacja oczekiwania powoduje niejawne wyszukiwanie formantu lub, gdy aplikacja jest zajęta, rzeczywisty czas oczekiwania może być większy niż określony limit czasu.

Poprzednie funkcje są zaawansowane i elastyczne i powinny spełniać niemal wszystkie warunki. Jednak w przypadku, gdy te metody nie spełnią Twoich potrzeb i należy wykonać kod <xref:Microsoft.VisualStudio.TestTools.UITesting.Playback.Wait%2A>albo <xref:System.Threading.Thread.Sleep%2A> lub w kodzie, zaleca się używanie odtwarzania. czekaj () zamiast wątku. uśpienia (). Przyczyny tego są następujące:

Możesz użyć <xref:Microsoft.VisualStudio.TestTools.UITesting.PlaybackSettings.ThinkTimeMultiplier%2A>właściwości, aby zmodyfikować czas trwania uśpienia. Domyślnie ta zmienna ma wartość 1, ale można ją zwiększyć lub zmniejszyć, aby zmienić czas oczekiwania na cały kod. Na przykład w przypadku testowania za pośrednictwem wolnej sieci lub innego przypadku niska wydajność można zmienić tę zmienną w jednym miejscu (lub nawet w pliku konfiguracji) na 1,5, aby dodać 50% dodatkowego oczekiwania we wszystkich miejscach.

Odtwarzanie. czekaj () wewnętrznie wywołuje wątek. uśpienia () (po wyższym obliczaniu) w mniejszych fragmentach w pętli for podczas sprawdzania, czy operacja cancel\break użytkownika. Innymi słowy odtwarzanie. czekaj () umożliwia anulowanie odtwarzania przed końcem oczekiwania, gdy uśpienie może nie być lub zgłosić wyjątek.

> [!TIP]
> Edytor kodowanego testu interfejsu użytkownika pozwala łatwo modyfikować kodowane testy interfejsu użytkownika. Za pomocą edytora kodowanego testu interfejsu użytkownika można lokalizować, wyświetlać i edytować metody testowe. Możesz również edytować akcje interfejsu użytkownika i ich skojarzone kontrolki na mapie formantów interfejsu użytkownika. Aby uzyskać więcej informacji, zobacz [Edytowanie kodowanych testów interfejsu użytkownika za pomocą edytora kodowanego testu interfejsu użytkownika](../test/editing-coded-ui-tests-using-the-coded-ui-test-editor.md).

## <a name="see-also"></a>Zobacz także

- [Używanie automatyzacji interfejsu użytkownika do testowania kodu](../test/use-ui-automation-to-test-your-code.md)
- [Tworzenie kodowanych testów interfejsu użytkownika](../test/use-ui-automation-to-test-your-code.md)
- [Przewodnik: Tworzenie, edytowanie i obsługa kodowanego testu interfejsu użytkownika](../test/walkthrough-creating-editing-and-maintaining-a-coded-ui-test.md)
- [Anatomia kodowanego testu interfejsu użytkownika](../test/anatomy-of-a-coded-ui-test.md)
- [Obsługiwane konfiguracje oraz platformy zakodowanych testów interfejsu użytkownika i nagrywania akcji](../test/supported-configurations-and-platforms-for-coded-ui-tests-and-action-recordings.md)
- [Instrukcje: Wstaw opóźnienie przed akcją interfejsu użytkownika przy użyciu edytora kodowanego testu interfejsu użytkownika](editing-coded-ui-tests-using-the-coded-ui-test-editor.md#insert-a-delay-before-a-ui-action)
