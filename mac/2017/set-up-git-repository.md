---
title: Konfigurowanie repozytorium Git
description: Korzystanie z git i subversion w programie Visual Studio dla komputerów Mac.
author: heiligerdankgesang
ms.author: dominicn
ms.date: 02/15/2018
ms.assetid: E992FA1D-B2AD-4A28-ADC6-47E4FC471060
ms.openlocfilehash: e6dbe3b04a39a1ffd9a6e1b8f241b497ba8a6563
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/20/2020
ms.locfileid: "74984848"
---
# <a name="set-up-a-git-repository"></a>Konfigurowanie repozytorium Git

Git to rozproszony system kontroli wersji, który umożliwia zespołom jednoczesną pracę nad tymi samymi dokumentami. Oznacza to, że istnieje jeden serwer, który zawiera wszystkie pliki, ale za każdym razem, gdy repozytorium jest wyewidencjonowany z tego centralnego źródła, całe repozytorium jest klonowane lokalnie do komputera.

Istnieje wiele zdalnych hostów, które umożliwiają pracę z Git do kontroli wersji, jednak najczęstszym hostem jest GitHub. W poniższym przykładzie użyto hosta Usługi GitHub, ale można użyć dowolnego hosta Git do kontroli wersji w programie Visual Studio dla komputerów Mac.

Jeśli chcesz korzystać z usługi GitHub, upewnij się, że masz konto utworzone i skonfigurowane przed wykonać kroki opisane w tym artykule.

## <a name="creating-a-remote-repo-on-github"></a>Tworzenie zdalnego repozytorium w usłudze GitHub

W poniższym przykładzie użyto hosta Usługi GitHub, ale można użyć dowolnego hosta Git do kontroli wersji w programie Visual Studio dla komputerów Mac.

Aby skonfigurować repozytorium Git, wykonaj następujące kroki:

1. Utwórz nowe repozytorium Git w github.com:

    ![Tworzenie nowego repozytorium git](media/version-control-git1-sml.png)

2. Ustaw nazwę repozytorium, opis i prywatność. **Nie** inicjuj repozytorium. Ustaw .gitignore i licencję na Brak:

    ![Ustawianie szczegółów repozytorium git](media/version-control-git2.png)

3. Następna strona umożliwia wyświetlanie i kopiowanie adresu HTTPS lub SSH do utworzonego repozytorium:

    ![wyświetlanie i kopiowanie adresu](media/version-control-git3.png)

   Musisz adres HTTPS, aby wskazać visual studio dla komputerów Mac do tego repozytorium.

## <a name="publishing-an-existing-project"></a>Publikowanie istniejącego projektu

Jeśli masz istniejący projekt, który _nie jest_ jeszcze w kontroli wersji, użyj następujących kroków, aby skonfigurować go w Git:

1. Wybierz nazwę rozwiązania z konsoli rozwiązania w programie Visual Studio dla komputerów Mac.

2. Na pasku menu wybierz pozycję **Kontrola wersji > publikuj w formancie wersji,** aby wyświetlić okno dialogowe **Wybierz repozytorium:**

    ![Rozpoczynanie realizacji transakcji w programie Visual Studio dla komputerów Mac](media/version-control-git4-sml.png)

    Jeśli ten element menu jest wyszarzony w menu, upewnij się, że wybrano nazwę rozwiązania.

3. Wybierz kartę **Zarejestrowane repozytoria** i naciśnij przycisk **Dodaj:**

    ![](media/version-control-git5.png)

4. Wprowadź nazwę repozytorium, zgodnie z oczekiwaniami, aby było wyświetlane lokalnie, i wklej adres URL z kroku #3. Okno dialogowe Konfiguracji repozytorium powinno wyglądać podobnie do następującego. Naciśnij przycisk OK:

    ![Wprowadź okno dialogowe szczegółów git](media/version-control-git6.png)

    Możliwe jest również użycie SSH do podłączenia do Git.

5. Aby spróbować opublikować aplikację w gicie, zaznacz repozytorium i upewnij się, że pola **tekstowe Nazwa modułu** i **Wiadomość** są wypełnione:

    ![Próba opublikowania projektu do git](media/version-control-git7.png)

6. Kliknij **pozycję Ok,** a następnie **pozycję Publikuj** z okna dialogowego alertu.

7. W oknie **Poświadczenia Git** wprowadź nazwę użytkownika i hasło usługi GitHub. 

> [!NOTE]
> Jeśli twoje konto ma włączone uwierzytelnianie dwuskładnikowe (2FA), należy utworzyć token dostępu, który jest używany zamiast hasła. Jeśli token dostępu nie został utworzony, wykonaj kroki opisane w dokumentacji [tokenu dostępu](https://help.github.com/articles/creating-an-access-token-for-command-line-use/) Git.

8. Wprowadź nazwę użytkownika i token dostępu osobistego, a następnie naciśnij **przycisk Dobra**:

    ![Wprowadź nazwę użytkownika i hasło do git](media/version-control-git9-sml.png)

9. Po kilku sekundach rozwiązanie powinno zostać opublikowane z jego początkowym zatwierdzeniem. Potwierdź, że został opublikowany, przeglądając pozycję menu Kontrola wersji, która powinna być teraz wypełniona wieloma opcjami:

    ![Menu kontroli wersji](media/version-control-git10.png)

10. Po rozpoczęciu wprowadzania dodatkowych zmian wybierz **opcję Wypychanie zmian,** aby wypchnąć zmiany do **zdalnego** repozytorium. Umożliwi to wszystkim odpowiednim użytkownikom wyświetlanie go na github.com:

    ![Wypychanie zmian w zdalnym repozytorium](media/version-control-git11.png)

## <a name="publishing-a-new-project"></a>Publikowanie nowego projektu

Nowe okno dialogowe projektu może służyć do tworzenia nowego projektu z lokalnym repozytorium git. Aby ją włączyć, zaznacz pole wyboru **Użyj git for version control,** jak pokazano na poniższym zrzucie ekranu. Spowoduje to zainicjowanie repozytorium i dodanie opcjonalnego pliku gitignore:

![Tworzenie nowego projektu z obsługą git](media/version-control-git-publish-new1.png)

Wykonaj poniższe czynności, aby wypchnąć nowe repozytorium lokalne do nowego repozytorium GitHub:

> [!NOTE]
> Jeśli nie utworzono jeszcze repozytorium GitHub, zapoznaj się z [sekcją Tworzenie zdalnego repozytorium w usłudze GitHub.](#creating-a-remote-repo-on-github)

1. Utwórz pierwsze zatwierdzenie, przechodząc do **kontroli wersji > rozwiązanie do przeglądu i zatwierdzania** na pasku menu.

2. Na karcie Stan wybierz pozycję **Zatwierdź** w lewym górnym rogu.

3. Napisz komunikat o zatwierdzeniu, na przykład "Pierwsze zatwierdzenie", a następnie kliknij **przycisk Commit**:

    ![Zatwierdzanie początkowych zmian w repozytorium git](media/version-control-git-publish-new2.png)

4. Następnie na pasku menu przejdź do **kontroli wersji > Zarządzaj gałęziami i pilotami**.

5. Przejdź do karty **Źródła zdalne,** a następnie kliknij pozycję **Dodaj**.

6. W oknie **Źródło zdalne** dodaj szczegóły wcześniej utworzonego repozytorium GitHub i kliknij przycisk **OK:**

    ![Konfigurowanie źródeł zdalnych dla repozytorium git](media/version-control-git-publish-new3.png)

7. Zamknij okno **Konfiguracja repozytorium Git,** a następnie na pasku menu przejdź do **kontroli wersji > wypychania zmian**.

8. W oknie **Push to Repozytorium** kliknij przycisk **Push Changes:**

    ![Wypychanie zmian do zdalnego repozytorium](media/version-control-git-publish-new4.png)

9. Po wyświetleniu monitu wprowadź nazwę użytkownika i hasło usługi GitHub.

> [!NOTE]
> Jeśli twoje konto ma włączone uwierzytelnianie dwuskładnikowe (2FA), należy utworzyć token dostępu, który jest używany zamiast hasła. Jeśli token dostępu nie został utworzony, wykonaj kroki opisane w dokumentacji [tokenu dostępu](https://help.github.com/articles/creating-an-access-token-for-command-line-use/) Git.

Visual Studio dla komputerów Mac będzie teraz wypychać zmiany do zdalnego repozytorium GitHub:

![Operacja wypychania pomyślnie zakończona potwierdzenie](media/version-control-git11.png)

## <a name="check-out-an-existing-repository"></a>Wyewidencjonuj istniejące repozytorium

Jest prawdopodobne, że będziesz musiał pracować z repozytorium GitHub, które istnieje tylko na pilocie, a nie na komputerze lokalnym. Visual Studio dla komputerów Mac umożliwia szybkie sprawdzenie tego repozytorium. Wykonaj poniższe czynności, aby sklonować go na komputerze:

1. Na pasku menu wybierz **pozycję Kontrola wersji > wyewidencjonowanie:**

2. Spowoduje to wyświetlenie karty **Połącz z repozytorium:**

    ![Połącz się z kartą Repozytorium z wprowadzonymi szczegółami](media/version-control-git13.png)

3. Na stronie GitHub zdalnego repozytorium naciśnij przycisk **Klonuj lub Pobierz** i skopiuj podany adres URL:

    ![github url wyświetlany](media/version-control-git14.png)

4. Zastąp cały tekst w polu wpisu **adresu URL** na karcie **Połącz z repozytorium.** Spowoduje to wypełnienie większości innych pól na tej karcie, jak pokazano na obrazie w kroku #2.

5. Wprowadź katalog, do którego chcesz sklonować repozytorium, i naciśnij klawisz **Wyewidencjonuj**.

> [!NOTE]
> Mogą wystąpić problemy, jeśli repozytorium ma rozmiar ponad 4 GB.

## <a name="troubleshooting"></a>Rozwiązywanie problemów

Jeśli masz problemy z zainicjowaniem projektu za pomocą pustego repozytorium zdalnego, możesz wykonać następujące czynności:

1. Przejdź do folderu rozwiązań.
1. Naciśnij **przycisk Poleceń + Shift + .** , aby wyświetlić ukryte pliki i foldery.
1. Jeśli istnieje folder **.git,** usuń go.
1. Jeśli istnieje plik **gitignore,** usuń go.
1. Naciśnij **przycisk Poleceń + Shift + .** , aby ukryć pliki i foldery.
1. Otwórz rozwiązanie w programie VS dla komputerów Mac.
1. Na panelu rozwiązania wybierz węzeł rozwiązania.
1. Przejdź do menu Kontrola wersji i wybierz polecenie **Publikuj w obszarze Kontrola wersji**.
1. Postępuj zgodnie z instrukcjami powyższego samouczka, zaczynając od kroku 6.

## <a name="see-also"></a>Zobacz też

- [Kontrola wersji w programie Visual Studio (w systemie Windows)](/visualstudio/version-control/)
