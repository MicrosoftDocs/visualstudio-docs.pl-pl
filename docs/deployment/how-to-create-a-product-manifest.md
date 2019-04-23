---
title: 'Instrukcje: Tworzenie manifestu produktu | Dokumentacja firmy Microsoft'
ms.date: 11/04/2016
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
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 68f3006104b50876f6d2716ff4eb1efe0a705284
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "60057410"
---
# <a name="how-to-create-a-product-manifest"></a>Instrukcje: Tworzenie manifestu produktu
Aby wdrożyć wymagania wstępne dotyczące aplikacji, można utworzyć pakietu programu inicjującego. Pakiet programu inicjującego zawiera pojedynczy plik manifestu produktu ale manifest pakietu dla poszczególnych ustawień regionalnych. Manifest pakietu zawiera aspekty specyficzne dla lokalizacji pakietu. W tym ciągi, Umowa licencyjna użytkownika oprogramowania i pakietów językowych.

 Aby uzyskać więcej informacji na temat manifestów pakietu zobacz [jak: Tworzenie manifestu pakietu](../deployment/how-to-create-a-package-manifest.md).

## <a name="create-the-product-manifest"></a>Tworzenie manifestu produktu

#### <a name="to-create-the-product-manifest"></a>Aby utworzyć manifest produktu

1. Utwórz katalog dla pakietu programu inicjującego. W tym przykładzie użyto C:\package.

2. W programie Visual Studio Utwórz nowy plik XML o nazwie *product.xml*i zapisać go w celu *C:\package* folderu.

3. Dodaj następujący kod XML opisujący przestrzeni nazw i produktu kod XML dla pakietu. Zastąp kod produktu o unikatowym identyfikatorze dla pakietu.

    ```xml
    <Product
    xmlns="http://schemas.microsoft.com/developer/2004/01/bootstrapper"
    ProductCode="Custom.Bootstrapper.Package">
    ```

4. Dodaj kod XML, aby określić, czy pakiet ma zależność. W tym przykładzie użyto zależność w systemie Microsoft Windows Installer 3.1.

    ```xml
    <RelatedProducts>
        <DependsOnProduct Code="Microsoft.Windows.Installer.3.1" />
      </RelatedProducts>
    ```

5. Dodaj kod XML, aby wyświetlić listę wszystkich plików, które należą do pakietu programu inicjującego. W tym przykładzie użyto nazwa pliku pakietu *CorePackage.msi*.

    ```xml
    <PackageFiles>
        <PackageFile Name="CorePackage.msi"/>
    </PackageFiles>
    ```

6. Kopiowanie lub przenoszenie *CorePackage.msi* plik *C:\package* folderu.

7. Dodaj kod XML, aby zainstalować pakiet przy użyciu poleceń programu inicjującego. Program inicjujący automatycznie dodaje **/qn** flaga *.msi* pliku, który zostanie zainstalowany w trybie dyskretnym. Jeśli plik jest *.exe*, uruchamia program inicjujący *.exe* plików przy użyciu powłoki. Następujący kody XML pokazuje bez argumentów do *CorePackage.msi*, ale można umieścić argument wiersza polecenia do `Arguments` atrybutu.

    ```xml
    <Commands>
        <Command PackageFile="CorePackage.msi" Arguments="">
    ```

8. Dodaj następujący kod XML, aby sprawdzić, czy zainstalowano ten pakiet programu inicjującego. Zastąp kod produktu o identyfikatorze GUID dla składnik redystrybucyjny.

    ```xml
    <InstallChecks>
        <MsiProductCheck
            Property="IsMsiInstalled"
            Product="{XXXXXXX-XXXX-XXXX-XXXX-XXXXXXXXXXXX}"/>
    </InstallChecks>
    ```

9. Dodaj kod XML, aby zmienić zachowanie programu inicjującego zależnie od tego, jeśli jest już zainstalowany składnik programu inicjującego. Jeśli zainstalowano składnik pakietu programu inicjującego nie działa. Następujący kod XML sprawdza, czy aktualny użytkownik ma uprawnienia administratora, ponieważ ten składnik wymaga uprawnień administracyjnych.

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

10. Dodaj kod XML, aby ustawić kody zakończenia, jeśli instalacja się powiodła, a jeśli konieczne jest ponowne uruchomienie komputera. Następujący kod XML pokazuje, że zakończy się niepowodzeniem i FailReboot wyjść kodów, które wskazują, że program inicjujący nie będzie kontynuowana, instalowanie pakietów.

    ```xml
    <ExitCodes>
        <ExitCode Value="0" Result="Success"/>
        <ExitCode Value="1641" Result="SuccessReboot"/>
        <ExitCode Value="3010" Result="SuccessReboot"/>
        <DefaultExitCode Result="Fail" String="GeneralFailure"/>
    </ExitCodes>
    ```

11. Dodaj następujący kod XML do końca sekcji dla poleceń programu inicjującego.

    ```xml
        </Command>
    </Commands>
    ```

12. Przenieś *C:\package* folder w katalogu program inicjujący Instalatora programu Visual Studio. W przypadku programu Visual Studio 2010, jest *\Program Files\Microsoft SDKs\Windows\v7.0A\Bootstrapper\Packages* katalogu.

## <a name="example"></a>Przykład
 Manifest produktu zawiera instrukcje dotyczące instalacji niestandardowej wstępnie wymaganych składników.

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

## <a name="see-also"></a>Zobacz także
- [Odwołanie do schematu produktu i pakietu](../deployment/product-and-package-schema-reference.md)