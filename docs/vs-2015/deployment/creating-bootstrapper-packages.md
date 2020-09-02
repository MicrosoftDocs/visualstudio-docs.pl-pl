---
title: Tworzenie pakietów programu inicjującego | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
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
caps.latest.revision: 47
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: daf72a4466cd0f02eb6ef3a357276ed690fd26bf
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "75845519"
---
# <a name="creating-bootstrapper-packages"></a>Tworzenie pakietów programu inicjującego
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Program instalacyjny jest instalatorem ogólnym, który można skonfigurować w celu wykrywania i instalowania składników redystrybucyjnych, takich jak pliki Instalator Windows (msi) i programy wykonywalne. Instalator jest również znany jako program inicjujący. Jest on zaprogramowany przez zestaw manifestów XML, które określają metadane do zarządzania instalacją składnika.  
  
 Program inicjujący najpierw wykrywa, czy którykolwiek z wymagań wstępnych jest już zainstalowany. Jeśli wymagania wstępne nie są zainstalowane, program inicjujący wyświetli umowy licencyjne. Po drugie, po zaakceptowaniu umów licencyjnych przez użytkownika końcowego instalacja rozpocznie się z myślą o wymaganiach wstępnych. W przeciwnym razie, jeśli zostaną wykryte wszystkie wymagania wstępne, program inicjujący rozpocznie pracę Instalatora aplikacji.  
  
## <a name="creating-custom-packages"></a>Tworzenie pakietów niestandardowych  
 Można generować manifesty za pomocą edytora XML w programie Visual Studio. Aby uzyskać więcej informacji, zobacz [jak: Tworzenie manifestu pakietu](../deployment/how-to-create-a-package-manifest.md) i [instrukcje: Tworzenie manifestu produktu](../deployment/how-to-create-a-product-manifest.md). Aby zapoznać się z przykładem tworzenia pakietu programu inicjującego, zobacz [Przewodnik: Tworzenie niestandardowego programu inicjującego w celu wyświetlenia monitu o prywatność](../deployment/walkthrough-creating-a-custom-bootstrapper-to-show-a-privacy-prompt.md).  
  
 Aby utworzyć pakiet programu inicjującego, należy podać redystrybucyjny w postaci pliku EXE lub MSI file.to Generator manifestu programu inicjującego. Następnie Generator manifestu programu inicjującego tworzy następujące pliki:  
  
- Manifest produktu product.xml, który zawiera wszelkie metadane niezależne od języka pakietu. Zawiera metadane wspólne dla wszystkich zlokalizowanych wersji składnika redystrybucyjnego.  
  
- Manifest pakietu, package.xml, zawierający metadane specyficzne dla języka; zwykle zawiera zlokalizowane komunikaty o błędach. Składnik musi mieć co najmniej jeden manifest pakietu dla każdej zlokalizowanej wersji tego składnika.  
  
  Po utworzeniu tych plików Umieść plik manifestu produktu w folderze o nazwie niestandardowego programu inicjującego. Plik manifestu pakietu przechodzi do folderu o nazwie dla ustawień regionalnych. Jeśli na przykład plik manifestu pakietu jest przeznaczony do redystrybucji w języku angielskim, należy umieścić go w folderze o nazwie en. Powtórz ten proces dla każdego ustawienia regionalnego, takiego jak ja dla języka japońskiego i Cofnij dla języka niemieckiego. Ostatni niestandardowy pakiet programu inicjującego może mieć następującą strukturę folderów.  
  
  `CustomBootstrapperPackage`  
  
  `product.xml`  
  
  `CustomBootstrapper.msi`  
  
  `de`  
  
  `eula.rtf`  
  
  `package.xml`  
  
  `en`  
  
  `eula.rtf`  
  
  `package.xml`  
  
  `ja`  
  
  `eula.rtf`  
  
  `package.xml`  
  
  Na koniec skopiuj pliki redystrybucyjne do lokalizacji folderu programu inicjującego. Aby uzyskać więcej informacji, zobacz [How to: Create a zlokalizowany pakiet programu inicjującego](../deployment/how-to-create-a-localized-bootstrapper-package.md).  
  
```  
\Program Files\Microsoft Visual Studio 14.0\SDK\Bootstrapper\Packages  
```  
  
 lub  
  
```  
\Program Files (x86)\Microsoft Visual Studio 14.0\SDK\Bootstrapper\Packages  
```  
  
 Można również określić lokalizację folderu programu inicjującego na podstawie wartości **Path** w następującym kluczu rejestru:  
  
```  
HKLM\Software\Microsoft\GenericBootstrapper\11.0  
```  
  
 W systemach 64 bitowych należy użyć następującego klucza rejestru:  
  
```  
HKLM\Software\Wow6432Node\Microsoft\GenericBootstrapper\11.0  
```  
  
 Każdy składnik redystrybucyjny pojawia się w osobnym podfolderze katalogu Packages. Manifest produktu i pliki redystrybucyjne są umieszczane w tym podfolderze. Zlokalizowane wersje składników i manifestów pakietów są umieszczane w podfolderach o nazwach zgodnych z nazwą kultury.  
  
 Po skopiowaniu tych plików do folderu programu inicjującego pakiet programu inicjującego automatycznie pojawia się w oknie dialogowym wymagania wstępne programu Visual Studio. Jeśli niestandardowy pakiet programu inicjującego nie jest wyświetlany, Zamknij i ponownie otwórz okno dialogowe wymagania wstępne. Aby uzyskać więcej informacji, zobacz [okno dialogowe wymagania wstępne](../ide/reference/prerequisites-dialog-box.md).  
  
 W poniższej tabeli przedstawiono właściwości, które są automatycznie wypełniane przez program inicjujący.  
  
|Właściwość|Opis|  
|--------------|-----------------|  
|ApplicationName|Nazwa aplikacji.|  
|ProcessorArchitecture|Procesor i bity dla poszczególnych wyrazów platformy, do których odnoszą się pliki wykonywalne. Dostępne są następujące wartości:<br /><br /> — Intel<br />— IA64<br />-AMD64|  
|[Version9x](https://msdn.microsoft.com/library/aa372490\(v=vs.140\).aspx)|Numer wersji dla systemów operacyjnych Microsoft Windows 95, Windows 98 lub Windows ME. Składnia wersji to główna. pomocnicza. dodatek Service Pack.|  
|[VersionNT](/windows/desktop/Msi/versionnt)|Numer wersji dla systemów operacyjnych Windows NT, Windows 2000, Windows XP, Windows Vista, Windows Server 2008 lub Windows 7. Składnia wersji to główna. pomocnicza. dodatek Service Pack.|  
|[VersionMSI](https://msdn.microsoft.com/library/aa372493\(v=vs.140\).aspx)|Wersja zestawu Instalator Windows (msi.dll) uruchamiana podczas instalacji.|  
|[AdminUser](https://msdn.microsoft.com/library/aa367545\(v=vs.140\).aspx)|Ta właściwość jest ustawiona, jeśli użytkownik ma uprawnienia administratora. Wartości mają wartość true lub false.|  
|Installmode|Tryb instalacji wskazuje, gdzie należy zainstalować składnik. Dostępne są następujące wartości:<br /><br /> -HomeSite — wymagania wstępne są instalowane z witryny sieci Web dostawcy.<br />-SpecificSite — wymagania wstępne są instalowane z wybranej lokalizacji.<br />-SameSite — wymagania wstępne są instalowane z tej samej lokalizacji, w której znajduje się aplikacja.|  
  
## <a name="separating-redistributables-from-application-installations"></a>Oddzielanie redystrybucyjnych od instalacji aplikacji  
 Można zapobiec wdrażaniu plików redystrybucyjnych w projektach instalacyjnych. W tym celu Utwórz listę redystrybucyjną w folderze RedistList w katalogu .NET Framework:  
  
 `%ProgramFiles%\Microsoft.NET\RedistList`  
  
 Lista redystrybucyjna to plik XML, który należy nazwać, używając następującego formatu: *Nazwa firmy*. *Nazwa składnika*.RedistList.xml. Tak więc, na przykład, jeśli składnik jest wywoływany przez Acme, użyj Acme.DataWidgets.RedistList.xml. Przykład zawartości listy redystrybucyjnej może wyglądać następująco:  
  
```  
<?xml version="1.0" encoding="UTF-8"?>  
<FileList Redist="Acme.DataWidgets" >  
<File AssemblyName="Acme.DataGrid" Version="1.0.0.0" PublicKeyToken="b03f5f7f11d50a3a" Culture="neutral" ProcessorArchitecture="MSIL" InGAC="true" />  
</FileList>  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Instrukcje: instalowanie wstępnie wymaganych składników za pomocą aplikacji ClickOnce](../deployment/how-to-install-prerequisites-with-a-clickonce-application.md)   
 [Wymagania wstępne — okno dialogowe](../ide/reference/prerequisites-dialog-box.md)   
 [Dokumentacja schematu produktu i pakietu](../deployment/product-and-package-schema-reference.md)   
 [Aby rozpocząć instalację, użyj programu inicjującego Visual Studio 2005](https://msdn.microsoft.com/magazine/cc163899.aspx)
