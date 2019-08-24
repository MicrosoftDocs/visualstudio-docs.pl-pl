---
title: Ustawianie preferencji umowy w portalu administracyjnym
author: evanwindom
ms.author: lank
manager: lank
ms.date: 08/21/2019
ms.topic: conceptual
description: Dowiedz się, jak ustawić preferencje dotyczące języka, kontaktów, poziomu subskrypcji i innych elementów w portalu administracyjnym
ms.openlocfilehash: 24e9ddfa92ee63e4d15eea086224e1069d4bcbc8
ms.sourcegitcommit: c90a998716b3dfa614dedc61a1bea515364efbec
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/23/2019
ms.locfileid: "70001441"
---
# <a name="set-preferences-for-your-agreements-in-the-administration-portal"></a>Ustawianie preferencji dla umów w portalu administracyjnym
Administratorzy Administratorzy mogą teraz ustawić pewne preferencje w portalu administracyjnym (portalu administracyjnym), które będą stosowane globalnie dla każdej umowy.  Preferencje te określają, które Administratorzy mogą ustawić podczas dodawania subskrybentów i mogą być modyfikowane tylko przez administratorów.  

## <a name="access-preferences"></a>Preferencje dostępu
Musisz zalogować się do [portalu administracyjnego](https://manage.visualstudio.com) przy użyciu identyfikatora logowania, który ma uprawnienia administratora na potrzeby wyświetlania lub modyfikowania preferencji.  

Aby ustawić preferencje:
1. Zaloguj się do portalu administracyjnego przy użyciu identyfikatora, który ma uprawnienia administratora.
2. Kliknij kartę **Zarządzanie administratorami** .
   > [!div class="mx-imgBorder"]
   > ![Przycisk preferencji administratora](_img/admin-prefs/admin-prefs-button.png)

3. Kliknij pozycję **Preferencje umowy**.
Panel zostanie otwarty po prawej stronie, a Twoje dostępne Preferencje zostaną wyświetlone. 

   > [!div class="mx-imgBorder"]
   > ![Okno dialogowe preferencji administratora](_img/admin-prefs/admin-prefs-flyout.png)

## <a name="set-your-preferences"></a>Ustawianie preferencji
Zapoznaj się z wszystkimi dostępnymi preferencjami i ich wpływami. 

### <a name="agreement"></a>Rozumie
Jeśli masz wiele umów, dla których jesteś administratorem, możesz wybrać odpowiednią umowę z listy rozwijanej.  Ustawione Preferencje będą stosowane tylko do tej umowy.  Indywidualni Administratorzy mogą przesłonić niektóre z tych preferencji w zależności od wielkości liter podczas przypisywania subskrypcji. 

Jeśli istnieje tylko jedna umowa skojarzona z adresem e-mail użytym do zalogowania się, zostanie wyświetlona i lista rozwijana zostanie wyłączona. 

### <a name="contact-email-address"></a>Kontaktowy adres e-mail
Dzięki tym preferencjom Subskrybenci mogą skontaktować się z administratorami za pomocą przycisku **skontaktuj się z administratorem** na [stronie Subskrypcje](https://my.visualstudio.com/subscriptions) portalu subskrybenta.  Jeśli ta preferencja pozostanie pusta, komunikaty subskrybenta będą przekazywane do wszystkich administratorów i administratorów w umowie.  Zalecamy użycie aliasu e-mail grupy lub grupy zabezpieczeń, aby dostosować odbiorców do tego kontaktu z adresem e-mail. Jeśli wolisz, możesz również wprowadzić adres e-mail osoby.

> [!NOTE]
> Podany tutaj adres e-mail nie zostanie dostarczony subskrybentom.  Gdy subskrybent przesyła żądanie **skontaktuj się z administratorem** w portalu subskrybenta, wiadomość zostanie przekazana do aliasu bez udostępniania go subskrybentom. 

### <a name="default-external-subscribers-setting"></a>Domyślne ustawienie subskrybentów zewnętrznych
To preferencja pozwala określić, czy Administratorzy mogą dodawać subskrybentów spoza dzierżawy/katalogu w organizacji.  Jeśli wyłączysz tę opcję, żaden subskrybent zewnętrzny nie będzie dozwolony.  Jeśli włączysz tę funkcję, a administrator podejmie próbę dodania subskrybenta zewnętrznego, zostanie poproszony o potwierdzenie wyboru i będzie można przypisać subskrypcję. Administratorzy nie mogą zastąpić tego ustawienia. 

### <a name="default-downloads-setting"></a>Domyślne ustawienie pobierania
Włączenie tego ustawienia, które domyślnie jest włączone, spowoduje umożliwienie subskrybentom dostępu do plików do pobrania, gdy administratorzy tworzą nowe subskrypcje.  Administratorzy nadal mogą wyłączyć pliki do pobrania w poszczególnych subskrypcjach.  

### <a name="default-subscription-level"></a>Domyślny poziom subskrypcji
Możesz użyć tego ustawienia, aby określić, które z poziomów subskrypcji uwzględnionych w umowie jest domyślnie zaznaczone, gdy subskrypcja jest przypisana do użytkownika.  Administratorzy mogą zmienić ustawienie na dowolny poziom subskrypcji w ramach umowy — to samo uniemożliwia konieczność wielokrotnego wyboru. 

### <a name="default-communication-preferences"></a>Domyślne preferencje komunikacji
Ustawienie domyślnego języka komunikacji i ustawień regionalnych może usprawnić proces przypisywania subskrypcji.  Na przykład jeśli zespół programistyczny jest oparty na innym kraju niż Twój zespół administracyjny, można ustawić preferencje najlepiej dopasowane do lokalizacji subskrybentów. Te ustawienia mogą być nadal zmieniane przez wszystkich administratorów dla poszczególnych subskrybentów. 

## <a name="frequently-asked-questions"></a>Często zadawane pytania
### <a name="q--can-i-disable-the-contact-email-address-so-subscribers-cannot-contact-administrators"></a>PYTANIA  Czy mogę wyłączyć **kontaktowy adres e-mail** , dzięki czemu Subskrybenci nie mogą kontaktować się z administratorami?
Odp.:  Nie — podczas określania, którzy Administratorzy są skontaktowani przy użyciu grupy zabezpieczeń, aliasu e-mail grupy lub indywidualnego adresu e-mail, nie można wyłączyć tej funkcji.

### <a name="q-if-i-answer-a-subscribers-email-will-they-have-my-email-address"></a>PYTANIA Czy w przypadku udzielenia odpowiedzi na wiadomość e-mail na subskrybencie będą mieć mój adres e-mail?
Odp.:  Ponieważ Twoja odpowiedź będzie pochodziła z używanego klienta poczty e-mail, odpowiedź odebrana przez subskrybenta będzie wyświetlana niezależnie od używanego adresu e-mail.  Dlatego, jeśli odpowiadasz za pomocą aliasu grupy, zobaczysz alias grupy.  Jeśli będziesz reagować na swój adres e-mail, zobaczysz to.  

### <a name="q-where-can-i-find-out-more-about-the-contact-my-admin-feature-in-the-subscriber-portal"></a>PYTANIA Gdzie mogę dowiedzieć się więcej o funkcji **skontaktuj się z administratorem** w portalu subskrybenta?
Odp.:  Zapoznaj się z artykułem dotyczącym [mojego administratora](contact-my-admin.md) . 

### <a name="q-if-we-dont-complete-the-contact-email-address-and-a-subscriber-uses-the-contact-my-admin-feature-who-receives-their-request"></a>PYTANIA Jeśli **adres E-mail osoby kontaktowej** nie zostanie zakończony, a subskrybent skorzysta z funkcji **skontaktuj się z administratorem** , który otrzyma żądanie?
Odp.:  Jeśli żaden konkretny adres e-mail nie zostanie ustawiony w preferencjach **adres E-mail osoby** , wszystkie Administratorzy na umowie otrzymają żądanie. 

## <a name="resources"></a>Zasoby
- [Pomoc techniczna dotycząca subskrypcji programu Visual Studio i administrowania nim](https://visualstudio.microsoft.com/support/support-overview-vs)

## <a name="next-steps"></a>Następne kroki
- Dowiedz się, jak [przypisywać subskrypcje](assign-license.md)
- Dowiedz się więcej na temat pełnego zakresu [korzyści z subskrypcji](https://visualstudio.microsoft.com/vs/benefits/)

