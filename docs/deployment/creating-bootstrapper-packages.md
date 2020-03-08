---
title: Tworzenie niestandardowych pakietów programu inicjującego
ms.date: 05/02/2018
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- deploying applications [Visual Studio], prerequisites
- deploying applications [Visual Studio], custom prerequisites
- prerequisites, custom
- RedistList file
- custom prerequisites
- redistributables list
ms.assetid: ba1a785b-693d-446b-bcae-b88cadee73d1
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0f84f91ebedd47df8c0804adee35dcbec18d8551
ms.sourcegitcommit: 3154387056160bf4c36ac8717a7fdc0cd9faf3f9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2020
ms.locfileid: "78409592"
---
# <a name="create-bootstrapper-packages"></a>Tworzenie niestandardowych pakietów programu inicjującego
Program instalacyjny jest instalatorem ogólnym, który można skonfigurować w celu wykrywania i instalowania składników redystrybucyjnych, takich jak pliki Instalator Windows (*MSI*) i programy wykonywalne. Instalator jest również znany jako program inicjujący. Jest on zaprogramowany przez zestaw manifestów XML, które określają metadane do zarządzania instalacją składnika.  Każdy składnik redystrybucyjny lub warunek wstępny, który jest wyświetlany w oknie dialogowym **wymagania wstępne** dla technologii ClickOnce, jest pakietem programu inicjującego. Pakiet programu inicjującego to grupa katalogów i plików, które zawierają pliki manifestu opisujące, jak należy zainstalować wymaganie wstępne.

Program inicjujący najpierw wykrywa, czy którykolwiek z wymagań wstępnych jest już zainstalowany. Jeśli wymagania wstępne nie są zainstalowane, program inicjujący wyświetli umowy licencyjne. Po drugie, po zaakceptowaniu przez użytkownika końcowego umów licencyjnych instalacja rozpocznie się w przypadku wymagań wstępnych. W przeciwnym razie, jeśli zostaną wykryte wszystkie wymagania wstępne, program inicjujący rozpocznie pracę Instalatora aplikacji.

## <a name="create-custom-bootstrapper-packages"></a>Utwórz niestandardowe pakiety programu inicjującego
Można wygenerować manifesty programu inicjującego za pomocą edytora XML w programie Visual Studio. Aby zapoznać się z przykładem tworzenia pakietu programu inicjującego, zobacz [Przewodnik: Tworzenie niestandardowego programu inicjującego z monitem o prywatność](../deployment/walkthrough-creating-a-custom-bootstrapper-to-show-a-privacy-prompt.md).

Aby utworzyć pakiet programu inicjującego, należy utworzyć manifest produktu i, dla każdej zlokalizowanej wersji składnika, również manifest pakietu.

* Manifest produktu, *Product. XML*, zawiera wszelkie metadane niezależne od języka dla pakietu. Zawiera metadane wspólne dla wszystkich zlokalizowanych wersji składnika redystrybucyjnego.  Aby utworzyć ten plik, zobacz [jak: Tworzenie manifestu produktu](../deployment/how-to-create-a-product-manifest.md).

* Manifest pakietu, *Package. XML*, zawiera metadane specyficzne dla języka; zwykle zawiera zlokalizowane komunikaty o błędach. Składnik musi mieć co najmniej jeden manifest pakietu dla każdej zlokalizowanej wersji tego składnika. Aby utworzyć ten plik, zobacz [How to: Create a Package manifest](../deployment/how-to-create-a-package-manifest.md).

Po utworzeniu tych plików Umieść plik manifestu produktu w folderze o nazwie niestandardowego programu inicjującego. Plik manifestu pakietu przechodzi do folderu o nazwie dla ustawień regionalnych. Jeśli na przykład plik manifestu pakietu jest przeznaczony do redystrybucji w języku angielskim, należy umieścić go w folderze o nazwie en. Powtórz ten proces dla każdego ustawienia regionalnego, takiego jak ja dla języka japońskiego i Cofnij dla języka niemieckiego. Ostatni niestandardowy pakiet programu inicjującego może mieć następującą strukturę folderów.

```
CustomBootstrapperPackage
  product.xml
  CustomBootstrapper.msi
  de
    eula.rtf
    package.xml
  en
    eula.rtf
    package.xml
  ja
    eula.rtf
    package.xml
```

Następnie skopiuj pliki redystrybucyjne do lokalizacji folderu programu inicjującego. Aby uzyskać więcej informacji, zobacz [How to: Create a zlokalizowany pakiet programu inicjującego](../deployment/how-to-create-a-localized-bootstrapper-package.md).

```
*\Program Files (x86)\Microsoft SDKs\ClickOnce Bootstrapper*
```

lub w przypadku starszych wersji programu Visual Studio

```
*\Program Files\Microsoft Visual Studio 14.0\SDK\Bootstrapper\Packages*
```

lub

```
*\Program Files (x86)\Microsoft Visual Studio 14.0\SDK\Bootstrapper\Packages*
```

Lokalizację folderu programu inicjującego można również znaleźć na podstawie wartości **Path** w następującym kluczu rejestru:

```
*HKLM\Software\Microsoft\GenericBootstrapper*
```

W systemach 64-bitowych należy użyć następującego klucza rejestru:

```
*HKLM\Software\Wow6432Node\Microsoft\GenericBootstrapper*
```

Każdy składnik redystrybucyjny pojawia się w osobnym podfolderze katalogu Packages. Manifest produktu i pliki redystrybucyjne muszą być umieszczone w tym podfolderze. Zlokalizowane wersje składników i manifestów pakietów muszą być umieszczone w podfolderach o nazwie zgodnie z nazwą kultury.

Po skopiowaniu tych plików do folderu programu inicjującego pakiet programu inicjującego automatycznie pojawia się w oknie dialogowym **wymagania wstępne** programu Visual Studio. Jeśli niestandardowy pakiet programu inicjującego nie jest wyświetlany, Zamknij i ponownie otwórz okno dialogowe **wymagania wstępne** . Aby uzyskać więcej informacji, zobacz [okno dialogowe wymagania wstępne](../ide/reference/prerequisites-dialog-box.md).

W poniższej tabeli przedstawiono właściwości, które są automatycznie wypełniane przez program inicjujący.

|Właściwość|Opis|
|--------------|-----------------|
|ApplicationName|Nazwa aplikacji.|
|ProcessorArchitecture|Procesor i bity dla poszczególnych wyrazów platformy, do których odnoszą się pliki wykonywalne. Dostępne są następujące wartości:<br /><br /> — Intel<br />— IA64<br />-AMD64|
|[Version9x](/windows/desktop/Msi/version9x)|Numer wersji dla systemów operacyjnych Microsoft Windows 95, Windows 98 lub Windows ME. Składnia wersji to główna. pomocnicza. dodatek Service Pack.|
|[VersionNT](/windows/desktop/Msi/versionnt)|Numer wersji dla systemów operacyjnych Windows NT, Windows 2000, Windows XP, Windows Vista, Windows Server 2008 lub Windows 7. Składnia wersji to główna. pomocnicza. dodatek Service Pack.|
|[VersionMSI](/windows/desktop/Msi/versionmsi)|Wersja zestawu Instalator Windows (msi. dll) do uruchomienia podczas instalacji.|
|[AdminUser](/windows/desktop/Msi/adminuser)|Ta właściwość jest ustawiona, jeśli użytkownik ma uprawnienia administratora. Wartości mają wartość true lub false.|
|Installmode|Tryb instalacji wskazuje, gdzie należy zainstalować składnik. Dostępne są następujące wartości:<br /><br /> -HomeSite — wymagania wstępne są instalowane z witryny sieci Web dostawcy.<br />-SpecificSite — wymagania wstępne są instalowane z wybranej lokalizacji.<br />-SameSite — wymagania wstępne są instalowane z tej samej lokalizacji, w której znajduje się aplikacja.|

## <a name="separate-redistributables-from-application-installations"></a>Oddziel pakiety redystrybucyjne od instalacji aplikacji
Można zapobiec wdrażaniu plików redystrybucyjnych w projektach instalacyjnych. W tym celu Utwórz listę redystrybucyjną w folderze RedistList w katalogu .NET Framework:

`%ProgramFiles%\Microsoft.NET\RedistList`

Lista redystrybucyjna to plik XML, który należy nazwać, używając następującego formatu: *\<nazwa firmy >.\<nazwę składnika >. RedistList. XML*. Tak więc, na przykład, jeśli składnik jest wywoływany przez Acme, użyj *Acme. DataWidgets. RedistList. XML*. Przykład zawartości listy redystrybucyjnej może wyglądać następująco:

```xml
<?xml version="1.0" encoding="UTF-8"?>
<FileList Redist="Acme.DataWidgets" >
<File AssemblyName="Acme.DataGrid" Version="1.0.0.0" PublicKeyToken="b03f5f7f11d50a3a" Culture="neutral" ProcessorArchitecture="MSIL" InGAC="true" />
</FileList>
```

## <a name="see-also"></a>Zobacz też
- [Instrukcje: instalowanie wstępnie wymaganych składników za pomocą aplikacji ClickOnce](../deployment/how-to-install-prerequisites-with-a-clickonce-application.md)
- [Wymagania wstępne — okno dialogowe](../ide/reference/prerequisites-dialog-box.md)
- [Dokumentacja schematu produktu i pakietu](../deployment/product-and-package-schema-reference.md)
- [Aby rozpocząć instalację, użyj programu inicjującego Visual Studio 2005](https://msdn.microsoft.com/magazine/cc163899.aspx)
