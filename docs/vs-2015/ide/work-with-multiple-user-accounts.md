---
title: Praca z wieloma kontami użytkownika | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
ms.assetid: b73c865c-74e0-420e-89cc-43524f4aafd0
caps.latest.revision: 17
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 5d269cdb4fe84820174ded9c477fc3c9f917b0b5
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54802645"
---
# <a name="work-with-multiple-user-accounts"></a>Praca z wieloma kontami użytkowników
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Jeśli masz wiele kont Microsoft i/lub konta służbowego lub szkolnego, można dodać je wszystkie do programu Visual Studio, tak, aby dostęp do zasobów z dowolnego konta bez konieczności logowania się do niego oddzielnie. W dniu Visual Studio 2015 RTM usługi platformy Azure, usługa Application Insights, Team Foundation Server i usługi Office 365 obsługują usprawnione środowisko logowania. Dodatkowe usługi może stają się dostępne, gdy czas.  
  
 Po dodaniu wielu kont na jednej maszynie, ten zestaw kont "wędrują" z Tobą Jeśli logujesz się do programu Visual Studio na innym komputerze. Należy zauważyć, że chociaż nazwy kont są przekazywane, poświadczenia nie są. W związku z tym można jest monitowany o podanie poświadczeń dla tych innych kont próby użycia zasobów na nowej maszynie po raz pierwszy.  
  
 W tym instruktażu przedstawiono sposób dodawania wielu kont w programie Visual Studio, a następnie jak sprawdzić, czy zasoby, które są dostępne z tych kont są odzwierciedlane w umieszcza takich jak **Dodaj podłączoną usługę** okno dialogowe, **Eksploratora serwera** , i **Team Explorer**.  
  
#### <a name="sign-in-to-visual-studio"></a>Logowanie do programu Visual Studio  
  
1.  Zaloguj się do programu Visual Studio 2015 za pomocą konta Microsoft lub kontem organizacyjnym. Powinny zostać wyświetlone swoją nazwę użytkownika, które zostaną uwzględnione w prawym górnym rogu okna, podobny do następującego:  
  
     ![Currentlly zalogowanego użytkownika](../ide/media/vs2015-username.png "VS2015_UserName")  
  
### <a name="access-your-azure-account-in-server-explorer"></a>Dostęp do konta platformy Azure w Eksploratorze serwera  
 Naciśnij klawisz **Ctrl + Alt + S** otworzyć **Eksploratora serwera**. Kliknij ikonę platformy Azure i jego rozszerzeniu powinien zostać wyświetlony zasobów dostępnych na koncie platformy Azure, który jest skojarzony z Identyfikatorem używanym do logowania do programu Visual Studio 2015. Powinien wyglądać następująco, chyba że zostanie wyświetlony własne zasoby nie Pan Guido firmy:  
  
 ![Rozwinięty węzeł narzędzi Azure przedstawiający Eksploratora serwera](../ide/media/vs2015-serverexplorer.png "VS2015_ServerExplorer")  
  
 Po raz pierwszy używasz programu Visual Studio na dowolnym urządzeniu określonego okna dialogowego zostaną wyświetlone tylko subskrypcje zarejestrowany w identyfikatorze, którego zalogowano się do środowiska IDE, za pomocą. Dostęp do zasobów dla każdego z innych kont, bezpośrednio z **Eksploratora serwera** , kliknięcie prawym przyciskiem myszy węzeł platformy Azure i wybierając pozycję **subskrypcji filtru i Zarządzaj** i dodać Twojego konta z Formant selektora konta. Następnie możesz wybrać inne konto, jeśli to konieczne, klikając strzałkę w dół, a następnie wybierając z listy kont. Po wybraniu konta, możesz wybrać subskrypcje, które w ramach tego konta, które mają być wyświetlane w Eksploratorze serwera.  
  
 ![Zarządzanie subskrypcjami platformy Azure w oknie dialogowym](../ide/media/vs2015-manage-subs.png "vs2015_manage_subs")  
  
 Przy następnym otwarciu Eksploratora serwera są wyświetlane zasoby dla tej subskrypcji.  
  
### <a name="access-your-azure-account-via-add-connected-service-dialog"></a>Dostęp do konta platformy Azure za pomocą okna dialogowego Dodawanie podłączonej usługi  
  
1.  Utwórz projekt aplikacji uniwersalnej w języku C#.  
  
2.  Kliknij prawym przyciskiem myszy węzeł projektu w Eksploratorze rozwiązań i wybierz polecenie **Dodaj > usługi połączonej**. Dodaj podłączoną usługę kreatora pojawia się i zostanie wyświetlony identyfikator listy usług na koncie platformy Azure, który jest skojarzony z identyfikatora logowania programu Visual Studio. Należy pamiętać, że nie trzeba osobno logowanie do platformy Azure. Jednakże należy zalogować się do innych kont spróbujesz uzyskać dostęp do zasobów z danego komputera po raz pierwszy.  
  
    > [!WARNING]
    >  Jeśli po raz pierwszy tworzysz Store app w programie Visual Studio 2015 na określonym komputerze, zostanie wyświetlony monit Włącz urządzenie w trybie projektowania, przechodząc do **ustawienia &#124; . Aktualizacje i zabezpieczenia &#124; dla deweloperów** na tym komputerze. Aby uzyskać więcej informacji, zobacz [Włącz swoje urządzenie do tworzenia](https://msdn.microsoft.com/library/windows/apps/dn706236.aspx).  
  
###  <a name="access_azure"></a> Dostęp do usługi Azure Active Directory w projekcie sieci Web  
 Usługa Azure AD umożliwia obsługę użytkownika końcowego logowania jednokrotnego w aplikacjach sieci web platformy ASP.NET MVC lub uwierzytelniania AD w usługach interfejsu API sieci Web. Uwierzytelnianie domeny różni się od uwierzytelniania konta użytkownika; Użytkownicy, którzy mają dostęp do domeny usługi Active Directory można użyć istniejących kont usługi Azure AD, połączyć się z aplikacji sieci web. Aplikacje usługi Office 365 można również użyć uwierzytelniania przez domenę. Aby to zobaczyć w działaniu, tworzenie aplikacji sieci web (**pliku > Nowy Projekt > C# > chmura > Aplikacja sieci Web ASP.NET**). W oknie dialogowym Nowy projekt ASP.NET wybierz **Zmień uwierzytelnianie**. Kreatora uwierzytelniania pojawia się i pozwala wybrać rodzaj uwierzytelniania do użycia w aplikacji.  
  
 ![Okna dialogowego uwierzytelnienia zmiany w technologii ASP.NET](../ide/media/vs2015-change-authentication.png "VS2015_change_authentication")  
  
 Aby uzyskać więcej informacji na temat różnych rodzajów uwierzytelniania w programie ASP.NET: zobacz [tworzenia projektów sieci Web platformy ASP.NET w programie Visual Studio 2013](http://www.asp.net/visual-studio/overview/2013/creating-web-projects-in-visual-studio#orgauth) (informacje o uwierzytelnianiu jest nadal istotne dla programu Visual Studio 2015).  
  
### <a name="access-your-visual-studio-team-services-account"></a>Dostęp do konta programu Visual Studio Team Services  
 W menu głównym wybierz **zespołu > Połącz z Team Foundation Server** aby przywołać **Team Explorer** okna. Kliknij pozycję **Wybierz projekty zespołowe**, a następnie w polu listy **wybierz Team Foundation Server**, powinien zostać wyświetlony adres URL dla konta usługi Visual Studio Team Services. Po wybraniu adresu URL możesz będą rejestrowane w bez konieczności ponownego wprowadzania poświadczeń.  
  
## <a name="add-a-second-user-account-to-visual-studio"></a>Dodawanie drugiego konta użytkownika w programie Visual Studio  
 Kliknij strzałkę w dół obok swojej nazwy użytkownika w prawym górnym rogu programu Visual Studio. Następnie kliknij pozycję **ustawienia konta** elementu menu. **Menedżerem** okno dialogowe pojawia się i wyświetla konta podczas logowania. Kliknij przycisk **Dodaj konto** linku w lewej dolnej części okna dialogowego, aby dodać nowe konto Microsoft lub nowej pracy lub konta służbowego.  
  
 ![Visual Studio account picker](../ide/media/vs2015-acct-picker.png "VS2015_acct_picker")  
  
 Postępuj zgodnie z monitami, aby wprowadzić nowe poświadczenia konta. Poniższa ilustracja przedstawia Menedżera konta, po użytkownik doda jego konto służbowe Contoso.com.  
  
 ![Menedżerem](../ide/media/vs2015-accountmanager.gif "VS2015_AccountManager")  
  
## <a name="revisit-the-add-connected-services-wizard-and-server-explorer"></a>Ponownie Dodaj usług połączonych kreatora i Eksplorator serwera  
 Teraz przejdź do **Eksploratora serwera** ponownie, kliknij prawym przyciskiem myszy na węzeł platformy Azure i wybierz polecenie **zarządzanie i Filtruj subskrypcje**. Wybierz nowe konto, klikając strzałkę listy rozwijanej obok bieżącego konta, a następnie wybierz subskrypcje, które mają być wyświetlane w Eksploratorze serwera. Powinny być widoczne wszystkie usługi, które są skojarzone z określonej subskrypcji. Mimo że nie aktualnie zalogowano Cię do środowiska IDE Visual Studio przy użyciu drugiego konta, zalogowano Cię do tego konta usług i zasobów. Dotyczy to także **Projekt > Dodaj podłączoną usługę** i **zespołu > Połącz z Team Foundation Server**.
