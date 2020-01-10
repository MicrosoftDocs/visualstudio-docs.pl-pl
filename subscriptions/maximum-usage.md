---
title: Korzystanie z funkcji maksymalnego użycia w portalu administracyjnym
author: evanwindom
ms.author: lank
manager: lank
ms.date: 03/24/2019
ms.topic: conceptual
description: Dowiedz się, jak wyświetlić maksymalną liczbę przypisanych subskrypcji w portalu administracyjnym
ms.openlocfilehash: 76360c9843d82350a2b9929b8debfdb4aa4cde82
ms.sourcegitcommit: c150d0be93b6f7ccbe9625b41a437541502560f5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/10/2020
ms.locfileid: "75852342"
---
# <a name="use-the-maximum-usage-feature-to-track-the-number-of-assigned-subscriptions"></a>Śledzenie liczby przypisanych subskrypcji przy użyciu funkcji maksymalnego użycia
Nowa funkcja portalu administracyjnego subskrypcji programu Visual Studio pomaga śledzić liczbę subskrybowanych i przypisanych subskrypcji oraz określać szczytową liczbę subskrypcji każdego przypisanego poziomu, zarówno w ciągu ostatniego roku, jak i w całej czas trwania umów. 

## <a name="view-your-maximum-usage"></a>Wyświetlanie maksymalnego użycia
Aby wyświetlić szczytową liczbę subskrypcji przypisanych do dowolnej umowy i poziomu subskrypcji:
1. Wybierz umowę do wyświetlenia na liście rozwijanej w lewym górnym rogu portalu. (Jeśli masz tylko jedną umowę, zostanie ona już zaznaczona).
2. Kliknij kartę **maksymalne użycie** .  
    > [!div class="mx-imgBorder"]
    > Menu ![maksymalnego użycia](_img/maximum-usage/maximum-usage-menu.png)
3. Zostanie wyświetlone okno "maksymalne Podsumowanie użycia" i zostanie wyświetlona Maksymalna liczba subskrypcji przypisanych w ciągu ostatniego roku dla każdego poziomu wraz z datą osiągnięcia tego szczytu.  Po osiągnięciu tego szczytu więcej niż raz, zostanie wyświetlony pierwszy raz. 
    > [!div class="mx-imgBorder"]
    > ![podsumowanie maksymalnego użycia](_img/maximum-usage/maximum-usage-summary.png)
4. Aby wyświetlić maksymalną liczbę subskrypcji przypisanych do okresu istnienia umowy, kliknij kartę **pełny okres** .

## <a name="view-your-assignment-history"></a>Wyświetl historię przypisania
Oprócz wyświetlania szczytowych przydziałów dla poszczególnych poziomów subskrypcji można zobaczyć uruchomione konto działania na umowie, w tym zakupów i przydziałów, klikając przycisk **Eksportuj pełny raport** .  

> [!div class="mx-imgBorder"]
> Pełny raport ![maksymalnego użycia](_img/maximum-usage/maximum-usage-full-report.png)

W przypadku każdego poziomu subskrypcji raport przedstawia datę osiągnięcia nowego maksymalnego poziomu przydziału oraz liczbę subskrypcji zakupionych w ramach tego dnia, co pozwala na łatwe przeglądanie dowolnych dat, w których wystąpiły nadmierne alokacje.  

Na przykład w powyższej tabeli można zobaczyć, że w dniu 12/13/2018 wystąpiły 123 Visual Studio Enterprise subskrypcje i 120 zostały przypisane.  W dniu 1/8/2019 przypisano jeszcze jedną subskrypcję z sumą do 121.  Kolejny dzień, przypisano kolejne sześć subskrypcji i dodano kolejne cztery subskrypcje do umowy w celu pokrycia nowych przypisań.  

## <a name="frequently-asked-questions"></a>Często zadawane pytania
### <a name="q-how-is-the-information-in-the-maximum-usage-different-from-the-assignment-information-available-in-the-overview-section-on-the-left-side-of-the-portal"></a>P: jak informacje o maksymalnym użyciu różnią się od informacji o przypisaniu dostępnych w sekcji "przegląd" po lewej stronie portalu?
Odp.: informacje w omówieniu przedstawiają *bieżące* przypisania i dostępne subskrypcje dla poszczególnych poziomów subskrypcji.  Może to być bardzo różne od maksymalnej liczby subskrypcji przypisanych do umowy w bieżącym roku lub w okresie obowiązywania umowy.  Funkcja maksymalnego użycia pozwala zobaczyć, kiedy zostały osiągnięte maksymalne poziomy przypisania i jakie są poziomy.  Jest to ważne rozróżnienie, ponieważ opłaty za subskrypcje są naliczane na podstawie maksymalnej liczby subskrypcji przypisanych w dowolnym momencie w roku. 

## <a name="resources"></a>Resources
- [Oficjalny dokument dotyczący licencjonowana programu Visual Studio](https://visualstudio.microsoft.com/wp-content/uploads/2019/06/Visual-Studio-Licensing-Whitepaper-May-2019.pdf)
- [Pomoc techniczna dotycząca subskrypcji programu Visual Studio i administrowania nim](https://visualstudio.microsoft.com/support/support-overview-vs)
- [Postanowienia dotyczące licencjonowania zbiorowego](https://www.microsoft.com/licensing/product-licensing/products.aspx)

## <a name="next-steps"></a>Następne kroki
- Jeśli masz jakieś pytania dotyczące przypisań subskrypcji lub innych aspektów portalu administracyjnego, skontaktuj się z pomocą techniczną, aby uzyskać pomoc w https://visualstudio.microsoft.com/subscriptions/support/. 
- Dowiedz się więcej o tym, co należy zrobić, Jeśli przypiszesz więcej zakupionych subskrypcji, nazywanych [nadmiernymi alokacjami](handle-overclaimed-license.md).
