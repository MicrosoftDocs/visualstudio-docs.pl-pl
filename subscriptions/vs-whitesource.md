---
title: Użyj narzędzia WhiteSource Bolt korzyści | Dokumentacja firmy Microsoft
author: evanwindom
ms.author: jaunger
manager: evelynp
ms.date: 12/19/2018
ms.topic: Get-Started-Article
description: Dowiedz się, jak aktywować subskrypcję WhiteSource Bolt zawartych w ramach subskrypcji programu Visual Studio.
ms.prod: vs-subscription
ms.technology: vs-subscriptions
searchscope: VS Subscription
ms.openlocfilehash: d9f4db463dad3ee2fbb216284791018dc504d7b6
ms.sourcegitcommit: 159ed9d4f56cdc1dff2fd19d9dffafe77e46cd4e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2018
ms.locfileid: "53739987"
---
#  <a name="whitesource-bolt-in-visual-studio-subscriptions"></a>Użyj narzędzia WhiteSource Bolt w subskrypcji programu Visual Studio

Znajdowanie i eliminowanie luk w zabezpieczeniach typu open source oraz generowanie kompleksowych raportów spisu i licencji wszystkich składników typu open source w kompilacji. Niektóre subskrypcje programu Visual Studio obejmują sześć miesięcy bezpłatnego dostępu.

## <a name="activation-steps"></a>Procedurę aktywacji

1. Aby aktywować swoje korzyści WhiteSource Bolt, zaloguj się do [ https://my.visualstudio.com/benefits ](https://my.visualstudio.com/benefits?wt.mc_id=o~msft~docs) .

2. Znajdź Kafelek WhiteSource Bolt w sekcji narzędzia, a następnie kliknij **uzyskać kod** link w dolnej części kafelka korzyści.
   > [!div class="mx-imgBorder"]
   > ![WhiteSource korzyści kafelka](_img/vs-whitesource/vs-whitesource-tile.png)

3. Otrzymasz powiadomienie o wyświetlaniu kodu aktywacji.  **Skopiuj kod do Schowka**, następnie kliknij przycisk **Aktywuj**.
   > [!div class="mx-imgBorder"]
   > ![WhiteSource korzyści kodu ](_img/vs-whitesource/vs-whitesource-code.png)

4. Na stronie sieci web WhiteSource kliknij **Aktywuj** przycisk lub przewiń w dół do **aktywować konta** części strony.
   > [!div class="mx-imgBorder"]
   > ![Aktywuj korzyść WhiteSource](_img/vs-whitesource/vs-whitesource-activate-page-cropped.png)

5. W **aktywować konta** sekcji strony poprowadzą Cię przez cztery kroki:

   - [Zainstaluj](https://marketplace.visualstudio.com/items?itemName=whitesource.ws-bolt) rozszerzenia WhiteSource Bolt z programu Microsoft Visual Studio marketplace. Jeśli nie masz uprawnienia do instalowania rozszerzeń, zobacz [instalowanie bezpłatnych rozszerzeń dla usługi Azure DevOps Services](/azure/devops/marketplace/install-vsts-extension?view=vsts).


~~~
Click the green **Install** button if you are using Azure DevOps Services, or the **Download** button for Team Foundation Server.  For this example, we will use Azure DevOps Services.
> [!div class="mx-imgBorder"]
> ![WhiteSource Benefit Install Extension](_img\vs-whitesource\vs-whitesource-download-install.png)

- Next, select the Azure DevOps organization you want to use and click **Confirm**.  (If you have not yet set up Azure DevOps Services, visit the [Benefits](https://my.visualstudio.com/benefits) page and activate your Azure DevOps Services benefit.)

> [!div class="mx-imgBorder"]
> ![WhiteSource Benefit Confirm Account](_img\vs-whitesource\vs-whitesource-confirm-account.png)

- You’ll receive a confirmation that the extension is installed and ready to use.  Click **Get started** to return to the WhiteSource Bolt page and continue.
> [!div class="mx-imgBorder"]
> ![WhiteSource Benefit Install Complete](_img\vs-whitesource\vs-whitesource-install-complete.png)
~~~

5. Otwórz pulpit nawigacyjny projektu DevOps platformy Azure, kliknij pozycję **potoki Azure** menu i wybierz polecenie **WhiteSource Bolt**.
   > [!div class="mx-imgBorder"]
   > ![WhiteSource korzyści Dodaj rozszerzenie](_img/vs-whitesource/vs-whitesource-installed-cropped.png)

6. Wklej kod aktywacji za pomocą kafelka korzyści WhiteSource Bolt, a następnie kliknij przycisk **Aktywuj**. Każdy z kolejnych kodów aktywacji można aktywować tylko jeden projekt.
   > [!div class="mx-imgBorder"]
   > ![Aktywować korzyści WhiteSource](_img/vs-whitesource/vs-whitesource-activate-code-cropped.png)

7. Proces aktywacji jest teraz gotowy i będzie mieć 180 dni pozostałych w ramach Twojej subskrypcji.

8. Należy dodać rozszerzenie WhiteSource Bolt jako jeden z kroków kompilacji.  Film wideo jest dostępna w [strony WhiteSource Bolt](https://www.whitesourcesoftware.com/whitesource_bolt_visualstudio_2017/#activate) aby pokazać, jak.

9. Po uruchomieniu kompilacji, następujące kompleksowych raportów i pulpitów nawigacyjnych będą automatycznie generowane:
    - Pulpit nawigacyjny luk w zabezpieczeniach
    - Raport o luk w zabezpieczeniach
    - Przestarzałe biblioteki raportów
    - Pulpit nawigacyjny ryzyka i zgodności licencji
    - Raport o spisie

## <a name="eligibility"></a>Uprawnienie

| Poziom subskrypcji                                                 |     Kanały                                            | Korzyść                                                          | Podlega odnowieniu?    |
|--------------------------------------------------------------------|---------------------------------------------------------|------------------------------------------------------------------|---------------|
| Visual Studio Enterprise (standardowa)   | Licencjonowania zbiorowego, Azure, w sprzedaży detalicznej, wybrane NFR<sup>1</sup> | 6 miesięcy       |  Tak          |
| Visual Studio Professional (standardowa) | VL, Azure, Retail                                       | Nie jest dostępna                                                           |Nie dotyczy         |
| Visual Studio Test Professional (standardowa)                         | Licencjonowania zbiorowego, handlu detalicznego                                              | Niedostępne                                             |  Nie dotyczy         |
| Platformy MSDN (standardowa)                                          | Licencjonowania zbiorowego, handlu detalicznego                                              | Niedostępne                                              | Nie dotyczy         |
| Visual Studio Dev Essentials | Nie dotyczy  | Niedostępne |Nie dotyczy |
| Program Visual Studio Enterprise, Visual Studio Professional (miesięcznych w chmurze) | Azure                                       | Niedostępne                                                           |Nie dotyczy|

<sup>1</sup>*obejmuje:    Microsoft Partner Network (przedsiębiorstwo).  Nie obejmuje: Inne Not for Resale (NFR), Visual Studio Industry Partner (VSIP), ekwiwalentu pełnego wymiaru czasu, MCT Software & deweloperów usług, BizSpark, Imagine, Microsoft wycenia Professional (MVP), dyrektor Region (usług pulpitu zdalnego), MCT Software & Services, Microsoft Partner Network (Professional ).*


> [!NOTE]
> Microsoft nie oferuje już program Visual Studio Professional rocznych subskrypcji i programu Visual Studio Enterprise rocznej subskrypcji w subskrypcje w chmurze. Będzie bez zmian do istniejących klientów obsługa produktu próbnego oraz możliwość odnowienia, zwiększyć, zmniejszyć lub anulować ich subskrypcje. Zachęcamy klientów, nowy, aby przejść do [ https://visualstudio.microsoft.com/vs/pricing/ ](https://visualstudio.microsoft.com/vs/pricing/) Aby zapoznać się z różnych opcji zakupu programu Visual Studio.


Nie masz pewności której subskrypcji używasz?  Połączyć się z [ https://my.visualstudio.com/subscriptions ](https://my.visualstudio.com/subscriptions?wt.mc_id=o~msft~docs) Aby wyświetlić wszystkie subskrypcje, które są przypisane do Twojego adresu e-mail. Jeśli nie widzisz wszystkie swoje subskrypcje, mogą mieć co najmniej jeden przypisany do innego adresu e-mail.  Musisz zalogować się przy użyciu tego adresu e-mail, aby wyświetlić te subskrypcje.

## <a name="support-resources"></a>Zasoby pomocy technicznej

-  Potrzebujesz pomocy dotyczącej WhiteSource Bolt?  Porozmawiaj z przedstawicielem WhiteSource Bolt na żywo w https://www.whitesourcesoftware.com/vse_whitesource_bolt/
-  Aby uzyskać pomoc dotyczącą sprzedaży, subskrypcji, kont i rozliczeń dla subskrypcji programu Visual Studio, skontaktuj się z pomocą programu Visual Studio [pomoc techniczna dla subskrypcji](https://visualstudio.microsoft.com/subscriptions/support/).
-  Masz pytanie dotyczące programu Visual Studio IDE, usługom DevOps platformy Azure lub innych produktów Visual Studio lub usług?  Odwiedź stronę [pomoc techniczna dla programu Visual Studio](https://visualstudio.microsoft.com/support/).