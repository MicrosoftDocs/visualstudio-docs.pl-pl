---
title: Często zadawane pytania dotyczące debugowania migawek | Microsoft Docs
ms.date: 11/07/2017
ms.topic: reference
helpviewer_keywords:
- debugger
ms.assetid: 944f1eb0-a74b-4d28-ae2b-a370cd869add
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5e0d8839daac2d470f4275257bfcfbc83fc7a62f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "72911404"
---
# <a name="frequently-asked-questions-for-snapshot-debugging-in-visual-studio"></a>Często zadawane pytania dotyczące debugowania migawek w programie Visual Studio

Poniżej znajduje się lista pytań, które mogą wystąpić podczas debugowania aktywnych aplikacji platformy Azure przy użyciu Snapshot Debugger.

#### <a name="what-is-the-performance-cost-of-taking-a-snapshot"></a>Jaki jest koszt wydajności tworzenia migawki?

Gdy Snapshot Debugger przechwytuje migawkę aplikacji, rozwidlenie procesu aplikacji i wstrzymuje kopiowanie do rozwidlenia. Podczas debugowania migawki jest debugowana w odniesieniu do rozwidlenia kopii procesu. Ten proces trwa tylko 10-20 milisekund, ale nie kopiuje pełnego sterty aplikacji. Zamiast tego kopiuje tylko tabelę stron i ustawia strony do kopiowania przy zapisie. Jeśli niektóre obiekty aplikacji na stercie zmienią się, ich odpowiednie strony zostaną skopiowane. W tej serwatki każda migawka ma mały koszt w pamięci (w kolejności setek kilobajtów dla większości aplikacji).

#### <a name="what-happens-if-i-have-a-scaled-out-azure-app-service-multiple-instances-of-my-app"></a>Co się stanie, jeśli mam Azure App Service skalowania w poziomie (wiele wystąpień aplikacji)?

Jeśli masz wiele wystąpień aplikacji, punkty przyciągania je zastosować do każdego pojedynczego wystąpienia. Tylko pierwszy punkt przyciągania do osiągnięcia z określonymi warunkami tworzy migawkę. Jeśli masz wiele punkty przyciągania, późniejsze migawki pochodzą z tego samego wystąpienia, które utworzyło pierwszą migawkę. Punkty rejestrowania wysyłane do okna danych wyjściowych będzie zawierać tylko komunikaty z jednego wystąpienia, podczas gdy punkty rejestrowania wysyłane do dzienników aplikacji wysyła komunikaty z każdego wystąpienia.

#### <a name="how-does-the-snapshot-debugger-load-symbols"></a>Jak są Snapshot Debugger symbole ładowania?

Snapshot Debugger wymaga posiadania pasujących symboli dla aplikacji lokalnie lub wdrożonej w Azure App Service. (Osadzone plików PDB nie są obecnie obsługiwane). Snapshot Debugger automatycznie pobiera symbole z Azure App Service. Począwszy od programu Visual Studio 2017 w wersji 15,2, wdrożenie do Azure App Service również wdraża symbole aplikacji.

#### <a name="does-the-snapshot-debugger-work-against-release-builds-of-my-application"></a>Czy Snapshot Debugger działa w przypadku kompilacji wydania mojej aplikacji?

Tak — Snapshot Debugger jest przeznaczony do pracy z kompilacjami wydań. Gdy punkt przyciągania jest umieszczany w funkcji, funkcja jest ponownie kompilowana z powrotem do wersji debugowania, dzięki czemu możliwością debugowania. Zatrzymywanie Snapshot Debugger zwraca funkcje do wersji kompilacji wydania.

#### <a name="can-logpoints-cause-side-effects-in-my-production-application"></a>Czy punkty rejestrowania może spowodować skutki uboczne w mojej aplikacji produkcyjnej?

Nie — wszystkie komunikaty dziennika dodawane do aplikacji są oceniane praktycznie. Nie mogą one spowodować żadnych efektów ubocznych w aplikacji. Niektóre właściwości macierzyste mogą jednak być niedostępne dla punkty rejestrowania.

#### <a name="does-the-snapshot-debugger-work-if-my-server-is-under-load"></a>Czy Snapshot Debugger działa, jeśli mój serwer jest w trakcie ładowania?

Tak, debugowanie migawek może współpracować z serwerami w ramach obciążenia. Snapshot Debugger ogranicza i nie przechwytuje migawek w sytuacjach, gdy na serwerze istnieje niska ilość wolnej pamięci.

#### <a name="how-do-i-uninstall-the-snapshot-debugger"></a>Jak mogę odinstalować Snapshot Debugger?

Na App Service można odinstalować rozszerzenie witryny Snapshot Debugger, wykonując następujące czynności:

1. Wyłącz App Service za pomocą programu Cloud Explorer w programie Visual Studio lub Azure Portal.
1. Przejdź do witryny kudu App Service (czyli yourappservice.** SCM**. azurewebsites.NET) i przejdź do **rozszerzeń witryny**.
1. Kliknij przycisk X na rozszerzeniu witryny Snapshot Debugger, aby go usunąć.

#### <a name="why-are-ports-opened-during-a-snapshot-debugger-session"></a>Dlaczego porty są otwierane podczas sesji Snapshot Debugger?

Snapshot Debugger musi otworzyć zestaw portów w celu debugowania migawek wykonanych na platformie Azure, które są tymi samymi portami, które są wymagane do zdalnego debugowania. [Listę portów można znaleźć tutaj](../debugger/remote-debugger-port-assignments.md).

#### <a name="how-do-i-disable-the-remote-debugger-extension"></a>Jak mogę wyłączyć rozszerzenie debugera zdalnego?

Dla App Services:
1. Wyłącz rozszerzenie debugera zdalnego za pomocą Azure Portal App Service.
2. Azure Portal > bloku zasobów usługi aplikacji > *ustawień aplikacji*
3. Przejdź do sekcji *debugowanie* , a następnie kliknij przycisk *off (Wyłącz* ) dla *debugowania zdalnego*.

Dla AKS:
1. Zaktualizuj pliku dockerfile, aby usunąć sekcje odpowiadające [Visual Studio Snapshot Debugger na obrazach platformy Docker](https://github.com/Microsoft/vssnapshotdebugger-docker).
2. Kompiluj ponownie i Wdróż zmodyfikowany obraz platformy Docker.

W przypadku maszyn wirtualnych i zestawów skalowania maszyn wirtualnych Usuń rozszerzenie debugera zdalnego, certyfikaty, magazyny kluczy i pule NAT dla ruchu przychodzącego w następujący sposób:

1. Usuń rozszerzenie debugera zdalnego

   Istnieje kilka sposobów wyłączenia zdalnego debugera dla maszyn wirtualnych i zestawów skalowania maszyn wirtualnych:

      - Wyłączanie debugera zdalnego za pomocą programu Cloud Explorer

         - W programie Cloud Explorer > zasobów maszyny wirtualnej > wyłączenie debugowania (wyłączenie debugowania nie istnieje dla zestawu skalowania maszyn wirtualnych w Eksploratorze chmury).

      - Wyłącz zdalny debuger za pomocą skryptów/poleceń cmdlet programu PowerShell

         Dla maszyny wirtualnej:

         ```powershell
         Remove-AzVMExtension -ResourceGroupName $rgName -VMName $vmName -Name Microsoft.VisualStudio.Azure.RemoteDebug.VSRemoteDebugger
         ```

         Dla zestawów skalowania maszyn wirtualnych:

         ```powershell
         $vmss = Get-AzVmss -ResourceGroupName $rgName -VMScaleSetName $vmssName
         $extension = $vmss.VirtualMachineProfile.ExtensionProfile.Extensions | Where {$_.Name.StartsWith('VsDebuggerService')} | Select -ExpandProperty Name
         Remove-AzVmssExtension -VirtualMachineScaleSet $vmss -Name $extension
         ```

      - Wyłącz zdalny debuger za pomocą Azure Portal
         - Azure Portal > bloku zasobów maszyny wirtualnej/zestawu skalowania maszyn wirtualnych > rozszerzenia
         - Odinstaluj rozszerzenie Microsoft. VisualStudio. Azure. RemoteDebug. VSRemoteDebugger

         > [!NOTE]
         > Zestawy skalowania maszyn wirtualnych — Portal nie zezwala na usuwanie portów DebuggerListener. Musisz użyć Azure PowerShell. Aby uzyskać szczegółowe informacje, zobacz poniżej.

2. Usuń certyfikaty i Magazyn kluczy platformy Azure

   Podczas instalowania rozszerzenia debugera zdalnego dla maszyny wirtualnej lub zestawu skalowania maszyn wirtualnych można utworzyć zarówno certyfikaty klienta, jak i serwera, aby uwierzytelniać klienta programu VS przy użyciu zasobów maszyn wirtualnych platformy Azure/zestawów skalowania maszyn wirtualnych.

   - Certyfikat klienta

      Ten certyfikat jest certyfikatem z podpisem własnym znajdującym się w certyfikacie:/CurrentUser/my/

      ```
      Thumbprint                                Subject
      ----------                                -------

      1234123412341234123412341234123412341234  CN=ResourceName
      ```

      Jednym ze sposobów usunięcia tego certyfikatu z komputera jest za pośrednictwem programu PowerShell

      ```powershell
      $ResourceName = 'ResourceName' # from above
      Get-ChildItem -Path Cert:\CurrentUser\My | Where-Object {$_.Subject -match $ResourceName} | Remove-Item
      ```

   - Certyfikat serwera
      - Odpowiedni odcisk palca certyfikatu serwera jest wdrażany jako klucz tajny magazynu kluczy platformy Azure. Program VS podejmie próbę znalezienia lub utworzenia magazynu kluczy z prefiksem MSVSAZ * w regionie odpowiadającym zasobie maszyny wirtualnej lub zestawu skalowania maszyn wirtualnych. Wszystkie zasoby maszyn wirtualnych i zestawów skalowania maszyn wirtualnych wdrożone w tym regionie będą współużytkować ten sam magazyn kluczy.
      - Aby usunąć wpis tajny odcisku palca certyfikatu serwera, przejdź do Azure Portal i Znajdź Magazyn kluczy MSVSAZ * w tym samym regionie, w którym znajduje się zasób. Usuń klucz tajny, który powinien być oznaczony etykietą `remotedebugcert<<ResourceName>>`
      - Należy również usunąć klucz tajny serwera z zasobu za pośrednictwem programu PowerShell.

      Dla maszyn wirtualnych:

      ```powershell
      $vm.OSProfile.Secrets[0].VaultCertificates.Clear()
      Update-AzVM -ResourceGroupName $rgName -VM $vm
      ```

      Dla zestawów skalowania maszyn wirtualnych:

      ```powershell
      $vmss.VirtualMachineProfile.OsProfile.Secrets[0].VaultCertificates.Clear()
      Update-AzVmss -ResourceGroupName $rgName -VMScaleSetName $vmssName -VirtualMachineScaleSet $vmss
      ```

3. Usuń wszystkie DebuggerListener przychodzące pule NAT (tylko zestaw skalowania maszyn wirtualnych)

   Zdalny debuger wprowadza DebuggerListener w powiązane pule NAT, które są stosowane do modułu równoważenia obciążenia zestawu skalowania.

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

Dla App Service:
1. Wyłącz Snapshot Debugger za pośrednictwem Azure Portal App Service.
2. Azure Portal > bloku zasobów usługi aplikacji > *ustawień aplikacji*
3. Usuń następujące ustawienia aplikacji z Azure Portal i Zapisz zmiany.
   - INSTRUMENTATIONENGINE_EXTENSION_VERSION
   - SNAPSHOTDEBUGGER_EXTENSION_VERSION

   > [!WARNING]
   > Wszelkie zmiany ustawień aplikacji spowodują zainicjowanie ponownego uruchomienia aplikacji. Aby uzyskać więcej informacji na temat ustawień aplikacji, zobacz [Konfigurowanie aplikacji App Service w Azure Portal](/azure/app-service/web-sites-configure).

Dla AKS:
1. Zaktualizuj pliku dockerfile, aby usunąć sekcje odpowiadające [Visual Studio Snapshot Debugger na obrazach platformy Docker](https://github.com/Microsoft/vssnapshotdebugger-docker).
2. Kompiluj ponownie i Wdróż zmodyfikowany obraz platformy Docker.

W przypadku maszyn wirtualnych i zestawów skalowania maszyn wirtualnych:

Istnieje kilka sposobów wyłączenia Snapshot Debugger:
- Program Cloud Explorer > swoją maszynę wirtualną/zasób zestawu skalowania maszyn wirtualnych > wyłączyć diagnostykę

- Azure Portal > bloku zasobów maszyny wirtualnej/zestawu skalowania maszyn wirtualnych > rozszerzenia > Odinstaluj rozszerzenie Microsoft. Insights. VMDiagnosticsSettings

- Polecenia cmdlet programu PowerShell z programu [AZ PowerShell](/powershell/azure/overview)

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
- [Debuguj aplikacje Live ASP.NET przy użyciu Snapshot Debugger](../debugger/debug-live-azure-applications.md)
- [Debuguj zestawy skalowania maszyn wirtualnych ASP.NET platformy Azure na żywo przy użyciu Snapshot Debugger](../debugger/debug-live-azure-virtual-machines.md)
- [Debuguj Live ASP.NET Azure Kubernetes przy użyciu Snapshot Debugger](../debugger/debug-live-azure-kubernetes.md)
- [Rozwiązywanie problemów i znane problemy związane z debugowaniem migawek](../debugger/debug-live-azure-apps-troubleshooting.md)
