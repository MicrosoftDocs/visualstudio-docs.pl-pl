---
title: '&lt;Commands — &gt; element (program inicjujący) | Microsoft Docs'
description: Element Commands implementuje testy w elementach pod InstallChecks i deklaruje pakiet do zainstalowania, jeśli test programu inicjującego ClickOnce zakończy się niepowodzeniem.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: 65c63d52290962d8c9878edf025bbc05487103da
ms.sourcegitcommit: 0893244403aae9187c9375ecf0e5c221c32c225b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/09/2020
ms.locfileid: "94383056"
---
# <a name="ltcommandsgt-element-bootstrapper"></a>&lt;Commands — &gt; element (program inicjujący)
`Commands`Element implementuje testy opisane przez elementy poniżej `InstallChecks` elementu i deklaruje pakiet, który program [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] inicjujący powinien zainstalować, jeśli test zakończy się niepowodzeniem.

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

## <a name="elements-and-attributes"></a>Elementy i atrybuty
 `Commands`Element jest wymagany. Element ma następujący atrybut.

|Atrybut|Opis|
|---------------|-----------------|
|`Reboot`|Opcjonalny. Określa, czy system ma być uruchamiany ponownie, jeśli którykolwiek z pakietów zwróci kod zakończenia ponownego uruchomienia. Poniższa lista zawiera prawidłowe wartości:<br /><br /> `Defer`. Ponowne uruchomienie jest odroczone do czasu w przyszłości.<br /><br /> `Immediate`. Powoduje natychmiastowe ponowne uruchomienie, jeśli jeden z pakietów zwrócił kod zakończenia ponownego uruchomienia.<br /><br /> `None`. Powoduje ignorowanie żądań ponownego uruchomienia.<br /><br /> Wartość domyślna to `Immediate`.|

## <a name="command"></a>Polecenie
 `Command`Element jest elementem podrzędnym `Commands` elementu. `Commands`Element może mieć jeden lub więcej `Command` elementów. Element ma następujące atrybuty.

|Atrybut|Opis|
|---------------|-----------------|
|`PackageFile`|Wymagane. Nazwa pakietu do zainstalowania powinna mieć co najmniej jeden warunek określony przez `InstallConditions` zwrócenie wartości false. Pakiet musi być zdefiniowany w tym samym pliku przy użyciu `PackageFile` elementu.|
|`Arguments`|Opcjonalny. Zestaw argumentów wiersza polecenia do przekazania do pliku pakietu.|
|`EstimatedInstallSeconds`|Opcjonalny. Szacowany czas, w sekundach, zajmie się instalacją pakietu. Ta wartość określa rozmiar paska postępu wyświetlanego użytkownikowi przez program inicjujący. Wartość domyślna to 0, w tym przypadku nie określono oszacowania czasu.|
|`EstimatedDiskBytes`|Opcjonalny. Szacowana ilość miejsca na dysku (w bajtach), którą zajmie pakiet po zakończeniu instalacji. Ta wartość jest używana w wymaganiach dotyczących miejsca na dysku twardym, które program inicjujący wyświetla użytkownikowi. Wartość domyślna to 0, w takim przypadku program inicjujący nie wyświetla żadnych wymagań dotyczących miejsca na dysku twardym.|
|`EstimatedTempBytes`|Opcjonalny. Szacowana ilość miejsca na dysku (w bajtach), które będzie wymagane przez pakiet.|
|`Log`|Opcjonalny. Ścieżka do pliku dziennika generowanego przez pakiet względem katalogu głównego pakietu.|

## <a name="installconditions"></a>InstallConditions
 `InstallConditions`Element jest elementem podrzędnym `Command` elementu. Każdy `Command` element może mieć co najwyżej jeden `InstallConditions` element. Jeśli żaden `InstallConditions` element nie istnieje, pakiet określony przez `Condition` jest zawsze uruchamiany.

## <a name="bypassif"></a>BypassIf
 `BypassIf`Element jest elementem podrzędnym `InstallConditions` elementu i opisuje pozytywny warunek, pod którym polecenie nie powinno być wykonywane. Każdy `InstallConditions` element może mieć zero lub więcej `BypassIf` elementów.

 `BypassIf` ma następujące atrybuty.

|Atrybut|Opis|
|---------------|-----------------|
|`Property`|Wymagane. Nazwa właściwości do przetestowania. Właściwość musi wcześniej być zdefiniowana przez `InstallChecks` element podrzędny elementu. Aby uzyskać więcej informacji, zobacz [ \<InstallChecks> element](../deployment/installchecks-element-bootstrapper.md).|
|`Compare`|Wymagane. Typ porównania do wykonania. Poniższa lista zawiera prawidłowe wartości:<br /><br /> `ValueEqualTo`, `ValueNotEqualTo`, `ValueGreaterThan`, `ValueGreaterThanOrEqualTo`, `ValueLessThan`, `ValueLessThanOrEqualTo`, `VersionEqualTo`, `VersionNotEqualTo`, `VersionGreaterThan`, `VersionGreaterThanOrEqualTo`, `VersionLessThan`, `VersionLessThanOrEqualTo`, `ValueExists`, `ValueNotExists`|
|`Value`|Wymagane. Wartość do porównania z właściwością.|
|`Schedule`|Opcjonalny. Nazwa `Schedule` tagu, który definiuje, kiedy ta reguła powinna być Szacowana.|

## <a name="failif"></a>FailIf
 `FailIf`Element jest elementem podrzędnym `InstallConditions` elementu i opisuje pozytywne warunki, w których instalacja powinna zostać zatrzymana. Każdy `InstallConditions` element może mieć zero lub więcej `FailIf` elementów.

 `FailIf` ma następujące atrybuty.

|Atrybut|Opis|
|---------------|-----------------|
|`Property`|Wymagane. Nazwa właściwości do przetestowania. Właściwość musi wcześniej być zdefiniowana przez `InstallChecks` element podrzędny elementu. Aby uzyskać więcej informacji, zobacz [ \<InstallChecks> element](../deployment/installchecks-element-bootstrapper.md).|
|`Compare`|Wymagane. Typ porównania do wykonania. Poniższa lista zawiera prawidłowe wartości:<br /><br /> `ValueEqualTo`, `ValueNotEqualTo`, `ValueGreaterThan`, `ValueGreaterThanOrEqualTo`, `ValueLessThan`, `ValueLessThanOrEqualTo`, `VersionEqualTo`, `VersionNotEqualTo`, `VersionGreaterThan`, `VersionGreaterThanOrEqualTo`, `VersionLessThan`, `VersionLessThanOrEqualTo`, `ValueExists`, `ValueNotExists`|
|`Value`|Wymagane. Wartość do porównania z właściwością.|
|`String`|Opcjonalny. Tekst, który ma być wyświetlany użytkownikowi w przypadku niepowodzenia.|
|`Schedule`|Opcjonalny. Nazwa `Schedule` tagu, który definiuje, kiedy ta reguła powinna być Szacowana.|

## <a name="exitcodes"></a>ExitCodes
 `ExitCodes`Element jest elementem podrzędnym `Command` elementu. `ExitCodes`Element zawiera jeden lub więcej `ExitCode` elementów, które określają, jak instalacja powinna zostać podjęta w odpowiedzi na kod zakończenia z pakietu. Może istnieć jeden opcjonalny `ExitCode` element poniżej `Command` elementu. `ExitCodes` nie ma atrybutów.

## <a name="exitcode"></a>ExitCode
 `ExitCode`Element jest elementem podrzędnym `ExitCodes` elementu. `ExitCode`Element określa, co proces instalacji powinien wykonać w odpowiedzi na kod zakończenia z pakietu. `ExitCode` nie zawiera elementów podrzędnych i ma następujące atrybuty.

|Atrybut|Opis|
|---------------|-----------------|
|`Value`|Wymagane. Wartość kodu zakończenia, do której `ExitCode` ma zastosowanie ten element.|
|`Result`|Wymagane. Jak instalacja powinna reagować na ten kod zakończenia. Poniższa lista zawiera prawidłowe wartości:<br /><br /> `Success`. Flaguje pakiet jako pomyślnie zainstalowany.<br /><br /> `SuccessReboot`. Flaguje pakiet jako pomyślnie zainstalowany i instruuje system do ponownego uruchomienia.<br /><br /> `Fail`. Flaguje pakiet jako niepowodzenie.<br /><br /> `FailReboot`. Flaguje pakiet jako zakończony niepowodzeniem i powoduje ponowne uruchomienie systemu.|
|`String`|Opcjonalny. Wartość, która ma zostać wyświetlona dla użytkownika w odpowiedzi na ten kod zakończenia.|
|`FormatMessageFromSystem`|Opcjonalny. Określa, czy należy użyć komunikatu o błędzie dostarczonego przez system odpowiadającego kodowi zakończenia lub użyć wartości podanej w `String` . Prawidłowe wartości to `true` , co oznacza użycie błędu dostarczonego przez system i `false` , który oznacza użycie ciągu dostarczonego przez `String` . Wartość domyślna to `false`. Jeśli ta właściwość ma `false` wartość, ale `String` nie jest ustawiona, zostanie użyty błąd dostarczony przez system.|

## <a name="example"></a>Przykład
 Poniższy przykład kodu definiuje polecenia instalacji .NET Framework 2,0.

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

## <a name="see-also"></a>Zobacz też
- [Dokumentacja schematu produktu i pakietu](../deployment/product-and-package-schema-reference.md)
- [\<InstallChecks> postaci](../deployment/installchecks-element-bootstrapper.md)