---
title: Publikowanie usługi w chmurze platformy Azure
description: Dowiedz się, jak skonfigurować różne ustawienia w Kreatorze publikacji aplikacji platformy Azure dla programu Visual Studio
author: ghogen
manager: jillfra
assetId: 7d8f1ac9-e439-47e0-a183-0642c4ea1920
ms.custom: vs-azure
ms.workload: azure-vs
ms.topic: how-to
ms.date: 03/21/2017
ms.author: ghogen
ms.openlocfilehash: 477b7860c320730d6362cdb7e0fcb46ad3bc7d17
ms.sourcegitcommit: 1d4f6cc80ea343a667d16beec03220cfe1f43b8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/23/2020
ms.locfileid: "85280534"
---
# <a name="using-the-visual-studio-publish-azure-application-wizard"></a>Korzystanie z kreatora publikacji aplikacji platformy Azure programu Visual Studio

Po opracowaniu aplikacji sieci Web w programie Visual Studio można opublikować tę aplikację w usłudze w chmurze platformy Azure za pomocą kreatora **publikowania aplikacji platformy Azure** .

> [!Note]
> Ten artykuł dotyczy wdrażania usług w chmurze, a nie witryn sieci Web. Informacje o wdrażaniu w witrynach sieci Web znajdują się w temacie [jak wdrożyć witrynę sieci Web systemu Azure](https://social.msdn.microsoft.com/Search/windowsazure?query=How%20to%20Deploy%20an%20Azure%20Web%20Site&Refinement=138&ac=4#refinementChanges=117&pageNumber=1&showMore=false).

## <a name="accessing-the-publish-azure-application-wizard"></a>Uzyskiwanie dostępu do Kreatora publikowania aplikacji platformy Azure

Dostęp do Kreatora publikowania aplikacji platformy Azure można uzyskać na dwa sposoby w zależności od typu projektu programu Visual Studio.

**Jeśli masz projekt usługi w chmurze platformy Azure:**

1. Utwórz lub Otwórz projekt usługi w chmurze platformy Azure w programie Visual Studio.

1. W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy projekt, a następnie z menu kontekstowego wybierz pozycję **Publikuj**.

**Jeśli masz projekt aplikacji sieci Web, który nie jest włączony dla platformy Azure:**

1. Utwórz lub Otwórz projekt usługi w chmurze platformy Azure w programie Visual Studio.

1. W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy projekt, a następnie z menu kontekstowego wybierz polecenie **Konwertuj**  >  **Konwertuj na projekt usługi w chmurze platformy Azure**.

1. W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy nowo utworzony projekt platformy Azure, a następnie z menu kontekstowego wybierz pozycję **Publikuj**.

## <a name="sign-in-page"></a>Strona logowania

![Strona logowania](./media/vs-azure-tools-publish-azure-application-wizard/sign-in.png)

**Konto** — wybierz konto lub wybierz pozycję **Dodaj konto** z listy rozwijanej konto.

**Wybierz subskrypcję** — wybierz subskrypcję, która ma być używana dla danego wdrożenia.

## <a name="settings-page---common-settings-tab"></a>Strona Ustawienia — Karta Ustawienia wspólne

![Typowe ustawienia](./media/vs-azure-tools-publish-azure-application-wizard/settings-common-settings.png)

**Usługa w chmurze** — Użyj listy rozwijanej, wybierz istniejącą usługę w chmurze lub wybierz pozycję ** &lt; Utwórz nową>** i Utwórz usługę w chmurze. Centrum danych wyświetla w nawiasach dla każdej usługi w chmurze. Zaleca się, aby lokalizacja centrum danych dla usługi w chmurze była taka sama jak lokalizacja centrum danych dla konta magazynu (Ustawienia zaawansowane).

**Środowisko** — wybierz opcję **produkcyjne** lub **przejściowe**. Wybierz środowisko przejściowe, jeśli chcesz wdrożyć aplikację w środowisku testowym.

**Konfiguracja kompilacji** — wybierz opcję **Debuguj** lub **Zwolnij**.

**Konfiguracja usługi** — wybierz **chmurę** lub **lokalną**.

**Włącz pulpit zdalny dla wszystkich ról** — wybierz tę opcję, jeśli chcesz mieć możliwość zdalnego łączenia się z usługą. Ta opcja jest używana głównie do rozwiązywania problemów. Aby uzyskać więcej informacji, zobacz [włączanie Podłączanie pulpitu zdalnego dla roli na platformie Azure Cloud Services przy użyciu programu Visual Studio](/azure/cloud-services/cloud-services-role-enable-remote-desktop-visual-studio).

**Włącz Web Deploy dla wszystkich ról sieci Web** — wybierz tę opcję, aby włączyć wdrażanie w sieci Web dla usługi. Należy również wybrać opcję **włącz pulpit zdalny dla wszystkich ról** , aby użyć tej funkcji. Aby uzyskać więcej informacji, zobacz [publikowanie usługi w chmurze przy użyciu programu Visual Studio](vs-azure-tools-publishing-a-cloud-service.md).

## <a name="settings-page---advanced-settings-tab"></a>Strona Ustawienia — Karta Ustawienia zaawansowane

![Ustawienia zaawansowane](./media/vs-azure-tools-publish-azure-application-wizard/settings-advanced-settings.png)

**Etykieta wdrożenia** — Zaakceptuj nazwę domyślną lub wprowadź wybraną nazwę. Aby dołączyć datę do etykiety wdrożenia, pozostaw zaznaczone pole wyboru.

**Konto magazynu** — wybierz konto magazynu, które ma być używane dla tego wdrożenia, * * &lt; Utwórz nowe>, aby utworzyć konto magazynu. Centrum danych wyświetla w nawiasach dla każdego konta magazynu. Zalecane jest, aby lokalizacja centrum danych dla konta magazynu była taka sama, jak lokalizacja centrum danych dla usługi w chmurze (typowe ustawienia).

Konto usługi Azure Storage przechowuje pakiet dla wdrożenia aplikacji. Po wdrożeniu aplikacji pakiet zostanie usunięty z konta magazynu.

**Usuń wdrożenie w przypadku niepowodzenia** — wybierz tę opcję, aby usunąć wdrożenie, jeśli podczas publikowania wystąpią jakieś błędy. Nie należy zaznaczać tego pola, jeśli chcesz zachować stały wirtualny adres IP dla usługi w chmurze.

**Aktualizacja wdrożenia** — wybierz tę opcję, jeśli chcesz wdrożyć tylko zaktualizowane składniki. Ten typ wdrożenia może być szybszy niż w przypadku pełnego wdrożenia. Należy to sprawdzić, jeśli chcesz zachować stały wirtualny adres IP dla usługi w chmurze.

**Aktualizacja wdrożenia-ustawienia** — to okno dialogowe służy do dokładniejszego określania, w jaki sposób mają być aktualizowane role. W przypadku wybrania **aktualizacji przyrostowych**każde wystąpienie aplikacji jest aktualizowane jeden po drugim, dzięki czemu aplikacja będzie zawsze dostępna. W przypadku wybrania opcji **równoczesne aktualizowanie**wszystkie wystąpienia aplikacji są aktualizowane w tym samym czasie. Jednoczesne aktualizowanie jest szybsze, ale usługa może być niedostępna w trakcie procesu aktualizacji.

![Ustawienia wdrożenia](./media/vs-azure-tools-publish-azure-application-wizard/deployment-settings.png)

**Włącz IntelliTrace** — Określ, czy chcesz włączyć IntelliTrace. Za pomocą IntelliTrace można rejestrować obszerne informacje o debugowaniu dla wystąpienia roli uruchomionego na platformie Azure. Jeśli chcesz znaleźć przyczynę problemu, możesz użyć dzienników IntelliTrace, aby przejść do kodu z programu Visual Studio, tak jakby był uruchomiony na platformie Azure. Aby uzyskać więcej informacji na temat korzystania z programu IntelliTrace, zobacz [debugowanie opublikowanej usługi w chmurze platformy Azure za pomocą programu Visual Studio i IntelliTrace](./vs-azure-tools-intellitrace-debug-published-cloud-services.md).

**Włącz profilowanie** — Określ, czy chcesz włączyć profilowanie wydajności. Program Visual Studio profiler umożliwia uzyskanie szczegółowej analizy aspektów obliczeniowych sposobu działania usługi w chmurze. Aby uzyskać więcej informacji na temat korzystania z profilera programu Visual Studio, zobacz [testowanie wydajności usługi w chmurze platformy Azure](./vs-azure-tools-performance-profiling-cloud-services.md).

**Włącz debuger zdalny dla wszystkich ról** — Określ, czy chcesz włączyć debugowanie zdalne. Aby uzyskać więcej informacji na temat debugowania usług w chmurze przy użyciu programu Visual Studio, zobacz [debugowanie usługi w chmurze lub maszyny wirtualnej platformy Azure w programie Visual Studio](./vs-azure-tools-debug-cloud-services-virtual-machines.md).

## <a name="diagnostics-settings-page"></a>Strona ustawień diagnostycznych

![Ustawienia diagnostyczne](./media/vs-azure-tools-publish-azure-application-wizard/diagnostic-settings.png)

Diagnostyka umożliwia rozwiązywanie problemów z usługą w chmurze platformy Azure (lub maszyną wirtualną platformy Azure). Aby uzyskać informacje na temat diagnostyki, zobacz [Konfigurowanie diagnostyki dla usług Azure Cloud Services i Virtual Machines](./vs-azure-tools-diagnostics-for-cloud-services-and-virtual-machines.md). Aby uzyskać informacje na temat Application Insights, zobacz [co to jest Application Insights?](/azure/application-insights/app-insights-overview).

## <a name="summary-page"></a>Strona podsumowania

![Podsumowanie](./media/vs-azure-tools-publish-azure-application-wizard/summary.png)

**Profil docelowy** — możesz wybrać opcję utworzenia profilu publikowania na podstawie ustawień, które zostały wybrane. Na przykład można utworzyć jeden profil dla środowiska testowego i drugi dla produkcji. Aby zapisać ten profil, wybierz ikonę **Zapisz** . Kreator utworzy profil i zapisze go w projekcie programu Visual Studio. Aby zmodyfikować nazwę profilu, Otwórz listę **profil docelowy** , a następnie wybierz pozycję ** &lt; Zarządzaj &gt; .**

   > [!Note]
   > Profil publikowania zostanie wyświetlony w Eksplorator rozwiązań w programie Visual Studio, a ustawienia profilu są zapisywane w pliku z rozszerzeniem. azurePubxml. Ustawienia są zapisywane jako atrybuty tagów XML.

## <a name="publishing-your-application"></a>Publikowanie aplikacji

Po skonfigurowaniu wszystkich ustawień wdrożenia projektu wybierz pozycję **Publikuj** w dolnej części okna dialogowego. Możesz monitorować stan procesu w oknie **danych wyjściowych** w programie Visual Studio.

## <a name="next-steps"></a>Następne kroki

- [Migrowanie i publikowanie aplikacji sieci Web w usłudze w chmurze platformy Azure z poziomu programu Visual Studio](./vs-azure-tools-migrate-publish-web-app-to-cloud-service.md)

- [Dowiedz się, jak opublikować usługę w chmurze platformy Azure za pomocą programu Visual Studio](./vs-azure-tools-publishing-a-cloud-service.md)

- [Debugowanie opublikowanej usługi w chmurze platformy Azure za pomocą programu Visual Studio i funkcji IntelliTrace](./vs-azure-tools-intellitrace-debug-published-cloud-services.md)

- [Testowanie wydajności usługi w chmurze platformy Azure](./vs-azure-tools-performance-profiling-cloud-services.md)

- [Konfigurowanie diagnostyki dla Cloud Services i Virtual Machines platformy Azure](./vs-azure-tools-diagnostics-for-cloud-services-and-virtual-machines.md).

- [Co to jest usługa Application Insights?](/azure/application-insights/app-insights-overview)