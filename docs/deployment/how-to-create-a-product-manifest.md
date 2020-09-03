---
title: Jak utworzyć manifest produktu | Microsoft Docs
ms.date: 11/04/2016
ms.topic: how-to
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
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f0f4302756b089376eca8926453399768faaf58f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "85382513"
---
# <a name="how-to-create-a-product-manifest"></a>Instrukcje: tworzenie manifestu produktu
Aby wdrożyć wymagania wstępne dla aplikacji, można utworzyć pakiet programu inicjującego. Pakiet programu inicjującego zawiera jeden plik manifestu produktu, ale manifest pakietu dla każdego ustawienia regionalnego. Manifest pakietu zawiera aspekty dotyczące lokalizacji pakietu. Dotyczy to również ciągów, umów licencyjnych użytkowników końcowych i pakietów językowych.

 Aby uzyskać więcej informacji o manifestach pakietów, zobacz [How to: Create a Package manifest](../deployment/how-to-create-a-package-manifest.md).

## <a name="create-the-product-manifest"></a>Tworzenie manifestu produktu

#### <a name="to-create-the-product-manifest"></a>Aby utworzyć manifest produktu

1. Utwórz katalog dla pakietu programu inicjującego. W tym przykładzie używa C:\Package.

2. W programie Visual Studio Utwórz nowy plik XML o nazwie *product.xml*i Zapisz go w folderze *C:\Package* .

3. Dodaj następujący kod XML, aby opisać przestrzeń nazw XML i kod produktu pakietu. Zastąp kod produktu unikatowym identyfikatorem pakietu.

    ```xml
    <Product
    xmlns="http://schemas.microsoft.com/developer/2004/01/bootstrapper"
    ProductCode="Custom.Bootstrapper.Package">
    ```

4. Dodaj plik XML, aby określić, że pakiet ma zależność. W tym przykładzie zastosowano zależność od firmy Microsoft Instalator Windows 3,1.

    ```xml
    <RelatedProducts>
        <DependsOnProduct Code="Microsoft.Windows.Installer.3.1" />
      </RelatedProducts>
    ```

5. Dodaj plik XML, aby wyświetlić listę wszystkich plików, które znajdują się w pakiecie programu inicjującego. W tym przykładzie użyta zostanie nazwa pliku pakietu *CorePackage.msi*.

    ```xml
    <PackageFiles>
        <PackageFile Name="CorePackage.msi"/>
    </PackageFiles>
    ```

6. Skopiuj lub Przenieś plik *CorePackage.msi* do folderu *C:\Package* .

7. Dodaj plik XML, aby zainstalować pakiet za pomocą poleceń programu inicjującego. Program inicjujący automatycznie dodaje do pliku *MSI* flagę **/Qn** , która zostanie zainstalowana w trybie dyskretnym. Jeśli plik jest plikiem *exe*, program inicjujący uruchamia plik *. exe* przy użyciu powłoki. Poniższy kod XML nie zawiera argumentów do *CorePackage.msi*, ale można umieścić argument wiersza polecenia w `Arguments` atrybucie.

    ```xml
    <Commands>
        <Command PackageFile="CorePackage.msi" Arguments="">
    ```

8. Dodaj następujący kod XML, aby sprawdzić, czy ten pakiet programu inicjującego został zainstalowany. Zastąp kod produktu identyfikatorem GUID składnika redystrybucyjnego.

    ```xml
    <InstallChecks>
        <MsiProductCheck
            Property="IsMsiInstalled"
            Product="{XXXXXXX-XXXX-XXXX-XXXX-XXXXXXXXXXXX}"/>
    </InstallChecks>
    ```

9. Dodaj kod XML, aby zmienić zachowanie programu inicjującego w zależności od tego, czy składnik programu inicjującego jest już zainstalowany. Jeśli składnik jest zainstalowany, nie zostanie uruchomiony pakiet programu inicjującego. Poniższe XML sprawdza, czy bieżący użytkownik jest administratorem, ponieważ ten składnik wymaga uprawnień administracyjnych.

    ```xml
    <InstallConditions>
        <BypassIf
           Property="IsMsiInstalled"
           Compare="ValueGreaterThan" Value="0"/>
        <FailIf Property="AdminUser"
            Compare="ValueNotEqualTo" Value="True"
            String="NotAnAdmin"/>
    </InstallConditions>
    ```

10. Dodaj kod XML, aby ustawić kody zakończenia, jeśli instalacja zakończy się pomyślnie i jeśli konieczne jest ponowne uruchomienie komputera. W poniższym kodzie XML przedstawiono kody zakończenia niepowodzenia i FailReboot, które wskazują, że program inicjujący nie będzie kontynuował instalowania pakietów.

    ```xml
    <ExitCodes>
        <ExitCode Value="0" Result="Success"/>
        <ExitCode Value="1641" Result="SuccessReboot"/>
        <ExitCode Value="3010" Result="SuccessReboot"/>
        <DefaultExitCode Result="Fail" String="GeneralFailure"/>
    </ExitCodes>
    ```

11. Dodaj następujący kod XML, aby zakończyć sekcję poleceń programu inicjującego.

    ```xml
        </Command>
    </Commands>
    ```

12. Przenieś folder *C:\Package* do katalogu inicjującego programu Visual Studio. W przypadku programu Visual Studio 2010 jest to katalog *\Program Files\Microsoft SDKs\Windows\v7.0A\Bootstrapper\Packages* .

## <a name="example"></a>Przykład
 Manifest produktu zawiera instrukcje dotyczące instalacji niestandardowych wymagań wstępnych.

```xml
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
- [Dokumentacja schematu produktu i pakietu](../deployment/product-and-package-schema-reference.md)