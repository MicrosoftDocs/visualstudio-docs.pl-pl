---
title: Ustawianie preferencji w portalu administracyjnym Visual Studio subskrypcji
author: evanwindom
ms.author: v-evwin
manager: cabuschl
ms.assetid: 0fe9eaa4-f589-429e-a443-13bf86637d5a
ms.date: 05/18/2021
ms.topic: conceptual
description: Dowiedz się, jak ustawiać preferencje dotyczące języka, kontaktów, poziomu subskrypcji i innych w portalu programowania
ms.openlocfilehash: 348febd6b964feec54053cff4a3d50cc02eba3d0
ms.sourcegitcommit: 162be102d2c22a1c4ad2c447685abd28e0e85d15
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/19/2021
ms.locfileid: "110018533"
---
# <a name="set-preferences-for-your-agreements-in-the-admin-portal"></a>Ustawianie preferencji dla umów w portalu administracyjnym
Administratorzy mogą ustawiać pewne preferencje w portalu administracyjnym (portalu administracyjnym), które będą stosowane globalnie dla każdej umowy.  Te preferencje będą automatycznie wypełniać szczegóły subskrypcji dla administratorów podczas dodawania subskrybentów i mogą być modyfikowane globalnie tylko przez administratorów.  

## <a name="access-preferences"></a>Preferencje dostępu
Aby wyświetlić lub zmodyfikować preferencje, musisz zalogować się do portalu administracyjnego przy użyciu identyfikatora logowania, który ma uprawnienia administratora do umowy. [](https://manage.visualstudio.com)  

Aby ustawić preferencje:
1. Zaloguj się do portalu administracyjnego przy użyciu identyfikatora, który ma uprawnienia administratora.
2. Kliknij ikonę ustawienia w okienku po lewej stronie.
   > [!div class="mx-imgBorder"]
   > ![Przycisk Preferencje administratora](_img/admin-preferences/admin-preferences-button.png "Kliknij pozycję Zarządzaj administratorami, a następnie pozycję Zamów preferencje, aby wyświetlić preferencje")

3. Kliknij **pozycję Preferencje umowy**.
Po lewej stronie zostanie otwarty panel z wyświetlonymi dostępnymi preferencjami. 

   > [!div class="mx-imgBorder"]
   > ![Okno dialogowe wysuwu preferencji administratora](_img/admin-preferences/admin-preferences-flyout-2.png "Ustaw preferencje i kliknij przycisk Zapisz")

## <a name="set-your-preferences"></a>Ustawianie preferencji
Przyjrzyjmy się każdej z dostępnych preferencji i ich efektów. 

### <a name="agreement"></a>Umowa
Jeśli masz wiele umów, dla których jesteś administratorem, możesz wybrać odpowiednią umowę z listy rozwijanej po prawej stronie rozwiniętego panelu ustawień.  Ustawione preferencje będą stosowane tylko do tej umowy.  Indywidualni administratorzy mogą przesłonić niektóre z tych preferencji dla poszczególnych przypadków podczas przypisywania subskrypcji. 

Jeśli z adresem e-mail użytym do zalogowania jest skojarzona tylko jedna umowa, zostanie ona wyświetlona po prawej stronie rozwiniętego panelu ustawień, a lista rozwijana zostanie wyłączona. 

### <a name="contact-email-address"></a>Kontaktowy adres e-mail
Ta preferencja umożliwia subskrybentom skontaktowanie się z administratorami  za pomocą przycisku Skontaktuj się z administratorem na stronie subskrypcji portalu subskrybenta. [](https://my.visualstudio.com/subscriptions)  Jeśli ta preferencja zostanie pozostawiona pusta, komunikaty subskrybenta zostaną przekazane do wszystkich administratorów i administratorów umowy.  Zalecamy użycie aliasu e-mail grupy lub grupy zabezpieczeń w celu dostosowania odbiorców do tej kontaktowej wiadomości e-mail. Jeśli wolisz, możesz również wprowadzić adres e-mail osoby poszczególnych osób.

> [!NOTE]
> Adres e-mail podany w tym miejscu NIE zostanie podany subskrybentom.  Gdy subskrybent przesyła  żądanie Skontaktuj się z administratorem w portalu dla subskrybentów, komunikat zostanie przekazane do aliasu bez ujawniania go subskrybentowi. 

### <a name="default-subscription-level"></a>Domyślny poziom subskrypcji
To ustawienie umożliwia określenie, które poziomy subskrypcji uwzględnione w umowie są domyślnie wybierane, gdy subskrypcja jest przypisana do użytkownika.  Administratorzy mogą zmienić to ustawienie na dowolny poziom subskrypcji w umowie — zapobiega to po prostu wielokrotnemu wyborze. 

### <a name="default-communication-preferences"></a>Domyślne preferencje komunikacji
Ustawienie domyślnego języka komunikacji i ustawień regionalnych może usprawnić proces przypisywania subskrypcji.  Jeśli na przykład twój zespół programistów znajduje się w innym kraju niż twój zespół administracyjny, możesz ustawić preferencje najlepiej dopasowane do lokalizacji subskrybentów. Te ustawienia mogą być nadal zmieniane przez wszystkich administratorów dla poszczególnych subskrybentów. 

### <a name="default-external-subscribers-setting"></a>Domyślne ustawienie dla subskrybentów zewnętrznych
Ta preferencja pozwala zdecydować, czy administratorzy mogą dodawać subskrybentów spoza dzierżawy/katalogu organizacji.  Jeśli to wyłączysz, żaden z zewnętrznych subskrybentów nie będzie dozwolony.  Jeśli ją włączysz, a administrator spróbuje dodać zewnętrznego subskrybenta, zostanie poproszony o potwierdzenie wyboru i będzie mógł przypisać subskrypcję. Administratorzy nie mogą zastąpić tego ustawienia. 

### <a name="default-downloads-setting"></a>Domyślne ustawienie pobierania
Włączenie tego ustawienia, które jest domyślnie włączone, umożliwi subskrybentom dostęp do plików do pobrania, gdy administratorzy będą tworzyć nowe subskrypcje.  Administratorzy mogą nadal wyłączać pobieranie w ramach poszczególnych subskrypcji.  Wyłączenie dostępu do pobierania powoduje również wyłączenie dostępu do kluczy produktów.  

### <a name="overallocation-notification"></a>Powiadomienie o alokacji 
Zrezygnuj z otrzymywania wiadomości e-mail, gdy przydziały w umowie staną się nadmiernie alokacji. To powiadomienie e-mail zostanie wysłane na kontaktowy adres [e-mail](admin-preferences.md#contact-email-address)lub na wszystkich administratorów w umowie, jeśli nie ma kontaktowego adresu e-mail. Użyj menu rozwijanego, aby skonfigurować próg, przy którym chcesz być powiadamiany. 

 
## <a name="frequently-asked-questions"></a>Często zadawane pytania
### <a name="q--can-i-disable-the-contact-email-address-so-subscribers-cannot-contact-admins"></a>Pytanie: Czy mogę wyłączyć kontaktowy **adres e-mail,** aby subskrybenci nie mogą kontaktować się z administratorami?
A: Nie — chociaż można określić, z którymi administratorami kontaktuje się grupa zabezpieczeń, alias adresu e-mail grupy lub indywidualny adres e-mail, nie można wyłączyć tej funkcji.

### <a name="q-if-i-answer-a-subscribers-email-will-they-have-my-email-address"></a>Pytanie: Jeśli odpowiem na adres e-mail subskrybenta, czy będzie on miał mój adres e-mail?
Odpowiedź: Ponieważ odpowiedź będzie pochodzić z dowolnego klienta poczty e-mail, z których korzystasz, odpowiedź obierania przez subskrybenta będzie pokazywać dowolny adres e-mail, z których korzystasz.  Dlatego jeśli odpowiadasz z aliasu grupy, zobaczą alias grupy.  Jeśli odpowiesz na swój własny adres e-mail, zobaczą to.  

### <a name="q-where-can-i-find-out-more-about-the-contact-my-admin-feature-in-the-subscriber-portal"></a>Pytanie: gdzie mogę dowiedzieć się więcej o funkcji Kontakt z **administratorem** w portalu dla subskrybentów?
A: Zapoznaj się z [artykułem Kontakt z administratorem.](contact-my-admin.md) 

### <a name="q-if-we-dont-complete-the-contact-email-address-and-a-subscriber-uses-the-contact-my-admin-feature-who-receives-their-request"></a>Pytanie: Jeśli adres e-mail kontaktu nie zostanie  ukończony, a subskrybent użyje funkcji Skontaktuj się z administratorem, kto otrzyma żądanie? 
O: Jeśli w preferencji Kontaktowy  adres e-mail nie ustawiono żadnego konkretnego adresu e-mail, wszyscy administratorzy umowy otrzymają żądanie. 

## <a name="resources"></a>Zasoby
- [Visual Studio administracji i subskrypcji](https://aka.ms/vsadminhelp)

## <a name="see-also"></a>Zobacz też
- [Visual Studio dokumentacji](/visualstudio/)
- [Azure DevOps documentation (Dokumentacja usługi Azure DevOps)](/azure/devops/)
- [Dokumentacja platformy Azure](/azure/)
- [Microsoft 365 dokumentacji](/microsoft-365/)

## <a name="next-steps"></a>Następne kroki
Dowiedz się więcej o zarządzaniu Visual Studio subskrypcji.
- [Przypisywanie poszczególnych subskrypcji](assign-license.md)
- [Przypisywanie wielu subskrypcji](assign-license-bulk.md)
- [Edytowanie subskrypcji](edit-license.md)
- [Określanie maksymalnego użycia](maximum-usage.md)