---
title: Często zadawane pytania dotyczące subskrypcji Visual Studio Enterprise i Visual Studio Professional w chmurze
author: evanwindom
ms.author: lank
manager: lank
ms.date: 07/28/2019
ms.topic: conceptual
description: Pytania dotyczące rozliczeń dla subskrypcji chmury.
ms.openlocfilehash: 12ff77a052e54520885642cb3cd6ed1dea31506b
ms.sourcegitcommit: b5cb0eb09369677514ee1f44d5d7050d34c7fbc1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/26/2019
ms.locfileid: "74491263"
---
# <a name="visual-studio-cloud-subscriptions-billing-faq"></a>Subskrypcje dotyczące rozliczeń w ramach subskrypcji programu Visual Studio Cloud
[PORÓWNAJ korzyści z subskrypcji chmury i ceny](https://visualstudio.microsoft.com/vs/pricing/) , aby poznać zalety każdej subskrypcji programu Visual Studio, z porównaniami między subskrypcjami w chmurze i standardami programu Visual Studio, szczegółowymi dotyczącymi korzyści dla subskrybentów i innymi.

## <a name="general-purchasing-questions"></a>Ogólne pytania dotyczące zakupu
### <a name="q-can-i-buy-visual-studio-cloud-subscriptions-using-a-purchase-order"></a>P: Czy mogę kupić subskrypcje programu Visual Studio w chmurze przy użyciu zamówienia zakupu?
Odp.: Nie. Wszystkie subskrypcje programu Visual Studio w chmurze muszą zostać zakupione przy użyciu subskrypcji platformy Azure. (Pomyśl, że jest to konto rozliczeniowe platformy Azure).

### <a name="q-what-types-of-azure-subscriptions-can-be-used-to-buy-visual-studio-cloud-subscriptions"></a>P: jakich typów subskrypcji platformy Azure można używać do kupowania subskrypcji w chmurze programu Visual Studio?
Odp.: można używać większości subskrypcji platformy Azure — obsługujemy subskrypcje platformy Azure połączone z [Umowa Enterprise (EA)](https://azure.microsoft.com/pricing/enterprise-agreement/), subskrypcje platformy Azure skonfigurowane przez dostawców rozwiązań w chmurze (CSP), subskrypcje platformy Azure skonfigurowane w ramach odsprzedawcaów licencji Open firmy Microsoft oraz subskrypcje platformy Azure z płatność zgodnie z rzeczywistym użyciem.

Nie można używać niektórych typów subskrypcji platformy Azure, w tym [bezpłatnej wersji próbnej platformy Azure](https://azure.microsoft.com/pricing/free-trial/) i subskrypcji oferowanych w ramach subskrypcji programu Visual Studio.

### <a name="q-am-i-required-to-buy-other-azure-services"></a>P: Czy muszę kupić inne usługi platformy Azure?
Odp.: nie. Jeśli chcesz kupić subskrypcje programu Visual Studio w chmurze tylko za pośrednictwem platformy Azure, możesz to zrobić.

## <a name="enterprise-agreement-ea-customers"></a>Klienci korzystający z Umowa Enterprise (EA)
### <a name="q-can-i-use-an-enterprise-agreement-to-buy-visual-studio-cloud-subscriptions"></a>P: Czy można używać Umowa Enterprise do kupowania subskrypcji programu Visual Studio w chmurze?
Odp.: tak, możesz. Musisz być właścicielem lub współautorem subskrypcji platformy Azure, która została utworzona dla umowy EA. Upewnij się, że zakupy dla subskrypcji programu Visual Studio Cloud są wprowadzane bezpośrednio w Visual Studio Marketplace. Nie można kupić subskrypcji programu Visual Studio w chmurze przy użyciu zamówienia zakupu.

### <a name="q-how-can-i-tell-whether-i-have-the-necessary-privileges-to-buy-services-in-the-visual-studio-marketplace-through-my-organizations-enterprise-agreement"></a>P: Jak mogę sprawdzić, czy mam wymagane uprawnienia do kupowania usług w Visual Studio Marketplace za pomocą Umowa Enterprise organizacji?
Odp.: najprostszym podejściem do ustalenia, czy masz odpowiednie uprawnienia, jest kliknięcie przycisku **Kup** dla usługi oferowanej w Visual Studio Marketplace.
Musisz wybrać subskrypcję platformy Azure (czyli konto rozliczeniowe) z wyświetlonej listy subskrypcji platformy Azure, które są obecnie połączone z logowaniem.
Ponieważ nazwa usługi Azure Subscription jest domyślna dla typu konta rozliczeniowego ("płatność zgodnie z rzeczywistym użyciem", "Umowa Enterprise" itp.), często jest jasne, jeśli subskrypcja platformy Azure jest częścią Umowa Enterprise.

Innym rozwiązaniem jest próba odwiedzenia [Enterprise Portal platformy Azure](https://ea.azure.com).  Jeśli możesz się z nią skontaktować, masz już rolę administratora przedsiębiorstwa lub właściciela konta. Tylko właściciele konta mogą konfigurować nowe konta rozliczeń platformy Azure w Umowa Enterprise. Jeśli nie możesz uzyskać dostępu do usługi Azure Enterprise Portal, skontaktuj się z pomocą techniczną w organizacji, aby dowiedzieć się, kto jest administratorem przedsiębiorstwa, i poproś o dodanie Cię jako właściciela konta w ramach usługi Azure Enterprise Portal.  Jeśli nie możesz znaleźć tej osoby, możesz [przesłać bilet pomocy technicznej](https://aka.ms/AzureEntSupport) i zażądać informacji kontaktowych.  W przypadku biletu pomocy technicznej potrzebna jest nazwa organizacji i numer rejestracji Umowa Enterprise.

### <a name="q-can-i-use-the-azure-monetary-commitment-funds-from-my-enterprise-agreement-to-buy-visual-studio-cloud-subscriptions"></a>P: Czy mogę użyć funduszy zobowiązania pieniężnego platformy Azure z mojej Umowa Enterprise, aby kupić subskrypcje programu Visual Studio w chmurze?
Odp.: nie, te przedpłacone środki nie kwalifikują się do zakupu subskrypcji programu Visual Studio w chmurze. Po wybraniu subskrypcji platformy Azure, która została utworzona dla umowy EA w celu zakupienia subskrypcji w chmurze programu Visual Studio, opłaty będą naliczane po następnej fakturze "nadwyżkowe". Zwykle odbywa się to co miesiąc, ale ze względu na reguły historyczne dla niektórych klientów z umowami EA, faktura nadwyżki nie może zostać wystawiona przez kilka miesięcy. Zapoznaj się z specjalistą ds. licencjonowania w ramach umowy EA, jeśli chcesz wiedzieć, jaka ilość dodatkowych zakupów (zakupów, które nie kwalifikują się do funduszy związanych z zobowiązaniami pieniężnymi platformy Azure), spowoduje wyzwolenie faktury nadwyżkowej.

## <a name="how-charges-are-processed"></a>Jak są przetwarzane opłaty
### <a name="q-how-are-monthly-cloud-subscription-charges-processed"></a>P: w jaki sposób są naliczane **miesięczne** opłaty za subskrypcję w chmurze?
Odp.: przy pierwszym zakupie opłata jest naliczana proporcjonalnie do pozostałej liczby dni w bieżącym miesiącu. Na przykład w przypadku zakupu 10 Visual Studio Professional comiesięcznych subskrypcji w chmurze w dniu 15 kwietnia firma Microsoft będzie liczyć 5 jednostek, ponieważ 50% miesiąca pozostanie (15 dni z 30-dniowym miesiącem).
W pierwszej kolejności i w każdym miesiącu, po upływie którego zostanie anulowana, zostanie naliczona pełna 10 jednostek.

Po zwiększeniu ilości płatnej później Oceńmy również zwiększenie liczby jednostek, aby pokryć pozostałe dni w bieżącym miesiącu. Jeśli więc zakupiono 1 więcej Visual Studio Professional comiesięczną subskrypcję chmury w dniu 10 maja, będziemy rozliczać około 0,677 jednostek (21 dni pozostałej w dniu 31-dniowego miesiąca).

### <a name="q-how-are-annual-cloud-subscription-charges-processed"></a>P: jak są przetwarzane **roczne** opłaty za subskrypcję w chmurze?
Odp.: przy każdym zakupie opłaty są naliczane natychmiast po zakupie. Opłaty nie są naliczane w ciągu roku i nie ma żadnej klasyfikacji. Jeśli kupisz roczną subskrypcję chmury w różnym czasie w roku, będziesz mieć subskrypcje odnawiane w różnych miesiącach. Firma Microsoft nie udostępnia żadnych rocznych subskrypcji w chmurze coterminous, które są wspólne w ramach zakupu w ramach umowy licencjonowania zbiorowego.

### <a name="q-how-do-cancelations-work"></a>P: jak działają anulowania?
Odp.: po anulowaniu subskrypcji programu Visual Studio w chmurze anulujesz automatyczne odnawianie. Subskrypcja jest kontynuowana do momentu normalnego odnowienia, a następnie po prostu wygaśnie.
Po wygaśnięciu subskrybent programu Visual Studio nie może już korzystać z programu Visual Studio ani żadnych innych korzyści z subskrypcji.

W przypadku comiesięcznych subskrypcji w chmurze, anulowania zaczynają obowiązywać pierwszego dnia następnego miesiąca. Jeśli anulujesz tylko niektóre miesięczne subskrypcje w chmurze, pamiętaj o usunięciu użytkowników z pierwszego miesiąca, aby upewnić się, że odpowiednie osoby nadal mają przypisane aktywne subskrypcje.

W przypadku rocznych subskrypcji w chmurze, anulowania zaczną obowiązywać pierwszego dnia miesiąca po 12 miesiącach od oryginalnego zakupu lub 12 miesięcy od ostatniej rocznej opłaty za odnowienie. Na przykład jeśli zakupiono Visual Studio Professional roczną subskrypcję w chmurze w dniu 3 stycznia 2018, zostanie ona uaktywniona do 1 lutego 2019, gdy zostanie automatycznie przedłużona przez kolejne lata. Jeśli anulujesz w dowolnym momencie między then i 1 lutego 2020, subskrypcja wygaśnie 1 lutego 2020. Nie ma rabatu do anulowania w ramach roku subskrypcji z rocznymi subskrypcjami chmury.

### <a name="q-what-kind-of-volume-discounts-are-available-for-visual-studio-subscriptions"></a>P: jakiego rodzaju rabaty na woluminy są dostępne dla subskrypcji programu Visual Studio?
Odp.: otrzymujesz 5% rabatu na szóste i wszystkie kolejne subskrypcje *w ramach każdego typu* subskrypcji:

* Visual Studio Professional miesięcznie
* Visual Studio Professional rocznie
* Visual Studio Enterprise miesięcznie
* Visual Studio Enterprise rocznie

Jeśli na przykład kupisz 6 Visual Studio Professional subskrypcje miesięczne i 5 Visual Studio Enterprise miesięcznych subskrypcji, będziesz mieć zwykłą cenę za 5 Professional, uzyskaj 5% rabat w szóstym Professional i płatność Zwykła cena za wszystkie 5 przedsiębiorstw opłaty.

Ponadto Rabat dotyczy opłat w danym miesięcznym okresie rozliczeniowym. Jeśli więc kupisz 5 Visual Studio Professional rocznych subskrypcji w ciągu miesiąca, a następnie kupisz 5 w następnym miesiącu, będziesz mieć zwykłą cenę za wszystkie 10 subskrypcji.

> [!NOTE]
> Firma Microsoft nie oferuje już Visual Studio Professional rocznych subskrypcji i Visual Studio Enterprise rocznych subskrypcji w ramach subskrypcji chmury. Istnieją zmiany w istniejących klientach i możliwość odnowienia, zwiększenia, zmniejszenia lub anulowania subskrypcji. Zachęcamy nowych klientów do przechodzenia do [https://visualstudio.microsoft.com/vs/pricing/](https://visualstudio.microsoft.com/vs/pricing/) , aby poznać różne opcje zakupu programu Visual Studio.

## <a name="other-questions"></a>Inne pytania
### <a name="q-can-i-use-the-monthly-azure-devtest-individual-credit-as-a-visual-studio-subscriber-to-buy-more-visual-studio-cloud-subscriptions"></a>P: Czy można użyć miesięcznych środków na korzystanie z platformy Azure DevTest jako subskrybenta programu Visual Studio, aby kupić więcej subskrypcji w chmurze programu Visual Studio?
Odp.: nie, nie możesz użyć miesięcznych środków na korzystanie z [platformy Azure DevTest](https://azure.microsoft.com/pricing/member-offers/credit-for-visual-studio-subscribers/) jako subskrybenta programu Visual Studio, aby uregulować zakupy Visual Studio Marketplace. Wszystkie zakupy w ramach subskrypcji programu Visual Studio w chmurze będą rozliczane na Twoją kartę kredytową.
Przed dokonaniem zakupów należy [usunąć limit wydatków](https://azure.microsoft.com/pricing/spending-limits/).

### <a name="q-whats-the-difference-between-annual-and-monthly-cloud-subscriptions"></a>P: Jaka jest różnica między rocznymi i miesięcznymi subskrypcjami w chmurze?
Odp.: miesięczne subskrypcje chmury obejmują program Visual Studio i użycie Azure DevOps Services i TFS. Roczna subskrypcja w chmurze jest taka, ale również obejmuje korzyści dla subskrybenta, w tym korzystanie z systemu Windows i innego oprogramowania firmy Microsoft w celu instalowania i testowania aplikacji, miesięcznych DevTest na korzystanie z platformy Azure na potrzeby eksperymentowania z platformą Azure usługi i opracowywanie i testowanie w chmurze, szkoleń, pomocy technicznej i wielu innych.
[Porównanie korzyści i cen subskrypcji chmury](https://visualstudio.microsoft.com/vs/pricing/)

### <a name="q-do-i-get-new-versions-of-visual-studio-if-i-buy-a-visual-studio-cloud-subscription"></a>P: Czy mogę uzyskać nowe wersje programu Visual Studio w przypadku zakupu subskrypcji programu Visual Studio w chmurze?
Odp.: tak. Po udostępnieniu nowych wersji można je pobrać i uruchomić. Ponadto można nadal uruchamiać wcześniejsze wersje.

### <a name="q-can-i-buy-visual-studio-cloud-subscriptions-from-my-software-reseller"></a>P: Czy mogę zakupić subskrypcje programu Visual Studio w chmurze od odsprzedawcy oprogramowania?
Odp.: tak, możesz, jeśli odsprzedawca uczestniczy w programie w programie Cloud Solution Provider (CSP). Po prostu zadawaj je.

## <a name="related-resources"></a>Powiązane zasoby
- [Portal administracyjny subskrypcji programu Visual Studio](https://manage.visualstudio.com/)
- [Obsługa subskrypcji programu Visual Studio](https://visualstudio.microsoft.com/vs/support/)
- [Kupowanie subskrypcji w chmurze programu Visual Studio dla dostawców CSP](vscloud-csp.md)

## <a name="next-steps"></a>Następne kroki
Kup teraz subskrypcje chmury
- [Visual Studio Professional miesięcznie](https://marketplace.visualstudio.com/items?itemName=ms.vs-professional-monthly)
- [Visual Studio Enterprise miesięcznie](https://marketplace.visualstudio.com/items?itemName=ms.vs-enterprise-monthly)