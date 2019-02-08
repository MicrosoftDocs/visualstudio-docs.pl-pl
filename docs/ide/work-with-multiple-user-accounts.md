---
title: Praca z wieloma kontami użytkowników
ms.date: 12/10/2018
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c910ab867be379264464650cef6bec00fc9d82f9
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2019
ms.locfileid: "55933395"
---
# <a name="work-with-multiple-user-accounts"></a>Praca z wieloma kontami użytkowników

Jeśli masz wiele kont Microsoft i/lub konta służbowego lub szkolnego, można dodać je wszystkie do programu Visual Studio, tak, aby dostęp do zasobów z dowolnego konta bez konieczności logowania się do niego oddzielnie. Wszystkie usługi platformy Azure, usługa Application Insights, DevOps platformy Azure i usługi Office 365 obsługują usprawnione środowisko logowania.

Po dodaniu wielu kont na jednym komputerze, czy zbiór kont uzyskuje mobilny dostęp z Tobą Jeśli logujesz się do programu Visual Studio na innym komputerze.

> [!NOTE]
> Mimo że mobilny dostęp do nazwy konta, nie są poświadczenia. Zostanie wyświetlony monit o podanie poświadczeń dla tych innych kont próby użycia zasobów na nowej maszynie po raz pierwszy.

W tym artykule pokazano, jak dodać wiele kont w programie Visual Studio. On również pokazano, jak można znaleźć w zasobach, które są dostępne z tych kont w miejscach takich jak **Dodaj podłączoną usługę** okno dialogowe, **Eksploratora serwera**, i **Team Explorer**.

## <a name="sign-in-to-visual-studio"></a>Logowanie do programu Visual Studio

Zaloguj się do programu Visual Studio za pomocą konta Microsoft lub kontem organizacyjnym. Powinny zostać wyświetlone swoją nazwę użytkownika, które pojawiają się w prawym górnym rogu okna, podobny do następującego:

![Aktualnie zalogowany użytkownik](../ide/media/vs2015_username.png)

### <a name="access-your-azure-account-in-server-explorer"></a>Dostęp do konta platformy Azure w Eksploratorze serwera

Naciśnij klawisz **Ctrl**+**Alt**+**S** otworzyć **Eksploratora serwera**. Rozwiń **Azure** węzeł i zwróć uwagę, że zawiera on zasobów dostępnych na koncie platformy Azure skojarzoną z kontem Uruchom jako używane do logowania do programu Visual Studio. Będzie on podobny do poniższej ilustracji:

![Rozwinięte Eksploratora serwera za pomocą węzła platformy Azure](../ide/media/work-with-multiple-user-accounts/server-explorer.png)

Po raz pierwszy używasz programu Visual Studio na dowolnym urządzeniu określonych, okno dialogowe wyświetla tylko subskrypcje zarejestrowany w ramach konta, który podpisany przy użyciu. Dostęp do zasobów dla każdego z innych kont, bezpośrednio z **Eksploratora serwera** przez kliknięcie prawym przyciskiem myszy **Azure** węzła, wybierając **zarządzanie i filtr subskrypcji**, a następnie dodając konta z formant selektora konta. Następnie możesz wybrać inne konto, jeśli to konieczne, klikając strzałkę w dół, a następnie wybierając z listy kont. Po wybraniu konta, możesz dostosować określone subskrypcje w ramach tego konta, aby wyświetlić **Eksploratora serwera**.

![Zarządzanie subskrypcjami platformy Azure w oknie dialogowym](../ide/media/vs2015_manage_subs.png)

Gdy następnym razem otworzysz **Eksploratora serwera**, wyświetlane są zasoby dla tej subskrypcji.

### <a name="access-your-azure-account-via-add-connected-service-dialog"></a>Dostęp do konta platformy Azure za pomocą okna dialogowego Dodawanie podłączonej usługi

1. Otwórz istniejący projekt lub Utwórz nowy projekt.

1. Wybierz węzeł projektu w **Eksploratora rozwiązań**, a następnie kliknij prawym przyciskiem myszy i wybierz **Dodaj** > **podłączoną usługę**.

   **Dodaj podłączoną usługę** kreatora pojawia się i zostanie wyświetlony na liście usług na koncie platformy Azure skojarzoną z kontem programu Visual Studio personalizacji. Nie musisz oddzielnie logowanie do platformy Azure. Jednak należy zalogować się do innych kont spróbujesz uzyskać dostęp do zasobów na innej maszynie po raz pierwszy.

### <a name="access-azure-active-directory-in-a-web-project"></a>Dostęp do usługi Azure Active Directory w projekcie sieci Web

Usługa Azure Active Directory (AAD) umożliwia obsługę użytkownika końcowego logowania jednokrotnego w aplikacjach sieci web platformy ASP.NET MVC lub uwierzytelniania AD w usługach interfejsu API sieci web. Uwierzytelnianie domeny różni się od uwierzytelniania konta użytkownika. Użytkownicy, którzy mają dostęp do domeny usługi Active Directory można użyć istniejących kont usługi AAD, połączyć się z aplikacji sieci web. Aplikacje usługi Office 365 można również użyć uwierzytelniania przez domenę.

Aby to zobaczyć w działaniu, tworzenie aplikacji sieci web (**pliku** > **nowy projekt** > **C#** > **chmury**  >  **Aplikacji sieci Web ASP.NET**). W **nowy projekt ASP.NET** okno dialogowe, wybierz **Zmień uwierzytelnianie**. Kreatora uwierzytelniania pojawia się i pozwala wybrać rodzaj uwierzytelniania do użycia w aplikacji.

![Okna dialogowego uwierzytelnienia zmiany dla platformy ASP.NET](../ide/media/vs2015_change_authentication.png)

Aby uzyskać więcej informacji na temat różnych rodzajów uwierzytelniania w programie ASP.NET: zobacz [projekty sieci web ASP.NET tworzenie w programie Visual Studio](/aspnet/visual-studio/overview/2013/creating-web-projects-in-visual-studio#authentication-methods).

### <a name="access-your-azure-devops-organization"></a>Dostęp do Twojej organizacji DevOps platformy Azure

W menu głównym wybierz **zespołu** > **Zarządzaj połączeniami** otworzyć **Team Explorer — łączenie** okna. Wybierz **Zarządzanie połączeniami** > **Połącz z projektem**. W **nawiązywanie połączenia z projektem** okno dialogowe, wybierz projekt z listy (lub wybierz **Dodaj serwer TFS** i wprowadź adres URL do serwera). Po wybraniu adresu URL, zalogowano Cię bez konieczności ponownego wprowadzania poświadczeń.

Aby uzyskać więcej informacji, zobacz [Połącz z projektami w programie Team Explorer](connect-team-project.md).

## <a name="add-an-additional-account-to-visual-studio"></a>Dodaj dodatkowe konto programu Visual Studio

Aby dodać dodatkowe konto programu Visual Studio:

1. Wybierz **pliku** > **ustawienia konta**.

1. W obszarze **wszystkich kont**, wybierz **Dodaj konto**.

1. Na **Zaloguj się do swojego konta** strony, wybierz konto lub wybierz **Użyj innego konta**. Postępuj zgodnie z monitami, aby wprowadzić nowe poświadczenia konta.

(Opcjonalnie) Teraz możesz przejść do **Eksploratora serwera** i zapoznaj się z usługami platformy Azure, skojarzone z kontem, właśnie został dodany. W **Eksploratora serwera**, kliknij prawym przyciskiem myszy **Azure** węzeł i wybierz polecenie **subskrypcji filtru i Zarządzaj**. Wybierz nowe konto, klikając strzałkę listy rozwijanej obok bieżącego konta, a następnie wybierz subskrypcje, które mają być wyświetlane w **Eksploratora serwera**. Powinny być widoczne wszystkie usługi, które są skojarzone z określonej subskrypcji. Nawet jeśli użytkownik nie jest obecnie zalogowany w programie Visual Studio przy użyciu drugiego konta, zalogowano Cię do tego konta usług i zasobów. Dotyczy to także **projektu** > **Dodaj podłączoną usługę** i **zespołu** > **nawiązywanie połączenia z Team Foundation Server**.

### <a name="add-an-account-using-device-code-flow"></a>Dodaj konto usługi przy użyciu przepływu kodu urządzenia

W niektórych przypadkach nie można zalogować lub dodać konto w zwykły sposób. Może to nastąpić, jeśli program Internet Explorer jest zablokowany z jakiegoś powodu, czy sieć jest za zaporą. Aby obejść ten problem, można włączyć *przepływ kodu urządzenia* do dodania konta lub ponownie uwierzytelniać konta. Przepływ kodu urządzenia umożliwia logowanie przy użyciu innej przeglądarki lub na innym komputerze&mdash;fizycznych lub wirtualnych (VM).

Aby zarejestrować się przy użyciu przepływu kodu urządzenia:

1. Otwórz [ **kont** ](reference/accounts-environment-options-dialog-box.md) strony w obszarze **narzędzia** > **opcje** > **środowiska**, a następnie wybierz pozycję **Włącz przepływ kodu urządzenia podczas dodawania lub ponownego uwierzytelniania konta**. Wybierz **OK** zamknąć stron opcji.

1. Wybierz **pliku** > **ustawienia konta** o otwarcie strony zarządzania kontem.

1. Wybierz **Dodaj konto** w obszarze **wszystkich kont**.

   Okno dialogowe zawiera adres URL i kod, aby wkleić w przeglądarce sieci web.

   ![Adres URL przepływu kodu urządzenia i kod](media/work-with-multiple-user-accounts/device-login-code.png)

1. Naciśnij klawisz **Ctrl**+**C** skopiować tekst z okna dialogowego, a następnie wybierz polecenie **OK** aby zamknąć okno dialogowe. Wklej tekst, który został skopiowany do edytora tekstów, takiego jak Notatnik. Dzięki temu można łatwiej będzie skopiować kod w następnym kroku.

1. Przejdź do adresu URL logowania urządzenia w przeglądarce komputera lub sieci web, którego chcesz użyć, aby zalogować się do programu Visual Studio, a następnie wklej lub wprowadź kod, w polu, które zostały skopiowane **kodu**.

   **Programu Visual Studio** nazwy aplikacji powinna zostać wyświetlona dalej na dół na stronie.

1. W obszarze **programu Visual Studio**, wybierz **Kontynuuj**.

   ![device-login-page.png](media/work-with-multiple-user-accounts/device-login-page.png)

1. Postępuj zgodnie z monitami, aby wprowadzić swoje poświadczenia konta.

   Zostanie wyświetlona strona z informacją, że logujesz się do programu Visual Studio na twoim urządzeniu i zamknięcie okna przeglądarki.

   ![Program Visual Studio Zaloguj się za pośrednictwem przeglądarki ukończone](media/work-with-multiple-user-accounts/sign-in-browser-complete.png)

1. Wróć do strony zarządzania kontem w programie Visual Studio, a zobaczysz nowo dodane konto, na liście **wszystkich kont**. Wybierz **Zamknij**.

## <a name="see-also"></a>Zobacz także

- [Logowanie do programu Visual Studio](signing-in-to-visual-studio.md)
- [Zaloguj się do programu Visual Studio dla komputerów Mac](/visualstudio/mac/signing-in)
