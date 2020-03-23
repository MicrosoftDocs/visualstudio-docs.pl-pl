---
title: Obsługa licencji z nadmierną alokacją | Dokumenty firmy Microsoft
author: evanwindom
ms.author: lank
manager: lank
ms.date: 03/03/2020
ms.topic: conceptual
description: Dowiedz się, jak administratorzy mogą rozwiązywać nadmierne subskrypcje z nadmierną alokacją
ms.openlocfilehash: 6773196d914306b7e18fe31ce06cc0cd89783ffd
ms.sourcegitcommit: f8e3715c64255b476520bfa9267ceaf766bde3b0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/21/2020
ms.locfileid: "78410277"
---
# <a name="overallocated-subscriptions"></a>Subskrypcje z nadmierną alokacją
Czasami zamówienia są zmieniane po dodaniu subskrybentów, co może spowodować, że będą mieć więcej przypisanych subskrypcji niż licencje należące do firmy. To się nazywa "nadmierna alokacja".  

Aby wyświetlić alokacje dolnego, kliknij górną ikonę po lewej stronie, aby otworzyć okienko alokacji.  

> [!NOTE]
> Nadmierne alokacje nie są dozwolone w programach Otwartej licencji.  Ponadto inne programy mogą wyświetlać te informacje w portalu w inny sposób.
>
> [!div class="mx-imgBorder"]
> ![Zawiadomienie o nadmiernych wnioskach o subskrypcji](_img/over-claimed/over-claimed-alert.png)

Należy zauważyć, że wyświetlacz używa paska skrótu do wskazania nadmiernej alokacji subskrypcji.  Liczba nadmiernych alokacji we wszystkich typach subskrypcji znajduje się w sekcji Przegląd u góry, a każdy poziom subskrypcji wyświetla również własny stan alokacji.  

## <a name="resolve-overallocated-subscriptions"></a>Rozwiązywanie problemu z nadmierną alokacją subskrypcji
Istnieje kilka sposobów rozwiązywania nadmiernych alokacji:
- Skontaktuj się ze sprzedawcą, aby zakupić dodatkowe subskrypcje.
- Poczekaj na roczny okres true-up i zapłacić za subskrypcje z nadmierną alokacją w tym momencie. 
- Usuń niektóre przypisania subskrypcji.  (Nie zapobiegnie to konieczności płatności w rocznym true-up, ponieważ true-up opiera się na maksymalnej liczbie subskrypcji przypisanych w dowolnym momencie w ciągu roku.)

## <a name="billing-and-true-up"></a>Rozliczenia i prawda
Jeśli twoja organizacja ma umowę Enterprise Agreement (EA), administratorzy mogą przypisywać subskrypcje bez ich zakupu i płacić za nie później za pośrednictwem procesu uzgadniania znanego jako "true-up".  Podczas nadmiernej alokacji organizacja będzie rozliczana z maksymalnej liczby subskrypcji przypisanych do użytkowników podczas "true-up".  Jest to prawdą, nawet jeśli nie masz już maksymalną liczbę subskrypcji przypisanych w momencie true-up ma miejsce.  Aby dowiedzieć się więcej na temat monitorowania maksymalnego użycia, zapoznaj się z tematem [Maksymalne użycie.](maximum-usage.md)

> [!Important]
> Jeśli subskrypcje programu Visual Studio z programem GitHub Enterprise są przypisywane przez administratorów subskrypcji programu Visual Studio i nigdy nie było zakupu tych subskrypcji, nie będą one widoczne dla administratorów usługi GitHub Enterprise w organizacji. Aby upewnić się, że subskrypcje GitHub Enterprise są widoczne, zakup obejmujący **co najmniej jeden** program Visual Studio Professional z pakietem GitHub Enterprise lub Visual Studio Enterprise z subskrypcją GitHub Enterprise powinien zostać dokonany przy pierwszym przypisaniu subskrypcji.
>
> Obowiązkiem klienta jest upewnienie się, że dla każdej przypisanej subskrypcji usługi GitHub istnieje odpowiedni program Visual Studio z subskrypcją Usługi GitHub przypisany w portalu Zarządzaj, aby zachować zgodność z wymaganiami licencyjnymi dotyczącymi tego Subskrypcji.

## <a name="see-also"></a>Zobacz też
- [Dokumentacja programu Visual Studio](https://docs.microsoft.com/visualstudio/)
- [Dokumentacja usługi Azure DevOps](https://docs.microsoft.com/azure/devops/)
- [Dokumentacja platformy Azure](https://docs.microsoft.com/azure/)
- [Dokumentacja usługi Microsoft 365](https://docs.microsoft.com/microsoft-365/)

## <a name="next-steps"></a>Następne kroki
- Dowiedz się więcej o zarządzaniu [subskrypcjami programu Visual Studio za pomocą usługi GitHub Enterprise](assign-github.md).
- Aby uzyskać pomoc dotyczącą sprzedaży, subskrypcji, kont i rozliczeń za subskrypcje programu Visual Studio, skontaktuj się z [pomocą techniczną dotyczącą subskrypcji](https://visualstudio.microsoft.com/subscriptions/support/)programu Visual Studio.