---
title: Jak zgłosić problem z programem Visual Studio
description: Dowiedz się, jak zgłosić problem z programem Visual Studio
ms.date: 03/11/2018
ms.topic: conceptual
ms.assetid: bee01179-cde5-4419-9095-190ee0ba5902
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3fca63b5e117f77d07c54f7556a603052853c7ef
ms.sourcegitcommit: 22deb247ad951e4971f27fdab413b158415d0584
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81276504"
---
# <a name="how-to-report-a-problem-with-visual-studio-or-visual-studio-installer"></a>Jak zgłosić problem z instalatorem programu Visual Studio lub Visual Studio

> [!NOTE]
> W programie Visual Studio dla komputerów Mac zobacz [Jak zgłosić problem w programie Visual Studio dla komputerów Mac](/visualstudio/mac/report-a-problem).

Problem można zgłosić w programie Visual Studio lub jego instalatorze za pomocą dołączonego w nich narzędzia opinii. Narzędzie opinii umożliwia łatwe dołączanie informacji diagnostycznych do opinii i pomaga zespołom programu Visual Studio znacznie skuteczniej diagnozować i rozwiązywać problemy. Oto kroki, aby zgłosić problem.

1. **W programie Visual Studio**wybierz ikonę opinii w prawym górnym rogu i wybierz pozycję Zgłoś problem. Dostęp do narzędzia opinii można również uzyskać z menu **Pomoc w** > **wysyłaniu opinii** > **Zgłoś problem**.
![Zgłoś problem wyskakującym okienku na platformie Visual Studio Developer Community](media/vsfeedbackentry.png) Alternatywnie, zgłoś problem w **Instalatorze programu Visual Studio,** jeśli nie możesz zainstalować programu Visual Studio lub nie możesz uzyskać dostępu do narzędzia opinii w programie Visual Studio.  W Instalatorze wybierz ikonę opinii w prawym górnym rogu i wybierz pozycję Zgłoś problem.
![Zgłoś wyskakujące okienko problemu w społeczności deweloperów programu Visual Studio](media/installer.png)

1. Jeśli nie jest zalogowany, wybierz **pozycję Zaloguj się,** jak pokazano na poniższym zrzucie ekranu. Postępuj zgodnie z instrukcjami wyświetlanymi na ekranie, aby się zalogować.

   ![Zaloguj się, aby zgłosić problem](../ide/media/sign-in-new-ux.png)

   Nie tylko możesz zgłosić problem po zalogowaniu się, ale także głosować i komentować wszelkie istniejące opinie.

1. Po zalogowaniu się na ekranie Elementy, które **obserwuję,** zobaczysz swoje **problemy** i **aktywność.**

   ![Przedmioty, które obserwuję](../ide/media/items-i-follow.png)

1. Visual Studio udostępnia interfejs, aby wyszukać problem i sprawdzić, czy inni zgłosili go. Jeśli ktoś to zgłosił, "up-vote" to poinformować nas o tym.
   > [!NOTE]
   > Aby wyszukać, wprowadź żądany tekst w polu wyszukiwania i kliknij przycisk Enter lub naciśnij ikonę Wyszukiwania.

   ![Szukaj i głosuj na podobne problemy](../ide/media/search-and-vote.png)

1. Jeśli nie znajdziesz napotkanego problemu, wybierz pozycję **Zgłoś nowy problem** u dołu ekranu.

   > [!NOTE]
   > Przycisk **Zgłoś nowy problem** pojawia się tylko w interfejsie programu Visual Studio dla społeczności deweloperów. Nie możesz zgłosić problemu bezpośrednio w witrynie [społeczności deweloperów.](https://developercommunity.visualstudio.com/)

1. Utwórz opisowy tytuł problemu, który pomaga nam kierować go do odpowiedniego zespołu programu Visual Studio.

1. Przekaż dodatkowe szczegóły i w miarę możliwości opisz kroki, które spowodowały wystąpienie problemu.

   ![Zgłoś nowy problem](../ide/media/report-new-problem.png)

1. Wybierz **pozycję Dalej,** aby przejść do karty **Załączniki.** W tym miejscu można przechwycić bieżący ekran, aby wysłać go do firmy Microsoft. Aby dołączyć dodatkowe zrzuty ekranu lub inne pliki, wybierz pozycję **Dołącz dodatkowe pliki**.

   ![Dołączanie zrzutu ekranu do raportu o problemie z programem Visual Studio](media/report-a-problem-screenshot.png)

1. Jeśli nie chcesz dołączać zrzutu ekranu ani [nagrywać repro,](#record-a-repro)wybierz **pozycję Dalej,** aby przejść do karty **Podsumowanie.**

1. Wybierz **opcję Prześlij,** aby wysłać raport wraz z wszelkimi obrazami i plikami śledzenia lub zrzutu. (Jeśli przycisk **Prześlij** jest wyszarzony, upewnij się, że podano tytuł i opis raportu).

   Aby uzyskać informacje o gromadzonych danych, zobacz [Dane, które zbieramy.](developer-community-privacy.md#data-we-collect)

## <a name="record-a-repro"></a>Nagrywanie repro

Pliki zrzutu śledzenia i sterty są przydatne w pomaganiu nam w diagnozowaniu problemów. Doceniamy to, gdy używasz narzędzia **Zgłoś problem** do rejestrowania kroków repropro i wysyłania danych do firmy Microsoft. Oto jak to zrobić:

1. Po wprowadzeniu tytułu i opisu problemu wybierz pozycję **Dalej,** aby przejść do karty **Załączniki.**

1. Wybierz kartę **Rekord.**

1. W obszarze **Nagraj swoje akcje**wybierz bieżące wystąpienie programu Visual Studio, jeśli można odtworzyć problem w tym miejscu. Jeśli nie można, na przykład jeśli visual studio jest zawieszony, wybierz ** \<Utwórz nowe wystąpienie>,** aby nagrać akcje w nowym wystąpieniu programu Visual Studio.

1. Wybierz **pozycję Rozpocznij nagrywanie**. Nadaj uprawnienia do uruchamiania narzędzia.

   ![Wybierz opcję "Rozpocznij nagrywanie", aby udostępnić plik zrzutu śledzenia i sterty w raporcie o problemie z programem Visual Studio](../ide/media/record-dialog-box.png)

1. Po **wyświetleniu** narzędzia Rejestrator kroków wykonaj kroki, które odtwarzają problem.

1. Po zakończeniu wybierz przycisk **Zatrzymaj nagrywanie.**

1. Poczekaj kilka minut, aż program Visual Studio zbierze i zapakuje zarejestrowane informacje.

   Aby uzyskać informacje o gromadzonych danych, zobacz [Dane, które zbieramy.](developer-community-privacy.md#data-we-collect)

## <a name="when-further-information-is-needed-need-more-info"></a>Gdy potrzebne są dalsze informacje (Potrzebujesz więcej informacji)

Począwszy od programu Visual Studio 2017 w wersji 15.5, istnieje nowy przepływ pracy, aby pomóc użytkownikom w dostarczaniu dodatkowych informacji na temat raportów o problemach.

1. Gdy inżynier firmy Microsoft ustawia problem [społeczności deweloperów programu Visual Studio](https://developercommunity.visualstudio.com/) na stan Potrzebujesz więcej **informacji,** każdy użytkownik, który opublikował, zagłosował, śledził lub skomentował ten problem, otrzymuje powiadomienie w narzędziu **Zgłoś problem** w programie Visual Studio.

   ![Potrzebujesz więcej informacji powiadomienie w programie Visual Studio](../ide/media/nmi-notification.png)

1. Kliknij **łącze Wyświetl problemy,** aby filtrować i sortować widok na problemy, które wymagają uwagi. Problemy te mają również wskaźnik obok nich, aby odróżnić je w ogólnym wyszukiwaniu.

1. Kliknij na problem, aby wyświetlić widok szczegółów problemu.

   ![Potrzebujesz więcej informacji powiadomienie](../ide/media/nmi-details-view.png)

1. Aby wyświetlić żądanie **Potrzebujesz więcej informacji,** kliknij łącze **Wyświetl ich żądanie i odpowiedz** w widoku szczegółów problemu. Okno dialogowe zawiera żądanie.

   ![Potrzebujesz więcej informacji powiadomienie](../ide/media/nmi-request.png)

1. Więcej informacji można podać, dodając komentarze, załączniki lub czynności nagraniowe. To doświadczenie jest podobne do zgłaszania nowego problemu lub dostarczania dodatkowych informacji podczas głosowania nad problemem.

1. Żądający inżynier firmy Microsoft otrzymuje powiadomienie o dodatkowych informacjach. Jeśli mają wystarczającą ilość informacji do zbadania, zmienia się stan problemu. W przeciwnym razie inżynier prosi o jeszcze więcej informacji.

   > [!NOTE]
   > * Gdy odpowiesz, powiadomienie zniknie. Na jego miejscu widać baner, który dziękuje i ułatwia sposób na dostarczenie jeszcze więcej informacji.
   > * Gdy problem zmieni stan, powiadomienie zniknie dla wszystkich, którzy śledzą problem.
   > * Więcej niż jedna osoba może odpowiedzieć na to samo żądanie **Need More Info.**
   > * Nie ma przepływu pracy **Need More Info** w społeczności [deweloperów,](https://developercommunity.visualstudio.com/) gdy uzyskujesz do niej dostęp bezpośrednio za pośrednictwem przeglądarki internetowej, ale możesz również tam przekazywać komentarze i załączniki.

## <a name="search-for-solutions-or-provide-feedback"></a>Wyszukiwanie rozwiązań lub przekazywanie opinii

Jeśli nie chcesz lub nie możesz użyć programu Visual Studio do zgłoszenia problemu, istnieje prawdopodobieństwo, że problem został już zgłoszony i rozwiązanie opublikowane na stronie [społeczności deweloperów programu Visual Studio.](https://developercommunity.visualstudio.com/)

Jeśli nie masz problemu z zgłoszeniem, ale chcesz zaproponować funkcję, jest na to miejsce. Aby uzyskać więcej informacji, zobacz stronę [Zaproponuj obiekt.](https://developercommunity.visualstudio.com/content/idea/post.html?space=8)

## <a name="see-also"></a>Zobacz też

* [Opcje opinii programu Visual Studio](../ide/feedback-options.md)
* [Zgłaszanie problemu z programem Visual Studio dla komputerów Mac](/visualstudio/mac/report-a-problem)
* [Zgłoś problem z c++](/cpp/how-to-report-a-problem-with-the-visual-cpp-toolset)
* [Społeczność deweloperów programu Visual Studio](https://developercommunity.visualstudio.com/)
* [Prywatność danych w społeczności deweloperów](developer-community-privacy.md)
