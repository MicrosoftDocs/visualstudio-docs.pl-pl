---
title: '&lt;InstallChecks&gt; — Element (program inicjujący) | Dokumentacja firmy Microsoft'
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e45a2d0527e1d245a0d034310939bd1601db8adc
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62927910"
---
# <a name="ltinstallchecksgt-element-bootstrapper"></a>&lt;InstallChecks&gt; — element (program inicjujący)
`InstallChecks` Element obsługuje uruchamianie szereg testów na komputerze lokalnym, aby upewnić się, że wszystkie odpowiednie wymagania wstępne dotyczące aplikacji zostały zainstalowane.

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
 Ten element jest podrzędnym elementem opcjonalnym elementu `InstallChecks`. Dla każdego wystąpienia `AssemblyCheck`, program inicjujący będzie upewnij się, że zestaw identyfikowane przez element istnieje w globalnej pamięci podręcznej zestawów (GAC). Nie zawiera żadnych elementów i ma następujące atrybuty.

|Atrybut|Opis|
|---------------|-----------------|
|`Property`|Wymagana. Nazwa właściwości, aby przechować wynik. Tej właściwości mogą być przywoływane z testu poniżej `InstallConditions` element, który jest elementem podrzędnym elementu `Command` elementu. Aby uzyskać więcej informacji, zobacz [ \<polecenia > Element](../deployment/commands-element-bootstrapper.md).|
|`Name`|Wymagana. W pełni kwalifikowana nazwa zestawu, aby sprawdzić.|
|`PublicKeyToken`|Wymagana. Formie skróconej klucza publicznego skojarzonego z tym silnej nazwy zestawu. Wszystkie zestawy, przechowywane w pamięci podręcznej GAC, musi mieć nazwę, wersję i kluczem publicznym.|
|`Version`|Wymagana. Wersja zestawu.<br /><br /> Numer wersji ma format \< *wersji głównej*>.\< *wersja pomocnicza*>.\< *Wersja kompilacji*>.\< *wersja poprawki*>.|
|`Language`|Opcjonalna. Język zlokalizowanej zestawu. Wartość domyślna to `neutral`.|
|`ProcessorArchitecture`|Opcjonalna. Procesor komputera przez tę instalację. Wartość domyślna to `msil`.|

## <a name="externalcheck"></a>ExternalCheck
 Ten element jest podrzędnym elementem opcjonalnym elementu `InstallChecks`. Dla każdego wystąpienia `ExternalCheck`, program inicjujący wykonywania o nazwie zewnętrzny program w oddzielnym procesie, a przechowywanie jego kod zakończenia we właściwości wskazywanym przez `Property`. `ExternalCheck` są przydatne do implementowania kontroli złożonych zależności i podczas tworzenia jego instancji jest jedynym sposobem, aby sprawdzić, czy istnienie składnika.

 `ExternalCheck` nie zawiera żadnych elementów i ma następujące atrybuty.

|Atrybut|Opis|
|---------------|-----------------|
|`Property`|Wymagana. Nazwa właściwości, aby przechować wynik. Tej właściwości mogą być przywoływane z testu poniżej `InstallConditions` element, który jest elementem podrzędnym elementu `Command` elementu. Aby uzyskać więcej informacji, zobacz [ \<polecenia > Element](../deployment/commands-element-bootstrapper.md).|
|`PackageFile`|Wymagana. Program zewnętrzny do wykonania. Program musi być częścią pakietu dystrybucji Instalatora.|
|`Arguments`|Opcjonalna. Dostarcza argumentów wiersza polecenia do pliku wykonywalnego o nazwie określonej przez `PackageFile`.|

## <a name="filecheck"></a>FileCheck
 Ten element jest podrzędnym elementem opcjonalnym elementu `InstallChecks`. Dla każdego wystąpienia `FileCheck`, program inicjujący określi, czy nazwany plik istnieje i zwraca numer wersji pliku. Jeśli plik nie ma numeru wersji, program inicjujący, ustawia właściwość o nazwie określonej przez `Property` na 0. Jeśli plik nie istnieje, `Property` nie jest ustawiony na dowolną wartość.

 `FileCheck` nie zawiera żadnych elementów i ma następujące atrybuty.

| Atrybut | Opis |
|-----------------| - |
| `Property` | Wymagana. Nazwa właściwości, aby przechować wynik. Tej właściwości mogą być przywoływane z testu poniżej `InstallConditions` element, który jest elementem podrzędnym elementu `Command` elementu. Aby uzyskać więcej informacji, zobacz [ \<polecenia > Element](../deployment/commands-element-bootstrapper.md). |
| `FileName` | Wymagana. Nazwa pliku, aby znaleźć. |
| `SearchPath` | Wymagana. Dysku lub folder, w którym do wyszukiwania pliku. Musi to być ścieżka względna, jeśli `SpecialFolder` przypisano; w przeciwnym razie musi być ścieżką bezwzględną. |
| `SpecialFolder` | Opcjonalna. Folder, który ma specjalne znaczenie, Windows lub do [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]. Wartość domyślna to do interpretacji `SearchPath` jako ścieżkę bezwzględną. Prawidłowe wartości są następujące:<br /><br /> `AppDataFolder`. Folder dane aplikacji, w tym [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikacji; specyficzne dla bieżącego użytkownika.<br /><br /> `CommonAppDataFolder`. Folder dane aplikacji używana przez wszystkich użytkowników.<br /><br /> `CommonFilesFolder`. Folder Common Files dla bieżącego użytkownika.<br /><br /> `LocalDataAppFolder`. Folder dane aplikacji — roamingu.<br /><br /> `ProgramFilesFolder`. Standardowa folderu Program Files dla aplikacji 32-bitowych.<br /><br /> `StartUpFolder`. Folder, który zawiera wszystkie aplikacje uruchomione podczas uruchamiania systemu.<br /><br /> `SystemFolder`. Folder, który zawiera system 32-bitowych bibliotek DLL.<br /><br /> `WindowsFolder`. Folder, który zawiera instalacji systemu Windows.<br /><br /> `WindowsVolume`. Dysk lub partycję, która zawiera instalacji systemu Windows. |
| `SearchDepth` | Opcjonalna. Głębokość, w którym do wyszukiwania podfoldery dla wskazanego pliku. Wyszukiwanie jest pierwszy głębi. Wartość domyślna to 0, co ogranicza wyszukiwanie do folderu najwyższego poziomu, określony przez `SpecialFolder` i **SearchPath**. |

## <a name="msiproductcheck"></a>MsiProductCheck
 Ten element jest podrzędnym elementem opcjonalnym elementu `InstallChecks`. Dla każdego wystąpienia `MsiProductCheck`, program inicjujący sprawdza, czy określony instalacji Instalator systemu Microsoft Windows zostało uruchomione, dopóki zostanie zakończona. Wartość właściwości jest ustawiana w zależności od stanu zainstalowanego produktu. Wartość dodatnia wskazuje produkt jest zainstalowany, 0 lub wartość -1 wskazuje, nie jest zainstalowany. (Zobacz funkcji zestawu SDK Instalatora Windows MsiQueryFeatureState, aby uzyskać więcej informacji.) . Jeśli Instalator Windows nie jest zainstalowany na komputerze, `Property` nie jest ustawiona.

 `MsiProductCheck` nie zawiera żadnych elementów i ma następujące atrybuty.

|Atrybut|Opis|
|---------------|-----------------|
|`Property`|Wymagana. Nazwa właściwości, aby przechować wynik. Tej właściwości mogą być przywoływane z testu poniżej `InstallConditions` element, który jest elementem podrzędnym elementu `Command` elementu. Aby uzyskać więcej informacji, zobacz [ \<polecenia > Element](../deployment/commands-element-bootstrapper.md).|
|`Product`|Wymagana. Identyfikator GUID zainstalowany produkt.|
|`Feature`|Opcjonalna. Identyfikator GUID określonej funkcji zainstalowanych aplikacji.|

## <a name="registrycheck"></a>RegistryCheck
 Ten element jest podrzędnym elementem opcjonalnym elementu `InstallChecks`. Dla każdego wystąpienia `RegistryCheck`, program inicjujący sprawdza, czy określony klucz rejestru istnieje, lub czy ma podaną wartość.

 `RegistryCheck` nie zawiera żadnych elementów i ma następujące atrybuty.

|Atrybut|Opis|
|---------------|-----------------|
|`Property`|Wymagana. Nazwa właściwości, aby przechować wynik. Tej właściwości mogą być przywoływane z testu poniżej `InstallConditions` element, który jest elementem podrzędnym elementu `Command` elementu. Aby uzyskać więcej informacji, zobacz [ \<polecenia > Element](../deployment/commands-element-bootstrapper.md).|
|`Key`|Wymagana. Nazwa klucza rejestru.|
|`Value`|Opcjonalna. Nazwa wartości rejestru do pobrania. Wartość domyślna to do zwrócenia tekstu dla wartości domyślnej. `Value` musi być ciąg lub wartość typu DWORD.|

## <a name="registryfilecheck"></a>RegistryFileCheck
 Ten element jest podrzędnym elementem opcjonalnym elementu `InstallChecks`. Dla każdego wystąpienia `RegistryFileCheck`, program inicjujący pobiera wersję określonego pliku, w pierwszej próby pobrania ścieżki do pliku z określonego klucza rejestru. Jest to szczególnie przydatne, jeśli chcesz wyszukać plik w katalogu określonego jako wartości w rejestrze.

 `RegistryFileCheck` nie zawiera żadnych elementów i ma następujące atrybuty.

|Atrybut|Opis|
|---------------|-----------------|
|`Property`|Wymagana. Nazwa właściwości, aby przechować wynik. Tej właściwości mogą być przywoływane z testu poniżej `InstallConditions` element, który jest elementem podrzędnym elementu `Command` elementu. Aby uzyskać więcej informacji, zobacz [ \<polecenia > Element](../deployment/commands-element-bootstrapper.md).|
|`Key`|Wymagana. Nazwa klucza rejestru. Jego wartość jest interpretowana jako ścieżkę do pliku, chyba że `File` ma ustawioną wartość atrybutu. Jeśli ten klucz nie istnieje, `Property` nie jest ustawiona.|
|`Value`|Opcjonalna. Nazwa wartości rejestru do pobrania. Wartość domyślna to do zwrócenia tekstu dla wartości domyślnej. `Value` musi być ciągiem.|
|`FileName`|Opcjonalna. Nazwa pliku. Jeśli zostanie określony, uzyskaną z klucza rejestru jest zakłada się, że ścieżka katalogu, a ta nazwa jest dołączany do niego. Jeśli nie zostanie określony, wartość zwracana z rejestru jest zakłada się, że pełna ścieżka do pliku.|
|`SearchDepth`|Opcjonalna. Głębokość, w którym do wyszukiwania podfoldery dla wskazanego pliku. Wyszukiwanie jest pierwszy głębi. Wartość domyślna to 0, co ogranicza wyszukiwanie do folderu najwyższego poziomu, określony przez wartość klucza rejestru.|

## <a name="remarks"></a>Uwagi
 Podczas gdy elementy poniżej `InstallChecks` zdefiniować testy do uruchomienia, ich są wykonywane. Aby wykonać testy, należy utworzyć `Command` elementy poniżej `Commands` elementu.

## <a name="example"></a>Przykład
 Poniższy przykład kodu demonstruje `InstallChecks` elementu, ponieważ jest używany w pliku produktu [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)].

```xml
<InstallChecks>
    <ExternalCheck Property="DotNetInstalled" PackageFile="dotnetchk.exe" />
    <RegistryCheck Property="IEVersion" Key="HKLM\Software\Microsoft\Internet Explorer" Value="Version" />
</InstallChecks>
```

## <a name="installconditions"></a>InstallConditions
 Gdy `InstallChecks` są oceniane, generuje właściwości. Właściwości są następnie używane przez `InstallConditions` czy pakietu należy zainstalować, obejście czy zakończyć się niepowodzeniem. W poniższej tabeli wymieniono `InstallConditions`:

|||
|-|-|
|`FailIf`|Jeśli istnieją `FailIf` warunek jest spełniony, pakietu zakończy się niepowodzeniem. Pozostałe warunki nie zostaną ocenione.|
|`BypassIf`|Jeśli istnieją `BypassIf` warunek jest spełniony, pakiet zostanie pominięta. Pozostałe warunki nie zostaną ocenione.|

## <a name="predefined-properties"></a>Wstępnie zdefiniowane właściwości
 W poniższej tabeli wymieniono `BypassIf` i `FailIf` elementy:

|Właściwość|Uwagi|Możliwe wartości|
|--------------|-----------|---------------------|
|`Version9X`|Numer wersji systemu operacyjnego Windows 9 X.|4.10 = Windows 98|
|`VersionNT`|Numer wersji systemu operacyjnego Windows NT.|Major.Minor.ServicePack<br /><br /> W wersji 5.0 = Windows 2000<br /><br /> 5.1.0 = Windows XP<br /><br /> 5.1.2 = Windows XP Professional z dodatkiem SP2<br /><br /> 5.2.0 = systemu Windows Server 2003|
|`VersionNT64`|Numer wersji systemu operacyjnego 64-bitowym systemem Windows NT.|Wartość taka sama jak wspomniano wcześniej.|
|`VersionMsi`|Numer wersji usługi Instalator Windows.|2.0 = Instalatora Windows w wersji 2.0|
|`AdminUser`|Określa, czy użytkownik ma uprawnienia administratora w systemie operacyjnym opartym na Windows NT.|0 = nie uprawnień administratora<br /><br /> 1 = uprawnień administratora|

 Na przykład aby zablokować instalację na komputerze z systemem Windows 95, należy użyć kodu, takie jak następujące:

```xml
<!-- Block install on Windows 95 -->
    <FailIf Property="Version9X" Compare="VersionLessThan" Value="4.10" String="InvalidPlatform"/>
```

## <a name="see-also"></a>Zobacz także
- [\<Polecenia > element](../deployment/commands-element-bootstrapper.md)
- [Odwołanie do schematu produktu i pakietu](../deployment/product-and-package-schema-reference.md)