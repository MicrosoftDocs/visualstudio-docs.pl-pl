---
title: Często zadawane pytania dotyczące centrum VLSC administratora migracji | Dokumentacja firmy Microsoft
author: evanwindom
ms.author: jaunger
manager: evelynp
ms.date: 03/13/2018
ms.topic: conceptual
description: Często zadawane pytania dotyczące Volume License Service Center administrator migracji
searchscope: VS Subscription
ms.openlocfilehash: 21083f50966472bb7d6d85c8ad594b586b810df9
ms.sourcegitcommit: cea6187005f8a0cdf44e866a1534a4cf5356208c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/27/2019
ms.locfileid: "56953953"
---
# <a name="visual-studio-subscriptions-administration-migration"></a>Migracja administracji subskrypcji programu Visual Studio

W ciągu następnych kilku miesięcy zostaną wprowadzone zmiany do zarządzania subskrypcjami programu Visual Studio (dawniej subskrypcje MSDN). Obecnie możesz kupić program Visual Studio, subskrypcje w ramach programu licencjonowania zbiorowego i subskrypcje, które są zarządzane w portalu Volume License Service Center (VLSC). Trwa tworzenie nowego portalu zarządzania i subskrypcje programu Visual Studio będzie odbywać się w nowym portalu w przyszłości. Oprócz istniejącej operacji zawartym w centrum VLSC nowego portalu będzie umożliwiać przypisanie zbiorcze z nieograniczoną śledzenie i filtrowanie subskrypcji i umożliwia korzystanie z usługi Azure Active Directory (Azure AD) do zarządzania dostępem. Nowego portalu administratora programu Visual Studio będzie następująca: [ https://manage.visualstudio.com ](https://manage.visualstudio.com).

> [!Note]
> Ta migracja nie ma wpływu na klientów z umowami MPSA.

## <a name="frequently-asked-questions"></a>Często zadawane pytania

### <a name="why-is-it-changing"></a>Dlaczego ulega to zmianie?
Nowy portal będzie Optymalizuj środowisko zarządzania subskrypcjami programu Visual Studio i utworzenie jednego środowiska zarządzania subskrypcjami programu Visual Studio, niezależnie od tego, jak zostały zakupione. Nowy portal ma nową platformę, który umożliwia usłudze Azure AD i umieszcza nam w przyszłości. Ponadto ma interfejs zaktualizowanego użytkownika, który będzie łatwiejsza, przejdź do użycia, co zwiększy efektywność administratorów.

### <a name="who-will-be-impacted"></a>Kto będzie mieć wpływ?
Zmiana wpłynie na wszystkich klientów, którzy kupili subskrypcji programu Visual Studio za pomocą licencjonowania zbiorowego aktywnymi umowami licencjonowania zbiorowego i.

### <a name="when-is-it-changing"></a>Kiedy ulegnie to zmianie?
Jest ogromną przejścia i zostanie wykonane w fazy aż do wszystkich klientów z aktywnymi umowami licencjonowania zbiorowego dla subskrypcji programu Visual Studio zostaną zmigrowani do nowego portalu zarządzania. Migracja rozpoczął się w pierwszym kwartale 2017 r. Firma Microsoft powiadomi klientów licencjonowania zbiorowego wyprzedzeniem o zaplanowanym tygodniu migracji.

### <a name="does-my-organization-need-to-sign-up-for-azure-active-directory-azure-ad"></a>Czy Moja organizacja musi zarejestrować się do usługi Azure Active Directory (Azure AD)?
Twoja organizacja nie musi zarejestrować się w usłudze Azure AD, ale możesz to zrobić w dowolnym momencie. Jeśli użytkownik chce dołączyć do usługi Azure AD, możesz to zrobić bez ponoszenia kosztów, przy użyciu warstwy bezpłatna usługi Azure AD. Za pomocą usługi Azure Active Directory jest będzie ochronę organizacji dzięki zwiększenia poziomu zabezpieczeń, kontroli i zapewnić długoterminową niezawodność. Jednakże jeśli nie jesteś gotowy do usługi Azure AD, można nadal mogą używać Accounts Microsoft (MSA) na niezmienionych.

### <a name="how-do-i-know-when-my-organization-will-be-migrated"></a>Jak sprawdzić, kiedy Moja organizacja zostanie zmigrowana?
Podstawowy/kontaktowymi zostanie wysłana wiadomość e-mail od nas zapraszając ich, aby ukończyć proces dołączania jeden tydzień, zanim Twoja organizacja zostanie poddana migracji. Menedżerowie subskrypcji również otrzyma wiadomość e-mail z informacją o utworzeniu możemy skontaktować się z podstawowym/kontaktowymi i podano szczegółowe informacje na temat sposobu zapewnienia pomyślnego dołączenia. Dowiedz się, jak [zlokalizować organizacji podstawowy/kontaktowymi](#How-do-I-find-out-who-my-Primary-or-Notices-Contact-is?).

### <a name="is-onboarding-different-from-migration"></a>Dołączanie różni się od migracji?
Tak.  Istnieją dwie fazy, w ramach tego procesu. Konfigurowanie (lub dołączenie) organizacji przed migracją gwarantuje, że jest Brak przerw w pracy jako administrator. Po zmigrowaniu informacji w organizacji, następnie można zarządzać subskrypcjami programu Visual Studio w nowym portalu. Jeśli podstawowy/kontaktowymi powiadomień nie dołączy przed migracją, menedżerowie subskrypcji zostaną zablokowane i nie będzie można zarządzać subskrypcjami do momentu ukończenia procesu dołączania.

### <a name="what-is-the-onboarding-process"></a>Co to jest proces dołączania?
Główna osoba kontaktowa i kontaktowa zaproszeniem do ukończenia procesu dołączania zostanie wysłana wiadomość e-mail.
Zobacz poniżej, aby uzyskać instrukcje na temat procesu.
1. **Przy szukaniu numeru PCN i zaloguj się:**

    a. W wiadomości e-mail, podstawowej i osoba kontaktowa znajdują się za pomocą unikatowego linku i trzy ostatnie cyfry dla swojego publicznego numeru klienta (PCN). *

    b. W celu uzyskania cały numer PCN, musisz zalogować się do centrum VLSC głównej osoby kontaktowej (instrukcje dotyczące lokalizacji dla numeru PCN znajdują się poniżej).

    c. Po uzyskaniu numer PCN, ich należy wybrać ich unikatowego linku, co spowoduje wyświetlenie monitu do logowania. Będą mogli zalogować się przy użyciu konta Microsoft (MSA) lub konto służbowe (jeśli Twojej organizacji w usłudze Azure AD), jeśli Twoja organizacja nie znajduje się w usłudze Azure AD.

    d. Następnie zostanie wyświetlony monit o podanie numeru PCN.

2. **Konfigurowanie administratorów:**

    Po wprowadzeniu numerów PCN, ich wyświetli się Strona gdzie są w stanie dodać superadministratorzy i Administratorzy (wcześniej znanej jako menedżerowie subskrypcji). W idealnym zostanie to ukończone przed datą migracji w organizacji dzięki temu można uniknąć przerw w zarządzaniu subskrypcjami.

3. **Uzyskiwanie dostępu do nowego portalu zarządzania subskrypcjami:** Po zmigrowaniu organizacji wiadomości e-mail będą wysyłane do superadministratorzy i Administratorzy zapraszając ich dostęp do nowego portalu i zarządzania subskrypcjami.

> [!NOTE]
> Jeśli główna osoba kontaktowa lub kontaktowa odbierze więcej niż jeden adres e-mail, oznacza to, że mają więcej niż jeden numer PCN. Należy ukończyć proces, korzystając z unikatowego linku dla numeru PCN, do którego odwołuje się każdej wiadomości e-mail.

### <a name="what-is-the-difference-between-a-super-admin-and-an-administrator"></a>Jaka jest różnica między Superadministratorem i administratorem?
Gdy podstawowy/kontaktowej loguje się po raz pierwszy, ich zostaną automatycznie skonfigurowane jako administratora. Superadministratorzy zarządzać dostępu administratora do subskrypcji, dodając/usuwając innych superadministratorów lub administratorów, a także mogli zarządzać subskrypcjami. Super admin można przypisać innych superadministratorów oprócz samodzielnie.

Administratorzy (wcześniej znanej jako menedżerowie subskrypcji) mogą tylko zarządzać subskrypcjami, ale nie można kontrolować, kto ma dostęp do zarządzania subskrypcjami.

### <a name="how-will-i-as-an-administrator-onboard-to-the-new-portal"></a>Jak będzie mogę, jako administrator, dołączanie do nowego portalu?
Głównymi osobami kontaktowymi i osoba kontaktowa w organizacji otrzyma wiadomość e-mail za pomocą unikatowego linku, który spowoduje przejście do strony, która umożliwi im logować się za pomocą obu firmowego lub szkolnego konta, wspierane przez usługi Azure Active Directory (Azure AD) lub osobistych kont MSA. Po zalogowaniu należy wprowadzić w organizacji publicznego numeru klienta (PCN) lub Numer autoryzacyjny w celu zweryfikowania umów. Mogą następnie być skonfiguruje jako superadministrator można dodawać innych administratorów, takich jak Ty, do zarządzania subskrypcjami programu Visual Studio.

### <a name="where-do-i-manage-subscriptions-if-my-organization-has-been-onboarded-but-hasnt-been-migrated"></a>Gdy zarządzanie subskrypcjami, jeśli Moja organizacja została dołączona, ale nie zostały poddane migracji?
Nadal będziesz zarządzać subskrypcjami, za pośrednictwem centrum VLSC, dopiero po otrzymaniu wiadomości e-mail z subskrypcji programu Visual Studio czy Twoja organizacja została zmigrowana i jest gotowy do można zarządzać w nowym portalu.

### <a name="where-can-i-locate-my-organizations-public-customer-number-pcn-or-authorization-number"></a>Gdzie można znaleźć publiczny numer klienta (PCN) lub Numer autoryzacyjny organizacji?
Zaloguj się do [VLSC](https://www.microsoft.com/Licensing/servicecenter/default.aspx) i przejdź do następującej ścieżki: **Subskrypcje** > **subskrypcje programu Visual Studio**. Numer PCN znajduje się poniżej **wyników numer klienta publicznego i umowy**. Uzyskaj wskazówki krok po kroku w znalezieniu numeru PCN w tym [artykułu pomocy](find-pcn.md).

### <a name="how-do-i-find-out-who-my-primary-or-notices-contact-is"></a>Jak sprawdzić, kto jest Moje podstawowe lub osoba kontaktowa?
Zaloguj się do [VLSC](https://www.microsoft.com/Licensing/servicecenter/default.aspx) i przejdź do następującej ścieżki: **Licencje > Podsumowanie relacji** wybierz swoje **licencjonowania identyfikator > kontakty**. Uzyskaj wskazówki krok po kroku dotyczące znajdowania sieci podstawowej lub osoba kontaktowa w tym [artykułu pomocy](find-primary-contact.md).

### <a name="what-if-my-primary-or-notices-contact-is-gone-no-longer-with-the-company-or-not-available-to-complete-onboarding"></a>Co zrobić, jeśli Moje podstawowe lub osoba kontaktowa jest stała, nie znajduje się już w firmie lub nie jest dostępny do dołączania?
Konieczne będzie [się z pomocą techniczną](https://visualstudio.microsoft.com/subscriptions/support/#talktous) i podaj adres e-mail, używanym w witrynie VLSC do zarządzania subskrypcjami. Po przeprowadzeniu weryfikacji personel, pomocy technicznej będzie mógł pomóc w realizacji procesu dołączania.

### <a name="what-will-happen-with-renewing-customers"></a>Co się stanie w przypadku klientów odnawiających subskrypcję?
Klientów odnawiających subskrypcję powinny nadal odnowienia subskrypcji w zwykły sposób, jako odnawiania procesy nie podlegają migracji.

### <a name="should-my-organization-wait-to-set-up-a-new-agreement-in-the-new-system-rather-than-renew-an-existing-agreement"></a>Należy poczekać i skonfigurować nową umowę w nowym systemie zamiast odnawiania istniejącej umowy?
Nie.  Migracja nie ma wpływu na tworzenie lub odnowienia Umowy.

### <a name="what-if-my-organizations-agreement-is-in-the-grace-period-during-the-transition-will-they-also-be-migrated"></a>Co zrobić, jeśli umowa mojej organizacji znajduje się w okresie prolongaty podczas przejścia? Zostanie również zostanie zmigrowana?
Tak, jeśli umowa wciąż jest aktywna, Twojej organizacji zostanie ono zmigrowane.

### <a name="what-if-my-organization-has-over-claimed-in-the-current-system-will-we-still-be-migrated-to-the-new-system"></a>Co zrobić, jeśli Moja organizacja zawyżyła liczbę w bieżącym systemie? Czy firma Microsoft zostaną zmigrowane do nowego systemu?
Tak, Twoja organizacja nadal zostaną zmigrowane do nowego systemu. Możliwość liczby zgłoszeń (w przypadku typów, które zezwalają na to) będzie istnieć w nowym systemie.

### <a name="what-if-my-organization-has-more-than-one-subscription-assigned-to-a-single-useremail-address"></a>Co zrobić, jeśli organizacja ma więcej niż jedną subskrypcję, przypisany do jednego użytkownika/adresu e-mail?
Twoja organizacja nadal zostaną poddane migracji.  Jednak nie będzie mógł przypisywać dodatkowych subskrypcji na tym samym poziomie (ie: Enterprise, Professional, itp..) do tego użytkownika/adresu e-mail. Żadnych subskrypcji na tym samym poziomie, które mają tego samego adresu e-mail podczas migracji będzie nadal widoczny, ale administratorzy muszą zmienić adresy e-mail, tak aby były unikatowe. Nie można przypisać wiele subskrypcji w tym samym poziomie do pojedynczego użytkownika/adresu e-mail w nowym portalu.

### <a name="where-can-i-find-the-most-up-to-date-information-about-the-migration"></a>Gdzie można znaleźć najbardziej aktualne informacje dotyczące migracji?
Większość informacji dotyczących tej migracji, odwiedź nasz administratora subskrypcji programu Visual Studio [strony sieci Web](https://aka.ms/vs-admin). Jeśli potrzebujesz pomocy, zapoznaj się z subskrypcji programu Visual Studio [stronę pomocy technicznej](http://visualstudio.microsoft.com/subscriptions/support/#!collections/962-subscriptions), w którym znajduje się samodzielna pomoc dotycząca informacje i pomoc techniczna informacje kontaktowe. W ciągu następnych kilku miesięcy firma Microsoft będzie dostarczać aktualizacje na stronę internetową administratora i za pośrednictwem poczty e-mail, aby ułatwić ten proces przejścia, które występują w ułatwienia.

## <a name="resources-and-support-information"></a>Zasoby i informacje pomocy technicznej
- [Stronę internetową administratora](https://visualstudio.microsoft.com/subscriptions-administration/)

- Subskrypcje programu Visual Studio i zarządzania [pomocy technicznej](https://visualstudio.microsoft.com/subscriptions/support/)

- [Jak znaleźć mój numer PCN](find-pcn.md)

- [Jak znaleźć Moje podstawowe lub osoba kontaktowa](find-primary-contact.md)

- [Film wideo](https://www.youtube.com/watch?v=ZmnywYGSFMg&list=PLReL099Y5nRfDyvvwzNDBaZe7qTxmuM2T&index=1&t=0s) do dołączenia do organizacji i zarządzania nimi, Administratorzy
