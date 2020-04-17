---
title: Publikowanie usługi w chmurze platformy Azure
description: Dowiedz się, jak skonfigurować różne ustawienia kreatora publikowania aplikacji platformy Azure w programie Visual Studio
author: ghogen
manager: jillfra
assetId: 7d8f1ac9-e439-47e0-a183-0642c4ea1920
ms.custom: vs-azure
ms.workload: azure-vs
ms.topic: conceptual
ms.date: 03/21/2017
ms.author: ghogen
ms.openlocfilehash: bc3c58343c699833a5a12eee6f79c023f57a2e85
ms.sourcegitcommit: 59a8732dc563242590f7c6ccf4ced6c6d195533c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2020
ms.locfileid: "81489652"
---
# <a name="using-the-visual-studio-publish-azure-application-wizard"></a>Korzystanie z kreatora publikacji aplikacji platformy Azure programu Visual Studio

Po opracowaniu aplikacji sieci web w programie Visual Studio, można opublikować tę aplikację do usługi w chmurze platformy Azure przy użyciu kreatora **publikowania aplikacji platformy Azure.**

> [!Note]
> Ten artykuł dotyczy wdrażania usług w chmurze, a nie witryn sieci Web. Aby uzyskać informacje dotyczące wdrażania w witrynach sieci Web, zobacz [Jak wdrożyć witrynę sieci Web platformy Azure](https://social.msdn.microsoft.com/Search/windowsazure?query=How%20to%20Deploy%20an%20Azure%20Web%20Site&Refinement=138&ac=4#refinementChanges=117&pageNumber=1&showMore=false).

## <a name="accessing-the-publish-azure-application-wizard"></a>Uzyskiwanie dostępu do kreatora publikowania aplikacji platformy Azure

Kreatora publikowania aplikacji platformy Azure można uzyskać na dwa sposoby, w zależności od typu posiadanego projektu programu Visual Studio.

**Jeśli masz projekt usługi w chmurze platformy Azure:**

1. Tworzenie lub otwieranie projektu usługi w chmurze platformy Azure w programie Visual Studio.

1. W **Eksploratorze rozwiązań**kliknij prawym przyciskiem myszy projekt, a następnie z menu kontekstowego wybierz polecenie **Publikuj**.

**Jeśli masz projekt aplikacji sieci web, który nie jest włączony dla platformy Azure:**

1. Tworzenie lub otwieranie projektu usługi w chmurze platformy Azure w programie Visual Studio.

1. W **Eksploratorze rozwiązań**kliknij prawym przyciskiem myszy projekt, a następnie z menu kontekstowego wybierz polecenie **Konwertuj** > **konwersję na usługę Azure Cloud Service Project**.

1. W **Eksploratorze rozwiązań**kliknij prawym przyciskiem myszy nowo utworzony projekt platformy Azure, a następnie z menu kontekstowego wybierz polecenie **Publikuj**.

## <a name="sign-in-page"></a>Strona logowania

![Strona logowania](./media/vs-azure-tools-publish-azure-application-wizard/sign-in.png)

**Konto** — wybierz konto lub wybierz **pozycję Dodaj konto** na liście rozwijanej konta.

**Wybierz subskrypcję** — wybierz subskrypcję, która ma być używana dla twojego wdrożenia.

## <a name="settings-page---common-settings-tab"></a>Strona Ustawienia — karta Ustawienia typowe

![Typowe ustawienia](./media/vs-azure-tools-publish-azure-application-wizard/settings-common-settings.png)

**Usługa w chmurze** — korzystając z listy rozwijanej, wybierz istniejącą usługę w chmurze lub wybierz pozycję ** &lt;Utwórz nową>** i utwórz usługę w chmurze. Centrum danych jest wyświetlane w nawiasach dla każdej usługi w chmurze. Zaleca się, aby lokalizacja centrum danych dla usługi w chmurze była taka sama jak lokalizacja centrum danych dla konta magazynu (Ustawienia zaawansowane).

**Środowisko** — wybierz **opcję Produkcja** lub **przemieszczania**. Wybierz środowisko przejściowe, jeśli chcesz wdrożyć aplikację w środowisku testowym.

**Konfiguracja kompilacji** — wybierz **debugowanie** lub **zwolnij**.

**Konfiguracja usługi** — wybierz **chmurę** lub **lokalną**.

**Włącz pulpit zdalny dla wszystkich ról** — wybierz tę opcję, jeśli chcesz mieć możliwość zdalnego łączenia się z usługą. Ta opcja jest używana głównie do rozwiązywania problemów. Aby uzyskać więcej informacji, zobacz [Włączanie połączenia pulpitu zdalnego dla roli w usługach w chmurze azure przy użyciu programu Visual Studio](/azure/cloud-services/cloud-services-role-enable-remote-desktop-visual-studio).

**Włącz wdrażanie w sieci Web dla wszystkich ról sieci Web** — wybierz tę opcję, aby włączyć wdrażanie sieci Web dla usługi. Aby korzystać z tej funkcji, należy również wybrać opcję **Włącz pulpit zdalny dla wszystkich ról.** Aby uzyskać więcej informacji, zobacz [Publikowanie usługi w chmurze przy użyciu programu Visual Studio](vs-azure-tools-publishing-a-cloud-service.md).

## <a name="settings-page---advanced-settings-tab"></a>Strona Ustawienia — karta Ustawienia zaawansowane

![Ustawienia zaawansowane](./media/vs-azure-tools-publish-azure-application-wizard/settings-advanced-settings.png)

**Etykieta wdrożenia** — zaakceptuj nazwę domyślną lub wprowadź wybraną nazwę. Aby dołączyć datę do etykiety wdrożenia, pozostaw zaznaczone pole wyboru.

**Konto magazynu** — wybierz konto magazynu, które&lt;ma być używane dla tego wdrożenia, ** Utwórz nowe>, aby utworzyć konto magazynu. Centrum danych jest wyświetlane w nawiasach dla każdego konta magazynu. Zaleca się, aby lokalizacja centrum danych dla konta magazynu była taka sama jak lokalizacja centrum danych dla usługi w chmurze (Ustawienia wspólne).

Konto magazynu platformy Azure przechowuje pakiet dla wdrożenia aplikacji. Po wdrożeniu aplikacji pakiet jest usuwany z konta magazynu.

**Usuń wdrożenie w przypadku awarii** — wybierz tę opcję, aby wdrożenie zostało usunięte, jeśli podczas publikowania wystąpią błędy. Powinno to być niezaznaczone, jeśli chcesz zachować stały wirtualny adres IP dla usługi w chmurze.

**Aktualizacja wdrożenia** — wybierz tę opcję, jeśli chcesz wdrożyć tylko zaktualizowane składniki. Ten typ wdrożenia może być szybszy niż pełne wdrożenie. Należy to sprawdzić, jeśli chcesz zachować stały wirtualny adres IP dla usługi w chmurze.

**Aktualizacja wdrożenia — ustawienia** — to okno dialogowe służy do dalszego określania sposobu aktualizowania ról. Jeśli **wybierzesz aktualizację przyrostową,** każde wystąpienie aplikacji jest aktualizowane jeden po drugim, dzięki czemu aplikacja jest zawsze dostępna. Jeśli wybierzesz **jednoczesną aktualizację,** wszystkie wystąpienia aplikacji są aktualizowane w tym samym czasie. Jednoczesne aktualizowanie jest szybsze, ale usługa może nie być dostępna podczas procesu aktualizacji.

![Ustawienia wdrożenia](./media/vs-azure-tools-publish-azure-application-wizard/deployment-settings.png)

**Włącz IntelliTrace** - Określ, czy chcesz włączyć IntelliTrace. Za pomocą intellitrace można rejestrować szczegółowe informacje debugowania dla wystąpienia roli, gdy jest uruchamiany na platformie Azure. Jeśli chcesz znaleźć przyczynę problemu, można użyć dzienników IntelliTrace, aby przejść przez kod z programu Visual Studio, tak jakby był uruchomiony na platformie Azure. Aby uzyskać więcej informacji na temat korzystania z intellitrace, zobacz [Debugowanie opublikowanej usługi w chmurze platformy Azure za pomocą programów Visual Studio i IntelliTrace](./vs-azure-tools-intellitrace-debug-published-cloud-services.md).

**Włącz profilowanie** — określ, czy chcesz włączyć profilowanie wydajności. Profiler programu Visual Studio umożliwia uzyskanie dogłębnej analizy aspektów obliczeniowych sposobu działania usługi w chmurze. Aby uzyskać więcej informacji na temat korzystania z programu Visual Studio profiler, zobacz [Testowanie wydajności usługi w chmurze platformy Azure.](./vs-azure-tools-performance-profiling-cloud-services.md)

**Włącz debuger zdalny dla wszystkich ról** — określ, czy chcesz włączyć debugowanie zdalne. Aby uzyskać więcej informacji na temat debugowania usług w chmurze przy użyciu programu Visual Studio, zobacz [Debugowanie usługi w chmurze lub maszyny wirtualnej platformy Azure w programie Visual Studio.](./vs-azure-tools-debug-cloud-services-virtual-machines.md)

## <a name="diagnostics-settings-page"></a>Strona Ustawienia diagnostyki

![Ustawienia diagnostyczne](./media/vs-azure-tools-publish-azure-application-wizard/diagnostic-settings.png)

Diagnostyka umożliwia rozwiązywanie problemów z usługą w chmurze platformy Azure (lub maszyną wirtualną platformy Azure). Aby uzyskać informacje na temat diagnostyki, zobacz [Konfigurowanie diagnostyki usług w chmurze i maszyn wirtualnych platformy Azure.](./vs-azure-tools-diagnostics-for-cloud-services-and-virtual-machines.md) Aby uzyskać informacje o usłudze Application Insights, zobacz [Co to jest usługa Application Insights?](/azure/application-insights/app-insights-overview).

## <a name="summary-page"></a>Strona podsumowania

![Podsumowanie](./media/vs-azure-tools-publish-azure-application-wizard/summary.png)

**Profil docelowy** — można utworzyć profil publikowania na podstawie wybranych ustawień. Na przykład można utworzyć jeden profil dla środowiska testowego, a drugi dla środowiska produkcyjnego. Aby zapisać ten profil, wybierz ikonę **Zapisz.** Kreator tworzy profil i zapisuje go w projekcie programu Visual Studio. Aby zmodyfikować nazwę profilu, otwórz listę **profilów docelowych,** a następnie wybierz pozycję ** &lt;Zarządzaj... &gt;**.

   > [!Note]
   > Profil publikowania pojawia się w Eksploratorze rozwiązań w programie Visual Studio, a ustawienia profilu są zapisywane w pliku z rozszerzeniem .azurePubxml. Ustawienia są zapisywane jako atrybuty znaczników XML.

## <a name="publishing-your-application"></a>Publikowanie aplikacji

Po skonfigurowaniu wszystkich ustawień wdrożenia projektu wybierz pozycję **Publikuj** u dołu okna dialogowego. Stan procesu można monitorować w oknie **Dane wyjściowe** w programie Visual Studio.

## <a name="next-steps"></a>Następne kroki

- [Migrowanie i publikowanie aplikacji sieci Web do usługi w chmurze platformy Azure z programu Visual Studio](./vs-azure-tools-migrate-publish-web-app-to-cloud-service.md)

- [Dowiedz się, jak publikować usługę w chmurze usługi Azure za pomocą programu Visual Studio](./vs-azure-tools-publishing-a-cloud-service.md)

- [Debugowanie opublikowanej usługi w chmurze platformy Azure za pomocą programu Visual Studio i funkcji IntelliTrace](./vs-azure-tools-intellitrace-debug-published-cloud-services.md)

- [Testowanie wydajności usługi w chmurze platformy Azure](./vs-azure-tools-performance-profiling-cloud-services.md)

- [Konfigurowanie diagnostyki usług w chmurze i maszyn wirtualnych platformy Azure.](./vs-azure-tools-diagnostics-for-cloud-services-and-virtual-machines.md)

- [Co to jest usługa Application Insights?](/azure/application-insights/app-insights-overview)