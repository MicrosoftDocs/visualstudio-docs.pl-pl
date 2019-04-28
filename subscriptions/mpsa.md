---
title: Subskrypcje programu Visual Studio w produkty firmy Microsoft i umowy o świadczenie usług (MPSA) | Dokumentacja firmy Microsoft
author: evanwindom
ms.author: jaunger
manager: evelynp
ms.date: 03/14/2018
ms.topic: conceptual
description: Subskrypcje programu Visual Studio w produkty firmy Microsoft i umowy o świadczenie usług (MPSA)
searchscope: VS Subscription
ms.openlocfilehash: cf0a6c0c7f09cefa70edd0af1dcedf46afdf81bf
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "63002321"
---
# <a name="visual-studio-subscriptions-in-a-microsoft-products-and-services-agreement-mpsa"></a>Subskrypcje programu Visual Studio w Microsoft Products and Services Agreement (MPSA)

Jeśli zakupiono subskrypcji programu Visual Studio za pośrednictwem programu umowy MPSA, istnieje kilka kwestii, które należy zwrócić uwagę przed może stać się administratorem subskrypcji programu Visual Studio i przypisywanie subskrypcji dla użytkowników. Jeśli możesz już skonfigurowano jako administrator, a następnie możesz przejść bezpośrednio do subskrypcji programu Visual Studio [portalu administracyjnego](https://manage.visualstudio.com/).

Jako klient korzystający z umowami MPSA zostaną wprowadzone do portalu, w którym możesz zarządzać Twoje zasoby, które zostały zakupione w ramach umowy MPSA. Nosi nazwę tego nowego portalu [Centrum biznesowych](https://businessaccount.microsoft.com/), który obsługuje niektóre z tych samych i nowe funkcje po prostu takich jak wolumin licencjonowania Service Center (VLSC). Obejmują one, wyświetlając Twoje podsumowanie licencji, pliki do pobrania, klucze, użytkownicy, itp. Jednak subskrypcje programu Visual Studio MPSA znacznie przypominają usług w chmurze. Centrum firmy używa również kont służbowych do logowania, zamiast Accounts firmy Microsoft. Jeśli Twoja organizacja korzysta z usług cloud services, takich jak usługi Office 365 lub Azure Active Directory, a Twój adres e-mail jest częścią żadnego z tych dwóch usług, nie będzie już konto służbowe. To pozwala zarejestrować się do Centrum firmy przy użyciu istniejącego hasła, które Twoja organizacja wyznaczone do Ciebie. Jeśli organizacja nie korzysta z usług w chmurze i swój adres e-mail nie jest konto służbowe w ogóle, nie martw się, jak korzystać z niej rejestrować się w Centrum firmy.

Ponadto subskrypcje programu Visual Studio [portalu administracyjnego](https://manage.visualstudio.com/) jest, gdzie subskrypcje zostaną przypisane do subskrybentów po staje się administratorem programu Visual Studio. MPSA subskrypcje programu Visual Studio musi być przygotowana do portalu zarządzania odpowiednich, który jest portalem administratora subskrypcji programu Visual Studio. Aby to zrobić, należy skojarzyć swoje konto zakupu do dzierżawy (np. contoso.onmicrosoft.com).

Należy pamiętać, że istnieją dwa typy dzierżaw (dzierżawy zarządzanej i niezarządzanej dzierżawy). Zarządzanej dzierżawy odnosi się do dzierżawy, który jest już zarządzany przez organizację jako administratorów w ramach.

Niezarządzana dzierżawa jest bez żadnych administratorów w ramach dzierżawy i nie jest używany dla usług Online, takich jak Office 365. Niezarządzanej dzierżawy są również tworzone podczas rejestrowania w Centrum firmy, za pomocą adresu e-mail, który nie jest konto służbowe. Jeśli zostały pytanie, aby utworzyć hasło podczas rejestrowania w Centrum firmy, następnie oznacza to, że Twój adres e-mail nie jest konto służbowe i ona utworzona niezarządzana dzierżawa.

Przed ukończenie skojarzenie dzierżawy poniżej przedstawiono kilka wymagań/czynnościach, które Aby zostać administratorem subskrypcji programu Visual Studio.

## <a name="pre-tenant-association-managed-tenant"></a>Skojarzenie wstępne dzierżawy (zarządzanego dzierżawcy)

- Musi być zarejestrowany użytkownik do centrum danych firmy.
- W ramach dzierżawy, które są częścią musi być użytkownika administratora (minimum) lub administrator globalny. (Dotyczy to jeśli firma korzysta już z usług w chmurze). Każda rola jest wymagana do administratora subskrypcji programu Visual Studio.
- Musisz być administratorem globalnym w dzierżawie, które są częścią, aby można było skojarzyć swoje konto zakupu dla Twojej dzierżawy.
- Musi być administratorem konta lub menedżerem w Centrum firmy.
- Pole "Kraj lub Region" w ramach profilu użytkownika (i innych użytkowników) [Azure](https://portal.azure.com/) musi być wypełnione odpowiednio w zależności od regionu (czyli Stany Zjednoczone, urzędu certyfikacji itp.). 

> [!NOTE]
> Użytkownicy, którzy mają być administratorów subskrypcji programu Visual Studio nie są wymagane do użytkowników w Centrum firmy, zgodnie z zapotrzebowaniem spełnia ono kryteriów w krokach 2 i 5.

Gdy są spełnione kryteria w powyższych krokach 5 możesz skojarzyć swoje konto zakupu dla Twojej dzierżawy, poniższe kroki.
1. Zaloguj się do [Centrum biznesowych](https://businessaccount.microsoft.com/).
2. Kliknij pozycję **konta** kartę i wybierz polecenie **kojarzenie domen**.
3. Wybierz swoje **Zakup konto** (Jeśli masz więcej niż jeden).
4. Wybierz swoje **dzierżawy** (np. contoso.onmicrosoft.com).
5. Kliknij przycisk **skojarzenia domeny**.

Po dokonaniu skojarzenia wszyscy użytkownicy spełniający kryteria wymagane zwykle przydzieli jako administratorów subskrypcji programu Visual Studio w ciągu kilku minut. Jednak czasami może potrwać do 24 godzin. Po zainicjowaniu będzie można uzyskać dostęp portalem administratora subskrypcji programu Visual Studio. Trwa to dłużej niż 24 godziny, skontaktuj się z umowami MPSA pomocy technicznej.

> [!NOTE]
> W przypadku nowych użytkowników, które spełniają kryteria w krokach 2 i 5 (po skojarzeniu) możesz skontaktować się pomoc techniczna MPSA. Pomoc techniczna MPSA zapewni pomoc do aprowizowania nowych administratorów subskrypcji programu Visual Studio.

## <a name="tenant-association-unmanaged"></a>Skojarzenie dzierżawy (niezarządzany)

Jeśli zarejestrowano się w Centrum firmy, za pomocą adresu e-mail, które nie były konta służbowego (nie zarejestrowane w usłudze Azure Active Directory "Azure AD"), jak wyjaśniono w akapicie 5 powyżej, skojarzenie dzierżawy będą nieco inne. Należy wykonać, co jest określana mianem "przejęcia domeny". W trakcie tego procesu wykonasz samodzielnie Administrator globalny, co spowoduje zmianę dzierżawy z niezarządzanych w zarządzanych.

Aby uzyskać bardziej szczegółowe informacje na temat tego procesu, możesz użyć [— Szybki Start zawiera informacje na temat](https://www.microsoft.com/en-us/Licensing/existing-customer/business-center-training-and-resources.aspx). Pobierz Przewodnik o nazwie *"Instalacji i użycie Twojej usługi Online"* który przeprowadzi Cię przez przejęcia domeny. Po zakończeniu tego procesu zakupu konta zostanie również skojarzony z dzierżawą.

> [!NOTE]
> Po ukończeniu procesu przejęcia domeny, musisz spełnić kryteria pięć kroków w sekcji dla skojarzenia dzierżawy Pre (kod zarządzany). Po spełnieniu kryteriów tylko należy się z pomocą techniczną umowy MPSA, aby aprowizować kolejnych administratorów subskrypcji programu Visual Studio.

Może się z pomocą techniczną za pośrednictwem telefonu lub adresu e-mail, jeśli potrzebują pomocy lub masz pytania.

Pomoc techniczna MPSA: **1-866-200-9611**, dostępny od poniedziałku do piątku 5:30:00 do 5:30 PM czasu pacyficznego

Adres e-mail: ngvlsup@microsoft.com
