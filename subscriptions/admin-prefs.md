---
title: Ustawianie preferencji umów w portalu administracyjnym
author: evanwindom
ms.author: lank
manager: lank
ms.assetid: 0fe9eaa4-f589-429e-a443-13bf86637d5a
ms.date: 03/17/2020
ms.topic: conceptual
description: Dowiedz się, jak ustawić preferencje dotyczące języka, kontaktów, poziomu subskrypcji i innych w Portalu administracyjnym
ms.openlocfilehash: cbcf532620e958ca408d43295d2d4200d12ee0cd
ms.sourcegitcommit: f8e3715c64255b476520bfa9267ceaf766bde3b0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/21/2020
ms.locfileid: "79508761"
---
# <a name="set-preferences-for-your-agreements-in-the-administration-portal"></a>Ustawianie preferencji dla umów w portalu administracyjnym
Superadministratorzy mogą ustawić określone preferencje w portalu administracyjnym (portalu administracyjnym), które będą stosowane globalnie dla każdej umowy.  Te preferencje będą automatycznie wypełniać szczegóły subskrypcji dla administratorów, gdy dodają subskrybentów, i mogą być modyfikowane globalnie tylko przez superadministratorów.  

## <a name="access-preferences"></a>Preferencje dostępu
Aby wyświetlić lub zmodyfikować preferencje, musisz zalogować się do [portalu administracyjnego](https://manage.visualstudio.com) przy użyciu identyfikatora logowania, który ma prawa administratora do umowy.  

Aby ustawić preferencje:
1. Zaloguj się do portalu administracyjnego przy przyuśmiać identyfikator, który ma uprawnienia administratora super administratora.
2. Kliknij kartę **Zarządzanie administratorami.**
   > [!div class="mx-imgBorder"]
   > ![Przycisk Preferencje administratora](_img/admin-prefs/admin-prefs-button.png)

3. Kliknij **pozycję Preferencje umowy**.
Po prawej stronie otworzy się panel i zostaną wyświetlone dostępne preferencje. 

   > [!div class="mx-imgBorder"]
   > ![Okno dialogowe wysuwanie preferencji administratora](_img/admin-prefs/admin-prefs-flyout.png)

## <a name="set-your-preferences"></a>Ustawianie preferencji
Przyjrzyjmy się każdemu z dostępnych preferencji i ich efektom. 

### <a name="agreement"></a>Umowy
Jeśli masz wiele umów, dla których jesteś superadministratorem, możesz wybrać żądaną umowę w rozwijanym.  Ustawione preferencje będą miały zastosowanie tylko do tej umowy.  Poszczególni administratorzy mogą zastąpić niektóre z tych preferencji indywidualnie podczas przypisywania subskrypcji. 

Jeśli z adresem e-mail użytym do zalogowania się jest tylko jedna umowa, zostanie wyświetlona, a rozwijana zostanie wyłączona. 

### <a name="contact-email-address"></a>Kontaktowy adres e-mail
Ta preferencja umożliwia subskrybentom kontakt z administratorami za pomocą przycisku **Skontaktuj się z administratorem** na [stronie subskrypcje](https://my.visualstudio.com/subscriptions) portalu subskrybenta.  Jeśli ta preferencja pozostanie pusta, wiadomości subskrybentów zostaną przekazane do wszystkich administratorów i superadministratorów w umowie.  Zalecamy użycie grupowego aliasu e-mail lub grupy zabezpieczeń, aby dostosować odbiorców do tej kontaktowej wiadomości e-mail. Możesz również wprowadzić adres e-mail danej osoby, jeśli wolisz.

> [!NOTE]
> Adres e-mail, który tutaj wymieniasz, NIE zostanie podany subskrybentom.  Gdy subskrybent przesyła żądanie **Skontaktuj się z administratorem** w portalu subskrybenta, wiadomość zostanie przekazana do aliasu bez narażania jej na subskrybenta. 

### <a name="default-external-subscribers-setting"></a>Domyślne ustawienie subskrybentów zewnętrznych
Ta preferencja pozwala zdecydować, czy administratorzy mogą dodawać subskrybentów spoza dzierżawy/katalogu organizacji.  Jeśli wyłączysz tę funkcję, nie będą mogli korzystać z zewnętrznych subskrybentów.  Jeśli włączysz go, a administrator spróbuje dodać zewnętrznego subskrybenta, zostanie poproszony o potwierdzenie wyboru i będzie mógł przypisać subskrypcję. Administratorzy nie mogą zastąpić tego ustawienia. 

### <a name="default-downloads-setting"></a>Domyślne ustawienie pobierania
Włączenie tego ustawienia, które jest domyślnie włączone, umożliwi subskrybentom dostęp do plików do pobrania, gdy administratorzy tworzą nowe subskrypcje.  Administratorzy nadal mogą wyłączyć pobieranie w ramach pojedynczej subskrypcji.  

### <a name="default-subscription-level"></a>Domyślny poziom subskrypcji
To ustawienie służy do określenia, który z poziomów subskrypcji zawartych w umowie jest wybrany domyślnie, gdy subskrypcja jest przypisana do użytkownika.  Administratorzy mogą zmienić ustawienie na dowolny poziom subskrypcji w umowie — zapobiega to wielokrotnemu dokonywaniu najbardziej powszechnego wyboru. 

### <a name="default-communication-preferences"></a>Domyślne preferencje komunikacji
Ustawienie domyślnego języka komunikacji i ustawień regionalnych może usprawnić proces przypisywania subskrypcji.  Jeśli na przykład zespół deweloperów ma siedzibę w innym kraju niż zespół administracyjny, możesz ustawić preferencje najlepiej dopasowane do lokalizacji subskrybentów. Te ustawienia mogą być nadal zmieniane przez wszystkich administratorów dla poszczególnych subskrybentów. 

## <a name="frequently-asked-questions"></a>Często zadawane pytania
### <a name="q--can-i-disable-the-contact-email-address-so-subscribers-cannot-contact-administrators"></a>Pyt.: Czy mogę wyłączyć **kontaktowy adres e-mail,** aby subskrybenci nie mogli skontaktować się z administratorami?
Odp.: Nie — chociaż można określić, z administratorami, z którymi kontaktowano się za pomocą grupy zabezpieczeń, grupowego aliasu e-mail lub indywidualnego adresu e-mail, funkcja nie może zostać wyłączona.

### <a name="q-if-i-answer-a-subscribers-email-will-they-have-my-email-address"></a>P: Jeśli odpowiem na wiadomość e-mail subskrybenta, czy będzie on miał mój adres e-mail?
Odp.: Ponieważ odpowiedź będzie pochodzić z dowolnego klienta poczty e-mail, którego używasz, odpowiedź, którą otrzymuje subskrybent, pokaże dowolny adres e-mail, którego używasz.  Jeśli więc odpowiadasz z aliasu grupy, zobaczysz alias grupy.  Jeśli odpowiesz z własnego adresu e-mail, zobaczą to.  

### <a name="q-where-can-i-find-out-more-about-the-contact-my-admin-feature-in-the-subscriber-portal"></a>P: Gdzie mogę dowiedzieć się więcej o funkcji **Kontakt z administratorem** w portalu subskrybenta?
O: Zapoznaj się z naszym [artykułem Kontakt z administratorem.](contact-my-admin.md) 

### <a name="q-if-we-dont-complete-the-contact-email-address-and-a-subscriber-uses-the-contact-my-admin-feature-who-receives-their-request"></a>Pyt.: Jeśli nie wypełnimy **kontaktowego adresu e-mail,** a subskrybent użyje funkcji **Skontaktuj się z administratorem,** kto otrzyma ich prośbę?
O: Jeśli w preferencji **Kontaktowy adres e-mail** nie ustawiono żadnego konkretnego adresu e-mail, wszyscy administratorzy umowy otrzymają żądanie. 

## <a name="resources"></a>Zasoby
- [Pomoc techniczna dotycząca subskrypcji programu Visual Studio i administrowania nim](https://visualstudio.microsoft.com/support/support-overview-vs)

## <a name="see-also"></a>Zobacz też
- [Dokumentacja programu Visual Studio](https://docs.microsoft.com/visualstudio/)
- [Dokumentacja usługi Azure DevOps](https://docs.microsoft.com/azure/devops/)
- [Dokumentacja platformy Azure](https://docs.microsoft.com/azure/)
- [Dokumentacja usługi Microsoft 365](https://docs.microsoft.com/microsoft-365/)

## <a name="next-steps"></a>Następne kroki
Dowiedz się więcej o zarządzaniu subskrypcjami programu Visual Studio.
- [Przypisywanie poszczególnych subskrypcji](assign-license.md)
- [Przypisywanie wielu subskrypcji](assign-license-bulk.md)
- [Edytowanie subskrypcji](edit-license.md)
- [Określanie maksymalnego użycia](maximum-usage.md)



