---
title: Praca z wieloma kontami użytkowników
ms.date: 07/23/2019
ms.topic: conceptual
author: ornellaalt
ms.author: ornella
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 872089158b6e4dc0b55c26ad187e3b68d0501f26
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "77027608"
---
# <a name="work-with-multiple-user-accounts"></a>Praca z wieloma kontami użytkowników

Jeśli masz wiele kont Microsoft i/lub kont służbowych, możesz dodać je wszystkie do programu Visual Studio, aby uzyskać dostęp do zasobów z dowolnego konta bez konieczności logowania się do niego oddzielnie. Usługi Azure, Application Insights, Azure DevOps i Office 365 obsługują usprawnione środowisko logowania.

Po dodaniu wielu kont na jednym komputerze ten zestaw kont przemieszcza się z Tobą, jeśli zalogujesz się do programu Visual Studio na innym komputerze.

> [!NOTE]
> Chociaż nazwy kont są przemęczone, poświadczenia nie są. Zostanie wyświetlony monit o wprowadzenie poświadczeń dla tych innych kont przy pierwszej próbie użycia ich zasobów na nowym komputerze.

W tym artykule pokazano, jak dodać wiele kont do programu Visual Studio. Pokazuje również, jak wyświetlić zasoby dostępne z tych kont w miejscach takich jak Okno dialogowe **Dodaj połączoną usługę,** **Eksplorator serwera**i **Eksplorator zespołu**.

## <a name="sign-in-to-visual-studio"></a>Logowanie do programu Visual Studio

Zaloguj się do programu Visual Studio za pomocą konta Microsoft lub konta organizacji. Nazwa użytkownika powinna być wyświetlana w górnym rogu okna, podobnie jak w tym przypadku:

![Aktualnie zalogowany użytkownik](../ide/media/vs2015_username.png)

### <a name="access-your-azure-account-in-server-explorer"></a>Uzyskiwanie dostępu do konta platformy Azure w Eksploratorze serwera

Aby otworzyć Eksploratora serwera, wybierz pozycję **Wyświetl** > **Eksploratora serwera** (lub, jeśli używasz "Ogólnych" ustawień [środowiska,](../ide/environment-settings.md)naciśnij **klawisz Ctrl**+**Alt**+**S**). Rozwiń węzeł **platformy Azure** i zwróć uwagę, że zawiera zasoby dostępne na koncie platformy Azure skojarzone z kontem, które zostało użyte do zalogowania się do programu Visual Studio. Wygląda podobnie do następującego obrazu:

![Eksplorator serwera z rozwiniętym węzłem platformy Azure](../ide/media/work-with-multiple-user-accounts/server-explorer.png)

Przy pierwszym użyciu programu Visual Studio na dowolnym określonym urządzeniu okno dialogowe zawiera tylko subskrypcje zarejestrowane na koncie, które się zalogowano. Dostęp do zasobów dla innych kont można uzyskać bezpośrednio z **Eksploratora serwera,** klikając prawym przyciskiem myszy węzeł **platformy Azure,** wybierając pozycję **Zarządzaj subskrypcjami i filtruj subskrypcje,** a następnie dodając konta z kontroli selektora kont. Następnie możesz wybrać inne konto, w razie potrzeby, klikając strzałkę w dół i wybierając z listy kont. Po wybraniu konta można dostosować subskrypcje w ramach tego konta do wyświetlenia w **Eksploratorze serwera**.

![Okno dialogowe Zarządzanie subskrypcjami platformy Azure](../ide/media/vs2015_manage_subs.png)

Przy następnym **otwarciu Eksploratora serwera**zostaną wyświetlone zasoby dla tej subskrypcji.

### <a name="access-your-azure-account-via-add-connected-service-dialog"></a>Dostęp do konta platformy Azure za pomocą okna dialogowego Dodawanie połączonej usługi

1. Otwórz istniejący projekt lub utwórz nowy projekt.

1. Wybierz węzeł projektu w **Eksploratorze rozwiązań,** a następnie kliknij prawym przyciskiem myszy i wybierz polecenie **Dodaj** > **połączoną usługę**.

   Kreator **Dodaj usługę połączoną** zostanie wyświetlony i wyświetli listę usług na koncie platformy Azure skojarzonych z kontem personalizacji programu Visual Studio. Nie musisz logować się oddzielnie na platformie Azure. Jednak musisz zalogować się do innych kont przy pierwszej próbie uzyskania dostępu do ich zasobów z innego komputera.

### <a name="access-azure-active-directory-in-a-web-project"></a>Uzyskiwanie dostępu do usługi Azure Active Directory w projekcie sieci Web

Usługa Azure Active Directory (AAD) umożliwia obsługę logowania jednokrotnego użytkownika końcowego ASP.NET aplikacji sieci Web MVC lub uwierzytelniania usługi AD w usługach interfejsu API sieci Web. Uwierzytelnianie domeny różni się od uwierzytelniania kont poszczególnych użytkowników. Użytkownicy, którzy mają dostęp do domeny usługi Active Directory, mogą łączyć się z aplikacjami sieci Web za pomocą istniejących kont usługi AAD. Aplikacje usługi Office 365 mogą również korzystać z uwierzytelniania domeny.

::: moniker range="vs-2017"

Aby to zobaczyć w akcji, utwórz nowy **projekt ASP.NET Core Web Application.** W oknie dialogowym **Nowa ASP.NET Podstawowa aplikacja sieci Web** wybierz szablon aplikacji sieci **Web,** a następnie wybierz polecenie **Zmień uwierzytelnianie**.

::: moniker-end

::: moniker range=">=vs-2019"

Aby to zobaczyć w akcji, utwórz nowy **projekt ASP.NET Core Web Application.** Na stronie **Tworzenie nowej ASP.NET podstawowej aplikacji sieci Web** wybierz szablon aplikacji sieci **Web,** a następnie wybierz pozycję **Zmień** w obszarze **Uwierzytelnianie**.

::: moniker-end

Zostanie wyświetlone okno dialogowe **Zmiana uwierzytelniania,** w którym można wybrać rodzaj uwierzytelniania, którego chcesz użyć w aplikacji.

![Okno dialogowe Zmienianie uwierzytelniania dla ASP.NET](../ide/media/vs2015_change_authentication.png)

Aby uzyskać więcej informacji na temat różnych rodzajów uwierzytelniania w ASP.NET, zobacz [Tworzenie projektów sieci Web ASP.NET w programie Visual Studio](/aspnet/visual-studio/overview/2013/creating-web-projects-in-visual-studio#authentication-methods).

### <a name="access-your-azure-devops-organization"></a>Uzyskiwanie dostępu do organizacji DevOps platformy Azure

W menu głównym wybierz **pozycję Team** > **Manage Connections** , aby otworzyć okno **Eksplorator zespołu — Połącz.** Wybierz pozycję **Zarządzaj połączeniami** > **Połącz z projektem**. W oknie **dialogowym Połącz** z projektem wybierz projekt z listy (lub wybierz **pozycję Dodaj serwer TFS** i wprowadź adres URL do serwera). Po wybraniu adresu URL użytkownik jest zalogowany bez konieczności ponownego wniesienia poświadczeń.

Aby uzyskać więcej informacji, zobacz [Łączenie się z projektami w Eksploratorze zespołu](connect-team-project.md).

## <a name="add-an-additional-account-to-visual-studio"></a>Dodawanie dodatkowego konta do programu Visual Studio

Aby dodać dodatkowe konto do programu Visual Studio:

1. Wybierz **pozycję Ustawienia** > **konta**plików .

1. W obszarze **Wszystkie konta**wybierz pozycję **Dodaj konto**.

1. Na stronie **Zaloguj się na konto** wybierz konto lub wybierz pozycję Użyj innego **konta**. Postępuj zgodnie z instrukcjami, aby wprowadzić nowe poświadczenia konta.

(Opcjonalnie) Teraz możesz przejść do **Eksploratora serwera** i wyświetlić usługi platformy Azure skojarzone z właśnie dodanym kontem. W **Eksploratorze serwera**kliknij prawym przyciskiem myszy węzeł **platformy Azure** i wybierz polecenie **Zarządzaj subskrypcjami i filtruj**. Wybierz nowe konto, klikając strzałkę listy rozwijanej obok bieżącego konta, a następnie wybierz subskrypcje, które mają być wyświetlane w **Eksploratorze serwera**. Powinny być widoczne wszystkie usługi skojarzone z określoną subskrypcją. Mimo że nie jesteś aktualnie zalogowany do programu Visual Studio przy za pomocą drugiego konta, użytkownik jest zalogowany do usług i zasobów tego konta. To samo dotyczy **usługi Project** > **Add Connected Service** i **Team** > **Connect z team foundation server**.

### <a name="add-an-account-using-device-code-flow"></a>Dodawanie konta przy użyciu przepływu kodu urządzenia

W niektórych przypadkach nie można zalogować się ani dodać konta w zwykły sposób. Może się tak zdarzyć, jeśli program Internet Explorer jest zablokowany z jakiegoś powodu lub jeśli sieć znajduje się za zaporą. Aby obejść ten temat, można włączyć *przepływ kodu urządzenia,* aby dodać konto lub ponownie uwierzytelnić konto. Przepływ kodu urządzenia umożliwia logowanie się przy użyciu&mdash;innej przeglądarki lub na innym komputerze fizycznym lub wirtualnym (VM).

Aby zalogować się przy użyciu przepływu kodu urządzenia:

1. Otwórz stronę [**Konta**](reference/accounts-environment-options-dialog-box.md) w obszarze**Środowisko opcji** > **Environment** **narzędzia** > , a następnie wybierz pozycję **Włącz przepływ kodu urządzenia podczas dodawania lub ponownego uwierzytelniania konta**. Wybierz **przycisk OK,** aby zamknąć strony opcji.

1. Wybierz pozycję**Ustawienia konta** **plików,** > aby otworzyć stronę zarządzania kontem.

1. Wybierz **pozycję Dodaj konto w** obszarze Wszystkie **konta**.

   Okno dialogowe zawiera adres URL i kod do wklejenia do przeglądarki internetowej.

   ![Adres URL i kod przepływu kodu urządzenia](media/work-with-multiple-user-accounts/device-login-code.png)

1. Naciśnij **klawisz Ctrl**+**C,** aby skopiować tekst okna dialogowego, a następnie wybierz przycisk **OK,** aby zamknąć okno dialogowe. Wklej skopiowany tekst do edytora tekstu, takiego jak Notatnik. Ułatwia to skopiowanie kodu w następnym kroku.

1. Przejdź do adresu URL logowania urządzenia na komputerze lub przeglądarce internetowej, którego chcesz użyć do zalogowania się do programu Visual Studio, a następnie wklej lub wprowadź kod skopiowany do pola z **napisem Kod**.

   Nazwa aplikacji **Visual Studio** powinna pojawić się w dalszej stronie.

1. W **obszarze Visual Studio**wybierz pozycję **Kontynuuj**.

   ![device-login-page.png](media/work-with-multiple-user-accounts/device-login-page.png)

1. Postępuj zgodnie z instrukcjami, aby wprowadzić poświadczenia konta.

   Zostanie wyświetlona strona informująca o zalogowaniu się do programu Visual Studio na urządzeniu i o tym, że można zamknąć okno przeglądarki.

   ![Pełne logowanie się w programie Visual Studio za pośrednictwem przeglądarki](media/work-with-multiple-user-accounts/sign-in-browser-complete.png)

1. Wróć do strony zarządzania kontem w programie Visual Studio, a zobaczysz nowo dodane konto wymienione w obszarze **Wszystkie konta**. Wybierz **pozycję Zamknij**.

## <a name="see-also"></a>Zobacz też

- [Logowanie do programu Visual Studio](signing-in-to-visual-studio.md)
- [Logowanie się do programu Visual Studio dla komputerów Mac](/visualstudio/mac/signing-in)
