---
title: Często zadawane pytania dotyczące rozliczeń dla subskrypcji w chmurze programu Visual Studio Enterprise i Visual Studio Professional
author: evanwindom
ms.author: v-evwin
manager: lank
ms.assetid: 21e0471d-ad59-4d21-9c6f-13f7147569af
ms.date: 03/24/2020
ms.topic: conceptual
description: Pytania dotyczące rozliczeń dotyczących subskrypcji w chmurze.
ms.openlocfilehash: a9845078a17425322dfd86bf417daa24238c7b0f
ms.sourcegitcommit: dfa9476b69851c28b684ece66980bee735fef8fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/26/2020
ms.locfileid: "80273832"
---
# <a name="visual-studio-cloud-subscriptions-billing-faq"></a>Często zadawane pytania dotyczące rozliczeń subskrypcji w chmurze programu Visual Studio
Upewnij się, że [porównaj korzyści z subskrypcji w chmurze i ceny,](https://visualstudio.microsoft.com/vs/pricing/) aby zrozumieć zalety każdej subskrypcji programu Visual Studio, z porównaniami między subskrypcjami w chmurze i standardowymi programami Visual Studio, szczegółami dotyczącymi korzyści dla subskrybentów i nie tylko.

## <a name="general-purchasing-questions"></a>Ogólne pytania zakupowe
### <a name="q-can-i-buy-visual-studio-cloud-subscriptions-using-a-purchase-order"></a>Pyt.: Czy można kupić subskrypcje w chmurze programu Visual Studio przy użyciu zamówienia zakupu?
Odpowiedź: nie. Wszystkie subskrypcje w chmurze programu Visual Studio muszą zostać zakupione przy użyciu subskrypcji platformy Azure. (Pomyśl o tym jako o koncie rozliczeniowym platformy Azure).

### <a name="q-what-types-of-azure-subscriptions-can-be-used-to-buy-visual-studio-cloud-subscriptions"></a>Pyt.: Jakie typy subskrypcji platformy Azure mogą służyć do zakupu subskrypcji w chmurze programu Visual Studio?
O: Większość subskrypcji platformy Azure może być używana — obsługujemy subskrypcje platformy Azure połączone z [umową Enterprise Agreement (EA),](https://azure.microsoft.com/pricing/enterprise-agreement/)subskrypcje platformy Azure skonfigurowane przez dostawców rozwiązań w chmurze (CSP), subskrypcje platformy Azure skonfigurowane za pośrednictwem odsprzedawców microsoft open license i subskrypcje platformy Pay-As-You-Go Azure.

Nie można używać niektórych typów subskrypcji platformy Azure, w tym [bezpłatnej wersji próbnej platformy Azure](https://azure.microsoft.com/pricing/free-trial/) i subskrypcji uwzględnionych jako korzyści dla subskrybentów w subskrypcjach programu Visual Studio.

### <a name="q-am-i-required-to-buy-other-azure-services"></a>Pyt.: Czy muszę kupić inne usługi platformy Azure?
O: Wcale nie. Jeśli chcesz kupić tylko subskrypcje w chmurze programu Visual Studio za pośrednictwem platformy Azure, możesz to zrobić.

## <a name="enterprise-agreement-ea-customers"></a>Klienci korzystający z umowy Enterprise Agreement (EA)
### <a name="q-can-i-use-an-enterprise-agreement-to-buy-visual-studio-cloud-subscriptions"></a>Pyt.: Czy można użyć umowy Enterprise Agreement do zakupu subskrypcji w chmurze programu Visual Studio?
O: Tak, możesz. Musisz być właścicielem lub współautorem subskrypcji platformy Azure, która została utworzona dla Twojej usługi EA. Upewnij się, że zakupy dla subskrypcji w chmurze programu Visual Studio są bezpośrednio w witrynie Visual Studio Marketplace. Nie można kupić subskrypcji w chmurze programu Visual Studio przy użyciu zamówienia zakupu.

### <a name="q-how-can-i-tell-whether-i-have-the-necessary-privileges-to-buy-services-in-the-visual-studio-marketplace-through-my-organizations-enterprise-agreement"></a>Pyt.: Jak sprawdzić, czy mam uprawnienia niezbędne do zakupu usług w portalu Visual Studio Marketplace za pośrednictwem umowy Enterprise Agreement mojej organizacji?
Odp.: Najprostszym podejściem do określenia, czy masz odpowiednie uprawnienia, jest kliknięcie przycisku **Kup** dla usługi oferowanej w witrynie Visual Studio Marketplace.
Musisz wybrać subskrypcję platformy Azure (która jest kontem rozliczeniowym) z wyświetlona lista subskrypcji platformy Azure, które są obecnie połączone z twoim loginem.
Ponieważ nazwa subskrypcji platformy Azure domyślnie do typu konta rozliczeniowego ("Płatność zgodnie z rzeczywistym umowy", "Enterprise Agreement" itp.), często jest jasne, czy subskrypcja platformy Azure jest częścią umowy Enterprise Agreement.

Innym podejściem jest próba odwiedzenia [usługi Azure Enterprise Portal](https://ea.azure.com).  Jeśli możesz osiągnąć go pomyślnie, masz już rolę Enterprise Admin lub Account Owner. Tylko właściciele kont mogą umować nowe konta rozliczeniowe platformy Azure w umowie Enterprise Agreement. Jeśli nie możesz uzyskać dostępu do usługi Azure Enterprise Portal, skontaktuj się z zapytaniem w organizacji, aby dowiedzieć się, kim jest administrator przedsiębiorstwa, i poproś tę osobę o dodanie Cię jako właściciela konta w usłudze Azure Enterprise Portal.  Jeśli nie możesz znaleźć tej osoby, możesz [przesłać zgłoszenie pomocy technicznej](https://support.microsoft.com/supportrequestform/cf791efa-485b-95a3-6fad-3daf9cd4027c) i poprosić o informacje kontaktowe.  Dla biletu pomocy technicznej potrzebna jest nazwa organizacji i numer rejestracji umowy Enterprise Agreement.

### <a name="q-can-i-use-the-azure-monetary-commitment-funds-from-my-enterprise-agreement-to-buy-visual-studio-cloud-subscriptions"></a>Pyt.: Czy mogę używać funduszy zobowiązania pieniężnego platformy Azure z umowy Enterprise Agreement do zakupu subskrypcji w chmurze programu Visual Studio?
Odp.: Nie, te środki przedpłaty nie kwalifikują się do zakupu subskrypcji w chmurze programu Visual Studio. Po wybraniu subskrypcji platformy Azure, która została utworzona dla EA do zakupu subskrypcji w chmurze programu Visual Studio, opłaty pojawią się na następnej fakturze "overage". Zazwyczaj dzieje się tak co miesiąc, ale ze względu na historyczne zasady dla niektórych klientów EA, faktura za przeszłe może nie być wystawiana przez kilka miesięcy. Jeśli chcesz wiedzieć, jaka kwota dodatkowych zakupów (zakupów, które nie kwalifikują się do otrzymania środków z funduszy na zobowiązania pieniężne platformy Azure) zostanie uruchomiona faktura za zobowiązania pieniężne platformy Azure, wywoła wystawienie faktury za nadmierne zobowiązania.

## <a name="how-charges-are-processed"></a>Sposób przetwarzania opłat
### <a name="q-how-are-monthly-cloud-subscription-charges-processed"></a>Pyt.: W jaki sposób są przetwarzane **miesięczne** opłaty za subskrypcje w chmurze?
O: Przy pierwszym zakupie rozliczamy proporcjonalną ilość na pokrycie pozostałych dni w bieżącym miesiącu. Na przykład jeśli zakup 10 Visual Studio Professional miesięczne subskrypcje w chmurze została dokonana w dniu 15 kwietnia, a następnie będziemy pobierać 5 jednostek, ponieważ 50% miesiąca pozostaje (15 dni 30-dniowego miesiąca).
W pierwszym maju, a następnie w każdym miesiącu do momentu anulowania, zostanie naliczona pełna 10 jednostek.

Po zwiększeniu płatnej ilości później, możemy również proporcjonalnie do zwiększonych jednostek na pokrycie pozostałych dni w bieżącym miesiącu. Jeśli więc kupisz jeszcze 1 miesięczną subskrypcję w chmurze programu Visual Studio Professional 10 maja, naliczymy około 0,677 jednostek (21 dni pozostałych w 31-dniowym miesiącu maja).

### <a name="q-how-are-annual-cloud-subscription-charges-processed"></a>Pyt.: W jaki sposób są przetwarzane **roczne** opłaty za subskrypcje w chmurze?
Odp.: Przy każdym zakupie rozliczamy natychmiast całą zakupioną ilość. Opłaty nie są rozłożone na cały rok i nie ma proratingu. Jeśli kupujesz roczne subskrypcje w chmurze o różnych porach roku, subskrypcje będą odnawiane w różnych miesiącach. Nie dokonujemy spójności wszystkich rocznych subskrypcji w chmurze klienta, jak to jest powszechne w przypadku zakupu umowy licencjonowania zbiorowego firmy Microsoft.

### <a name="q-how-do-cancelations-work"></a>P: Jak działają anulowania?
Odp.: Po anulowaniu subskrypcji w chmurze programu Visual Studio anulujesz automatyczne odnawianie. Subskrypcja jest kontynuowana do zwykłej daty odnowienia, a następnie po prostu wygasa.
Po wygaśnięciu subskrybent programu Visual Studio nie może już używać programu Visual Studio ani żadnych innych korzyści z subskrypcji.

W przypadku miesięcznych subskrypcji w chmurze anulowanie pracy zaczyna obowiązywać pierwszego dnia następnego miesiąca. Jeśli anulujesz tylko niektóre z miesięcznych subskrypcji w chmurze, pamiętaj, aby usunąć użytkowników pierwszego z następnego miesiąca, aby upewnić się, że poprawne osoby nadal mają przypisane aktywne subskrypcje.

W przypadku rocznych subskrypcji w chmurze anulowanie jest skuteczne pierwszego dnia miesiąca następującego po 12 miesiącach od pierwotnego zakupu lub 12 miesięcy od ostatniej rocznej opłaty za odnowienie. Na przykład jeśli zakupiono roczną subskrypcję chmury programu Visual Studio Professional 3 stycznia 2018 r., pozostanie ona aktywna do 1 lutego 2019 r., kiedy zostanie automatycznie odnowiona na kolejny rok. Jeśli anulujesz subskrypcję w dowolnym momencie między tym a 1 lutego 2020 r., subskrypcja wygaśnie 1 lutego 2020 r. Nie ma rabatu za anulowanie części w ciągu roku subskrypcji z rocznymi subskrypcjami w chmurze.

### <a name="q-what-kind-of-volume-discounts-are-available-for-visual-studio-subscriptions"></a>Pyt.: Jakiego rodzaju rabaty zbiorcze są dostępne dla subskrypcji programu Visual Studio?
Odp.: Otrzymasz 5% zniżki na 6 i wszystkie kolejne subskrypcje *w ramach każdego typu* subskrypcji:

* Program Visual Studio Professional co miesiąc
* Visual Studio Professional roczne
* Program Visual Studio Enterprise co miesiąc
* Roczne wersje programu Visual Studio Enterprise

Na przykład, jeśli kupisz 6 miesięcznych subskrypcji Programu Visual Studio Professional i 5 miesięcznych subskrypcji Visual Studio Enterprise, zapłacisz regularną cenę na 5 Professional, otrzymasz 5% zniżki na 6. Subskrypcji.

Ponadto rabat dotyczy tylko opłat w danym miesięcznym okresie rozliczeniowym. Jeśli więc kupisz 5 rocznych subskrypcji programu Visual Studio Professional w ciągu jednego miesiąca, a następnie kupisz 5 kolejnych w następnym miesiącu, zapłacisz normalną cenę za wszystkie subskrypcje 10.

> [!NOTE]
> Firma Microsoft nie oferuje już rocznych subskrypcji programu Visual Studio Professional i rocznych subskrypcji programu Visual Studio Enterprise w subskrypcjach w chmurze. Nie będzie żadnych zmian w istniejącym doświadczeniu klientów i możliwości odnawiania, zwiększania, zmniejszania lub anulowania subskrypcji. Zachęcamy nowych klientów, [https://visualstudio.microsoft.com/vs/pricing/](https://visualstudio.microsoft.com/vs/pricing/) aby przejść do eksplorowania różnych opcji zakupu programu Visual Studio.

## <a name="other-questions"></a>Inne pytania
### <a name="q-can-i-use-the-monthly-azure-devtest-individual-credit-as-a-visual-studio-subscriber-to-buy-more-visual-studio-cloud-subscriptions"></a>Pyt.: Czy mogę użyć miesięcznych indywidualnych środków usługi Azure DevTest jako subskrybent programu Visual Studio, aby kupić więcej subskrypcji w chmurze programu Visual Studio?
Odp.: Nie, nie można używać [miesięcznych indywidualnych środków platformy Azure DevTest](https://azure.microsoft.com/pricing/member-offers/credit-for-visual-studio-subscribers/) jako subskrybenta programu Visual Studio do płacenia za zakupy w witrynie Visual Studio Marketplace. Wszelkie zakupy w chmurze programu Visual Studio będą rozliczane na karcie kredytowej.
Przed dokonaniem zakupów należy [usunąć limit wydatków](https://azure.microsoft.com/pricing/spending-limits/).

### <a name="q-whats-the-difference-between-annual-and-monthly-cloud-subscriptions"></a>P: Jaka jest różnica między roczną i miesięczną subskrypcją w chmurze?
Odp.: Miesięczne subskrypcje w chmurze obejmują program Visual Studio oraz korzystanie z usług Azure DevOps i usług TFS. Roczne subskrypcje w chmurze również to mają, ale obejmują również korzyści dla subskrybentów, w tym korzystanie z systemu Windows i innego oprogramowania firmy Microsoft do instalowania i uruchamiania w celu tworzenia i testowania, miesięczny indywidualny kredyt azure devtest używany do eksperymentowania z platformą Azure i testowanie w chmurze, szkolenia, wsparcie i wiele więcej.
[Porównanie korzyści z subskrypcji w chmurze i cen](https://visualstudio.microsoft.com/vs/pricing/)

### <a name="q-do-i-get-new-versions-of-visual-studio-if-i-buy-a-visual-studio-cloud-subscription"></a>Pyt.: Czy mogę uzyskać nowe wersje programu Visual Studio, jeśli kupię subskrypcję w chmurze programu Visual Studio?
O: Tak. W miarę wydania nowych wersji można je pobrać i uruchomić. Plus można nadal uruchamiać poprzednie wersje zbyt.

### <a name="q-can-i-buy-visual-studio-cloud-subscriptions-from-my-software-reseller"></a>Pyt.: Czy mogę kupić subskrypcje w chmurze programu Visual Studio od sprzedawcy oprogramowania?
O: Tak, możesz, jeśli twój sprzedawca uczestniczy w programie Dostawcy rozwiązań w chmurze (CSP). Po prostu zapytaj ich.

## <a name="related-resources"></a>Powiązane zasoby
- [Portal administrowania subskrypcjami programu Visual Studio](https://manage.visualstudio.com/)
- [Pomoc techniczna w ramach subskrypcji programu Visual Studio](https://visualstudio.microsoft.com/vs/support/)
- [Zakup subskrypcji w chmurze programu Visual Studio dla dostawców usług skrypcyjnych](vscloud-csp.md)

## <a name="see-also"></a>Zobacz też
- [Dokumentacja programu Visual Studio](https://docs.microsoft.com/visualstudio/)
- [Dokumentacja usługi Azure DevOps](https://docs.microsoft.com/azure/devops/)
- [Dokumentacja platformy Azure](https://docs.microsoft.com/azure/)
- [Dokumentacja usługi Microsoft 365](https://docs.microsoft.com/microsoft-365/)

## <a name="next-steps"></a>Następne kroki
Kup subskrypcje w chmurze już teraz
- [Program Visual Studio Professional co miesiąc](https://marketplace.visualstudio.com/items?itemName=ms.vs-professional-monthly)
- [Program Visual Studio Enterprise co miesiąc](https://marketplace.visualstudio.com/items?itemName=ms.vs-enterprise-monthly)
