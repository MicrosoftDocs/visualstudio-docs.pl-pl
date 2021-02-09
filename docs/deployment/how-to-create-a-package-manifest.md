---
title: Tworzenie manifestu pakietu | Microsoft Docs
description: Dowiedz się więcej o używaniu pakietu programu inicjującego do wdrażania wymagań wstępnych dla aplikacji ClickOnce, która zawiera manifest pakietu dla każdego ustawienia regionalnego.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: cef6cd23a1e5ff1e00e2d4d93313ee1e9355ece2
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99927564"
---
# <a name="how-to-create-a-package-manifest"></a>Instrukcje: tworzenie manifestu pakietu
Aby wdrożyć wymagania wstępne dla aplikacji, można użyć pakietu programu inicjującego. Pakiet programu inicjującego zawiera jeden plik manifestu produktu, ale manifest pakietu dla każdego ustawienia regionalnego. Funkcje udostępnione w różnych zlokalizowanych wersjach powinny przechodzić do manifestu produktu.

 Aby uzyskać więcej informacji na temat manifestów produktu, zobacz [How to: Create a Product](../deployment/how-to-create-a-product-manifest.md)for.

## <a name="create-the-package-manifest"></a>Tworzenie manifestu pakietu

#### <a name="to-create-the-package-manifest"></a>Aby utworzyć manifest pakietu

1. Utwórz katalog dla pakietu programu inicjującego. W tym przykładzie używa *C:\Package*.

2. Utwórz podkatalog o nazwie ustawień regionalnych, takich jak *pl* dla języka angielskiego.

3. W programie Visual Studio Utwórz plik XML o nazwie *package.xml* i Zapisz go w folderze *C:\package\en* .

4. Dodaj plik XML, aby wyświetlić nazwę pakietu programu inicjującego, kulturę dla tego zlokalizowanego manifestu pakietu i opcjonalną umowę licencyjną. W poniższym kodzie XML są stosowane zmienne `DisplayName` i `Culture` , które są zdefiniowane w późniejszym elemencie.

    ```xml
    <Package
        xmlns="http://schemas.microsoft.com/developer/2004/01/bootstrapper"
        Name="DisplayName"
        Culture="Culture"
        LicenseAgreement="eula.txt">
    ```

5. Dodaj plik XML, aby wyświetlić listę wszystkich plików znajdujących się w katalogu specyficznym dla ustawień regionalnych. Poniższy kod XML używa pliku o nazwie *eula.txt* , który jest stosowany dla ustawień regionalnych **EN** .

    ```xml
    <PackageFiles>
      <PackageFile Name="eula.txt"/>
    </PackageFiles>
    ```

6. Dodaj kod XML, aby zdefiniować lokalizowalne ciągi dla pakietu programu inicjującego. Poniższy kod XML dodaje ciągi błędów dla ustawień regionalnych **EN** .

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

7. Skopiuj folder *C:\Package* do katalogu inicjującego programu Visual Studio. W przypadku programu Visual Studio 2010 jest to katalog *\Program Files\Microsoft SDKs\Windows\v7.0A\Bootstrapper\Packages* .

## <a name="example"></a>Przykład
 Manifest pakietu zawiera informacje specyficzne dla ustawień regionalnych, takie jak komunikaty o błędach, postanowienia licencyjne dotyczące oprogramowania i pakiety językowe.

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

## <a name="see-also"></a>Zobacz też
- [Dokumentacja schematu produktu i pakietu](../deployment/product-and-package-schema-reference.md)