---
title: Obsługa niealokowanych licencji | Microsoft Docs
author: evanwindom
ms.author: lank
manager: lank
ms.date: 03/03/2020
ms.topic: conceptual
description: Dowiedz się, jak Administratorzy mogą rozwiązywać nadmiarowe subskrypcje
ms.openlocfilehash: 6773196d914306b7e18fe31ce06cc0cd89783ffd
ms.sourcegitcommit: 3154387056160bf4c36ac8717a7fdc0cd9faf3f9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2020
ms.locfileid: "78410277"
---
# <a name="overallocated-subscriptions"></a>Naddzielono subskrypcje
Czasami zamówienia są zmieniane po dodaniu subskrybentów, co może spowodować, że masz więcej przypisanych subskrypcji niż licencje należące do firmy. Jest to tzw. "nadmierna alokacja".  

Aby wyświetlić alokacje wyższą, kliknij górną ikonę po lewej stronie, aby otworzyć okienko alokacje.  

> [!NOTE]
> Nadmierne alokacje nie są dozwolone w programach licencjonowania Open.  Ponadto inne programy mogą wyświetlać te informacje w portalu inaczej.
>
> [!div class="mx-imgBorder"]
> ![powiadomienia o nadmiernie przejętych subskrypcjach](_img/over-claimed/over-claimed-alert.png)

Zauważ, że na ekranie jest używany skrót słupkowy, który wskazuje subskrypcje z nadmiarową alokacją.  Liczba nadmiernych alokacji we wszystkich typach subskrypcji znajduje się w sekcji Przegląd u góry, a na każdym poziomie subskrypcji jest również wyświetlany własny stan alokacji.  

## <a name="resolve-overallocated-subscriptions"></a>Rozwiązywanie nadalokowanych subskrypcji
Istnieje kilka sposobów rozwiązywania nadmiernych alokacji:
- Skontaktuj się z odsprzedawcą, aby zakupić dodatkowe subskrypcje.
- Poczekaj, aż upłynie roczny okres działania i płatność za nadmiarowe subskrypcje w tym momencie. 
- Usuń niektóre przypisania subskrypcji.  (Nie uniemożliwi to potrzeby płatności w rocznym wykorzystaniu subskrypcji, co ma na celu wyróżnienie w tym przypadku maksymalnej liczby przypisanych subskrypcje w dowolnym momencie w roku).

## <a name="billing-and-true-up"></a>Rozliczenia i prawdziwe
Jeśli Twoja organizacja ma Umowa Enterprise (EA), Administratorzy mogą przypisywać subskrypcje bez ich zakupu i uregulować je później za pomocą procesu uzgadniania znanego jako "true-up".  Po przeniesieniu do przydziału organizacja będzie rozliczana za maksymalną liczbę subskrypcji przypisanych do użytkowników podczas "prawdziwej konfiguracji".  Ta wartość jest prawdziwa, nawet jeśli nie masz już maksymalnej liczby subskrypcji przypisanych w czasie rzeczywistym.  Aby dowiedzieć się więcej o monitorowaniu maksymalnego użycia, przejdź do tematu [maksymalne użycie](maximum-usage.md) .

> [!Important]
> Jeśli subskrypcje programu Visual Studio z usługą GitHub Enterprise są przypisane przez administratorów subskrypcji programu Visual Studio, a nigdy nie zakupionych subskrypcji, nie będą one widoczne dla administratorów przedsiębiorstwa usługi GitHub w organizacji. Aby upewnić się, że subskrypcje w witrynie GitHub są widoczne, należy dokonać zakupu, w tym **co najmniej jeden** Visual Studio Professional z usługą GitHub enterprise lub Visual Studio Enterprise z subskrypcją usługi GitHub Enterprise, przy pierwszym przypisaniu subskrypcji.
>
> Klient jest odpowiedzialny za zagwarantowanie, że dla każdej przypisanej subskrypcji usługi GitHub istnieje odpowiedni program Visual Studio z subskrypcją usługi GitHub przypisany w portalu zarządzania w celu zachowania zgodności z wymaganiami dotyczącymi licencjonowania dla tego ramach.

## <a name="see-also"></a>Zobacz też
- [Dokumentacja programu Visual Studio](https://docs.microsoft.com/visualstudio/)
- [Dokumentacja usługi Azure DevOps](https://docs.microsoft.com/azure/devops/)
- [Dokumentacja platformy Azure](https://docs.microsoft.com/azure/)
- [Dokumentacja Microsoft 365](https://docs.microsoft.com/microsoft-365/)

## <a name="next-steps"></a>Następne kroki
- Dowiedz się więcej o zarządzaniu [subskrypcjami programu Visual Studio za pomocą usługi GitHub Enterprise](assign-github.md).
- Aby uzyskać pomoc dotyczącą sprzedaży, subskrypcji, kont i rozliczeń dla subskrypcji programu Visual Studio, skontaktuj się z [pomocą techniczną subskrypcji](https://visualstudio.microsoft.com/subscriptions/support/)programu Visual Studio.