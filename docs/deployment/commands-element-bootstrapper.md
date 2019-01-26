---
title: '&lt;Polecenia&gt; — Element (program inicjujący) | Dokumentacja firmy Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- <Commands> element [bootstrapper]
ms.assetid: e61d5787-fe1f-4ebf-b0cf-0d7909be7ffb
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: eab1e5d8ab9a4e1644c8eb1a99d1aab4fdf6d9e0
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "54928077"
---
# <a name="ltcommandsgt-element-bootstrapper"></a>&lt;Polecenia&gt; — element (program inicjujący)
`Commands` Element implementuje badania opisane przez elementy poniżej `InstallChecks` elementu i oświadcza, które pakiety [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] należy zainstalować program inicjujący, jeśli test zakończy się niepowodzeniem.  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<Commands  
    Reboot  
>  
    <Command  
        PackageFile  
        Arguments  
        EstimatedInstallSeconds  
        EstimatedDiskBytes  
        EstimatedTempBytes  
        Log  
    >  
        <InstallConditions>  
            <BypassIf   
                Property  
                Compare  
                Value  
                Schedule  
            />  
            <FailIf   
                Property  
                Compare  
                Value  
                String  
                Schedule  
            />  
        </InstallConditions>  
        <ExitCodes>  
            <ExitCode   
                Value  
                Result  
                String  
            />  
        </ExitCodes>  
    </Command>  
</Commands>  
```  
  
## <a name="elements-and-attributes"></a>Atrybuty i elementy  
 `Commands` Element jest wymagany. Element ma atrybut.  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|`Reboot`|Opcjonalna. Określa, czy jeśli żadnych pakietów zwróci kod zakończenia ponownego uruchomienia należy ponownie uruchomić system. Poniższa lista przedstawia prawidłowe wartości:<br /><br /> `Defer`. Ponowne uruchomienie jest odroczone do czasu niektóre czas w przyszłości.<br /><br /> `Immediate`. Powoduje natychmiastowe ponowne uruchomienie, jeśli jeden z pakietów zwrócił kod zakończenia ponownego uruchomienia.<br /><br /> `None`. Powoduje, że wszystkie żądania ponownego uruchomienia, są ignorowane.<br /><br /> Wartość domyślna to `Immediate`.|  
  
## <a name="command"></a>Polecenie  
 `Command` Element jest elementem podrzędnym `Commands` elementu. A `Commands` element może mieć co najmniej jeden `Command` elementów. Element ma następujące atrybuty.  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|`PackageFile`|Wymagana. Nazwa pakietu do zainstalowania należy co najmniej jeden z warunków określonych przez `InstallConditions` zwróci wartość false. Pakiet musi być zdefiniowany w tym samym pliku przy użyciu `PackageFile` elementu.|  
|`Arguments`|Opcjonalna. Zestaw argumenty wiersza polecenia do przekazania do pliku pakietu.|  
|`EstimatedInstallSeconds`|Opcjonalna. Szacowany czas w sekundach, trwa instalowanie pakietu. Ta wartość określa rozmiar paska postępu, który program inicjujący wyświetla dla użytkownika. Wartość domyślna to 0, w którym to przypadku nie razem, gdy określono szacowania.|  
|`EstimatedDiskBytes`|Opcjonalna. Szacowana ilość miejsca na dysku, w bajtach, które zajmują po zakończeniu instalacji pakietu zostało zakończone. Ta wartość jest używana w wymagania dotyczące miejsca na dysku twardym, które program inicjujący wyświetla dla użytkownika. Wartość domyślna to 0, w przypadku program inicjujący nie wyświetla żadnych wymagań dotyczących miejsca na dysku twardym.|  
|`EstimatedTempBytes`|Opcjonalna. Szacowana ilość tymczasowego miejsca na dysku, w bajtach, które wymagają pakietu.|  
|`Log`|Opcjonalna. Ścieżka do pliku dziennika, który generuje pakiet, względem katalogu głównego pakietu.|  
  
## <a name="installconditions"></a>InstallConditions  
 `InstallConditions` Element jest elementem podrzędnym `Command` elementu. Każdy `Command` element może mieć co najwyżej jeden `InstallConditions` elementu. Jeśli nie `InstallConditions` element istnieje pakiet określony przez `Condition` zawsze działa.  
  
## <a name="bypassif"></a>BypassIf  
 `BypassIf` Element jest elementem podrzędnym `InstallConditions` elementu oraz opis warunku dodatnią, w ramach której polecenia nie powinien być wykonywany. Każdy `InstallConditions` element może mieć zero lub więcej `BypassIf` elementów.  
  
 `BypassIf` ma następujące atrybuty.  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|`Property`|Wymagana. Nazwa właściwości do testowania. Właściwość musi wcześniej zostały zdefiniowane przez element podrzędny elementu `InstallChecks` elementu. Aby uzyskać więcej informacji, zobacz [ \<InstallChecks > Element](../deployment/installchecks-element-bootstrapper.md).|  
|`Compare`|Wymagana. Typ porównania do wykonania. Poniższa lista przedstawia prawidłowe wartości:<br /><br /> `ValueEqualTo`, `ValueNotEqualTo`, `ValueGreaterThan`, `ValueGreaterThanOrEqualTo`, `ValueLessThan`, `ValueLessThanOrEqualTo`, `VersionEqualTo`, `VersionNotEqualTo`, `VersionGreaterThan`, `VersionGreaterThanOrEqualTo`, `VersionLessThan`, `VersionLessThanOrEqualTo`, `ValueExists`, `ValueNotExists`|  
|`Value`|Wymagana. Wartość do porównania z właściwościami.|  
|`Schedule`|Opcjonalna. Nazwa `Schedule` tag, który definiuje, gdy ta reguła powinna być oceniana.|  
  
## <a name="failif"></a>FailIf  
 `FailIf` Element jest elementem podrzędnym `InstallConditions` element i opisuje dodatnią warunek, pod którym ma zostać zatrzymana, instalacji. Każdy `InstallConditions` element może mieć zero lub więcej `FailIf` elementów.  
  
 `FailIf` ma następujące atrybuty.  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|`Property`|Wymagana. Nazwa właściwości do testowania. Właściwość musi wcześniej zostały zdefiniowane przez element podrzędny elementu `InstallChecks` elementu. Aby uzyskać więcej informacji, zobacz [ \<InstallChecks > Element](../deployment/installchecks-element-bootstrapper.md).|  
|`Compare`|Wymagana. Typ porównania do wykonania. Poniższa lista przedstawia prawidłowe wartości:<br /><br /> `ValueEqualTo`, `ValueNotEqualTo`, `ValueGreaterThan`, `ValueGreaterThanOrEqualTo`, `ValueLessThan`, `ValueLessThanOrEqualTo`, `VersionEqualTo`, `VersionNotEqualTo`, `VersionGreaterThan`, `VersionGreaterThanOrEqualTo`, `VersionLessThan`, `VersionLessThanOrEqualTo`, `ValueExists`, `ValueNotExists`|  
|`Value`|Wymagana. Wartość do porównania z właściwościami.|  
|`String`|Opcjonalna. Tekst do wyświetlenia dla użytkownika w przypadku awarii.|  
|`Schedule`|Opcjonalna. Nazwa `Schedule` tag, który definiuje, gdy ta reguła powinna być oceniana.|  
  
## <a name="exitcodes"></a>ExitCodes  
 `ExitCodes` Element jest elementem podrzędnym `Command` elementu. `ExitCodes` Elementu zawiera jeden lub więcej `ExitCode` elementów, które określają, jakie instalacji należy wykonać w odpowiedzi kod wyjściowy z pakietu. Może istnieć tylko jeden opcjonalny `ExitCode` element poniżej `Command` elementu. `ExitCodes` nie ma żadnych atrybutów.  
  
## <a name="exitcode"></a>ExitCode  
 `ExitCode` Element jest elementem podrzędnym `ExitCodes` elementu. `ExitCode` Element określa, jakie instalacji należy wykonać w odpowiedzi kod wyjściowy z pakietu. `ExitCode` nie zawiera żadnych elementów podrzędnych i ma następujące atrybuty.  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|`Value`|Wymagana. Wartość kodu zakończenia, do którego należy to `ExitCode` element ma zastosowanie.|  
|`Result`|Wymagana. Sposób instalacji powinien reagować na ten kod wyjścia. Poniższa lista przedstawia prawidłowe wartości:<br /><br /> `Success`. Flag pakietów, jak pomyślnie zainstalowane.<br /><br /> `SuccessReboot`. Flagi pakietu, jak pomyślnie zainstalować i powoduje, że ponowne uruchomienie systemu.<br /><br /> `Fail`. Flagi pakietu jako zakończony niepowodzeniem.<br /><br /> `FailReboot`. Flagi pakietu, ponieważ nie powiodło się i powoduje, że ponowne uruchomienie systemu.|  
|`String`|Opcjonalna. Wartość do wyświetlania użytkownikowi w odpowiedzi na ten kod wyjścia.|  
|`FormatMessageFromSystem`|Opcjonalna. Określa, czy należy użyć dostarczane przez system komunikat o błędzie odpowiadający kod zakończenia lub wartość podana w `String`. Prawidłowe wartości to `true`, co oznacza, że do użycia dostarczane przez system błąd i `false`, co oznacza, że użyć parametrów dostarczonych przez `String`. Wartość domyślna to `false`. Jeśli ta właściwość jest `false`, ale `String` nie jest ustawiona, błąd dostarczane przez system, który będzie używany.|  
  
## <a name="example"></a>Przykład  
 Poniższy kod definiuje polecenia dotyczące instalowania programu .NET Framework 2.0.  
  
```xml  
<Commands Reboot="Immediate">  
    <Command PackageFile="instmsia.exe"  
             Arguments= ' /q /c:"msiinst /delayrebootq"'  
             EstimatedInstallSeconds="20" >  
        <InstallConditions>  
           <BypassIf Property="VersionNT" Compare="ValueExists"/>  
             BypassIf Property="VersionMsi" Compare="VersionGreaterThanOrEqualTo" Value="2.0"/>  
        </InstallConditions>  
        <ExitCodes>  
            <ExitCode Value="0" Result="SuccessReboot"/>  
            <ExitCode Value="1641" Result="SuccessReboot"/>  
            <ExitCode Value="3010" Result="SuccessReboot"/>  
            <DefaultExitCode Result="Fail" FormatMessageFromSystem="true" String="GeneralFailure" />  
        </ExitCodes>  
    </Command>  
    <Command PackageFile="WindowsInstaller-KB884016-v2-x86.exe"  
             Arguments= '/quiet /norestart'   
             EstimatedInstallSeconds="20" >  
      <InstallConditions>  
          <BypassIf Property="Version9x" Compare="ValueExists"/>  
          <BypassIf Property="VersionNT" Compare="VersionLessThan" Value="5.0.3"/>  
          <BypassIf Property="VersionMsi" Compare="VersionGreaterThanOrEqualTo" Value="3.0"/>  
          <FailIf Property="AdminUser" Compare="ValueEqualTo" Value="false" String="AdminRequired"/>  
      </InstallConditions>  
      <ExitCodes>  
          <ExitCode Value="0" Result="Success"/>  
          <ExitCode Value="1641" Result="SuccessReboot"/>  
          <ExitCode Value="3010" Result="SuccessReboot"/>  
          <DefaultExitCode Result="Fail" FormatMessageFromSystem="true" String="GeneralFailure" />  
      </ExitCodes>  
    </Command>  
    <Command PackageFile="dotnetfx.exe"   
         Arguments=' /q:a /c:"install /q /l"'   
         EstimatedInstalledBytes="21000000"   
         EstimatedInstallSeconds="300">  
  
        <!-- These checks determine whether the package is to be installed -->  
        <InstallConditions>  
            <!-- Either of these properties indicates the .NET Framework is already installed -->  
            <BypassIf Property="DotNetInstalled" Compare="ValueNotEqualTo" Value="0"/>  
  
            <!-- Block install if user does not have adminpermissions -->  
            <FailIf Property="AdminUser" Compare="ValueEqualTo" Value="false" String="AdminRequired"/>  
  
            <!-- Block install on Windows 95 -->  
            <FailIf Property="Version9X" Compare="VersionLessThan" Value="4.10" String="InvalidPlatformWin9x"/>  
  
            <!-- Block install on Windows 2000 SP 2 or less -->  
            <FailIf Property="VersionNT" Compare="VersionLessThan" Value="5.0.3" String="InvalidPlatformWinNT"/>  
  
            <!-- Block install if Internet Explorer 5.01 or later is not present -->  
            <FailIf Property="IEVersion" Compare="ValueNotExists" String="InvalidPlatformIE" />  
            <FailIf Property="IEVersion" Compare="VersionLessThan" Value="5.01" String="InvalidPlatformIE" />  
  
            <!-- Block install if the operating system does not support x86 -->  
            <FailIf Property="ProcessorArchitecture" Compare="ValueNotEqualTo" Value="Intel" String="InvalidPlatformArchitecture" />  
       </InstallConditions>  
  
        <ExitCodes>  
            <ExitCode Value="0" Result="Success"/>  
            <ExitCode Value="3010" Result="SuccessReboot"/>  
            <ExitCode Value="4097" Result="Fail" String="AdminRequired"/>  
            <ExitCode Value="4098" Result="Fail" String="WindowsInstallerComponentFailure"/>  
            <ExitCode Value="4099" Result="Fail" String="WindowsInstallerImproperInstall"/>  
            <ExitCode Value="4101" Result="Fail" String="AnotherInstanceRunning"/>  
            <ExitCode Value="4102" Result="Fail" String="OpenDatabaseFailure"/>  
            <ExitCode Value="4113" Result="Fail" String="BetaNDPFailure"/>  
            <DefaultExitCode Result="Fail" FormatMessageFromSystem="true" String="GeneralFailure" />  
        </ExitCodes>  
  
    </Command>  
</Commands>  
```  
  
## <a name="see-also"></a>Zobacz także  
 [Odwołanie do schematu produktu i pakietu](../deployment/product-and-package-schema-reference.md)   
 [\<InstallChecks > element](../deployment/installchecks-element-bootstrapper.md)