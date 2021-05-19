---
title: Obsługa zbyt przydzielonych licencji w Visual Studio subskrypcji | Microsoft Docs
author: evanwindom
ms.author: v-evwin
manager: cabuschl
ms.assetid: a747100c-6f08-41a4-aaad-05099741742b
ms.date: 05/18/2021
ms.topic: conceptual
description: Dowiedz się, jak administratorzy mogą rozwiązywać problemy z zbyt przydzielonymi subskrypcjami
ms.openlocfilehash: 533ce71e8795e89bcb21fd437da6bea91db291f4
ms.sourcegitcommit: 162be102d2c22a1c4ad2c447685abd28e0e85d15
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/19/2021
ms.locfileid: "109973396"
---
# <a name="over-allocated-subscriptions"></a>Zbyt przydzielone subskrypcje
Czasami zamówienia są zmieniane po dodaniu subskrybentów, co może prowadzić do posiadania większej liczby przypisanych subskrypcji niż licencji należących do firmy. Jest to nazywane "zbytnią alokacją".  

Aby wyświetlić alokacje subskrypcji, kliknij ikonę u góry po lewej stronie, aby otworzyć okienko alokacji.  

> [!NOTE]
> Zbytnie alokacje nie są dozwolone w programach licencjonowania Open License.  Ponadto inne programy mogą wyświetlać te informacje w portalu w inny sposób.
>
> [!div class="mx-imgBorder"]
> ![Powiadomienie o przejmowanych subskrypcjach](_img/over-claimed/over-claimed-alert.png "Liczba nadanych alokacji jest wymieniona w przeglądzie i jest reprezentowana przez skrót na wykresie dla każdego typu subskrypcji.")

Zwróć uwagę, że na ekranie użyto paska skrótu, aby wskazać zbyt przydzielone subskrypcje.  Liczba zbyt wielu alokacji we wszystkich typach subskrypcji znajduje się w sekcji Przegląd u góry, a każdy poziom subskrypcji również wyświetla własny stan alokacji.  

## <a name="receive-notifications-when-over-allocations-occur"></a>Otrzymywanie powiadomień w przypadku wystąpienia zbytniej alokacji
Można wyznaczyć adres e-mail do odbierania powiadomień o wystąpieniach alokacji, a także ustawić próg, który musi zostać przekroczony przed wysyłaniem powiadomień.  Dowiedz się więcej [na temat ustawiania preferencji dla umów](admin-preferences.md) w portalu administracyjnym.

## <a name="resolve-over-allocated-subscriptions"></a>Rozwiązywanie problemów z zbyt przydzielonymi subskrypcjami
Istnieje kilka sposobów rozwiązywania problemów z przesyłaniami:
- Skontaktuj się ze sprzedawcą, aby kupić dodatkowe subskrypcje.
- Zaczekaj na roczny okres prawdziwej płatności i zapłać za przydzielone subskrypcje w tym momencie. 
- Usuń niektóre przypisania subskrypcji.  (Nie zapobiegnie to potrzebie płatności przy rocznej wartości true-up, ponieważ wartość true-up jest oparta na maksymalnej liczbie subskrypcji przypisanych w dowolnym momencie roku).

## <a name="billing-and-true-up"></a>Rozliczenia i true-up
Jeśli Twoja organizacja ma konto Enterprise Agreement (EA), administratorzy mogą przypisywać subskrypcje bez ich zakupu i płacić za nie później w ramach procesu uzgadniania nazywanego "true-up".  W przypadku zbyt dużej alokacji organizacja będzie rozliczana za maksymalną liczbę subskrypcji przypisanych do użytkowników podczas "true-up".  Ta wartość jest prawdziwa, nawet jeśli nie masz już przypisanej maksymalnej liczby subskrypcji w czasie, gdy ma miejsce true-up.  Aby dowiedzieć się więcej na temat monitorowania maksymalnego użycia, odwiedź [temat Maksymalne użycie.](maximum-usage.md)


## <a name="see-also"></a>Zobacz też
- [Visual Studio dokumentacji](/visualstudio/)
- [Azure DevOps documentation (Dokumentacja usługi Azure DevOps)](/azure/devops/)
- [Dokumentacja platformy Azure](/azure/)
- [Microsoft 365 dokumentacji](/microsoft-365/)

## <a name="next-steps"></a>Następne kroki
- Dowiedz się więcej na [temat zarządzania Visual Studio subskrypcjami za pomocą GitHub Enterprise](assign-github.md).
- Aby uzyskać pomoc w zakresie sprzedaży, subskrypcji, kont i rozliczeń dla subskrypcji Visual Studio, skontaktuj się z Visual Studio [pomocy technicznej dotyczącej subskrypcji.](https://aka.ms/vsadminhelp)