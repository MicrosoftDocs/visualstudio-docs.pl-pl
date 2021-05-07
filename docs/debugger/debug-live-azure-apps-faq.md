---
title: Często zadawane pytania dotyczące debugowania migawek | Microsoft Docs
description: Zapoznaj się z listą często zadawanych pytań, które mogą pojawić się podczas debugowania aplikacji platformy Azure na żywo przy użyciu Snapshot Debugger w Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/07/2017
ms.topic: reference
helpviewer_keywords:
- debugger
ms.assetid: 944f1eb0-a74b-4d28-ae2b-a370cd869add
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 9bd8a80f7f6d11587c9f0cd5c6b9bf96e38a0a74
ms.sourcegitcommit: dd2fc6e03a789c044f8438096b8f112e4dba5557
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/06/2021
ms.locfileid: "108800500"
---
# <a name="frequently-asked-questions-for-snapshot-debugging-in-visual-studio"></a>Często zadawane pytania dotyczące debugowania migawek w programie Visual Studio

Poniżej znajduje się lista pytań, które mogą pojawić się podczas debugowania aplikacji platformy Azure na żywo przy użyciu Snapshot Debugger.

#### <a name="what-is-the-performance-cost-of-taking-a-snapshot"></a>Jaki jest koszt wydajności tworzenia migawki?

Gdy Snapshot Debugger migawkę aplikacji, powoduje to widelec procesu aplikacji i zawiesza kopię poszybową. Podczas debugowania migawki debugujesz dla kopię rozdrzewaną procesu. Ten proces trwa tylko 10–20 milisekund, ale nie kopiuje pełnego stosu aplikacji. Zamiast tego kopiuje tylko tabelę stron i ustawia strony do skopiowania podczas zapisu. Jeśli niektóre obiekty aplikacji na stercie zmienią się, odpowiednie strony zostaną skopiowane. Oznacza to, że każda migawka ma niewielki koszt w pamięci (w kolejności setek kilobajtów dla większości aplikacji).

#### <a name="what-happens-if-i-have-a-scaled-out-azure-app-service-multiple-instances-of-my-app"></a>Co się stanie, jeśli mam skalowaną w Azure App Service (wiele wystąpień mojej aplikacji)?

Jeśli masz wiele wystąpień aplikacji, punkty przyciągania są stosowane do każdego pojedynczego wystąpienia. Tylko pierwszy punkt przyciągania, który zostanie trafiony z określonymi warunkami, tworzy migawkę. Jeśli masz wiele punktów przyciągania, późniejsze migawki pochodzą z tego samego wystąpienia, które utworzyło pierwszą migawkę. Punkty dziennika wysyłane do okna danych wyjściowych będą wyświetlać tylko komunikaty z jednego wystąpienia, podczas gdy punkty dziennika wysyłane do dzienników aplikacji wysyłają komunikaty z każdego wystąpienia.

#### <a name="how-does-the-snapshot-debugger-load-symbols"></a>W jaki sposób Snapshot Debugger ładować symbole?

Aplikacja Snapshot Debugger wymaga, aby były zgodne symbole dla aplikacji lokalnie lub wdrożone w Azure App Service. (Osadzone pliki PDB nie są obecnie obsługiwane). Plik Snapshot Debugger automatycznie pobiera symbole z Azure App Service. Począwszy od Visual Studio 2017 w wersji 15.2, wdrażanie w Azure App Service wdraża również symbole aplikacji.

#### <a name="does-the-snapshot-debugger-work-against-release-builds-of-my-application"></a>Czy Snapshot Debugger działa z kompilacjami wydania mojej aplikacji?

Tak — Snapshot Debugger jest przeznaczona do pracy z kompilacjami wydania. Po umieszczeniu punktu przyciągania w funkcji funkcja jest ponownie kompilowana do wersji debugowania, dzięki czemu można ją debugować. Zatrzymanie Snapshot Debugger zwraca funkcje do wersji kompilacji wydania.

#### <a name="can-logpoints-cause-side-effects-in-my-production-application"></a>Czy punkty dziennika mogą powodować skutki uboczne w mojej aplikacji produkcyjnej?

Nie — wszystkie komunikaty dziennika, które dodajesz do aplikacji, są oceniane wirtualnie. Nie mogą one powodować żadnych efektów ubocznych w aplikacji. Jednak niektóre właściwości natywne mogą nie być dostępne z punktami dziennika.

#### <a name="does-the-snapshot-debugger-work-if-my-server-is-under-load"></a>Czy serwer Snapshot Debugger działa, jeśli mój serwer jest załadowywny?

Tak, debugowanie migawek może działać w przypadku serwerów pod obciążeniem. Funkcja Snapshot Debugger ogranicza i nie przechwytuje migawek w sytuacjach, gdy na serwerze jest mała ilość wolnej pamięci.

#### <a name="how-do-i-uninstall-the-snapshot-debugger"></a>Jak mogę odinstalować Snapshot Debugger?

Aby odinstalować rozszerzenie Snapshot Debugger lokacji na komputerze App Service, należy wykonać następujące czynności:

1. Wyłącz swoje aplikacje App Service za pomocą Eksploratora chmury w usłudze Visual Studio lub Azure Portal.
1. Przejdź do App Service Kudu twojej aplikacji (to jest Twojausługa Aplikacji).**scm**.azurewebsites.net) i przejdź do **rozszerzenia witryny**.
1. Kliknij przycisk X na Snapshot Debugger lokacji, aby go usunąć.

#### <a name="why-are-ports-opened-during-a-snapshot-debugger-session"></a>Dlaczego porty są otwierane w Snapshot Debugger sesji?

Snapshot Debugger musi otworzyć zestaw portów w celu debugowania migawek na platformie Azure, są to te same porty, które są wymagane do zdalnego debugowania. [Listę portów można znaleźć tutaj.](../debugger/remote-debugger-port-assignments.md)

#### <a name="how-do-i-disable-the-remote-debugger-extension"></a>Jak mogę wyłączyć rozszerzenie debugera zdalnego?

W App Services:
1. Wyłącz rozszerzenie zdalnego debugera za pośrednictwem Azure Portal dla App Service.
2. Azure Portal > bloku zasobów usługi Application Service > *ustawienia aplikacji*
3. Przejdź do sekcji *Debugowanie* i kliknij przycisk *Wyłącz* dla opcji *Debugowanie zdalne.*

W przypadku AKS:
1. Zaktualizuj plik Dockerfile, aby usunąć sekcje odpowiadające Visual Studio Snapshot Debugger [obrazów platformy Docker.](https://github.com/Microsoft/vssnapshotdebugger-docker)
2. Ponownie skompilować i ponownie wdązywać zmodyfikowany obraz platformy Docker.

W przypadku maszyn wirtualnych/zestawów skalowania maszyn wirtualnych usuń rozszerzenie debugera zdalnego, certyfikaty, magazyny kluczy i pule NAT dla ruchu przychodzącego w następujący sposób:

1. Usuwanie rozszerzenia zdalnego debugera

   Istnieje kilka sposobów wyłączania zdalnego debugera dla maszyn wirtualnych i zestawów skalowania maszyn wirtualnych:

      - Wyłączanie zdalnego debugera za pośrednictwem eksploratora chmury

         - Usługa Cloud Explorer > zasobów maszyny wirtualnej i > debugowanie (wyłączanie debugowania nie istnieje dla zestawu skalowania maszyn wirtualnych w eksploratorze chmury).

      - Wyłączanie zdalnego debugera za pomocą skryptów/poleceń cmdlet programu PowerShell

         Dla maszyny wirtualnej:

         ```powershell
         Remove-AzVMExtension -ResourceGroupName $rgName -VMName $vmName -Name Microsoft.VisualStudio.Azure.RemoteDebug.VSRemoteDebugger
         ```

         W przypadku zestawów skalowania maszyn wirtualnych:

         ```powershell
         $vmss = Get-AzVmss -ResourceGroupName $rgName -VMScaleSetName $vmssName
         $extension = $vmss.VirtualMachineProfile.ExtensionProfile.Extensions | Where {$_.Name.StartsWith('VsDebuggerService')} | Select -ExpandProperty Name
         Remove-AzVmssExtension -VirtualMachineScaleSet $vmss -Name $extension
         ```

      - Wyłącz debuger zdalny za pośrednictwem Azure Portal
         - Azure Portal > bloku zasobów zestawy skalowania maszyn wirtualnych/maszyn wirtualnych > rozszerzenia
         - Odinstaluj rozszerzenie Microsoft.VisualStudio.Azure.RemoteDebug.VSRemoteDebugger

         > [!NOTE]
         > Zestawy skalowania maszyn wirtualnych — portal nie zezwala na usuwanie portów DebuggerListener. Konieczne będzie użycie Azure PowerShell. Aby uzyskać szczegółowe informacje, zobacz poniżej.

2. Usuwanie certyfikatów i usługi Azure KeyVault

   Podczas instalowania rozszerzenia debugera zdalnego dla maszyny wirtualnej lub zestawów skalowania maszyn wirtualnych są tworzone certyfikaty klienta i serwera w celu uwierzytelnienia klienta usługi Visual Studio za pomocą zasobów usługi Azure Virtual Machine/virtual machine scale sets.

   - Certyfikat klienta

      Ten certyfikat jest certyfikatem z podpisem własnym, który znajduje się w Cert:/CurrentUser/My/

      ```
      Thumbprint                                Subject
      ----------                                -------

      1234123412341234123412341234123412341234  CN=ResourceName
      ```

      Jednym ze sposobów usunięcia tego certyfikatu z komputera jest za pomocą programu PowerShell

      ```powershell
      $ResourceName = 'ResourceName' # from above
      Get-ChildItem -Path Cert:\CurrentUser\My | Where-Object {$_.Subject -match $ResourceName} | Remove-Item
      ```

   - Certyfikat serwera
      - Odpowiedni odcisk palca certyfikatu serwera jest wdrażany jako klucz tajny w usłudze Azure KeyVault. Visual Studio spróbuje znaleźć lub utworzyć usługę KeyVault z prefiksem MSVSAZ* w regionie odpowiadającym zasobowi maszyny wirtualnej lub zestawu skalowania maszyn wirtualnych. W związku z tym wszystkie zasoby maszyn wirtualnych lub zestawów skalowania maszyn wirtualnych wdrożone w tym regionie będą współużytkować ten sam program KeyVault.
      - Aby usunąć klucz tajny odcisku palca certyfikatu serwera, przejdź do Azure Portal i znajdź usługę MSVSAZ* KeyVault w tym samym regionie, w którym hostowany jest zasób. Usuń klucz tajny, który powinien być oznaczony etykietą `remotedebugcert<<ResourceName>>`
      - Musisz również usunąć klucz tajny serwera z zasobu za pomocą programu PowerShell.

      W przypadku maszyn wirtualnych:

      ```powershell
      $vm.OSProfile.Secrets[0].VaultCertificates.Clear()
      Update-AzVM -ResourceGroupName $rgName -VM $vm
      ```

      W przypadku zestawów skalowania maszyn wirtualnych:

      ```powershell
      $vmss.VirtualMachineProfile.OsProfile.Secrets[0].VaultCertificates.Clear()
      Update-AzVmss -ResourceGroupName $rgName -VMScaleSetName $vmssName -VirtualMachineScaleSet $vmss
      ```

3. Usuń wszystkie pule NAT dla ruchu przychodzącego debuggerListener (tylko zestaw skalowania maszyn wirtualnych)

   Debuger zdalny wprowadza powiązane pule NAT debuggerListener, które są stosowane do usługi równoważenia obciążenia zestawu skalowania.

   ```powershell
   $inboundNatPools = $vmss.VirtualMachineProfile.NetworkProfile.NetworkInterfaceConfigurations.IpConfigurations.LoadBalancerInboundNatPools
   $inboundNatPools.RemoveAll({ param($pool) $pool.Id.Contains('inboundNatPools/DebuggerListenerNatPool-') }) | Out-Null

   if ($LoadBalancerName)
   {
      $lb = Get-AzLoadBalancer -ResourceGroupName $ResourceGroup -name $LoadBalancerName
      $lb.FrontendIpConfigurations[0].InboundNatPools.RemoveAll({ param($pool) $pool.Id.Contains('inboundNatPools/DebuggerListenerNatPool-') }) | Out-Null
      Set-AzLoadBalancer -LoadBalancer $lb
   }
   ```

#### <a name="how-do-i-disable-snapshot-debugger"></a>Jak mogę wyłączyć Snapshot Debugger?

W App Service:
1. Wyłącz Snapshot Debugger za pośrednictwem Azure Portal dla App Service.
2. Azure Portal > bloku zasobów usługi Application Service > *ustawienia aplikacji*
3. Usuń następujące ustawienia aplikacji w Azure Portal i zapisz zmiany.
   - INSTRUMENTATIONENGINE_EXTENSION_VERSION
   - SNAPSHOTDEBUGGER_EXTENSION_VERSION

   > [!WARNING]
   > Wszelkie zmiany ustawień aplikacji zainicjują ponowne uruchomienie aplikacji. Aby uzyskać więcej informacji na temat ustawień aplikacji, [zobacz Konfigurowanie App Service aplikacji w Azure Portal](/azure/app-service/web-sites-configure).

W przypadku AKS:
1. Zaktualizuj plik Dockerfile, aby usunąć sekcje odpowiadające Visual Studio Snapshot Debugger [obrazów platformy Docker.](https://github.com/Microsoft/vssnapshotdebugger-docker)
2. Ponownie skompilować i ponownie wdązywać zmodyfikowany obraz platformy Docker.

W przypadku zestawów skalowania maszyn wirtualnych::

Istnieje kilka sposobów wyłączania Snapshot Debugger:
- Eksplorator chmury > zasobów zestawu skalowania maszyn wirtualnych i maszyn wirtualnych > wyłącz diagnostykę

- Azure Portal > zasobu maszyny wirtualnej/zestawu skalowania maszyn wirtualnych > Rozszerzenia > Odinstaluj rozszerzenie Microsoft.Insights.VMDiagnosticsSettings

- Polecenia cmdlet programu PowerShell z [az programu PowerShell](/powershell/azure/overview)

   Maszyna wirtualna:

   ```powershell
      Remove-AzVMExtension -ResourceGroupName $rgName -VMName $vmName -Name Microsoft.Insights.VMDiagnosticsSettings
   ```

   Zestawy skalowania maszyn wirtualnych:

   ```powershell
      $vmss = Get-AzVmss -ResourceGroupName $rgName -VMScaleSetName $vmssName
      Remove-AzVmssExtension -VirtualMachineScaleSet $vmss -Name Microsoft.Insights.VMDiagnosticsSettings
   ```

## <a name="see-also"></a>Zobacz też

- [Debugowanie w Visual Studio](../debugger/index.yml)
- [Debugowanie aplikacji ASP.NET na żywo przy użyciu Snapshot Debugger](../debugger/debug-live-azure-applications.md)
- [Debugowanie zestawów skalowania ASP.NET usługi Azure Virtual Machines\Virtual Machines przy użyciu Snapshot Debugger](../debugger/debug-live-azure-virtual-machines.md)
- [Debugowanie dzienników ASP.NET azure Kubernetes przy użyciu narzędzia Snapshot Debugger](../debugger/debug-live-azure-kubernetes.md)
- [Rozwiązywanie problemów i znane problemy dotyczące debugowania migawek](../debugger/debug-live-azure-apps-troubleshooting.md)
