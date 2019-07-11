---
title: Korzystanie z portalu administratora | Portal Marketplace programu Visual Studio
author: evanwindom
ms.author: jaunger
manager: evelynp
ms.date: 10/03/2017
ms.topic: conceptual
description: Dowiedz się, jak zarządzać subskrypcjami programu Visual Studio w organizacji za pomocą portalu administratora.
ms.openlocfilehash: 6da1f0ce52e810a7652dd306ff5a6e44404b76f7
ms.sourcegitcommit: 208395bc122f8d3dae3f5e5960c42981cc368310
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67784792"
---
# <a name="using-the-visual-studio-subscriptions-administrator-portal"></a>Korzystanie z portalu administratora subskrypcji programu Visual Studio

Miej to na uwadze, korzystając z portalu administratora subskrypcji Visual Studio:

- **Subskrypcje programu Visual Studio są licencjonowane na poszczególnych użytkowników.** Każdy subskrybent może korzystać z oprogramowania na komputerach w razie potrzeby tworzenia i testowania.
- **Przypisanie poziomu tylko jedną subskrypcję dla każdego subskrybenta**, odpowiadające subskrypcji programu Visual Studio zakupione w Twojej organizacji. W przypadku subskrybentów z więcej niż jeden poziom subskrypcji przypisane, Edytuj ich ustawienia, aby udzielić użytkownikom tylko jedną.
- **Poziom subskrypcji subskrybenta będą musiały zostać zaktualizowane** po uaktualnieniu (po zakupie licencji "podniesienie") lub odnowienia na niższym poziomie subskrypcji.
- **Nie należy udostępniać subskrypcji od subskrybentów.** Dla każdego, kto używa całość lub część korzyści z subskrypcji (oprogramowanie do tworzenia i testowania Microsoft Azure e-learning, itp.), należy przypisać subskrypcję.

## <a name="administrator-roles"></a>Role administratorów

Istnieją dwie różne role, które istnieją w portalu nowego administratora subskrypcji programu Visual Studio dla klientów licencjonowania zbiorowego. Te role są podobne do roli podstawowej/kontaktowej i rolę Menedżer subskrypcji w witrynie VLSC już dziś.

**Superadministratorzy:** Po skonfigurowaniu organizacji, główna osoba kontaktowa lub kontaktowa staje się super admin domyślnie. Skontaktuj się z podstawowej maszyny wirtualnej lub uwagi można przypisać dodatkowe superadministratorów lub administratorów. Super admin dodawać i usuwać innych administratorów, a także subskrybentów. Jeśli istnieje więcej niż dwóch superadministratorzy w systemie, superadministrator umożliwia usunięcie wszystkich ostatnie dwa zabezpieczeń.

**Administratorzy:** Administrator może można skonfigurować tylko przez administratora administratora. Administrator może zarządzać subskrybentów w ramach umów, na które super admin przypisuje do nich.

## <a name="getting-started"></a>Wprowadzenie

Aby korzystać z portalu administratora do zarządzania subskrypcjami dla Twojej organizacji, należy najpierw dodać organizacji do portalu.  Po zakończeniu dołączania, warto zapoznać się ze strony subskrybentów i szczegółowe informacje, jak są, gdzie znajdziesz, narzędzia i informacje potrzebne do wykonania zadania związane z zarządzaniem subskrypcją.

### <a name="onboarding"></a>Dołączanie do

Jeśli Twoja organizacja jest gotowy do dodania do portalu administratora subskrypcji Visual Studio zostanie wysłana wiadomość e-mail główna osoba kontaktowa i kontaktowa zaproszeniem do ukończenia procesu dołączania. Poniższe szczegóły przedstawiono kroki, które należy podjąć dołączyć do nowego portalu. Jeśli chcesz wskazówki procesu, zapoznaj się z tą [dołączania administratora wideo](https://channel9.msdn.com/Series/Visual-Studio-Subscriptions-Administration/Onboarding-your-organization-to-the-new-Visual-Studio-Subscription-Administration-Portal-and-setting) bądź [artykuł pomocy technicznej](https://support.microsoft.com/help/4013931/visual-studio-subscriptions-administrator-migration-process "procesu migracji administratora subskrypcje Studio Visual").

1. **Przy szukaniu numeru PCN i zaloguj się:**
    - W wiadomości e-mail podstawowej i osoba kontaktowa są dostarczane za pomocą unikatowego linku i trzy ostatnie cyfry dla swojego publicznego numeru klienta (PCN). * 
    - Aby uzyskać cały numer PCN, musisz zalogować się do centrum VLSC głównej osoby kontaktowej (można znaleźć instrukcje dotyczące lokalizacji numer PCN). 
    - Po uzyskaniu numer PCN, ich należy wybrać ich unikatowego linku, co spowoduje wyświetlenie monitu do logowania. Będą mogli logować się przy użyciu konta Microsoft (MSA) lub konto służbowe (jeśli Twojej organizacji w usłudze AAD), jeśli Twoja organizacja nie znajduje się w usłudze AAD. 
    - Następnie należy wprowadź numer PCN. 
2. **Konfigurowanie administratorów usługi.** Po wprowadzeniu numerów PCN, zostaną zarejestrowane jako superadministrator w nowym systemie i będzie można dodać inne superadministratorzy i Administratorzy (wcześniej znanej jako menedżerowie subskrypcji). Aby uniknąć utraty dostępu, to należy wykonać przed datą migracji Twojej organizacji. 
3. **Uzyskiwanie dostępu do nowego portalu zarządzania subskrypcjami.**  Po zmigrowaniu organizacji wiadomości e-mail będą wysyłane do nowo dodanego superadministratorzy i Administratorzy zapraszając ich dostęp do nowego portalu i zarządzania subskrypcjami.  

> [!NOTE]
> Jeśli główna osoba kontaktowa lub kontaktowa odbierze więcej niż jeden adres e-mail, oznacza to, że mają więcej niż jeden numer PCN. Muszą się ukończyć proces, korzystając z unikatowego linku dla numeru PCN, do którego odwołuje się każdego email.*

Jeśli potrzebujesz mają zostać dodane do nowego portalu programu Visual Studio subskrypcje administracji i nie masz pewności, będącego kontakt podstawowy/uwagi, można znaleźć te informacje po zarejestrowaniu się [VLSC](https://www.microsoft.com/Licensing/servicecenter/default.aspx). Przyjrzyj się [znaleźć Twojej głównej osoby kontaktowej](find-primary-contact.md) temacie kroki, aby znaleźć podstawowy/uwagi dotyczące przejrzenia przez osobę kontaktową w witrynie VLSC.
Jeśli możesz już skonfigurowano jako administrator, a następnie możesz też przejść bezpośrednio do [Portal administratora subskrypcji programu Visual Studio](https://manage.visualstudio.com).

### <a name="understanding-the-subscribers-page"></a>Informacje o stronie subskrybentów
Po przypisaniu subskrypcji, na karcie subskrybentów zawiera szczegółowe informacje na temat subskrybentów, w tym:
- Imię i nazwisko każdego subskrybenta.
- Adres e-mail dla tego użytkownika.
- Poziom subskrypcji, która ma przypisane do nich.
- Data ich subskrypcja została przypisana do nich.
- Data wygaśnięcia dla swojej subskrypcji.
- Opcjonalny opis.
- Wskazanie, czy pliki do pobrania dla subskrybentów został włączony lub wyłączony.
- Kraj, w którym się znajdują.
- Swoje preferencje językowe dla wiadomość e-mail dotycząca przypisania komunikacji z portalu administratora.
- Pole opcjonalne dla inny adres e-mail używany do komunikacji logowania.

Na lewym rogu tej strony znajdują się dodatkowe informacje o liczbie licencji subskrypcji zakupionych przypisane i nadal dostępne w Twojej organizacji, dla każdej umowy.
> [!div class="mx-imgBorder"]
> ![Strona subskrybentów portalu administratora subskrypcji programu Visual Studio](_img/using-admin-portal/subscribers-page.png)

### <a name="understanding-the-details-page"></a>Informacje o stronie szczegółów
Aby uzyskać więcej informacji o umowie, że jest wyświetlana wybierz kartę szczegółów. Wskazuje ono na stan umowy, Zakup konto, szczegóły organizacji, głównymi osobami kontaktowymi (firmy Microsoft VLSC), superadministratorzy (jeśli jest dostępny) i inne istotne informacje.
> [!div class="mx-imgBorder"]
> ![Strona szczegółów w portalu administratora subskrypcji programu Visual Studio](_img/using-admin-portal/details-page.png)
