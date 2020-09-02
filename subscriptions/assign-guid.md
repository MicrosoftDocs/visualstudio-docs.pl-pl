---
title: Przypisywanie określonych identyfikatorów GUID do subskrybentów programu Visual Studio | Microsoft Docs
author: evanwindom
ms.author: lank
manager: lank
ms.date: 04/20/2020
ms.topic: conceptual
description: Dowiedz się, jak Administratorzy mogą uzyskać określony identyfikator GUID subskrypcji dla subskrybentów
ms.openlocfilehash: e6c50239721d810964f2b95e0ec3509999d2f4d5
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "87235189"
---
# <a name="assign-specific-subscriptions-in-the-visual-studio-subscriptions-administration-portal"></a>Przypisywanie określonych subskrypcji w portalu administratora subskrypcji programu Visual Studio

Administratorzy mogą teraz używać portalu administracyjnego subskrypcji programu Visual Studio do przypisywania określonych subskrypcji do poszczególnych subskrybentów.  Może to być przydatne w sytuacjach, w których organizacja ma tymczasowego pracownika lub dostawców, którzy potrzebują dostępu do subskrypcji przez krótki okres.  Administratorzy mogą przypisywać subskrypcję, która została już częściowo użyta, pozostawiając ich nowe subskrypcje do dłuższego użycia.  

<br>

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4t4cl]


## <a name="assign-specific-subscription-guids-to-users"></a>Przypisywanie określonych identyfikatorów GUID subskrypcji do użytkowników

Proces przypisywania określonych subskrypcji do poszczególnych użytkowników polega na użyciu dwóch istniejących procesów administracyjnych w celu przypisania unikatowych identyfikatorów globalnych (GUID) w ramach subskrypcji indywidualnym użytkownikom.  Proces trójstanowy obejmuje wyeksportowanie listy bieżących subskrypcji i przypisań przy użyciu tej listy w celu zidentyfikowania określonych identyfikatorów GUID, które chcesz przypisać, a następnie użycie zbiorczego procesu dodawania do przekazywania nowych przypisań.

### <a name="export-your-subscriptions-information"></a>Eksportowanie informacji o subskrypcjach

Aby przeprowadzić eksport:
1. Zaloguj się do [portalu administracyjnego](https://manage.visualstudio.com).
2. Wybierz kartę **Eksportuj** . plik zostanie pobrany na komputer lokalny. Plik będzie zawierać nazwę umowy zawierającej subskrypcje użytkowników, a także datę eksportu.
> [!div class="mx-imgBorder"]
> ![Eksportowanie subskrybentów](_img/exporting-subscriptions/exporting-subscriptions.png "Kliknij przycisk Eksportuj, aby zapisać listę przypisanych subskrypcji z informacjami o subskrybencie.")

### <a name="identify-the-guids-you-want-to-assign"></a>Zidentyfikuj identyfikatory GUID, które chcesz przypisać

Jeśli wcześniej używasz narzędzia eksportu, Zauważ, że nowe pola zostały dodane do arkusza kalkulacyjnego, który został utworzony.  Pomoże to określić stan każdej subskrypcji, a które mają być przypisane do użytkowników.  

- **Stan subskrypcji**: w tym polu będzie wskazywana wartość "przypisany" lub "nieprzypisane".  Jeśli subskrypcja ma stan "przypisany", będzie również zawierać skojarzone z nią informacje o użytkowniku, takie jak nazwa, adres e-mail itd. 
- **Stan użycia**: stan użycia będzie wskazywać na "nowe", co oznacza, że nigdy nie został przypisany do użytkownika lub "używany", co oznacza, że został przypisany do użytkownika w pewnym momencie.  

Możesz użyć wartości w tych polach wraz z innymi informacjami w arkuszu kalkulacyjnym, aby określić, które subskrypcje mają być przypisane do poszczególnych użytkowników. Możesz zastosować filtr w programie Excel, aby ograniczyć listę według stanu, poziomu subskrypcji, daty wygaśnięcia itd. 

### <a name="upload-your-new-assignments"></a>Przekaż nowe przypisania

Ostatnim krokiem jest pobranie **zbiorczego szablonu Dodaj** , wypełnienie wymaganych informacji dotyczących subskrypcji, które chcesz przypisać, i przekazanie szablonu.  Aby uzyskać pełny opis tego procesu, zobacz nasz artykuł [Dodawanie wielu użytkowników](assign-license-bulk.md) .  

> [!IMPORTANT]
> Aby zapewnić pomyślne przekazywanie, upewnij się, że:
> - W przypadku wybrania opcji **Dodaj zbiorczo**używasz szablonu połączonego w oknie dialogowym.  Nie należy używać lokalnie przechowywanej kopii szablonu, ponieważ może nie zawierać wszystkich wymaganych pól.  Użycie starego szablonu spowoduje niepowodzenie przekazywania. 
> - Wszystkie pola wyświetlane jako **wymagane** w szablonie są kompletne.
> - Brak błędów wymienionych w kolumnie **komunikat o błędzie** .
> - Każdy identyfikator GUID jest używany tylko raz w szablonie. 
> - Poziom subskrypcji w szablonie jest zgodny z subskrypcją identyfikatora GUID na wyeksportowanej liście. 
> - Identyfikator GUID nie jest już przypisany do innego użytkownika na wyeksportowanej liście. 

## <a name="frequently-asked-questions"></a>Często zadawane pytania
### <a name="qhow-do-i-change-which-subscription-is-currently-assigned-to-an-individual-user"></a>Q:How zmienić, która subskrypcja jest obecnie przypisana do pojedynczego użytkownika?
Odp.: Jeśli chcesz zmienić identyfikator GUID przypisany do użytkownika, musisz najpierw usunąć subskrypcję dla tego użytkownika.  Aby uzyskać więcej informacji, zobacz artykuł [usuwanie subskrypcji](delete-license.md) , aby uzyskać więcej informacji.  Po usunięciu subskrypcji dla tego użytkownika należy użyć podanego powyżej procesu, aby wyeksportować listę i przekazać nowe informacje o subskrypcji.  

## <a name="see-also"></a>Zobacz też
- [Dokumentacja programu Visual Studio](/visualstudio/)
- [Dokumentacja usługi Azure DevOps](/azure/devops/)
- [Dokumentacja platformy Azure](/azure/)
- [Dokumentacja Microsoft 365](/microsoft-365/)

## <a name="next-steps"></a>Następne kroki
Teraz, gdy masz przypisane subskrypcje użytkownikom, Dowiedz się, jak wykonywać inne zadania administracyjne.
- [Przypisywanie pojedynczych subskrypcji](assign-license.md)
- [Przypisywanie wielu subskrypcji](assign-license-bulk.md)
- [Edytowanie subskrypcji](edit-license.md)
- [Usuwanie subskrypcji](delete-license.md)
- [Określanie maksymalnego użycia](maximum-usage.md)


