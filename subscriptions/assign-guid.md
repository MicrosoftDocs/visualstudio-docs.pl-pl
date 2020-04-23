---
title: Przypisywanie określonych identyfikatorów GUID do subskrybentów programu Visual Studio | Dokumenty firmy Microsoft
author: evanwindom
ms.author: lank
manager: lank
ms.date: 04/20/2020
ms.topic: conceptual
description: Dowiedz się, jak administratorzy mogą określać identyfikator GUID subskrypcji subskrybentom
ms.openlocfilehash: e2e8cd4f5d07f218fc23c0b7b6f28ababc25263f
ms.sourcegitcommit: 0b8497b720eb06bed8ce2194731177161b65eb84
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2020
ms.locfileid: "82072596"
---
# <a name="assign-specific-subscriptions-in-the-visual-studio-subscriptions-administration-portal"></a>Przypisywanie określonych subskrypcji w portalu administracyjnym subskrypcji programu Visual Studio

Administratorzy mogą teraz używać portalu administracyjnego subskrypcji programu Visual Studio do przypisywania określonych subskrypcji poszczególnym subskrybentom.  Może to być przydatne w sytuacjach, gdy organizacja ma pracowników tymczasowych lub dostawców, którzy potrzebują dostępu do subskrypcji na krótki okres.  Administratorzy mogą przypisać subskrypcję, która została już częściowo wykorzystana, pozostawiając nowe subskrypcje do dłuższego użytku.  

<br>

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4t4cl]


## <a name="assign-specific-subscription-guids-to-users"></a>Przypisywanie określonych identyfikatorów GUID subskrypcji do użytkowników

Proces przypisywania określonych subskrypcji do osób fizycznych polega na wykorzystaniu dwóch istniejących procesów administracyjnych w celu przypisania określonych unikatowych identyfikatorów (GUID) globalnej subskrypcji do poszczególnych użytkowników.  Trzyetapowy proces obejmuje eksportowanie listy bieżących subskrypcji i przypisań, używanie tej listy do identyfikowania określonych identyfikatorów GUID, które chcesz przypisać, a następnie używanie zbiorczego procesu dodawania do przekazywania nowych przypisań.

### <a name="export-your-subscriptions-information"></a>Eksportowanie informacji o subskrypcjach

Aby przeprowadzić eksport:
1. Zaloguj się do [portalu administracyjnego](https://manage.visualstudio.com).
2. Wybierz kartę **Eksportuj,** a plik zostanie pobrany na komputer lokalny. Plik będzie zawierał nazwę umowy zawierającą subskrypcje użytkowników, a także datę eksportu.
> [!div class="mx-imgBorder"]
> ![Eksportowanie subskrybentów](_img/exporting-subscriptions/exporting-subscriptions.png)

### <a name="identify-the-guids-you-want-to-assign"></a>Identyfikowanie identyfikatorów GUID, które chcesz przypisać

Jeśli narzędzie Eksportuj było wcześniej używane, zauważysz, że do tworzonego arkusza kalkulacyjnego dodano nowe pola.  Pomogą one określić stan każdej subskrypcji i te, które chcesz przypisać do użytkowników.  

- **Stan subskrypcji:** To pole wskazuje "przypisany" lub "nieprzypisany".  Jeśli subskrypcja ma stan "przypisany", będzie również mieć informacje o użytkowniku z nią związane, takie jak nazwa, adres e-mail itp. 
- **Stan użycia:** Stan użycia wskazuje "nowy", co oznacza, że nigdy nie został przypisany do użytkownika lub "używany", co oznacza, że został przypisany do użytkownika w pewnym momencie.  

Wartości w tych polach wraz z innymi informacjami w arkuszu kalkulacyjnym można użyć do określenia subskrypcji, które mają zostać przypisane poszczególnym użytkownikom. Możesz zastosować filtr w programie Excel, aby zawęzić listę według stanu, poziomu subskrypcji, daty wygaśnięcia itp. 

### <a name="upload-your-new-assignments"></a>Przesyłanie nowych zadań

Ostatnim krokiem jest pobranie szablonu **zbiorczego dodawania,** wypełnienie wymaganych informacji dla subskrypcji, które chcesz przypisać, i przekazanie szablonu.  Pełny opis tego procesu można znaleźć w artykule [Dodaj wielu użytkowników.](assign-license-bulk.md)  

> [!IMPORTANT]
> Aby zapewnić pomyślne przesłanie, upewnij się, że:
> - Używasz szablonu połączonego w oknie dialogowym po **wybraniu opcji Dodaj zbiorczo**.  Nie należy używać lokalnie przechowywanej kopii szablonu, ponieważ może ona nie zawierać wszystkich wymaganych pól.  Użycie starego szablonu spowoduje niepowodzenie przekazywania. 
> - Wszystkie pola wyświetlane jako **wymagane** w szablonie są kompletne.
> - W kolumnie **Komunikat o błędzie** nie ma żadnych błędów.
> - Każdy identyfikator GUID jest używany tylko raz w szablonie. 
> - Poziom subskrypcji w szablonie odpowiada subskrypcji identyfikatora GUID na liście eksportowanych. 
> - Identyfikator GUID nie jest jeszcze przypisany do innego użytkownika na wyeksportowanym liście. 

## <a name="frequently-asked-questions"></a>Często zadawane pytania
### <a name="qhow-do-i-change-which-subscription-is-currently-assigned-to-an-individual-user"></a>P: Jak zmienić subskrypcję, która jest obecnie przypisana do indywidualnego użytkownika?
Odp.: Jeśli chcesz zmienić identyfikator GUID przypisany do użytkownika, należy najpierw usunąć subskrypcję dla tego użytkownika.  Aby uzyskać więcej informacji, zobacz nasz artykuł [Usuń subskrypcje,](delete-license.md) aby uzyskać więcej informacji.  Po usunięciu subskrypcji dla tego użytkownika użyj procesu opisanego powyżej, aby wyeksportować listę i przekazać nowe informacje o subskrypcji.  

## <a name="see-also"></a>Zobacz też
- [Dokumentacja programu Visual Studio](/visualstudio/)
- [Dokumentacja usługi Azure DevOps](/azure/devops/)
- [Dokumentacja platformy Azure](/azure/)
- [Dokumentacja usługi Microsoft 365](/microsoft-365/)

## <a name="next-steps"></a>Następne kroki
Teraz, gdy przypisano subskrypcje do użytkowników, dowiedz się, jak wykonywać inne zadania administracyjne.
- [Przypisywanie poszczególnych subskrypcji](assign-license.md)
- [Przypisywanie wielu subskrypcji](assign-license-bulk.md)
- [Edytowanie subskrypcji](edit-license.md)
- [Usuwanie subskrypcji](delete-license.md)
- [Określanie maksymalnego użycia](maximum-usage.md)


