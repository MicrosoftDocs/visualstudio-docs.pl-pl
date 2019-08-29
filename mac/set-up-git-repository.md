---
title: Konfigurowanie repozytorium git
description: Używanie systemu Git i Subversion w Visual Studio dla komputerów Mac.
author: jmatthiesen
ms.author: jomatthi
ms.date: 02/15/2019
ms.assetid: E992FA1D-B2AD-4A28-ADC6-47E4FC471060
ms.openlocfilehash: 9b21ed322d2b22be619a71e474a3b5078607bbe5
ms.sourcegitcommit: cf8c0fef2b9690595e99ce3802586cdd55fd37c2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/28/2019
ms.locfileid: "70107889"
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

1. Wybierz nazwę rozwiązania z okienko rozwiązania w Visual Studio dla komputerów Mac.

2. Na pasku menu wybierz pozycję **Kontrola wersji > publikowanie w kontroli wersji** , aby wyświetlić okno dialogowe **Wybieranie repozytorium** :

    ![Rozpocznij wyewidencjonowywanie w Visual Studio dla komputerów Mac](media/version-control-git4-sml.png)

    Jeśli ten element menu zostanie wyświetlony w menu w kolorze szarym, upewnij się, że wybrano nazwę rozwiązania.

3. Wybierz kartę **zarejestrowane repozytoria** i naciśnij przycisk **Dodaj** :

    ![](media/version-control-git5.png)

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

10. Po rozpoczęciu wprowadzania dodatkowych zmian wybierz pozycję **wypchnij zmiany** , aby wypchnąć zmiany do **zdalnego** repozytorium. Umożliwi to wszystkim odpowiednim użytkownikom wyświetlanie go w witrynie github.com:

    ![Wypychanie zmian do repozytorium zdalnego](media/version-control-git11.png)

## <a name="publishing-a-new-project"></a>Publikowanie nowego projektu

Okno dialogowe Nowy projekt może służyć do tworzenia nowego projektu z lokalnym repozytorium git. Aby ją włączyć, zaznacz pole wyboru **Użyj narzędzia Git dla kontroli wersji** , jak pokazano na poniższym zrzucie ekranu. Spowoduje to zainicjowanie repozytorium i dodanie opcjonalnego pliku GITIGNORE:

![Utwórz nowy projekt z obsługą git](media/version-control-git-publish-new1.png)

Wykonaj poniższe kroki, aby wypchnąć nowe repozytorium lokalne do nowego repozytorium GitHub:

> [!NOTE]
> Jeśli repozytorium GitHub nie zostało jeszcze utworzone, zapoznaj się z sekcją [Tworzenie zdalnego repozytorium w serwisie GitHub](#creating-a-remote-repo-on-github) .

1. Utwórz pierwsze zatwierdzenie, przechodząc do **kontroli wersji > Przejrzyj rozwiązanie i zatwierdzenie** na pasku menu.

2. Na karcie stan wybierz pozycję **Zatwierdź** w lewym górnym rogu.

3. Napisz wiadomość zatwierdzania, na przykład "pierwsze zatwierdzenie", a następniekliknij pozycję Zatwierdź:

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

## <a name="check-out-an-existing-repository"></a>Zapoznaj się z istniejącym repozytorium

Prawdopodobnie trzeba będzie pracować z repozytorium GitHub, które istnieje tylko na pilocie, a nie na komputerze lokalnym. Visual Studio dla komputerów Mac umożliwia szybkie sprawdzenie tego repozytorium. Wykonaj poniższe kroki, aby sklonować je do maszyny:

1. Na pasku menu wybierz pozycję **Kontrola wersji > wyewidencjonowanie**:

2. Spowoduje to wyświetlenie karty **Połącz z repozytorium** :

    ![Karta łączenie z repozytorium z wprowadzonymi szczegółami](media/version-control-git13.png)

3. Na stronie GitHub repozytorium zdalnego kliknij przycisk **Klonuj lub Pobierz** i skopiuj podany adres URL:

    ![wyświetlany adres URL usługi GitHub](media/version-control-git14.png)

4. Zastąp cały tekst w polu wpis **adresu URL** na karcie **Połącz z repozytorium** . Spowoduje to wypełnienie większości innych pól na tej karcie, jak pokazano na ilustracji w kroku #2.

5. Wprowadź katalog, w którym ma zostać Sklonowane repozytorium, a następnienaciśnij pozycję Wyewidencjonowywanie.

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
1. W konsoli rozwiązania wybierz węzeł rozwiązania.
1. Przejdź do menu kontroli wersji i wybierz polecenie **Publikuj w kontroli wersji**.
1. Wykonaj kroki opisane powyżej samouczka, rozpoczynając od kroku 6.

## <a name="see-also"></a>Zobacz także

- [Kontrola wersji w programie Visual Studio (w systemie Windows)](/visualstudio/version-control/)
