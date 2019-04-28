---
title: Wprowadź oczekiwania testy kodowane interfejsu użytkownika dla określonych zdarzeń
ms.date: 11/04/2016
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3e2c83b74c2649681251ffa51f1366c0ce96d677
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62788814"
---
# <a name="make-coded-ui-tests-wait-for-specific-events-during-playback"></a>Utworzyć kodowane testy interfejsu użytkownika, poczekaj, aż określonych zdarzeń podczas odtwarzania

Podczas odtwarzania testu kodowanego interfejsu użytkownika można nakazać testu oczekiwania dla określonych zdarzeń, takiego jak okno pojawia się pasek postępu zniknąć i tak dalej. Aby to zrobić, użyj odpowiedniej metody UITestControl.WaitForControlXXX(), zgodnie z opisem w poniższej tabeli. Na przykład kodowane testy interfejsu użytkownika, która czeka formantu, który ma zostać włączone za pomocą <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl.WaitForControlEnabled%2A> metody, zobacz [instruktażu: Tworzenie, edytowanie i obsługa kodowanego testu interfejsu użytkownika](../test/walkthrough-creating-editing-and-maintaining-a-coded-ui-test.md).

[!INCLUDE [coded-ui-test-deprecation](includes/coded-ui-test-deprecation.md)]

**Wymagania**

Visual Studio Enterprise

> [!TIP]
> Można również dodać opóźnienia przed akcji za pomocą edytora kodowanego testu interfejsu użytkownika. Aby uzyskać więcej informacji, zobacz [jak: Wstawianie opóźnienia przed akcją UI za pomocą edytora kodowanego testu interfejsu użytkownika](editing-coded-ui-tests-using-the-coded-ui-test-editor.md#insert-a-delay-before-a-ui-action).

**UITestControl.WaitForControlXXX() Methods**

<xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl.WaitForControlReady%2A>

Czeka na formant aby być gotowy do akceptowania myszy i klawiatury. Aparat niejawnie wywołuje ten interfejs API dla wszystkich akcji, oczekiwania na formant będzie gotowa, przed wykonaniem wszelkich operacji. W niektórych wybór scenariusza może mieć celu jawnym wywołaniem.

<xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl.WaitForControlEnabled%2A>

Czeka na formant aby można włączyć, gdy kreator wykonuje niektóre asynchroniczne sprawdzanie poprawności danych wejściowych przez wykonywanie wywołań do serwera. Można na przykład metodę, aby czekać na **dalej** przycisk kreatora Aby być (włączone). Aby uzyskać przykład tej metody, zobacz [instruktażu: Tworzenie, edytowanie i obsługa kodowanego testu interfejsu użytkownika](../test/walkthrough-creating-editing-and-maintaining-a-coded-ui-test.md).

<xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl.WaitForControlExist%2A>

Czeka na formant, który ma być wyświetlana w Interfejsie użytkownika. Na przykład po aplikacji ma wykonać sprawdzanie poprawności parametrów są oczekiwane okna dialogowego błędu. Czas potrzebny do sprawdzania poprawności jest zmienna. Ta metoda umożliwia oczekiwania dla okna dialogowego błędu.

<xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl.WaitForControlNotExist%2A>

Czeka na formant są usuwane z interfejsu użytkownika. Na przykład możesz poczekać, aż pasek postępu zniknąć.

<xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl.WaitForControlPropertyEqual%2A>

Czeka, aż do określonej właściwości formantu, aby mieć dana wartość. Na przykład trzeba odczekać tekstu stanu zmienić **gotowe**.

<xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl.WaitForControlPropertyNotEqual%2A>

Czeka, aż do określonej właściwości formantu, aby mieć przeciwieństwo określoną wartość. Na przykład po odczekaniu pole edycji, aby nie może być tylko do odczytu, oznacza to, że można edytować.

<xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl.WaitForControlCondition%2A>

Oczekuje określony predykat zwraca się `true`. To może służyć do operacji oczekiwania złożonych (np. warunków OR) na określonej kontrolki. Na przykład możesz poczekaj, aż będzie tekst statusu **Powodzenie** lub **niepowodzenie** jak pokazano w poniższym kodzie:

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

 Wszystkich poprzednich metod to wystąpienie metody UITestControl. Ta metoda jest statyczna metoda. Ta metoda także oczekuje na określony predykat to `true` , ale może służyć do operacji oczekiwania złożonych (np. warunków OR) na wielu kontrolek. Na przykład możesz poczekaj, aż będzie tekst statusu **Powodzenie** lub dopóki nie zostanie wyświetlony komunikat o błędzie, jak pokazano w poniższym kodzie:

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

 Metody zwracają wartość true, jeśli czas oczekiwania jest udane, jak i wartość false, jeśli czas oczekiwania nie powiodła się.

 Niejawne limit czasu operacji oczekiwania jest określony przez <xref:Microsoft.VisualStudio.TestTools.UITesting.PlaybackSettings.WaitForReadyTimeout%2A> właściwości. Wartość domyślna tej właściwości to 60000 milisekund (co minutę).

 Metody mają przeciążenia do wykonania jawnej limitu czasu w milisekundach. Jednak podczas operacji oczekiwania w wyniku niejawnego wyszukiwania dla formantu, lub gdy aplikacja jest zajęta, rzeczywisty czas może być większa niż limit czasu określony.

 Poprzednie funkcje są wydajne i elastyczne i powinny spełniać prawie wszystkie warunki. Jednak w przypadku tych metod nie spełnia Twoich potrzeb i należy kodu albo <xref:Microsoft.VisualStudio.TestTools.UITesting.Playback.Wait%2A>, lub <xref:System.Threading.Thread.Sleep%2A> w kodzie, zaleca się używać Playback.Wait() zamiast Thread.Sleep() interfejsu API. Są to:

 Możesz użyć <xref:Microsoft.VisualStudio.TestTools.UITesting.PlaybackSettings.ThinkTimeMultiplier%2A>właściwości, aby zmodyfikować czas trwania uśpienia. Domyślnie ta zmienna ma wartość 1, ale można zwiększyć lub zmniejszyć, aby zmienić czas oczekiwania w całym kodzie. Na przykład testujesz specjalnie za pośrednictwem wolno działającą sieć lub innym przypadku spadek wydajności, można zmienić tej zmiennej w jednym miejscu (lub nawet w pliku konfiguracyjnym) do wersji 1.5, można dodać 50% dodatkowego czekać na wszystkich miejsc.

 Playback.Wait() wywołuje wewnętrznie Thread.Sleep() (po powyżej obliczenia) na mniejsze fragmenty w pętli for podczas sprawdzania, czy operacja cancel\break użytkownika. Innymi słowy Playback.Wait() umożliwia anulowanie odtwarzania przed zakończeniem czas oczekiwania, natomiast uśpienia może nie lub wyjątku.

> [!TIP]
> Edytor kodowanego testu interfejsu użytkownika umożliwia łatwe modyfikowanie kodowanych testów interfejsu użytkownika. Za pomocą edytora testu interfejsu użytkownika, możesz zlokalizować, wyświetlić i edytować swoje metody testowe. Można również edytować akcje interfejsu użytkownika oraz skojarzone z nimi kontrolki w mapy formantów interfejsu użytkownika. Aby uzyskać więcej informacji, zobacz [Edycja kodowanych testów interfejsu użytkownika, za pomocą edytora kodowanego testu interfejsu użytkownika](../test/editing-coded-ui-tests-using-the-coded-ui-test-editor.md).

## <a name="see-also"></a>Zobacz także

- [Używanie automatyzacji interfejsu użytkownika do testowania kodu](../test/use-ui-automation-to-test-your-code.md)
- [Tworzenie kodowanych testów interfejsu użytkownika](../test/use-ui-automation-to-test-your-code.md)
- [Przewodnik: Tworzenie, edytowanie i obsługa kodowanego testu interfejsu użytkownika](../test/walkthrough-creating-editing-and-maintaining-a-coded-ui-test.md)
- [Anatomia kodowanego testu interfejsu użytkownika](../test/anatomy-of-a-coded-ui-test.md)
- [Obsługiwane konfiguracje oraz platformy zakodowanych testów interfejsu użytkownika i nagrywania akcji](../test/supported-configurations-and-platforms-for-coded-ui-tests-and-action-recordings.md)
- [Instrukcje: Wstawianie opóźnienia przed akcją UI za pomocą edytora kodowanego testu interfejsu użytkownika](editing-coded-ui-tests-using-the-coded-ui-test-editor.md#insert-a-delay-before-a-ui-action)
