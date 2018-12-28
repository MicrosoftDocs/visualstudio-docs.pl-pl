---
title: Za pomocą aplikacji platformy Azure Kreator publikacji | Dokumentacja firmy Microsoft
description: Dowiedz się, jak skonfigurować różne ustawienia w programie Visual Studio Azure Kreator publikowania aplikacji
author: ghogen
manager: douge
assetId: 7d8f1ac9-e439-47e0-a183-0642c4ea1920
ms.prod: visual-studio-dev14
ms.technology: vs-azure
ms.custom: vs-azure
ms.workload: azure-vs
ms.topic: conceptual
ms.date: 03/21/2017
ms.author: ghogen
ms.openlocfilehash: ed8d162d3b4cde48515986c475563e368a5946bf
ms.sourcegitcommit: f6dd17b0864419083d0a1bf54910023045526437
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/27/2018
ms.locfileid: "53803109"
---
# <a name="using-the-visual-studio-publish-azure-application-wizard"></a>Korzystanie z kreatora publikacji aplikacji platformy Azure programu Visual Studio

Po opracowywania aplikacji sieci web w programie Visual Studio, można opublikować tę aplikację w usłudze w chmurze platformy Azure za pomocą **publikowanie aplikacji platformy Azure** kreatora.

> [!Note]
> Ten artykuł dotyczy wdrażania do usług w chmurze, nie do witryn sieci web. Aby uzyskać informacji na temat wdrażania witryn sieci web, zobacz [sposób wdrażania witryny sieci Web systemu Azure](https://social.msdn.microsoft.com/Search/windowsazure?query=How%20to%20Deploy%20an%20Azure%20Web%20Site&Refinement=138&ac=4#refinementChanges=117&pageNumber=1&showMore=false).

## <a name="accessing-the-publish-azure-application-wizard"></a>Uzyskiwanie dostępu do Kreatora publikowania aplikacji na platformie Azure

Możesz uzyskać dostęp do Kreatora publikowania aplikacji na platformie Azure na dwa sposoby w zależności od typu projektu programu Visual Studio, do których masz.

**Jeśli masz projekt usługi w chmurze platformy Azure:**

1. Utwórz lub Otwórz projekt usługi w chmurze platformy Azure w programie Visual Studio.

1. W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy projekt i wybierz z menu kontekstowego **Publikuj**.

**Jeśli masz projekt aplikacji sieci web, która nie jest włączona dla platformy Azure:**

1. Utwórz lub Otwórz projekt usługi w chmurze platformy Azure w programie Visual Studio.

1. W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy projekt i wybierz z menu kontekstowego **przekonwertować** > **Konwertuj na projekt usługi w chmurze Azure**.

1. W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy nowo utworzony projekt platformy Azure i z menu kontekstowego wybierz **Publikuj**.

## <a name="sign-in-page"></a>Strona logowania

![Strona logowania](./media/vs-azure-tools-publish-azure-application-wizard/sign-in.png)

**Konto** — wybierz konto lub **Dodaj konto** na liście rozwijanej konta.

**Wybierz subskrypcję** — Wybierz subskrypcję do użycia dla danego wdrożenia.

## <a name="settings-page---common-settings-tab"></a>Strona ustawień — karta typowe ustawienia

![Typowe ustawienia](./media/vs-azure-tools-publish-azure-application-wizard/settings-common-settings.png)

**Usługa w chmurze** — korzystając z listy rozwijanej, wybierz istniejącej chmury usługi lub wybierz  **&lt;Utwórz nową >** i Utwórz usługę w chmurze. Centrum danych są wyświetlane w nawiasach dla każdej usługi w chmurze. Zaleca się, że centrum danych lokalizacji usługi w chmurze być taka sama jak lokalizacja centrum danych dla konta magazynu (Zaawansowane ustawienia).

**Środowisko** — wybierz opcję **produkcji** lub **przemieszczania**. Wybierz środowisko przejściowe, jeśli chcesz wdrożyć aplikację w środowisku testowym.

**Konfiguracja kompilacji** — wybierz opcję **debugowania** lub **wersji**.

**Konfiguracja usługi** — wybierz opcję **chmury** lub **lokalnego**.

**Włącz pulpit zdalny dla wszystkich ról** — wybierz tę opcję, jeśli chcesz można było zdalnie połączyć się z usługą. Ta opcja jest używany głównie do rozwiązywania problemów. Aby uzyskać więcej informacji, zobacz [Włącz Podłączanie pulpitu zdalnego dla roli w usługach Azure Cloud Services przy użyciu programu Visual Studio](/azure/cloud-services/cloud-services-role-enable-remote-desktop-visual-studio).

**Włącz narzędzie Web Deploy dla wszystkich ról w sieci web** — wybierz tę opcję, aby umożliwić wdrażanie w Internecie usługi. Należy również zaznaczyć **Włącz pulpit zdalny dla wszystkich ról** opcję, aby korzystać z tej funkcji. Aby uzyskać więcej informacji, zobacz [publikowania usługi w chmurze przy użyciu programu Visual Studio](vs-azure-tools-publishing-a-cloud-service.md).

## <a name="settings-page---advanced-settings-tab"></a>Strona ustawień — karta Ustawienia zaawansowane

![Ustawienia zaawansowane](./media/vs-azure-tools-publish-azure-application-wizard/settings-advanced-settings.png)

**Etykieta wdrożenia** — zaakceptuj nazwę domyślną lub wprowadź nazwę. Aby dołączyć datę do etykiety wdrożenia, pozostaw zaznaczone pole wyboru.

**Konto magazynu** — wybierz konto magazynu do użycia dla tego wdrożenia **&lt;Utwórz nową > Utwórz konto magazynu. Centrum danych są wyświetlane w nawiasach dla każdego konta magazynu. Zaleca się, że na lokalizację centrum danych dla konta magazynu jest taka sama jak lokalizacja centrum danych dla usługi w chmurze (typowe ustawienia).

Konto usługi Azure storage przechowuje pakietu dla wdrożenia aplikacji. Po wdrożeniu aplikacji, pakiet zostanie usunięty z konta magazynu.

**Usuń wdrożenie w przypadku niepowodzenia** — wybierz tę opcję, aby wdrożenie usunięte, jeśli nie zostaną napotkane błędy podczas publikowania. To powinno być zaznaczone, jeśli chcesz utrzymać stałej wirtualny adres IP dla usługi w chmurze.

**Wdrożenia aktualizacji** — wybierz tę opcję, jeśli chcesz wdrożyć tylko zaktualizowane składniki. Ten typ wdrożenia może być szybsza niż pełne wdrożenie. Jeśli chcesz utrzymać stałej wirtualny adres IP dla usługi w chmurze, to powinno być zaznaczone.

**Wdrożenia aktualizacji - ustawienia** — to okno dialogowe służy do dalszego określenia sposobu ról do zaktualizowania. Jeśli wybierzesz **aktualizacji przyrostowej**, każde wystąpienie aplikacji zostanie zaktualizowany po kolei, więc, że aplikacja jest zawsze dostępna. Jeśli wybierzesz **jednoczesne aktualizowanie**, wszystkie wystąpienia aplikacji są aktualizowane w tym samym czasie. Jednoczesne aktualizowanie jest szybsze, ale usługa może nie być dostępna podczas procesu aktualizacji.

![Ustawienia wdrożenia](./media/vs-azure-tools-publish-azure-application-wizard/deployment-settings.png)

**Włączenie funkcji IntelliTrace** — Określ, czy chcesz włączyć funkcji IntelliTrace. Po uruchomieniu na platformie Azure przy użyciu funkcji IntelliTrace, możesz rejestrować wyczerpujące informacje debugowania dla wystąpienia roli. Jeśli potrzebujesz znaleźć przyczynę problemu, można użyć dzienników IntelliTrace do kroku przez kod z programu Visual Studio, tak jakby były uruchamiane na platformie Azure. Aby uzyskać więcej informacji na temat za pomocą funkcji IntelliTrace, zobacz [debugowanie usługi opublikowana chmura platformy Azure za pomocą programu Visual Studio i IntelliTrace](./vs-azure-tools-intellitrace-debug-published-cloud-services.md).

**Włącz profilowanie** — Określ, czy włączyć profilowanie ich wydajności. Profilera Visual Studio pozwala uzyskać dokładnych analiz obliczeniową aspektami działania usługi w chmurze. Aby uzyskać więcej informacji na temat korzystania z programu Visual Studio profiler, zobacz [testowanie wydajności usługi w chmurze Azure](./vs-azure-tools-performance-profiling-cloud-services.md).

**Włącz zdalny debuger dla wszystkich ról** — Określ, czy włączyć zdalne debugowanie. Aby uzyskać więcej informacji na temat debugowania usług w chmurze przy użyciu programu Visual Studio, zobacz [debugowanie usługi w chmurze platformy Azure lub maszynie wirtualnej w programie Visual Studio](./vs-azure-tools-debug-cloud-services-virtual-machines.md).

## <a name="diagnostics-settings-page"></a>Strona Ustawienia diagnostyki

![Ustawienia diagnostyki](./media/vs-azure-tools-publish-azure-application-wizard/diagnostic-settings.png)

Diagnostyka umożliwia rozwiązywanie problemów z usługą w chmurze platformy Azure (lub maszyn wirtualnych platformy Azure). Aby uzyskać informacje o diagnostyce, zobacz [Konfigurowanie diagnostyki dla usług Azure Cloud Services i Virtual Machines](./vs-azure-tools-diagnostics-for-cloud-services-and-virtual-machines.md). Aby uzyskać informacje na temat usługi Application Insights, zobacz [co to jest usługa Application Insights?](/azure/application-insights/app-insights-overview).

## <a name="summary-page"></a>Strona podsumowania

![Podsumowanie](./media/vs-azure-tools-publish-azure-application-wizard/summary.png)

**Docelowy profil** — możesz utworzyć profil publikowania z ustawień, które zostały wybrane. Na przykład utworzyć jeden profil dla środowiska testowego, a drugi dla środowiska produkcyjnego. Aby zapisać ten profil, wybierz **Zapisz** ikony. Kreator utworzy profil i zapisze go w projekcie programu Visual Studio. Aby zmodyfikować nazwę profilu, otwórz **docelowy profil** , a następnie wybierz  **&lt;Zarządzaj... &gt;**.

   > [!Note]
   > Profil publikowania zostanie wyświetlony w Eksploratorze rozwiązań w programie Visual Studio, a ustawienia profilu są zapisywane w pliku z rozszerzeniem .azurePubxml. Ustawienia są zapisywane jako atrybuty tagów XML.

## <a name="publishing-your-application"></a>Publikowanie aplikacji

Po skonfigurowaniu wszystkich ustawień dla wdrażania projektu, wybierz **Publikuj** w dolnej części okna dialogowego. Możesz monitorować stan procesu w **dane wyjściowe** okna w programie Visual Studio.

## <a name="next-steps"></a>Następne kroki

- [Migracja i publikowanie aplikacji sieci Web w usłudze w chmurze platformy Azure z programu Visual Studio](./vs-azure-tools-migrate-publish-web-app-to-cloud-service.md)

- [Dowiedz się, jak publikować usługi w chmurze platformy Azure za pomocą programu Visual Studio](./vs-azure-tools-publishing-a-cloud-service.md)

- [Debugowanie usługi opublikowana chmura platformy Azure za pomocą programu Visual Studio i funkcji IntelliTrace](./vs-azure-tools-intellitrace-debug-published-cloud-services.md)

- [Testowanie wydajności usługi w chmurze platformy Azure](./vs-azure-tools-performance-profiling-cloud-services.md)

- [Konfigurowanie diagnostyki dla usług Azure Cloud Services i Virtual Machines](./vs-azure-tools-diagnostics-for-cloud-services-and-virtual-machines.md).

- [Co to jest usługa Application Insights?](/azure/application-insights/app-insights-overview)