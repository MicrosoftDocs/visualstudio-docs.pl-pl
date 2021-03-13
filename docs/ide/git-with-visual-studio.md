---
title: Środowisko Git w programie Visual Studio
titleSuffix: ''
description: Dowiedz się, w jaki sposób nowe zintegrowane środowisko Git w programie Visual Studio 2019 może pomóc w zwiększeniu produktywności.
ms.date: 01/15/2021
ms.topic: conceptual
ms.author: tglee
author: TerryGLee
ms.manager: jillfra
monikerRange: vs-2019
ms.openlocfilehash: 354be4d3e31ead2d77e62f61600c20c1774353cd
ms.sourcegitcommit: 99b66b0f4ced46ead0b2506a103f974f40cc0076
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2021
ms.locfileid: "103295785"
---
# <a name="git-experience-in-visual-studio"></a>Środowisko Git w programie Visual Studio

Git jest teraz domyślnym interfejsem kontroli wersji w programie Visual Studio 2019. Od [wersji 16,6](/visualstudio/releases/2019/release-notes-v16.6)pracowałem nad tworzeniem zestawu funkcji i iteracją na podstawie opinii użytkowników. Nowe środowisko git jest domyślnie włączone dla wszystkich użytkowników w [wersji 16,8](/visualstudio/releases/2019/release-notes/).

> [!TIP]
> Git to najczęściej używany nowoczesny system kontroli wersji, dlatego bez względu na to, czy jesteś specjalistą dla profesjonalistów, czy też wiesz, jak kod, program git może być bardzo przydatny dla użytkownika. Jeśli dopiero zaczynasz pracę z usługą git, https://git-scm.com/ Witryna sieci Web jest dobrym miejscem do uruchomienia. W tym miejscu znajdziesz arkusze Ściągawka, popularną książkę online i wideo z podstawowymi informacjami na temat usługi git.

## <a name="how-to-use-git-in-visual-studio"></a>Jak używać narzędzia Git w programie Visual Studio

Przeprowadzimy Cię przez proces używania nowego środowiska Git w programie Visual Studio 2019, ale jeśli chcesz najpierw skorzystać z krótkiego przewodnika, zapoznaj się z następującym wideo: <br><br>*Długość wideo: 5,27 minut*

> [!VIDEO https://www.youtube.com/embed/UHrAg3iKoe0]

Istnieją trzy sposoby, aby rozpocząć korzystanie z narzędzia Git z programem Visual Studio, aby zwiększyć produktywność:

- [Otwórz istniejące repozytorium git](#open-an-existing-local-repository). Jeśli Twój kod znajduje się już na Twojej maszynie, możesz otworzyć **go za pomocą polecenia**  >  **Otwórz**  >  **projekt/rozwiązanie** (lub **folder**), a program Visual Studio automatycznie wykrywa, czy ma zainicjowane repozytorium git.
- [Utwórz nowe repozytorium git](#create-a-new-git-repository). Jeśli kod nie jest skojarzony z usługą git, możesz utworzyć nowe repozytorium git.
- [Klonuj istniejące repozytorium git](#clone-an-existing-git-repository). Jeśli kod, nad którym chcesz korzystać, nie znajduje się na komputerze, możesz sklonować wszystkie istniejące repozytoria zdalne.

> [!NOTE]
> Począwszy od [wersji 16,8](/visualstudio/releases/2019/release-notes/), Visual Studio 2019 obejmuje w pełni zintegrowane środowisko usługi GitHub. Teraz możesz dodać konta usługi GitHub i GitHub przedsiębiorstwa do łańcucha kluczy. Będziesz w stanie dodawać i korzystać z nich tak samo jak w przypadku kont Microsoft, co oznacza, że będziesz mieć łatwiejszy czas uzyskiwania dostępu do zasobów usługi GitHub w programie Visual Studio. Aby uzyskać więcej informacji, zobacz temat [współpraca z kontami usługi GitHub na stronie programu Visual Studio](work-with-github-accounts.md) .

## <a name="create-a-new-git-repository"></a>Utwórz nowe repozytorium git

Jeśli kod nie jest skojarzony z usługą git, możesz zacząć od utworzenia nowego repozytorium git. W tym celu wybierz pozycję **git**  >  **Utwórz repozytorium git** na pasku menu. Następnie w oknie dialogowym **Tworzenie repozytorium git** wprowadź informacje.

:::image type="content" source="media/git-create-repository.png" alt-text="Okno dialogowe Tworzenie repozytorium Git w programie Visual Studio.":::

Okno dialogowe **Tworzenie repozytorium git** ułatwia wypychanie nowego repozytorium do usługi GitHub. Domyślnie nowe repozytorium jest prywatne, co oznacza, że jesteś jedynym, kto ma do niego dostęp. Jeśli wyłączysz to pole, repozytorium będzie publiczne, co oznacza, że każdy z nich może go wyświetlić.

> [!TIP]
> Bez względu na to, czy repozytorium jest publiczne, czy prywatne, najlepiej bezpieczniej utworzyć kopię zapasową kodu przechowywaną w serwisie GitHub, nawet jeśli nie pracujesz z zespołem. Zapewnia to również, że Twój kod jest dostępny niezależnie od używanego komputera.

Można utworzyć tylko lokalne repozytorium git przy użyciu opcji **tylko lokalna** . Możesz też połączyć repozytorium z dowolnym istniejącym pustym repozytorium zdalnym dla dowolnego innego dostawcy Git za pomocą istniejącej opcji **zdalnej** .

## <a name="clone-an-existing-git-repository"></a>Klonowanie istniejącego repozytorium git

Program Visual Studio zawiera proste środowisko klonowania. Jeśli znasz adres URL repozytorium, które chcesz sklonować, możesz wkleić adres URL w sekcji **Lokalizacja repozytorium** , a następnie wybrać lokalizację dysku, do której ma zostać sklonowany program Visual Studio.

:::image type="content" source="media/git-clone-repository.png" alt-text="Okno dialogowe klonowanie repozytorium Git w programie Visual Studio.":::

Jeśli nie znasz adresu URL repozytorium, program Visual Studio ułatwia przeglądanie i Klonowanie istniejącego repozytorium usługi GitHub lub Azure DevOps.

### <a name="open-an-existing-local-repository"></a>Otwórz istniejące repozytorium lokalne

Po sklonowaniu repozytorium lub utworzeniu go program Visual Studio wykrywa repozytorium git i dodaje je do listy **lokalnych repozytoriów** w menu git. W tym miejscu możesz szybko uzyskać dostęp do repozytoriów Git i przełączać się między nimi.

:::image type="content" source="media/git-local-repositories.png" alt-text="Opcja lokalnych repozytoriów z menu Git w programie Visual Studio ":::

## <a name="view-files-in-solution-explorer"></a>Wyświetl pliki w Eksplorator rozwiązań

Po sklonowaniu repozytorium lub otwarciu repozytorium lokalnego program Visual Studio przełącza użytkownika do tego kontekstu git przez zapisanie i zamknięcie wszelkich otwartych wcześniej rozwiązań i projektów. Eksplorator rozwiązań ładuje folder w katalogu głównym repozytorium git i skanuje drzewo katalogów dla wszystkich plików widoku. Obejmują one pliki takie jak CMakeLists.txt lub z rozszerzeniem. sln.

Program Visual Studio dostosowuje swój widok na podstawie tego, który plik widoku jest ładowany w Eksplorator rozwiązań:

- W przypadku klonowania repozytorium zawierającego pojedynczy plik. sln, Eksplorator rozwiązań bezpośrednio ładuje to rozwiązanie.
- Jeśli Eksplorator rozwiązań nie wykryje żadnych plików SLN w repozytorium, domyślnie wczytuje widok folderu.
- Jeśli repozytorium zawiera więcej niż jeden plik. sln, Eksplorator rozwiązań wyświetla listę dostępnych widoków do wyboru.

Można przełączać się między aktualnie otwartym widokiem a listą widoków przy użyciu przycisku **Przełącz widoki** na pasku narzędzi Eksplorator rozwiązań.

:::image type="content" source="media/git-solution-explorer-views.png" alt-text="Eksplorator rozwiązań z przyciskiem przełączania widoków wybranym w programie Visual Studio.":::

## <a name="git-changes-window"></a>Okno zmian git

Git śledzi zmiany plików w repozytorium podczas pracy i oddziela pliki w repozytorium do trzech kategorii. Te zmiany są równoważne z informacjami wyświetlanymi po wprowadzeniu `git status` polecenia w wierszu polecenia:

- **Pliki niezmodyfikowane**: te pliki nie zostały zmienione od czasu ostatniego zatwierdzenia.
- **Zmodyfikowane pliki**: te pliki mają zmiany od czasu ostatniego zatwierdzenia, ale jeszcze nie zostały przygotowane do następnego zatwierdzenia.
- **Pliki przemieszczane**: te pliki zawierają zmiany, które zostaną dodane do następnego zatwierdzenia.

Podczas pracy program Visual Studio śledzi zmiany plików w projekcie w sekcji **zmiany** w oknie zmiany w usłudze **git** .

:::image type="content" source="media/git-changes-window.png" alt-text="Okno zmiany w usłudze Git w programie Visual Studio.":::

Gdy wszystko będzie gotowe do przemieszczania zmian, kliknij **+** przycisk (plus) w każdym pliku, który chcesz przygotować, lub kliknij prawym przyciskiem myszy plik, a następnie wybierz pozycję **etap**. Możesz również przemieścić wszystkie zmodyfikowane pliki jednym kliknięciem, używając przycisku przemieszczenie wszystko **+** (plus) w górnej części sekcji **zmiany** .

Podczas przygotowywania zmiany program Visual Studio tworzy sekcję **przemieszczone zmiany** . Tylko zmiany w sekcji **przemieszczane zmiany** są dodawane do następnego zatwierdzenia, które można wykonać, wybierając pozycję **Zatwierdź przygotowane**. Równoważne polecenie dla tej akcji to `git commit -m "Your commit message"` . Zmiany mogą być również nieprzygotowane, klikając przycisk **–** (minus). Równoważne polecenie dla tej akcji polega `git reset <file_path>` na rozmieszczeniu pojedynczego pliku lub `git reset <directory_path>` rozmieszczeniu wszystkich plików w katalogu.

Możesz również zrezygnować z przygotowania zmodyfikowanych plików, pomijając obszar przejściowy. W takim przypadku program Visual Studio pozwala na zatwierdzanie zmian bezpośrednio bez konieczności ich przemieszczania. Po prostu wprowadź wiadomość dotyczącą zatwierdzenia, a następnie wybierz pozycję **Zatwierdź wszystko**. Równoważne polecenie dla tej akcji to `git commit -a` .

Program Visual Studio ułatwia również przekazywanie i synchronizowanie za pomocą jednego kliknięcia przy użyciu skrótów **Zatwierdź wszystkie i wypchnij** i **Zatwierdź wszystkie skróty i Synchronizuj** . Po dwukrotnym kliknięciu dowolnego pliku w sekcjach **zmiany** i **przemieszczane zmiany** można zobaczyć porównanie liniowe z niezmodyfikowaną wersją pliku.

:::image type="content" source="media/git-file-version-compare.png" alt-text="Porównanie liniowe w wersji plików w programie Visual Studio ":::

> [!TIP]
> Możesz skojarzyć element roboczy usługi Azure DevOps z zatwierdzeniem za pomocą znaku "#", jeśli masz połączenie z repozytorium usługi Azure DevOps. Repozytorium usługi Azure DevOps można połączyć za pomocą **Team Explorer**  >  **zarządzania połączeniami**.

### <a name="select-an-existing-branch"></a>Wybierz istniejącą gałąź

Program Visual Studio Wyświetla bieżącą gałąź w selektorze w górnej części okna **zmiany systemu Git** .

:::image type="content" source="media/git-changes-current-branch-selector.png" alt-text="Bieżące gałęzie, które można wyświetlić za pomocą selektora w górnej części selektora zmian Git w programie Visual Studio ":::

Bieżąca gałąź jest również dostępna na pasku stanu w prawym dolnym rogu środowiska IDE programu Visual Studio.

:::image type="content" source="media/git-changes-current-branch-status-bar.png" alt-text="Bieżące gałęzie, które można wyświetlić przy użyciu paska stanu w prawym dolnym rogu środowiska IDE programu Visual Studio ":::

Z obu lokalizacji można przełączać się między istniejącymi gałęziami.

### <a name="create-a-new-branch"></a>Utwórz nową gałąź

Można również utworzyć nową gałąź. Równoważne polecenie dla tej akcji to `git checkout -b <branchname>` .

Tworzenie nowej gałęzi jest tak proste jak wprowadzenie nazwy gałęzi i oparcie jej poza istniejącą gałęzią.

:::image type="content" source="media/git-changes-create-new-branch.png" alt-text="Okno dialogowe Tworzenie nowej gałęzi w programie Visual Studio ":::

Możesz wybrać istniejącą gałąź lokalną lub zdalną jako podstawę. Pole wyboru **rozgałęzienie wyewidencjonowania** automatycznie przełącza użytkownika do nowo utworzonego rozgałęzienia. Równoważne polecenie dla tej akcji to `git checkout -b <new-branch><existing-branch>` .

## <a name="git-repository-window"></a>Okno repozytorium git

Program Visual Studio zawiera nowe okno **repozytorium git** , które jest skonsolidowanym widokiem wszystkich szczegółów w repozytorium, w tym wszystkich gałęzi, zdalnych i historii zatwierdzeń. Dostęp do tego okna można uzyskać bezpośrednio z poziomu **narzędzia Git** lub **widoku** na pasku menu lub na pasku stanu.

### <a name="manage-branches"></a>Zarządzanie gałęziami

Po wybraniu opcji **Zarządzaj gałęziami** w menu **git** zobaczysz widok drzewa gałęzie w oknie **repozytorium git** . W lewym okienku możesz użyć menu kontekstowego kliknij prawym przyciskiem myszy, aby wyewidencjonować gałęzie, utworzyć nowe gałęzie, scalić, zmienić bazę, selekcjonowanie i nie tylko. Po kliknięciu gałęzi można zobaczyć podgląd jej historii zatwierdzania w okienku po prawej stronie.

### <a name="incoming-and-outgoing-commits"></a>Zatwierdzenia przychodzące i wychodzące

Po pobraniu gałęzi okno zmiany w usłudze **git** ma wskaźnik pod listą rozwijaną gałąź, która wyświetla liczbę nieściągniętych zatwierdzeń z gałęzi zdalnej. Ten wskaźnik przedstawia również liczbę niewypychanych zatwierdzeń lokalnych.

:::image type="content" source="media/git-repo-drop-down-indicator.png" alt-text="Okno zmiany git, które pokazuje element interfejsu użytkownika listy rozwijanej wskaźnika w programie Visual Studio ":::

Wskaźnik również działa jako link umożliwiający przejście do historii zatwierdzania tej gałęzi w oknie **repozytorium git** . W górnej części historii są teraz wyświetlane szczegóły tych zatwierdzeń przychodzących i wychodzących. W tym miejscu możesz również zdecydować się na ściąganie lub wypchnięcie zatwierdzeń.

:::image type="content" source="media/git-branch-commit-history.png" alt-text="Okno repozytorium git, które pokazuje historię zatwierdzania gałęzi w programie Visual Studio ":::

#### <a name="commit-details"></a>Szczegóły zatwierdzenia

Po dwukrotnym kliknięciu **zatwierdzenia** program Visual Studio otwiera jego szczegóły w osobnym oknie narzędzi. W tym miejscu możesz cofnąć zatwierdzenie, zresetować zatwierdzenie, zmienić komunikat zatwierdzenia lub utworzyć tag w zatwierdzeniu. Po kliknięciu zmienionego pliku w zatwierdzeniu program Visual Studio otwiera widok **różnic** obok siebie zatwierdzania i jego elementu nadrzędnego.

:::image type="content" source="media/git-branch-commit-details.png" alt-text="Okno dialogowe Szczegóły zatwierdzania w programie Visual Studio ":::

## <a name="handle-merge-conflicts"></a>Obsługa konfliktów scalania

Konflikty mogą wystąpić podczas scalania, jeśli dwaj deweloperzy modyfikują te same wiersze w pliku, a Git nie jest automatycznie znana. Git zatrzymuje scalanie i informuje użytkownika o stanie konfliktu.

Program Visual Studio ułatwia identyfikowanie i rozwiązywanie konfliktów scalania. Pierwsze okno **repozytorium git** zawiera złoty pasek informacyjny w górnej części okna.

:::image type="content" source="media/git-merge-conflict-gold-bar.png" alt-text="Komunikat &quot;scalanie zostało ukończone z konfliktami&quot; w programie Visual Studio ":::

W oknie zmiany w usłudze **git** zostanie również wyświetlony komunikat "*scalanie w toku z konfliktami*" z niescalonymi plikami w oddzielnej sekcji poniżej.

:::image type="content" source="media/git-merge-progress-conflicts-message.png" alt-text="Komunikat &quot;scalanie w toku ze konfliktami&quot; w programie Visual Studio ":::

Jeśli jednak żadne z tych okien nie jest otwarte, a zamiast tego przejdziesz do pliku, który ma konflikty scalania, nie będzie konieczne wyszukiwanie następującego tekstu:

```bash
    <<<<<<< HEAD
    =======
    >>>>>>> main
```

Zamiast tego program Visual Studio Wyświetla złoty pasek informacyjny u góry strony, który wskazuje, że otwarty plik ma konflikty. Następnie możesz kliknąć link, aby otworzyć **Edytor scalania**.

:::image type="content" source="media/git-merge-conflict-gold-info-bar.png" alt-text="Zrzut ekranu przedstawiający komunikat &quot;plik zawiera konflikty scalania&quot; w programie Visual Studio ":::

### <a name="the-merge-editor"></a>Edytor scalania

Edytor scalania w programie Visual Studio to trójwymiarowe narzędzie do scalania, które wyświetla zmiany przychodzące, bieżące zmiany i wynik scalania. Możesz użyć paska narzędzi na najwyższym poziomie **edytora scalania** , aby nawigować między konfliktami i automatycznie scalone różnice w pliku.

:::image type="content" source="media/git-merge-editor.png" alt-text="Edytor scalania w programie Visual Studio ":::

Można również użyć przełączników, aby pokazać/ukryć różnice, pokazać/ukryć różnice między wyrazami i dostosować układ. W górnej części każdej strony znajdują się pola wyboru, za pomocą których można przyjmować wszystkie zmiany z jednej strony. Aby wprowadzić indywidualne zmiany, można kliknąć pola wyboru po lewej stronie wierszy powodujących konflikty po obu stronach. Wreszcie po zakończeniu rozwiązywania konfliktów można wybrać przycisk **Akceptuj scalanie** w edytorze scalania. Następnie napiszesz komunikat dotyczący zatwierdzenia i zatwierdzisz zmiany, aby ukończyć rozwiązywanie.

## <a name="personalize-your-git-settings"></a>Personalizowanie ustawień usługi git

Aby spersonalizować i dostosować ustawienia Git na poziomie repozytorium, a także na poziomie globalnym, przejdź do pozycji   >  **Ustawienia** Git na pasku menu lub **Narzędzia**  >  **Opcje**  >  **kontroli źródła** na pasku menu. Następnie wybierz odpowiednie opcje.

:::image type="content" source="media/git-options-settings.png" alt-text="Okno dialogowe Opcje, w którym można wybrać ustawienia personalizacji i dostosowywania w środowisku IDE programu Visual Studio ":::

## <a name="how-to-use-the-full-team-explorer-experience-in-visual-studio"></a>Jak korzystać z pełnego środowiska Team Explorer w programie Visual Studio

Nowe środowisko git to domyślny system kontroli wersji w programie Visual Studio 2019 od [wersji 16,8](/visualstudio/releases/2019/release-notes/) lub nowszej. Jeśli jednak chcesz ją wyłączyć, możesz to zrobić. Przejdź do pozycji **Narzędzia**  >  **Opcje**  >  **środowiska**  >  **Podgląd funkcje** , a następnie Przełącz nowe pole wyboru środowisko **użytkownika systemu Git** , które spowoduje przełączenie się z powrotem do Team Explorer dla usługi git.

:::image type="content" source="media/git-opt-new-user-experience.png" alt-text="Sekcja funkcje w wersji zapoznawczej okna dialogowego Opcje w programie Visual Studio ":::

## <a name="whats-next"></a>Co dalej

Mimo że nowe środowisko git jest teraz domyślnie włączone w programie Visual Studio 2019 w [wersji 16,8](/visualstudio/releases/2019/release-notes/), będziemy nadal dodawać nowe funkcje, aby usprawnić środowisko pracy. Jeśli chcesz wyewidencjonować nowe aktualizacje środowiska Git w wersji zapoznawczej, możesz je pobrać i zainstalować ze strony [wersji zapoznawczej programu Visual Studio](https://aka.ms/vspreview/) .

> [!IMPORTANT]
> Jeśli masz sugestię, daj nam znać! Doceniamy okazję do skontaktowania się z informacjami na temat decyzji projektowych za pośrednictwem portalu [**społeczności deweloperów**](https://aka.ms/vs-suggest) .

## <a name="see-also"></a>Zobacz też

- [Ogłaszanie wersji środowiska Git w blogu programu Visual Studio](https://devblogs.microsoft.com/visualstudio/announcing-the-release-of-the-git-experience-in-visual-studio/)
- [Uruchomienie nowego środowiska git](https://www.youtube.com/watch?v=UHrAg3iKoe0&t) w serwisie YouTube
- [Seria Visual Studio Toolbox prezentuje: nowe wideo dotyczące środowiska git](https://channel9.msdn.com/Shows/Visual-Studio-Toolbox/The-New-Git-Experience) w witrynie Channel 9 i w serwisie [YouTube](https://www.youtube.com/watch?v=ZiQ2LXtAJ6I&feature=youtu.be)
- [Atrakcyjne nowe aktualizacje środowiska Git w blogu programu Visual Studio](https://devblogs.microsoft.com/visualstudio/exciting-new-updates-to-the-git-experience-in-visual-studio/)
- [Ulepszone środowisko Git w blogu programu Visual Studio 2019](https://devblogs.microsoft.com/visualstudio/improved-git-experience-in-visual-studio-2019/)
- [Praca z kontami usługi GitHub w programie Visual Studio](work-with-github-accounts.md)
- [Informacje o wersji programu Visual Studio 2019](/visualstudio/releases/2019/release-notes)
