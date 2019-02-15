---
title: Konfigurowanie repozytorium Git
description: Przy użyciu narzędzia Git i Subversion w programie Visual Studio dla komputerów Mac.
author: conceptdev
ms.author: crdun
ms.date: 02/15/2018
ms.assetid: E992FA1D-B2AD-4A28-ADC6-47E4FC471060
ms.openlocfilehash: 17067e9b19a36f198a6653f0c354e6ce3004eaeb
ms.sourcegitcommit: 752f03977f45169585e407ef719450dbe219b7fc
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/15/2019
ms.locfileid: "56317351"
---
# <a name="set-up-a-git-repository"></a>Konfigurowanie repozytorium Git

Git to Rozproszony system kontroli wersji umożliwiający zespoły mogą pracować na tym samym dokumentach jednocześnie. Oznacza to, jest jednym serwerze, który zawiera wszystkie pliki, ale zawsze wtedy, gdy repozytorium jest wyewidencjonowany z tego źródła centralnej, całe repozytorium został sklonowany lokalnie na komputerze.

Istnieje wiele hostów zdalnych, które umożliwiają pracę przy użyciu narzędzia Git do kontroli wersji, jednak najczęściej host jest GitHub. W poniższym przykładzie użyto hosta usługi GitHub, ale można użyć dowolnego hosta usługi Git do kontroli wersji w programie Visual Studio dla komputerów Mac.

Jeśli chcesz korzystać z usługi GitHub, upewnij się, że masz konto utworzone i skonfigurowane przed wykonaniem kroków opisanych w tym artykule.

## <a name="creating-a-remote-repo-on-github"></a>Tworzenie repozytorium zdalnego w serwisie GitHub

W poniższym przykładzie użyto hosta usługi GitHub, ale można użyć dowolnego hosta usługi Git do kontroli wersji w programie Visual Studio dla komputerów Mac.

Aby skonfigurować repozytorium Git, wykonaj następujące czynności:

1. Utwórz nowe repozytorium Git w github.com:

    ![Tworzenie nowego repozytorium git](media/version-control-git1-sml.png)

2. Ustaw nazwę repozytorium, opis i ochrony prywatności. Czy **nie** Zainicjuj repozytorium. Ustaw pliki .gitignore i licencji na Brak:

    ![Szczegóły zestawu z repozytorium git](media/version-control-git2.png)

3. Następnej strony daje możliwość wyświetlenia, a następnie skopiuj adres HTTPS lub protokołu SSH do repozytorium, które zostały utworzone:

    ![Wyświetl i skopiuj adres](media/version-control-git3.png)

   Konieczne będzie z adresu HTTPS do punktu, Visual Studio dla komputerów Mac w tym repozytorium.

## <a name="publishing-an-existing-project"></a>Publikowanie istniejący projekt

Jeśli masz istniejący projekt, który _nie_ już w kontroli wersji, wykonaj następujące kroki, aby skonfigurować w usłudze Git:

1.  Wybierz nazwę rozwiązania z konsoli rozwiązania w programie Visual Studio dla komputerów Mac.

2. Na pasku Menu wybierz **kontroli wersji > Publikuj w kontroli wersji** do wyświetlenia **wybierz repozytorium** okno dialogowe:

    ![Rozpocznij wyewidencjonowania w programie Visual Studio dla komputerów Mac](media/version-control-git4-sml.png)

    Jeśli ten element menu pojawia się wyszarzonym w menu, upewnij się, że wybrana nazwa rozwiązania.

3. Wybierz **zarejestrowane repozytoria** kartę, a następnie naciśnij klawisz **Dodaj** przycisku:

    ![](media/version-control-git5.png)

4. Wprowadź nazwę repozytorium, jak chcesz, aby wyświetlić lokalnie, a następnie wklej w adresie URL w kroku #3. Konfiguracja repozytorium okna dialogowego powinny wyglądać podobnie do następującego. Naciśnij przycisk OK:

    ![Wprowadź szczegóły git w oknie dialogowym](media/version-control-git6.png)

    Istnieje również możliwość łączenia do usługi Git za pomocą protokołu SSH.

5. Próby publikowanie aplikacji w usłudze Git, wybierz repozytorium i upewnij się, że oba **Nazwa modułu** i **komunikat** odbywa się pól tekstowych:

    ![Próba opublikowania projektu do usługi git](media/version-control-git7.png)

6. Kliknij przycisk **OK**, a następnie **Publikuj** z okna dialogowego alertu.

7. W **poświadczeń Git** okna, wprowadź nazwę użytkownika usługi GitHub i hasło. 

> [!NOTE]
> Jeśli Twoje konto ma uwierzytelniania dwuskładnikowego (2FA) włączone, należy utworzyć Token dostępu, który jest używany zamiast hasła. Jeśli token dostępu nie została utworzona, wykonaj kroki w Git [Token dostępu](https://help.github.com/articles/creating-an-access-token-for-command-line-use/) dokumentacji.

8. Wprowadź nazwę użytkownika i osobisty Token dostępu i naciśnij klawisz **OK**:

    ![Wprowadź nazwę użytkownika i hasło dla usługi git](media/version-control-git9-sml.png)

9. Po kilku sekundach rozwiązania powinny być publikowane z jego początkowe zatwierdzenie. Upewnij się, że został opublikowany, przechodząc elementu menu kontroli wersji, który powinien zostać wypełniony wiele opcji:

    ![Menu Kontrola wersji](media/version-control-git10.png)

10. Po rozpoczęciu wprowadzania dodatkowych zmian, wybierz **wypychanie zmian** wypychania zmian do **zdalnego** repozytorium. Zezwalaj na wszystkich odpowiednich użytkowników go wyświetlić w witrynie github.com:

    ![Wypchnij zmiany do repozytorium zdalnego](media/version-control-git11.png)

## <a name="publishing-a-new-project"></a>Publikowanie nowego projektu

Okno dialogowe nowego projektu może służyć do tworzenia nowego projektu z repozytorium lokalnego narzędzia git. Aby ją włączyć, wybierz **za pomocą narzędzia git do kontroli wersji** pole wyboru, jak pokazano na poniższym zrzucie ekranu. Spowoduje to zainicjowanie repozytorium i Dodaj plik gitignore opcjonalne:

![Utwórz nowy projekt z obsługą usługi git](media/version-control-git-publish-new1.png)

Wykonaj poniższe kroki, aby wypchnąć nowe repozytorium lokalne do nowego repozytorium usługi GitHub:

> [!NOTE]
> Jeśli jeszcze nie utworzono repozytorium GitHub, zapoznaj się [Tworzenie zdalnego repozytorium w serwisie GitHub](#creating-a-remote-repo-on-github) sekcji.

1. Tworzenie pierwszego zatwierdzenia, przechodząc do **kontroli wersji > Przejrzyj rozwiązanie i zatwierdź** na pasku Menu.

2. Na karcie Stan wybierz **zatwierdzić** w lewym górnym rogu.

3. Napisz wiadomość dotyczącą zatwierdzenia, na przykład "pierwsze zatwierdzenie", a następnie kliknij pozycję **zatwierdzenia**:

    ![Zatwierdź początkowej zmiany do repozytorium git](media/version-control-git-publish-new2.png)

4. Następnie na pasku Menu, przejdź do **kontroli wersji > Zarządzanie gałęziami i źródłami zdalnymi**.

5. Przejdź do **zdalnych źródeł** , a następnie kliknij **Dodaj**.

6. W **zdalnego źródła** okna, Dodaj szczegóły wcześniej utworzonego repozytorium GitHub i kliknij przycisk **OK**:

    ![Konfigurowanie zdalnych źródeł dla repozytorium git](media/version-control-git-publish-new3.png)

7. Zamknij **Konfiguracja repozytorium Git** okna, a następnie na pasku Menu, przejdź do **kontroli wersji > wypychanie zmian**.

8. W **Wypchnij do repozytorium** kliknij okno **wypychanie zmian** przycisku:

    ![Wypchnij zmiany do repozytorium zdalnego](media/version-control-git-publish-new4.png)

9. Po wyświetleniu monitu wprowadź nazwę użytkownika usługi GitHub i hasło.

> [!NOTE]
> Jeśli Twoje konto ma uwierzytelniania dwuskładnikowego (2FA) włączone, należy utworzyć Token dostępu, który jest używany zamiast hasła. Jeśli token dostępu nie została utworzona, wykonaj kroki w Git [Token dostępu](https://help.github.com/articles/creating-an-access-token-for-command-line-use/) dokumentacji.

Program Visual Studio for Mac zostanie teraz Wypchnij zmiany do zdalnego repozytorium GitHub:

![Wypychanie potwierdzenia pomyślnie Ukończono operację](media/version-control-git11.png)

## <a name="check-out-an-existing-repository"></a>Zapoznaj się z istniejącym repozytorium

Istnieje prawdopodobieństwo, że musisz pracować z repozytorium GitHub, która istnieje tylko w lokalizacji zdalnej, nie na komputerze lokalnym. Program Visual Studio for Mac umożliwia szybkie wyewidencjonować tego repozytorium. Wykonaj poniższe kroki, aby sklonować ten projekt do komputera:

1. Na pasku Menu wybierz **kontroli wersji > wyewidencjonowania**:

2. Spowoduje to wyświetlenie **nawiązywanie połączenia z repozytorium** karty:

    ![Połącz kartę repozytorium ze szczegółami podanymi](media/version-control-git13.png)

3. Na stronie GitHub repozytorium zdalnego, naciśnij klawisz **Klonuj lub Pobierz** przycisk i skopiuj adres URL podany:

    ![wyświetlany adres url usługi github](media/version-control-git14.png)

4. Zastąp cały tekst w **adresu URL** pola wpisu w **nawiązywanie połączenia z repozytorium** kartę. Spowoduje to wypełnienie większości innych pól na tej karcie, jak pokazano na ilustracji w kroku #2.

5. Wprowadź katalog, który chcesz sklonować repozytorium do, a następnie naciśnij klawisz **wyewidencjonowania**.

> [!NOTE]
> Mogą wystąpić problemy, jeśli repozytorium jest ponad 4 GB.

## <a name="troubleshooting"></a>Rozwiązywanie problemów

Jeśli masz problemy z inicjowanie projektu za pomocą puste repozytorium zdalnego, możesz spróbować następujące czynności:

1. Przejdź do folderu rozwiązania.
1. Naciśnij klawisz **Command + Shift +.** Aby wyświetlić ukryte pliki i foldery.
1. W przypadku **.git** folder, usuń go.
1. W przypadku **gitignore** , usuń go.
1. Naciśnij klawisz **Command + Shift +.** Aby ukryć, pliki i foldery.
1. Otwórz swoje rozwiązanie w programie VS dla komputerów Mac.
1. Na rozwiązanie konsoli wybierz węzeł rozwiązania.
1. Przejdź do menu kontroli wersji, a następnie wybierz **publikowania w systemie kontroli wersji**.
1. Wykonaj kroki samouczka powyżej, zaczynając od kroku 6.

## <a name="see-also"></a>Zobacz także

- [Kontrola wersji w programie Visual Studio (na Windows)](/visualstudio/version-control/)
