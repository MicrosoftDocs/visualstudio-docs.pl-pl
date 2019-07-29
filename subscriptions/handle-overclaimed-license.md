---
title: Obsługa niealokowanych licencji | Microsoft Docs
author: evanwindom
ms.author: lank
manager: lank
ms.date: 07/24/2019
ms.topic: conceptual
description: Dowiedz się, jak Administratorzy mogą rozwiązywać nadmiarowe subskrypcje
ms.openlocfilehash: 924f6fb2c513d70aefd28c1d4ff18d1af62178c2
ms.sourcegitcommit: ce1ab8a25c66a83e60eab80ed8e1596fe66dd85c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/29/2019
ms.locfileid: "68605508"
---
# <a name="overallocated-subscriptions"></a>Naddzielono subskrypcje
Czasami zamówienia są zmieniane po dodaniu subskrybentów, co może spowodować, że masz więcej przypisanych subskrypcji niż licencje należące do firmy. Jest to tzw. "nadmierna alokacja".  W takim przypadku na karcie Subskrybenci zostanie wyświetlony alert z informacją o liczbie subskrypcji, które zostały zastąpione.

> [!NOTE]
> Nadmierne alokacje nie są dozwolone w programach licencjonowania Open.  Ponadto inne programy mogą wyświetlać te informacje w portalu inaczej.
>
> [!div class="mx-imgBorder"]
> ![Powiadomienie o nadmiernie przejętych subskrypcjach](_img/over-claimed/over-claimed-alert.png)

## <a name="resolve-overallocated-subscriptions"></a>Rozwiązywanie nadalokowanych subskrypcji
Istnieje kilka sposobów rozwiązywania nadmiernych alokacji:
- Skontaktuj się z odsprzedawcą, aby zakupić dodatkowe subskrypcje.
- Poczekaj, aż upłynie roczny okres działania i płatność za nadmiarowe subskrypcje w tym momencie. 
- Usuń niektóre przypisania subskrypcji.  (Nie uniemożliwi to potrzeby płatności w rocznym wykorzystaniu subskrypcji, co ma na celu wyróżnienie w tym przypadku maksymalnej liczby przypisanych subskrypcje w dowolnym momencie w roku).

## <a name="billing-and-true-up"></a>Rozliczenia i prawdziwe
Jeśli Twoja organizacja ma Umowa Enterprise (EA), Administratorzy mogą przypisywać subskrypcje bez ich zakupu i uregulować je później za pomocą procesu uzgadniania znanego jako "true-up".  Po przeniesieniu do przydziału organizacja będzie rozliczana za maksymalną liczbę subskrypcji przypisanych do użytkowników podczas "prawdziwej konfiguracji".  Ta wartość jest prawdziwa, nawet jeśli nie masz już maksymalnej liczby subskrypcji przypisanych w czasie rzeczywistym.  Aby dowiedzieć się więcej o monitorowaniu maksymalnego użycia, przejdź do tematu [maksymalne użycie](maximum-usage.md) .

> [!Important]
> Jeśli subskrypcje programu Visual Studio z usługą GitHub Enterprise są przypisane przez administratorów subskrypcji programu Visual Studio, a nigdy nie zakupionych subskrypcji, nie będą one widoczne dla administratorów przedsiębiorstwa usługi GitHub w organizacji. Aby mieć pewność, że subskrypcje w witrynie GitHub Enterprise są widoczne, należy dokonać zakupu, w tym **co najmniej jednego** Visual Studio Professional z usługą GitHub enterprise lub Visual Studio Enterprise z subskrypcją usługi GitHub Enterprise, przy pierwszej subskrypcji są przypisane.
>
> Klient jest odpowiedzialny za zagwarantowanie, że dla każdej przypisanej subskrypcji usługi GitHub istnieje odpowiedni program Visual Studio z subskrypcją usługi GitHub przypisany w portalu zarządzania w celu zachowania zgodności z wymaganiami dotyczącymi licencjonowania dla tego ramach.

## <a name="next-steps"></a>Następne kroki
- Dowiedz się więcej o zarządzaniu [subskrypcjami programu Visual Studio za pomocą usługi GitHub Enterprise](assign-github.md).
- Aby uzyskać pomoc dotyczącą sprzedaży, subskrypcji, kont i rozliczeń dla subskrypcji programu Visual Studio, skontaktuj się z [pomocą techniczną subskrypcji](https://visualstudio.microsoft.com/subscriptions/support/)programu Visual Studio.
