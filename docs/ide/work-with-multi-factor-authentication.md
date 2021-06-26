---
title: Korzystanie z kont wymagających uwierzytelniania wieloskładnikowego
ms.date: 05/27/2020
ms.custom: SEO-VS-2020
ms.topic: conceptual
description: Dowiedz się, jak używać Visual Studio z kontami, które wymagają uwierzytelniania wieloskładnikowego.
author: j-martens
ms.author: jmartens
manager: jmartens
ms.workload:
- multiple
monikerRange: '>=vs-2019'
ms.openlocfilehash: 9ac42ccff8c7bffcc22c453002aad1caf6935d28
ms.sourcegitcommit: e4630a3bb89b4d606fe2cbd709bc773c5b538b78
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/26/2021
ms.locfileid: "112975677"
---
# <a name="how-to-use-visual-studio-with-accounts-that-require-multi-factor-authentication"></a>Jak używać Visual Studio z kontami, które wymagają uwierzytelniania wieloskładnikowego

Podczas współpracy z zewnętrznymi użytkownikami-gośćmi dobrym pomysłem jest ochrona aplikacji i danych przy użyciu zasad dostępu **warunkowego,** takich jak uwierzytelnianie wieloskładnikowe **(MFA).**  

Po włączeniu tej opcji użytkownicy-goście będą potrzebować więcej niż tylko nazwy użytkownika i hasła, aby uzyskać dostęp do zasobów, i muszą spełniać dodatkowe wymagania dotyczące zabezpieczeń. Zasady MFA można wymuszać na poziomie dzierżawy, aplikacji lub pojedynczego użytkownika-gościa, tak samo jak są one włączane dla członków w Twojej organizacji. 

## <a name="how-is-the-visual-studio-experience-affected-by-mfa-policies"></a>Jak na środowisko Visual Studio mają wpływ zasady MFA?
Wersje programu Visual Studio starsze niż 16.6 mogą mieć obniżoną wydajność uwierzytelniania, jeśli są używane z kontami, które mają włączone zasady urzędu certyfikacji, takie jak uwierzytelnianie wieloskładnikowe, i są skojarzone z co najmniej dwoma dzierżawami.

Te problemy mogą powodować wielokrotne monitowanie Visual Studio o ponowne uwierzytelnianie w ciągu dnia. Może być wymagane ponowne wdjęcie poświadczeń dla wcześniej uwierzytelnionych dzierżaw, nawet w trakcie tej samej Visual Studio dzierżawy.

## <a name="using-visual-studio-with-mfa-policies"></a>Używanie Visual Studio z zasadami MFA
W wersji 16.6 dodaliśmy nowe funkcje do programu Visual Studio 2019, które usprawniają sposób, w jaki użytkownicy mogą uzyskać dostęp do zasobów zabezpieczonych za pośrednictwem zasad urzędu certyfikacji, takich jak uwierzytelniania wieloskładnikowego. Aby korzystać z tego ulepszonego przepływu pracy, musisz zdecydować się na używanie domyślnej przeglądarki internetowej systemu jako mechanizmu dodawania i ponownego uwierzytelniania Visual Studio kont.  

> [!WARNING]
> Nieuprawnianie tego przepływu pracy może wyzwolić środowisko o obniżonej wydajności, co spowoduje wiele dodatkowych monitów o uwierzytelnienie podczas dodawania lub ponownego uwierzytelniania Visual Studio kont. 

### <a name="enabling-system-web-browser"></a>Włączanie systemowej przeglądarki internetowej

> [!NOTE] 
> Aby uzyskać najlepsze wyniki, zalecamy wyczyszczenie domyślnych danych przeglądarki internetowej systemu przed rozpoczęciem tego przepływu pracy. Ponadto jeśli masz konta służbowe w ustawieniach usługi Windows 10 w obszarze Uzyskaj dostęp do konta służbowego, sprawdź, czy są one prawidłowo uwierzytelnione.

Aby włączyć ten przepływ pracy, przejdź do okna dialogowego Opcje usługi Visual Studio  **(Narzędzia > Opcje...),**  wybierz kartę Konta i wybierz pozycję Przeglądarka sieci **Web** System z listy rozwijanej Dodaj i ponownie uwierzytelnij konta przy użyciu: . 

:::image type="content" source="media/select-system-web-browser.png" alt-text="Wybierz z menu pozycję System web browser (Systemowa przeglądarka internetowa).":::

### <a name="sign-into-additional-accounts-with-mfapolicies"></a>Logowanie się do dodatkowych kont przy użyciu zasad uwierzytelniania wieloskładnikowego 
Po włączeniu przepływu pracy przeglądarki sieci Web systemu można logować się lub dodawać konta do usługi Visual Studio w zwykły sposób za pośrednictwem okna dialogowego Ustawienia konta (Ustawienia konta usługi **>...).**   
</br>
:::image type="content" source="media/add-personalization-account.png" alt-text="Dodaj nowe konto personalizacji do Visual Studio." border="false":::

Ta akcja spowoduje otwarcie domyślnej przeglądarki internetowej systemu, poprosi o zalogowanie się do konta i zweryfikowanie wszystkich wymaganych zasad usługi MFA.

Podczas procesu logowania może zostać wyświetlony dodatkowy monit z prośbą o pozostanie zalogowanym. Ten monit będzie prawdopodobnie wyświetlany po raz drugi, gdy konto zostanie użyte do zalogowania. Aby zminimalizować konieczność ponownego wprowadzania poświadczeń, zalecamy wybranie opcji **Tak,** ponieważ zapewnia to zachowywanie poświadczeń między sesjami przeglądarki.

:::image type="content" source="media/kmsi.png" alt-text="Nie wy zalogowano się?":::

W oparciu o działania programowe i konfigurację zasobów może być nadal wyświetlany monit o ponowne wejrzenie poświadczeń podczas sesji. Taka możliwość może wystąpić podczas dodawania nowego zasobu lub próby uzyskania dostępu do zasobu bez wcześniejszego spełniania wymagań autoryzacji urzędu certyfikacji/usługi MFA.

## <a name="reauthenticating-an-account"></a>Ponowne uwierzytelnianie konta  
Jeśli masz problem z Twoim kontem, możesz Visual Studio poprosić o ponowne wprosienie poświadczeń konta.  

:::image type="content" source="media/reauthenticate-account.png" alt-text="Ponownie uwierzytelnij swoje Visual Studio konto.":::

Kliknięcie pozycji **Ponownie wentuj poświadczenia** spowoduje otwarcie domyślnej przeglądarki internetowej systemu i próba automatycznego odświeżenia poświadczeń. Jeśli to się nie powiedzie, zostanie poproszony o zalogowanie się do konta i zweryfikowanie wszystkich wymaganych zasad urzędu certyfikacji/uwierzytelniania wieloskładnikowego.

> [!NOTE] 
> Aby uzyskać najlepsze wyniki, nie otwieraj przeglądarki, dopóki wszystkie zasady urzędu certyfikacji/uwierzytelniania wieloskładnikowego nie zostaną zweryfikowane pod względem zasobów. Zamknięcie przeglądarki może spowodować utratę poprzednio sbudowaną stanu usługi MFA i może powodować monity o dodatkowe monity o autoryzację.

## <a name="how-to-opt-out-of-using-a-specific-azure-active-directory-tenant-in-visual-studio"></a>Jak zrezygnować z używania określonej Azure Active Directory dzierżawy w Visual Studio

Visual Studio 2019 w wersji 16.6 oferuje elastyczność filtrowania dzierżaw indywidualnie lub globalnie, efektywnie ukrywając je przed Visual Studio. Filtrowanie eliminuje konieczność uwierzytelniania w tej dzierżawie, ale oznacza również, że nie będzie można uzyskać dostępu do skojarzonych zasobów.

Ta funkcja jest przydatna, gdy masz wiele dzierżaw, ale chcesz zoptymalizować środowisko projektowe przez ukierunkowanie określonego podzestawu. Może to również pomóc w wystąpieniach, gdy nie można zweryfikować określonej zasady urzędu certyfikacji/uwierzytelniania wieloskładnikowego, ponieważ można odfiltrować dzierżawę, która jest zaniedbywalna. 

### <a name="how-to-filter-out-all-tenants"></a>Jak odfiltrować wszystkie dzierżawy
Aby globalnie odfiltrować wszystkie dzierżawy, otwórz okno dialogowe Ustawienia konta (Ustawienia konta usługi **>...)** i usuń zaznaczenie pola wyboru Uwierzytelnij we wszystkich katalogach usługi **Azure Active Directories.**

Usunięcie zaznaczenia tej opcji gwarantuje, że uwierzytelnianie będzie możliwe tylko w przypadku domyślnej dzierżawy konta. Oznacza to również, że nie będzie można uzyskać dostępu do żadnych zasobów skojarzonych z innymi dzierżawami, w których Twoje konto może być gościem.

### <a name="how-to-filter-out-individual-tenants"></a>Jak filtrować poszczególne dzierżawy
Aby filtrować dzierżawy skojarzone z kontem usługi Visual Studio, otwórz okno dialogowe Ustawienia konta (Ustawienia konta **>...)** i kliknij pozycję **Zastosuj filtr.** 
</br>
</br>

:::image type="content" source="media/apply-filter.png" alt-text="Zastosuj filtr." border="false":::

Zostanie **wyświetlone okno** dialogowe Filtrowanie konta, w którym można wybrać dzierżawy, których chcesz używać ze swoim kontem. 

:::image type="content" source="media/select-filter-account.png" alt-text="Wybierz konto do filtrowania.":::

## <a name="see-also"></a>Zobacz też

- [Logowanie do programu Visual Studio](signing-in-to-visual-studio.md)
- [Zaloguj się do Visual Studio dla komputerów Mac](/visualstudio/mac/signing-in)
- [Praca z wieloma kontami użytkowników](work-with-multiple-user-accounts.md)
