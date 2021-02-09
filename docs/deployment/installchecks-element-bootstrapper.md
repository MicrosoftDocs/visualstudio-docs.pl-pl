---
title: '&lt;InstallChecks — &gt; element (program inicjujący) | Microsoft Docs'
description: Element InstallChecks obsługuje uruchamianie różnych testów na komputerze lokalnym, aby upewnić się, że wszystkie wymagania wstępne dotyczące aplikacji zostały zainstalowane.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- <InstallChecks> element [bootstrapper]
ms.assetid: ad329c87-b0ad-4304-84de-ae9496514c42
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 550baf52347c1128ef50509e7787861355c9428f
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99903401"
---
# <a name="ltinstallchecksgt-element-bootstrapper"></a>&lt;InstallChecks — &gt; element (program inicjujący)
`InstallChecks`Element obsługuje uruchamianie różnych testów na komputerze lokalnym, aby upewnić się, że zostały zainstalowane wszystkie odpowiednie wymagania wstępne dotyczące aplikacji.

## <a name="syntax"></a>Składnia

```xml
<InstallChecks>
    <AssemblyCheck
        Property
        Name
        PublicKeyToken
        Version
        Language
        ProcessorArchitecture
    />
    <RegistryCheck
        Property
        Key
        Value
    />
    <ExternalCheck
        PackageFile
        Property
        Arguments
    />
    <FileCheck
        Property
        FileName
        SearchPath
        SpecialFolder
        SearchDepth
    />
    <MsiProductCheck
        Property
        Product
        Feature
    />
    <RegistryFileCheck
        Property
        Key
        Value
        FileName
        SearchDepth
    />
</InstallChecks>
```

## <a name="assemblycheck"></a>AssemblyCheck
 Ten element jest opcjonalnym elementem podrzędnym `InstallChecks` . Dla każdego wystąpienia programu `AssemblyCheck` inicjującego upewnij się, że zestaw identyfikowany przez element istnieje w globalnej pamięci podręcznej zestawów (GAC). Nie zawiera żadnych elementów i ma następujące atrybuty.

|Atrybut|Opis|
|---------------|-----------------|
|`Property`|Wymagane. Nazwa właściwości do przechowywania wyniku. Do tej właściwości można odwoływać się z testu poniżej `InstallConditions` elementu, który jest elementem podrzędnym `Command` elementu. Aby uzyskać więcej informacji, zobacz [ \<Commands> element](../deployment/commands-element-bootstrapper.md).|
|`Name`|Wymagane. W pełni kwalifikowana nazwa zestawu do sprawdzenia.|
|`PublicKeyToken`|Wymagane. Skrócona forma klucza publicznego skojarzonego z tym silnie nazwanym zestawem. Wszystkie zestawy przechowywane w pamięci podręcznej GAC muszą mieć nazwę, wersję i klucz publiczny.|
|`Version`|Wymagane. Wersja zestawu.<br /><br /> Numer wersji ma format \<*major version*> . \<*minor version*> . \<*build version*> . \<*revision version*>|
|`Language`|Opcjonalny. Język zlokalizowanego zestawu. Wartość domyślna to `neutral`.|
|`ProcessorArchitecture`|Opcjonalny. Procesor komputera przeznaczony dla tej instalacji. Wartość domyślna to `msil`.|

## <a name="externalcheck"></a>ExternalCheck
 Ten element jest opcjonalnym elementem podrzędnym `InstallChecks` . Dla każdego wystąpienia `ExternalCheck` program inicjujący wykona nazwany program zewnętrzny w oddzielnym procesie i zapisze jego kod zakończenia we właściwości wskazanej przez `Property` . `ExternalCheck` jest przydatne do implementowania złożonych kontroli zależności lub gdy jedynym sposobem sprawdzenia istnienia składnika jest utworzenie jego wystąpienia.

 `ExternalCheck` nie zawiera żadnych elementów i ma następujące atrybuty.

|Atrybut|Opis|
|---------------|-----------------|
|`Property`|Wymagane. Nazwa właściwości do przechowywania wyniku. Do tej właściwości można odwoływać się z testu poniżej `InstallConditions` elementu, który jest elementem podrzędnym `Command` elementu. Aby uzyskać więcej informacji, zobacz [ \<Commands> element](../deployment/commands-element-bootstrapper.md).|
|`PackageFile`|Wymagane. Program zewnętrzny do wykonania. Program musi być częścią pakietu dystrybucji Instalatora.|
|`Arguments`|Opcjonalny. Dostarcza argumenty wiersza polecenia do pliku wykonywalnego o nazwie przez `PackageFile` .|

## <a name="filecheck"></a>FileCheck
 Ten element jest opcjonalnym elementem podrzędnym `InstallChecks` . Dla każdego wystąpienia programu `FileCheck` program inicjujący określi, czy nazwany plik istnieje, i zwraca numer wersji pliku. Jeśli plik nie ma numeru wersji, program inicjujący ustawia właściwość o nazwie `Property` na 0. Jeśli plik nie istnieje, `Property` nie jest ustawiony na żadnej wartości.

 `FileCheck` nie zawiera żadnych elementów i ma następujące atrybuty.

| Atrybut | Opis |
|-----------------| - |
| `Property` | Wymagane. Nazwa właściwości do przechowywania wyniku. Do tej właściwości można odwoływać się z testu poniżej `InstallConditions` elementu, który jest elementem podrzędnym `Command` elementu. Aby uzyskać więcej informacji, zobacz [ \<Commands> element](../deployment/commands-element-bootstrapper.md). |
| `FileName` | Wymagane. Nazwa pliku do wyszukania. |
| `SearchPath` | Wymagane. Dysk lub folder, w którym ma być wyszukiwany plik. Ta wartość musi być ścieżką względną `SpecialFolder` , jeśli jest przypisana; w przeciwnym razie musi być ścieżką bezwzględną. |
| `SpecialFolder` | Opcjonalny. Folder, który ma specjalne znaczenie dla systemu Windows lub [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] . Wartością domyślną jest interpretowanie `SearchPath` jako ścieżki bezwzględnej. Prawidłowe wartości to:<br /><br /> `AppDataFolder`. Folder dane aplikacji dla tej [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikacji; określony dla bieżącego użytkownika.<br /><br /> `CommonAppDataFolder`. Folder danych aplikacji używany przez wszystkich użytkowników.<br /><br /> `CommonFilesFolder`. Folder Common Files dla bieżącego użytkownika.<br /><br /> `LocalDataAppFolder`. Folder danych dla aplikacji niemobilnych.<br /><br /> `ProgramFilesFolder`. Folder Program Files w warstwie Standardowa dla aplikacji 32-bitowych.<br /><br /> `StartUpFolder`. Folder zawierający wszystkie aplikacje, które są uruchamiane podczas uruchamiania systemu.<br /><br /> `SystemFolder`. Folder zawierający 32-bitowe systemowe biblioteki DLL.<br /><br /> `WindowsFolder`. Folder zawierający instalację systemu Windows.<br /><br /> `WindowsVolume`. Dysk lub partycja zawierająca instalację systemu Windows. |
| `SearchDepth` | Opcjonalny. Głębokość przeszukiwania podfolderów dla nazwanego pliku. Wyszukiwanie jest głębokością — najpierw. Wartość domyślna to 0, co ogranicza wyszukiwanie do folderu najwyższego poziomu określonego przez `SpecialFolder` i **SearchPath**. |

## <a name="msiproductcheck"></a>MsiProductCheck
 Ten element jest opcjonalnym elementem podrzędnym `InstallChecks` . Dla każdego wystąpienia `MsiProductCheck` program inicjujący sprawdza, czy określona instalacja programu Microsoft Instalator Windows została uruchomiona, dopóki nie zostanie ukończona. Wartość właściwości jest ustawiana w zależności od stanu zainstalowanego produktu. Wartość dodatnia oznacza, że produkt jest zainstalowany, 0 lub-1 oznacza, że nie jest zainstalowany. (Aby uzyskać więcej informacji Instalator Windows, zobacz MsiQueryFeatureState zestawu SDK. . Jeśli Instalator Windows nie jest zainstalowana na komputerze, `Property` nie jest ustawiona.

 `MsiProductCheck` nie zawiera żadnych elementów i ma następujące atrybuty.

|Atrybut|Opis|
|---------------|-----------------|
|`Property`|Wymagane. Nazwa właściwości do przechowywania wyniku. Do tej właściwości można odwoływać się z testu poniżej `InstallConditions` elementu, który jest elementem podrzędnym `Command` elementu. Aby uzyskać więcej informacji, zobacz [ \<Commands> element](../deployment/commands-element-bootstrapper.md).|
|`Product`|Wymagane. Identyfikator GUID zainstalowanego produktu.|
|`Feature`|Opcjonalny. Identyfikator GUID określonej funkcji zainstalowanej aplikacji.|

## <a name="registrycheck"></a>RegistryCheck
 Ten element jest opcjonalnym elementem podrzędnym `InstallChecks` . Dla każdego wystąpienia programu `RegistryCheck` program inicjujący sprawdza, czy określony klucz rejestru istnieje lub czy ma określoną wartość.

 `RegistryCheck` nie zawiera żadnych elementów i ma następujące atrybuty.

|Atrybut|Opis|
|---------------|-----------------|
|`Property`|Wymagane. Nazwa właściwości do przechowywania wyniku. Do tej właściwości można odwoływać się z testu poniżej `InstallConditions` elementu, który jest elementem podrzędnym `Command` elementu. Aby uzyskać więcej informacji, zobacz [ \<Commands> element](../deployment/commands-element-bootstrapper.md).|
|`Key`|Wymagane. Nazwa klucza rejestru.|
|`Value`|Opcjonalny. Nazwa wartości rejestru do pobrania. Wartością domyślną jest zwrócenie tekstu wartości domyślnej. `Value` musi być ciągiem lub DWORD.|

## <a name="registryfilecheck"></a>RegistryFileCheck
 Ten element jest opcjonalnym elementem podrzędnym `InstallChecks` . Dla każdego wystąpienia `RegistryFileCheck` program inicjujący Pobiera wersję określonego pliku, a najpierw próbuje pobrać ścieżkę do pliku z określonego klucza rejestru. Jest to szczególnie przydatne, jeśli chcesz wyszukać plik w katalogu określonym jako wartość rejestru.

 `RegistryFileCheck` nie zawiera żadnych elementów i ma następujące atrybuty.

|Atrybut|Opis|
|---------------|-----------------|
|`Property`|Wymagane. Nazwa właściwości do przechowywania wyniku. Do tej właściwości można odwoływać się z testu poniżej `InstallConditions` elementu, który jest elementem podrzędnym `Command` elementu. Aby uzyskać więcej informacji, zobacz [ \<Commands> element](../deployment/commands-element-bootstrapper.md).|
|`Key`|Wymagane. Nazwa klucza rejestru. Jego wartość jest interpretowana jako ścieżka do pliku, chyba że `File` atrybut jest ustawiony. Jeśli ten klucz nie istnieje, `Property` nie jest ustawiony.|
|`Value`|Opcjonalny. Nazwa wartości rejestru do pobrania. Wartością domyślną jest zwrócenie tekstu wartości domyślnej. `Value` musi być ciągiem.|
|`FileName`|Opcjonalny. Nazwa pliku. Jeśli jest określony, zakłada się, że wartość uzyskana z klucza rejestru jest ścieżką katalogu, a ta nazwa jest dołączana do niej. Jeśli nie zostanie określony, przyjmuje się, że wartość zwracana z rejestru jest pełną ścieżką do pliku.|
|`SearchDepth`|Opcjonalny. Głębokość przeszukiwania podfolderów dla nazwanego pliku. Wyszukiwanie jest głębokością — najpierw. Wartością domyślną jest 0, która ogranicza wyszukiwanie do folderu najwyższego poziomu określonego przez wartość klucza rejestru.|

## <a name="remarks"></a>Uwagi
 Chociaż elementy poniżej `InstallChecks` definiują testy do uruchomienia, nie wykonują ich. Aby wykonać testy, należy utworzyć `Command` elementy poniżej `Commands` elementu.

## <a name="example"></a>Przykład
 Poniższy przykład kodu demonstruje element, który `InstallChecks` jest używany w pliku produktu dla .NET Framework.

```xml
<InstallChecks>
    <ExternalCheck Property="DotNetInstalled" PackageFile="dotnetchk.exe" />
    <RegistryCheck Property="IEVersion" Key="HKLM\Software\Microsoft\Internet Explorer" Value="Version" />
</InstallChecks>
```

## <a name="installconditions"></a>InstallConditions
 Kiedy `InstallChecks` są oceniane, tworzą właściwości. Właściwości są następnie używane przez program `InstallConditions` , aby określić, czy pakiet ma być instalowany, pomijany, czy niepowodzeniem. W poniższej tabeli wymieniono `InstallConditions` :

|Warunek|Opis|
|-|-|
|`FailIf`|Jeśli dowolny `FailIf` warunek zwróci wartość true, pakiet zakończy się niepowodzeniem. Pozostałe warunki nie zostaną ocenione.|
|`BypassIf`|Jeśli którykolwiek `BypassIf` z warunków zwróci wartość true, pakiet zostanie pominięty. Pozostałe warunki nie zostaną ocenione.|

## <a name="predefined-properties"></a>Wstępnie zdefiniowane właściwości
 W poniższej tabeli wymieniono `BypassIf` `FailIf` elementy i:

|Właściwość|Uwagi|Możliwe wartości|
|--------------|-----------|---------------------|
|`Version9X`|Numer wersji systemu operacyjnego Windows 9X.|4,10 = Windows 98|
|`VersionNT`|Numer wersji systemu operacyjnego opartego na systemie Windows NT.|Główna. pomocnicza. dodatek Service Pack<br /><br /> 5,0 = Windows 2000<br /><br /> 5.1.0 = Windows XP<br /><br /> 5.1.2 = Windows XP Professional z dodatkiem SP2<br /><br /> 5.2.0 = Windows Server 2003|
|`VersionNT64`|Numer wersji 64-bitowego systemu operacyjnego Windows NT.|Tak samo jak wspomniano wcześniej.|
|`VersionMsi`|Numer wersji usługi Instalator Windows.|2,0 = Instalator Windows 2,0|
|`AdminUser`|Określa, czy użytkownik ma uprawnienia administratora w systemie operacyjnym Windows NT.|0 = brak uprawnień administratora<br /><br /> 1 = uprawnienia administratora|

 Aby na przykład zablokować instalację na komputerze z systemem Windows 95, należy użyć następującego kodu:

```xml
    <!-- Block install on Windows 95 -->
    <FailIf Property="Version9X" Compare="VersionLessThan" Value="4.10" String="InvalidPlatform"/>
```

 Aby pominąć uruchamianie instalacji, sprawdź, czy spełniony jest warunek FailIf lub BypassIf, Użyj atrybutu BeforeInstallChecks.  Na przykład:

```xml
    <!-- Block install and do not evaluate install checks if user does not have admin privileges -->
    <FailIf Property="AdminUser" Compare="ValueEqualTo" Value="false" String="AdminRequired" BeforeInstallChecks="true"/>
```

>[!NOTE]
>Ten `BeforeInstallChecks` atrybut jest obsługiwany, zaczynając od wersji programu Visual Studio 2019 Update 9.

## <a name="see-also"></a>Zobacz też
- [\<Commands> postaci](../deployment/commands-element-bootstrapper.md)
- [Dokumentacja schematu produktu i pakietu](../deployment/product-and-package-schema-reference.md)