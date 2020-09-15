---
title: Korzystanie z kont wymagających uwierzytelniania wieloskładnikowego
ms.date: 05/27/2020
ms.custom: SEO-VS-2020
ms.topic: conceptual
description: Dowiedz się, jak używać programu Visual Studio z kontami, które wymagają uwierzytelniania wieloskładnikowego.
author: ornellaalt
ms.author: ornella
manager: jillfra
ms.workload:
- multiple
monikerRange: '>=vs-2019'
ms.openlocfilehash: ebacdd78cbb72bbd1cb90a0b5c719d0c753a95ca
ms.sourcegitcommit: a18c7e9b367c2f92f6e54c3eaef442775d457667
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/15/2020
ms.locfileid: "90093354"
---
# <a name="how-to-use-visual-studio-with-accounts-that-require-multi-factor-authentication"></a>Jak używać programu Visual Studio z kontami, które wymagają uwierzytelniania wieloskładnikowego

Podczas współpracy z zewnętrznymi użytkownikami-gość warto chronić aplikacje i dane za pomocą zasad **dostępu warunkowego (CA)** , takich jak **uwierzytelnianie wieloskładnikowe (MFA)**.  

Po włączeniu użytkownicy-Goście będą musieli uzyskać więcej niż tylko nazwę użytkownika i hasło, aby uzyskać dostęp do zasobów i muszą spełniać dodatkowe wymagania dotyczące zabezpieczeń. Zasady MFA można wymuszać na poziomie dzierżawy, aplikacji lub pojedynczego użytkownika-gościa, tak samo jak są one włączane dla członków w Twojej organizacji. 

## <a name="how-is-the-visual-studio-experience-affected-by-mfa-policies"></a>W jaki sposób środowisko Visual Studio ma wpływ na zasady usługi MFA?
Wersje programu Visual Studio starsze niż 16,6 mogą mieć obniżone działania związane z uwierzytelnianiem, gdy są używane z kontami z włączonymi zasadami urzędu certyfikacji, takimi jak MFA, i są skojarzone z co najmniej dwoma dzierżawcami.

Te problemy mogą spowodować, że wystąpienie programu Visual Studio będzie monitować o ponowne uwierzytelnienie wielokrotnie dziennie. Może być konieczne ponowne wprowadzenie poświadczeń dla wcześniej uwierzytelnionych dzierżawców, nawet w ramach tej samej sesji programu Visual Studio.

## <a name="using-visual-studio-with-mfa-policies"></a>Korzystanie z programu Visual Studio z zasadami usługi MFA
W wersji 16,6 dodaliśmy nowe możliwości do programu Visual Studio 2019, które ułatwiają użytkownikom dostęp do zasobów zabezpieczonych za pośrednictwem zasad urzędu certyfikacji, takich jak MFA. Aby korzystać z tego ulepszonego przepływu pracy, należy zadecydować o użyciu domyślnej przeglądarki sieci Web systemu jako mechanizmu dodawania i ponownego uwierzytelniania kont programu Visual Studio.  

> [!WARNING]
> Nie można używać tego przepływu pracy, który może wyzwolić obniżenie wydajności, co powoduje wielokrotne wyświetlanie dodatkowych wierszy uwierzytelniania przy dodawaniu lub ponownym uwierzytelnianiu kont programu Visual Studio. 

### <a name="enabling-system-web-browser"></a>Włączanie przeglądarki sieci Web systemu

> [!NOTE] 
> Aby uzyskać najlepsze doświadczenia, zalecamy wyczyszczenie domyślnych danych przeglądarki sieci Web systemu przed kontynuowaniem tego przepływu pracy. Ponadto jeśli masz konta służbowe w ustawieniach systemu Windows 10 w obszarze **dostęp do zasobów służbowych**, sprawdź, czy są one prawidłowo uwierzytelniane.

Aby włączyć ten przepływ pracy, przejdź do okna dialogowego Opcje programu Visual Studio **(narzędzia > opcje...)**, wybierz kartę **konta** i opcję Wybierz **systemową przeglądarkę internetową** w obszarze **Dodaj i ponownie Uwierzytelnij konta przy użyciu:** lista rozwijana. 

:::image type="content" source="media/select-system-web-browser.png" alt-text="Z menu wybierz opcję systemowa przeglądarka sieci Web.":::

### <a name="sign-into-additional-accounts-with-mfapolicies"></a>Logowanie się do dodatkowych kont przy użyciu zasad usługi MFA 
Po włączeniu przepływu pracy przeglądarki sieci Web systemu można zalogować się lub dodać konta do programu Visual Studio, jak zwykle, za pomocą okna dialogowego Ustawienia konta **(Ustawienia konta > pliku...)**.   
</br>
:::image type="content" source="media/add-personalization-account.png" alt-text="Dodaj nowe konto personalizacji do programu Visual Studio." border="false":::

Ta akcja spowoduje otwarcie domyślnej przeglądarki sieci Web systemu, poproszenie Cię o zalogowanie się do konta i zweryfikowanie wymaganych zasad MFA.

W trakcie procesu logowania może zostać wyświetlony dodatkowy monit z prośbą o pozostawanie zalogowania. Ten monit będzie prawdopodobnie wyświetlany podczas drugiego logowania do konta. Aby zminimalizować konieczność ponownego wprowadzania poświadczeń, zalecamy wybranie **opcji tak**, ponieważ dzięki temu poświadczenia są zachowywane w sesjach przeglądarki.

:::image type="content" source="media/kmsi.png" alt-text="Pozostać zalogowanym?":::

W oparciu o działania deweloperskie i konfigurację zasobów nadal może zostać wyświetlony monit o ponowne wprowadzenie poświadczeń podczas sesji. Taka sytuacja może wystąpić, gdy dodasz nowy zasób lub spróbujesz uzyskać dostęp do zasobu bez wcześniejszego spełnienia wymagań związanych z autoryzacją urzędu certyfikacji/MFA.

## <a name="reauthenticating-an-account"></a>Reuwierzytelnianie konta  
Jeśli wystąpi problem z Twoim kontem, program Visual Studio może poprosił o ponownie wprowadzenie poświadczeń konta.  

:::image type="content" source="media/reauthenticate-account.png" alt-text="Ponownie Uwierzytelnij Twoje konto programu Visual Studio.":::

Kliknięcie przycisku **ponownie wprowadź poświadczenia** spowoduje otwarcie domyślnej przeglądarki sieci Web systemu i próba automatycznego odświeżenia poświadczeń. Jeśli nie powiedzie się, zostanie wyświetlony monit o zalogowanie się do konta i zweryfikowanie wszystkich wymaganych zasad urzędu certyfikacji/MFA.

> [!NOTE] 
> W celu uzyskania najlepszego środowiska przeglądarka zostanie otwarta, dopóki wszystkie zasady urzędu certyfikacji/MFA nie zostaną zweryfikowane dla Twoich zasobów. Zamknięcie przeglądarki może spowodować utratę poprzednio skompilowanego stanu usługi MFA i może monitować o dodatkowe monity o autoryzację.

## <a name="how-to-opt-out-of-using-a-specific-azure-active-directory-tenant-in-visual-studio"></a>Jak zrezygnować z używania określonej dzierżawy Azure Active Directory w programie Visual Studio

Program Visual Studio 2019 w wersji 16,6 oferuje elastyczność filtrowania określonych dzierżawców, co ukrywa je w programie Visual Studio. Filtrowanie eliminuje konieczność uwierzytelniania w tej dzierżawie, ale oznacza również, że nie będzie można uzyskać dostępu do żadnych skojarzonych zasobów. 

Ta funkcja jest przydatna, gdy masz wiele dzierżawców, ale chcesz zoptymalizować środowisko programistyczne, przeznaczoną dla określonego podzestawu. Może również pomóc w wystąpieniu, gdy nie można sprawdzić poprawności określonych zasad urzędu certyfikacji/MFA, ponieważ można odfiltrować nieprawidłową dzierżawę. 

### <a name="how-to-filter-out-a-tenant"></a>Jak odfiltrować dzierżawcę
Aby filtrować dzierżawców skojarzonych z Twoim kontem programu Visual Studio, Otwórz okno dialogowe Ustawienia konta **(Ustawienia konta > pliku...)** i kliknij przycisk **Zastosuj filtr**. 
</br>
</br>

:::image type="content" source="media/apply-filter.png" alt-text="Zastosuj filtr." border="false":::

Zostanie wyświetlone okno dialogowe **filtrowanie konta** umożliwiające wybranie dzierżawców, które mają być używane z Twoim kontem. 

:::image type="content" source="media/select-filter-account.png" alt-text="Wybierz pozycję konto do filtrowania.":::

## <a name="see-also"></a>Zobacz także

- [Logowanie do programu Visual Studio](signing-in-to-visual-studio.md)
- [Zaloguj się do Visual Studio dla komputerów Mac](/visualstudio/mac/signing-in)
- [Praca z wieloma kontami użytkowników](work-with-multiple-user-accounts.md)
