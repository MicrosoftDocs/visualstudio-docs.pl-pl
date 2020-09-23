---
title: Ustawianie preferencji umowy w portalu administracyjnym
author: evanwindom
ms.author: v-evwin
manager: cabuschl
ms.assetid: 0fe9eaa4-f589-429e-a443-13bf86637d5a
ms.date: 09/21/2020
ms.topic: conceptual
description: Dowiedz się, jak ustawić preferencje dotyczące języka, kontaktów, poziomu subskrypcji i innych elementów w portalu administracyjnym
ms.openlocfilehash: 58819995966f5cdf17335de474e83d2a77eccc37
ms.sourcegitcommit: 4affcf2830337e6aba84621c3eda5faf5d0d4a01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/23/2020
ms.locfileid: "91022617"
---
# <a name="set-preferences-for-your-agreements-in-the-administration-portal"></a>Ustawianie preferencji dla umów w portalu administracyjnym
Administratorzy mogą ustawić pewne preferencje w portalu administracyjnym (portalu administracyjnym), które będą stosowane globalnie dla każdej umowy.  Te preferencje automatycznie wypełniają szczegóły subskrypcji dla administratorów podczas dodawania subskrybentów i mogą być modyfikowane tylko przez administratorów.  

## <a name="access-preferences"></a>Preferencje dostępu
Musisz zalogować się do [portalu administracyjnego](https://manage.visualstudio.com) przy użyciu identyfikatora logowania, który ma uprawnienia administratora na potrzeby wyświetlania lub modyfikowania preferencji.  

Aby ustawić preferencje:
1. Zaloguj się do portalu administracyjnego przy użyciu identyfikatora, który ma uprawnienia administratora.
2. Kliknij ikonę ustawienia w okienku po lewej stronie.
   > [!div class="mx-imgBorder"]
   > ![Przycisk preferencji administratora](_img/admin-prefs/admin-prefs-button.png "Kliknij kolejno pozycje Zarządzaj administratorami, a następnie Preferencje umów, aby wyświetlić Preferencje")

3. Kliknij pozycję **Preferencje umowy**.
Panel zostanie otwarty po lewej stronie, a Twoje dostępne Preferencje zostaną wyświetlone. 

   > [!div class="mx-imgBorder"]
   > ![Okno dialogowe preferencji administratora](_img/admin-prefs/admin-prefs-flyout.png "Ustaw preferencje i kliknij przycisk Zapisz.")

## <a name="set-your-preferences"></a>Ustawianie preferencji
Zapoznaj się z wszystkimi dostępnymi preferencjami i ich wpływami. 

### <a name="agreement"></a>Umowa
Jeśli masz wiele umów, dla których jesteś administratorem, możesz wybrać odpowiednią umowę z listy rozwijanej z prawej strony panelu Ustawienia rozwinięte.  Ustawione Preferencje będą stosowane tylko do tej umowy.  Indywidualni Administratorzy mogą przesłonić niektóre z tych preferencji w zależności od wielkości liter podczas przypisywania subskrypcji. 

Jeśli istnieje tylko jedna umowa skojarzona z adresem e-mail użytym do zalogowania się, zostanie ona wyświetlona po prawej stronie panelu Ustawienia rozwinięte i lista rozwijana zostanie wyłączona. 

### <a name="contact-email-address"></a>Kontaktowy adres e-mail
Dzięki temu Subskrybenci mogą skontaktować się z administratorami za pomocą przycisku **skontaktuj się z administratorem** na [stronie Subskrypcje](https://my.visualstudio.com/subscriptions) portalu subskrybenta.  Jeśli ta preferencja pozostanie pusta, komunikaty subskrybenta będą przekazywane do wszystkich administratorów i administratorów w umowie.  Zalecamy użycie aliasu e-mail grupy lub grupy zabezpieczeń, aby dostosować odbiorców do tego kontaktu z adresem e-mail. Jeśli wolisz, możesz również wprowadzić adres e-mail osoby.

> [!NOTE]
> Podany tutaj adres e-mail nie zostanie dostarczony subskrybentom.  Gdy subskrybent przesyła żądanie **skontaktuj się z administratorem** w portalu subskrybenta, wiadomość zostanie przekazana do aliasu bez udostępniania go subskrybentowi. 

### <a name="default-subscription-level"></a>Domyślny poziom subskrypcji
Możesz użyć tego ustawienia, aby określić, które z poziomów subskrypcji uwzględnionych w umowie jest domyślnie zaznaczone, gdy subskrypcja jest przypisana do użytkownika.  Administratorzy mogą zmienić ustawienie na dowolny poziom subskrypcji w ramach umowy — to samo uniemożliwia konieczność wielokrotnego wyboru. 

### <a name="default-communication-preferences"></a>Domyślne preferencje komunikacji
Ustawienie domyślnego języka komunikacji i ustawień regionalnych może usprawnić proces przypisywania subskrypcji.  Na przykład jeśli zespół programistyczny jest oparty na innym kraju niż Twój zespół administracyjny, można ustawić preferencje najlepiej dopasowane do lokalizacji subskrybentów. Te ustawienia mogą być nadal zmieniane przez wszystkich administratorów dla poszczególnych subskrybentów. 

### <a name="default-external-subscribers-setting"></a>Domyślne ustawienie subskrybentów zewnętrznych
To preferencja pozwala określić, czy Administratorzy mogą dodawać subskrybentów spoza dzierżawy/katalogu w organizacji.  Jeśli wyłączysz tę opcję, żaden subskrybent zewnętrzny nie będzie dozwolony.  Jeśli włączysz tę funkcję, a administrator podejmie próbę dodania subskrybenta zewnętrznego, zostanie poproszony o potwierdzenie wyboru i będzie można przypisać subskrypcję. Administratorzy nie mogą zastąpić tego ustawienia. 

### <a name="default-downloads-setting"></a>Domyślne ustawienie pobierania
Włączenie tego ustawienia, które domyślnie jest włączone, spowoduje umożliwienie subskrybentom dostępu do plików do pobrania, gdy administratorzy tworzą nowe subskrypcje.  Administratorzy nadal mogą wyłączyć pliki do pobrania w poszczególnych subskrypcjach.  Wyłączenie dostępu do plików do pobrania powoduje także wyłączenie dostępu do kluczy produktów.  


## <a name="frequently-asked-questions"></a>Często zadawane pytania
### <a name="q--can-i-disable-the-contact-email-address-so-subscribers-cannot-contact-administrators"></a>P: Czy można wyłączyć **kontaktowy adres e-mail** , aby Subskrybenci nie mogli skontaktować się z administratorami?
Odp.: nie — podczas określania, którzy Administratorzy są skontaktowani przy użyciu grupy zabezpieczeń, aliasu e-mail grupy lub indywidualnego adresu e-mail, nie można wyłączyć tej funkcji.

### <a name="q-if-i-answer-a-subscribers-email-will-they-have-my-email-address"></a>P: Jeśli odpowieem adres e-mail subskrybenta, czy ma mój adres e-mail?
Odp.: od momentu odebrania odpowiedzi od dowolnego klienta poczty e-mail, odpowiedź odbierana przez subskrybenta będzie zawierać adres e-mail, z którego korzystasz.  Dlatego, jeśli odpowiadasz za pomocą aliasu grupy, zobaczysz alias grupy.  Jeśli będziesz reagować na swój adres e-mail, zobaczysz to.  

### <a name="q-where-can-i-find-out-more-about-the-contact-my-admin-feature-in-the-subscriber-portal"></a>P: gdzie można dowiedzieć się więcej o funkcji **skontaktuj się z administratorem** w portalu subskrybenta?
Odp.: Zapoznaj [się z](contact-my-admin.md) artykułem dotyczącym mojego administratora. 

### <a name="q-if-we-dont-complete-the-contact-email-address-and-a-subscriber-uses-the-contact-my-admin-feature-who-receives-their-request"></a>Pytanie: Jeśli nie dokończysz **kontaktu z adresem e-mail** i subskrybentem korzysta z funkcji **skontaktuj się z administratorem** , która otrzymuje żądanie?
Odp.: Jeśli nie określono określonego adresu e-mail w preferencjach **adres e-mail do kontaktu** , wszystkie Administratorzy na umowie otrzymają żądanie. 

## <a name="resources"></a>Zasoby
- [Pomoc techniczna dotycząca subskrypcji programu Visual Studio i administrowania nim](https://visualstudio.microsoft.com/support/support-overview-vs)

## <a name="see-also"></a>Zobacz też
- [Dokumentacja programu Visual Studio](/visualstudio/)
- [Dokumentacja usługi Azure DevOps](/azure/devops/)
- [Dokumentacja platformy Azure](/azure/)
- [Dokumentacja Microsoft 365](/microsoft-365/)

## <a name="next-steps"></a>Następne kroki
Dowiedz się więcej o zarządzaniu subskrypcjami programu Visual Studio.
- [Przypisywanie pojedynczych subskrypcji](assign-license.md)
- [Przypisywanie wielu subskrypcji](assign-license-bulk.md)
- [Edytowanie subskrypcji](edit-license.md)
- [Określanie maksymalnego użycia](maximum-usage.md)