---
title: 'Instrukcje: Tworzenie manifestu pakietu | Microsoft Docs'
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
- package files [Windows Installer]
- package files [ClickOnce]
- prerequisites, custom bootstrapper package
- dependencies, custom bootstrapper packages
ms.assetid: 5aecc507-2764-42f2-ae6f-c227971cf0af
caps.latest.revision: 14
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: c711c50ab484cc88b1d6aff5c8e3018cead69953
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68153839"
---
# <a name="how-to-create-a-package-manifest"></a>Porady: tworzenie manifestu pakietu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Aby wdrożyć wymagania wstępne dla aplikacji, można użyć pakietu programu inicjującego. Pakiet programu inicjującego zawiera jeden plik manifestu produktu, ale manifest pakietu dla każdego ustawienia regionalnego. Funkcje udostępnione w różnych zlokalizowanych wersjach powinny przechodzić do manifestu produktu.  
  
 Aby uzyskać więcej informacji na temat manifestów pakietów, zobacz [How to: Create a Product](../deployment/how-to-create-a-product-manifest.md)for.  
  
## <a name="creating-the-package-manifest"></a>Tworzenie manifestu pakietu  
  
#### <a name="to-create-the-package-manifest"></a>Aby utworzyć manifest pakietu  
  
1. Utwórz katalog dla pakietu programu inicjującego. W tym przykładzie używa C:\Package.  
  
2. Utwórz podkatalog o nazwie ustawień regionalnych, takich jak pl dla języka angielskiego.  
  
3. W programie Visual Studio Utwórz plik XML o nazwie `package.xml` i Zapisz go w folderze C:\package\en.  
  
4. Dodaj plik XML, aby wyświetlić nazwę pakietu programu inicjującego, kulturę dla tego zlokalizowanego manifestu pakietu i opcjonalną umowę licencyjną. W poniższym kodzie XML są stosowane zmienne `DisplayName` i `Culture` , które są zdefiniowane w późniejszym elemencie.  
  
    ```  
    <Package  
        xmlns="http://schemas.microsoft.com/developer/2004/01/bootstrapper"  
        Name="DisplayName"  
        Culture="Culture"  
        LicenseAgreement="eula.txt">  
    ```  
  
5. Dodaj plik XML, aby wyświetlić listę wszystkich plików znajdujących się w katalogu specyficznym dla ustawień regionalnych. Poniższy kod XML używa pliku o nazwie eula.txt, który jest stosowany dla ustawień regionalnych **EN** .  
  
    ```  
    <PackageFiles>  
      <PackageFile Name="eula.txt"/>  
    </PackageFiles>  
    ```  
  
6. Dodaj kod XML, aby zdefiniować lokalizowalne ciągi dla pakietu programu inicjującego. Poniższy kod XML dodaje ciągi błędów dla ustawień regionalnych en.  
  
    ```  
      <Strings>  
        <String Name="DisplayName">Custom Bootstrapper Package</String>  
        <String Name="CultureName">en</String>  
        <String Name="NotAnAdmin">You must be an administrator to install   
    this package.</String>  
        <String Name="GeneralFailure">A general error has occurred while   
    installing this package.</String>  
    </Strings>  
    ```  
  
7. Skopiuj folder C:\Package do katalogu inicjującego programu Visual Studio. W przypadku programu Visual Studio 2010 jest to katalog \Program Files\Microsoft SDKs\Windows\v7.0A\Bootstrapper\Packages.  
  
## <a name="example"></a>Przykład  
 Manifest pakietu zawiera informacje specyficzne dla ustawień regionalnych, takie jak komunikaty o błędach, postanowienia licencyjne dotyczące oprogramowania i pakiety językowe.  
  
```  
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
 [Produkt i pakiet — odwołanie do schematu](../deployment/product-and-package-schema-reference.md)
