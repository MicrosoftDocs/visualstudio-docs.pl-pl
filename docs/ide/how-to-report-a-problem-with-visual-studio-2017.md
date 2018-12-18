---
title: Jak zgłosić problem z programem Visual Studio
titleSuffix: ''
description: Dowiedz się, jak zgłosić problem z programem Visual Studio 2017 do firmy Microsoft, można zdiagnozować i naprawić.
ms.custom: seodec18
ms.date: 03/11/2018
ms.technology: vs-acquisition
ms.prod: visual-studio-dev15
ms.topic: conceptual
ms.assetid: bee01179-cde5-4419-9095-190ee0ba5902
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 968b86af3620e42d7bca48335a03cca76f5afac3
ms.sourcegitcommit: 0cdd8e8a53fb4fd5e869f07c35204419fa12783d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/10/2018
ms.locfileid: "53159285"
---
# <a name="how-to-report-a-problem-with-visual-studio-2017"></a>Jak zgłosić problem w programie Visual Studio 2017

Jeśli wystąpi problem z programem Visual Studio, chcielibyśmy się dowiedzieć o nim. Poniżej przedstawiono sposób zgłosić problem do [społeczności deweloperów](https://developercommunity.visualstudio.com/) tak, aby firma Microsoft zdiagnozować i rozwiązać go.

> [!NOTE]
> Ten temat dotyczy programu Visual Studio w Windows. Dla programu Visual Studio dla komputerów Mac, zobacz [jak zgłosić problem w programie Visual Studio dla komputerów Mac](/visualstudio/mac/report-a-problem).

## <a name="report-a-problem-by-using-visual-studio"></a>Zgłoś problem w programie Visual Studio

Aby zgłosić problem dla programu Visual Studio, należy zainicjować raportu z programu Visual Studio lub Instalatora programu Visual Studio. Nie można go bezpośrednio za pomocą [społeczności deweloperów](https://developercommunity.visualstudio.com/) witryny sieci Web. Raportowanie przy użyciu programu Visual Studio umożliwia informacje diagnostyczne, które mają zostać automatycznie uwzględnione w raporcie.

![Okno podręczne z problem sporządzić raport na temat społeczności deweloperów programu Visual Studio](media/report-an-issue.png)

1. W programie Visual Studio, wybierz **pomocy** > **Wyślij opinię** > **Zgłoś Problem**.

   > [!TIP]
   > Jeśli nie można ukończyć instalacji programu Visual Studio lub nie masz dostępu do narzędzia opinii w programie Visual Studio, możesz zgłosić problem za pomocą **Instalatora programu Visual Studio**. Aby to zrobić, wybierz ikonę opinii w prawym górnym rogu **Instalatora programu Visual Studio**.

1. Jeśli nie zalogowano Cię, wybierz opcję **Sign In**; jest po prawej stronie narzędzia, jak pokazano na poniższym zrzucie ekranu. Postępuj zgodnie z instrukcjami wyświetlanymi na ekranie, aby zalogować się.

   ![Zaloguj się zgłosić problem](../ide/media/sign-in-new-ux.png)

   Po zalogowaniu, możesz zgłosić problem, który wystąpił. Możesz również głosować lub opublikowane komentarz na inny problem, który zostanie wyświetlony.

1. Po zalogowaniu będzie można wyświetlić swoje **problemów** i **działania** w **elementów I postępuj zgodnie z** ekranu

    ![Obserwowane elementy](../ide/media/items-i-follow.png)

1. Program Visual Studio udostępnia interfejs do wyszukiwania dla danego problemu i zobacz, jeśli inne zgłaszali go. Jeśli ktoś zgłosił go, "up-vote" je, aby dać nam znać.
   > [!NOTE]
   > Aby wyszukać, wprowadź odpowiedni tekst w polu wyszukiwania i kliknij przycisk Enter lub naciśnij ikonę wyszukiwania.

   ![Wyszukiwanie i głosuj na podobne problemy](../ide/media/search-and-vote.png)

1. Jeśli nie znajdziesz problem pojawił się, wybierz opcję **Zgłoś nowy problem** w dolnej części ekranu.

   > [!NOTE]
   > **Zgłoś nowy problem** przycisk pojawia się tylko w interfejsie programu Visual Studio dla społeczności deweloperów. Nie można zgłosić problem bezpośrednio na [społeczności deweloperów](https://developercommunity.visualstudio.com/) witryny sieci Web.

1. Utwórz opisowy tytuł problemu, który pomoże nam go przesłać do właściwego zespołu programu Visual Studio.

1. Przekaż dodatkowe szczegóły i w miarę możliwości opisz kroki, które spowodowały wystąpienie problemu.

   ![Zgłoś nowy problem](../ide/media/report-new-problem.png)

1. Wybierz **dalej** można przenieść do **załączniki** kartę. W tym miejscu można przechwycić bieżącego ekranu, aby wysłać je do firmy Microsoft. Aby dołączyć dodatkowe zrzuty ekranu lub inne pliki, wybierz opcję **Dołącz dodatkowe pliki**.

   ![Dołącz zrzut ekranu, aby raport o problemie programu Visual Studio](media/report-a-problem-screenshot.png)

1. Jeśli nie chcesz dołączyć zrzut ekranu lub [rejestrowania odtwarzania](#record-a-repro), wybierz opcję **dalej** można przenieść do **Podsumowanie** kartę.

1. Wybierz **przesyłania** wysłanie raportu, wraz z wszystkie obrazy i pliki śledzenia lub zrzutu. (Jeśli **przesyłania** przycisk będzie szary, upewnij się, że został podany tytuł i opis raportu.)

   Aby dowiedzieć się, jak dane są zbierane, zobacz [dane zbierane](developer-community-privacy.md#data-we-collect).

## <a name="record-a-repro"></a>Rekord odtwarzania

Pliki zrzutu śledzenia i stosu są przydatne podczas diagnozowania problemów. Firma Microsoft docenia, możesz użyć **Zgłoś Problem** narzędzie, aby zarejestrować kroki odtworzenia i wysyłać dane do firmy Microsoft. Oto jak to zrobić:

1. Po wprowadzeniu tytuł i opis dla danego problemu, wybierz **dalej** można przenieść do **załączniki** kartę.

1. Wybierz **rekordu** kartę.

1. W obszarze **Zarejestruj swoje czynności**, wybierz bieżące wystąpienie programu Visual Studio, jeśli można odtworzyć problem. Jeśli z jakiegoś powodu, na przykład jeśli zawiesiła się programu Visual Studio, wybierz  **\<Utwórz nowe wystąpienie >** do rejestrowania akcji w nowym wystąpieniu programu Visual Studio.

1. Wybierz **Rozpocznij nagrywanie**. Nadaj uprawnienia, aby uruchomić narzędzie.

   ![Wybierz pozycję "Rozpocznij nagrywanie" pozwala udostępnić plik zrzutu śledzenia i sterty w raporcie problem programu Visual Studio](../ide/media/record-dialog-box.png)

1. Gdy **Rejestrator** zostanie wyświetlone narzędzie, należy wykonać czynności, które odtworzenia problemu.

1. Gdy wszystko będzie gotowe, wybierz pozycję **zatrzymać rekordu** przycisku.

1. Poczekaj kilka minut dla programu Visual Studio zbierać i utworzyć pakiet informacje, które są zarejestrowane.

   Aby dowiedzieć się, jak dane są zbierane, zobacz [dane zbierane](developer-community-privacy.md#data-we-collect).

## <a name="when-further-information-is-needed-need-more-info"></a>Gdy dalsze informacje są potrzebne (potrzebujesz więcej informacji)

Począwszy od programu Visual Studio 2017 w wersji 15.5 istnieje nowy przepływ pracy, aby ułatwić użytkownikom, podaj dodatkowe informacje o raporty problemów.

1. Gdy ustawia inżynier z firmy Microsoft [społeczności deweloperów programu Visual Studio](https://developercommunity.visualstudio.com/) problem do **żądania dalszych informacji** stanu, każdy użytkownik, który jest opublikowany, głosujących, a następnie lub komentarz problem pobiera powiadomienie w **Zgłoś Problem** narzędzia w programie Visual Studio.

   ![Potrzebujesz więcej powiadomienia o w programie Visual Studio](../ide/media/nmi-notification.png)

1. Kliknij pozycję **Wyświetl problemy** łącze do filtrowania i sortowania widoku problemów, które wymagają uwagi. Te problemy mają również wskaźnik obok nich, aby odróżnić je ogólnie rzecz biorąc wyszukiwania.

1. Kliknij problem, aby wyświetlić szczegóły problemu.

   ![Potrzebujesz więcej informacji o powiadomień](../ide/media/nmi-details-view.png)

1. Aby wyświetlić **żądania dalszych informacji** żądania, kliknij przycisk **żądanie i Odpowiedz** łącze w widoku szczegółów problemu. Okno dialogowe jest wyświetlane żądanie.

   ![Potrzebujesz więcej informacji o powiadomień](../ide/media/nmi-request.png)

1. Dodając komentarze lub załączników albo rejestrowania kroków może dostarczyć dodatkowych informacji. To środowisko jest podobny do zgłaszania nowego problemu lub zawierającej dodatkowe informacje, gdy głosując na problem.

1. Żądanie inżynier z firmy Microsoft otrzyma powiadomienie o dodatkowe informacje. Jeśli mają one wystarczające informacje, aby zbadać, zmieni się stan problemu. W przeciwnym razie serwisant pyta, czy nawet dalsze informacje.

   > [!NOTE]
   > * Odpowiedź, powiadomienie zniknie. W jego miejsce zostanie wyświetlony Baner z Dziękujemy oraz usprawnia sposób, aby zapewnić jeszcze więcej informacji.
   > * Gdy problem zmienia stan, powiadomienia stanie się niepotrzebna dla wszystkich użytkowników obserwowanych problem.
   > * Więcej niż jedna osoba może odpowiedzieć na tym samym **żądania dalszych informacji** żądania.
   > * Nie ma **żądania dalszych informacji** przepływu pracy na [społeczności deweloperów](https://developercommunity.visualstudio.com/) po możesz uzyskać do niego dostęp bezpośrednio za pomocą przeglądarki sieci web, ale można również dołączyć komentarze i załączniki istnieje.

## <a name="search-for-solutions-or-provide-feedback"></a>Wyszukaj rozwiązania lub Wyraź swoją opinię

Jeśli nie chcesz lub nie można użyć programu Visual Studio, aby zgłosić problem, istnieje szansa, że już zgłoszono problem i rozwiązaniem opublikowano [społeczności deweloperów programu Visual Studio](https://developercommunity.visualstudio.com/) strony.

Jeśli masz problem, aby zgłosić, ale chcesz zaproponować funkcję, ma miejsce, w tym za. Aby uzyskać więcej informacji, zobacz [Zaproponuj funkcję](https://developercommunity.visualstudio.com/content/idea/post.html?space=8) strony.

## <a name="see-also"></a>Zobacz także

* [Porozmawiaj z nami](../ide/talk-to-us.md)
* [Zgłoś problem z programem Visual Studio dla komputerów Mac](/visualstudio/mac/report-a-problem)
* [Zgłoś problem przy użyciu języka C++](/cpp/how-to-report-a-problem-with-the-visual-cpp-toolset)
* [Fora społeczności deweloperów programu Visual Studio](https://developercommunity.visualstudio.com/)
* [Prywatność danych społeczności deweloperów](developer-community-privacy.md)