---
title: Środowisko usługi Git w Visual Studio 2019 r.
titleSuffix: ''
description: Dowiedz się, jak nowe zintegrowane środowisko git w programie Visual Studio 2019 może pomóc w produktywności.
ms.date: 04/01/2021
ms.topic: overview
ms.author: tglee
author: TerryGLee
ms.manager: jillfra
ms.openlocfilehash: 96018a203a6a0e5d404a818817ea4e9fb7e18551
ms.sourcegitcommit: 5fb684ff8729eb118aa91ce9f049c79eeb9747b1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2021
ms.locfileid: "107917922"
---
# <a name="git-experience-in-visual-studio"></a>Środowisko git w usłudze Visual Studio

Usługa Git jest teraz domyślnym środowiskom kontroli wersji w Visual Studio 2019 r. Od [wersji 16.6](/visualstudio/releases/2019/release-notes-v16.6)pracowaliśmy nad budowania zestawu funkcji i iterowania po nim na podstawie opinii użytkowników. Nowe środowisko git jest domyślnie włączone dla wszystkich użytkowników w wersji [16.8.](/visualstudio/releases/2019/release-notes/)

> [!TIP]
> Usługa Git jest najczęściej używanym nowoczesnym systemem kontroli wersji, więc niezależnie od tego, czy jesteś profesjonalnym deweloperem, czy też wiesz, jak kodować, usługa Git może być dla Ciebie bardzo przydatna. Jeśli jesteś nowym użytkownikom usługi Git, witryna https://git-scm.com/ internetowa jest dobrym miejscem do rozpoczęcia pracy. Znajdziesz tam ściągawki, popularną książkę online i klipy wideo z podstaw usługi Git.

## <a name="how-to-use-git-in-visual-studio"></a>Jak używać usługi Git w programie Visual Studio

Dowiesz się, jak korzystać z nowego doświadczenia usługi Git w programie Visual Studio 2019, ale jeśli chcesz najpierw skorzystać z krótkiego przewodnika, zapoznaj się z następującym filmem wideo: <br><br>*Długość wideo: 5,27 min*

> [!VIDEO https://www.youtube.com/embed/UHrAg3iKoe0]

Istnieją trzy sposoby rozpoczęcia korzystania z usługi Git za Visual Studio, aby pracować wydajniej:

- [Otwórz istniejące repozytorium Git.](#open-an-existing-local-repository) Jeśli kod znajduje się już na komputerze, możesz otworzyć go za pomocą polecenia **Otwórz**  >    >  **projekt/rozwiązanie** w pliku (lub **folderu)** i Visual Studio automatycznie wykrywa, czy ma ono zainicjowane repozytorium Git.
- [Utwórz nowe repozytorium Git.](#create-a-new-git-repository) Jeśli twój kod nie jest skojarzony z repozytorium Git, możesz utworzyć nowe repozytorium Git.
- [Sklonuj istniejące repozytorium Git.](#clone-an-existing-git-repository) Jeśli kod, nad który chcesz pracować, nie znajduje się na Twojej maszynie, możesz sklonować dowolne istniejące repozytoria zdalne.

> [!NOTE]
> Począwszy od [wersji 16.8,](/visualstudio/releases/2019/release-notes/)Visual Studio 2019 r. obejmuje w pełni zintegrowane środowisko konta usługi GitHub. Teraz można dodawać konta usługi GitHub i GitHub Enterprise do swojego klucza. Będziesz mieć możliwość ich dodawania i wykorzystania tak samo jak w przypadku kont Microsoft, co oznacza, że będziesz mieć łatwiejszy czas na dostęp do zasobów usługi GitHub w różnych Visual Studio. Aby uzyskać więcej informacji, zobacz stronę [Praca z kontami usługi GitHub Visual Studio](../ide/work-with-github-accounts.md) aplikacji.

## <a name="create-a-new-git-repository"></a>Tworzenie nowego repozytorium Git

Jeśli kod nie jest skojarzony z repozytorium Git, możesz rozpocząć od utworzenia nowego repozytorium Git. W tym celu wybierz pozycję **Git**  >  **Create Git Repository (Utwórz repozytorium Git)** na pasku menu. Następnie w **oknie dialogowym Tworzenie repozytorium Git** wprowadź informacje.

:::image type="content" source="media/git-create-repository.png" alt-text="Okno dialogowe Tworzenie repozytorium Git w Visual Studio.":::

Okno **dialogowe Tworzenie repozytorium Git** ułatwia wypychanie nowego repozytorium do usługi GitHub. Domyślnie nowe repozytorium jest prywatne, co oznacza, że jesteś jedynym, który może uzyskać do niego dostęp. Jeśli to pole nie zostanie zaznaczone, repozytorium będzie publiczne, co oznacza, że każda osoba w witrynie GitHub może je wyświetlić.

> [!TIP]
> Niezależnie od tego, czy repozytorium jest publiczne, czy prywatne, najlepiej jest mieć zdalną kopię zapasową kodu przechowywaną bezpiecznie w usłudze GitHub, nawet jeśli nie pracujesz z zespołem. Dzięki temu kod będzie dostępny niezależnie od tego, jakiego komputera używasz.

Możesz utworzyć repozytorium Git tylko lokalne przy użyciu opcji **Tylko** lokalne. Możesz też połączyć projekt lokalny z istniejącym pustym repozytorium zdalnym w usłudze Azure DevOps lub innym dostawcą usługi Git przy użyciu **opcji Istniejące zdalne.**

## <a name="clone-an-existing-git-repository"></a>Klonowanie istniejącego repozytorium Git

Visual Studio obejmuje proste środowisko klonowania. Jeśli znasz adres URL repozytorium, które chcesz sklonować, możesz  wkleić adres URL w sekcji Lokalizacja repozytorium, a następnie wybrać lokalizację dysku, do Visual Studio chcesz sklonować.

:::image type="content" source="media/git-clone-repository.png" alt-text="Okno dialogowe Klonowanie repozytorium Git w Visual Studio.":::

Jeśli nie znasz adresu URL repozytorium, usługa Visual Studio ułatwia przeglądanie, a następnie klonowanie istniejącego repozytorium GitHub lub Azure DevOps repozytorium.

### <a name="open-an-existing-local-repository"></a>Otwieranie istniejącego repozytorium lokalnego

Po sklonowanym lub utworzonym repozytorium usługa Visual Studio wykryje repozytorium Git i doda  je do listy repozytoriów lokalnych w menu Git. W tym miejscu możesz szybko uzyskać dostęp do repozytoriów Git i przełączać się między nimi.

:::image type="content" source="media/git-local-repositories.png" alt-text="Opcja Repozytoria lokalne z menu Git w Visual Studio ":::

## <a name="view-files-in-solution-explorer"></a>Wyświetlanie plików w Eksplorator rozwiązań

Podczas klonowania repozytorium lub otwierania repozytorium lokalnego program Visual Studio użytkownika do tego kontekstu usługi Git, zapisując i zamykając wszystkie wcześniej otwarte rozwiązania i projekty. Eksplorator rozwiązań folder zostanie załadowany w katalogu głównym repozytorium Git i przeskanuje drzewo katalogów pod poszukiwaniu dowolnych plików widoku. Obejmują one pliki, takie CMakeLists.txt lub pliki z rozszerzeniem SLN.

Visual Studio dostosowuje widok na podstawie tego, który plik widoku ładujesz w Eksplorator rozwiązań:

- W przypadku sklonowania repozytorium zawierającego pojedynczy plik sln Eksplorator rozwiązań to rozwiązanie zostanie załadowane bezpośrednio.
- Jeśli Eksplorator rozwiązań nie wykryje żadnych plików sln w repozytorium, domyślnie ładuje widok folderu.
- Jeśli repozytorium zawiera więcej niż jeden plik sln, Eksplorator rozwiązań zostanie wyświetlona lista dostępnych widoków do wyboru.

Możesz przełączać się między aktualnie otwartym widokiem a listą widoków przy użyciu przycisku **Przełącz** widoki na pasku Eksplorator rozwiązań narzędzi.

:::image type="content" source="media/git-solution-explorer-views.png" alt-text="Eksplorator rozwiązań przy użyciu przycisku Przełącz widoki wybranego w Visual Studio.":::

## <a name="git-changes-window"></a>Okno Git Changes (Zmiany usługi Git)

Usługa Git śledzi zmiany plików w repozytorium podczas pracy i dzieli pliki w repozytorium na trzy kategorie. Te zmiany są równoważne tym, co zobaczysz po wprowadzeniu `git status` polecenia w wierszu polecenia:

- **Niezmodyfikowane pliki:** te pliki nie uległy zmianie od czasu ostatniego zatwierdzenia.
- **Zmodyfikowane pliki:** te pliki mają zmiany od czasu ostatniego zatwierdzenia, ale nie zostały jeszcze przesłoone do następnego zatwierdzenia.
- **Pliki etapowe:** te pliki mają zmiany, które zostaną dodane do następnego zatwierdzenia.

Podczas pracy program Visual Studio śledzić zmiany pliku w projekcie w sekcji **Zmiany** w **oknie Git Changes.**

:::image type="content" source="media/git-changes-window.png" alt-text="Okno Git Changes w Visual Studio.":::

Gdy wszystko będzie gotowe do przygotowanych zmian, kliknij przycisk (plus) w każdym pliku, który chcesz przygotować, lub kliknij prawym przyciskiem myszy plik, **+** a następnie wybierz pozycję **Przygotuj**. Możesz również jednym kliknięciem przekrój wszystkie zmodyfikowane pliki, używając przycisku stage all (plus) w górnej części **+** **sekcji** Zmiany.

Podczas etapu zmiany program Visual Studio **sekcję Zmiany** etapowe. Tylko zmiany w sekcji **Zmiany etapowe** są dodawane do następnego zatwierdzenia, co można zrobić, wybierając pozycję **Zat zatwierdzanie przeetapiowane.** Równoważnym poleceniem dla tej akcji jest `git commit -m "Your commit message"` . Zmiany można również nieprzygotowyć, klikając przycisk **–** (minus). Równoważnym poleceniem dla tej akcji jest cofkanie pełnego pliku lub cofnieniesz wszystkie pliki `git reset <file_path>` `git reset <directory_path>` w katalogu.

Możesz również zmodyfikować zmodyfikowane pliki, pomijając obszar przejściowy. W takim przypadku Visual Studio zatwierdzanie zmian bezpośrednio bez konieczności ich etapu. Po prostu wprowadź komunikat o zatwierdzeniu, a następnie wybierz **pozycję Zat zatwierdzeniu wszystkiego.** Równoważnym poleceniem dla tej akcji jest `git commit -a` .

Visual Studio także ułatwia zatwierdzanie i synchronizowanie jednym kliknięciem przy użyciu skrótów **Zateń** wszystko i Wypchń i Zateń **wszystko i Synchronizuj.** Po dwukrotnym kliknięciu dowolnego pliku w  sekcjach **Zmiany** i Zmiany etapowe można wyświetlić porównanie wiersz po wierszu ze niezmodyfikowana wersją pliku.

:::image type="content" source="media/git-file-version-compare.png" alt-text="Porównanie wiersz po wierszu wersji plików w Visual Studio ":::

> [!TIP]
> Możesz skojarzyć Azure DevOps pracy z zatwierdzeniem przy użyciu znaku "#", jeśli masz połączenie z Azure DevOps repozytorium. Możesz połączyć repozytorium Azure DevOps za pomocą Team Explorer  >  **Zarządzaj połączeniami.**

### <a name="select-an-existing-branch"></a>Wybierz istniejącą gałąź

Visual Studio gałąź bieżąca jest wyświetlana w selektorze w górnej części okna **Git Changes.**

:::image type="content" source="media/git-changes-current-branch-selector.png" alt-text="Bieżące gałęzie, które można wyświetlić za pomocą selektora w górnej części selektora Git Changes w Visual Studio ":::

Bieżąca gałąź jest również dostępna na pasku stanu w prawym dolnym rogu Visual Studio IDE.

:::image type="content" source="media/git-changes-current-branch-status-bar.png" alt-text="Bieżące gałęzie, które można wyświetlić przy użyciu paska stanu w prawym dolnym rogu w Visual Studio IDE ":::

Z obu lokalizacji można przełączać się między istniejącymi gałęziami.

### <a name="create-a-new-branch"></a>Tworzenie nowej gałęzi

Możesz również utworzyć nową gałąź. Równoważnym poleceniem dla tej akcji jest `git checkout -b <branchname>` .

Tworzenie nowej gałęzi jest tak proste, jak wprowadzenie nazwy gałęzi i oparcie jej na istniejącej gałęzi.

:::image type="content" source="media/git-changes-create-new-branch.png" alt-text="Okno dialogowe Tworzenie nowej gałęzi w Visual Studio ":::

Jako bazę można wybrać istniejącą gałąź lokalną lub zdalną. Pole **wyboru Gałąź** wyewidencjonowania spowoduje automatyczne przełączenie na nowo utworzoną gałąź. Równoważnym poleceniem dla tej akcji jest `git checkout -b <new-branch><existing-branch>` .

## <a name="git-repository-window"></a>Okno Repozytorium Git

Visual Studio nowe okno Repozytorium **Git,** które jest skonsolidowanym widokiem wszystkich szczegółów w repozytorium, w tym wszystkich gałęzi, zdalnych i historii zatwierdzeń. Dostęp do tego okna można uzyskać bezpośrednio z narzędzia **Git** lub **widoku** na pasku menu lub z paska stanu.

### <a name="manage-branches"></a>Zarządzanie gałęziami

Po wybraniu pozycji **Zarządzaj gałęziami** w menu **Git** zobaczysz widok drzewa gałęzi w oknie **Repozytorium Git.** W okienku po lewej stronie możesz użyć menu kontekstowego dostępnego po kliknięciu prawym przyciskiem myszy, aby wyewidencjonować gałęzie, utworzyć nowe gałęzie, scalić, ponownie utworzyć bazę, wybrać opcję wyboru głównego i nie tylko. Po kliknięciu gałęzi w okienku po prawej stronie zostanie wyświetlony podgląd jej historii zatwierdzń.

### <a name="incoming-and-outgoing-commits"></a>Zatwierdzenia przychodzące i wychodzące

Po pobraniu gałęzi w oknie Zmiany usługi **Git** znajduje się wskaźnik z listy rozwijanej gałęzi, który wyświetla liczbę niezapełnionych zatwierdzeń z gałęzi zdalnej. Ten wskaźnik pokazuje również liczbę niezatwierdzeń lokalnych bez zasad.

:::image type="content" source="media/git-repo-drop-down-indicator.png" alt-text="Okno Git Changes (Zmiany usługi Git) z elementem interfejsu użytkownika listy rozwijanej wskaźników w Visual Studio ":::

Wskaźnik działa również jako link do historii zatwierdzania tej gałęzi w oknie **Repozytorium Git.** W górnej części historii są teraz wyświetlane szczegóły tych przychodzących i wychodzących zatwierdzeń. W tym miejscu możesz również zdecydować się na ściągnięcie lub wypchnięcie zatwierdzeń.

:::image type="content" source="media/git-branch-commit-history.png" alt-text="Okno Repozytorium Git, w których jest pokazana historia zatwierdzania gałęzi w Visual Studio ":::

#### <a name="commit-details"></a>Szczegóły zatwierdzenia

Dwukrotne kliknięcie polecenia **Commit (Zatwierdzenie)** Visual Studio jego szczegółów w osobnym oknie narzędzi. W tym miejscu możesz cofnąć zatwierdzenie, zresetować zatwierdzenie, zmienić komunikat zatwierdzenia lub utworzyć tag w zatwierdzeniu. Po kliknięciu zmienionego pliku w zatwierdzeniu program Visual Studio widok  różnic obok siebie zatwierdzenia i jego elementu nadrzędnego.

:::image type="content" source="media/git-branch-commit-details.png" alt-text="Okno dialogowe Szczegóły zatwierdzenia w Visual Studio ":::

## <a name="handle-merge-conflicts"></a>Obsługa konfliktów scalania

Konflikty mogą wystąpić podczas scalania, jeśli dwaj deweloperzy zmodyfikują te same wiersze w pliku, a usługa Git nie wie automatycznie, które z nich jest poprawne. Usługa Git zatrzymuje scalanie i informuje o tym, że występuje konflikt.

Visual Studio ułatwia identyfikowanie i rozwiązywanie konfliktu scalania. Najpierw w **oknie Repozytorium Git** w górnej części okna jest wyświetlany złoty pasek informacyjny.

:::image type="content" source="media/git-merge-conflict-gold-bar.png" alt-text="Komunikat &quot;Scalanie ukończone z konfliktami&quot; w Visual Studio ":::

W **oknie Git** Changes(Zmiany git) jest również wyświetlany komunikat "Scalanie jest w toku z konfliktami", a nieschemane pliki znajdują się w oddzielnej sekcji poniżej.

:::image type="content" source="media/git-merge-progress-conflicts-message.png" alt-text="Komunikat &quot;Scalanie w toku z konfliktami&quot; w Visual Studio ":::

Jeśli jednak nie masz otwartego okna i zamiast tego przejdź do pliku, który ma konflikty scalania, nie musisz wyszukiwać następującego tekstu:

```bash
    <<<<<<< HEAD
    =======
    >>>>>>> main
```

Zamiast tego Visual Studio w górnej części strony zostanie wyświetlony złoty pasek informacji wskazujący, że otwarty plik zawiera konflikty. Następnie możesz kliknąć link, aby otworzyć Edytor **scalania**.

:::image type="content" source="media/git-merge-conflict-gold-info-bar.png" alt-text="Zrzut ekranu przedstawiający komunikat &quot;Plik zawiera konflikty scalania&quot; w Visual Studio ":::

### <a name="the-merge-editor"></a>Edytor scalania

Edytor scalania w Visual Studio to trzykierunkowe narzędzie scalania, które wyświetla przychodzące zmiany, bieżące zmiany i wynik scalania. Paska narzędzi na najwyższym poziomie edytora  scalania można użyć do nawigowania między konfliktami i różnicami w pliku automatycznie scalanych.

:::image type="content" source="media/git-merge-editor.png" alt-text="Edytor scalania w Visual Studio ":::

Przełączników można również używać do pokazywania/ukrywania różnic, pokazywania/ukrywania różnic między wyrazami oraz dostosowywania układu. W górnej części każdej strony znajdują się pola wyboru, których można użyć do podjęcia wszystkich zmian z jednej lub drugiej strony. Aby jednak wprowadzić poszczególne zmiany, możesz kliknąć pola wyboru z lewej strony wierszy powodujące konflikt po obu stronach. Na koniec po zakończeniu rozwiązywania konfliktów możesz wybrać przycisk **Zaakceptuj** scalanie w Edytorze scalania. Następnie napiszesz komunikat zatwierdzenia i zatwierdzisz zmiany, aby ukończyć rozwiązanie.

## <a name="personalize-your-git-settings"></a>Personalizowanie ustawień usługi Git

Aby spersonalizować i dostosować ustawienia usługi Git na poziomie repozytorium, a także na poziomie globalnym, przejdź do pozycji **Ustawienia usługi Git** na pasku menu lub do pozycji Narzędzia Opcje Kontrola źródła na pasku  >     >    >   menu. Następnie wybierz opcje, które chcesz.

:::image type="content" source="media/git-options-settings.png" alt-text="Opcje okno dialogowe, w którym można wybrać ustawienia personalizacji i dostosowywania w Visual Studio IDE ":::

## <a name="how-to-use-the-full-team-explorer-experience-in-visual-studio"></a>Jak korzystać z pełnego Team Explorer na Visual Studio

Nowe środowisko Git to domyślny system kontroli wersji w wersji Visual Studio 2019 od [wersji 16.8.](/visualstudio/releases/2019/release-notes/) Jeśli jednak chcesz ją wyłączyć, możesz to zrobić. Przejdź do **opcji Narzędzia** Funkcje środowiska w wersji zapoznawczej, a następnie przełącz pole wyboru Nowe środowisko użytkownika usługi Git, co spowoduje powrót do  >    >    >   Team Explorer dla usługi Git. 

:::image type="content" source="media/git-opt-new-user-experience.png" alt-text="Sekcja Funkcje w wersji zapoznawczej okna dialogowego Opcje w Visual Studio ":::

## <a name="whats-next"></a>Co dalej

Nowe środowisko usługi Git jest teraz domyślnie włączone w wersji [16.8](/visualstudio/releases/2019/release-notes/)programu Visual Studio 2019, ale w celu ulepszania tego doświadczenia nadal dodajemy nowe funkcje. Jeśli chcesz sprawdzić nowe aktualizacje usługi Git w wersji zapoznawczej, możesz pobrać i zainstalować je ze [strony Visual Studio Preview](https://aka.ms/vspreview/) git.

> [!IMPORTANT]
> Jeśli masz dla nas sugestię, daj nam znać! Doceniamy możliwość kontaktowania się z Tobem w sprawie decyzji projektowych za [**pośrednictwem Developer Community**](https://aka.ms/vs-suggest) portal.

## <a name="see-also"></a>Zobacz też

- [Rozpocznij z narzędziami Git i gitHub](/learn/modules/visual-studio-github-push/) w Visual Studio samouczku Microsoft Learn
- [Wprowadzenie do usługi Git w Visual Studio](https://www.youtube.com/watch?v=GCZ9x3yqkyc) wideo w serwisie YouTube
- [Announcing the Release of the Git Experience in Visual Studio](https://devblogs.microsoft.com/visualstudio/announcing-the-release-of-the-git-experience-in-visual-studio/) wpis w blogu
- [Wprowadzenie nowego wideo na temat usługi Git w](https://www.youtube.com/watch?v=UHrAg3iKoe0&t) serwisie YouTube
- [Seria Visual Studio Toolbox przedstawia: nowe](https://channel9.msdn.com/Shows/Visual-Studio-Toolbox/The-New-Git-Experience) wideo dotyczące usługi Git w witrynie Channel 9 i [serwisie YouTube](https://www.youtube.com/watch?v=ZiQ2LXtAJ6I&feature=youtu.be)
- [Atrakcyjne nowe aktualizacje funkcji Git w Visual Studio](https://devblogs.microsoft.com/visualstudio/exciting-new-updates-to-the-git-experience-in-visual-studio/) wpisie w blogu
- [Ulepszony wpis w blogu git experience in Visual Studio 2019 (Ulepszone środowisko](https://devblogs.microsoft.com/visualstudio/improved-git-experience-in-visual-studio-2019/) git w programie Visual Studio 2019)
- [Praca z kontami usługi GitHub w programie Visual Studio](../ide/work-with-github-accounts.md)
- [Visual Studio wersji 2019](/visualstudio/releases/2019/release-notes)
