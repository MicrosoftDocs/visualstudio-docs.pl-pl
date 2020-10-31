---
title: Nowe środowisko Git w programie Visual Studio (wersja zapoznawcza)
titleSuffix: ''
description: Dowiedz się więcej na temat nowego zintegrowanego środowiska Git w programie Visual Studio 2019
ms.date: 10/13/2020
ms.topic: conceptual
ms.author: tglee
author: prnadago
ms.manager: jillfra
monikerRange: vs-2019
ms.openlocfilehash: ad75fcff26365afdbc4fb4b02975d7c3211fa79b
ms.sourcegitcommit: a731a9454f1fa6bd9a18746d8d62fe2e85e5ddb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2020
ms.locfileid: "92334210"
---
# <a name="new-git-experience-in-visual-studio-preview"></a>Nowe środowisko Git w programie Visual Studio (wersja zapoznawcza)

Począwszy od [wersji 16,6](/visualstudio/releases/2019/release-notes-v16.6), program Visual Studio 2019 zawiera teraz nowe środowisko git, które ułatwia korzystanie z narzędzia Git z poziomu środowiska IDE. Git to najczęściej używany nowoczesny system kontroli wersji, więc niezależnie od tego, czy jesteś specjalistą dla profesjonalistów, czy wiesz, jak kod, program git może być bardzo przydatny dla użytkownika.

> [!TIP]
> Jeśli dopiero zaczynasz pracę z usługą git, https://git-scm.com/ Witryna sieci Web jest dobrym miejscem do uruchomienia. W tym miejscu znajdziesz popularne książki online, wideo podstawowe informacje dotyczące usługi git i arkusze Ściągawka.

## <a name="how-to-start-using-git-in-visual-studio"></a>Jak zacząć korzystać z usługi Git w programie Visual Studio

Aby włączyć nowe środowisko git, przejdź do pozycji **Narzędzia**  >  **Opcje**  >  **środowisko**  >  **Podgląd funkcji** , a następnie zaznacz pole wyboru **nowe środowisko użytkownika usługi git** .

:::image type="content" source="media/git-opt-new-user-experience.png" alt-text="Zrzut ekranu przedstawiający sekcję funkcje w wersji zapoznawczej okna dialogowego Opcje w programie Visual Studio ":::

Istnieją trzy sposoby używania usługi Git w programie Visual Studio 2019:

- [Otwórz istniejące repozytorium git](#open-an-existing-local-repository). Jeśli Twój kod znajduje się już na Twojej maszynie, możesz otworzyć **go za pomocą polecenia**  >  **Otwórz**  >  **projekt/rozwiązanie** (lub **folder** ), a program Visual Studio automatycznie wykrywa, czy ma zainicjowane repozytorium git.
- [Utwórz nowe repozytorium git](#create-a-new-git-repository). Jeśli kod nie jest skojarzony z usługą git, możesz utworzyć nowe repozytorium git.
- [Klonuj istniejące repozytorium git](#clone-an-existing-git-repository). Jeśli kod, nad którym chcesz korzystać, nie znajduje się na komputerze, możesz sklonować wszystkie istniejące repozytoria zdalne.

## <a name="create-a-new-git-repository"></a>Utwórz nowe repozytorium git

Jeśli kod nie jest skojarzony z usługą git, możesz zacząć od utworzenia nowego repozytorium git. W tym celu wybierz pozycję **git**  >  **Utwórz repozytorium git** na pasku menu. Następnie w oknie dialogowym **Tworzenie repozytorium git** wprowadź informacje.

:::image type="content" source="media/git-create-repository.png" alt-text="Zrzut ekranu przedstawiający sekcję funkcje w wersji zapoznawczej okna dialogowego Opcje w programie Visual Studio ":::

Okno dialogowe **Tworzenie repozytorium git** ułatwia wypychanie nowego repozytorium do usługi GitHub. Domyślnie nowe repozytorium jest prywatne, co oznacza, że jesteś jedynym, kto ma do niego dostęp. Jeśli wyłączysz to pole, repozytorium będzie publiczne, co oznacza, że każdy z nich może go wyświetlić.

> [!TIP]
> Bez względu na to, czy repozytorium jest publiczne, czy prywatne, najlepiej bezpieczniej utworzyć kopię zapasową kodu przechowywaną w serwisie GitHub, nawet jeśli nie pracujesz z zespołem. Zapewnia to również, że Twój kod jest dostępny niezależnie od używanego komputera.

Można utworzyć tylko lokalne repozytorium git przy użyciu opcji **tylko lokalna** . Możesz też połączyć repozytorium z dowolnym istniejącym pustym repozytorium zdalnym dla dowolnego innego dostawcy Git za pomocą istniejącej opcji **zdalnej** .

## <a name="clone-an-existing-git-repository"></a>Klonowanie istniejącego repozytorium git

Program Visual Studio zawiera proste środowisko klonowania. Jeśli znasz adres URL repozytorium, które chcesz sklonować, możesz wkleić adres URL w sekcji **Lokalizacja repozytorium** , a następnie wybrać lokalizację dysku, do której ma zostać sklonowany program Visual Studio.

:::image type="content" source="media/git-clone-repository.png" alt-text="Zrzut ekranu przedstawiający sekcję funkcje w wersji zapoznawczej okna dialogowego Opcje w programie Visual Studio ":::

Jeśli nie znasz adresu URL repozytorium, program Visual Studio ułatwia przeglądanie i Klonowanie istniejącego repozytorium usługi GitHub lub Azure DevOps.

### <a name="open-an-existing-local-repository"></a>Otwórz istniejące repozytorium lokalne

Po sklonowaniu repozytorium lub utworzeniu go program Visual Studio wykrywa repozytorium git i dodaje je do listy **lokalnych repozytoriów** w menu git. W tym miejscu możesz szybko uzyskać dostęp do repozytoriów Git i przełączać się między nimi.

:::image type="content" source="media/git-local-repositories.png" alt-text="Zrzut ekranu przedstawiający sekcję funkcje w wersji zapoznawczej okna dialogowego Opcje w programie Visual Studio ":::

## <a name="view-files-in-solution-explorer"></a>Wyświetl pliki w Eksplorator rozwiązań

Po sklonowaniu repozytorium lub otwarciu repozytorium lokalnego program Visual Studio przełącza użytkownika do tego kontekstu git przez zapisanie i zamknięcie wszelkich otwartych wcześniej rozwiązań i projektów. Eksplorator rozwiązań ładuje folder w katalogu głównym repozytorium git i skanuje drzewo katalogów dla wszystkich plików widoku. Obejmują one pliki takie jak CMakeLists.txt lub z rozszerzeniem. sln.

Program Visual Studio dostosowuje swój widok na podstawie tego, który plik widoku jest ładowany w Eksplorator rozwiązań:

- W przypadku klonowania repozytorium zawierającego pojedynczy plik. sln, Eksplorator rozwiązań bezpośrednio ładuje to rozwiązanie.
- Jeśli Eksplorator rozwiązań nie wykryje żadnych plików SLN w repozytorium, domyślnie wczytuje widok folderu.
- Jeśli repozytorium zawiera więcej niż jeden plik. sln, Eksplorator rozwiązań wyświetla listę dostępnych widoków do wyboru.

Można przełączać się między aktualnie otwartym widokiem a listą widoków przy użyciu przycisku **Przełącz widoki** na pasku narzędzi Eksplorator rozwiązań.

:::image type="content" source="media/git-solution-explorer-views.png" alt-text="Zrzut ekranu przedstawiający sekcję funkcje w wersji zapoznawczej okna dialogowego Opcje w programie Visual Studio ":::

## <a name="git-changes-window"></a>Okno zmian git

Git śledzi zmiany plików w repozytorium podczas pracy i oddziela pliki w repozytorium do trzech kategorii. Te zmiany są równoważne z informacjami wyświetlanymi po wprowadzeniu `git status` polecenia w wierszu polecenia:

- **Pliki niezmodyfikowane** : te pliki nie zostały zmienione od czasu ostatniego zatwierdzenia.
- **Zmodyfikowane pliki** : te pliki mają zmiany od czasu ostatniego zatwierdzenia, ale jeszcze nie zostały przygotowane do następnego zatwierdzenia.
- **Pliki przemieszczane** : te pliki zawierają zmiany, które zostaną dodane do następnego zatwierdzenia.

Podczas pracy program Visual Studio śledzi zmiany plików w projekcie w sekcji **zmiany** w oknie zmiany w usłudze **git** .

:::image type="content" source="media/git-changes-window.png" alt-text="Zrzut ekranu przedstawiający sekcję funkcje w wersji zapoznawczej okna dialogowego Opcje w programie Visual Studio ":::

Gdy wszystko będzie gotowe do przemieszczania zmian, kliknij **+** przycisk (plus) w każdym pliku, który chcesz przygotować, lub kliknij prawym przyciskiem myszy plik, a następnie wybierz pozycję **etap** . Możesz również przemieścić wszystkie zmodyfikowane pliki jednym kliknięciem, używając przycisku przemieszczenie wszystko **+** (plus) w górnej części sekcji **zmiany** .

Podczas przygotowywania zmiany program Visual Studio tworzy sekcję **przemieszczone zmiany** . Tylko zmiany w sekcji **przemieszczane zmiany** są dodawane do następnego zatwierdzenia, które można wykonać, wybierając pozycję **Zatwierdź przygotowane** . Zmiany mogą być również nieprzygotowane, klikając przycisk **–** (minus). Równoważne polecenie dla tej akcji to `git commit -m "Your commit message"` .

Możesz również zrezygnować z przygotowania zmodyfikowanych plików, pomijając obszar przejściowy. W takim przypadku program Visual Studio pozwala na zatwierdzanie zmian bezpośrednio bez konieczności ich przemieszczania. Po prostu wprowadź wiadomość dotyczącą zatwierdzenia, a następnie wybierz pozycję **Zatwierdź wszystko** . Równoważne polecenie dla tej akcji to `git commit -a` .

Program Visual Studio ułatwia również przekazywanie i synchronizowanie za pomocą jednego kliknięcia przy użyciu skrótów **Zatwierdź wszystkie i wypchnij** i **Zatwierdź wszystkie skróty i Synchronizuj** . Po dwukrotnym kliknięciu dowolnego pliku w sekcjach **zmiany** i **przemieszczane zmiany** można zobaczyć porównanie liniowe z niezmodyfikowaną wersją pliku.

:::image type="content" source="media/git-file-version-compare.png" alt-text="Zrzut ekranu przedstawiający sekcję funkcje w wersji zapoznawczej okna dialogowego Opcje w programie Visual Studio ":::

> [!TIP]
> Możesz skojarzyć element roboczy usługi Azure DevOps z zatwierdzeniem, używając znaku "#", jeśli masz połączenie z repozytorium usługi Azure DevOps. Repozytorium usługi Azure DevOps można połączyć za pomocą **Team Explorer**  >  **zarządzania połączeniami** .

### <a name="select-an-existing-branch"></a>Wybierz istniejącą gałąź

Program Visual Studio Wyświetla bieżącą gałąź w selektorze w górnej części okna **zmiany systemu Git** .

:::image type="content" source="media/git-changes-current-branch-selector.png" alt-text="Zrzut ekranu przedstawiający sekcję funkcje w wersji zapoznawczej okna dialogowego Opcje w programie Visual Studio ":::

Bieżąca gałąź jest również dostępna na pasku stanu w prawym dolnym rogu środowiska IDE programu Visual Studio.

:::image type="content" source="media/git-changes-current-branch-status-bar.png" alt-text="Zrzut ekranu przedstawiający sekcję funkcje w wersji zapoznawczej okna dialogowego Opcje w programie Visual Studio ":::

Z obu lokalizacji można przełączać się między istniejącymi gałęziami.

### <a name="create-a-new-branch"></a>Utwórz nową gałąź

Można również utworzyć nową gałąź. Równoważne polecenie dla tej akcji to `git checkout <branchname>` .

Tworzenie nowej gałęzi jest tak proste jak wprowadzenie nazwy gałęzi i oparcie jej poza istniejącą gałęzią.

:::image type="content" source="media/git-changes-create-new-branch.png" alt-text="Zrzut ekranu przedstawiający sekcję funkcje w wersji zapoznawczej okna dialogowego Opcje w programie Visual Studio ":::

Możesz wybrać istniejącą gałąź lokalną lub zdalną jako podstawę. Pole wyboru **rozgałęzienie wyewidencjonowania** automatycznie przełącza użytkownika do nowo utworzonego rozgałęzienia. Równoważne polecenie dla tej akcji to `git checkout -b <new-branch><existing-branch>` .

## <a name="git-repository-window"></a>Okno repozytorium git

Program Visual Studio zawiera nowe okno **repozytorium git** , które jest skonsolidowanym widokiem wszystkich szczegółów w repozytorium, w tym wszystkich gałęzi, zdalnych i historii zatwierdzeń. Dostęp do tego okna można uzyskać bezpośrednio z poziomu **narzędzia Git** lub **widoku** na pasku menu lub na pasku stanu.

### <a name="manage-branches"></a>Zarządzanie gałęziami

Po wybraniu opcji **Zarządzaj gałęziami** w menu **git** zobaczysz widok drzewa gałęzie w oknie **repozytorium git** . W lewym okienku możesz użyć menu kontekstowego kliknij prawym przyciskiem myszy, aby wyewidencjonować gałęzie, utworzyć nowe gałęzie, scalić, zmienić bazę, selekcjonowanie i nie tylko. Po kliknięciu gałęzi można zobaczyć podgląd jej historii zatwierdzania w okienku po prawej stronie.

### <a name="incoming-and-outgoing-commits"></a>Zatwierdzenia przychodzące i wychodzące

Po pobraniu gałęzi okno zmiany w usłudze **git** ma wskaźnik pod listą rozwijaną gałąź, która wyświetla liczbę nieściągniętych zatwierdzeń z gałęzi zdalnej. Ten wskaźnik przedstawia również liczbę niewypychanych zatwierdzeń lokalnych.

:::image type="content" source="media/git-repo-drop-down-indicator.png" alt-text="Zrzut ekranu przedstawiający sekcję funkcje w wersji zapoznawczej okna dialogowego Opcje w programie Visual Studio ":::

Wskaźnik również działa jako link umożliwiający przejście do historii zatwierdzania tej gałęzi w oknie **repozytorium git** . W górnej części historii są teraz wyświetlane szczegóły tych zatwierdzeń przychodzących i wychodzących. W tym miejscu możesz również zdecydować się na ściąganie lub wypchnięcie zatwierdzeń.

:::image type="content" source="media/git-branch-commit-history.png" alt-text="Zrzut ekranu przedstawiający sekcję funkcje w wersji zapoznawczej okna dialogowego Opcje w programie Visual Studio ":::

#### <a name="commit-details"></a>Szczegóły zatwierdzenia

Po dwukrotnym kliknięciu **zatwierdzenia** program Visual Studio otwiera jego szczegóły w osobnym oknie narzędzi. W tym miejscu możesz cofnąć zatwierdzenie, zresetować zatwierdzenie, zmienić komunikat zatwierdzenia lub utworzyć tag w zatwierdzeniu. Po kliknięciu zmienionego pliku w zatwierdzeniu program Visual Studio otwiera widok **różnic** obok siebie zatwierdzania i jego elementu nadrzędnego.

:::image type="content" source="media/git-branch-commit-details.png" alt-text="Zrzut ekranu przedstawiający sekcję funkcje w wersji zapoznawczej okna dialogowego Opcje w programie Visual Studio ":::

## <a name="handle-merge-conflicts"></a>Obsługa konfliktów scalania

Konflikty mogą wystąpić podczas scalania, jeśli dwaj deweloperzy modyfikują te same wiersze w pliku, a Git nie jest automatycznie znana. Git zatrzymuje scalanie i informuje użytkownika o stanie konfliktu.

Program Visual Studio ułatwia identyfikowanie i rozwiązywanie konfliktów scalania. Pierwsze okno **repozytorium git** zawiera złoty pasek informacyjny w górnej części okna.

:::image type="content" source="media/git-merge-conflict-gold-bar.png" alt-text="Zrzut ekranu przedstawiający sekcję funkcje w wersji zapoznawczej okna dialogowego Opcje w programie Visual Studio " z niescalonymi plikami w oddzielnej sekcji poniżej.

:::image type="content" source="media/git-merge-progress-conflicts-message.png" alt-text="Zrzut ekranu przedstawiający sekcję funkcje w wersji zapoznawczej okna dialogowego Opcje w programie Visual Studio ":::

Jeśli jednak żadne z tych okien nie jest otwarte, a zamiast tego przejdziesz do pliku, który ma konflikty scalania, nie będzie konieczne wyszukiwanie następującego tekstu:

```bash
    <<<<<<< HEAD
    =======
    >>>>>>> main
```

Zamiast tego program Visual Studio Wyświetla złoty pasek informacyjny u góry strony, który wskazuje, że otwarty plik ma konflikty. Następnie możesz kliknąć link, aby otworzyć **Edytor scalania** .

:::image type="content" source="media/git-merge-conflict-gold-info-bar.png" alt-text="Zrzut ekranu przedstawiający sekcję funkcje w wersji zapoznawczej okna dialogowego Opcje w programie Visual Studio ":::

### <a name="the-merge-editor"></a>Edytor scalania

Edytor scalania w programie Visual Studio to trójwymiarowe narzędzie do scalania, które wyświetla zmiany przychodzące, bieżące zmiany i wynik scalania. Możesz użyć paska narzędzi na najwyższym poziomie **edytora scalania** , aby nawigować między konfliktami i automatycznie scalone różnice w pliku.

:::image type="content" source="media/git-merge-editor.png" alt-text="Zrzut ekranu przedstawiający sekcję funkcje w wersji zapoznawczej okna dialogowego Opcje w programie Visual Studio ":::

Można również użyć przełączników, aby pokazać/ukryć różnice, pokazać/ukryć różnice między wyrazami i dostosować układ. W górnej części każdej strony znajdują się pola wyboru, za pomocą których można przyjmować wszystkie zmiany z jednej strony. Aby wprowadzić indywidualne zmiany, można kliknąć pola wyboru po lewej stronie wierszy powodujących konflikty po obu stronach. Wreszcie po zakończeniu rozwiązywania konfliktów można wybrać przycisk **Akceptuj scalanie** w edytorze scalania. Następnie napiszesz komunikat dotyczący zatwierdzenia i zatwierdzisz zmiany, aby ukończyć rozwiązywanie.

## <a name="personalize-your-git-settings"></a>Personalizowanie ustawień usługi git

Aby spersonalizować i dostosować ustawienia Git na poziomie repozytorium, a także na poziomie globalnym, przejdź do pozycji **Git**  >  **Ustawienia** Git na pasku menu lub **Narzędzia**  >  **Opcje**  >  **kontroli źródła** na pasku menu. Następnie wybierz odpowiednie opcje.

:::image type="content" source="media/git-options-settings.png" alt-text="Zrzut ekranu przedstawiający sekcję funkcje w wersji zapoznawczej okna dialogowego Opcje w programie Visual Studio ":::

## <a name="whats-next"></a>Co dalej

Bądź na bieżąco; Ta strona zostanie zaktualizowana, ponieważ będziemy nadal udoskonalać nowe środowisko Git w programie Visual Studio 2019.

> [!IMPORTANT]
> Jeśli masz sugestię, daj nam znać! Doceniamy okazję do skontaktowania się z informacjami na temat decyzji projektowych za pośrednictwem portalu [**społeczności deweloperów**](https://aka.ms/vs-suggest) .

## <a name="see-also"></a>Zobacz też

- [Nowe wideo dotyczące środowiska git](https://channel9.msdn.com/Shows/Visual-Studio-Toolbox/The-New-Git-Experience) w witrynie Channel 9 i [YouTube](https://www.youtube.com/watch?v=ZiQ2LXtAJ6I&feature=youtu.be)
- [Atrakcyjne nowe aktualizacje środowiska Git w blogu programu Visual Studio](https://devblogs.microsoft.com/visualstudio/exciting-new-updates-to-the-git-experience-in-visual-studio/)
- [Ulepszone środowisko Git w blogu programu Visual Studio 2019](https://devblogs.microsoft.com/visualstudio/improved-git-experience-in-visual-studio-2019/)
- [Informacje o wersji programu Visual Studio 2019](/visualstudio/releases/2019/release-notes)
