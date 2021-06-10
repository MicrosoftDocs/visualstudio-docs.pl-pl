---
title: Tworzenie niestandardowych pakietów programu inicjującego
description: Dowiedz się więcej o programie instalacyjnym i instrukcje korzystania z manifestów XML, które określają metadane do zarządzania instalacją składników ClickOnce.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 007a7f42448ab8026d8acdc262ce5e0dcdd99b28
ms.sourcegitcommit: 6aa55db5e1fe19d4d17886e0bfe140dbd186f8ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/10/2021
ms.locfileid: "111877731"
---
# <a name="create-bootstrapper-packages"></a>Tworzenie niestandardowych pakietów programu inicjującego
Program instalacyjny to ogólny instalator, który można skonfigurować do wykrywania i instalowania składników redystrybucyjnego, takich jak pliki Instalator Windows *(.msi)* i programy wykonywalne. Instalator jest również znany jako program inicjujący. Jest on zaprogramowany za pomocą zestawu manifestów XML, które określają metadane do zarządzania instalacją składnika.  Każdy składnik redystrybucyjnego lub wymaganie wstępne, który pojawia się w **oknie** dialogowym Wymagania wstępne dla clickOnce jest pakietem programu inicjjącego. Pakiet programu inicjujący to grupa katalogów i plików zawierających pliki manifestu, które opisują sposób instalowania wymagań wstępnych.

Program inicjujący najpierw wykrywa, czy którekolwiek z wymagań wstępnych są już zainstalowane. Jeśli wymagania wstępne nie są zainstalowane, najpierw program inicjujący wyświetla umowy licencyjne. Po drugie, gdy użytkownik końcowy zaakceptuje umowy licencyjne, rozpocznie się instalacja w celu zachowania wymagań wstępnych. W przeciwnym razie, jeśli zostaną wykryte wszystkie wymagania wstępne, program inicjujący po prostu uruchamia instalatora aplikacji.

## <a name="create-custom-bootstrapper-packages"></a>Tworzenie niestandardowych pakietów programu inicjjącego
Manifesty programu inicjjącego można wygenerować przy użyciu edytora XML w Visual Studio. Aby zobaczyć przykład tworzenia pakietu programu inicjjącego, zobacz Przewodnik: tworzenie niestandardowego programu [inicjującego z monitem o prywatność.](../deployment/walkthrough-creating-a-custom-bootstrapper-to-show-a-privacy-prompt.md)

Aby utworzyć pakiet programu inicjujący, należy utworzyć manifest produktu oraz manifest pakietu dla każdej zlokalizowanej wersji składnika.

* Manifest produktu, *product.xml*, zawiera wszystkie metadane neutralne dla języka dla pakietu. Zawiera metadane wspólne dla wszystkich zlokalizowanych wersji składnika redystrybucyjnego.  Aby utworzyć ten plik, zobacz [How to: Create a Product Manifest](../deployment/how-to-create-a-product-manifest.md)(Jak utworzyć manifest produktu).

* Manifest pakietu, *package.xml*, zawiera metadane specyficzne dla języka; Zwykle zawiera zlokalizowane komunikaty o błędach. Składnik musi mieć co najmniej jeden manifest pakietu dla każdej zlokalizowanej wersji tego składnika. Aby utworzyć ten plik, zobacz [Jak utworzyć manifest pakietu](../deployment/how-to-create-a-package-manifest.md).

Po utworzeniu tych plików umieść plik manifestu produktu w folderze o nazwie dla niestandardowego programu inicjjącego. Plik manifestu pakietu znajduje się w folderze o nazwie dla danych regionalnych. Jeśli na przykład plik manifestu pakietu jest dla ponownej dystrybucji w języku angielskim, umieść plik w folderze o nazwie en. Powtórz ten proces dla każdego języka lokalnego, takiego jak ja dla języka japońskiego i de dla języka niemieckim. Ostateczny niestandardowy pakiet programu inicjujący może mieć następującą strukturę folderów.

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

Następnie skopiuj pliki redystrybucyjne do lokalizacji folderu programu inicjjącego. Aby uzyskać więcej informacji, [zobacz Jak utworzyć zlokalizowany pakiet programu inicjujący](../deployment/how-to-create-a-localized-bootstrapper-package.md).

```
*\Program Files (x86)\Microsoft SDKs\ClickOnce Bootstrapper\Packages*
```

lub

```
*<VS Install Path>\MSBuild\Microsoft\VisualStudio\BootstrapperPackages*
```

>[!NOTE]
>Ścieżka wymieniona powyżej w ścieżce instalacji Visual Studio działa od wersji Visual Studio 2019 Update 7.

Lokalizację folderu programu inicjjącego można również znaleźć w wartości **Ścieżka** w następującym kluczu rejestru:

```
*HKLM\Software\Microsoft\GenericBootstrapper*
```

W systemach 64-bitowych użyj następującego klucza rejestru:

```
*HKLM\Software\Wow6432Node\Microsoft\GenericBootstrapper*
```

Każdy składnik redystrybucyjnego pojawia się we własnym podfolderze w katalogu packages. Manifest produktu i pliki redystrybucyjne należy umieścić w tym podfolderze. Zlokalizowane wersje manifestów składnika i pakietu należy umieścić w podfolderach o nazwie zgodnie z nazwą kultury.

Po skopiowaniu tych plików do folderu programu inicjjącego pakiet programu inicjujący zostanie automatycznie wyświetlony w oknie dialogowym Visual Studio **Prerequisites** (Wymagania wstępne programu inicjjącego). Jeśli niestandardowy pakiet programu inicjujący nie jest wyświetlany, zamknij i otwórz ponownie **okno dialogowe Wymagania** wstępne. Aby uzyskać więcej informacji, zobacz [Okno dialogowe Wymagania wstępne.](../ide/reference/prerequisites-dialog-box.md)

W poniższej tabeli przedstawiono właściwości, które są automatycznie wypełniane przez program inicjujący.

|Właściwość|Opis|
|--------------|-----------------|
|ApplicationName|Nazwa aplikacji.|
|ProcessorArchitecture|Procesor i bity na słowo platformy docelowej dla pliku wykonywalnego. Wartości obejmują następujące elementy:<br /><br /> — Intel<br />- IA64<br />- AMD64|
|[Wersja 9x](/windows/desktop/Msi/version9x)|Numer wersji dla systemów operacyjnych Microsoft Windows 95, Windows 98 lub Windows ME. Składnia wersji to Major.Minor.ServicePack.|
|[VersionNT](/windows/desktop/Msi/versionnt)|Numer wersji dla systemów operacyjnych Windows NT, Windows 2000, Windows XP, Windows Vista, Windows Server 2008 lub Windows 7. Składnia wersji to Major.Minor.ServicePack.|
|[VersionMSI](/windows/desktop/Msi/versionmsi)|Wersja zestawu Instalator Windows (msi.dll) do uruchomienia podczas instalacji.|
|[AdministratorUser](/windows/desktop/Msi/adminuser)|Ta właściwość jest ustawiana, jeśli użytkownik ma uprawnienia administratora. Wartości mają wartość true lub false.|
|Tryb InstallMode|Tryb instalacji wskazuje, z którego miejsca należy zainstalować składnik. Wartości obejmują następujące elementy:<br /><br /> - HomeSite — wymagania wstępne są instalowane z witryny internetowej dostawcy.<br />- SpecificSite — wymagania wstępne są instalowane z wybranej lokalizacji.<br />- SameSite — wymagania wstępne są instalowane z tej samej lokalizacji co aplikacja.|

## <a name="separate-redistributables-from-application-installations"></a>Oddzielanie redystrybucji od instalacji aplikacji
Możesz zapobiec wdrażaniu plików redystrybucyjnego w projektach instalacyjnych. W tym celu utwórz listę redystrybucyjną w folderze RedistList .NET Framework katalogu:

`%ProgramFiles%\Microsoft.NET\RedistList`

Lista redystrybucyjna to plik XML, który należy nazwać przy użyciu następującego formatu: *\<Company Name> . \<Component Name>*.RedistList.xml. Jeśli więc na przykład składnik ma nazwę DataWidgets wykonany przez firmę Acme, użyj *Acme.DataWidgets.RedistList.xml*. Przykład zawartości listy redystrybucyjnej może wyglądać następująco:

```xml
<?xml version="1.0" encoding="UTF-8"?>
<FileList Redist="Acme.DataWidgets" >
<File AssemblyName="Acme.DataGrid" Version="1.0.0.0" PublicKeyToken="b03f5f7f11d50a3a" Culture="neutral" ProcessorArchitecture="MSIL" InGAC="true" />
</FileList>
```

## <a name="see-also"></a>Zobacz też
- [How to: Install prerequisites with a ClickOnce application (Instaluj wymagania wstępne za pomocą aplikacji ClickOnce)](../deployment/how-to-install-prerequisites-with-a-clickonce-application.md)
- [Okno dialogowe Wymagania wstępne](../ide/reference/prerequisites-dialog-box.md)
- [Odwołanie do schematu produktu i pakietu](../deployment/product-and-package-schema-reference.md)
- [Użyj programu inicjjącego Visual Studio 2005, aby rozpocząć instalację](/archive/msdn-magazine/2004/october/visual-studio-2005-bootstrapper-start-kick-your-installation)
