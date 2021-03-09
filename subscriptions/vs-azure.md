---
title: Microsoft Azure korzyść w subskrypcjach programu Visual Studio | Microsoft Docs
author: evanwindom
ms.author: v-evwin
manager: cabuschl
ms.assetid: 872c5746-5357-4764-949b-aa525a0adf1a
ms.date: 02/19/2021
ms.topic: how-to
description: Dowiedz się, jak aktywować usługę Azure DevTest z korzyściami z tytułu skorzystania z subskrypcji programu Visual Studio.
ms.openlocfilehash: 0834020113ac4a383abe551ace0ae2e3181e0650
ms.sourcegitcommit: 35fa920126b34c8d3839da53e3a4c2c6f509968f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/09/2021
ms.locfileid: "102473377"
---
# <a name="use-microsoft-azure-in-visual-studio-subscriptions"></a>Używanie Microsoft Azure w subskrypcjach programu Visual Studio
Jako subskrybent programu Visual Studio możesz używać Microsoft Azure bez dodatkowych opłat.  W przypadku comiesięcznych środków na korzystanie z [platformy Azure DevTest](https://azure.microsoft.com/pricing/member-offers/msdn-benefits-details/), platforma Azure jest osobistą piaskownicą na potrzeby tworzenia i testowania.  Możesz udostępniać maszyny wirtualne, usługi w chmurze i inne zasoby platformy Azure.  Kwoty kredytowe różnią się w zależności od poziomu subskrypcji.

## <a name="activation-steps"></a>Kroki aktywacji
1. Zaloguj się do witryny [https://my.visualstudio.com/benefits](https://my.visualstudio.com/benefits?wt.mc_id=o~msft~docs).

2. Znajdź kafelek platformy Azure w sekcji Tools na stronie korzyści i wybierz pozycję **Aktywuj** link w dolnej części kafelka korzyści.
   > [!div class="mx-imgBorder"]
   > ![Kafelek platformy Azure](_img/vs-azure/vs-azure-tile.png "Kliknij przycisk "Aktywuj" na kafelku platformy Azure, aby rozpocząć pracę.")

3. Jeśli nie masz istniejącej subskrypcji platformy Azure, zostanie wyświetlony monit o wypełnienie wymaganych informacji w celu utworzenia subskrypcji platformy Azure.  Pierwszym krokiem jest podanie informacji osobistych, a następnie wybranie **przycisku Dalej**.
   > [!div class="mx-imgBorder"]
   > ![Rejestracja na platformie Azure](_img/vs-azure/vs-azure-about-you.png "Dodaj swoje osobiste informacje kontaktowe do subskrypcji platformy Azure.")

4. Następnie musisz zweryfikować swoją tożsamość przy użyciu prostego kodu weryfikacyjnego. Podaj numer telefonu, a następnie wybierz, czy chcesz otrzymać kod za pomocą tekstu, czy telefonu.  Wprowadź otrzymany kod, a następnie wybierz pozycję **Weryfikuj kod**.   
   > [!div class="mx-imgBorder"]
   > ![Trwa przygotowywanie platformy Azure](_img/vs-azure/vs-azure-identity.png "Poproś o kod weryfikacyjny, a następnie wprowadź go, aby przejść.")

5. W przypadku kroku końcowego zaznacz pole wyboru, aby zaakceptować warunki, a następnie wybierz pozycję **Utwórz konto**.  To wszystko!
   > [!div class="mx-imgBorder"]
   > ![Rejestracja na platformie Azure](_img/vs-azure/vs-azure-agreement.png "Kliknij przycisk Utwórz konto, aby zakończyć tworzenie subskrypcji platformy Azure.")

0. Zostanie załadowana centrum szybkiego startu pulpitu nawigacyjnego platformy Azure.  
   > [!div class="mx-imgBorder"]
   > ![Pulpit nawigacyjny platformy Azure](_img/vs-azure/vs-azure-quick-start.png "Po utworzeniu subskrypcji platformy Azure nastąpi przekierowanie do Azure Portal.") 

0. Tworzenie zakładek [Azure Portal](https://portal.azure.com) w celu łatwego dostępu w przyszłości.

## <a name="maintain-a-subscription-to-use-monthly-credits"></a>Obsługuj subskrypcję do korzystania z kredytów miesięcznych
Jeśli Twoja subskrypcja programu Visual Studio wygasła lub została usunięta, wszystkie korzyści z subskrypcji, w tym miesięczne środki na korzystanie z platformy Azure dotyczące tworzenia i testowania, nie będą już dostępne. Aby nadal korzystać z platformy Azure z miesięcznymi środkami, musisz odnowić subskrypcję, zakupić nową subskrypcję lub przenieść korzyść platformy Azure do aktywnej subskrypcji, która obejmuje środki na korzystanie z platformy Azure na potrzeby tworzenia i testowania.  

> [!IMPORTANT]
> Aby można było wyłączyć bieżącą subskrypcję platformy Azure lub utracić dostęp do danych, musisz przenieść swoje zasoby do innej subskrypcji platformy Azure.  

Istnieje kilka sposobów na kontynuowanie korzystania z miesięcznych środków na korzystanie z platformy Azure.  Aby zapisać zasoby platformy Azure, musisz [przenieść swoje zasoby](/azure/azure-resource-manager/management/move-resource-group-and-subscription) do innej subskrypcji platformy Azure, niezależnie od akcji wybranej poniżej. 

- **Jeśli masz bezpośrednio zakupić swoją subskrypcję programu Visual Studio**, Kup nową subskrypcję lub Odnów subskrypcję za pomocą Microsoft Store.  
    - [Visual Studio Enterprise](https://www.microsoft.com/p/visual-studio-enterprise-subscription/dg7gmgf0dst4?activetab=pivot%3aoverviewtab)
    - [Visual Studio Professional](https://www.microsoft.com/p/visual-studio-professional-subscription/dg7gmgf0dst3?activetab=pivot%3aoverviewtab)
    - [Visual Studio Test Professional](https://www.microsoft.com/p/visual-studio-test-professional-subscription/dg7gmgf0dst6?activetab=pivot%3aoverviewtab)
- **Jeśli ktoś w organizacji kupuje subskrypcje Twojej organizacji**, [skontaktuj się z administratorem subskrypcji programu Visual Studio](./contact-my-admin.md) i zażądaj subskrypcji, która zapewnia miesięczny kredyt, którego potrzebujesz.  
- **Jeśli masz inną aktywną subskrypcję programu Visual Studio** na tym samym poziomie subskrypcji, która jest skojarzona z innym konto Microsoft, możesz przenieść korzyść platformy Azure do innej aktywnej subskrypcji programu Visual Studio, [dodając alternatywne konto](./manage-vs-subscriptions.md#managing-my-profile) w [portalu subskrypcji](https://my.visualstudio.com/subscriptions)programu Visual Studio.  

Skorzystaj z poniższej tabeli kwalifikowania, aby określić, ile kredytów jest dołączonych do poszczególnych typów subskrypcji.  


## <a name="convert-your-azure-subscription-to-pay-as-you-go"></a>Konwertuj subskrypcję platformy Azure na płatność zgodnie z rzeczywistym użyciem

Jeśli nie potrzebujesz już subskrypcji lub kredytu programu Visual Studio, ale chcesz nadal korzystać z zasobów platformy Azure, [Przenieś swoje zasoby](/azure/azure-resource-manager/management/move-resource-group-and-subscription) do innej subskrypcji platformy Azure lub Przekształć subskrypcję platformy Azure w Cennik z opcją płatność zgodnie z rzeczywistym użyciem, [usuwając limit wydatków](/azure/cost-management-billing/manage/spending-limit#remove-the-spending-limit-in-azure-portal). 

Jeśli nie wykonasz żadnej z tych akcji, Twoja subskrypcja platformy Azure zostanie wyłączona i usunięta po upływie 30 dni od otrzymania powiadomienia e-mail.  

## <a name="have-a-question"></a>Masz pytanie?
Jeśli masz pytania dotyczące transferu zasobów, usuwania limitów wydatków lub innych tematów dotyczących platformy Azure, możesz [przesłać żądanie pomocy technicznej platformy Azure](https://portal.azure.com/#blade/Microsoft_Azure_Support/HelpAndSupportBlade/overview) w Azure Portal. 

## <a name="eligibility"></a>Kryteria
|                 Poziom subskrypcji/program                 |           Korzyść           |                         Odnawialny?                          |
|--------------------------------------------------------------|-----------------------------|-------------------------------------------------------------|
|              Visual Studio Enterprise Standard               |     $150 — środki miesięczne     |                             Tak                             |
|              Visual Studio Enterprise subskrypcję z usługą GitHub Enterprise               |     $150 — środki miesięczne     |                             Tak                             |
|               Visual Studio Enterprise miesięcznie               |        Niedostępne        |                                                             |
|             Visual Studio Professional Standard              |     $50 — środki miesięczne      |                             Tak
|              Visual Studio Professional subskrypcję z usługą GitHub Enterprise              |     $50 — środki miesięczne     |                             Tak                             |
|              Visual Studio Professional miesięcznie              |        Niedostępne        |                                                             |
|                    Visual Studio Test Pro                    |     $50 — środki miesięczne      |                             Tak                             |
|                        Platformy MSDN                        |     $100 — środki miesięczne     |                             Tak                             |
|               Visual Studio Enterprise — NFR\*               |     $150 — środki miesięczne     |                             Tak                             |
|                Visual Studio Enterprise — równoważnik                |     $150 — środki miesięczne     |                             Tak                             |
|     Visual Studio Enterprise — Microsoft Partner Network     |     $150 — środki miesięczne     |                             Tak                             |
|    Visual Studio Professional — Microsoft Partner Network    |        Niedostępne        |                                                             |
|        Visual Studio Enterprise — Wyobraź sobie (standard)         |        Niedostępne        |                                                             |
|         Visual Studio Enterprise — Wyobraź sobie (Premium)         |        Niedostępne        |                                                             |
|             Visual Studio Enterprise — BizSpark              |     $150 — środki miesięczne     |                             Tak                             |
|      Visual Studio Enterprise — MCT oprogramowania & Services      |     $100 — środki miesięczne     |                             Tak                             |
| Visual Studio Enterprise — deweloper usług & oprogramowania MCT |     $150 — środki miesięczne     |                             Tak                             |

* Nie obejmuje odsprzedaży (NFR), najbardziej cennych profesjonalistów (MVP), regionalnej dyrektora (RD), Visual Studio Industry partner (VSIP)

> [!NOTE]
> Firma Microsoft nie oferuje już Visual Studio Professional rocznych subskrypcji i Visual Studio Enterprise rocznych subskrypcji w ramach subskrypcji chmury. Istnieją zmiany w istniejących klientach i możliwość odnowienia, zwiększenia, zmniejszenia lub anulowania subskrypcji. Zachęcamy nowych klientów do [https://visualstudio.microsoft.com/vs/pricing/](https://visualstudio.microsoft.com/vs/pricing/) przeglądania różnych opcji zakupu programu Visual Studio.

Nie masz pewności, której subskrypcji używasz?  Połącz się z, [https://my.visualstudio.com/subscriptions](https://my.visualstudio.com/subscriptions?wt.mc_id=o~msft~docs) Aby wyświetlić wszystkie subskrypcje przypisane do Twojego adresu e-mail. Jeśli nie widzisz wszystkich subskrypcji, być może masz co najmniej jeden przypisany do innego adresu e-mail.  Musisz zalogować się przy użyciu tego adresu e-mail, aby zobaczyć te subskrypcje.

## <a name="frequently-asked-questions"></a>Często zadawane pytania
### <a name="q-how-do-i-submit-a-technical-support-incident-from-within-the-azure-portal"></a>P: Jak mogę przesyłania zdarzenia pomocy technicznej z poziomu Azure Portal?
Odp.: przesyłanie incydentu pomocy technicznej z Azure Portal jest procesem dwuetapowym.
1. Aktywuj korzyść pomocy technicznej i uzyskaj identyfikator dostępu do identyfikatora kontraktu.
2. Połącz umowę pomocy technicznej z subskrypcją platformy Azure.
3. Prześlij zdarzenie pomocy technicznej.

Aby uzyskać szczegółowe informacje, zapoznaj się z dokumentacją [techniczną](vs-tech-support.md) .

### <a name="q-who-owns-the-intellectual-property-i-create-using-my-azure-devtest-individual-credit"></a>P: kto jest właścicielem własności intelektualnej, którą tworzysz przy użyciu funkcji My DevTest na platformie Azure?
Odp.: własność intelektualna utworzona przez pracownika utworzonego w ramach zasobów dostarczonych przez firmę to własność intelektualna firmy dostarczającej zasób. W związku z tym, jeśli otrzymasz subskrypcję programu Visual Studio przez pracodawcę, zasady własności intelektualnej byłyby stosowane. 

## <a name="support-resources"></a>Zasoby pomocy technicznej
- Potrzebujesz pomocy dotyczącej platformy Azure?  Zapoznaj się z tymi zasobami:
  - Pomoc techniczna: [https://azure.microsoft.com/support/options/](https://azure.microsoft.com/support/options/)
  - [Wskazówki dotyczące platformy Azure & sztuczki](https://microsoft.github.io/AzureTipsAndTricks/ "Wskazówki dotyczące platformy Azure & sztuczki") 
- Aby uzyskać pomoc dotyczącą sprzedaży, subskrypcji, kont i rozliczeń dla subskrypcji programu Visual Studio, skontaktuj się z [pomocą techniczną subskrypcji](https://aka.ms/vssubscriberhelp)programu Visual Studio.
- Masz pytanie dotyczące środowiska IDE programu Visual Studio, Azure DevOps Services lub innych produktów lub usług Visual Studio?  Odwiedź stronę [pomocy technicznej programu Visual Studio](https://visualstudio.microsoft.com/support/).

## <a name="see-also"></a>Zobacz też
- [Dokumentacja programu Visual Studio](/visualstudio/)
- [Azure DevOps documentation (Dokumentacja usługi Azure DevOps)](/azure/devops/)
- [Dokumentacja platformy Azure](/azure/)
- [Dokumentacja Microsoft 365](/microsoft-365/)

## <a name="next-steps"></a>Następne kroki
Aby uzyskać więcej informacji na temat narzędzi i usług firmy Microsoft, zapoznaj się z dokumentacją dotyczącą:
- [Azure](/azure/)
- [Azure DevOps](/azure/devops/)
- [Visual Studio IDE](/visualstudio/)