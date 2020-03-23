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
ms.sourcegitcommit: 95f26af1da51d4c83ae78adcb7372b32364d8a2b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/13/2020
ms.locfileid: "79301994"
---
# <a name="create-bootstrapper-packages"></a>Tworzenie niestandardowych pakietów programu inicjującego
Program instalacyjny jest instalatorem ogólnym, który można skonfigurować do wykrywania i instalowania redystrybucyjnych składników, takich jak pliki Instalatora Windows (*msi*) i programy wykonywalne. Instalator jest również znany jako inichuracyjny. Jest programowany za pomocą zestawu manifestów XML, które określają metadane do zarządzania instalacją składnika.  Każdy redystrybucyjny składnik lub warunek wstępny, który pojawia się w oknie dialogowym **Wymagania wstępne** dla ClickOnce jest pakietem programu inicjującego. Pakiet programu inicjującego to grupa katalogów i plików zawierających pliki manifestu, które opisują sposób instalowania wymaganego.

Program inicjał wykrywa najpierw, czy którykolwiek z wymagań wstępnych jest już zainstalowany. Jeśli wymagania wstępne nie są zainstalowane, najpierw program inicjał pokazuje umowy licencyjne. Po drugie, po zaakceptowaniu przez użytkownika końcowego umów licencyjnych rozpocznie się instalacja dla wymagań wstępnych. W przeciwnym razie jeśli zostaną wykryte wszystkie wymagania wstępne, program uruchamiany po prostu uruchamia instalator aplikacji.

## <a name="create-custom-bootstrapper-packages"></a>Tworzenie niestandardowych pakietów inicjującego
Manifesty programu inichowania można wygenerować przy użyciu edytora XML w programie Visual Studio. Aby zobaczyć przykład tworzenia pakietu inicjującego, zobacz [Przewodnik: Tworzenie niestandardowego inicjowania z monitem o prywatność](../deployment/walkthrough-creating-a-custom-bootstrapper-to-show-a-privacy-prompt.md).

Aby utworzyć pakiet programu inicjującego, należy utworzyć manifest produktu i, dla każdej zlokalizowanej wersji składnika, manifest pakietu, jak również.

* Manifest produktu, *product.xml*, zawiera wszystkie metadane neutralne dla języka dla pakietu. Zawiera metadane wspólne dla wszystkich zlokalizowanych wersji składnika redystrybucyjnego.  Aby utworzyć ten plik, zobacz [Jak: Tworzenie manifestu produktu](../deployment/how-to-create-a-product-manifest.md).

* Manifest pakietu, *package.xml*, zawiera metadane specyficzne dla języka; zazwyczaj zawiera zlokalizowane komunikaty o błędach. Składnik musi mieć co najmniej jeden manifest pakietu dla każdej zlokalizowanej wersji tego składnika. Aby utworzyć ten plik, zobacz [Jak: Tworzenie manifestu pakietu](../deployment/how-to-create-a-package-manifest.md).

Po utworzeniu tych plików umieść plik manifestu produktu w folderze nazwanym dla niestandardowego programu inichowania. Plik manifestu pakietu przechodzi do folderu o nazwie dla ustawień regionalnych. Na przykład jeśli plik manifestu pakietu jest do redystrybucji w języku angielskim, umieść plik w folderze o nazwie en. Powtórz ten proces dla każdego ustawienia regionalne, takiego jak ja dla języka japońskiego i de dla języka niemieckiego. Ostateczny niestandardowy pakiet programów inicjującego może mieć następującą strukturę folderów.

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

Następnie skopiuj pliki redystrybucyjne do lokalizacji folderu programu iniekcyjnego. Aby uzyskać więcej informacji, zobacz [Jak: Tworzenie zlokalizowanego pakietu inicjującego](../deployment/how-to-create-a-localized-bootstrapper-package.md).

```
*\Program Files (x86)\Microsoft SDKs\ClickOnce Bootstrapper*
```

lub, dla starszych wersji programu Visual Studio

```
*\Program Files\Microsoft Visual Studio 14.0\SDK\Bootstrapper\Packages*
```

lub

```
*\Program Files (x86)\Microsoft Visual Studio 14.0\SDK\Bootstrapper\Packages*
```

Lokalizację folderu programowego można również znaleźć na podstawie wartości **Ścieżka** w następującym kluczu rejestru:

```
*HKLM\Software\Microsoft\GenericBootstrapper*
```

W systemach 64-bitowych użyj następującego klucza rejestru:

```
*HKLM\Software\Wow6432Node\Microsoft\GenericBootstrapper*
```

Każdy komponent redystrybucyjny pojawia się we własnym podfolderze w katalogu pakietów. Manifest produktu i pliki redystrybucyjne muszą być umieszczone w tym podfolderze. Zlokalizowane wersje manifestów składnika i pakietu muszą być umieszczone w podfolderach o nazwie zgodnie z nazwą kultury.

Po skopiowaniu tych plików do folderu programu bootstrapper pakiet programu inicjującego automatycznie pojawia się w oknie dialogowym **Wymagania wstępne** programu Visual Studio. Jeśli niestandardowy pakiet programu inicjującego nie jest wyświetlany, zamknij, a następnie ponownie otwórz okno dialogowe **Wymagania wstępne.** Aby uzyskać więcej informacji, zobacz [Okno dialogowe Wymagania wstępne](../ide/reference/prerequisites-dialog-box.md).

W poniższej tabeli przedstawiono właściwości, które są automatycznie wypełniane przez program inichura.

|Właściwość|Opis|
|--------------|-----------------|
|ApplicationName|Nazwa aplikacji.|
|ProcessorArchitecture|Procesor i bity na słowo platformy, na które wykonywalny jest plik wykonywalny. Wartości są następujące:<br /><br /> - Firma Intel<br />- IA64<br />- AMD64|
|[Wersja 9x](/windows/desktop/Msi/version9x)|Numer wersji systemów operacyjnych Microsoft Windows 95, Windows 98 lub Windows ME. Składnia wersji to Major.Minor.ServicePack.|
|[WersjaNT](/windows/desktop/Msi/versionnt)|Numer wersji systemów operacyjnych Windows NT, Windows 2000, Windows XP, Windows Vista, Windows Server 2008 lub Windows 7. Składnia wersji to Major.Minor.ServicePack.|
|[WersjaMSI](/windows/desktop/Msi/versionmsi)|Wersja zestawu Instalatora Windows (msi.dll) do uruchomienia podczas instalacji.|
|[Administrator](/windows/desktop/Msi/adminuser)|Ta właściwość jest ustawiana, jeśli użytkownik ma uprawnienia administratora. Wartości są prawdziwe lub fałszywe.|
|Tryb instalacji|Tryb instalacji wskazuje, gdzie należy zainstalować komponent. Wartości są następujące:<br /><br /> - Strona główna - wymagania wstępne są instalowane z witryny sieci Web dostawcy.<br />- SpecificSite - wymagania wstępne są instalowane z wybranej lokalizacji.<br />- SameSite - wymagania wstępne są instalowane z tej samej lokalizacji co aplikacja.|

## <a name="separate-redistributables-from-application-installations"></a>Oddzielne redystrybucyjne od instalacji aplikacji
Można zapobiec wdrażaniu plików redystrybucyjnych w projektach instalatora. Aby to zrobić, utwórz listę redystrybucjową w folderze RedistList w katalogu .NET Framework:

`%ProgramFiles%\Microsoft.NET\RedistList`

Lista redystrybucjowa to plik XML, który należy nazwać w następującym formacie: * \<Nazwa firmy>.\<> nazwa składnika. Strona RedistList.xml*. Tak więc, na przykład, jeśli składnik jest nazywany DataWidgets przez Acme, użyj *Acme.DataWidgets.RedistList.xml*. Przykład zawartości listy redystrybucyjnej może przypominać następującą następującą:

```xml
<?xml version="1.0" encoding="UTF-8"?>
<FileList Redist="Acme.DataWidgets" >
<File AssemblyName="Acme.DataGrid" Version="1.0.0.0" PublicKeyToken="b03f5f7f11d50a3a" Culture="neutral" ProcessorArchitecture="MSIL" InGAC="true" />
</FileList>
```

## <a name="see-also"></a>Zobacz też
- [Jak: Zainstaluj wymagania wstępne za pomocą aplikacji ClickOnce](../deployment/how-to-install-prerequisites-with-a-clickonce-application.md)
- [Wstępnie wymagane składniki — Okno dialogowe](../ide/reference/prerequisites-dialog-box.md)
- [Odwołanie do schematu produktu i pakietu](../deployment/product-and-package-schema-reference.md)
- [Rozpoczęcie instalacji za pomocą programu Visual Studio 2005](https://msdn.microsoft.com/magazine/cc163899.aspx)
