---
title: Często zadawane pytania dotyczące debugowania migawek | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: 43b76ad81a2c075a11ff55dcbd7fbc5e8a4b3fe7
ms.sourcegitcommit: ba5e072c9fedeff625a1332f22dcf3644d019f51
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/31/2019
ms.locfileid: "66431842"
---
# <a name="frequently-asked-questions-for-snapshot-debugging-in-visual-studio"></a>Często zadawane pytania dotyczące debugowania migawek w programie Visual Studio

Poniżej przedstawiono listę pytań, które mogą się podczas debugowania na żywo aplikacji platformy Azure przy użyciu rozszerzenia Snapshot Debugger.

#### <a name="what-is-the-performance-cost-of-taking-a-snapshot"></a>Co to jest to koszt wydajności wykonywania migawki?

Po przechwyceniu przez rozszerzenie Snapshot Debugger migawkę aplikacji rozwidlenia procesu aplikacji i wstrzymuje rozwidlone kopiowania. Podczas debugowania migawki debugowania względem rozwidlone kopię procesu. Ten proces zajmuje tylko 10-20 MS, ale nie obejmuje kopiowania pełnego stosu aplikacji. Zamiast tego kopiuje tabeli strony i ustawia strony, aby skopiować przy zapisie. Jeśli niektóre obiekty aplikacji w przypadku zmiany sterty odpowiednich stronach są kopiowane. To serwatki każda migawka zawiera małe w pamięci kosztów (rzędu kilku setki kilobajtów dla większości aplikacji).

#### <a name="what-happens-if-i-have-a-scaled-out-azure-app-service-multiple-instances-of-my-app"></a>Co się dzieje w przypadku skalowania w poziomie w usłudze Azure App Service (wiele wystąpień aplikacji)?

Jeśli masz wiele wystąpień aplikacji, punkty przyciągania stosowane do każdego pojedynczego wystąpienia. Tylko pierwszy punkt przyciągania, aby trafić warunkom określonym tworzy migawkę. Jeśli masz wiele punktów przyciągania, nowsze migawek pochodzą z tego samego wystąpienia, jak utworzyć pierwszą migawką. Punkty rejestrowania wysyłany do okna danych wyjściowych będzie wyświetlana tylko komunikaty z jednego wystąpienia, gdy punkty rejestrowania wysyłane do dzienników aplikacji wysyłanie komunikatów z każdego wystąpienia.

#### <a name="how-does-the-snapshot-debugger-load-symbols"></a>Jak rozszerzenie Snapshot Debugger załadować symbole?

Rozszerzenie Snapshot Debugger wymaga posiadania pasujących symboli dla aplikacji lokalnych lub wdrożony do usługi Azure App Service. (Osadzonych plików PDB obecnie nie są obsługiwane.) Rozszerzenie Snapshot Debugger automatycznie pobiera symbole z usługi Azure App Service. Począwszy od programu Visual Studio 2017 wersja 15.2, wdrażanie w usłudze Azure App Service wdraża symbole Twojej aplikacji.

#### <a name="does-the-snapshot-debugger-work-against-release-builds-of-my-application"></a>Rozszerzenie Snapshot Debugger działa dla kompilacji wydania mojej aplikacji?

Tak — rozszerzenie Snapshot Debugger jest przeznaczony do pracy dla kompilacji wydania. Gdy punktu przyciągania jest umieszczany w funkcji, funkcja jest ponownie kompilowana do wersji debugowania, dzięki czemu debugowania. Zatrzymywanie rozszerzenia Snapshot Debugger zwraca funkcje do wersji kompilacji wydania.

#### <a name="can-logpoints-cause-side-effects-in-my-production-application"></a>Punkty rejestrowania może spowodować skutki uboczne w mojej aplikacji produkcyjnych?

Nie — komunikaty dziennika, dodanych do aplikacji są przetwarzane niemal. Nie spowodują one wszelkie efekty uboczne w aplikacji. Jednak niektóre właściwości natywne mogą być niedostępne z punkty rejestrowania.

#### <a name="does-the-snapshot-debugger-work-if-my-server-is-under-load"></a>Rozszerzenie Snapshot Debugger działa Jeśli mój serwer znajduje się pod obciążeniem?

Tak, debugowanie migawki można pracować na serwerach w warunkach obciążenia. Rozszerzenie Snapshot Debugger ogranicza i nie przechwytywania migawek w sytuacjach, gdy istnieje małą ilością wolnej pamięci na serwerze.

#### <a name="how-do-i-uninstall-the-snapshot-debugger"></a>Jak odinstalować rozszerzenie Snapshot Debugger?

Możesz odinstalować rozszerzenie witryny Snapshot Debugger w usłudze App Service wykonując następujące kroki:

1. Wyłącz usługi App Service za pomocą Eksploratora chmury w programie Visual Studio lub witryny Azure portal.
1. Przejdź do witryny Kudu usługi App Service (czyli yourappservice. **Menedżer sterowania usługami**. azurewebsites.net) i przejdź do **rozszerzeń witryny**.
1. Kliknij przycisk X w rozszerzenie witryny Snapshot Debugger go usunąć.

#### <a name="why-are-ports-opened-during-a-snapshot-debugger-session"></a>Dlaczego porty są otwarte w trakcie sesji rozszerzenia Snapshot Debugger

Rozszerzenie Snapshot Debugger musi otworzyć zestawu portów w celu debugowania migawki wykonane na platformie Azure, są tego samego porty wymagane do zdalnego debugowania. [Listę portów, w tym miejscu można znaleźć](../debugger/remote-debugger-port-assignments.md).

#### <a name="how-do-i-disable-the-remote-debugger-extension"></a>Jak wyłączyć rozszerzenie zdalnego debugera?

W przypadku usług aplikacji:
1. Wyłącz rozszerzenia zdalny debuger za pośrednictwem witryny Azure portal dla usługi App Service.
2. Witryna Azure portal > Blok zasobu usługi aplikacji > *ustawień aplikacji*
3. Przejdź do *debugowanie* sekcji, a następnie kliknij przycisk *poza* przycisku *zdalne debugowanie*.

Dla usługi AKS:
1. Aktualizacja z pliku Dockerfile, aby usunąć sekcje odpowiadające [Visual Studio Snapshot Debugger w obrazach Docker](https://github.com/Microsoft/vssnapshotdebugger-docker).
2. Ponownie skompiluj i wdróż zmodyfikowany obraz Docker.

Do skalowania maszyn wirtualnych/maszyna wirtualna zestawy Usuń pule KeyVaults i ruchu przychodzącego NAT rozszerzenie, certyfikaty, zdalny debuger w następujący sposób:

1. Usuń rozszerzenie debugera zdalnego  

   Istnieje kilka sposobów, aby wyłączyć zdalnego debugera dla maszyn wirtualnych i zestawów skalowania maszyn wirtualnych:  

      - Wyłącz zdalnego debugera za pomocą Eksploratora chmury  

         - Eksplorator chmury > zasobu maszyny wirtualnej > Wyłącz debugowanie (Wyłączanie debugowania nie istnieje dla zestawu w programie Cloud Explorer skalowania maszyn wirtualnych).  


      - Wyłącz zdalnego debugera za pomocą skryptów/poleceń cmdlet programu PowerShell  

         Dla maszyny wirtualnej:  

         ```
         Remove-AzVMExtension -ResourceGroupName $rgName -VMName $vmName -Name Microsoft.VisualStudio.Azure.RemoteDebug.VSRemoteDebugger  
         ```

         Dla zestawów skalowania maszyn wirtualnych:  
         ```
         $vmss = Get-AzVmss -ResourceGroupName $rgName -VMScaleSetName $vmssName  
         $extension = $vmss.VirtualMachineProfile.ExtensionProfile.Extensions | Where {$_.Name.StartsWith('VsDebuggerService')} | Select -ExpandProperty Name  
         Remove-AzVmssExtension -VirtualMachineScaleSet $vmss -Name $extension  
         ```

      - Wyłącz zdalnego debugera w witrynie Azure portal
         - Witryna Azure portal > Twojej maszyny wirtualnej/wirtualnego machine scale sets z bloku zasobów > rozszerzenia  
         - Odinstaluj rozszerzenie Microsoft.VisualStudio.Azure.RemoteDebug.VSRemoteDebugger  


         > [!NOTE]
         > Zestawy skalowania maszyn wirtualnych — portalu nie zezwala na usuwanie porty DebuggerListener. Należy użyć programu Azure PowerShell. Zobacz szczegóły poniżej.
  
2. Usuń certyfikaty i usługa Azure KeyVault

   Podczas instalowania rozszerzenia debugera zdalnego dla maszyny wirtualnej lub zestawy skalowania maszyn wirtualnych, certyfikaty klienta i serwera są tworzone do uwierzytelniania klienta w PORÓWNANIU z maszyny wirtualnej platformy Azure lub zasobów zestawów skalowania maszyn wirtualnych.  

   - Certyfikat klienta  

      Ten certyfikat jest certyfikat z podpisem własnym na terenie Cert: / CurrentUser/Moje /  

      ```
      Thumbprint                                Subject  
      ----------                                -------  

      1234123412341234123412341234123412341234  CN=ResourceName  
      ```

      Jednym ze sposobów, aby usunąć ten certyfikat z Twojego komputera jest za pomocą programu PowerShell

      ```
      $ResourceName = 'ResourceName' # from above  
      Get-ChildItem -Path Cert:\CurrentUser\My | Where-Object {$_.Subject -match $ResourceName} | Remove-Item  
      ```

   - Certyfikat serwera
      - Odpowiednie odcisk palca certyfikatu serwera jest wdrażany jako wpis tajny do magazynu kluczy Azure. VS spróbuje znaleźć lub utworzyć magazynu kluczy z prefiksem MSVSAZ * w regionie odpowiadające maszynie wirtualnej lub zasobie zestawów skalowania maszyn wirtualnych. Wszystkie maszyny wirtualnej lub maszyny wirtualnej zestawów skalowania zasobów, w którym wdrożona w związku z tym współużytkują ten sam magazyn kluczy.  
      - Aby usunąć wpis tajny odcisk palca dla certyfikatu serwera, przejdź do witryny Azure portal i Znajdź KeyVault MSVSAZ * w tym samym regionie, który jest hostem zasobu. Usuń klucz tajny, który powinien być oznaczony jako `remotedebugcert<<ResourceName>>`  
      - Należy również usunąć tajnego klucza serwera z zasobu za pomocą programu PowerShell.  

      W przypadku maszyn wirtualnych:  

      ```
      $vm.OSProfile.Secrets[0].VaultCertificates.Clear()  
      Update-AzVM -ResourceGroupName $rgName -VM $vm  
      ```
                        
      Dla zestawów skalowania maszyn wirtualnych:  

      ```
      $vmss.VirtualMachineProfile.OsProfile.Secrets[0].VaultCertificates.Clear()  
      Update-AzVmss -ResourceGroupName $rgName -VMScaleSetName $vmssName -VirtualMachineScaleSet $vmss  
      ```
                        
3. Usuń wszystkie pule translatora adresów Sieciowych dla ruchu przychodzącego DebuggerListener (tylko zestaw skalowania maszyn wirtualnych)  

   Zdalny debuger wprowadza DebuggerListener pule translatora adresów Sieciowych przychodzącego, które są stosowane do modułu równoważenia obciążenia z zestawu skalowania.  

   ```
   $inboundNatPools = $vmss.VirtualMachineProfile.NetworkProfile.NetworkInterfaceConfigurations.IpConfigurations.LoadBalancerInboundNatPools  
   $inboundNatPools.RemoveAll({ param($pool) $pool.Id.Contains('inboundNatPools/DebuggerListenerNatPool-') }) | Out-Null  
                
   if ($LoadBalancerName)  
   {
      $lb = Get-AzLoadBalancer -ResourceGroupName $ResourceGroup -name $LoadBalancerName  
      $lb.FrontendIpConfigurations[0].InboundNatPools.RemoveAll({ param($pool) $pool.Id.Contains('inboundNatPools/DebuggerListenerNatPool-') }) | Out-Null  
      Set-AzLoadBalancer -LoadBalancer $lb  
   }
   ```

#### <a name="how-do-i-disable-snapshot-debugger"></a>Jak wyłączyć rozszerzenie Snapshot Debugger?

Dla usługi App Service:
1. Wyłącz rozszerzenia Snapshot Debugger w witrynie Azure portal dla usługi App Service.
2. Witryna Azure portal > Blok zasobu usługi aplikacji > *ustawień aplikacji*
3. Usuń następujące ustawienia aplikacji w witrynie Azure portal, a następnie zapisz zmiany. 
    - INSTRUMENTATIONENGINE_EXTENSION_VERSION
    - SNAPSHOTDEBUGGER_EXTENSION_VERSION

    > [!WARNING]
    > Zmiany w ustawieniach aplikacji zostanie zainicjowana ponowne uruchomienie aplikacji. Szczegółowe informacje o ustawieniach aplikacji można znaleźć [tutaj](https://docs.microsoft.com/azure/app-service/web-sites-configure#app-settings). 

Dla usługi AKS:
1. Aktualizacja z pliku Dockerfile, aby usunąć sekcje odpowiadające [Visual Studio Snapshot Debugger w obrazach Docker](https://github.com/Microsoft/vssnapshotdebugger-docker).
2. Ponownie skompiluj i wdróż zmodyfikowany obraz Docker.

Dla zestawów skalowania maszyn wirtualnych/maszyna wirtualna:

Istnieje kilka sposobów, aby wyłączyć rozszerzenia Snapshot Debugger:
- Eksplorator chmury > zasobów w zestawie skalowania maszyn wirtualnych/maszyna wirtualna > Wyłącz diagnostyki

- Witryna Azure portal > bloku zasobów w zestawie skalowania maszyn wirtualnych/maszyna wirtualna > Rozszerzenia > Microsoft.Insights.VMDiagnosticsSettings odinstalować rozszerzenie

- Polecenia cmdlet programu PowerShell z [Az programu PowerShell](https://docs.microsoft.com/powershell/azure/overview)

    Maszyna wirtualna:
    ```
        Remove-AzVMExtension -ResourceGroupName $rgName -VMName $vmName -Name Microsoft.Insights.VMDiagnosticsSettings 
    ```
    
    Zestawy skalowania maszyn wirtualnych:
    ```
        $vmss = Get-AzVmss -ResourceGroupName $rgName -VMScaleSetName $vmssName
        Remove-AzVmssExtension -VirtualMachineScaleSet $vmss -Name Microsoft.Insights.VMDiagnosticsSettings
    ```

## <a name="see-also"></a>Zobacz także

- [Debugowanie w programie Visual Studio](../debugger/index.md)
- [Debugowanie na żywo aplikacji ASP.NET, przy użyciu rozszerzenia Snapshot Debugger](../debugger/debug-live-azure-applications.md)
- [Debugowanie na żywo maszyn wirtualnych Machines\Virtual Azure ASP.NET scale sets przy użyciu rozszerzenia Snapshot Debugger](../debugger/debug-live-azure-virtual-machines.md)
- [Debugowanie na żywo ASP.NET Azure Kubernetes za pomocą rozszerzenia Snapshot Debugger](../debugger/debug-live-azure-kubernetes.md)
- [Rozwiązywanie problemów i znane problemy dotyczące debugowania migawek](../debugger/debug-live-azure-apps-troubleshooting.md)