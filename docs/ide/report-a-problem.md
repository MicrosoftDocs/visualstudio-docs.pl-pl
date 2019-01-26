---
title: zgłaszanie problemu
description: Zawiera omówienie raportu narzędzie Problem i zawiera stany problem i definicje
ms.date: 11/15/2018
ms.prod: visual-studio-dev15
ms.custom: seodec18
ms.topic: conceptual
author: seaniyer
ms.author: seiyer
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d01686d3e0bbc034095ae1b4ec54e5995fc6462f
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "54958735"
---
# <a name="overview-report-a-problem"></a>Przegląd: Zgłoś Problem

Raport narzędzia Problem umożliwia społeczności deweloperów programu Visual Studio, aby przesyłać problemy. Każdej z nich raporty o problemach staje się elementu roboczego na naszych podstawowych inżynierii systemu, co pozwala na angażowanie bezpośrednio z naszych zespołów produktu, aby pomóc nam identyfikować i rozwiązywać problemy z atrakcyjnych. Twoja opinia przesłane zawierających rozbudowane informacje diagnostyczne jest krytyczne dla poprawy rodziny produktów Visual Studio. Naprawdę Doceniamy poświęcenie czasu na zgłaszanie problemów.

Ponadto można oddawać głosy na opinię z innym członkom społeczności, aby wyświetlić większej uwagi na problem i szybsze rozwiązanie problemu.

## <a name="problem-status"></a>Stan problemu

Po zgłosić problem stany wskazują, gdzie materiałów przesłanych znajdują się w ich cyklu życia. Zgodnie z aplikacją Microsoft teams, Przejrzyj swoje opinie, mogą ustawić go przy użyciu właściwego stanu.  Śledź postęp raporty o problemach, odwołując się do stanów wymienione poniżej pod warunkiem wraz z ich znaczenia i kolor wskaźników.

![Nowy stan dla problemu raportowanie społeczności deweloperów](../ide/media/ProblemStates/New.jpg)

**Nowe** wskazuje, że nowo zgłaszane usterki lub problem i nie uwzględniono w niej jeszcze.

- - -

![Stan problemu raportowanie społeczności deweloperów zaklasyfikowane](../ide/media/ProblemStates/Triaged.jpg)

**Zaklasyfikowane** wskazuje, że wstępne kroki Moderowanie, tłumaczenia i początkowe sprawdzanie duplikatów ukończone. Bilet został przesłany do odpowiedniego zespołu inżynieryjnego wziąć pod uwagę.

- - -

![W obszarze stanu brany pod uwagę w przypadku problemu raportowanie społeczności deweloperów](../ide/media/ProblemStates/UnderConsideration.jpg)

**Rozważany** wskazuje, że Microsoft dokonuje przeglądu problemu dla społeczności, wpływ i powoduje zwiększenie priorytetu go odpowiednio. Wpływ społeczności nie jest jasne lub znaczące jeszcze, będziemy monitorować problem w tym stanie.

- - -

![W obszarze Stan badania problemu raportowanie społeczności deweloperów](../ide/media/ProblemStates/UnderInvestigation.jpg)

**W obszarze badania** wskazuje, że inżynierów aktywnie pracują nad jego problemu można znaleźć rozwiązania.

- - -

![Potrzebujesz więcej informacji o stanie problemu raportowanie społeczności deweloperów](../ide/media/ProblemStates/NeedMoreInfo.jpg)

**Potrzebujesz więcej informacji** wskazuje, że potrzebujemy więcej informacji diagnostycznych od Ciebie tak, aby firma Microsoft może przejść do przodu w badaniu.  [Dowiedz się, jak odpowiadać na żądania dalszych informacji.](./how-to-report-a-problem-with-visual-studio-2017.md#when-further-information-is-needed-need-more-info)

- - -

![Rozwiązany — oczekiwanie na wydanie stanu problemu raportowanie społeczności deweloperów](../ide/media/ProblemStates/FixedPendingRelease.jpg)

**Stałe — oczekiwanie na wydanie** wskazuje, że istnieje rozwiązanie tego problemu i będzie on dostępny w nadchodzącej wersji zapoznawczej lub wersji.  Gdy poprawka stanie się dostępna w wersji zapoznawczej, ten problem zostanie oznaczony znacznikiem "fixed w" Określanie wersji zapoznawczej.

- - -

![Zamknięte — stan stały dla problemu raportowanie społeczności deweloperów](../ide/media/ProblemStates/ClosedFixed.jpg)

**Zamknięty — rozwiązany** wskazuje, że wydaliśmy poprawkę rozwiązującą ten problem. Problem jest teraz również oznaczane "rozwiązane w:" tag określania pełnej wersji.

- - -

![Zamknięty — duplikat stan problemu raportowanie społeczności deweloperów](../ide/media/ProblemStates/ClosedDuplicate.jpg)

**Zamknięty — duplikat** wskazuje, że problem został już zgłoszony za pośrednictwem innego opinii. Firma Microsoft udostępni możesz za pomocą linku służącego do śledzenia oryginalny raport o problemie.

- - -

![Zamknięte — niższy priorytet stan problemu raportowanie społeczności deweloperów](../ide/media/ProblemStates/ClosedLowerPriority.jpg)

**Zamknięte — niższy priorytet** skoncentrować się na dostosowanie się w naszej społeczności deweloperów o najwyższej wartości, znaczenie przy określaniu priorytetów problemy związane z sobą największe skutki klienta. Mimo że firma Microsoft nie uda się rozwiązać problem związany z określonym w tej chwili, mieć pewność, że wszystkie Twoje opinie są cenne i pomagają poprawić program Visual Studio.

- - -

![Zamknięty — nie stan błędu w przypadku problemu raportowanie społeczności deweloperów](../ide/media/ProblemStates/ClosedNotaBug.jpg)

**Zamknięty — nie usterka** wskazuje, że firma Microsoft posiadany to funkcje zgłoszonych przez bieżący projekt.

- - -

![Zamknięty — nie ma wystarczającej ilości informacji o stan problemu raportowanie społeczności deweloperów](../ide/media/ProblemStates/ClosedNotEnoughInfo.jpg)

**Zamknięte — Brak wystarczającej ilości informacji** oznacza, że firma Microsoft nie ma wystarczających informacji, aby zbadać to dla Ciebie. Będziemy wszystkiego o ponowne rozpatrzenie opinii po udostępnieniu niezbędne informacje.

- - -

![Zamknięte — inny stan produktu dla problemu raportowanie społeczności deweloperów](../ide/media/ProblemStates/ClosedOtherProduct.jpg)

**Zamknięte — inny produkt** wskazuje już Ustaliliśmy, że problem ma zastosowanie do innego produktu. Zobacz komentarz od firmy Microsoft, dla którego zewnętrzne produktu i wszystkie łącza pokrewne.

- - -

![Zamknięty — nie do naprawienia stan problemu raportowanie społeczności deweloperów](../ide/media/ProblemStates/ClosedWontFix.jpg)

**Zamknięty — nie do naprawienia** wskazuje, że firma Microsoft nie są należy wykonać ten problem, ze względu na czynników, takich jak brak wpływu wyrównania lub społeczności kierunek produktu. Zobacz komentarz od firmy Microsoft dla dowolnego dodatkowego wyjaśnienia.  Mimo że nie można rozwiązać tego konkretnego problemu, należy zapewnić, że wszystkie opinie są cenne i pomagają poprawić program Visual Studio.

- - -

## <a name="faq"></a>Najczęściej zadawane pytania

### <a name="how-can-i-increase-the-chance-of-my-problem-getting-resolved-quickly"></a>Jak zwiększyć prawdopodobieństwo wprowadzenie szybko rozwiązać problem?

Firma Microsoft zaleca, aby upewnić się, czy problem, który masz zamiar raport już nie został zgłoszony w wyszukiwaniu. Jeśli istniejący element dopasowania problemu możesz znaleźć, wykonaj i głosować w sprawie tego biletu problem.

 Podaj informacje, które mogą pomóc nasze zespoły odtworzenia swój problem.  Informacje te obejmują potrzeby Odtwórz kroki, fragmenty kodu, zrzuty ekranu, nagrania odtwarzania, pliki dziennika i innych artefaktów.  Oto [jak zgłosić problem w programie Visual Studio](./how-to-report-a-problem-with-visual-studio-2017.md).

### <a name="how-is-my-feedback-prioritized"></a>Jak ma priorytet moje opinie

Firma Microsoft otrzyma dużej liczby cenne problemów od naszych klientów. Aby upewnić się, że do każdego, udostępniamy o najwyższej wartości w naszej społeczności deweloperów, znaczenie przy określaniu priorytetów działań na opinie, które ma wpłynąć społeczności.

Jeśli nie możemy osobiście reagować na opinie użytkowników, że firma Microsoft pełni docenić dane wejściowe. Mieć pewność, że Twoja opinia pobiera odpowiedni zespół.

Naprawdę Doceniamy czas zainwestować w zapewnienie lepszego programu Visual Studio.

### <a name="what-actions-can-i-take-if-im-not-satisfied-with-the-resolution"></a>Jakie akcje mogą muszę zrobić, jeśli nie mam zadowolony z rozwiązania?

Nasze zespoły nie optymalne, aby zdiagnozować i rozwiązać problemy, które występują, jednak czasami może być po zakończeniu nie pełni nasze zalecenie. Komentarz po powrocie na opinie i Daj nam znać dokładnie, co nie jesteś zadowolony z, a spróbujemy najlepszych upewnij się, że firma Microsoft własnych potrzeb.

### <a name="how-will-i-get-notified-of-progress-on-my-feedback"></a>Jak będą otrzymywać powiadomienia o postępie dotyczącymi mojej opinii?

Zespoły inżynierów firmy Microsoft będą komunikować się z Tobą, dodawania komentarzy do biletu opinii i zmiany jego stanu biletem, zgodnie z ich postęp. Poszukaj wiadomości e-mail z powiadomieniami, które są wysyłane po opublikowaniu zmian stanu biletu lub komentarz.  Możesz zarządzać częstotliwości powiadomień w ustawieniach profilu i preferencje klientów w witrynie społeczności deweloperów.

### <a name="why-cant-i-add-a-problem-for-visual-studio-ide-on-the-developer-community-website"></a>Dlaczego nie mogę dodać problem dla środowiska IDE programu Visual Studio w witrynie sieci Web społeczności deweloperów?

Zgłoszenie problemu za pomocą programu Visual Studio umożliwia informacje diagnostyczne automatycznie uwzględnione w raporcie. To podstawowe informacje, które zapewnia nasi inżynierowie zajmujący się kontekstu muszą być w pełni ułatwią zrozumienie problemu i pracy, aby rozwiązać ten problem.

Gdy raport za pomocą programu Visual Studio możesz mogą łatwo udostępniać rozbudowane informacje diagnostyczne z nami, takich jak duże pliki dziennika, informacje o awariach, zrzuty ekranu, nagrywania odtwarzania i innych artefaktów, które pomagają nam dostarczać szybciej rozdzielczości wyższej jakości do Ciebie.