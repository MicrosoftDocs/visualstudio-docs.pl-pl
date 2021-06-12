---
title: Visual Studio subskrypcji chmury dla dostawców CSP
author: evanwindom
ms.author: v-evwin
manager: cabuschl
ms.assetid: d2ab13ed-ef79-4ef0-8736-eccd04bc6020
ms.date: 03/18/2021
ms.topic: conceptual
description: Informacje dla dostawców rozwiązań w chmurze dotyczące kupowania subskrypcji Visual Studio w chmurze dla klientów i zarządzania nimi.
ms.openlocfilehash: 09c905d113920a0bb55aed8851d3fb62c92a39bf
ms.sourcegitcommit: 4b2b6068846425f6964c1fd867370863fc4993ce
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/12/2021
ms.locfileid: "112042852"
---
# <a name="buy-and-manage-visual-studio-cloud-subscriptions-for-your-customers"></a>Kupowanie subskrypcji Visual Studio w chmurze i zarządzanie nimi dla klientów
Partnerzy w [programie Dostawca rozwiązań w chmurze (CSP)](https://partner.microsoft.com/cloud-solution-provider) mogą kupować subskrypcje Visual Studio Enterprise i Visual Studio Professional w chmurze dla swoich klientów.

[Porównanie opcji subskrypcji chmury](https://visualstudio.microsoft.com/vs/pricing)

> [!NOTE]
> Firma Microsoft nie oferuje już Visual Studio Professional w ramach subskrypcji w chmurze Visual Studio Enterprise roczne subskrypcje. Istniejące doświadczenia klientów nie zmienią się i nie będzie można odnawiać, zwiększać, zmniejszać ani anulować swoich subskrypcji. Zachęcamy nowych klientów do pójść do firmy , [https://visualstudio.microsoft.com/vs/pricing/](https://visualstudio.microsoft.com/vs/pricing/) aby poznać różne opcje zakupu Visual Studio.

## <a name="prerequisites"></a>Wymagania wstępne
Najpierw należy skonfigurować dzierżawę klienta w usłudze Partner Center i utworzyć subskrypcję platformy Azure dla tej dzierżawy.

[Dowiedz się więcej](/azure/devops/organizations/billing/csp/set-up-csp-customer)

## <a name="who-can-buy-visual-studio-subscriptions"></a>Kto może kupić Visual Studio subskrypcji?
Każda osoba [z dostępem właściciela lub współautora](https://na01.safelinks.protection.outlook.com/?url=https%3A%2F%2Fdocs.microsoft.com%2Fen-us%2Fvsts%2Forganizations%2Fbilling%2Fadd-backup-billing-managers%3Fview%3Dvsts%2520%2520sa&data=02%7C01%7C%7Cb9e717e8abff47b0cd7e08d618edd860%7C72f988bf86f141af91ab2d7cd011db47%7C1%7C0%7C636723807145220358&sdata=aIaamEXHhx94KCYVY%2FFibqFzNBEqKPntpql867xAMgU%3D&reserved=0) do subskrypcji platformy Azure może Visual Studio subskrypcji.

## <a name="how-to-buy"></a>Jak kupić

1. Zaloguj się do [witryny Microsoft Partner Center](https://partnercenter.microsoft.com).
0. Wybierz **pozycję Klienci** i wybierz klienta, dla których chcesz kupić.
0. Wybierz **pozycję Zarządzanie usługami.**
0. Wybierz **Visual Studio Marketplace**.
0. Upewnij się, że w prawym górnym rogu znajduje się nazwa klienta.
0. Wybierz **pozycję Subskrypcje.**
0. Wybierz opcję Enterprise lub Professional dla Visual Studio.
0. Wybierz **pozycję Kup**.
0. Wybierz subskrypcję platformy Azure, dla których chcesz dokonać zakupu.
0. Wprowadź liczbę użytkowników, których potrzebuje Klient.
0. Przejrzyj zamówienie i **potwierdź** je.

>[!NOTE]
> Te kroki należy wykonać za każdym razem, gdy Visual Studio subskrypcje jako CSP. Obecnie nie ma interfejsu API automatyzacji zakupów.

Po potwierdzeniu zakupu możesz  wybrać pozycję Zarządzaj, aby przypisać subskrypcje do użytkowników końcowych klienta.  Dostęp do portalu administracyjnego subskrypcji można również uzyskać z witryny Partner Center, wybierając **pozycję Zarządzanie usługami.**  W tym miejscu zapoznaj się z poniższymi krokami lub filmem wideo.

## <a name="how-to-manage-visual-studio-cloud-subscriptions-for-your-customer"></a>Jak zarządzać subskrypcjami Visual Studio w chmurze dla klienta

1. Zaloguj się do witryny [Microsoft Partner Center](https://partnercenter.microsoft.com).
0. Wybierz **pozycję** Klienci i nazwę klienta.
0. Wybierz **pozycję Zarządzanie usługami.**
0. Wybierz **pozycję Visual Studio subskrypcjami.**

Jeśli masz więcej niż jedną subskrypcję platformy Azure dla tego klienta, użyj menu rozwijanego, aby wybrać subskrypcję platformy Azure, w ramach której dokonano zakupów.  Podsumowanie **licencji zawiera** liczbę przypisanych subskrypcji oraz liczbę dostępnych subskrypcji dla poszczególnych subskrypcji Visual Studio w chmurze.  Podsumowanie umożliwia również zakup dodatkowych subskrypcji lub zmniejszenie ich liczby.

Wybierz **pozycję Dodaj,** aby przypisać subskrypcję do nowego użytkownika.  Liczba wyświetlanych aktualizacji jest aktualizowana, a użytkownik końcowy otrzymuje powiadomienie e-mail. Użytkownik końcowy może następnie zalogować się przy użyciu podanego adresu e-mail, aby aktywować swoją Visual Studio subskrypcji w [portalu Visual Studio subskrybenta.](https://my.visualstudio.com?wt.mc_id=o~msft~docs)

Aby ponownie Visual Studio subskrypcji do innego użytkownika, możesz usunąć bieżącego subskrybenta i dodać nowego subskrybenta.

Jeśli subskrybent nie aktywował subskrypcji Visual Studio, może to być spowodowane tym, że pominięto wiadomość e-mail z zaproszeniem.  Możesz również poprosić o ponowne wysyłanie zaproszenia do aktywacji do użytkownika z poziomu Visual Studio administracyjnego.

## <a name="view-visual-studio-pricing-for-csp-partners"></a>Wyświetlanie Visual Studio cen dla partnerów CSP
Aby wyświetlić Visual Studio dla partnerów CSP, zaloguj się do Partner Center [.](https://partnercenter.microsoft.com)  Wybierz **pozycję Ceny i oferty** w lewym okienku nav.  Wybierz plik cennika bieżącego miesiąca w **obszarze usług opartych** na użyciu w prawym górnym rogu. Po pobraniu arkusza kalkulacyjnego programu Excel przejdź do arkusza **cennika** platformy Azure i przefiltruj kolumnę **Kategoria** miernika, **aby Visual Studio**.

Oto jak interpretować to, co widzisz w tym arkuszu kalkulacyjnym:

| Kategoria miernika    |   Nazwa                 |  Lekcji                                |           Co to jest                          |
|-------------------|------------------------|---------------------------------------|-------------------------------------------------|
| Visual Studio     | Przedsiębiorstwa             |  Subskrypcja                         | Visual Studio Enterprise subskrypcji miesięcznej   |
| Visual Studio     | Professional Edition           |  Subskrypcja                         | Visual Studio Professional subskrypcji miesięcznej |

Oferujemy 5% rabatu na 6. kupowaną jednostkę (dla danego klienta) każdego miesiąca każdej Visual Studio subskrypcji. Dlatego zobaczysz dwa wiersze dla każdej opcji subskrypcji. Jeden wiersz zawiera wartość "Wartość minimalna" o wartości 0, którą należy interpretować jako cenę podstawową dla jednostek od 1 do 5. Drugi wiersz zawiera wartość "Wartość minimalna" o wartości 5, więc jest to 5% rabatu, która ma zastosowanie do jednostek 6 i ych.

## <a name="frequently-asked-questions"></a>Często zadawane pytania
### <a name="q-how-are-monthly-cloud-subscription-charges-processed"></a>Pytanie: Jak są **przetwarzane miesięczne opłaty** za subskrypcję chmury?
A: Przy pierwszym zakupie naliczamy proporcjonalną ilość, aby pokrywać pozostałe dni w bieżącym miesiącu. Jeśli na przykład zakup 10 Visual Studio Professional miesięcznych subskrypcji w chmurze został dokonany 15 kwietnia, naliczamy 5 jednostek, ponieważ w ciągu 30-dniowego miesiąca pozostało 15 dni, czyli 50%, a jednostki są naliczane według wartości 50%. Od pierwszego maja i każdego miesiąca później do momentu anulowania zostanie rozliowanych 10 pełnych jednostek.

W przypadku późniejszego zwiększenia ilości płatnej zwiększamy również liczbę jednostek w celu pokrycia pozostałych dni w bieżącym miesiącu. Jeśli więc zakupiono jeszcze 1 Visual Studio Professional miesięcznej subskrypcji chmury 10 maja, opłaty będą naliczane mniej więcej za 0,677 jednostek (21 dni w ciągu 31-dniowego miesiąca maja).

### <a name="q-how-do-cancellations-work"></a>Pytanie: Jak działają anulowania?
Odpowiedzi: Anulując subskrypcję Visual Studio w chmurze, anulujesz automatyczne odnawianie. Subskrypcja pozostanie ważna do zwykłej daty odnowienia, a potem po prostu wygaśnie. Gdy subskrypcja wygaśnie, subskrybent programu Visual Studio nie będzie już mógł korzystać z programu Visual Studio i nie będzie miał dostępu do żadnych korzyści związanych z subskrypcją.

Subskrypcje miesięczne w chmurze zostaną anulowane pierwszego dnia kolejnego miesiąca. Jeśli anulujesz tylko niektóre miesięczne subskrypcje chmury klienta, pamiętaj o usunięciu użytkowników w pierwszym dniu następnego miesiąca, aby upewnić się, że właściwe osoby nadal mają przypisane aktywne subskrypcje.

Roczne subskrypcje w chmurze zostaną anulowane pierwszego dnia miesiąca przypadającego po upływie 12 miesięcy od daty zakupu lub 12 miesięcy od ostatniej rocznej opłaty za odnowienie. Jeśli na przykład zakupiono roczną subskrypcję Visual Studio Enterprise w chmurze w dniu 3 stycznia 2018 r., pozostanie ona aktywna do 1 lutego 2019 r., gdy zostanie automatycznie odnowiona na kolejny rok. Jeśli anulujesz ją pomiędzy tą datą a 1 lutego 2020 roku, ta subskrypcja wygaśnie 1 lutego 2020 r. Nie ma rabatu za anulowanie rocznych subskrypcji w chmurze przed upływem roku.

### <a name="q-what-kind-of-volume-discounts-are-available-for-visual-studio-subscriptions"></a>Pytanie: Jakiego rodzaju rabaty na woluminy są dostępne dla Visual Studio subskrypcji?
A: Otrzymasz 5% rabatu na 6. i wszystkie kolejne subskrypcje *w ramach każdego typu* subskrypcji:
- Visual Studio Professional miesięczne
- Visual Studio Enterprise miesięcznie

Jeśli na przykład zakupisz 6 subskrypcji Visual Studio Professional miesięcznych i 5 subskrypcji miesięcznych usługi Visual Studio Enterprise, zapłacisz zwykłą cenę za pięć subskrypcji Professional, otrzymasz 5% rabatu na 6. profesjonalną subskrypcję i zapłacisz regularną cenę za wszystkie pięć subskrypcji Enterprise.

Ponadto rabat dotyczy tylko opłat w danym miesięcznym okresie rozliczeniowym. Jeśli więc kupisz 5 Visual Studio Professional roczne subskrypcje w jednym miesiącu, a następnie kupisz 5 kolejnych subskrypcji w następnym miesiącu, zapłacisz regularną cenę za wszystkie dziesięć subskrypcji.

Te rabaty są odzwierciedlone w danych cenowych w Partner Center [.](https://partnercenter.microsoft.com)

### <a name="q-are-there-renewal-discounts"></a>Pytanie: Czy istnieją rabaty na odnowienie?
A: Nie, ceny za subskrypcje Visual Studio są płaskie. Ta sama cena jest oferowana dla nowych subskrypcji i ciągłych subskrypcji.

### <a name="q-are-there-azure-devtest-pricing-options-for-csps"></a>Pytanie: Czy istnieją opcje cenowe tworzenia i testowania platformy Azure dla CSP?
A: Obecnie nie. Klienci mogą korzystać z cennika tworzenia i testowania platformy [Azure,](https://azure.microsoft.com/pricing/dev-test/)ale nie mamy niczego specjalnie dla CSP.

## <a name="resources"></a>Zasoby
- Aby uzyskać pomoc w zakresie sprzedaży, subskrypcji, kont i rozliczeń dla subskrypcji Visual Studio, zobacz Visual Studio Subscriptions support (Pomoc techniczna dotycząca subskrypcji [platformy Azure).](https://aka.ms/vssubscriberhelp)

## <a name="see-also"></a>Zobacz też
- [Visual Studio dokumentacji](/visualstudio/)
- [Azure DevOps documentation (Dokumentacja usługi Azure DevOps)](/azure/devops/)
- [Dokumentacja platformy Azure](/azure/)
- [Microsoft 365 dokumentacji](/microsoft-365/)

## <a name="next-steps"></a>Następne kroki
Zobacz często zadawane [pytania dotyczące rozliczeń w chmurze,](vscloud-billing-faq.yml) aby uzyskać odpowiedzi na często zadawane pytania dotyczące rozliczeń.