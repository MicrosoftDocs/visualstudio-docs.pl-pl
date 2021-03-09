---
title: Często zadawane pytania dotyczące subskrypcji w chmurze Visual Studio | Microsoft Docs
author: evanwindom
ms.author: v-evwin
manager: cabuschl
ms.assetid: 21e0471d-ad59-4d21-9c6f-13f7147569af
ms.date: 03/05/2021
ms.topic: conceptual
description: Pytania dotyczące rozliczeń dla subskrypcji chmury.
ms.openlocfilehash: d3c370eecab49de5f4ea5001e6052c18ff83e00b
ms.sourcegitcommit: 35fa920126b34c8d3839da53e3a4c2c6f509968f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/09/2021
ms.locfileid: "102473416"
---
# <a name="visual-studio-cloud-subscriptions-billing-faq"></a>Subskrypcje dotyczące rozliczeń w ramach subskrypcji programu Visual Studio Cloud
[PORÓWNAJ korzyści z subskrypcji chmury i ceny](https://visualstudio.microsoft.com/vs/pricing/) , aby poznać zalety każdej subskrypcji programu Visual Studio, z porównaniami między subskrypcjami w chmurze i standardami programu Visual Studio, szczegółowymi dotyczącymi korzyści dla subskrybentów i innymi.

## <a name="general-purchasing-questions"></a>Ogólne pytania dotyczące zakupu
### <a name="q-can-i-buy-visual-studio-cloud-subscriptions-using-a-purchase-order"></a>P: Czy mogę kupić subskrypcje programu Visual Studio w chmurze przy użyciu zamówienia zakupu?
Odpowiedź: nie. Wszystkie subskrypcje programu Visual Studio w chmurze muszą zostać zakupione przy użyciu subskrypcji platformy Azure. (Pomyśl, że jest to konto rozliczeniowe platformy Azure).

### <a name="q-what-types-of-azure-subscriptions-can-be-used-to-buy-visual-studio-cloud-subscriptions"></a>P: jakich typów subskrypcji platformy Azure można używać do kupowania subskrypcji w chmurze programu Visual Studio?
Odp.: można używać większości subskrypcji platformy Azure — obsługujemy subskrypcje platformy Azure połączone z [Enterprise Agreement (EA)](https://azure.microsoft.com/pricing/enterprise-agreement/), subskrypcje platformy Azure skonfigurowane przez dostawców rozwiązań w chmurze (CSP), subskrypcje platformy Azure skonfigurowane w ramach odsprzedawcaów licencji Open firmy Microsoft oraz subskrypcje platformy Azure z płatność zgodnie z rzeczywistym użyciem.

Nie można używać niektórych typów subskrypcji platformy Azure, w tym [bezpłatnej wersji próbnej platformy Azure](https://azure.microsoft.com/pricing/free-trial/) i subskrypcji oferowanych w ramach subskrypcji programu Visual Studio.

### <a name="q-am-i-required-to-buy-other-azure-services"></a>P: Czy muszę kupić inne usługi platformy Azure?
Odp.: nie. Jeśli chcesz kupić subskrypcje programu Visual Studio w chmurze tylko za pośrednictwem platformy Azure, możesz to zrobić.

### <a name="q-where-can-i-view-my-billing-and-usage-data"></a>P: gdzie można wyświetlić dane dotyczące rozliczeń i użycia?
Odp.: Uzyskaj informacje na temat [wyświetlania faktury i użycia](https://docs.microsoft.com/azure/cost-management-billing/manage/download-azure-invoice-daily-usage-date).

## <a name="enterprise-agreement-ea-customers"></a>Klienci korzystający z Enterprise Agreement (EA)
### <a name="q-can-i-use-an-enterprise-agreement-to-buy-visual-studio-cloud-subscriptions"></a>P: Czy można używać Enterprise Agreement do kupowania subskrypcji programu Visual Studio w chmurze?
Odp.: tak, możesz. Musisz być współautorem lub wyższą rolą dla subskrypcji platformy Azure, która została utworzona dla umowy EA. Upewnij się, że zakupy dla subskrypcji programu Visual Studio Cloud są wprowadzane bezpośrednio w Visual Studio Marketplace. Nie można kupić subskrypcji programu Visual Studio w chmurze przy użyciu zamówienia zakupu.

### <a name="q-how-can-i-tell-whether-i-have-the-necessary-privileges-to-buy-services-in-the-visual-studio-marketplace-through-my-organizations-enterprise-agreement"></a>P: Jak mogę sprawdzić, czy mam wymagane uprawnienia do kupowania usług w Visual Studio Marketplace za pomocą Enterprise Agreement organizacji?
Odp.: najprostszym podejściem do ustalenia, czy masz odpowiednie uprawnienia, jest wybranie przycisku **Kup** dla usługi oferowanej w Visual Studio Marketplace.
Musisz wybrać subskrypcję platformy Azure (czyli konto rozliczeniowe) z wyświetlonej listy subskrypcji platformy Azure, które są obecnie połączone z logowaniem.
Ponieważ nazwa usługi Azure Subscription jest domyślna dla typu konta rozliczeniowego ("płatność zgodnie z rzeczywistym użyciem", "Enterprise Agreement" itp.), często jest jasne, jeśli subskrypcja platformy Azure jest częścią Enterprise Agreement.

Innym rozwiązaniem jest próba odwiedzenia [Enterprise Portal platformy Azure](https://ea.azure.com).  Jeśli możesz się z nią skontaktować, masz już rolę administratora przedsiębiorstwa lub właściciela konta. Tylko właściciele konta mogą konfigurować nowe konta rozliczeń platformy Azure w Enterprise Agreement. Jeśli nie możesz uzyskać dostępu do usługi Azure Enterprise Portal, skontaktuj się z pomocą techniczną w organizacji, aby dowiedzieć się, kto jest administratorem przedsiębiorstwa, i poproś o dodanie Cię jako właściciela konta w ramach usługi Azure Enterprise Portal.  Jeśli nie możesz znaleźć tej osoby, możesz [przesłać bilet pomocy technicznej](https://support.microsoft.com/supportrequestform/cf791efa-485b-95a3-6fad-3daf9cd4027c) i zażądać informacji kontaktowych.  W przypadku biletu pomocy technicznej potrzebna jest nazwa organizacji i numer rejestracji Enterprise Agreement.

### <a name="q-can-i-use-the-azure-monetary-commitment-funds-from-my-enterprise-agreement-to-buy-visual-studio-cloud-subscriptions"></a>P: Czy mogę użyć funduszy zobowiązania pieniężnego platformy Azure z mojej Enterprise Agreement, aby kupić subskrypcje programu Visual Studio w chmurze?
Odp.: nie, te przedpłacone środki nie kwalifikują się do zakupu subskrypcji programu Visual Studio w chmurze. Po wybraniu subskrypcji platformy Azure, która została utworzona dla umowy EA w celu zakupienia subskrypcji w chmurze programu Visual Studio, opłaty będą naliczane po następnej fakturze "nadwyżkowe". Zwykle odbywa się to co miesiąc, ale ze względu na reguły historyczne dla niektórych klientów z umowami EA, faktura nadwyżki nie może zostać wystawiona przez kilka miesięcy. Zapoznaj się z specjalistą ds. licencjonowania w ramach umowy EA, jeśli chcesz wiedzieć, jaka ilość dodatkowych zakupów (zakupów, które nie kwalifikują się do funduszy związanych z zobowiązaniami pieniężnymi platformy Azure), spowoduje wyzwolenie faktury nadwyżkowej.

## <a name="how-charges-are-processed"></a>Jak są przetwarzane opłaty
### <a name="q-how-are-monthly-cloud-subscription-charges-processed"></a>P: w jaki sposób są naliczane **miesięczne** opłaty za subskrypcję w chmurze?
Odp.: przy pierwszym zakupie opłata jest naliczana proporcjonalnie do pozostałej liczby dni w bieżącym miesiącu. Na przykład w przypadku zakupu 10 Visual Studio Professional comiesięcznych subskrypcji w chmurze w dniu 15 kwietnia firma Microsoft będzie liczyć 5 jednostek, ponieważ 50% miesiąca pozostanie (15 dni z 30-dniowym miesiącem).
W pierwszej kolejności i w każdym miesiącu, po upływie którego zostanie anulowana, zostanie naliczona pełna 10 jednostek.

Po zwiększeniu ilości płatnej później Oceńmy również zwiększenie liczby jednostek, aby pokryć pozostałe dni w bieżącym miesiącu. Jeśli więc zakupiono 1 więcej Visual Studio Professional comiesięczną subskrypcję chmury w dniu 10 maja, będziemy rozliczać około 0,677 jednostek (21 dni pozostałej w dniu 31-dniowego miesiąca).

### <a name="q-how-are-annual-cloud-subscription-charges-processed"></a>P: jak są przetwarzane **roczne** opłaty za subskrypcję w chmurze?
Odp.: przy każdym zakupie opłaty są naliczane natychmiast po zakupie. Opłaty nie są naliczane w ciągu roku i nie ma żadnej klasyfikacji. Jeśli kupisz roczną subskrypcję chmury w różnym czasie w roku, będziesz mieć subskrypcje odnawiane w różnych miesiącach. Firma Microsoft nie udostępnia żadnych rocznych subskrypcji w chmurze coterminous, które są wspólne w ramach zakupu w ramach umowy licencjonowania zbiorowego.

### <a name="q-how-do-cancellations-work"></a>P: jak działają anulowania?
Odp.: po anulowaniu subskrypcji programu Visual Studio w chmurze anulujesz automatyczne odnawianie. Subskrypcja pozostanie ważna do zwykłej daty odnowienia, a potem po prostu wygaśnie.
Gdy subskrypcja wygaśnie, subskrybent programu Visual Studio nie będzie już mógł korzystać z programu Visual Studio i nie będzie miał dostępu do żadnych korzyści związanych z subskrypcją.

Subskrypcje miesięczne w chmurze zostaną anulowane pierwszego dnia kolejnego miesiąca. Jeśli chcesz anulować tylko część miesięcznych subskrypcji w chmurze, usuń użytkowników pierwszego dnia kolejnego miesiąca, aby mieć pewność, że właściwe osoby nadal będą miały przypisane aktywne subskrypcje.

Roczne subskrypcje w chmurze zostaną anulowane pierwszego dnia miesiąca przypadającego po upływie 12 miesięcy od daty zakupu lub 12 miesięcy od ostatniej rocznej opłaty za odnowienie. Jeśli na przykład kupiono roczną subskrypcję programu Visual Studio Professional w chmurze 3 stycznia 2018 roku, będzie ona aktywna do 1 lutego 2019 roku i wtedy zostanie automatycznie odnowiona na kolejny rok. Jeśli anulujesz ją pomiędzy tą datą a 1 lutego 2020 roku, ta subskrypcja wygaśnie 1 lutego 2020 r. Nie ma rabatu za anulowanie rocznych subskrypcji w chmurze przed upływem roku.

### <a name="q-what-kind-of-volume-discounts-are-available-for-visual-studio-subscriptions"></a>P: jakiego rodzaju rabaty na woluminy są dostępne dla subskrypcji programu Visual Studio?
Odp.: otrzymujesz 5% rabatu na szóste i wszystkie kolejne subskrypcje *w ramach każdego typu* subskrypcji:

* Visual Studio Professional miesięcznie
* Visual Studio Professional rocznie
* Visual Studio Enterprise miesięcznie
* Visual Studio Enterprise rocznie

Jeśli na przykład kupisz 6 Visual Studio Professional subskrypcje miesięczne i 5 Visual Studio Enterprise miesięcznych subskrypcji, będziesz mieć zwykłą cenę w dniu 5 Professional, uzyskaj rabat w wysokości 5% w przypadku szóstego specjalisty i płatność Zwykła cena wszystkich 5 subskrypcji przedsiębiorstwa.

Ponadto Rabat dotyczy opłat w danym miesięcznym okresie rozliczeniowym. Jeśli więc kupisz 5 Visual Studio Professional rocznych subskrypcji w ciągu miesiąca, a następnie kupisz 5 w następnym miesiącu, będziesz mieć zwykłą cenę za wszystkie 10 subskrypcji.

> [!NOTE]
> Firma Microsoft nie oferuje już Visual Studio Professional rocznych subskrypcji i Visual Studio Enterprise rocznych subskrypcji w ramach subskrypcji chmury. Istnieją zmiany w istniejących klientach i możliwość odnowienia, zwiększenia, zmniejszenia lub anulowania subskrypcji. Zachęcamy nowych klientów do [https://visualstudio.microsoft.com/vs/pricing/](https://visualstudio.microsoft.com/vs/pricing/) przeglądania różnych opcji zakupu programu Visual Studio.

## <a name="other-questions"></a>Inne pytania
### <a name="q-can-i-use-the-monthly-azure-devtest-individual-credit-as-a-visual-studio-subscriber-to-buy-more-visual-studio-cloud-subscriptions"></a>P: Czy można użyć miesięcznych środków na korzystanie z platformy Azure DevTest jako subskrybenta programu Visual Studio, aby kupić więcej subskrypcji w chmurze programu Visual Studio?
Odp.: nie, nie możesz użyć miesięcznych środków na korzystanie z [platformy Azure DevTest](https://azure.microsoft.com/pricing/member-offers/credit-for-visual-studio-subscribers/) jako subskrybenta programu Visual Studio, aby uregulować zakupy Visual Studio Marketplace. Wszystkie zakupy w ramach subskrypcji programu Visual Studio w chmurze będą rozliczane na Twoją kartę kredytową.
Przed dokonaniem zakupów należy [usunąć limit wydatków](https://azure.microsoft.com/pricing/spending-limits/).

### <a name="q-whats-the-difference-between-annual-and-monthly-cloud-subscriptions"></a>P: Jaka jest różnica między rocznymi i miesięcznymi subskrypcjami w chmurze?
Odp.: miesięczne subskrypcje chmury obejmują program Visual Studio i użycie Azure DevOps Services i TFS. Roczne subskrypcje chmurowe mają takie rozwiązanie, ale również obejmują korzyści dla subskrybentów, w tym korzystanie z systemu Windows i innych programów firmy Microsoft w celu instalowania i testowania aplikacji, miesięcznych DevTest na korzystanie z platformy Azure na potrzeby eksperymentowania z usługami platformy Azure oraz opracowywania i testowania w chmurze, szkoleń, pomocy technicznej i wielu innych.
[Porównanie korzyści i cen subskrypcji chmury](https://visualstudio.microsoft.com/vs/pricing/)

### <a name="q-do-i-get-new-versions-of-visual-studio-if-i-buy-a-visual-studio-cloud-subscription"></a>P: Czy mogę uzyskać nowe wersje programu Visual Studio w przypadku zakupu subskrypcji programu Visual Studio w chmurze?
Odp.: tak. Po udostępnieniu nowych wersji można je pobrać i uruchomić. Ponadto można nadal uruchamiać wcześniejsze wersje.

### <a name="q-can-i-buy-visual-studio-cloud-subscriptions-from-my-software-reseller"></a>P: Czy mogę zakupić subskrypcje programu Visual Studio w chmurze od odsprzedawcy oprogramowania?
Odp.: tak, możesz, jeśli odsprzedawca uczestniczy w programie w programie Cloud Solution Provider (CSP). Po prostu zadawaj je.

### <a name="q-where-can-i-find-information-about-azure-invoices"></a>P: gdzie można znaleźć informacje na temat faktur platformy Azure?
Odp.: Zapoznaj się z artykułem [Omówienie usługi Azure Invoice](https://docs.microsoft.com/azure/cost-management-billing/understand/understand-invoice) w [dokumentacji platformy Azure](/azure/).

## <a name="related-resources"></a>Powiązane zasoby
- [Portal administratora subskrypcji programu Visual Studio](https://manage.visualstudio.com/)
- [Kupowanie subskrypcji w chmurze programu Visual Studio dla dostawców CSP](vscloud-csp.md)
- Aby uzyskać pomoc dotyczącą sprzedaży, subskrypcji, kont i rozliczeń dla subskrypcji programu Visual Studio, zobacz [Obsługa subskrypcji](https://aka.ms/vssubscriberhelp)programu Visual Studio.

## <a name="see-also"></a>Zobacz też
- [Dokumentacja programu Visual Studio](/visualstudio/)
- [Azure DevOps documentation (Dokumentacja usługi Azure DevOps)](/azure/devops/)
- [Dokumentacja platformy Azure](/azure/)
- [Dokumentacja Microsoft 365](/microsoft-365/)

## <a name="next-steps"></a>Następne kroki
Kup teraz subskrypcje chmury
- [Visual Studio Professional miesięcznie](https://marketplace.visualstudio.com/items?itemName=ms.vs-professional-monthly)
- [Visual Studio Enterprise miesięcznie](https://marketplace.visualstudio.com/items?itemName=ms.vs-enterprise-monthly)