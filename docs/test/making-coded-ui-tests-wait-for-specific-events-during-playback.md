---
title: Spraw, aby kodowane testy interfejsu użytkownika czekały na określone zdarzenia
ms.date: 11/04/2016
ms.topic: conceptual
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 6e594a6aec3f9e3a9664c5eac829b27f96f12ea0
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "75584455"
---
# <a name="make-coded-ui-tests-wait-for-specific-events-during-playback"></a>Spraw, aby kodowane testy interfejsu użytkownika czekały na określone zdarzenia podczas odtwarzania

W kodowane odtwarzanie testu interfejsu użytkownika, można poinstruować test czekać na pewne zdarzenia wystąpią, takie jak okno, aby pojawić się, pasek postępu zniknąć i tak dalej. Aby to zrobić, należy użyć odpowiedniej metody UITestControl.WaitForControlXXX(), zgodnie z opisem w poniższej tabeli. Na przykład kodowany test interfejsu użytkownika, który czeka na formant, który ma być włączony przy użyciu <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl.WaitForControlEnabled%2A> metody, zobacz [Instruktaż: Tworzenie, edytowanie i obsługa kodowanego testu interfejsu użytkownika](../test/walkthrough-creating-editing-and-maintaining-a-coded-ui-test.md).

[!INCLUDE [coded-ui-test-deprecation](includes/coded-ui-test-deprecation.md)]

**Wymagania**

Visual Studio Enterprise

> [!TIP]
> Można również dodać opóźnienia przed działaniami przy użyciu Edytora testów kodowanych interfejsu użytkownika. Aby uzyskać więcej informacji, zobacz [Jak: Wstawianie opóźnienia przed akcją interfejsu użytkownika przy użyciu edytora kodowanych testów interfejsu użytkownika](editing-coded-ui-tests-using-the-coded-ui-test-editor.md#insert-a-delay-before-a-ui-action).

**UITestControl.WaitForControlXXX() Metody**

<xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl.WaitForControlReady%2A>

Czeka, aż formant będzie gotowy do zaakceptowania danych wejściowych myszy i klawiatury. Aparat niejawnie wywołuje ten interfejs API dla wszystkich akcji czekać na formant, aby być gotowy przed wykonaniem jakiejkolwiek operacji. Jednak w niektórych scenariuszach ezoterycznych może być konieczne wywołanie jawne.

<xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl.WaitForControlEnabled%2A>

Czeka na formantu, aby włączyć, gdy kreator wykonuje niektóre asynchroniiowe sprawdzanie poprawności danych wejściowych przez wywołanie serwera. Można na przykład zaczekać, aż przycisk **Dalej** kreatora zostanie włączony (). Na przykład tej metody zobacz [Przewodnik: Tworzenie, edytowanie i obsługa kodowany test interfejsu użytkownika](../test/walkthrough-creating-editing-and-maintaining-a-coded-ui-test.md).

<xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl.WaitForControlExist%2A>

Czeka na formant pojawi się w interfejsie użytkownika. Na przykład oczekujesz okna dialogowego błędu po zakończeniu sprawdzania poprawności parametrów przez aplikację. Czas sprawdzania poprawności jest zmienny. Za pomocą tej metody można czekać na okno dialogowe błędu.

<xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl.WaitForControlNotExist%2A>

Czeka na formantu zniknąć z interfejsu użytkownika. Na przykład można poczekać, aż pasek postępu zniknie.

<xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl.WaitForControlPropertyEqual%2A>

Czeka na określoną właściwość formantu, aby mieć pod uwagę wartość. Na przykład można poczekać, aż tekst stanu zmieni się na **Gotowe**.

<xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl.WaitForControlPropertyNotEqual%2A>

Czeka na określoną właściwość formantu, aby mieć przeciwieństwo określonej wartości. Na przykład poczekaj, aż pole edycji nie będzie tylko do odczytu, czyli edytowalne.

<xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl.WaitForControlCondition%2A>

Czeka na określony predykat zwraca `true`się . Może to służyć do operacji złożonego oczekiwania (jak warunki OR) na danym formancie. Na przykład można poczekać, aż tekst stanu zakończy **się pomyślnie** lub **nie powiodło się,** jak pokazano w poniższym kodzie:

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

Wszystkie poprzednie metody są metody wystąpienia UITestControl. Ta metoda jest metodą statyczną. Ta metoda czeka również na określony predykat, `true` ale może służyć do operacji złożonych oczekiwania (takich jak warunki OR) na wielu formantów. Na przykład można poczekać, aż tekst stanu zakończy **się pomyślnie** lub do wyświetlenie komunikatu o błędzie, jak pokazano w poniższym kodzie:

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

Metody zwracają true, jeśli oczekiwanie zakończy się pomyślnie i false, jeśli oczekiwanie nie powiodło się.

Niejawny limit czasu dla operacji <xref:Microsoft.VisualStudio.TestTools.UITesting.PlaybackSettings.WaitForReadyTimeout%2A> oczekiwania jest określony przez właściwość. Wartość domyślna tej właściwości to 60000 milisekund (jedna minuta).

Metody mają przeciążenie, aby wziąć jawny limit czasu w milisekundach. Jednak gdy operacja oczekiwania powoduje niejawne wyszukiwanie formantu lub, gdy aplikacja jest zajęta, rzeczywisty czas oczekiwania może być więcej niż określony limit czasu.

Poprzednie funkcje są wydajne i elastyczne i powinny spełniać prawie wszystkie warunki. Jednak w przypadku, gdy te metody nie spełniają twoich <xref:Microsoft.VisualStudio.TestTools.UITesting.Playback.Wait%2A>potrzeb <xref:System.Threading.Thread.Sleep%2A> i trzeba kodować lub w kodzie w kodzie, zaleca się użycie interfejsu API Playback.Wait() zamiast interfejsu API Thread.Sleep(). Powody tego są:

Za pomocą <xref:Microsoft.VisualStudio.TestTools.UITesting.PlaybackSettings.ThinkTimeMultiplier%2A>właściwości można zmodyfikować czas trwania snu. Domyślnie ta zmienna jest 1, ale można zwiększyć lub zmniejszyć go, aby zmienić czas oczekiwania całego kodu. Na przykład jeśli testujesz w szczególności za pośrednictwem powolnej sieci lub innego przypadku o powolnej wydajności, możesz zmienić tę zmienną w jednym miejscu (lub nawet w pliku konfiguracyjnym) na 1,5, aby dodać 50% dodatkowego oczekiwania we wszystkich miejscach.

Playback.Wait() wewnętrznie wywołuje Thread.Sleep() (po przekroju obliczeniowym) w mniejszych fragmentach w pętli for-loop podczas sprawdzania operacji anuluj\przerwać użytkownika. Innymi słowy Playback.Wait() umożliwia anulowanie odtwarzania przed zakończeniem oczekiwania, podczas gdy uśpienie może nie lub zgłosić wyjątek.

> [!TIP]
> Edytor kodowanych testów interfejsu użytkownika umożliwia łatwe modyfikowanie kodowanych testów interfejsu użytkownika. Za pomocą Edytora testów kodowanych interfejsu użytkownika można zlokalizować, wyświetlić i edytować metody testowe. Akcje interfejsu użytkownika i skojarzone z nimi formanty można również edytować na mapie sterowania interfejsu użytkownika. Aby uzyskać więcej informacji, zobacz [Edytowanie zakodowanych testów interfejsu użytkownika przy użyciu edytora kodowanych testów interfejsu użytkownika](../test/editing-coded-ui-tests-using-the-coded-ui-test-editor.md).

## <a name="see-also"></a>Zobacz też

- [Użyj automatyzacji interfejsu użytkownika, aby przetestować kod](../test/use-ui-automation-to-test-your-code.md)
- [Tworzenie kodowanych testów interfejsu użytkownika](../test/use-ui-automation-to-test-your-code.md)
- [Przewodnik: Tworzenie, edytowanie i obsługa kodowany test interfejsu użytkownika](../test/walkthrough-creating-editing-and-maintaining-a-coded-ui-test.md)
- [Anatomia zakodowany test interfejsu użytkownika](../test/anatomy-of-a-coded-ui-test.md)
- [Obsługiwane konfiguracje i platformy dla zakodowanych testów interfejsu użytkownika i nagrań akcji](../test/supported-configurations-and-platforms-for-coded-ui-tests-and-action-recordings.md)
- [Jak: Wstaw opóźnienie przed akcją interfejsu użytkownika przy użyciu kodowego edytora testów interfejsu użytkownika](editing-coded-ui-tests-using-the-coded-ui-test-editor.md#insert-a-delay-before-a-ui-action)
