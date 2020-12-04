---
title: Konfigurowanie repozytorium git
description: Nawiązywanie połączenia z repozytorium git przy użyciu Visual Studio dla komputerów Mac.
author: therealjohn
ms.author: johmil
ms.date: 12/03/2020
ms.assetid: E992FA1D-B2AD-4A28-ADC6-47E4FC471060
ms.topic: how-to
ms.openlocfilehash: bacd533bf5c28c6f431fe7088fad36b6bbd3d04b
ms.sourcegitcommit: bbed6a0b41ac4c4a24e8581ff3b34d96345ddb00
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2020
ms.locfileid: "96561061"
---
# <a name="set-up-a-git-repository"></a>Konfigurowanie repozytorium git

Git to rozproszony system kontroli wersji, który umożliwia zespołom równoczesne działanie tych samych dokumentów. Oznacza to, że istnieje jeden serwer, który zawiera wszystkie pliki, ale w każdym przypadku, gdy repozytorium jest wyewidencjonowane z tego centralnego źródła, całe repozytorium jest sklonowane lokalnie na komputerze.

Istnieje wiele hostów zdalnych, które umożliwiają współdziałanie z usługą Git na potrzeby kontroli wersji, jednak najczęściej spotykanym hostem jest GitHub. W poniższym przykładzie użyto hosta usługi GitHub, ale można użyć dowolnego hosta Git na potrzeby kontroli wersji w Visual Studio dla komputerów Mac.

Jeśli chcesz korzystać z usługi GitHub, przed wykonaniem kroków opisanych w tym artykule upewnij się, że konto zostało utworzone i skonfigurowane.

## <a name="creating-a-remote-repo-on-github"></a>Tworzenie zdalnego repozytorium w serwisie GitHub

W poniższym przykładzie użyto hosta usługi GitHub, ale można użyć dowolnego hosta Git na potrzeby kontroli wersji w Visual Studio dla komputerów Mac.

Aby skonfigurować repozytorium git, wykonaj następujące czynności:

1. Utwórz nowe repozytorium Git w witrynie github.com:

    ![Utwórz nowe repozytorium git](media/version-control-git1-sml.png)

2. Ustaw nazwę, opis i prywatność repozytorium. **Nie** Inicjuj repozytorium. Ustaw wartość. gitignore i licencję na wartość none:

    ![Ustaw szczegóły repozytorium git](media/version-control-git2.png)

3. Następna strona zapewnia opcję wyświetlania i kopiowania adresu HTTPS lub SSH do utworzonego repozytorium:

    ![Wyświetlanie i kopiowanie adresu](media/version-control-git3.png)

   Musisz mieć adres HTTPS, aby wskazać Visual Studio dla komputerów Mac tego repozytorium.

## <a name="publishing-an-existing-project"></a>Publikowanie istniejącego projektu

Jeśli masz istniejący projekt, który _nie jest_ jeszcze w kontroli wersji, wykonaj następujące kroki, aby skonfigurować go w usłudze git:

> [!TIP]
> Użyj pliku. gitignore, aby kontrolować foldery i pliki, które są śledzone i publikowane w usłudze git. Może być konieczne wykluczenie katalogów kompilacji, plików binarnych lub plików wygenerowanych. Więcej informacji znajduje się w [dokumentacji usługi GitHub w przypadku ignorowania plików](https://docs.github.com/en/free-pro-team@latest/github/using-git/ignoring-files).

1. Wybierz nazwę rozwiązania z okna rozwiązanie w Visual Studio dla komputerów Mac.

2. Na pasku menu wybierz pozycję **Kontrola wersji > publikowanie w kontroli wersji** , aby wyświetlić okno dialogowe **klonowanie repozytorium** :

    ![Rozpocznij wyewidencjonowywanie w Visual Studio dla komputerów Mac](media/version-control-git4.png)

    Jeśli ten element menu zostanie wyświetlony w menu w kolorze szarym, upewnij się, że wybrano nazwę rozwiązania.

3. Wybierz kartę **Wybierz z zarejestrowanych** i naciśnij przycisk **Dodaj** :

    ![Okno dialogowe Dodawanie zarejestrowanego repozytorium.](media/version-control-git5.png)

4. Wprowadź nazwę repozytorium, które ma być wyświetlane lokalnie, a następnie wklej adres URL z kroku #3. Okno dialogowe konfiguracji repozytorium powinno wyglądać podobnie do poniższego. Naciśnij przycisk OK:

    ![Okno dialogowe wprowadzanie szczegółów usługi git](media/version-control-git6.png)

    Istnieje również możliwość łączenia się z usługą git przy użyciu protokołu SSH.

5. Aby spróbować opublikować aplikację w usłudze git, wybierz repozytorium i upewnij się, że zostały wykonane pola **Nazwa modułu** i tekst **komunikatu** :

    ![Próba opublikowania projektu w usłudze git](media/version-control-git7.png)

6. Kliknij przycisk **OK**, a następnie **Opublikuj** w oknie dialogowym alertu.

7. W oknie **poświadczenia git** wprowadź nazwę użytkownika i hasło usługi GitHub. 

> [!NOTE]
> Jeśli konto ma włączone uwierzytelnianie dwuskładnikowe (funkcji 2FA), musisz utworzyć token dostępu, który będzie używany zamiast hasła. Jeśli nie utworzono tokenu dostępu, wykonaj kroki opisane w dokumentacji [tokenu dostępu](https://help.github.com/articles/creating-an-access-token-for-command-line-use/) git.

8. Wprowadź nazwę użytkownika i token dostępu osobistego, a następnie naciśnij przycisk **OK**:

    ![Wprowadź nazwę użytkownika i hasło do usługi git](media/version-control-git9-sml.png)

9. Po kilku sekundach rozwiązanie powinno być opublikowane z jego początkowym zatwierdzeniem. Potwierdź, że została opublikowana, przeglądając element menu kontroli wersji, który powinien zostać teraz wypełniony wieloma opcjami:

    ![Menu kontroli wersji](media/version-control-git10.png)

10. Po rozpoczęciu wprowadzania dodatkowych zmian Użyj menu **Kontrola wersji > przegląd i zatwierdzanie** , aby otworzyć widok stanu. Po wybraniu i zatwierdzeniu zmian wybierz pozycję **wypychanie** , aby wypchnąć zmiany do zdalnego repozytorium. Umożliwi to wszystkim odpowiednim użytkownikom wyświetlanie go w witrynie github.com:

    ![Wypychanie zmian do repozytorium zdalnego](media/version-control-git11.png)

## <a name="publishing-a-new-project"></a>Publikowanie nowego projektu

Okno dialogowe Nowy projekt może służyć do tworzenia nowego projektu z lokalnym repozytorium git. Aby ją włączyć, zaznacz pole wyboru **Użyj narzędzia Git dla kontroli wersji** , jak pokazano na poniższym zrzucie ekranu. Spowoduje to zainicjowanie repozytorium i dodanie opcjonalnego pliku GITIGNORE:

![Utwórz nowy projekt z obsługą git](media/version-control-git-publish-new1.png)

Wykonaj poniższe kroki, aby wypchnąć nowe repozytorium lokalne do nowego repozytorium GitHub:

> [!NOTE]
> Jeśli repozytorium GitHub nie zostało jeszcze utworzone, zapoznaj się z sekcją [Tworzenie zdalnego repozytorium w serwisie GitHub](#creating-a-remote-repo-on-github) .

1. Utwórz pierwsze zatwierdzenie, przechodząc do **kontroli wersji > Przejrzyj i zatwierdź** na pasku menu.

2. Na karcie stan wybierz pozycję **Zatwierdź** w lewym górnym rogu.

3. Napisz wiadomość zatwierdzania, na przykład "pierwsze zatwierdzenie", a następnie kliknij pozycję **Zatwierdź**:

    ![Zatwierdzanie początkowych zmian w repozytorium git](media/version-control-git-publish-new2.png)

4. Następnie na pasku menu Przejdź do pozycji **Kontrola wersji > zarządzanie gałęziami i zdalnymi**.

5. Przejdź do karty **źródła zdalne** , a następnie kliknij przycisk **Dodaj**.

6. W oknie **Źródło zdalne** Dodaj szczegóły utworzonego wcześniej repozytorium GitHub i kliknij przycisk **OK**:

    ![Konfigurowanie źródeł zdalnych dla repozytorium git](media/version-control-git-publish-new3.png)

7. Zamknij okno **Konfiguracja repozytorium git** , a następnie na pasku menu Przejdź do pozycji **Kontrola wersji > wypychanie zmian**.

8. W oknie **wypychanie do repozytorium** kliknij przycisk **wypchnij zmiany** :

    ![Wypchnij zmiany do zdalnego repozytorium](media/version-control-git-publish-new4.png)

9. Po wyświetleniu monitu wprowadź nazwę użytkownika i hasło usługi GitHub.

> [!NOTE]
> Jeśli konto ma włączone uwierzytelnianie dwuskładnikowe (funkcji 2FA), musisz utworzyć token dostępu, który będzie używany zamiast hasła. Jeśli nie utworzono tokenu dostępu, wykonaj kroki opisane w dokumentacji [tokenu dostępu](https://help.github.com/articles/creating-an-access-token-for-command-line-use/) git.

Visual Studio dla komputerów Mac teraz wypchnij zmiany do zdalnego repozytorium GitHub:

![Pomyślnie ukończono potwierdzenie operacji wypychania](media/version-control-git11.png)

## <a name="clone-an-existing-repository"></a>Klonowanie istniejącego repozytorium

Prawdopodobnie trzeba będzie pracować z repozytorium GitHub, które istnieje tylko na pilocie, a nie na komputerze lokalnym. Visual Studio dla komputerów Mac umożliwia szybkie klonowanie tego repozytorium. Wykonaj poniższe kroki, aby sklonować je do maszyny:

1. Na pasku menu wybierz pozycję **Kontrola wersji > repozytorium klonowania**:

2. Spowoduje to wyświetlenie karty **Połącz z adresem URL** :

    ![Karta łączenie z adresem URL z wprowadzonymi szczegółami](media/version-control-git13.png)

3. Na stronie GitHub repozytorium zdalnego kliknij przycisk **Klonuj lub Pobierz** i skopiuj podany adres URL:

    ![wyświetlany adres URL usługi GitHub](media/version-control-git14.png)

4. Zastąp cały tekst w polu wpis **adresu URL** na karcie **Połącz z adresem URL** . Spowoduje to wypełnienie większości innych pól na tej karcie, jak pokazano na ilustracji w kroku #2.

5. Wprowadź katalog, w którym ma zostać Sklonowane repozytorium, a następnie naciśnij pozycję **Klonuj**.

> [!NOTE]
> Problemy mogą występować, jeśli repozytorium ma rozmiar ponad 4 GB.

## <a name="troubleshooting"></a>Rozwiązywanie problemów

Jeśli masz problemy z zainicjowaniem projektu za pomocą pustego repozytorium zdalnego, możesz spróbować wykonać następujące czynności:

1. Przejdź do folderu rozwiązania.
1. Naciśnij klawisze **Command + Shift +.** do wyświetlania ukrytych plików i folderów.
1. Jeśli istnieje folder **. git** , usuń go.
1. Jeśli istnieje plik **GITIGNORE** , usuń go.
1. Naciśnij klawisze **Command + Shift +.** Aby ukryć pliki i foldery.
1. Otwórz rozwiązanie w programie VS dla komputerów Mac.
1. W oknie rozwiązanie wybierz węzeł rozwiązania.
1. Przejdź do menu kontroli wersji i wybierz polecenie **Publikuj w kontroli wersji**.
1. Wykonaj kroki opisane powyżej samouczka, rozpoczynając od kroku 6.

## <a name="see-also"></a>Zobacz także

- [Kontrola wersji w programie Visual Studio (w systemie Windows)](/visualstudio/version-control/)
