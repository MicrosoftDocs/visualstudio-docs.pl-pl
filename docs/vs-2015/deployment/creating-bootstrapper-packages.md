---
title: Tworzenie pakietów programu inicjującego | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: 89bb8b28333bd7607dda9515a137bd75283a9e5f
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54779826"
---
# <a name="creating-bootstrapper-packages"></a>Tworzenie pakietów programu inicjującego
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Setup program jest generycznym Instalatorem, który można skonfigurować, aby wykrywać i instalować składników pakietu redystrybucyjnego, takie jak pliki Instalatora Windows (msi) i programy wykonywalne. Instalator jest również znany jako program inicjujący. Jest programowane za pomocą zestawu manifestów XML, które określają metadane w celu zarządzania instalacją składnika.  
  
 Program inicjujący najpierw wykrywa, czy dowolny z wymagań wstępnych są już zainstalowane. Jeśli wymagania wstępne nie są zainstalowane, najpierw program inicjujący wyświetli umów licencyjnych. Po drugie, po użytkownik końcowy akceptuje umów licencyjnych, rozpocznie się instalacja dla wymagań wstępnych. W przeciwnym razie jeśli zostaną wykryte wszystkie wymagania wstępne, program inicjujący tylko uruchamia Instalatora aplikacji.  
  
## <a name="creating-custom-packages"></a>Tworzenie pakietów niestandardowych  
 Można wygenerować manifestów za pomocą edytora XML w programie Visual Studio. Aby uzyskać więcej informacji, zobacz [jak: Tworzenie manifestu pakietu](../deployment/how-to-create-a-package-manifest.md) i [jak: Tworzenie manifestu produktu](../deployment/how-to-create-a-product-manifest.md). Aby zobaczyć przykład utworzenia pakietu bootstrapper, zobacz [instruktażu: Tworzenie niestandardowego programu inicjującego wyświetlającego monit zasad ochrony prywatności](../deployment/walkthrough-creating-a-custom-bootstrapper-to-show-a-privacy-prompt.md).  
  
 Aby utworzyć pakiet bootstrapper, musisz dostarczyć redystrybucyjne w formie file.to pliku EXE lub MSI do generatora manifestu Bootstrapper. Następnie Manifest generatora Bootstrapper tworzy następujące pliki:  
  
- Manifest produktu, product.xml, który zawiera wszystkie metadane niezależny od języka dla pakietu. Zawiera to metadane wspólne dla wszystkich lokalizowanych wersji komponentu do redystrybucji.  
  
- Manifest pakietu, package.xml, który zawiera metadane specyficzne dla języka; typowo zawiera lokalizowane komunikaty o błędzie. Składnik musi mieć co najmniej jeden manifest pakietu dla każdej zlokalizowanej wersji tego składnika.  
  
  Po utworzeniu tych plików, należy umieścić plik manifestu produktu w folderze o nazwie niestandardowy program inicjujący. Plik manifestu pakietu przechodzi do folderu nazwanego na podstawie lokalizacji. Na przykład w przypadku pliku manifestu pakietu do redystrybucji w języku angielskim, należy umieścić plik w folderze o nazwie en. Powtórz ten proces dla poszczególnych ustawień regionalnych, takich jak ja w języku japońskim i "de" dla języka niemieckiego. Końcowe niestandardowy pakiet programu inicjującego może mieć następującą strukturę folderów.  
  
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
  
  Na koniec skopiuj przeznaczone do redystrybucji pliki do folderu programu inicjującego. Aby uzyskać więcej informacji, zobacz [jak: Tworzenie zlokalizowanego pakietu programu inicjującego](../deployment/how-to-create-a-localized-bootstrapper-package.md).  
  
```  
\Program Files\Microsoft Visual Studio 14.0\SDK\Bootstrapper\Packages  
```  
  
 lub  
  
```  
\Program Files (x86)\Microsoft Visual Studio 14.0\SDK\Bootstrapper\Packages  
```  
  
 Możesz również określić lokalizacje folderu Bootstrapper z **ścieżki** wartość w następującym kluczu rejestru:  
  
```  
HKLM\Software\Microsoft\GenericBootstrapper\11.0  
```  
  
 W systemach 64-bitowy należy użyć następującego klucza rejestru:  
  
```  
HKLM\Software\Wow6432Node\Microsoft\GenericBootstrapper\11.0  
```  
  
 Każdy składnik redystrybucyjny jest wyświetlany w podfolderze katalogu pakietów. Produkt plików manifestu i redystrybucyjne są umieszczane w tym podfolderze. Zlokalizowane wersje składników i wykazu manifestów są umieszczane w podfolderach nazwanych zgodnie z nazwami kultur.  
  
 Po te pliki są kopiowane do folderu Program inicjujący, pakiet inicjujący automatycznie pojawia się w oknie dialogowym wstępnie wymagane składniki programu Visual Studio. Jeśli pakiet niestandardowego programu inicjującego nie jest widoczny, zamknij i ponownie otwórz okno dialogowe wymagań wstępnych. Aby uzyskać więcej informacji, zobacz [wstępnie wymagane składniki, okno dialogowe](../ide/reference/prerequisites-dialog-box.md).  
  
 W poniższej tabeli przedstawiono właściwości, które są wypełniane automatycznie przez program inicjujący.  
  
|Właściwość|Opis|  
|--------------|-----------------|  
|ApplicationName|Nazwa aplikacji.|  
|ProcessorArchitecture|Procesor i bity na słowo platformy docelowej przez plik wykonywalny. Następujące wartości:<br /><br /> -Firmy Intel<br />-IA64<br />-AMD64|  
|[Version9x](https://msdn.microsoft.com/library/aa372490\(v=vs.140\).aspx)|Numer wersji systemów operacyjnych Microsoft Windows 95, Windows 98 lub Windows ME. Składnia wersji to Major.Minor.ServicePack.|  
|[VersionNT](https://msdn.microsoft.com/library/aa372495\(v=vs.140\).xaspx)|Numer wersji dla systemów operacyjnych Windows NT, Windows 2000, Windows XP, Windows Vista, Windows Server 2008 lub Windows 7. Składnia wersji to Major.Minor.ServicePack.|  
|[VersionMSI](https://msdn.microsoft.com/library/aa372493\(v=vs.140\).aspx)|Wersja zestawu Instalatora Windows (msi.dll) uruchomiona podczas instalacji.|  
|[AdminUser](https://msdn.microsoft.com/library/aa367545\(v=vs.140\).aspx)|Ta właściwość jest ustawiona, jeśli użytkownik ma uprawnienia administratora. Wartości są prawdziwe lub fałszywe.|  
|Tryb instalacji|Tryb instalacji wskazuje, gdzie mają zostać zainstalowane z składnika. Następujące wartości:<br /><br /> -HomeSite - wstępnie wymagane składniki są instalowane z witryny sieci Web dostawcy.<br />-SpecificSite — wymagania wstępne są instalowane z wybranej lokalizacji.<br />-SameSite — wymagania wstępne są instalowane z tej samej lokalizacji co aplikacja.|  
  
## <a name="separating-redistributables-from-application-installations"></a>Oddzielenie pakietów redystrybucyjnych od instalacji aplikacji  
 Aby uniemożliwić Twoich plików redystrybucyjnych w projektach konfiguracji wdrożenia. Aby to zrobić, Utwórz redystrybucyjną listę w folderze RedistList w katalogu .NET Framework:  
  
 `%ProgramFiles%\Microsoft.NET\RedistList`  
  
 Redystrybucyjna lista jest plikiem XML, należy nadać nazwę w następującym formacie: *Nazwa firmy*. *Nazwa składnika*. RedistList.xml. Tak na przykład, jeśli składnik ten jest wywoływany przez Acme Datawidgets, użyj Acme.DataWidgets.RedistList.xml. Przykład zawartości listy do dystrybucji może wyglądać następująco:  
  
```  
<?xml version="1.0" encoding="UTF-8"?>  
<FileList Redist="Acme.DataWidgets" >  
<File AssemblyName="Acme.DataGrid" Version="1.0.0.0" PublicKeyToken="b03f5f7f11d50a3a" Culture="neutral" ProcessorArchitecture="MSIL" InGAC="true" />  
</FileList>  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Instrukcje: Instalowanie wymagań wstępnych przy użyciu aplikacji ClickOnce](../deployment/how-to-install-prerequisites-with-a-clickonce-application.md)   
 [Wymagania wstępne, okno dialogowe](../ide/reference/prerequisites-dialog-box.md)   
 [Produkt i pakiet — dokumentacja schematu](../deployment/product-and-package-schema-reference.md)   
 [Użyj programu Visual Studio 2005 Bootstrapper, aby uruchomić instalację](http://go.microsoft.com/fwlink/?LinkId=107537)
