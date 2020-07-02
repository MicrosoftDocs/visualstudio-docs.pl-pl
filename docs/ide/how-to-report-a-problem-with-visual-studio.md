---
title: Jak zgłosić problem w programie Visual Studio
description: Dowiedz się, jak zgłosić problem w programie Visual Studio
ms.date: 03/11/2018
ms.topic: how-to
ms.assetid: bee01179-cde5-4419-9095-190ee0ba5902
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1c985d6699c75a78900366204c8bd5275f4c051d
ms.sourcegitcommit: f27084e64c79e6428746a20dda92795df996fb31
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85769933"
---
# <a name="how-to-report-a-problem-with-visual-studio-or-visual-studio-installer"></a>Jak zgłosić problem z programem Visual Studio lub Instalator programu Visual Studio

> [!NOTE]
> Aby uzyskać Visual Studio dla komputerów Mac, zobacz [temat jak zgłosić problem w programie Visual Studio dla komputerów Mac](/visualstudio/mac/report-a-problem).

Możesz zgłosić problem z programu Visual Studio lub jego instalatora za pomocą dostępnego w nich narzędzia do przesyłania opinii. Narzędzie do przesyłania opinii umożliwia łatwe dołączanie informacji diagnostycznych do opinii i ułatwia zespołom programu Visual Studio łatwiejsze diagnozowanie i rozwiązywanie problemów. Poniżej przedstawiono procedurę zgłaszania problemu.

1. **W programie Visual Studio**wybierz ikonę opinii w prawym górnym rogu, a następnie wybierz pozycję Zgłoś problem. Możesz również uzyskać dostęp do narzędzia opinii z menu **Pomoc**w  >  **wysyłaniu opinii**  >  **Zgłoś problem**.
![Zgłoś problem w oknie podręcznym w społeczności deweloperów programu Visual Studio ](media/vsfeedbackentry.png) , zgłoś problem w programie **Instalator programu Visual Studio** , jeśli nie możesz zainstalować programu Visual Studio lub nie możesz uzyskać dostępu do narzędzia opinii w programie Visual Studio.  W instalatorze wybierz ikonę opinii w prawym górnym rogu, a następnie wybierz pozycję Zgłoś problem.
![Zgłoś problem w oknie podręcznym w społeczności deweloperów programu Visual Studio](media/installer.png)

1. Jeśli nie jest zalogowany, wybierz pozycję **Zaloguj** , jak pokazano na poniższym zrzucie ekranu. Postępuj zgodnie z instrukcjami wyświetlanymi na ekranie, aby się zalogować.

   ![Zaloguj się, aby zgłosić problem](../ide/media/sign-in-new-ux.png)

   Nie tylko możesz zgłosić problem podczas logowania, ale możesz również zagłosować i komentować wszelkie istniejące Opinie.

1. Po zalogowaniu będzie można zobaczyć swoje **problemy** i **działanie** na ekranie **obserwowane elementy**

   ![Obserwowane elementy](../ide/media/items-i-follow.png)

1. Program Visual Studio udostępnia interfejs do wyszukiwania Twojego problemu i sprawdzenia, czy inne osoby je zgłosiły. Jeśli ktoś zgłosił ją, "do głosowania", aby poinformować nas o tym.
   > [!NOTE]
   > Aby wyszukać, wprowadź żądany tekst w polu wyszukiwania, a następnie kliknij przycisk ENTER lub naciśnij ikonę wyszukiwania.

   ![Wyszukaj podobne problemy i zagłosuj na nie](../ide/media/search-and-vote.png)

1. Jeśli nie znajdziesz napotkanego problemu, wybierz pozycję **zgłoś nowy problem** u dołu ekranu.

1. Utwórz opisowy tytuł problemu, który pomoże nam skierować go do poprawnego zespołu programu Visual Studio.

1. Przekaż dodatkowe szczegóły i w miarę możliwości opisz kroki, które spowodowały wystąpienie problemu.

   ![Zgłoś nowy problem](../ide/media/report-new-problem.png)

1. Wybierz przycisk **dalej** , aby przejść do karty **załączniki** . W tym miejscu możesz przechwycić bieżący ekran, aby wysłać go do firmy Microsoft. Aby dołączyć dodatkowe zrzuty ekranu lub inne pliki, wybierz **Dołącz dodatkowe pliki**.

   ![Dołącz zrzut ekranu do raportu o problemach programu Visual Studio](media/report-a-problem-screenshot.png)

1. Jeśli nie chcesz dołączyć zrzutu ekranu lub [rekordu Odtwórz](#record-a-repro), wybierz przycisk **dalej** , aby przejść do karty **Podsumowanie** .

1. Wybierz pozycję **Prześlij** , aby wysłać raport, wraz z dowolnymi obrazami i plikami śledzenia lub zrzutów. (Jeśli przycisk **Prześlij** jest wyszarzony, upewnij się, że podano tytuł i opis raportu).

   Aby uzyskać informacje o zbieranych danych, zobacz zbierane [dane](developer-community-privacy.md#data-we-collect).

## <a name="record-a-repro"></a>Rejestrowanie Odtwórz

Pliki zrzutu śledzenia i sterty są przydatne podczas diagnozowania problemów. Dziękujemy za korzystanie z narzędzia **Zgłoś problem** w celu zarejestrowania kroków Odtwórz i wysłania danych do firmy Microsoft. Oto jak to zrobić:

1. Po wprowadzeniu tytułu i opisu problemu wybierz pozycję **dalej** , aby przejść do karty **załączniki** .

1. Wybierz kartę **rekord** .

1. W obszarze **Rejestrowanie akcji**wybierz bieżące wystąpienie programu Visual Studio, jeśli możesz odtworzyć problem. Jeśli nie jest to możliwe, na przykład jeśli program Visual Studio jest zawieszony, wybierz opcję **\<Create a new instance>** rejestrowania akcji w nowym wystąpieniu programu Visual Studio.

1. Wybierz pozycję **Rozpocznij nagrywanie**. Nadaj uprawnienia do uruchamiania tego narzędzia.

   ![Wybierz pozycję "Rozpocznij nagrywanie", aby dostarczyć plik śledzenia i zrzut sterty w raporcie o problemach programu Visual Studio](../ide/media/record-dialog-box.png)

1. Po wyświetleniu narzędzia do **rejestrowania kroków** wykonaj kroki, które odtwarzają problem.

1. Gdy skończysz, wybierz przycisk **Zatrzymaj rekord** .

1. Poczekaj kilka minut, aż program Visual Studio będzie zbierać i tworzyć pakiety zarejestrowanych informacji.

   Aby uzyskać informacje o zbieranych danych, zobacz zbierane [dane](developer-community-privacy.md#data-we-collect).

## <a name="when-further-information-is-needed-need-more-info"></a>Gdy są potrzebne dalsze informacje (potrzebne są więcej informacji)

Począwszy od programu Visual Studio 2017 w wersji 15,5, istnieje nowy przepływ pracy, który ułatwia użytkownikom dostarczenie dodatkowych informacji na temat raportów o problemach.

1. Gdy inżynier firmy Microsoft ustawi problem [społeczności dla deweloperów programu Visual Studio](https://developercommunity.visualstudio.com/) , aby uzyskać informacje o stanie **więcej informacji** , każdy użytkownik, który opublikował, wygłosował lub dodał komentarz dotyczący problemu, otrzymuje powiadomienie w narzędziu **Zgłoś problem** w programie Visual Studio.

   ![Potrzebujesz więcej informacji o powiadomieniach w programie Visual Studio](../ide/media/nmi-notification.png)

1. Kliknij link **Wyświetl problemy** , aby przefiltrować i posortować widok do problemów wymagających uwagi. Te problemy mają również wskaźnik obok nich, aby odróżnić je od ogólnego wyszukiwania.

1. Kliknij problem, aby wyświetlić widok Szczegóły problemu.

   ![Potrzebna więcej informacji powiadomienie](../ide/media/nmi-details-view.png)

1. Aby wyświetlić **potrzebne więcej informacji** , kliknij link **Wyświetl ich żądanie i odpowiadaj** w widoku Szczegóły problemu. Zostanie wyświetlone okno dialogowe z żądaniem.

   ![Potrzebna więcej informacji powiadomienie](../ide/media/nmi-request.png)

1. Więcej informacji można uzyskać, dodając komentarze, załączniki lub kroki nagrywania. To środowisko jest podobne do zgłaszania nowego problemu lub podawania dodatkowych informacji podczas głosowania na temat problemu.

1. Żądanie inżyniera firmy Microsoft otrzymuje powiadomienie o podanych dodatkowych informacjach. Jeśli mają wystarczającą ilość informacji do zbadania, stan problemu ulegnie zmianie. W przeciwnym razie inżynier prosi o podanie jeszcze dalszych informacji.

   > [!NOTE]
   > * Po odebraniu odpowiedzi powiadomienie zostanie odrzucone. W swoim miejscu zobaczysz baner, który Cię Dziękujemy i ułatwia zapewnienie jeszcze większej ilości informacji.
   > * Po zmianie stanu problemu powiadomienie jest odrzucane dla wszystkich użytkowników.
   > * Więcej niż jedna osoba może odpowiedzieć na to samo żądanie **więcej informacji** .
   > * Nie jest potrzebny przepływ pracy **więcej informacji** na temat [społeczności deweloperów](https://developercommunity.visualstudio.com/) , gdy dostęp do niego odbywa się bezpośrednio za pomocą przeglądarki sieci Web, ale można również udostępniać Komentarze i załączniki.

## <a name="search-for-solutions-or-provide-feedback"></a>Wyszukaj rozwiązania lub Prześlij opinię

Jeśli nie chcesz lub nie możesz użyć programu Visual Studio, aby zgłosić problem, istnieje szansa, że problem został już zgłoszony i rozwiązanie zostało opublikowane na stronie [społeczności deweloperów programu Visual Studio](https://developercommunity.visualstudio.com/) .

Jeśli nie masz problemu z raportowaniem, ale chcesz zasugerować funkcję, istnieje już miejsce. Aby uzyskać więcej informacji, zobacz stronę [Sugeruj funkcję](https://developercommunity.visualstudio.com/content/idea/post.html?space=8) .

## <a name="see-also"></a>Zobacz także

* [Opcje opinii programu Visual Studio](../ide/feedback-options.md)
* [Zgłoś problem z Visual Studio dla komputerów Mac](/visualstudio/mac/report-a-problem)
* [Zgłoś problem w języku C++](/cpp/how-to-report-a-problem-with-the-visual-cpp-toolset)
* [Społeczność deweloperów programu Visual Studio](https://developercommunity.visualstudio.com/)
* [Prywatność danych w społeczności deweloperów](developer-community-privacy.md)
