---
title: Logowanie do subskrypcji programu Visual Studio może zakończyć się niepowodzeniem podczas aliasy użycia | Dokumentacja firmy Microsoft
author: evanwindom
ms.author: jaunger
manager: evelynp
ms.date: 01/02/2018
ms.topic: conceptual
description: Logowanie może zakończyć się niepowodzeniem, jeśli są używane aliasy lub przyjazne nazwy
ms.openlocfilehash: 7285c1ede495a1aa2603216f2a9e9fe9f89331ea
ms.sourcegitcommit: 208395bc122f8d3dae3f5e5960c42981cc368310
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67783691"
---
# <a name="signing-in-to-visual-studio-subscriptions-may-fail-when-using-aliases"></a>Logowanie do subskrypcji programu Visual Studio może zakończyć się niepowodzeniem przy użyciu aliasów

W zależności od typu konta używanego do logowania, dostępne subskrypcje mogą nie być poprawnie wyświetlane podczas logowania się do [ https://my.visualstudio.com ](https://my.visualstudio.com?wt.mc_id=o~msft~docs). Jeden potencjalną przyczyną jest użycie "aliasy" lub "przyjazne nazwy" zamiast tożsamość logowania do którego jest przypisana subskrypcja. Jest to nazywane "aliasowanie".

## <a name="what-is-aliasing"></a>Czym jest aliasowanie?

Termin "aliasowanie" dotyczy użytkownicy korzystają z różnych tożsamości do logowania się na Windows (lub usługi Active Directory) i dostęp do poczty e-mail.

Tworzenie aliasów może wystąpić, gdy firma ma więcej niż Microsoft Online Services dla katalogu zalogowania, takie jak JohnD@contoso.com, ale użytkownicy uzyskują dostęp do swoich kont poczty e-mail przy użyciu aliasów lub przyjaznych nazw, takich jak John.Doe@contoso.com. Dla wielu klientów, którzy zarządzają subskrypcjami za pośrednictwem wolumin licencjonowania Service Center (VLSC), może to spowodować się niepowodzeniem środowisko logowania jako adresu e-mail pod warunkiem (John.Doe@contoso.com) nie jest zgodny z adresem katalogu (JohnD@contoso.com) wymagane do pomyślnego uwierzytelnienia za pomocą opcji "Konto służbowe".

## <a name="as-an-administrator-what-options-do-i-have"></a>Jako administrator jakie opcje są dostępne?

Jako administrator, dostępne są dwie opcje, aby zapewnić subskrybentom pomyślnego logowania na [ https://my.visualstudio.com ](https://my.visualstudio.com?wt.mc_id=o~msft~docs).
- Pierwsza opcja (zalecane), jest korzystanie z konta katalogu jako przypisany adres w wolumin licencjonowania Service Center (VLSC). Zapoznaj się [przypisywanie subskrybentów z kontem katalogu](#assigning-subscribers-to-a-directory-account) sekcję w tym artykule, aby uzyskać więcej informacji.
- Druga opcja (mniej bezpieczna opcja), jest umożliwienie subskrybentom (zwany również skojarzyć swój adres e-mail "Pracy lub szkoły" w celu konta "Osobistego" Konto Microsoft lub konta Microsoft). Zapoznaj się [definiowania pracy lub konto służbowe jako konto osobiste](#defining-a-work-or-school-account-as-a-personal-account) sekcję w tym artykule, aby uzyskać więcej informacji.

> [!NOTE]
> Gdy Twoja firma jest migrowana do nowej subskrypcji programu Visual Studio [portalu zarządzania](https://manage.visualstudio.com), będzie można korzystać z zalet nowego środowiska administracji, umożliwiający zarówno adresy katalogu adresy e-mail należy podać jako część Profil subskrybenta. Dowiedz się więcej o [migracji](https://support.microsoft.com/help/4013930/visual-studio-subscriptions-administrator-migration-details).

## <a name="as-a-subscriber-what-options-do-i-have"></a>Jako subskrybent jakie opcje są dostępne?

Z perspektywy abonenta ważne jest pierwszym pracować z administratorem, aby zrozumieć konfigurację tożsamość firmy. Jeśli to konieczne, administrator może być aktualizacja ustawień konta z poziomu ich portalu administracyjnego lub może być konieczne utworzenie konta Microsoft (MSA) przy użyciu adresu e-mail firmy. Przed podjęciem kroki, aby utworzyć konto MSA, Porozmawiaj z administratorem w sprawie żadnych zasad lub problemy z wykonaniem tej akcji. Zapoznaj się [definiowania pracy lub konto służbowe jako konto osobiste](#defining-a-work-or-school-account-as-a-personal-account) sekcję w tym artykule, aby uzyskać więcej informacji.

## <a name="assigning-subscribers-to-a-directory-account"></a>Przypisywanie subskrybentów z kontem katalogu

We wszystkich przypadkach Menedżer subskrypcji w obrębie woluminu licencjonowania Service Center (VLSC) należy użyć adres katalogu dla nowych subskrybentów, lub zaktualizować adres e-mail dla subskrybentów "istniejący". Należy zauważyć, że przy użyciu adresu katalogu oznacza wszelkie nowi subskrybenci nie otrzyma powitalną wiadomość E-mail, a Administrator będą potrzebne do powiadamiania subskrybenta, która subskrypcja została przypisana do nich. Po wykonaniu poniższych kroków, można także swobodnie korzystaj wiadomości e-mail [szablonu](#notifying-your-subscribers-with-directory-addresses) Powiadom subskrybentom i ułatwienie procesu logowania.

### <a name="adding-new-subscribers"></a>Dodawanie nowych subskrybentów

Wykonaj następujące kroki, aby dodać nowy abonent przy użyciu konta katalogu.

1. Odwiedź stronę [Volume Licensing Service Center](https://www.microsoft.com/Licensing/servicecenter/default.aspx) (firmy Microsoft VLSC) i zaloguj się.
2. Na stronie administratora VLSC kliknij **subskrypcje** i następnie **subskrypcji programu Visual Studio**.

    > [!div class="mx-imgBorder"]
    > ![Menu subskrypcji](_img//vlsc/vlsc-subscriptions.png)

3. Kliknij przycisk **numer umowy** skojarzony z subskrypcją programu Visual Studio.

    > [!div class="mx-imgBorder"]
    > ![Wybierz umowę](_img/vlsc/vlsc-agreement.png)

4. Kliknij przycisk **przypisywanie subskrypcji**.
5. Wybierz żądany **poziom subskrypcji**.
6. Sprawdź poprawność masz dostępne do przypisania, a następnie kliknij pozycję subskrypcje **dalej**.
7. Wprowadź szczegóły subskrybenta i adres katalogu w polu Adres E-mail, a następnie kliknij przycisk **dalej**.
8. Sprawdź poprawność informacji dotyczących subskrybenta, a następnie kliknij przycisk **Zakończ**.
9. Powiadom subskrybenta, że ich subskrypcji zostały udostępnione przy użyciu poniższych [szablonu](#notifying-your-subscribers-with-directory-addresses).

### <a name="updating-an-existing-subscriber"></a>Aktualizowanie istniejący subskrybent

Wykonaj poniższe kroki, aby zaktualizować istniejący subskrybent przy użyciu konta katalogu.

1. Odwiedź stronę [Volume Licensing Service Center](https://www.microsoft.com/Licensing/servicecenter/default.aspx) (firmy Microsoft VLSC) i zaloguj się.
2. Na stronach administratora VLSC kliknij **subskrypcje** i następnie **subskrypcji programu Visual Studio**.
3. Kliknij przycisk **numer umowy** skojarzony z subskrypcją programu Visual Studio.
4. Kliknij przycisk **Strzałka w dół** na pasku wyszukiwania.
5. Wyszukaj subskrybenta przy użyciu pola "Email address Adres".
6. Na liście wyników kliknij **nazwisko** subskrybenta.
7. Kliknij przycisk **Edytuj**.
8. Zmień wartość pola Adres E-mail na adres w żądanym katalogu, a następnie kliknij przycisk **Zapisz**.
9. Powiadom subskrybenta, że ich subskrypcji zostały udostępnione przy użyciu poniższych szablon wiadomości e-mail.

### <a name="notifying-your-subscribers-with-directory-addresses"></a>Powiadamianie subskrybentom z adresami katalogu

Ponieważ powitalną wiadomość E-mail nie dotrze pomyślnie subskrybenta, skopiuj i wklej poniższe wiadomość na adres e-mail i Wyślij do subskrybenta. Zastąp słowo % odpowiednimi informacjami dla każdego subskrybenta.

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

## <a name="defining-a-work-or-school-account-as-a-personal-account"></a>Definiowanie konto służbowe jako konto osobiste

Można korzystać z instrukcji przedstawionych w temacie [przypisywanie subskrybentów z kontem katalogu](#assigning-subscribers-to-a-directory-account) sekcji, aby dodać nowego użytkownika lub zaktualizować adres e-mail użytkownika w obrębie woluminu licencjonowania Service Center (VLSC).  W przypadkach, w których adres e-mail nie został rozpoznany przez katalogu użytkownik musi przejść przez proces tworzenia nowego konta, aby zdefiniować adres e-mail jako konto osobiste.  Krótkoterminowe zespół subskrypcji programu Visual Studio ma zabezpieczone wykluczenie z zasad tożsamości określonych poniżej, ale możemy inwestuje w możliwości Usuń te zasady.

> [!WARNING]
> Microsoft nie zaleca się, łącząc "Pracy lub szkoły" tożsamościami przy użyciu tożsamości "Osobistego".  Ta akcja powoduje, że organizacja utraty własności i kontroli konta, a pracownik mogą w dalszym ciągu dostęp do określonych produktów i usług, nawet po wyjściu firmy.  Zobacz to [wpis w blogu](https://blogs.technet.microsoft.com/enterprisemobility/2016/09/15/cleaning-up-the-azure-ad-and-microsoft-account-overlap/), od zespołu Microsoft Identity, aby uzyskać dodatkowe informacje.

### <a name="defining-an-email-address-as-a-personal-account"></a>Definiowanie adresu e-mail jako konto osobiste

Po przypisaniu subskrypcji do subskrybenta, otrzymają one wiadomość e-mail z prośbą ich do [ https://my.visualstudio.com ](https://my.visualstudio.com?wt.mc_id=o~msft~docs) z zalet korzyści z subskrypcji.  Podczas próby logowania, logowania subskrypcji programu Visual Studio zakończy się niepowodzeniem z o błędzie informujący, że konto nie został rozpoznany.  Przed logując się do [ https://my.visualstudio.com ](https://my.visualstudio.com?wt.mc_id=o~msft~docs) występują, poproś subskrybentom wykonaj te instrukcje.  Jeśli to konieczne, możesz użyć tej funkcji [szablonu](#notifying-your-subscribers-using-personal-accounts) powiadomić subskrybenta, po przypisaniu subskrypcji.

1. Przejdź do https://my.visualstudio.com i kliknij przycisk **Utwórz nowe konto Microsoft**.

2. Wypełnij pola:
   - Wprowadź adres e-mail, która otrzymała powitalnej wiadomości E-mail w Someone@example.com okno
   - Utwórz hasło
   - Wybierz ustawienia promocyjna
   - Kliknij przycisk **dalej**

3. Wykonaj kroki weryfikacji, a następnie kliknij przycisk **dalej**.

4. Nowych użytkowników może być konieczne wykonanie profilu programu Visual Studio.

5. Teraz powinny być widoczne w subskrypcji i korzyści.

### <a name="notifying-your-subscribers-using-personal-accounts"></a>Powiadamianie użytkownika subskrybentów korzystających z osobistych kont

W tym scenariuszu opisanych powyżej subskrybenta będą otrzymywać "Powitalną wiadomość E-mail", ale z powodu aliasów one może się okazać, że nie można się zalogować.  Możesz użyć poniżej tekstu w celu otrzymywania powiadomień o subskrybenta z powyższych kroków, zaleca się opcje pomocy technicznej, jeśli jest to wymagane.  Zastąp słowo % odpowiednimi informacjami dla każdego subskrybenta.

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
