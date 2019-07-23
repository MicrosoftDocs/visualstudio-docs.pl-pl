---
title: Logowanie się do subskrypcji programu Visual Studio może zakończyć się niepowodzeniem podczas korzystania z aliasów | Microsoft Docs
author: evanwindom
ms.author: lank
manager: lank
ms.date: 07/19/2019
ms.topic: conceptual
description: Logowanie może zakończyć się niepowodzeniem w przypadku używania aliasów lub przyjaznych nazw
ms.openlocfilehash: 392b86699b1116f45ca75df3b611fff6a2aebc62
ms.sourcegitcommit: 485881e6ba872c7b28a7b17ceaede845e5bea4fe
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/22/2019
ms.locfileid: "68378022"
---
# <a name="signing-in-to-visual-studio-subscriptions-may-fail-when-using-aliases"></a>Logowanie się do subskrypcji programu Visual Studio może zakończyć się niepowodzeniem podczas korzystania z aliasów
W zależności od typu konta użytego do zalogowania się dostępne subskrypcje mogą nie być poprawnie wyświetlane podczas logowania do [https://my.visualstudio.com](https://my.visualstudio.com?wt.mc_id=o~msft~docs)programu. Jedną z potencjalnych przyczyn jest użycie "aliasów" lub "przyjaznych nazw" zamiast tożsamości logowania, do której przypisano subskrypcję. Jest to nazywane "aliasem".

## <a name="what-is-aliasing"></a>Co to jest aliasowanie?
Termin "aliasowanie" odnosi się do użytkowników, którzy mają różne tożsamości do logowania się do systemu Windows (lub Active Directory) oraz do uzyskiwania dostępu do poczty e-mail.

Aliasowanie może wystąpić, gdy firma ma usługę online firmy Microsoft dotyczącą logowania do katalogu, na przykład "JohnD@contoso.com", ale użytkownicy uzyskują dostęp do swoich kont e-mail przy użyciu aliasów lub przyjaznych nazw, takich jak "John.Doe@contoso.com". W przypadku wielu klientów, którzy zarządzają swoimi subskrypcjami za pośrednictwem usługi licencjonowania zbiorowego (VLSC), może to spowodować nieudane działanie logowania, ponieważ podany adres e-mail ('John.Doe@contoso.com') nie jest zgodny z adresem katalogu ('JohnD@contoso.com' ) wymagane do pomyślnego uwierzytelnienia za pomocą opcji "konto służbowe".

## <a name="as-an-administrator-what-options-do-i-have"></a>Jakie opcje są dostępne dla administratorów?
Jako administrator dostępne są dwie opcje, dzięki którym Subskrybenci mogą pomyślnie korzystać z funkcji [https://my.visualstudio.com](https://my.visualstudio.com?wt.mc_id=o~msft~docs)logowania.
- Pierwszą opcją (zalecane) jest użycie konta katalogu jako przypisanego adresu w witrynie Volume Licensing Service Center (VLSC). Aby uzyskać więcej informacji, zapoznaj się z sekcją [przypisywanie subskrybentów do konta katalogu](#assigning-subscribers-to-a-directory-account) w tym artykule.
- Druga opcja (mniej bezpieczna) polega na tym, że Subskrybenci mogą skojarzyć swój adres e-mail "służbowy" z kontem "osobisty" (vel Konto Microsoft lub MSA). Aby uzyskać więcej informacji, zobacz [Definiowanie konta służbowego jako sekcji konta osobistego](#defining-a-work-or-school-account-as-a-personal-account) w tym artykule.

> [!NOTE]
> Gdy Twoja firma zostanie zmigrowana do nowego [portalu administratora](https://manage.visualstudio.com)subskrypcji programu Visual Studio, będzie można skorzystać z zalet nowego środowiska administracyjnego, co umożliwi udostępnienie katalogu i adresów e-mail jako części profilu. Dowiedz się więcej o [migracji](https://support.microsoft.com/help/4013930/visual-studio-subscriptions-administrator-migration-details).

## <a name="assigning-subscribers-to-a-directory-account"></a>Przypisywanie subskrybentów do konta katalogu
We wszystkich przypadkach Menedżer subskrypcji w ramach usługi licencjonowania zbiorowego (VLSC) będzie musiał użyć adresu katalogu dla nowych subskrybentów lub zaktualizować adres e-mail dla subskrybentów "istniejących". Należy pamiętać, że użycie adresu katalogu oznacza, że nowi Subskrybenci nie otrzymają powitalnej wiadomości E-mail, a administrator musi powiadomić subskrybenta, że do nich przypisano subskrypcję. Po wykonaniu poniższych kroków można również skorzystać z [szablonu](#notifying-your-subscribers-with-directory-addresses) wiadomości e-mail w celu powiadomienia subskrybentów i pomocy w procesie logowania.

### <a name="adding-new-subscribers"></a>Dodawanie nowych subskrybentów
Wykonaj następujące kroki, aby dodać nowego subskrybenta z kontem katalogu.

1. Odwiedź witrynę [Volume Licensing Service Center](https://www.microsoft.com/Licensing/servicecenter/default.aspx) (VLSC) i zaloguj się.
2. Na stronie Administrator VLSC kliknij pozycję **subskrypcje** , a następnie opcję **subskrypcje programu Visual Studio**.

    > [!div class="mx-imgBorder"]
    > ![Menu subskrypcje](_img//vlsc/vlsc-subscriptions.png)

3. Kliknij **numer umowy** skojarzony z Visual Studio Subscription.

    > [!div class="mx-imgBorder"]
    > ![Wybierz umowę](_img/vlsc/vlsc-agreement.png)

4. Kliknij pozycję **Przypisz subskrypcję**.
5. Wybierz żądany **poziom subskrypcji**.
6. Sprawdź, czy masz dostępne subskrypcje do przypisania, a następnie kliknij przycisk **dalej**.
7. Wprowadź szczegóły subskrybenta i adres katalogu w polu adres E-mail, a następnie kliknij przycisk **dalej**.
8. Sprawdź poprawność informacji o subskrybencie i kliknij przycisk **Zakończ**.
9. Powiadom abonenta, że jego subskrypcja została zainicjowana przy użyciu poniższego [szablonu](#notifying-your-subscribers-with-directory-addresses).

### <a name="updating-an-existing-subscriber"></a>Aktualizowanie istniejącego subskrybenta
Wykonaj poniższe kroki, aby zaktualizować istniejącego subskrybenta przy użyciu konta katalogu.

1. Odwiedź witrynę [Volume Licensing Service Center](https://www.microsoft.com/Licensing/servicecenter/default.aspx) (VLSC) i zaloguj się.
2. Na stronach administracyjnych VLSC kliknij pozycję **subskrypcje** , a następnie opcję **subskrypcje programu Visual Studio**.
3. Kliknij **numer umowy** skojarzony z Visual Studio Subscription.
4. Kliknij **strzałkę w dół** na pasku wyszukiwania.
5. Wyszukaj subskrybenta przy użyciu pola "adres E-mail".
6. Na liście wyników kliknij **nazwisko** subskrybenta.
7. Kliknij przycisk **Edytuj**.
8. Zmień pole adres E-mail na żądany adres katalogu, a następnie kliknij przycisk **Zapisz**.
9. Powiadom abonenta, że jego subskrypcja została zainicjowana przy użyciu poniższego szablonu wiadomości e-mail.

### <a name="notifying-your-subscribers-with-directory-addresses"></a>Powiadamianie subskrybentów o adresach katalogu
Ponieważ powitalna wiadomość E-mail nie powiedzie się, skopiuj i wklej poniższy komunikat do wiadomości e-mail i Wyślij do subskrybenta. Zastąp% WORD% odpowiednimi informacjami dla każdego subskrybenta.

```
----------- Copy Below (Ctrl+C) -----------

Hello %SUBSCRIBER NAME%

You have been assigned a Visual Studio subscription. Please visit https://my.visualstudio.com, and log in with your %DIRECTORY ADDRESS% address to activate and access your subscription.

If you’re having trouble, please contact the support team (https://visualstudio.microsoft.com/subscriptions/support/).

At the bottom of the page, select the following:
   - Accounts, Subscriptions, and Billing Support
   - From Issue, choose Subscription sign in support
   - Choose the appropriate Country
   - Select the desired Assisted Support option

----------- End Copy -----------
```

## <a name="defining-a-work-or-school-account-as-a-personal-account"></a>Definiowanie konta służbowego jako konta osobistego
Aby dodać nowego użytkownika lub zaktualizować adres e-mail użytkownika w ramach usługi licencjonowania zbiorowego (VLSC), Skorzystaj z instrukcji opisanych w sekcji [przypisywanie subskrybentów do konta katalogu](#assigning-subscribers-to-a-directory-account) .  W przypadku, gdy adres e-mail nie jest rozpoznawany przez katalog, użytkownik będzie musiał przejść krok po kroku, aby utworzyć nowe konto w celu zdefiniowania adresu e-mail jako konta osobistego.  W krótkim czasie zespół subskrypcji programu Visual Studio podłączył wykluczenie z zasad tożsamości zdefiniowanych poniżej, ale zainwestowano w możliwości niezbędne do usunięcia tych zasad.

> [!WARNING]
> Firma Microsoft nie zaleca łączenia tożsamości "służbowych" z tożsamościami "osobistymi".  Ta akcja powoduje utratę własności i kontroli konta przez organizację, a pracownik może nadal uzyskiwać dostęp do określonych produktów lub usług nawet po opuszczeniu firmy.  

### <a name="defining-an-email-address-as-a-personal-account"></a>Definiowanie adresu e-mail jako konta osobistego
Po przypisaniu subskrypcji do subskrybenta otrzymasz wiadomość e-mail z prośbą o odwiedzenie [https://my.visualstudio.com](https://my.visualstudio.com?wt.mc_id=o~msft~docs) , aby skorzystać z korzyści z subskrypcji.  Podczas próby zalogowania się do Visual Studio Subscription logowania zakończy się niepowodzeniem z powodu błędu informującego, że konto nie zostało rozpoznane.  Przed zalogowaniem [https://my.visualstudio.com](https://my.visualstudio.com?wt.mc_id=o~msft~docs) się do środowiska zapoznaj się z poniższymi instrukcjami.  W razie potrzeby można użyć tego [szablonu](#notifying-your-subscribers-using-personal-accounts) do powiadomienia subskrybenta po przypisaniu subskrypcji.

1. Przejdź do https://my.visualstudio.com, a następnie kliknij pozycję **Utwórz nowe konto Microsoft**.

2. Wypełnij pola:
   - Wprowadź adres e-mail, na który otrzymasz powitalną wiadomość Someone@example.com e-mail w polu
   - Utwórz hasło
   - Wybierz ustawienia promocyjne
   - Kliknij przycisk **dalej** .

3. Wykonaj kroki walidacji i kliknij przycisk **dalej**.

4. Nowi użytkownicy mogą wymagać zakończenia profilu programu Visual Studio.

5. Subskrypcja i korzyści powinny teraz być widoczne.

### <a name="notifying-your-subscribers-using-personal-accounts"></a>Powiadamianie subskrybentów przy użyciu kont osobistych
W powyższym scenariuszu subskrybent otrzyma "powitalną wiadomość E-mail", ale ze względu na aliasy mogą oni się nie zalogować.  Poniższego tekstu można użyć do powiadomienia subskrybenta powyższych kroków i zalecać opcje pomocy technicznej, jeśli jest to wymagane.  Zastąp% WORD% odpowiednimi informacjami dla każdego subskrybenta.

```
----------- Copy Below (Ctrl+C) -----------

Hello %SUBSCRIBER NAME%

You have been assigned a Visual Studio subscription, and may have been directed to log into https://my.visualstudio.com based on your Welcome email.  While this is the correct website for consuming benefits, our organization requires you to take a few extra steps before you can access the site.  Please follow the below instructions to help you create a “Microsoft Account” that is tied to our corporate email address.  Once these steps are completed, you will use your email address to access the Subscription benefits.
1. Visit https://my.visualstudio.com

2. Click Create new Microsoft Account on the right hand side

3. Complete the Form:
   - Use your corporate email address in the someone@example.com box
   - Enter a password
   - Select your promotional preference
   - Click Next

4. Complete the account validation steps

5. If necessary, complete the Visual Studio profile

6. You should now see your benefits

Note:  When visiting https://my.visualstudio.com in the future, you may be prompted to select which account you’d like to use (e.g. “Work or School Account” or “Personal Account”).  After following the steps above, you will need to leverage the “Personal Account” option.

If you’re having trouble, please contact the support team (https://visualstudio.microsoft.com/subscriptions/support/).

At the bottom of the page, select the following:
   - Accounts, Subscriptions, and Billing Support
   - From Issue, choose Subscription sign in support
   - Choose the appropriate Country
   - Select the desired Assisted Support option

----------- End Copy -----------
```
