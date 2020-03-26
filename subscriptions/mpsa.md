---
title: Subskrypcje programu Visual Studio w umowie dotyczącej produktów i usług firmy Microsoft (MPSA)| Dokumenty firmy Microsoft
author: evanwindom
ms.author: lank
manager: lank
ms.assetid: b331c837-3524-42b7-820e-b4fdd5e12793
ms.date: 03/03/2020
ms.topic: conceptual
description: Subskrypcje programu Visual Studio w umowie dotyczącej produktów i usług firmy Microsoft (MPSA)
ms.openlocfilehash: e59929404febda5a07ba13f7dc230ab89e09addf
ms.sourcegitcommit: eeff6f675e7850e718911647343c5df642063d5e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2020
ms.locfileid: "80232201"
---
# <a name="visual-studio-subscriptions-in-a-microsoft-products-and-services-agreement-mpsa"></a>Subskrypcje programu Visual Studio w umowie dotyczącej produktów i usług firmy Microsoft (MPSA)
Jeśli zakupiono subskrypcje programu Visual Studio za pośrednictwem programu MPSA, należy pamiętać o kilku rzeczach, zanim będzie można stać się administratorem subskrypcji programu Visual Studio i przypisać subskrypcje do użytkowników. Jeśli zostałeś już skonfigurowany jako administrator, możesz przejść bezpośrednio do [portalu administracyjnego](https://manage.visualstudio.com/)subskrypcji programu Visual Studio .

Klienci MPSA zarządzają teraz zasobami zakupionymi za pośrednictwem protokołu MPSA w nowym portalu o nazwie [Business Center,](https://businessaccount.microsoft.com/Customer)który obsługuje funkcje podobne do Centrum usług licencjonowania zbiorowego (VLSC). Obejmują one wyświetlanie podsumowania licencji, zamówień, pobrań, kluczy, użytkowników itp. Jednak subskrypcje programu Visual Studio w mpsa zachowują się podobnie jak usługi w chmurze. Centrum biznesowe używa również kont służbowych do logowania się zamiast kont Microsoft (MSA). Jeśli twoja organizacja korzysta z usług w chmurze, takich jak Office 365 lub Azure Active Directory, a poczta e-mail jest częścią jednej z tych dwóch usług, jest już kontem służbowym. Dzięki temu możesz zarejestrować się w Business Center przy za pomocą istniejącego hasła. Jeśli twoja organizacja nie korzysta z usług w chmurze, a poczta e-mail nie jest kontem służbowym, możesz użyć jej do zarejestrowania się w Centrum biznesowym.

Ponadto [portal administracyjny](https://manage.visualstudio.com/) subskrypcji programu Visual Studio jest miejscem, w którym subskrypcje będą przypisywane subskrybentom, gdy staniesz się administratorem subskrypcji programu Visual Studio. W mpsa subskrypcji programu Visual Studio muszą być aprowidzone do ich odpowiedniego portalu zarządzania, który jest Visual Studio Subscriptions Administration Portal. Aby to zrobić, musisz powiązać swoje konto zakupowe z najemcą (tj. contoso.onmicrosoft.com).

Należy pamiętać, że istnieją dwa typy dzierżaw - dzierżaw zarządzanych i niezarządzanych dzierżaw. Dzierżawa zarządzana odnosi się do dzierżawy, która jest już zarządzana przez administratorów w organizacji.

Dzierżawa niezarządzana jest dzierżawą bez przypisanych administratorów i nie jest użyteczna dla usług online, takich jak Office 365. Dzierżawy niezarządzane są również tworzone podczas rejestrowania się w Centrum biznesowym za pomocą wiadomości e-mail, która nie jest kontem służbowym. Jeśli podczas rejestracji w Centrum biznesowym zostaniesz poproszony o utworzenie hasła, oznacza to, że twój adres e-mail nie był kontem służbowym i utworzył niezarządzaną dzierżawę.

Oto kilka wymagań/kroków potrzebnych do zostania administratorem subskrypcji programu Visual Studio przed ukończeniem skojarzenia dzierżawy.

## <a name="pre-tenant-association-managed-tenant"></a>Stowarzyszenie przed dzierżawą (dzierżawa zarządzana)
- Musisz być zarejestrowanym użytkownikiem w Centrum biznesowym.
- Musisz być administratorem użytkownika (co najmniej) lub administratorem globalnym w dzierżawie, której jesteś częścią. (Ma to zastosowanie, jeśli Twoja firma korzysta już z usług w chmurze). Każda rola jest potrzebna do administratora subskrypcji programu Visual Studio.
- Musisz być administratorem globalnym w dzierżawie, której jesteś częścią, aby móc skojarzyć swoje konto zakupowe z dzierżawą.
- Musisz być administratorem konta lub Menedżerem kont w Centrum biznesowym.
- Pole "Kraj lub region" w profilu użytkownika (i innych użytkowników) na [platformie Azure](https://portal.azure.com/) musi zostać odpowiednio wypełnione w zależności od regionu (np. 

> [!NOTE]
> Wszyscy użytkownicy, którzy mają zostać administratorami subskrypcji programu Visual Studio, nie muszą być użytkownikami w Centrum biznesowym, ponieważ muszą spełniać tylko kryteria 2 i 5.

Po spełnieniu powyższych kryteriów możesz przystąpić do skojarzenia swojego konta zakupowego z najemcą, wykonując poniższe czynności.
1. Zaloguj się do [Centrum biznesowego](https://businessaccount.microsoft.com/Customer).
2. Kliknij kartę **Konto** i wybierz pozycję **Skojarz domeny**.
3. Wybierz swoje **konto zakupowe** (jeśli masz więcej niż jedno).
4. Wybierz **dzierżawę** (np. contoso.onmicrosoft.com).
5. Kliknij pozycję **Skojarz domenę**.

Po skojarzeniu wszyscy użytkownicy spełniający kryteria zazwyczaj będą aprowizować jako administratorzy subskrypcji programu Visual Studio w ciągu kilku minut. Jednak czasami może to potrwać do 24 godzin. Po udostępnieniu dzierżawy będzie można uzyskać dostęp do portalu administracyjnego subskrypcji programu Visual Studio. Jeśli trwa to dłużej niż 24 godziny, skontaktuj się z pomocą techniczną MPSA, wykonując następujące czynności:
1. Połącz się zhttps://www.microsoft.com/licensing/mpsa/default
2. Kliknij menu **Więcej** u góry strony. 
3. Wybierz **pomoc techniczną**
4. Wybieranie **pomocy technicznej licencjonowania**
5. Wybierz opcję wsparcia, która najlepiej odpowiada Twoim potrzebom. 

> [!NOTE]
> Jeśli są nowi użytkownicy, którzy spełniają kryteria w krokach 2 i 5 (po skojarzeniu), należy skontaktować się z pomocą techniczną MPSA. Obsługa MPSA zapewni pomoc w celu aprowizowania nowych administratorów subskrypcji programu Visual Studio.

## <a name="tenant-association-unmanaged"></a>Skojarzenie dzierżawy (niezarządzane)
Jeśli zarejestrowałeś się w centrum biznesowym za pomocą wiadomości e-mail, która nie była kontem służbowym (nie zarejestrowanym w usłudze Azure Active Directory "Azure AD"), jak wyjaśniono powyżej, skojarzenie dzierżawy będzie się nieco różnić. Musisz wykonać tak zwane "przejęcie domeny". Podczas tego procesu zostaniesz administratorem globalnym, który zmieni dzierżawę z niezarządzanej na zarządzaną.

Aby uzyskać bardziej szczegółowe wyjaśnienie tego procesu, można użyć [przewodników Szybki start](https://www.microsoft.com/Licensing/existing-customer/business-center-training-and-resources.aspx). Pobierz przewodnik o nazwie *"Konfiguracja i korzystanie z usług online",* który poprowadzi Cię przez przejęcie domeny. Po zakończeniu twoje konto zakupowe będzie również powiązane z twoją dzierżawą.

> [!NOTE]
> Po zakończeniu procesu przejęcia domeny, należy przestrzegać kryteriów z pięciu kroków w sekcji dla pre tenant Association (Zarządzane). Po spełnieniu kryteriów konieczne będzie skontaktowanie się tylko z pomocą techniczną MPSA w celu zainicjowania dodatkowych administratorów subskrypcji programu Visual Studio.

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
- [Usuwanie subskrypcji](delete-license.md)
- [Określanie maksymalnego użycia](maximum-usage.md)
