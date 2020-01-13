---
title: Pracuj z wieloma kontami użytkowników | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
ms.assetid: b73c865c-74e0-420e-89cc-43524f4aafd0
caps.latest.revision: 17
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 7dc2ba585c500fe045d143a2b8baa2d193466fdf
ms.sourcegitcommit: 939407118f978162a590379997cb33076c57a707
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/13/2020
ms.locfileid: "75917784"
---
# <a name="work-with-multiple-user-accounts"></a>Praca z wieloma kontami użytkowników
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Jeśli masz wiele kont Microsoft i/lub kont służbowych, możesz dodać je wszystkie do programu Visual Studio, aby uzyskać dostęp do zasobów z dowolnego konta bez konieczności logowania się do niego osobno. Począwszy od programu Visual Studio 2015 RTM, platformy Azure, Application Insights, Team Foundation Server i pakietu Office 365 obsługują usprawnione środowisko logowania. Dodatkowe usługi mogą stać się dostępne jako czas przekroczenia czasu.

 Po dodaniu wielu kont na jednej maszynie ten zbiór kont zostanie przemobilny, jeśli zalogujesz się do programu Visual Studio na innym komputerze. Należy pamiętać, że chociaż nazwy kont są przenoszone, poświadczenia nie są przekazywane. W związku z tym podczas pierwszej próby użycia zasobów na nowym komputerze zostanie wyświetlony monit o podanie poświadczeń dla tych kont.

 W tym instruktażu pokazano, jak dodać wiele kont do programu Visual Studio i jak sprawdzić, czy zasoby dostępne z tych kont są odzwierciedlone w miejscach, takich jak okno dialogowe **Dodawanie podłączonej usługi** , **Eksplorator serwera**i **Team Explorer**.

#### <a name="sign-in-to-visual-studio"></a>Logowanie do programu Visual Studio

1. Zaloguj się do programu Visual Studio 2015 przy użyciu konto Microsoft lub konta organizacyjnego. Twoja nazwa użytkownika powinna zostać wyświetlona w prawym górnym rogu okna, podobnie jak w przypadku:

     ![Zalogowany użytkownik Currentlly](../ide/media/vs2015-username.png "VS2015_UserName")

### <a name="access-your-azure-account-in-server-explorer"></a>Uzyskaj dostęp do konta platformy Azure w Eksplorator serwera
 Naciśnij **kombinację klawiszy CTRL + ALT + S** , aby otworzyć **Eksplorator serwera**. Kliknij ikonę platformy Azure i po jej rozszerzeniu powinny zostać wyświetlone zasoby dostępne na koncie platformy Azure skojarzone z IDENTYFIKATORem użytym do zalogowania się do programu Visual Studio 2015. Powinien on wyglądać podobnie do tego, z tą różnicą, że zobaczysz własne zasoby, a nie Mr. Guido:

 ![Eksplorator serwera wyświetlania rozwiniętego węzła narzędzi platformy Azure](../ide/media/vs2015-serverexplorer.png "VS2015_ServerExplorer")

 Przy pierwszym użyciu programu Visual Studio na dowolnym konkretnym urządzeniu w oknie dialogowym zostaną wyświetlone tylko subskrypcje zarejestrowane w ramach identyfikatora, który został zalogowany do środowiska IDE za pomocą programu. Aby uzyskać dostęp do zasobów dla dowolnego innego konta bezpośrednio z **Eksplorator serwera** , kliknij prawym przyciskiem myszy węzeł platformy Azure, a następnie wybierz pozycję **Zarządzaj subskrypcjami** i Dodaj swoje konta z poziomu kontrolki wyboru konta. W razie potrzeby możesz wybrać inne konto, klikając strzałkę w dół i wybierając pozycję z listy kont. Po wybraniu konta możesz wybrać subskrypcje w ramach tego konta, które mają być wyświetlane w Eksplorator serwera.

 ![Okno dialogowe Zarządzanie subskrypcjami platformy Azure](../ide/media/vs2015-manage-subs.png "vs2015_manage_subs")

 Przy następnym otwarciu Eksplorator serwera zostaną wyświetlone zasoby dla tej subskrypcji.

### <a name="access-your-azure-account-via-add-connected-service-dialog"></a>Uzyskiwanie dostępu do konta platformy Azure za pomocą okna dialogowego Dodawanie połączonej usługi

1. Utwórz projekt aplikacji uniwersalnej w C#programie.

2. Kliknij prawym przyciskiem myszy węzeł projektu w Eksplorator rozwiązań i wybierz polecenie **dodaj > połączoną usługę**. Zostanie wyświetlony Kreator dodawania usługi połączonej z listą usług na koncie platformy Azure skojarzonym z IDENTYFIKATORem logowania programu Visual Studio. Pamiętaj, że nie musisz logować się oddzielnie na platformie Azure. Należy jednak zalogować się do innych kont przy pierwszej próbie uzyskania dostępu do zasobów z danego komputera.

    > [!WARNING]
    > Jeśli tworzysz aplikację ze sklepu w programie Visual Studio 2015 na określonym komputerze po raz pierwszy, zostanie wyświetlony monit o włączenie tego urządzenia do trybu deweloperskiego, przechodząc do **ustawień &#124; . Aktualizacje i zabezpieczenia &#124; dla deweloperów** na komputerze. Aby uzyskać więcej informacji, zobacz [Włączanie urządzenia na potrzeby programowania](https://msdn.microsoft.com/library/windows/apps/dn706236.aspx).

### <a name="access_azure"></a>Dostęp do Azure Active Directory w projekcie sieci Web
 Usługa Azure AD umożliwia obsługę logowania jednokrotnego dla użytkowników końcowych w aplikacjach sieci Web ASP.NET MVC lub uwierzytelnianie usługi AD w usługach interfejsu API sieci Web. Uwierzytelnianie domeny różni się od uwierzytelniania poszczególnych kont użytkowników. Użytkownicy mający dostęp do domeny Active Directory mogą korzystać z istniejących kont usługi Azure AD w celu łączenia się z aplikacjami sieci Web. Aplikacje pakietu Office 365 mogą również korzystać z uwierzytelniania domeny. Aby wyświetlić tę akcję, Utwórz aplikację sieci Web (**plik > nowym projekcie > C# > aplikacji sieci web w chmurze > ASP.NET**). W oknie dialogowym Nowy projekt ASP.NET wybierz pozycję **Zmień uwierzytelnianie**. Zostanie wyświetlony Kreator uwierzytelniania i pozwala wybrać rodzaj uwierzytelniania, który ma być używany w aplikacji.

 ![Okno dialogowe Zmienianie uwierzytelniania dla ASP.NET](../ide/media/vs2015-change-authentication.png "VS2015_change_authentication")

 Aby uzyskać więcej informacji na temat różnych rodzajów uwierzytelniania w programie ASP.NET, zobacz [Tworzenie projektów sieci Web ASP.NET w Visual Studio 2013](/aspnet/visual-studio/overview/2013/creating-web-projects-in-visual-studio#orgauth) (informacje o uwierzytelnianiu są nadal istotne dla programu Visual Studio 2015).

### <a name="access-your-visual-studio-team-services-account"></a>Uzyskaj dostęp do konta Visual Studio Team Services
 Z menu głównego wybierz kolejno pozycje **zespół > Połącz z Team Foundation Server** , aby wyświetlić okno **Team Explorer** . Kliknij pozycję **Wybierz projekty zespołowe**, a następnie w polu listy w obszarze **Wybierz Team Foundation Server**powinien zostać wyświetlony adres URL konta Visual Studio Team Services. Po wybraniu adresu URL, który zostanie zalogowany, bez konieczności ponownego wprowadzania poświadczeń.

## <a name="add-a-second-user-account-to-visual-studio"></a>Dodawanie drugiego konta użytkownika do programu Visual Studio
 Kliknij strzałkę w dół obok swojej nazwy użytkownika w prawym górnym rogu programu Visual Studio. Następnie kliknij element menu **Ustawienia konta** . Zostanie wyświetlone okno dialogowe **Menedżer kont** zawierające konto, za pomocą którego zalogowano się. Kliknij link **Dodaj konto** w lewym dolnym rogu okna dialogowego, aby dodać nowe konto Microsoft lub nowe konto służbowe.

 ![Selektor konta programu Visual Studio](../ide/media/vs2015-acct-picker.png "VS2015_acct_picker")

 Postępuj zgodnie z monitami, aby wprowadzić nowe poświadczenia konta. Na poniższej ilustracji przedstawiono Menedżera kont po dodaniu przez użytkownika konta służbowego Contoso.com.

 ![Menedżer kont](../ide/media/vs2015-accountmanager.gif "VS2015_AccountManager")

## <a name="revisit-the-add-connected-services-wizard-and-server-explorer"></a>Ponownie odwiedź Kreatora dodawania podłączonych usług i Eksplorator serwera
 Teraz przejdź do **Eksplorator serwera** ponownie, kliknij prawym przyciskiem myszy węzeł platformy Azure, a następnie wybierz pozycję **Zarządzaj i Filtruj subskrypcje**. Wybierz nowe konto, klikając strzałkę listy rozwijanej obok bieżącego konta, a następnie wybierz subskrypcje, które mają być wyświetlane w Eksplorator serwera. Powinny zostać wyświetlone wszystkie usługi skojarzone z określoną subskrypcją. Mimo że obecnie nie zalogowano się do środowiska IDE programu Visual Studio przy użyciu drugiego konta, zalogowano się do usług i zasobów tego konta. Ta sama wartość dotyczy **projektu > Dodaj podłączoną usługę** i **zespół > połącz się z Team Foundation Server**.
