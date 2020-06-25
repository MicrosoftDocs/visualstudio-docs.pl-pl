---
title: Subskrypcje programu Visual Studio w ramach umowy dotyczącej produktów i usług firmy Microsoft (MPSA) | Microsoft Docs
author: evanwindom
ms.author: lank
manager: lank
ms.assetid: b331c837-3524-42b7-820e-b4fdd5e12793
ms.date: 03/03/2020
ms.topic: conceptual
description: Subskrypcje programu Visual Studio w ramach umowy dotyczącej produktów i usług firmy Microsoft (MPSA)
ms.openlocfilehash: d38da1784eb543519f1a36ba7342f0b13ab2b1ac
ms.sourcegitcommit: 1d4f6cc80ea343a667d16beec03220cfe1f43b8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/23/2020
ms.locfileid: "85289355"
---
# <a name="visual-studio-subscriptions-in-a-microsoft-products-and-services-agreement-mpsa"></a>Subskrypcje programu Visual Studio w ramach umowy dotyczącej produktów i usług firmy Microsoft (MPSA)
Jeśli masz zakupione subskrypcje programu Visual Studio w programie MPSA, musisz znać kilka kwestii, aby móc stać się administratorem subskrypcji programu Visual Studio i przypisać subskrypcje użytkownikom. Jeśli użytkownik został już skonfigurowany jako administrator, możesz przejść bezpośrednio do [portalu administracyjnego](https://manage.visualstudio.com/)subskrypcji programu Visual Studio.

MPSA klienci mogą teraz zarządzać zasobami zakupionymi za pomocą usługi MPSA w nowym portalu o nazwie [centrum biznesowego](https://businessaccount.microsoft.com/Customer), który obsługuje funkcje podobne do centrum usługi licencjonowania zbiorowego (VLSC). Obejmują one Wyświetlanie podsumowania licencji, zamówień, plików do pobrania, kluczy, użytkowników itp. Jednak subskrypcje programu Visual Studio w programie MPSA działają podobnie jak Cloud Services. W centrum biznesowym są również wykorzystywane konta służbowe, a nie konta Microsoft (MSA). Jeśli Twoja organizacja korzysta z usług w chmurze, takich jak Office 365 lub Azure Active Directory, a Twoja poczta e-mail należy do jednej z tych dwóch usług, to już konto służbowe. Pozwoli to na zarejestrowanie się w usłudze Business Center przy użyciu istniejącego hasła. Jeśli Twoja organizacja nie korzysta z usług w chmurze, a Twoja poczta e-mail nie jest kontem służbowym, możesz użyć jej do zarejestrowania się w centrum biznesowym.

Ponadto [Portal administracyjny](https://manage.visualstudio.com/) subskrypcji programu Visual Studio to miejsce, w którym subskrypcje zostaną przypisane do subskrybentów po przeprowadzeniu administratora subskrypcji programu Visual Studio. W programie MPSA subskrypcje programu Visual Studio muszą być obsługiwane w odpowiednim portalu zarządzania, który jest portalem administracyjnym subskrypcji programu Visual Studio. Aby to zrobić, należy skojarzyć konto zakupu z dzierżawcą (np. contoso.onmicrosoft.com).

Należy pamiętać, że istnieją dwa typy dzierżawców zarządzanych przez dzierżawców i niezarządzanych dzierżawców. Zarządzana dzierżawa odnosi się do dzierżawy, która jest już zarządzana przez administratorów w organizacji.

Niezarządzana dzierżawa jest dzierżawcą bez przypisanych administratorów i nie jest używana do usług online, takich jak Office 365. Niezarządzane dzierżawy są również tworzone podczas rejestrowania w centrum biznesowym za pomocą wiadomości e-mail, która nie jest kontem służbowym. Jeśli poprosisz o utworzenie hasła podczas rejestrowania w usłudze Business Center, oznacza to, że Twoja poczta e-mail nie jest kontem służbowym i utworzyła niezarządzaną dzierżawę.

Poniżej przedstawiono kilka wymagań/kroków, które trzeba wykonać, aby zostać administratorem subskrypcji programu Visual Studio przed ukończeniem skojarzenia dzierżawy.

## <a name="pre-tenant-association-managed-tenant"></a>Skojarzenie przed dzierżawcą (zarządzana dzierżawa)
- Musisz być zarejestrowanym użytkownikiem w usłudze Business Center.
- Musisz być administratorem użytkownika (co najmniej) lub administratorem globalnym w ramach dzierżawy, która jest częścią. (Dotyczy to sytuacji, w której firma już używa Cloud Services). Każda rola jest wymagana jako administrator subskrypcji programu Visual Studio.
- Musisz być administratorem globalnym w dzierżawie, do której należysz, aby skojarzyć konto zakupu z dzierżawcą.
- Musisz być administratorem konta lub menedżerem kont w programie Business Center.
- Pole "kraj lub region" w profilu użytkownika (oraz każdy inny użytkownik) na [platformie Azure](https://portal.azure.com/) musi być odpowiednio wypełniane w zależności od regionu (tj. USA, urzędu certyfikacji itp.). 

> [!NOTE]
> Wszyscy użytkownicy, którym chcesz nawiązać administratorów subskrypcji programu Visual Studio, nie muszą być użytkownikami w centrum biznesowym, ponieważ muszą spełniać tylko kryteria 2 i 5.

Po spełnieniu powyższych kryteriów można utworzyć skojarzenie konta zakupu z dzierżawcą, wykonując poniższe kroki.
1. Zaloguj się do programu [Business Center](https://businessaccount.microsoft.com/Customer).
2. Kliknij kartę **konto** i wybierz pozycję **Skojarz domeny**.
3. Wybierz **konto zakupu** (Jeśli masz więcej niż jeden).
4. Wybierz **dzierżawę** (np. contoso.onmicrosoft.com).
5. Kliknij pozycję **Skojarz domenę**.

Po skojarzeniu wszyscy użytkownicy spełniający kryteria będą zazwyczaj udostępniać Administratorzy subskrypcji programu Visual Studio w ciągu kilku minut. Jednak czasami może to potrwać do 24 godzin. Po zainicjowaniu obsługi dzierżawy będzie można uzyskać dostęp do portalu administracyjnego subskrypcji programu Visual Studio. Jeśli trwa to dłużej niż 24 godziny, skontaktuj się z pomocą techniczną usługi MPSA, wykonując następujące czynności:
1. Połącz z<https://www.microsoft.com/licensing/mpsa/default>
2. Kliknij menu **więcej** w górnej części strony. 
3. Wybierz **Pomoc techniczną**
4. Wybierz **Pomoc techniczną licencjonowania**
5. Wybierz opcję pomocy technicznej, która najlepiej odpowiada Twoim potrzebom. 

> [!NOTE]
> Jeśli istnieją nowi użytkownicy, którzy spełniają kryteria w krokach 2 i 5 (po skojarzeniu), musisz skontaktować się z pomocą techniczną MPSA. Pomoc techniczna MPSA zapewnia pomoc w zakresie udostępniania nowych administratorów subskrypcji programu Visual Studio.

## <a name="tenant-association-unmanaged"></a>Skojarzenie dzierżawy (niezarządzane)
Jeśli zarejestrowano Cię w centrum biznesowym za pomocą wiadomości e-mail, która nie jest kontem służbowym (nie jest zarejestrowana w Azure Active Directory "Azure AD"), jak wyjaśniono powyżej, skojarzenie dzierżawy będzie nieco inne. Należy wykonać czynności, które są nazywane "przejmowaniem domeny". W trakcie tego procesu użytkownik zostanie samemu administratorem globalnym, który zmieni dzierżawę z niezarządzanych na zarządzaną.

Aby uzyskać bardziej szczegółowy opis tego procesu, możesz użyć [przewodników szybki start](https://www.microsoft.com/Licensing/existing-customer/business-center-training-and-resources.aspx). Pobierz przewodnik o nazwie *"Instalacja i korzystanie z usług online"* , który przeprowadzi Cię przez procedurę przejęcia przez domenę. Po zakończeniu tego procesu konto zakupu zostanie również skojarzone z dzierżawcą.

> [!NOTE]
> Po przeprowadzeniu procesu przejęcia domeny należy przestrzegać kryteriów z pięciu kroków w sekcji w przypadku skojarzenia predzierżawców (zarządzane). Po spełnieniu kryteriów będzie konieczne skontaktowanie się z pomocą techniczną MPSA w celu udostępnienia dodatkowych administratorów subskrypcji programu Visual Studio.

## <a name="see-also"></a>Zobacz też
- [Dokumentacja programu Visual Studio](https://docs.microsoft.com/visualstudio/)
- [Dokumentacja usługi Azure DevOps](https://docs.microsoft.com/azure/devops/)
- [Dokumentacja platformy Azure](https://docs.microsoft.com/azure/)
- [Dokumentacja Microsoft 365](https://docs.microsoft.com/microsoft-365/)

## <a name="next-steps"></a>Następne kroki
Dowiedz się więcej o zarządzaniu subskrypcjami programu Visual Studio.
- [Przypisywanie pojedynczych subskrypcji](assign-license.md)
- [Przypisywanie wielu subskrypcji](assign-license-bulk.md)
- [Edytowanie subskrypcji](edit-license.md)
- [Usuwanie subskrypcji](delete-license.md)
- [Określanie maksymalnego użycia](maximum-usage.md)
