---
title: 'Instrukcje: Tworzenie manifestu pakietu | Dokumentacja firmy Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- package files [Windows Installer]
- package files [ClickOnce]
- prerequisites, custom bootstrapper package
- dependencies, custom bootstrapper packages
ms.assetid: 5aecc507-2764-42f2-ae6f-c227971cf0af
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d8083ca9a8d3025b1760edde96279a0cd557f722
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62899743"
---
# <a name="how-to-create-a-package-manifest"></a>Instrukcje: Tworzenie manifestu pakietu
Aby wdrożyć wymagania wstępne dotyczące aplikacji, można użyć pakietu programu inicjującego. Pakiet programu inicjującego zawiera pojedynczy plik manifestu produktu ale manifest pakietu dla poszczególnych ustawień regionalnych. Zestawu funkcji wspólnych w różnych wersjach zlokalizowanych powinny należeć do manifestu produktu.

 Aby uzyskać więcej informacji na temat manifestów produktu, zobacz [jak: Tworzenie manifestu produktu](../deployment/how-to-create-a-product-manifest.md).

## <a name="create-the-package-manifest"></a>Tworzenie manifestu pakietu

#### <a name="to-create-the-package-manifest"></a>Aby utworzyć manifest pakietu

1. Utwórz katalog dla pakietu programu inicjującego. W tym przykładzie użyto *C:\package*.

2. Utwórz podkatalog o nazwie ustawień regionalnych, takich jak *en* w języku angielskim.

3. W programie Visual Studio, należy utworzyć plik XML, który nosi nazwę *package.xml*i zapisać go w celu *C:\package\en* folderu.

4. Dodaj kod XML, aby wyświetlić listę Nazwa pakietu programu inicjującego, kultura tego manifestu pakietu zlokalizowane i umowę licencyjną opcjonalne. Następujący kod XML używa zmiennych `DisplayName` i `Culture`, które są określone w elemencie nowsze.

    ```xml
    <Package
        xmlns="http://schemas.microsoft.com/developer/2004/01/bootstrapper"
        Name="DisplayName"
        Culture="Culture"
        LicenseAgreement="eula.txt">
    ```

5. Dodaj kod XML, aby wyświetlić listę wszystkich plików, które znajdują się w katalogu specyficzny dla ustawień regionalnych. Następujący kod XML, używany jest plik o nazwie *eula.txt* który jest odpowiedni dla **en** ustawień regionalnych.

    ```xml
    <PackageFiles>
      <PackageFile Name="eula.txt"/>
    </PackageFiles>
    ```

6. Dodaj kod XML do definiowania możliwych do zlokalizowania ciągi dla pakietu programu inicjującego. Następujący kod XML dodaje ciągi błędów dla **en** ustawień regionalnych.

    ```xml
      <Strings>
        <String Name="DisplayName">Custom Bootstrapper Package</String>
        <String Name="CultureName">en</String>
        <String Name="NotAnAdmin">You must be an administrator to install
    this package.</String>
        <String Name="GeneralFailure">A general error has occurred while
    installing this package.</String>
    </Strings>
    ```

7. Kopiuj *C:\package* folder w katalogu program inicjujący Instalatora programu Visual Studio. W przypadku programu Visual Studio 2010, jest *\Program Files\Microsoft SDKs\Windows\v7.0A\Bootstrapper\Packages* katalogu.

## <a name="example"></a>Przykład
 Manifest pakietu zawiera informacje specyficzne dla ustawień regionalnych, takie jak komunikaty o błędach, postanowienia licencyjne dotyczące oprogramowania i pakietów językowych.

```xml
<?xml version="1.0" encoding="utf-8" ?>
<Package
  xmlns="http://schemas.microsoft.com/developer/2004/01/bootstrapper"
  Name="DisplayName"
  Culture="Culture"
  LicenseAgreement="eula.txt">

  <PackageFiles>
    <PackageFile Name="eula.txt"/>
  </PackageFiles>

  <Strings>
    <String Name="DisplayName">Custom Bootstrapper Package</String>
    <String Name="Culture">en</String>
    <String Name="NotAnAdmin">You must be an administrator to install this package.</String>
    <String Name="GeneralFailure">A general error has occurred while
installing this package.</String>
  </Strings>
</Package>
```

## <a name="see-also"></a>Zobacz także
- [Odwołanie do schematu produktu i pakietu](../deployment/product-and-package-schema-reference.md)