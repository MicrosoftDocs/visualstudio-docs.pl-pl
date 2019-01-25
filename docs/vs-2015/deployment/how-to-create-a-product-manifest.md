---
title: 'Instrukcje: Tworzenie manifestu produktu | Dokumentacja firmy Microsoft'
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
- product files [ClickOnce]
- product files [Windows Installer]
- prerequisites, custom bootstrapper package
- dependencies, custom bootstrapper package
ms.assetid: 2d316aaa-8bc0-4ce5-90ab-23b3eac0b5dd
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 948cbe88f39b0a39fc23ff8307c3e3484fb9438c
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54788631"
---
# <a name="how-to-create-a-product-manifest"></a>Instrukcje: Tworzenie manifestu produktu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Aby wdrożyć wymagania wstępne dotyczące aplikacji, można utworzyć pakietu programu inicjującego. Pakiet programu inicjującego zawiera pojedynczy plik manifestu produktu ale manifest pakietu dla poszczególnych ustawień regionalnych. Manifest pakietu zawiera aspekty specyficzne dla lokalizacji pakietu. W tym ciągi, Umowa licencyjna użytkownika oprogramowania i pakietów językowych.  
  
 Aby uzyskać więcej informacji na temat manifestów produktu, zobacz [jak: Tworzenie manifestu pakietu](../deployment/how-to-create-a-package-manifest.md).  
  
## <a name="creating-the-product-manifest"></a>Tworzenie manifestu produktu  
  
#### <a name="to-create-the-product-manifest"></a>Aby utworzyć manifest produktu  
  
1.  Utwórz katalog dla pakietu programu inicjującego. W tym przykładzie użyto C:\package.  
  
2.  W programie Visual Studio Utwórz nowy plik XML o nazwie `product.xml`i zapisz go w folderze C:\package.  
  
3.  Dodaj następujący kod XML opisujący przestrzeni nazw i produktu kod XML dla pakietu. Zastąp kod produktu o unikatowym identyfikatorze dla pakietu.  
  
    ```  
    <Product  
    xmlns="http://schemas.microsoft.com/developer/2004/01/bootstrapper"   
    ProductCode="Custom.Bootstrapper.Package">  
    ```  
  
4.  Dodaj kod XML, aby określić, czy pakiet ma zależność. W tym przykładzie użyto zależność w systemie Microsoft Windows Installer 3.1.  
  
    ```  
    <RelatedProducts>  
        <DependsOnProduct Code="Microsoft.Windows.Installer.3.1" />  
      </RelatedProducts>  
    ```  
  
5.  Dodaj kod XML, aby wyświetlić listę wszystkich plików, które należą do pakietu programu inicjującego. W tym przykładzie używa nazwy pliku pakietu CorePackage.msi.  
  
    ```  
    <PackageFiles>  
        <PackageFile Name="CorePackage.msi"/>  
    </PackageFiles>  
    ```  
  
6.  Skopiuj lub Przenieś plik CorePackage.msi do folderu C:\package.  
  
7.  Dodaj kod XML, aby zainstalować pakiet przy użyciu poleceń programu inicjującego. Program inicjujący automatycznie dodaje **/qn** flagi do pliku .msi, co spowoduje zainstalowanie w trybie dyskretnym. Jeśli plik .exe, program inicjujący uruchamia plik .exe przy użyciu powłoki. Następujący kody XML pokazuje bez argumentów do CorePackage.msi, ale argument wiersza polecenia można umieścić w atrybucie argumentów.  
  
    ```  
    <Commands>  
        <Command PackageFile="CorePackage.msi" Arguments="">  
    ```  
  
8.  Dodaj następujący kod XML, aby sprawdzić, czy zainstalowano ten pakiet programu inicjującego. Zastąp kod produktu o identyfikatorze GUID dla składnik redystrybucyjny.  
  
    ```  
    <InstallChecks>  
        <MsiProductCheck   
            Property="IsMsiInstalled"   
            Product="{XXXXXXX-XXXX-XXXX-XXXX-XXXXXXXXXXXX}"/>  
    </InstallChecks>  
    ```  
  
9. Dodaj kod XML, aby zmienić zachowanie programu inicjującego zależnie od tego, jeśli jest już zainstalowany składnik programu inicjującego. Jeśli zainstalowano składnik pakietu programu inicjującego nie działa. Następujący kod XML sprawdza, czy aktualny użytkownik ma uprawnienia administratora, ponieważ ten składnik wymaga uprawnień administracyjnych.  
  
    ```  
    <InstallConditions>  
        <BypassIf   
           Property="IsMsiInstalled"   
           Compare="ValueGreaterThan" Value="0"/>  
        <FailIf Property="AdminUser"   
            Compare="ValueNotEqualTo" Value="True"  
            String="NotAnAdmin"/>  
    </InstallConditions>  
    ```  
  
10. Dodaj kod XML, aby ustawić kody zakończenia, jeśli instalacja się powiodła, a jeśli konieczne jest ponowne uruchomienie komputera. Następujący kod XML pokazuje, że zakończy się niepowodzeniem i FailReboot wyjść kodów, które wskazują, że program inicjujący nie będzie kontynuowana, instalowanie pakietów.  
  
    ```  
    <ExitCodes>  
        <ExitCode Value="0" Result="Success"/>  
        <ExitCode Value="1641" Result="SuccessReboot"/>  
        <ExitCode Value="3010" Result="SuccessReboot"/>  
        <DefaultExitCode Result="Fail" String="GeneralFailure"/>  
    </ExitCodes>  
    ```  
  
11. Dodaj następujący kod XML do końca sekcji dla poleceń programu inicjującego.  
  
    ```  
        </Command>  
    </Commands>  
    ```  
  
12. Przenieś C:\package folder katalogu program inicjujący Instalatora programu Visual Studio. Dla programu Visual Studio 2010 to jest katalog SDKs\Windows\v7.0A\Bootstrapper\Packages \Program Files\Microsoft.  
  
## <a name="example"></a>Przykład  
 Manifest produktu zawiera instrukcje dotyczące instalacji niestandardowej wstępnie wymaganych składników.  
  
```  
<?xml version="1.0" encoding="utf-8" ?>  
<Product  
  xmlns="http://schemas.microsoft.com/developer/2004/01/bootstrapper"  
  ProductCode="Custom.Bootstrapper.Package">  
  
  <RelatedProducts>  
    <DependsOnProduct Code="Microsoft.Windows.Installer.3.1" />  
  </RelatedProducts>  
  
  <PackageFiles>  
    <PackageFile Name="CorePackage.msi"/>  
  </PackageFiles>  
  
  <InstallChecks>  
    <MsiProductCheck Product="IsMsiInstalled"   
      Property="{XXXXXXXX-XXXX-XXXX-XXXX-XXXXXXXXXXXX}"/>  
  </InstallChecks>  
  
  <Commands>  
    <Command PackageFile="CorePackage.msi" Arguments="">  
  
      <InstallConditions>  
        <BypassIf Property="IsMsiInstalled"  
          Compare="ValueGreaterThan" Value="0"/>  
        <FailIf Property="AdminUser"   
          Compare="ValueNotEqualTo" Value="True"  
         String="NotAnAdmin"/>  
      </InstallConditions>  
  
      <ExitCodes>  
        <ExitCode Value="0" Result="Success"/>  
        <ExitCode Value="1641" Result="SuccessReboot"/>  
        <ExitCode Value="3010" Result="SuccessReboot"/>  
        <DefaultExitCode Result="Fail" String="GeneralFailure"/>  
      </ExitCodes>  
    </Command>  
  </Commands>  
</Product>  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Produkt i pakiet — dokumentacja schematu](../deployment/product-and-package-schema-reference.md)
