---
title: Praca z wieloma kontami użytkowników
ms.date: 07/23/2019
ms.topic: conceptual
author: ornellaalt
ms.author: ornella
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: abca888cda2d309951d6b8921cfd2078972ce195
ms.sourcegitcommit: a801ca3269274ce1de4f6b2c3f40b58bbaa3f460
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/25/2020
ms.locfileid: "88800232"
---
# <a name="work-with-multiple-user-accounts"></a>Praca z wieloma kontami użytkowników

Jeśli masz wiele kont Microsoft i/lub kont służbowych, możesz dodać je wszystkie do programu Visual Studio, aby uzyskać dostęp do zasobów z dowolnego konta bez konieczności logowania się do niego osobno. Na platformie Azure, Application Insights, Azure DevOps i Microsoft 365 Services wszystkie obsługują usprawnione środowisko logowania.

Po dodaniu wielu kont na jednej maszynie ten zbiór kont zostanie przejściu do Ciebie, jeśli zalogujesz się do programu Visual Studio na innym komputerze.

> [!NOTE]
> Mimo że nazwy kont są przenoszone, poświadczenia nie są obsługiwane. Zostanie wyświetlony monit o podanie poświadczeń dla tych innych kont przy pierwszej próbie użycia zasobów na nowym komputerze.

W tym artykule pokazano, jak dodać wiele kont do programu Visual Studio. Przedstawiono w nim również sposób wyświetlania zasobów dostępnych z tych kont w miejscach takich jak okno dialogowe **Dodawanie podłączonej usługi** , **Eksplorator serwera**i **Team Explorer**.

## <a name="sign-in-to-visual-studio"></a>Logowanie do programu Visual Studio

Zaloguj się do programu Visual Studio przy użyciu konto Microsoft lub konta organizacyjnego. Twoja nazwa użytkownika powinna pojawić się w górnym rogu okna, podobnie jak w przypadku:

![Aktualnie zalogowany użytkownik](../ide/media/vs2015_username.png)

### <a name="access-your-azure-account-in-server-explorer"></a>Uzyskaj dostęp do konta platformy Azure w Eksplorator serwera

Aby otworzyć Eksplorator serwera, wybierz pozycję **Wyświetl**  >  **Eksplorator serwera** (lub, jeśli używasz [ustawień środowiska](../ide/environment-settings.md)"ogólne", naciśnij klawisze **Ctrl** + **Alt** + **S**). Rozwiń węzeł **platformy Azure** i zwróć uwagę, że zawiera on zasoby dostępne na koncie platformy Azure skojarzonym z kontem używanym do logowania się w programie Visual Studio. Wygląda podobnie do poniższej ilustracji:

![Eksplorator serwera z rozwiniętym węzłem platformy Azure](../ide/media/work-with-multiple-user-accounts/server-explorer.png)

Przy pierwszym użyciu programu Visual Studio na dowolnym konkretnym urządzeniu w oknie dialogowym są wyświetlane tylko subskrypcje zarejestrowane w ramach konta, na którym się zalogowano. Możesz uzyskać dostęp do zasobów dla dowolnego innego konta bezpośrednio z **Eksplorator serwera** , klikając prawym przyciskiem myszy węzeł **platformy Azure** , wybierając pozycję **Zarządzaj i Filtruj subskrypcje**, a następnie dodając konta z poziomu kontrolki selektor kont. W razie potrzeby możesz wybrać inne konto, klikając strzałkę w dół i wybierając pozycję z listy kont. Po wybraniu konta możesz dostosować subskrypcje w ramach tego konta, które mają być wyświetlane w **Eksplorator serwera**.

![Okno dialogowe Zarządzanie subskrypcjami platformy Azure](../ide/media/vs2015_manage_subs.png)

Przy następnym otwarciu **Eksplorator serwera**zostaną wyświetlone zasoby dla tej subskrypcji.

### <a name="access-your-azure-account-via-add-connected-service-dialog"></a>Uzyskiwanie dostępu do konta platformy Azure za pomocą okna dialogowego Dodawanie połączonej usługi

1. Otwórz istniejący projekt lub Utwórz nowy projekt.

1. Wybierz węzeł projektu w **Eksplorator rozwiązań**, a następnie kliknij prawym przyciskiem myszy i wybierz polecenie **Dodaj**  >  **podłączoną usługę**.

   Zostanie wyświetlony Kreator **dodawania usługi połączonej** z listą usług na koncie platformy Azure skojarzonym z Twoim kontem personalizacji programu Visual Studio. Nie musisz logować się osobno na platformie Azure. Należy jednak zalogować się do innych kont przy pierwszej próbie uzyskania dostępu do zasobów z innego komputera.

### <a name="access-azure-active-directory-in-a-web-project"></a>Dostęp do Azure Active Directory w projekcie sieci Web

Usługa Azure Active Directory (AAD) umożliwia obsługę logowania jednokrotnego dla użytkowników końcowych w aplikacjach sieci Web ASP.NET MVC lub uwierzytelnianie usługi AD w usługach interfejsu API sieci Web. Uwierzytelnianie domeny różni się od uwierzytelniania poszczególnych kont użytkowników. Użytkownicy, którzy mają dostęp do domeny Active Directory mogą korzystać z istniejących kont usługi AAD do łączenia się z aplikacjami sieci Web. Aplikacje Microsoft 365 mogą również korzystać z uwierzytelniania domeny.

::: moniker range="vs-2017"

Aby wyświetlić tę akcję, Utwórz nowy projekt **ASP.NET Core aplikacji sieci Web** . W oknie dialogowym **Nowa aplikacja sieci web ASP.NET Core** wybierz szablon **aplikacja sieci Web** , a następnie wybierz pozycję **Zmień uwierzytelnianie**.

::: moniker-end

::: moniker range=">=vs-2019"

Aby wyświetlić tę akcję, Utwórz nowy projekt **ASP.NET Core aplikacji sieci Web** . Na stronie **Tworzenie nowej ASP.NET Core aplikacji sieci Web** wybierz szablon **aplikacja sieci Web** , a następnie wybierz pozycję **Zmień** w obszarze **uwierzytelnianie**.

::: moniker-end

Zostanie wyświetlone okno dialogowe **Zmienianie uwierzytelniania** , w którym można wybrać rodzaj uwierzytelniania, który ma być używany w aplikacji.

![Okno dialogowe Zmienianie uwierzytelniania dla ASP.NET](../ide/media/vs2015_change_authentication.png)

Aby uzyskać więcej informacji na temat różnych rodzajów uwierzytelniania w programie ASP.NET, zobacz [Tworzenie projektów sieci web ASP.NET w programie Visual Studio](/aspnet/visual-studio/overview/2013/creating-web-projects-in-visual-studio#authentication-methods).

### <a name="access-your-azure-devops-organization"></a>Dostęp do organizacji usługi Azure DevOps

Z menu głównego wybierz kolejno pozycje **zespół**  >  **Zarządzanie połączeniami** , aby otworzyć okno **Team Explorer-Connect** . Wybierz pozycję **Zarządzaj połączeniami**  >  **Połącz**się z projektem. W oknie dialogowym **Połącz z projektem** wybierz projekt z listy (lub wybierz pozycję **Dodaj serwer TFS** i wprowadź adres URL serwera). Po wybraniu adresu URL użytkownik jest zalogowany bez konieczności ponownego wprowadzania poświadczeń.

Aby uzyskać więcej informacji, zobacz [nawiązywanie połączenia z projektami w Team Explorer](connect-team-project.md).

## <a name="add-an-additional-account-to-visual-studio"></a>Dodawanie dodatkowego konta do programu Visual Studio

Aby dodać dodatkowe konto do programu Visual Studio:

1. Wybierz **File**pozycję  >  **Ustawienia konta**pliku.

1. W obszarze **wszystkie konta**wybierz pozycję **Dodaj konto**.

1. Na stronie **Logowanie do konta** wybierz konto lub wybierz pozycję **Użyj innego konta**. Postępuj zgodnie z monitami, aby wprowadzić nowe poświadczenia konta.

Obowiązkowe Teraz możesz przejść do **Eksplorator serwera** i wyświetlić usługi platformy Azure skojarzone z właśnie dodanym kontem. W **Eksplorator serwera**kliknij prawym przyciskiem myszy węzeł **platformy Azure** , a następnie wybierz pozycję **Zarządzaj i Filtruj subskrypcje**. Wybierz nowe konto, klikając strzałkę listy rozwijanej obok bieżącego konta, a następnie wybierz subskrypcje, które mają być wyświetlane w **Eksplorator serwera**. Powinny zostać wyświetlone wszystkie usługi skojarzone z określoną subskrypcją. Mimo że użytkownik nie jest obecnie zalogowany do programu Visual Studio przy użyciu drugiego konta, loguje się do usług i zasobów tego konta. To samo jest prawdziwe w przypadku **programu Project**  >  **Dodawanie połączonej usługi** i łączenie **zespołu**z  >  **Team Foundation Server**.

### <a name="add-an-account-using-device-code-flow"></a>Dodawanie konta przy użyciu przepływu kodu urządzenia

W niektórych przypadkach nie można zalogować się lub dodać konta w zwykły sposób. Taka sytuacja może wystąpić, jeśli program Internet Explorer jest blokowany z jakiegoś powodu lub jeśli sieć znajduje się za zaporą. Aby obejść ten proces, można włączyć *przepływ kodu urządzenia* , aby dodać konto lub ponownie uwierzytelnić Twoje konto. Przepływ kodu urządzenia umożliwia zalogowanie się przy użyciu innej przeglądarki lub innej maszyny &mdash; fizycznej lub wirtualnej (VM).

Aby zalogować się za pomocą przepływu kodu urządzenia:

1. Otwórz stronę [**konta**](reference/accounts-environment-options-dialog-box.md) w obszarze **Narzędzia**  >  **Opcje**  >  **środowisko**, a następnie wybierz pozycję **Włącz przepływ kodu urządzenia podczas dodawania lub ponownego uwierzytelniania konta**. Wybierz **przycisk OK** , aby zamknąć strony Opcje.

1. Wybierz **File**pozycję  >  **Ustawienia konta** pliku, aby otworzyć stronę Zarządzanie kontem.

1. Wybierz pozycję **Dodaj konto** w obszarze **wszystkie konta**.

   Zostanie wyświetlone okno dialogowe z adresem URL i kodem do wklejenia do przeglądarki sieci Web.

   ![Adres URL i kod przepływu kodu urządzenia](media/work-with-multiple-user-accounts/device-login-code.png)

1. Naciśnij klawisz **Ctrl** + **C** , aby skopiować tekst okna dialogowego, a następnie wybierz przycisk **OK** , aby zamknąć okno dialogowe. Wklej skopiowany tekst do edytora tekstu, takiego jak Notatnik. Ułatwia to skopiowanie kodu w następnym kroku.

1. Przejdź do adresu URL logowania do urządzenia na komputerze lub w przeglądarce sieci Web, którego chcesz użyć do zalogowania się do programu Visual Studio, a następnie wklej lub wprowadź kod skopiowany do pola, w którym znajduje się **kod**.

   Nazwa aplikacji **Visual Studio** powinna zostać wyświetlona w dalszej postaci na stronie.

1. W obszarze **Visual Studio**wybierz pozycję **Kontynuuj**.

   ![device-login-page.png](media/work-with-multiple-user-accounts/device-login-page.png)

1. Postępuj zgodnie z monitami, aby wprowadzić poświadczenia konta.

   Zostanie wyświetlona strona z informacją, że użytkownik zalogował się do programu Visual Studio na urządzeniu i że można zamknąć okno przeglądarki.

   ![Ukończono logowanie w programie Visual Studio za poorednictwem przeglądarki](media/work-with-multiple-user-accounts/sign-in-browser-complete.png)

1. Wróć do strony zarządzania kontami w programie Visual Studio, a nowo dodane konto zostanie wyświetlone w obszarze **wszystkie konta**. Wybierz pozycję **Zamknij**.

## <a name="see-also"></a>Zobacz też

- [Logowanie do programu Visual Studio](signing-in-to-visual-studio.md)
- [Zaloguj się do Visual Studio dla komputerów Mac](/visualstudio/mac/signing-in)
