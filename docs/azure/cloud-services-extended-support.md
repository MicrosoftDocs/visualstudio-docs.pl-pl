---
title: Użyj Cloud Services (obsługa rozszerzona) (wersja zapoznawcza)
description: Dowiedz się teraz, jak tworzyć i wdrażać Cloud Services (rozszerzoną pomoc techniczną) przy użyciu Azure Resource Manager z programem Visual Studio
author: ghogen
manager: jillfra
ms.custom: vs-azure
ms.workload: azure-vs
ms.topic: how-to
ms.date: 01/25/2021
ms.author: ghogen
monikerRange: '>=vs-2019'
ms.openlocfilehash: ff45cf05a6811c02881c26f76193d4c1f5a5e735
ms.sourcegitcommit: 7d34ab111614ae6bde5fb3c2bb91dd79e29a0a78
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2021
ms.locfileid: "98750306"
---
# <a name="create-and-deploy-to-cloud-services-extended-support-in-visual-studio-preview"></a>Tworzenie i wdrażanie do Cloud Services (obsługa rozszerzona) w programie Visual Studio (wersja zapoznawcza)

Począwszy od [programu Visual Studio 2019 wersja 16,9](https://visualstudio.microsoft.com/vs/preview) (obecnie w wersji zapoznawczej), możesz współpracować z usługami w chmurze, korzystając z Azure Resource Manager, co znacznie upraszcza i modernizacj konserwację zasobów platformy Azure oraz zarządzanie nimi. Jest to możliwe dzięki nowej usłudze platformy Azure, która jest nazywana *Cloud Services (obsługa rozszerzona)*. Istnieje możliwość opublikowania istniejącej usługi w chmurze w celu Cloud Services (obsługa rozszerzona). Aby uzyskać informacje na temat tej usługi platformy Azure, zobacz [dokumentację dotyczącą Cloud Services (obsługa rozszerzona)](/azure/cloud-services-extended-support/overview).

## <a name="publish-to-cloud-services-extended-support"></a>Publikowanie w Cloud Services (obsługa rozszerzona)

W przypadku publikowania istniejącego projektu usługi w chmurze platformy Azure w celu Cloud Services (obsługa rozszerzona) nadal będzie można publikować w klasycznej usłudze w chmurze platformy Azure. W programie Visual Studio 2019 w wersji 16,9 Preview 3 i nowszych projekty usług w chmurze klasycznej mają specjalną wersję polecenia **Publikuj** , **Publikuj (obsługa rozszerzona)**. To polecenie pojawia się w menu skrótów w **Eksplorator rozwiązań**.

Istnieją pewne różnice w publikowaniu do Cloud Services (obsługa rozszerzona). Na przykład nie zostanie wyświetlony monit o opublikowanie w środowisku **przejściowym** lub **produkcyjnym**, ponieważ te miejsca wdrożenia nie są częścią modelu publikowania obsługi rozszerzonej. Zamiast tego w przypadku Cloud Services (obsługa rozszerzona) można skonfigurować wiele wdrożeń i wymienić wdrożenia w Azure Portal. Mimo że narzędzia programu Visual Studio pozwalają na ustawienie tego ustawienia w wersji zapoznawczej 3 programu 16,9, funkcja wymiany nie zostanie włączona do nowszej wersji Cloud Services (obsługa rozszerzona) i może spowodować błąd podczas wdrażania w trakcie okresu zapoznawczego.

Przed opublikowaniem klasycznej usługi w chmurze platformy Azure w celu Cloud Services (obsługa rozszerzona) Sprawdź konta magazynu używane przez program Project i upewnij się, że są to konta magazynu w wersji 1 lub 2. Klasyczne typy kont magazynu zakończą się niepowodzeniem z komunikatem o błędzie w czasie wdrażania. Upewnij się, że konto magazynu używane przez diagnostykę jest zaznaczone. Aby sprawdzić konto magazynu diagnostyki, zobacz [Konfigurowanie diagnostyki dla usług Azure Cloud Services i Virtual Machines](vs-azure-tools-diagnostics-for-cloud-services-and-virtual-machines.md). Jeśli usługa korzysta z klasycznego konta magazynu, możesz ją uaktualnić. Zobacz [uaktualnianie do konta magazynu ogólnego przeznaczenia w wersji 2](/azure/storage/common/storage-account-upgrade?tabs=azure-portal).  Aby uzyskać ogólne informacje na temat typów kont magazynu, zobacz [Omówienie konta magazynu](/azure/storage/common/storage-account-overview).

### <a name="to-publish-a-classic-azure-cloud-service-project-to-cloud-services-extended-support"></a>Aby opublikować projekt klasycznej usługi w chmurze platformy Azure do Cloud Services (obsługa rozszerzona)

1. Cloud Services (obsługa rozszerzona) jest obecnie w wersji zapoznawczej. Zarejestruj funkcję subskrypcji w następujący sposób:

   ```azurepowershell-interactive
   Register-AzProviderFeature -FeatureName CloudServices -ProviderNamespace Microsoft.Compute
   ```

1. Kliknij prawym przyciskiem myszy węzeł projektu w projekcie usługi w chmurze platformy Azure (klasyczny) i wybierz polecenie **Publikuj (obsługa rozszerzona).**.. Zostanie otwarty **Kreator publikowania** na pierwszym ekranie.

   ![Wybierz pozycję Publikuj (obsługa rozszerzona) z menu](./media/cloud-services-extended-support/publish-commands-on-menu.png)

   Zostanie wyświetlony Kreator **publikacji** .

   ![Strona logowania](./media/cloud-services-extended-support/publish-step1.png)

1. **Konto** — wybierz konto lub wybierz pozycję **Dodaj konto** z listy rozwijanej konto.

1. **Wybierz subskrypcję** — wybierz subskrypcję, która ma być używana dla danego wdrożenia.

1. Wybierz przycisk **dalej** , aby przejść do strony **ustawień** .

   ![Typowe ustawienia](./media/cloud-services-extended-support/publish-settings.png)

1. **Usługa w chmurze (obsługa rozszerzona)** — za pomocą listy rozwijanej wybierz istniejącą usługę w chmurze (rozszerzoną obsługę) lub wybierz pozycję **Utwórz nową** i utwórz ją. Centrum danych wyświetla w nawiasach dla każdej usługi w chmurze (obsługa rozszerzona). Zaleca się, aby lokalizacja centrum danych dla usługi w chmurze (obsługa rozszerzona) była taka sama, jak lokalizacja centrum danych dla konta magazynu.

   Jeśli zdecydujesz się utworzyć nową usługę, zobaczysz okno dialogowe **Tworzenie usługi w chmurze (obsługa rozszerzona)** . Określ lokalizację i grupę zasobów, której chcesz używać dla usługi w chmurze (obsługa rozszerzona).

   ![Tworzenie usługi w chmurze (obsługa rozszerzona)](./media/cloud-services-extended-support/extended-support-dialog.png)

1. **Konfiguracja kompilacji** — wybierz opcję **Debuguj** lub **Zwolnij**.

1. **Konfiguracja usługi** — wybierz **chmurę** lub **lokalną**.

1. **Konto magazynu** — wybierz konto magazynu do użycia w ramach tego wdrożenia lub **Utwórz nowe** , aby utworzyć konto magazynu. Region jest wyświetlany w nawiasach dla każdego konta magazynu. Zalecane jest, aby lokalizacja centrum danych dla konta magazynu była taka sama, jak lokalizacja centrum danych dla usługi w chmurze (typowe ustawienia).

   Konto usługi Azure Storage przechowuje pakiet dla wdrożenia aplikacji.

1. **Magazyn kluczy** — Określ Magazyn kluczy zawierający klucze tajne dla tej usługi w chmurze (obsługa rozszerzona). Ta funkcja jest włączona, jeśli pulpit zdalny jest włączony, lub jeśli do konfiguracji zostaną dodane certyfikaty.

1. **Włącz pulpit zdalny dla wszystkich ról** — wybierz tę opcję, jeśli chcesz mieć możliwość zdalnego łączenia się z usługą. Zostanie wyświetlony monit o podanie poświadczeń.

   ![Ustawienia pulpitu zdalnego](./media/cloud-services-extended-support/remote-desktop-configuration.png)

1. Wybierz przycisk **dalej** , aby przejść do strony **Ustawienia diagnostyki** .

   ![Ustawienia diagnostyki](./media/cloud-services-extended-support/diagnostics-settings.png)

   Diagnostyka umożliwia rozwiązywanie problemów z usługą w chmurze platformy Azure (obsługa rozszerzona). Aby uzyskać informacje na temat diagnostyki, zobacz [Konfigurowanie diagnostyki dla usług Azure Cloud Services i Virtual Machines](./vs-azure-tools-diagnostics-for-cloud-services-and-virtual-machines.md). Aby uzyskać informacje na temat Application Insights, zobacz [co to jest Application Insights?](/azure/application-insights/app-insights-overview).

1. Wybierz przycisk **dalej** , aby przejść do strony **Podsumowanie** .

   ![Podsumowanie](./media/cloud-services-extended-support/publish-summary.png)

1. **Profil docelowy** — możesz wybrać opcję utworzenia profilu publikowania na podstawie ustawień, które zostały wybrane. Na przykład można utworzyć jeden profil dla środowiska testowego i drugi dla produkcji. Aby zapisać ten profil, wybierz ikonę **Zapisz** . Kreator utworzy profil i zapisze go w projekcie programu Visual Studio. Aby zmodyfikować nazwę profilu, Otwórz listę **profil docelowy** , a następnie wybierz pozycję **Zarządzaj.**

   > [!Note]
   > Profil publikowania zostanie wyświetlony w Eksplorator rozwiązań w programie Visual Studio, a ustawienia profilu są zapisywane w pliku z rozszerzeniem *. azurePubxml* . Ustawienia są zapisywane jako atrybuty tagów XML.

1. Po skonfigurowaniu wszystkich ustawień wdrożenia projektu wybierz pozycję **Publikuj** w dolnej części okna dialogowego. Możesz monitorować stan procesu w oknie danych wyjściowych **dziennika aktywności platformy Azure** w programie Visual Studio. Wybierz link **Otwórz w portalu** , aby 

Gratulacje! Projekt usługi w chmurze (obsługa rozszerzona) został opublikowany na platformie Azure. Aby ponownie opublikować z tymi samymi ustawieniami, możesz użyć ponownie profilu publikowania lub Powtórz te kroki, aby utworzyć nowy. Szablon Azure Resource Manager (ARM) i parametry, które są używane do wdrożenia, są zapisywane w folderze *bin/ \<configuration\> /Publish* .

## <a name="clean-up-azure-resources"></a>Czyszczenie zasobów platformy Azure

Aby wyczyścić zasoby platformy Azure utworzone w ramach tego samouczka, przejdź do [Azure Portal](https://portal.azure.com), wybierz pozycję **grupy zasobów**, Znajdź i otwórz grupę zasobów, która została użyta do utworzenia usługi w chmurze (obsługa rozszerzona), a następnie wybierz pozycję **Usuń grupę zasobów**.

## <a name="next-steps"></a>Następne kroki

Skonfiguruj ciągłą integrację (CI) za pomocą przycisku **Konfiguruj** na ekranie **publikowania** . Aby uzyskać więcej informacji, zobacz [dokumentację Azure Pipelines](/azure/devops/pipelines/?view=azure-devops&preserve-view=true).
